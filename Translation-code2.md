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
- To create network under connections
= gcloud sql network create web-front-end --authorized-network=(network address)/32

## Task 5: Configure an application in a Compute Engine instance to use Cloud SQL
- To SSH into SQL bloghost
= SSH bloghost
- To change work directory 
= cd /var/www/html
- To edit work file 
= sudo nano index.php
- Instruction: copy and paste the below lines of code in work fille
=<html>
<head><title>Welcome to my excellent blog</title></head>
<body>
<h1>Welcome to my excellent blog</h1>
<?php
 $dbserver = "CLOUDSQLIP";
$dbuser = "blogdbuser";
$dbpassword = "DBPASSWORD";
// In a production blog, we would not store the MySQL
// password in the document root. Instead, we would store it in a
// configuration file elsewhere on the web server VM instance.

$conn = new mysqli($dbserver, $dbuser, $dbpassword);

if (mysqli_connect_error()) {
        echo ("Database connection failed: " . mysqli_connect_error());
} else {
        echo ("Database connection succeeded.");
}
?>
</body></html>
- Click Ctrl+O then press enter
- Click Ctrl+x to exit nano editor
- To restart web server
= sudo service apache2 restart

## Task 6: Configure an application in a Compute Engine instance to use a Cloud Storage object
- Copy public URL link for object
- SSH bloghost
- To change directory
= cd /var/www/html
- To edit work file
= sudo nano index.php
- Edit h1 element
- Paste this HTML markup immediately before the URL: <img src='
- Place a closing single quotation mark and a closing angle bracket at the end of the URL: '>
- Result should look thus : <img src='https://storage.googleapis.com/qwiklabs-gcp-0005e186fa559a09/my-excellent-blog.png'>
- Press Ctrl+O and press enter
- Press Ctrl+X to exit the editor
- To restart web server
= sudo service apache2 restart



