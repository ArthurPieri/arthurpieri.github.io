---
title: 98% Economy on Data Lake
author: Arthur Pieri
tags:
  - data-engineering
  - data
keywords:
  - datawarehouse
  - data engineering
---
## The beginning

One day I was looking at some of the KPIs from our Data lake; we use a pretty "standard" stack with:

- [[Snowflake]] is our data lake.
- [[Airflow]] to manage execution
- [[Python]] with [[pandas]] to execute the ETL process

Only one person made this stack on a tight schedule, so we expected to have some places to optimize. And one day, I was talking to a friend who said that he was able to cut costs from their Data Lake simply by changing a lot of processes  that were created with:

```sql
CREATE OR REPLACE TABLE xxxxx
```

And then I thought, if things like that happened in more prominent companies, we probably would have some stuff like that on our own.

So we started looking and found one pipeline where every table was constructed with the infamous CREATE OR REPLACE.

## Collecting data
1. The first "red flag is that our fail-safe was way more extensive than the actual database
![[datalake_storage_before.png]]
2. The other thing that caught our attention was the number of tables being created in a single pipeline: 26. The mean time to run the pipeline was close to 11 minutes for a pipeline that runs every 30 minutes.

## From top to bottom
### The first step
The first thing we did after that was to look at the most important and used table on the pipeline, which is one of those [[_OBT]]s. 
After gathering all the columns and finding where those columns came from, we found the second problem:
- In the urge to follow a "design pattern," we created lots of useless tables. Ok, we had schemas that follow a pattern:
	- Transient
	- Raw
	- Trusted
	- Internal
- The problem was we didn't need this, and we were creating schemas and tables that did nothing to the data and were just there, wasting storage and time.

### The second step
Understanding our source tables and how to extract only the delta from them. This took some time, but nothing too complex.

### The third step
Document everything!
- What tables were created before
- What tables were being created now
- Were there any columns that were being left out?
- Every schema removed got its own commit, so it would be easy to roll back if needed.
- Run tests

### Finally
We applied the changes in production, and here are some of the improvements:
- The mean time to run the pipeline went from almost 11 minutes to around 6 minutes.
- The amount of written data was cut down by 98% (From close to 700MB to around 10MB). Remember, it was being written every 30 minutes.
![[datalake_storage_half_way.png]]
- The number of tables down from 26 to 11

## Thoughts
- Even though I am only presenting the most significant differences, we got some other less impressive and yet substantial changes, like a 52% reduction on our customer orders table.
- And a sneak peek of the other big economy we made:
![[datalake_storage_end.png]]
	- From 1.3TB to 550GB