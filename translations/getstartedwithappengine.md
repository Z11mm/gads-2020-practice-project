# Google Cloud Fundamentals: Getting Started With App Engine

In this lab, you create and deploy a simple App Engine application using a virtual environment in the Google Cloud Shell.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Initialize App Engine.__

2. __Preview an App Engine application running locally in Cloud Shell.__

3. __Deploy an App Engine application, so that others can reach it.__

4. __Disable an App Engine application, when you no longer want it to be visible.__

> *You will activate Google Cloud Shell for this lab.  
In Cloud Shell, you can list the active account name with this command:  
`gcloud auth list`  
Output:  
`Credentialed accounts:`  
 `- google1623327_student@qwiklabs.net`  
You can list the project ID with this command:  
`gcloud config list project`  
Output:  
`[core]
project = qwiklabs-gcp-44776a13dea667a6`*

### Task 1: Initialize App Engine

Step 1.  
Initialize your App Engine app with your project and choose its region:  
`gcloud app create --project=$DEVSHELL_PROJECT_ID`  
> *When prompted, select the region where you want your App Engine application located. A region is specified in lab credentials.*

Step 2.  
Clone the source code repository for a sample application in the hello_world directory:  
`git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

Step 3.  
Navigate to the source directory:  
`cd python-docs-samples/appengine/standard_python3/hello_world`

### Task 2: Run Hello World application locally

> *In this task, you run the Hello World application in a local, virtual environment in Google Cloud Shell.*

Step 1.  
Execute the following command to download and update the packages list.  
`sudo apt-get update`  
