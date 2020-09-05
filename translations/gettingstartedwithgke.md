# Google Cloud Fundamentals: Getting Started with GKE

In this lab, you create a Google Kubernetes Engine cluster containing several containers, each containing a web server. You place a load balancer in front of the cluster and view its contents.

## Objectives

In this lab, you learn how to perform the following tasks:

1. __Provision a Kubernetes cluster using Kubernetes Engine.__

2. __Deploy and manage Docker containers using `kubectl`.__

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

Step 1.  
For convenience, place the zone that Qwiklabs assigned you to into an environment variable called MY_ZONE. Your complete command will look similar to this:  
`export MY_ZONE=us-central1-a`  

Step 2.  
Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster __webfrontend__ and configure it to run 2 nodes:  
`gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2`  
> *It takes several minutes to create a cluster as Kubernetes Engine provisions virtual machines for you.*  

Step 3.  
After the cluster is created, check your installed version of Kubernetes using the kubectl version command:  
`kubectl version`  
> *The `gcloud container clusters create` command automatically authenticated `kubectl` for you.*  
>
> You may need to install `kubectl` by running the following command:  
`gcloud components install kubectl`  

### Task 4: Run and deploy a container

Step 1.  
From your Cloud Shell prompt, launch a single instance of the nginx container(Nginx is a popular web server):  
`kubectl create deploy nginx --image=nginx:1.17.10`  

> *In Kubernetes, all containers run in pods. This use of the `kubectl create` command caused Kubernetes to create a deployment consisting of a single pod containing the nginx container. A Kubernetes deployment keeps a given number of pods up and running even in the event of failures among the nodes on which they run. In this command, you launched the default number of pods, which is 1.*

Step 2.  
View the pod running the nginx container:  
`kubectl get pods`

Step 3.  
Expose the nginx container to the Internet:  
`kubectl expose deployment nginx --port 80 --type LoadBalancer`

> *Kubernetes created a service and an external load balancer with a public IP address attached to it. The IP address remains the same for the life of the service. Any network traffic to that public IP address is routed to pods behind the service: in this case, the nginx pod.*

Step 4.  
View the new service:  
`kubectl get services`  

> *You can use the displayed external IP address to test and contact the nginx container remotely.*
>
> *It may take a few seconds before the __External-IP__ field is populated for your service. This is normal. Just re-run the kubectl get services command every few seconds until the field is populated.*

Step 5.  
Open a new web browser tab and paste your cluster's external IP address into the address bar. The default home page of the Nginx browser is displayed.


