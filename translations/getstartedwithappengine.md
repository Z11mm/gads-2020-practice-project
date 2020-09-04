# Google Cloud Fundamentals: Getting Started With App Engine

In this lab, you create and deploy a simple App Engine application using a virtual environment in the Google Cloud Shell.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Initialize App Engine.__

2. __Preview an App Engine application running locally in Cloud Shell.__

3. __Deploy an App Engine application, so that others can reach it.__

4. __Disable an App Engine application, when you no longer want it to be visible.__

> *You will need to have the Google Cloud SDK downloaded and installed on your machine. 
To set up your development environment, type in the command `gcloud init` and follow the prompts.  
You will need your project ID for this lab. Use the command `gcloud config project list` to retrieve your project ID.    
Then, save it as an environment variable with this command `export DEVSHELL_PROJECT_ID=<your project ID>`*

### Task 1: Initialize App Engine

Step 1.  
Initialize your App Engine app with your project and choose its region:  
`gcloud app create --project=$DEVSHELL_PROJECT_ID`  
> *When prompted, select the region where you want your App Engine application located.*

Step 2.  
Clone the source code repository for a sample application in the hello_world directory:  
`git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

Step 3.  
Navigate to the source directory:  
`cd python-docs-samples/appengine/standard_python3/hello_world`