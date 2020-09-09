# Google Cloud Fundamentals: Getting Started with BigQuery

In this lab, you load a web server log into a BigQuery table. After loading the data, you query it using the BigQuery web user interface and the BigQuery CLI.

BigQuery helps you perform interactive analysis of petabyte-scale databases, and it enables near-real time analysis of massive datasets. It offers a familiar SQL 2011 query language and functions.

Data stored in BigQuery is highly durable. Google stores your data in a replicated manner by default and at no additional charge for replicas. With BigQuery, you pay only for the resources you use. Data storage in BigQuery is inexpensive. Queries incur charges based on the amount of data they process: when you submit a query, you pay for the compute nodes only for the duration of that query. You don't have to pay to keep a compute cluster up and running.

Using BigQuery involves interacting with a number of Google Cloud Platform resources, including projects (covered elsewhere in this course), datasets, tables, and jobs. This lab introduces you to some of these resources, and this brief introduction summarizes their role in interacting with BigQuery.

__Datasets__: A dataset is a grouping mechanism that holds zero or more tables. A dataset is the lowest level unit of access control. Datasets are owned by GCP projects. Each dataset can be shared with individual users.

__Tables__: A table is a row-column structure that contains actual data. Each table has a schema that describes strongly typed columns of values. Each table belongs to a dataset.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Load data from Cloud Storage into BigQuery.__

2. __Perform a query on the data in BigQuery.__

### Task 1: Sign in to the Google Cloud Platform (GCP) Console

In Cloud Shell, type in the following command:  `gcloud auth login`.  
A browser window opens with a dialog box. Paste in the lab credentials provided for authentication.

### Task 2: Load data from Cloud Storage into BigQuery

Step 1.  
Create a new dataset within your project.  
For __Dataset ID__, type __logdata__.  
For __Data location__, select the continent closest to the region your project was created in.  
Use the following command:  
`bq --location=US mk \
logdata \
<project_id>`

Step 2.  
Create a new table in the __logdata__ called __accesslog__ to store the data from a CSV file stored in Cloud Storage. Use the following command:  
`bq load --autodetect --source_format=CSV logdata.accesslog gs://cloud-training/gcpfci/access_log.csv`

> To create a Cloud Storage bucket and upload the CSV file, use the following command: `gsutil mb gs://<BUCKET_NAME>` to make a bucket.
> To upload an object, i.e, the CSV file, into the bucket, use the command:  
`gsutil cp <OBJECT_LOCATION> gs://<DESTINATION_BUCKET_NAME>`  
where:  
OBJECT_LOCATION is the local path to your object. For example, Desktop/dog.png  
DESTINATION_BUCKET_NAME is the name of the bucket to which you are uploading your object.

### Task 3: Perform a query on the data using the BigQuery web UI

Step 1.  
In this section of the lab, you use the BigQuery web UI to query the accesslog table you created previously. Type the following query:  
`bq query "select int64_field_6 as hour, count(*) as hitcount from logdata.accesslog group by hour order by hour"`

> Because you told BigQuery to automatically discover the schema when you load the data, the hour of the day during which each web hit arrived is in a field called `int_field_6`.

Step 2.  
Click __Enter__ and examine the results. At what time of day is the website busiest? When is it least busy?

### Task 4: Perform a query on the data using the bq command

Step 1.  
In the Cloud Shell, enter this command:  
`bq query "select string_field_10 as request, count(*) as requestcount from logdata.accesslog group by request order by requestcount desc"`

> The first time you use the `bq` command, it caches your Google Cloud Platform credentials, and then asks you to choose your default project. Choose the project that Qwiklabs assigned you to. Its name will look like __qwiklabs-gcp-__ followed by a hexadecimal number.

The `bq` command then performs the action requested on its command line. What URL offered by this web server was most popular? Which was least popular?

__End of lab!__