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
I'm currently working for a company that began using MongoDB as its primary database. 
The problem is that it was supposed to be only for the MVP, but it kept growing and growing and since Mongo doesn't care about typing, we end up with lots of unstructured data, garbage, and even sometimes, a truly macaronic bundle of arrays inside jsons inside arrays the definition of a rat's nest... 

--------
-------------

> Other option

Searching online for some help to bring data from MongoDB into pandas and then sending it to Snowflake, I've encountered one big problem, everyone just assumes your data is perfectly normalized and without changes. It seems more like data coming from a SQL Table than from a semi-structured source.

-----------
--------

And being responsible to create a Pipeline to take data from Mongo and send it to Snowflake, I've encountered all sorts of problems, and decided to document them, since searching for help online, all I found were examples using the best-case scenario where the data resembled much more a SQL database than a semi-structured kind.

## First things first
Our data tools were:
- Airflow
- Python and its libraries
- Snowflake
- AWS S3
- DBT
- MongoDB (of course)

## The quick and dirty solution
In order to get the pipeline running as fast as possible, we decided to start by grabbing data from MongoDB using Pymongo, and sending it to S3 as a JSON file. Once there, we would read the files using Snowflake's external file capabilities, and use Plain SQL to send data to tables.

The following code is not complete and is used only for example.

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

So the code above gets batches of data from Mongo, dumps it into a JSON, and sends it to an S3 Bucket. From there we can access the data in Snowflake and use some functions to extract the data. Something like:

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
> Note: please do not use CREATE OR REPLACE TABLE see [[98% Economy on Data Lake]]

> After that, all you need to do is start merging the new data into this table.

### Pros
- Fast way to get you going
- You don't need to deal with the data in Python
### Cons
- Double or Triple the cost of storage
	- Snowflake (external stage and internal stage), S3, and Mongo
- Put the processing cost into Snowflake (which can be expensive if not careful)
- If anything changes in MongoDB you need to manually change the SQL that creates and updates ir raw table.

> If your data is mostly unmutable, and well structured, this can do the trick, but what happens when developers use to the fullest the not typing of data in Mongo?

# Making it a little more future proof



