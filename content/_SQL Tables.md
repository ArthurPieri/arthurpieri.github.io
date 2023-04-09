---
title: "_SQL Tables"
author: "Arthur Pieri"
tags: 
- 
---
# What are SQL Tables?



All RDBMS uses the same principle to store data: A two-dimensional table consisted of Data rows on the Horizontal Axis and strictly enforced column types on the Vertical Axis. 

Each row represents a unique record and each column represents a field in that record.

For instance, if you want to create a register of your spending we can create a table that contains:
- Name of the Store 
- Name of the item
- Cost of the item
- Description

| Store | Item | Price | Description |
| ----- | ---- | ----- | ----------- |
| x     | x    | x     | x           |

Those are our columns, and we can input as many records as we want

| Store     | Item        | Price | Description         |
| --------- | ----------- | ----- | ------------------- |
| Gamex     | Xbox        | 400   | Xbox console        |
| Gamex     | FIFA 2023   | 60    | Xbox game           |
| Groceries | Chocolate   | 5     |                     |
| GameX     | Playstation | 420   | Playstation console |
| GameX     | FIFA 2023   | 60    | PS game                    |

Not so bad, but we are still missing a few things in that table, how can we search for a single record? Is there anything that can uniquely identify one record for every single record?

At this moment, there isn't that is why almost every SQL table contains a special column that is used to Uniquely Identify a record called Primary Key or PK

So our table would look like this:

| ID  | Store     | Item        | Price | Description         |     |     |     |     |     |
| --- | --------- | ----------- | ----- | ------------------- | --- | --- | --- | --- | --- |
|  1   | Gamex     | Xbox        | 400   | Xbox console        |     |     |     |     |     |
|  2   | Gamex     | FIFA 2023   | 60    | Xbox game           |     |     |     |     |     |
|  3   | Groceries | Chocolate   | 5     |                     |     |     |     |     |     |
|  4   | GameX     | Playstation | 420   | Playstation console |     |     |     |     |     |
|  5   | GameX     | FIFA 2023   | 60    | PS game             |     |     |     |     |     |

The PK column can be of any type and can be manually created, or automatically created by the RDBMS. The only constraint is that it needs to be Unique. 


And that could be it, but we are missing two essencial things

each column can be defined as one of the [[_SQL Data types]]