# Translation code for Getting started with Cloud Storage and Cloud SQL

## Task 1: Sign in to Google Cloud Platform (GCP) Console
- Set Project ID
= gcloud set project (project ID)
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

  # Task 3: Create a Cloud Storage Bucket using gsutil command line
  
