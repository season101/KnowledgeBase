# Table of Contents 
 1: Getting Started with SQL for Data Engineering
 2: Setup Tools for Data Engineering Essentials
 3: Setup Application Tables and Data in Postgres Database 
 4: Writing Basic SQL Queries
 5: Cumulative Aggregations and Ranking in SQL Queries
 6: SQL Troubleshooting and Debugging Guides
 7: Performance Tuning of SQL Queries
 8: Exercises for Basics of SQL Queries
 9: Solutions for Basic SQL Queries
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

## Setup Tools for Data Engineering Essentials
### IDE: VS Code
### Python 3.9
### Postgres 14
Simple command to list the tables:
```sql
SELECT * FROM information_schema.tables;
```

---
# Setup Application Tables and Data in Postgres Database
## Overview of Connecting to Database using pgAdmin
Postgres is a multi-tenant database server.
PgAdmin is a client to connect to Postgres server.
![[Pasted image 20231010084935.png]]
## Creating Application Database and User in Postgres Database Server

**Creating a Database**
```sql
CREATE DATABASE itversity_retail_db;
```
**Creating a User**
```sql
CREATE USER itversity_retail_user WITH ENCRYPTED PASSWORD 'itversity';
```
**Assigning Permissions**
```sql
GRANT ALL ON DATABASE itversity_retail_db TO itversity_retail_user;
```
**Creating a Table**
sample example:
```sql
-- Postgres Table Creation Script
--

--
-- Table structure for table departments
--

CREATE TABLE departments (
  department_id INT NOT NULL,
  department_name VARCHAR(45) NOT NULL,
  PRIMARY KEY (department_id)
);

--
-- Table structure for table categories
--

CREATE TABLE categories (
  category_id INT NOT NULL,
  category_department_id INT NOT NULL,
  category_name VARCHAR(45) NOT NULL,
  PRIMARY KEY (category_id)
); 

--
-- Table structure for table products
--

CREATE TABLE products (
  product_id INT NOT NULL,
  product_category_id INT NOT NULL,
  product_name VARCHAR(45) NOT NULL,
  product_description VARCHAR(255) NOT NULL,
  product_price FLOAT NOT NULL,
  product_image VARCHAR(255) NOT NULL,
  PRIMARY KEY (product_id)
);

--
-- Table structure for table customers
--

CREATE TABLE customers (
  customer_id INT NOT NULL,
  customer_fname VARCHAR(45) NOT NULL,
  customer_lname VARCHAR(45) NOT NULL,
  customer_email VARCHAR(45) NOT NULL,
  customer_password VARCHAR(45) NOT NULL,
  customer_street VARCHAR(255) NOT NULL,
  customer_city VARCHAR(45) NOT NULL,
  customer_state VARCHAR(45) NOT NULL,
  customer_zipcode VARCHAR(45) NOT NULL,
  PRIMARY KEY (customer_id)
); 

--
-- Table structure for table orders
--

CREATE TABLE orders (
  order_id INT NOT NULL,
  order_date TIMESTAMP NOT NULL,
  order_customer_id INT NOT NULL,
  order_status VARCHAR(45) NOT NULL,
  PRIMARY KEY (order_id)
);

--
-- Table structure for table order_items
--

CREATE TABLE order_items (
  order_item_id INT NOT NULL,
  order_item_order_id INT NOT NULL,
  order_item_product_id INT NOT NULL,
  order_item_quantity INT NOT NULL,
  order_item_subtotal FLOAT NOT NULL,
  order_item_product_price FLOAT NOT NULL,
  PRIMARY KEY (order_item_id)
);
```

