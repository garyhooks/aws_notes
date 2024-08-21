# Summary

| Use Case    | Option |
| :-------- | ------- |
| Quick adhoc searches  | Athena    |
| Huge integrated, intensive and prolonged searches | Redshift     |



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


# QuickSight

* Serverless 
* Integrates with BI (Business Intelligence)
* Allows analytics, creation of dashboards and reports
