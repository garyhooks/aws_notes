# Summary

| Use Case    | Option |
| :-------- | ------- |
| Quick adhoc searches  | Athena    |
| Data Warehousing & Huge integrated, intensive and prolonged searches | Redshift     |
| Big Data | Amazon EMR with Hadoop |
| Business Intelligence | Amazon QuickSight | 

# Amazon Athena

* Serverless
* Designed to analyse data within S3 buckets
* Uses SQL language - although it is built on the Presto language
* Built on open-source frameworks
* Flexible way to analyse petabytes of data
* Can integrate with MachineLearning tools
* Supports formats including CSV, JSON, ORC, Avro and Parquet.
* Commonly used with **Amazon QuickSight** to create dashboards
* This link has a lot of the SQL code needed to analyse S3 access logs: https://docs.aws.amazon.com/AmazonS3/latest/userguide/using-s3-access-logs-to-identify-requests.html

#### Performance Improvements

* Use columnar data for cost savings (you only scan the columns you need)
    * Apache Parquet or ORC is best
    * Huge performance improvements
    * To get the files into the right format, use **Glue** to convert your data to Parquet or ORC
      
* File size:
    * Compress data so there is smaller retrievals
    * Use larger files to minimise overheads
      
* Partition datasets in S3 for easy quering on virtual columns - then you are not quering ALL data each time, for example:
    * S3://my-s3-bucket/flight/parquet/year=1991/month=1/day=23

#### Ingest Options - Federated Query

You can scan data anywhere using a Data Source Connector which uses **AWS Lambda** to run **Federated Queries**

1) ElastiCache
2) DynamoDB
3) Redshift
4) Aurora and other databases
5) Operational Databases
6) Data warehouses
7) Bigdata
8) ERP (Enterprise resource planning)
9) Other cloud services
10) Amazon S3

#### Use Cases

* Business intelligence
* VPC Flow Logs
* ELB Logs
* CloudTrail Logs
* Submit a single SQL query to search S3
* Use machine learning models in SQL queries to look for anomolies and sales prediction analysis

# Redshift

* Database and analytics engine
* Based on PostgreSQL but it is not used for OLTP (Online Transaction Processing)
* It's OLAP (Online Analytics Processing)
* 10x better performance than other data warehouses
* Columnar storage of data (rather than row based) so it is much quicker
* Pay only for based on instances provisioned
* Has an SQL interface
* BI Tools such as Amazon QuickSight or Tableau Integrate
* Faster than Athena with queries/joins/aggregations due to having **indexes**

#### Redshift Cluster

* Leader Node: for query planning and results aggregation
* Computer Node: for performing the queries and sending results to the leader

#### Snapshots and Disaster Recovery

* Multi-AZ for some clusters
* Snapshots can be used - only what has changed is saved
* You can restore the snapshot into a new cluster
* You can take these snapshots
    * Automated - every 8 hours or every 5gb
    * Manual
* You can configure Redshift to copy snapshots to other regions

#### Ingesting Data

1) Amazon Kinesis Data Firehouse - receiving data from different sources. This writes the data to an S3 bucket first, then Firehouse copies it from S3
2) S3 using COPY command using IAM role
3) EC2 Instance using JDBC driver

#### Redshift Spectrum

* Query data in S3 without loading it
* The query is completed by thousands of Redshift Spectrum nodes
* The bucket you want to query must be in the same region as your cluster 

# Amazon QuickSight

* Serverless
* Business Intelligence
* Allows analytics, creation of dashboards and reports
* SPICE Engine: In-memory computational engine
    * It only works if you **import data** into QuickSight
    * Does not work if it is just connected to another database
* Allows Column-Level Security (CLS) to restrict which columns are shown depending on user
* Can integrate with 3rd party services like SalesForce and Jira
* Can integrate with 3rd party databases such as on-presmises
* Import data sources such as CSV, Excel, JSON etc

# Amazon OpenSearch Service (Previously named ElasticSearch)

* In DynamoDB you can only query by Primary key or indexes
* But with OpenSearch, you can search ANY fields, even for partial matches
* Use OpenSearch to compliment another database
* Two modes:
    1) Managed Cluster
    2) Serverless Cluster - everything including scaling is handled by AWS
* Does not natively support SQL - but it can be enabled
* Ingestion is through Kinesis FIrehouse, IoT and Cloudwatch
* Security using Cognito & IAM, KMS  
  
![image](https://github.com/user-attachments/assets/1da093f1-0cd1-4262-9184-59923ef7a8b9)


# Amazon EMR (Elastic MapReduce)

* Helps create Hadoop Clusters (Big Data) to analyse huge amounts of data
* Clusters are made of hundreds of EC2 instances
* EMR comes bundled with Apache Spark, HBase, Presto, Apache Flink
* EMR takes care of all the setting up and configuration
* Allows autoscaling and spot instances
* Use Cases:
    * Data Processing
    * Machine Learning
    * Web Indexing
    * Big Data
* Master Node: manages health - long running
* Core Node: Run tasks and store data - long running
* Task Node: Just to run tasks - usually Spot

# AWS Glue

* Serverless
* ETL Service (Extract, Transform, Load)
* Moves data between stores
* Can create jobs to transfer the data and also transform it
* Automatically conducts schema detection which can automatically map the data
* Example: move S3 into Redshift Data Warehouse
  





