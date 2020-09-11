# Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives

1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

2. Create a Compute Engine virtual machine using the gcloud command-line interface.

## Step 1

1. Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    gcloud compute instances create "my-vm-1" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default" --tags http

    gcloud compute firewall-rules create allow-http --action=ALLOW --direction=INGRESS --rules=tcp:80 --target-tags=http

2. Create a Compute Engine virtual machine using the gcloud command-line interface.

   gcloud config set compute/zone us-central1-b
   
   gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" --image "debian-9-stretch-v20190213" --subnet "default" 


3. Connect between two instances

   a) Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:

   - Connect to my-vm-2

       gcloud compute ssh my-vm-2

   - Ping my-vm-1 from my-vm-2

       ping my-vm-1

   b) Use the ssh command to open a command prompt on my-vm-1 from my-vm-2

      ssh my-vm-1

   c) At the command prompt on my-vm-1, install the Nginx web server:

      sudo apt-get install nginx-light -y
   
   d) Use the nano text editor to add a custom message to the home page of the web server:
      
      sudo nano /var/www/html/index.nginx-debian.html

   e) Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:

      Hi from Henry

   f) Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.

   g) Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:

        curl http://localhost/

   h) The response will be the HTML source of the web server's home page, including your line of custom text.

        exit
     
    You will return to the command prompt on my-vm-2

   i) To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:
    
      curl http://my-vm-1/s


