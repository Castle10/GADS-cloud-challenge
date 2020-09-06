# Translation code for Getting started with Cloud Storage and Cloud SQL

## Task 1: Logon

## Task 2: Sign in to Google Cloud Platform (GCP) Console
- Set Project ID
= gcloud config set project (project ID)
- To set region
= gcloud compute zones list | grep us-central1
- To set Zone
= gcloud config set compute/zone us-central1-a
- To configure VM
= gcloud compute instances create "bloghost" --machine-type "e2-medium" 
- To configure firewall
= network-tier=PREMIUM
- To configure startup script
= metadata=startup-script=apt-get\ update$'\n'apt-get\ install\ apache2\ php\ php-mysql\ -y$'\n'service\ apache2\ restart

- CMD line
= gcloud beta compute --project=qwiklabs-gcp-02-b478afec7251 instances create bloghost --zone=us-central1-a --machine-type=e2-medium --subnet=default --network-tier=PREMIUM --metadata=startup-script=apt-get\ update$'\n'apt-get\ install\ apache2\ php\ php-mysql\ -y$'\n'service\ apache2\ restart

## Task 3: Create a Cloud Storage Bucket using gsutil command line
- To set perferred location
= export LOCATION=US
- To set enviroment project ID
= gsutil mb -l $LOCATION gs://$DEVSHELL_PROJECT_ID
- To Retrieve a banner image
= gsutil cp gs://cloud-training/gcpfci/my-excellent-blog.png my-excellent-blog.png
- To Copy the banner image to your newly created Cloud Storage bucket
= gsutil cp my-excellent-blog.png gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png
- To Modify the Access Control List
= gsutil acl ch -u allUsers:R gs://$DEVSHELL_PROJECT_ID/my-excellent-blog.png

## Task 4: Create cloud sql instance
- To create SQL instance
= gcloud sql instances create blog-db --root-password=password --region=us-central1
(copy IP address to clipboard)
- To create user for the sql instance
= gcloud sql users create blogdbuser --instance=blog-db --password=password

