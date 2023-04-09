---
title: "_SQL Syntax_"
author: "Arthur Pieri"
tags: 
- 
---

https://en.wikipedia.org/wiki/SQL_syntax

The SQL language is subdivided into several language elements, including:

-   _Clauses_, which are constituent components of statements and queries. (In some cases, these are optional.)
-   _Expressions_, which can produce either [scalar](https://en.wikipedia.org/wiki/Scalar_(computing) "Scalar (computing)") values, or [tables](https://en.wikipedia.org/wiki/Table_(database) "Table (database)") consisting of [columns](https://en.wikipedia.org/wiki/Column_(database) "Column (database)") and [rows](https://en.wikipedia.org/wiki/Row_(database) "Row (database)") of data
-   _Predicates_, which specify conditions that can be evaluated to SQL [three-valued logic (3VL)](https://en.wikipedia.org/wiki/Ternary_logic "Ternary logic") (true/false/unknown) or [Boolean](https://en.wikipedia.org/wiki/Boolean_logic "Boolean logic") [truth values](https://en.wikipedia.org/wiki/Truth_value "Truth value") and are used to limit the effects of statements and queries, or to change program flow.
-   _Queries_, which retrieve the data based on specific criteria. This is an important element of _SQL_.
-   _Statements_, which may have a persistent effect on schemata and data, or may control [transactions](https://en.wikipedia.org/wiki/Database_transaction "Database transaction"), program flow, connections, sessions, or diagnostics.
    -   SQL statements also include the [semicolon](https://en.wikipedia.org/wiki/Semicolon "Semicolon") (";") statement terminator. Though not required on every platform, it is defined as a standard part of the SQL grammar.
-   _[Insignificant whitespace](https://en.wikipedia.org/wiki/Whitespace_(computer_science) "Whitespace (computer science)")_ is generally ignored in SQL statements and queries, making it easier to format SQL code for readability.