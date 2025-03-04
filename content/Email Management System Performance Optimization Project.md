---
title: Email Management System Performance Optimization Project
author: Arthur Pieri
tags:
  - data-engineering
  - data
---
# Email Management System Performance Optimization Project

## Executive Summary

This report documents the successful optimization of our fundraising platform's email management system. Through strategic database restructuring and application modernization, we achieved a 95% reduction in query response time while significantly reducing infrastructure costs. The project addressed critical performance issues that were impacting customer experience and system reliability.

## Problem Identification

Our fundraising platform's email management system, which enables customers to send emails, track KPIs, and manage campaigns, was experiencing severe performance degradation as the user base grew. Reports and dashboards were loading slowly or failing during peak usage periods.

Initial assessment suggested a simple need to separate OLTP (transactional) and OLAP (analytical) workloads. However, deeper investigation revealed more fundamental issues with the database architecture.

## Technical Analysis

Key findings from our database analysis:

- The database was relatively modest in size (~700GB), running on an Aurora X-Large instance.
- A single email event log table accounted for 95% of all database utilization.
- This table contained multiple event types (sends, opens, clicks) in a unified structure.
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

- Database response time was reduced by 85% through architectural changes alone.
- Overall system response time improved from 5 seconds to under 200ms when combined with application refactoring.
- Infrastructure costs were reduced by migrating to smaller Aurora instances.
- System reliability enhanced through the ability to deploy additional read replicas
- Improved scalability foundation for future growth

## Conclusion

This project demonstrates how targeted database architecture improvements combined with modern application design principles can dramatically enhance system performance and reliability while reducing operational costs. The new architecture provides the scalability and performance needed to support our growing customer base.
