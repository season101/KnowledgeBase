# Table of Contents 
 1: Getting Started with SQL for Data Engineering
 2: Setup Tools for Data Engineering Essentials 
 3: Writing Basic SQL Queries
 4: Cumulative Aggregations and Ranking in SQL Queries
 5: SQL Troubleshooting and Debugging Guides
 6: Performance Tuning of SQL Queries
 7: Exercises for Basics of SQL Queries
 8: Solutions for Basic SQL Queries
---
# Getting Started with SQL for Data Engineering

## Overview of Application Architecture and RDBMS
![[Pasted image 20231006181216.png]]

## Overview of Database Technologies and relevance of SQL
Common database technologies are: Oracle, Snowflake, Databricks, Postgres, MySQL, MSSQL Server, Teradata, Sybase, etc. They have SQL technology in common.

RDBMS: Oracle, MySQL, Postgres, MS SQL Server, Sybase.
Transactional use case. For example. Web server.

Data Warehouse: Snowflake, Databricks, Teradata, GCP BigQuery, AWS Redshift, Azure Synapse

## Purpose Built Databases

1. RDBMS
2. Data Warehouse or MPP(Massively Parallel Processing)
3. NoSQL: Cassandra, MongoDB
4. Search: Elastic Search, SoLR
5. Graph: Neo4j

![[Pasted image 20231006182650.png]]

## Overview of Data Warehouse and Data Lake
Dashboarding and Analytics purpose. To Process Downstream of data.

![[Pasted image 20231006183116.png]]

Data Lake: Basically, Data storage. 
Data Warehouse: Provides computational power. 

## Usage of Data Warehouse and Data Lake
Business Problems:
1. What is the profitability of the organization?
2. What is the Revenue trend over this year?
3. Which category is performing well?

## Comparison between RDBMS and Data Warehouse

| RDBMS | Data WareHouse |
|---|---|
| Tables, Columns, Data Types, Rows or Records | Tables, Columns, Data Types, Rows or Records |
| Transactional (OLTP) | OLAP or DSS |
| Mobile or Web | Reports or Dashboards |
| SQL | SQL |


OLTP: Online Transactional Processing
OLAP: Online Analytical Processing
DSS: Decision Support System

# Setup Tools for Data Engineering Essentials
