# Translation code for Getting started with Compute engine

# Task 1: Sign in to GCP console

## Task 2: Create a virtual machine 
- To set project ID 
= gcloud set project (project Id)
- To set region
= gcloud compute zones list | grep us-central1
- To set Zone
= gcloud config set compute/zone us-central1-a
- To configure VM
= gcloud compute instances create "my-vm-1" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default"

## Task 3: Create a virtual machine using the gcloud command line
- To set region
= gcloud compute zones list | grep us-central1
- To set Zone
= gcloud config set compute/zone us-central1-b
- To create a VM Instance called my-vm-2
= gcloud compute instances create "my-vm-2" \
--machine-type "n1-standard-1" \
--image-project "debian-cloud" \
--image "debian-9-stretch-v20190213" \
--subnet "default"

## Task 4: Connect between VM instance 
- To ping my-vm-1 from my-vm-2
= ssh my-vm-2
= ping my-vm-1
- To install ngnix server on my-vm-1
= sudo apt-get install nginx-light -y
- To add custom message
= sudo nano /var/www/html/index.nginx-debian.html
- To confirm web server is working 
= curl http://localhost/
- To confirm my-vm-2 can reach web server on my-vm-1
= curl http://my-vm-1/

