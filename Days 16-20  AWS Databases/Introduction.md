# What is a database?
A **database** is a logically organized collection of information designed in such a way that the information can be accessed for later use by a computer program.

## Types of databases
- Relational databases - Ideal for structured data
- Non-relational databases - Ideal for unstructured and/or semi-structured data

| Relational databases | Non-relational databases|
|----------------------|-------------------------|
| - Data records are organized in a set of tables and rows |- Stores data in unstructured ways using key-value pairs, documents or graphs |
| - Each row holds info about a record and columns contain attributes of the data|- A row does not contain data for each column. Non-relational databases scale out horizontally |
| - Each row has an identifier column to uniquely distinguish the record from other records. The value in the identifier column is called a **primary key**|- Was designed to overcome the limitations of relational databases for handling demands of variable structured data |

## Use cases
### Relational databases



## Non-relational databases
- Providing a personalized customer experience. Each customer has different habits, preferences, and desires.


# AWS Databases
There are several types of databases offered by AWS depending on the customer's needs. Examples include:
- Relational databases e.g. **Amazon RDS, Amazon Aurora, Amazon Redshift**
- Key-value databases e.g. **Amazon DynamoDB**
- Document databases e.g. **Amazon DocumentDB**
- Timestream databases e.g. **Amazon Timestream**
- In-memory databases e.g. **Amazon ElastiCache**
- Graph databases e.g. **Amazon Neptune**
- Ledger databases e.g. **Amazon Quantum Ledger Database (QLDB)**
- Keyspaces databases e.g. **Amazon Keyspaces**\


The main and most common type is the **Amazon Relational Database (AWS RDS)**

# Amazon RDS
It is a fully managed relational database service.\
There are 6 database engines to choose from:
- SQL Server
- Oracle
- PostgreSQL
- MySQL
- MariaDB
- Amazon Aurora

## Benefits
- Easy to administer
- Available and durable
- Highly scalable
- Fast in terms of performance
- Secure
- Inexpensive

## High availability in Amazon RDS
This is achieved by enabling Amazon RDS Muti-AZ.

For redundancy, Amazon RDS creates a secondary copy of your database in another AZ. Amazon RDS uses the secondary copy of the database as a standby in case the primary fails.

If that occurs, the standby database is automatically set as the primary database, and then either creates another standby database instance or demotes the previous primary DB to standby DB to keep the Multi-AZ configuration active.

### Benefits of multi-AZ deployments
- Enhanced durability
- Increased availability
- No administrative intervention

## Amazon RDS Read Replicas
A read replica is a special type of database instance created from a source database instance.

Updates made to a source DB are asynchronously copied to the Read replica instance. This gives you the option of reducing the load on your source DB by routing the read queries to your RR instance.

RR can also be manually promoted when needed to become stand-alone DB instances.

![Amazon RDS read replicas simple model](https://github.com/achenchi7/AWS-Projects-2023-2024/blob/main/images/Amazon%20RDS%20Read%20replicas%20(1).png)

## Use cases for Amazon RDS
**1. Read heavy OLTP application**\
In this online transaction processing (OLTP)application, Amazon RDS is used with a read replica, which is asynchronously updated.


