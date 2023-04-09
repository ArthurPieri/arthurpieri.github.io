---
title: "_SQL Datatypes"
author: "Arthur Pieri"
tags: 
- 
---

## SQL data types

The SQL standard defines three kinds of [data types](https://en.wikipedia.org/wiki/Data_type "Data type") (chapter 4.1.1 of SQL/Foundation):

-   predefined data types
-   constructed types
-   user-defined types.

_Constructed types_ are one of ARRAY, MULTISET, REF(erence), or ROW. _User-defined types_ are comparable to classes in object-oriented language with their own constructors, observers, mutators, methods, inheritance, overloading, overwriting, interfaces, and so on. _Predefined data types_ are intrinsically supported by the implementation.

### Predefined data types[[edit](https://en.wikipedia.org/w/index.php?title=SQL&action=edit&section=21 "Edit section: Predefined data types")]

-   Character types

-   Character (CHAR)
-   Character varying (VARCHAR)
-   Character large object (CLOB)

-   National character types

-   National character (NCHAR)
-   National character varying (NCHAR VARYING)
-   National character large object (NCLOB)

-   Binary types

-   Binary (BINARY)
-   Binary varying (VARBINARY)
-   Binary large object (BLOB)

-   Numeric types

-   Exact numeric types (NUMERIC, DECIMAL, SMALLINT, INTEGER, BIGINT)
-   Approximate numeric types (FLOAT, REAL, DOUBLE PRECISION)
-   Decimal floating-point type (DECFLOAT)

-   Datetime types (DATE, TIME, TIMESTAMP)
-   Interval type (INTERVAL)
-   Boolean
-   XML
-   JSON