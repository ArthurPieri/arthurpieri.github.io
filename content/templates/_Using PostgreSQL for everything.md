---
title: _Using PostgreSQL for everything
author: Arthur Pieri
tags:
  - data-engineering
  - data
---
## Where we started

I was hired as a data engineer at a company that developed a fundraising platform. Because of that, they've also created an email management system that helps customers send emails, check for KPIs, create focused campaigns, and do everything else related to their business.

The problem was that when they started growing, the reports and KPIs took too long to load and sometimes would not work because the database was not responding.

At first, we believed that the problem was simple: the OLTP and OLAP databases were the same, so we would only need to create distinct databases.

As we moved with this approach, we were still having trouble where some queries would take too long, and when the ETL batch processing started, the OLTP database could not respond to transactional queries.

So, along with developers, we decided to look into database construction and how the codebase generated queries.

## The True problem
The first thing that caught our attention was that the whole database was less than a TeraByte size, closer to 700GB. The Aurora instance was an X-Large, so infrastructure, computing, or memory was not a problem. PostgreSQL was supposed to deal with database orders of a magnitude bigger than this, and yet our requests were taking too long.

Then, we ran a few analyses into the database and discovered that among the more than 200 tables, only one was responsible for about 95% of all usage, and the following two tables were responsible for almost all of the 5% usage left.

This one table was being used as a log for email events (email sent, email received, email opened, link clicked, etc.), so it should be a "write-focused" table. Still, it had about five different indexes representing almost 18% of the total size of the table.

Another thing was that every event was being saved into the same table, and two of those indexes were trying to deal with that fact.

## The solution
The Tech team wanted to rewrite this management system for some time, breaking it down into smaller services and using a more performant language like Go. From what we saw, the database also needed refactoring from the ground up.

So we decided to:
1. Create a few different databases in every instance
2. Have one database work as an event log, using CDC and breaking events into schemas and tables to save each event type into a specific table.
3. Have another database with pre-calculated metrics to be shown in dashboards and on the web app
4. Use AWS SNS/SQS as a queue for new writes

## The results

By making only the database changes, we cut about 85% of the mean query response time; when factoring in the new codebase with Go, the gains were about an order of magnitude, going from 5s to less than 200ms.

This new database was running in a small instance of AWS Aurora (cutting a lot of the cost) and enabling the creation of more replica databases to ensure data would always be available to customers.

======================
# Email Management System Performance Optimization Project

## Executive Summary

This report documents the successful optimization of our fundraising platform's email management system. Through strategic database restructuring and application modernization, we achieved a 95% reduction in query response time while significantly reducing infrastructure costs. The project addressed critical performance issues that were impacting customer experience and system reliability.

## Problem Identification

Our fundraising platform's email management system, which enables customers to send emails, track KPIs, and manage campaigns, was experiencing severe performance degradation as the user base grew. Reports and dashboards were loading slowly or failing completely during peak usage periods.

Initial assessment suggested a simple need to separate OLTP (transactional) and OLAP (analytical) workloads. However, deeper investigation revealed more fundamental issues with the database architecture.

## Technical Analysis

Key findings from our database analysis:

- The database was relatively modest in size (~700GB) running on an Aurora X-Large instance
- A single email event log table was responsible for 95% of all database utilization
- This table contained multiple event types (sends, opens, clicks) in a unified structure
- Five different indexes on this table constituted 18% of its total size
- ETL batch processing was creating contention with operational queries

These findings indicated that our performance issues stemmed from database design rather than infrastructure limitations.

## Solution Implementation

We implemented a comprehensive restructuring approach:

1. Separated databases based on workload patterns
2. Created a dedicated event log database using Change Data Capture (CDC)
3. Implemented separate tables for different event types to optimize query patterns
4. Developed a pre-calculated metrics database for reporting and visualization
5. Implemented AWS SNS/SQS for asynchronous event processing
6. Supported the development team's initiative to refactor the application into microservices using Go

## Results and Business Impact

The optimization delivered measurable improvements:

- Database response time reduced by 85% through architectural changes alone
- Overall system response time improved from 5 seconds to under 200ms when combined with application refactoring
- Infrastructure costs reduced by migrating to smaller Aurora instances
- System reliability enhanced through the ability to deploy additional read replicas
- Improved scalability foundation for future growth

## Conclusion

This project demonstrates how targeted database architecture improvements combined with modern application design principles can dramatically enhance system performance and reliability while reducing operational costs. The new architecture provides the scalability and performance needed to support our growing customer base.


===============
> Linkedin Project Text
# Email Management System Performance Optimization Project

## Initial Challenge

Our fundraising platform's email management system was experiencing severe performance degradation. As our customer base grew, critical reports and KPIs became increasingly slow to load, sometimes failing when the database couldn't respond.

## Root Cause Analysis

Initially, we hypothesized that separating our transactional (OLTP) and analytical (OLAP) databases would resolve these issues. However, a deeper investigation revealed more fundamental problems:

1. A single event logging table consumed 95% of database resources
2. This table stored all email events (sends, opens, clicks) in one location
3. Multiple indexes (consuming 18% of table size) were attempting to compensate for poor structure
4. Database architecture didn't align with actual usage patterns

Our infrastructure wasn't the bottleneck—our 700GB database was running on an Aurora X-Large instance with ample computing capacity.

## Implemented Solution

We completely redesigned the database architecture:

- Created separate specialized databases on each instance
- Developed an event log database with event-specific tables
- Implemented a dedicated metrics database with pre-calculated values
- Integrated AWS SNS/SQS for queue management of new writes

## Results

The transformation delivered significant improvements:

- 85% reduction in query response time from database changes alone
- Overall performance improvement from 5s to under 200ms with new Go codebase
- Reduced infrastructure costs by running on smaller Aurora instances
- Enhanced reliability through additional replica databases
- Improved scalability to support continued business growth

This project demonstrated how targeted architectural improvements can deliver substantial performance gains while reducing operational costs.