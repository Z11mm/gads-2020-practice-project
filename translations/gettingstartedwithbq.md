# Google Cloud Fundamentals: Getting Started with BigQuery

In this lab, you load a web server log into a BigQuery table. After loading the data, you query it using the BigQuery web user interface and the BigQuery CLI.

BigQuery helps you perform interactive analysis of petabyte-scale databases, and it enables near-real time analysis of massive datasets. It offers a familiar SQL 2011 query language and functions.

Data stored in BigQuery is highly durable. Google stores your data in a replicated manner by default and at no additional charge for replicas. With BigQuery, you pay only for the resources you use. Data storage in BigQuery is inexpensive. Queries incur charges based on the amount of data they process: when you submit a query, you pay for the compute nodes only for the duration of that query. You don't have to pay to keep a compute cluster up and running.

Using BigQuery involves interacting with a number of Google Cloud Platform resources, including projects (covered elsewhere in this course), datasets, tables, and jobs. This lab introduces you to some of these resources, and this brief introduction summarizes their role in interacting with BigQuery.

Datasets: A dataset is a grouping mechanism that holds zero or more tables. A dataset is the lowest level unit of access control. Datasets are owned by GCP projects. Each dataset can be shared with individual users.

Tables: A table is a row-column structure that contains actual data. Each table has a schema that describes strongly typed columns of values. Each table belongs to a dataset.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Load data from Cloud Storage into BigQuery.__

2. __Perform a query on the data in BigQuery.__

### Task 1: Sign in to the Google Cloud Platform (GCP) Console

In Cloud Shell, type in the following command:  `gcloud auth login`.  
A browser window opens with a dialog box. Paste in the lab credentials provided for authentication.

### Task 2: Load data from Cloud Storage into BigQuery

Create a new dataset within your project using the following command:  
`bq --location=location mk \
--dataset \
--default_table_expiration integer1 \
--default_partition_expiration integer2 \
--description description \
project_id:dataset`