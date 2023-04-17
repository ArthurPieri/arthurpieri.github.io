---
title: "Learning SQL"
author: "Arthur Pieri"
Tags: 
- data-engineering
- data
- SQL
---
#data #SQL 
## What is SQL?
Structured Query Language (SQL pronounced S Q L or Sequel) is a language focused in access and manipulating Databases, it became an ANSI standard in 1986 and ISO in 1987. 

But even though it is a Standard each developer/company can implement it in different ways. However, to be considered ANSI Compliant (and be suitable for production use) it must support the major commands:
- SELECT
- UPDATE
- DELETE
- INSERT
- WHERE
- and a few others.

Many SQL databases possess proprietary extensions and additions specific to their implementations and therefore will not be covered here.

> SQL commands are case-insensitive meaning you can write them all in Uppercase: SELECT, all lowercase: update or make it a party like DeLeTE.

> It is however a common practice to write the function names in uppercase since it improves the readability of your queries: 
```sql
SELECT customerName FROM table.
```
Using SQL you can query for data, preferably structured data, hosted by a Relational DataBase Management System (RDBMS).

Data in an RDBMS is organized, from more complex to less:
- [[_SQL Databases]]
- [[_SQL Schemas]]
- [[SQL Tables]]

SQL was first created using concepts from relational algebra and tuple relational calculus. And can be broken down into 5 "sublanguages":
- [[DDL: data definition language]], such as: 
	- Operations
		 - CREATE
		- ALTER
		- DROP
	- Targets
		- database
		- table
		- constraints
		- View
		- index
- [[DQL: data query language]], such as: 
	- SELECT
	- FROM
	- JOIN
	- WHERE
	- GROUP BY
	- HAVING
	- ORDER BY
	- LIMIT
- [[DML: data manipulation language]], such as 
	- INSERT
	- UPDATE
	- DELETE  
- [[DCL: data control language]], such as: 
	- GRANT
	- REVOKE  
- [[TCL: transaction control language]], such as: 
	- START (BEGIN) TRANSACTION
	- COMMIT
	- ROLLBACK

There are also 3 implementation dependant components:
- [[SQL Operators]]
	- SQL Logical operators
	- SQL Comparison operators
	- SQL Math operators
- [[SQL Functions]]
	- SQL Numeric functions
	- SQL String functions
	- SQL Datetime functions
- [[_SQL Data types]]
	- SQL Numeric type
	- SQL String type
	- SQL Datetime type
	- SQL Boolean type
	- SQL JSON type

## SQL Queries syntax
The SQL language can be subdivised in several elements, that may help the learning:
[[_SQL Syntax_]]

SQL techniques:
- [[CTE - Common Table Expression]]
- [[TEMPORARY TABLES]]
- [[TRANSIENT TABLES]]

Source: https://www.w3schools.com/sql/sql_intro.asp