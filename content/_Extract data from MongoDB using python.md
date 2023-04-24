---
title: "_Extract data from MongoDB using python"
author: "Arthur Pieri"
tags: 
- data-engineering
- python
- pandas
- mongodb
---
#data-engineering #python #pandas #mongodb 
# The problem
In the company, I'm currently working for, I was tasked to create a pipeline to bring data from MongoDB to our DataLake. Searching online for some tutorials or help, but found nothing really useful. Every tutorial or article treats MongoDB as somewhat of a SQL database. Everything is well structured, every record possesses the same fields and all is good.

The problem is that working with a MongoDB that really is used, we found a lot of things that aren't all sunshine and rainbows. Data is somewhat unstructured, there is a lot of garbage in data, and even some truly macaronic architecture that has an array of jsons with arrays, the true definition of a rat's nest.

And that's why I decided to document everything I needed to do when working with real-world data, and a not-so-perfect architecture and database.

## First things first
Our data stack is composed by:
- Airflow
- Python and its libraries
- Snowflake
- AWS S3
- DBT
- MongoDB (of course)

## The quick and dirty solution
In order to get the pipeline running as fast as possible, we decided to start by grabbing data from MongoDB using Pymongo, and sending it to AWS S3 as a JSON file. Once there, we would read the files using Snowflake's external file capabilities, and use Plain SQL to load data into tables.

> The following code is not complete and is used only as an example.

```python
import pymongo
from datetime import datetime
from bson import decode_all
from bson.json_util import dumps

def get_mongo_data(
	agg_clause: str,
	bucket_name: str, 
	collection: str,
	connection_string: str,
	database_name: str,
	last_date: datetime,
	mongo_filter: list):
	'''
	Get the delta of data from MongoDB
	This code is not complete, since it calls for functions that are not implemented.
	'''
	# Get MongoDB Cursor
	mongo_client = pymongo.MongoClient(connection_string)
	db = mongo_client[database_name]
	filter_condition = get_filter_condition(agg_clause, mongo_filter, last_date)
	cursor = db[collection]. aggregate_raw_batches(
			[
				{'$match': condition},
				agg_clause,
			]
		)
	# Get boto3 connection to s3
	boto3_sesion = get_connection()
	s3_client = boto3_session.client('s3')

	file_count = 0

	# Get batches from the cursor
	for batch in cursor:
		file_count += 1
		file_path = 'stage/year/month/day/hour'
		result = dumps(decode_all(batch))
		s3_client.put_object(Bucket=bucket_name, Key=file_path, Body=result)

	mongo_client.close()

```

So the code above gets batches of data from Mongo, dumps it into a JSON, and sends it to an S3 Bucket. From there we can access the data in Snowflake and use some functions to load the data. Something like:

```SQL
CREATE TABLE IF NOT EXISTS database.raw_schema.table AS(
	SELECT
	-- I'm breaking down the lines to be a little easier to understand what is happening
		TRY_PARSE_JSON(
			replace(
				GET_IGNORE_CASE($1, 'id'), '$')):oid::text as id
		,TRY_PARSE_JSON(
			replace(
				GET_IGNORE_CASE($1, 'date_field'), '$')):date::DATETIME as _date
		-- ...
	FROM
		@stage/path/to/file (file_format => json_array)
);

```
> Note: please do not use CREATE OR REPLACE TABLE see [[98% Economy on Data Lake]] for context

> After that, all you need to do is start merging the new data into this table. Using COPY INTO or MERGE functions on Snowflake.

### Pros
- Fast way to get you going
- You don't need to deal with the data in Python
### Cons
- Double or Triple the cost of storage
	- Snowflake (external stage and internal stage) and S3.
- Put the processing cost into Snowflake (which can be expensive if not careful)
- If anything changes in MongoDB you need to manually change the SQL that creates and updates the raw table.

> If your data is mostly unmutable, and well structured, this can do the trick, but what happens when developers use to the fullest the not typing of data in Mongo? 

# Making it a little more future proof
