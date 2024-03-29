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

# Setup Tools for Data Engineering Essentials
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


# Writing Basic SQL Queries
Note:
use **FORCE**
	Focus
	Observe
	Read
	Comprehend
	Experiment
## Review Data Model Diagram
![[Pasted image 20231010212444.png]]

## Define Problem Statement for SQL Queries
Statement 1: Complete daily product revenue considering "complete" or "closed" orders.
Refer to the data model as they reveal a lot of information related to the problem statement.
We will work towards this problem statement in incremental fashion.
## Filtering Data using SQL Queries
Step 1: Getting "complete" or "closed" orders.
For given database, we observe that following are various **order_status** available to us.
```sql
SELECT DISTINCT order_status FROM orders;
"COMPLETE"
"ON_HOLD"
"PENDING_PAYMENT"
"PENDING"
"CLOSED"
"CANCELED"
"PROCESSING"
"PAYMENT_REVIEW"
"SUSPECTED_FRAUD"
```

Getting the Orders that has "COMPLETE" or "CLOSED" status:
```sql
SELECT * FROM orders 
WHERE order_status= 'COMPLETE' 
OR order_status = 'CLOSED';
```

Alternatively, for this kind of scenario **IN** operator is recommended for better readability and flexibility.
eg:
```sql
SELECT * FROM orders 
WHERE order_status IN ('COMPLETE','CLOSED');
```

This helps in creating the prepared statements in program effectively.
## Total Aggregations using SQL Queries
### AKA Global Aggregations
We aggregate without specifying specific columns as a part of group by. Getting count from specific column is considered global aggregation. Getting revenue for particular product id is global aggregation. eg: COUNT, TOTAL using SUM, MIN, MAX, AVG.
eg: 
```sql
SELECT COUNT(DISTINCT order_status) FROM orders;
```
eg: 
```sql
SELECT SUM(order_item_subtotal) FROM order_items;
```

## Group By Aggregations using SQL Queries
### AKA By Key Aggregations
eg:

Aggregation by order_status:
```sql
SELECT order_status, count(*) AS order_count FROM orders
GROUP BY 1
ORDER BY 2 DESC
;
```
Result: 
![[Pasted image 20231014195234.png]]
Aggregation by order_date:

```sql
SELECT order_date, count(*) AS order_count FROM orders
GROUP BY 1
ORDER BY 2 DESC;
```

Result
![[Pasted image 20231014195314.png]]

**Trick**: to get order by months:
```sql
SELECT to_char(order_date,'yyyy-MM') AS order_month, count(*) AS order_count FROM orders
GROUP BY 1
ORDER BY 1 ASC;
```
RESULT:
![[Pasted image 20231014195821.png]]