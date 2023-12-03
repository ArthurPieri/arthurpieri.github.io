---
title: SQL Tables
author: Arthur Pieri
tags:
  - data-engineering
  - coding
  - SQL
keywords:
  - data engineering
  - coding
  - sql
---
# What are SQL Tables?

All [[_RDBMS]] uses the same principle to store data: A two-dimensional table consisted of Data rows on the Horizontal Axis and strictly enforced column types on the Vertical Axis. 

The Horizontal axis is known as a [[SQL row]] and the Vertical axis is known as a [[SQL Column]]

Each row represents a unique record and each column represents a field in that record.

For instance, if you want to register all of your spendings we can create a table that contains the:
- Name of the Store 
- Name of the item
- Cost of the item
- Description

> All our examples will be focused on the SQLite3 database since it is one of the simplest and easiest to use.

```SQL
CREATE TABLE IF NOT EXISTS spendings (
	store VARCHAR(64)
	, item VARCHAR(32)
	, price INTEGER
	, description VARCHAR(256)
)
```

> To understand more about column names and column types on SQL check [[_SQL Data types]]

So our table ends up like this:
| Store | Item | Price | Description |
| ----- | ---- | ----- | ----------- |
| x     | x    | x     | x           |

Those are our columns, and we can input as many records as we want, for instance:

```sql
INSERT INTO spendings (store, item, price, description)
VALUES ('Gamex', 'Xbox', 400,' Xbox console')
```

That results in the following table:
| Store     | Item        | Price | Description         |
| --------- | ----------- | ----- | ------------------- |
| Gamex     | Xbox        | 400   | Xbox console        |

> And we can keep adding data

| Store     | Item        | Price | Description         |
| --------- | ----------- | ----- | ------------------- |
| Gamex     | Xbox        | 400   | Xbox console        |
| Gamex     | FIFA 2023   | 60    | Xbox game           |
| Groceries | Chocolate   | 5     |                     |
| GameX     | PlayStation | 420   | Playstation console |
| GameX     | FIFA 2023   | 60    | PS game                    |

Not so bad, but we are still missing a few things in that table, how can we search for a single record? Is there anything that can uniquely identify one record? for every single record?

At this moment, there isn't, which is why almost every SQL table contains a special column that is used to Uniquely Identify a record called Primary Key or PK. And we can create a column named ID as our Primary Key:

```sql
ALTER TABLE spendings ADD COLUMN id INTEGER PRIMARY KEY AUTOINCREMENT
```

> So our table would look like this:

| ID  | Store     | Item        | Price | Description         | 
| --- | --------- | ----------- | ----- | ------------------- | 
|  1   | Gamex     | Xbox        | 400   | Xbox console        |
|  2   | Gamex     | FIFA 2023   | 60    | Xbox game           |
|  3   | Groceries | Chocolate   | 5     |                     |
|  4   | GameX     | PlayStation | 420   | Playstation console |
|  5   | GameX     | FIFA 2023   | 60    | PS game             |

The PK column can be of any type and can be manually created, or automatically created by the RDBMS. The only constraint is that it needs to be Unique. 

