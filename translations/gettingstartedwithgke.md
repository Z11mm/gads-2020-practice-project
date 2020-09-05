# Google Cloud Fundamentals: Getting Started with GKE

In this lab, you create a Google Kubernetes Engine cluster containing several containers, each containing a web server. You place a load balancer in front of the cluster and view its contents.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Provision a Kubernetes cluster using Kubernetes Engine.__

2. __Deploy and manage Docker containers using kubectl.__

### Task 1: Sign in to the Google Cloud Platform (GCP) Console

For each lab, you get a new GCP project and set of resources for a fixed time at no cost.  

Type in this command `gcloud auth login` in Cloud Shell. A browser window opens with a dialog box. Paste in the lab credentials provided for authentication.

> *Note the name of your GCP project*

### Task 2: Confirm that needed APIs are enabled

Step 1.  
Get a list of services that you can enable in your project:
`gcloud services list --available` 

You will need to enable both of these APIs:  

* Kubernetes Engine API
* Container Registry API

> *If you don't see the API listed, that means you haven't been granted access to enable the API.*

Step 2.  
To enable the Kubernetes Engine API:  
`gcloud services enable container.googleapis.com --project <your project ID>`  

To enable the Container Registry API:  
`gcloud services enable containerregistry.googleapis.com --project <your project ID>`  

### Task 3: Start a Kubernetes Engine cluster

