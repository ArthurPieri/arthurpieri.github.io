---
title: "Learning SQL"
author: "Arthur Pieri"
tags: 
- data-engineering
- data
- SQL
---
#data #SQL 
## What is SQL?
Structured Query Language (SQL pronounced S Q L or Sequel) is a language focused in access and manipulate Databases, it became a ANSI standard in 1986 and ISO in 1987. But even though it is a Standard there are multiple versions of it's implementation. But all of them must suport the major commands to be considered ANSI compliant. Commands like:
- SELECT
- UPDATE
- DELETE
- INSERT
- WHERE
and a few others.
And many SQL databases posses their own proprietary extensions and additions.

> SQL commands are case-insensitive meaning you can write them all Uppercase: SELECT, all lowercase: update or make party like:DeLeTE.

> It is however a commom practice to write the function names in uppercase: 
```sql
SELECT customerName FROM table.
```
> Since it improve readability of your queries

A SQL Database usually need a Relational DataBase Management System or RDBMS to be accessed.

All RDBMS uses the same principle to store data: A two dimensional table consisted of Data rows in the Horizontal Axis and strictly enforced column types on the Vertical Axis. 

And many tables form a Database.

It can be thought as a set of components:

There are 5 generic components of the SQL language:  
- [[DDL: data definition language]], such as: 
	- Operations
		 - CREATE
		- ALTER
		- DROP
	- Targets
		- database
		- table
		- constraints
		- view
		- index
- [[DQL: data query language]], such as: 
	- SELECT
	- FROM
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
- [[SQL Data Types]]
	- SQL Numeric type
	- SQL String type
	- SQL Datetime type
	- SQL Boolean type
	- SQL JSON type

SQL techniques:
- [[CTE - Common Table Expression]]
- [[TEMPORARY TABLES]]
- [[TRANSIENT TABLES]]

Source: https://www.w3schools.com/sql/sql_intro.asp