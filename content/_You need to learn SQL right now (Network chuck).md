---
title: "You need to learn SQL right now (Network chuck)"
author: "Arthur Pieri"
tags: 
- SQL
---

# Draft
**Walkthrough and commands:**

**Update your repos**

sudo apt install -y; sudo apt upgrade -y

  

**Install MySQL**

_sudo apt install mysql-server_

  

**Verify MySQL is running**

_sudo systemctl status mysql_

  

**Login to SQL**

_sudo mysql_

  

**View databases**

_show databases;_

  

**Create database**

_CREATE DATABASE <database name>;_

  

**Select database**

USE <Database name>;

  

**Show tables**

SHOW tables;

  

**Create Table example**

`_CREATE TABLE Characters (_`

_`FirstName varchar(255),`_

_`LastName varchar(255),`_

_`Origin varchar(255),`_

_`Age int,`_

_`name varchar(255)`_

`_);_`

  

**Show basic table info**

_describe <table_name>;_

  

**Adding data in to a table example**

_INSERT INTO Characters (FirstName,LastName,Origin,Age,Alias)VALUES ('Thor','Odinson','Asgard',1500,'God of thunder');_

  

**Basic select statement**

_SELECT * FROM <table>;_

  

**Where clause example**

_SELECT * FROM Avengers WHERE Origin = 'Earth';_

  

**Delete entry**

`_DELETE FROM Characters_`

`_WHERE FirstName = ‘Jeff’;_`

  

**Update entry**

_update table_

_set <column> = <value>_

_where <condition>;_

  

**Order by ascending** 

_SELECT * FROM avengers ORDER BY Age ASC;_

  

**Order by descending**

_SELECT * FROM avengers ORDER BY Age DESC;_

  

**Alter table**

_alter table < table name>  add <column> <data type>;_