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
> *When prompted, select the region where you want your App Engine application located. A region is specified in the lab credentials.*

Step 2.  
Clone the source code repository for a sample application in the hello_world directory:  
`git clone https://github.com/GoogleCloudPlatform/python-docs-samples`

Step 3.  
Navigate to the source directory:  
`cd python-docs-samples/appengine/standard_python3/hello_world`

### Task 2: Run Hello World application locally

> *In this task, you run the Hello World application in a local, virtual environment in Google Cloud Shell.*

Step 1.  
Execute the following command to download and update the packages list:  
`sudo apt-get update`  

Step 2.  
Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system:  
`sudo apt-get install virtualenv`  
> *If prompted [Y/n], press Y and then `Enter`.*    
Then,  
`virtualenv -p python3 venv`  

Step 3.  
Activate the virtual environment:   
`source venv/bin/activate`  

Step 4.  
Navigate to your project directory and install dependencies:   
`pip install  -r requirements.txt`  

Step 5.  
Run the application:  
`python main.py`

Step 6.  
To end the test, press `Ctrl+C` to abort the deployed service.

### Task 3: Deploy and run Hello World on App Engine 

To deploy your application to the App Engine Standard environment:  

Step 1.  
Navigate to the source directory:  
`cd ~/python-docs-samples/appengine/standard_python3/hello_world`  

Step 2.  
Deploy your Hello World application:  
`gcloud app deploy`  
> *If prompted "Do you want to continue (Y/n)?", press Y and then `Enter`.*  
> *This `app deploy` command uses the __app.yaml__ file to identify project configuration.*  

Step 3.  
Launch your browser to view the app at http://YOUR_PROJECT_ID.appspot.com:  
`gcloud app browse`  

Step 4.  
App Engine offers no option to __undeploy__ an application. After an application is deployed, it remains deployed. However, you can disable the application in the Cloud Console, which causes it to no longer be accessible to users.  

__End of lab!__