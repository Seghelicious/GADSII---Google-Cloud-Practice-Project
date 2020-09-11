# Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives

#### At the end of this lab, I would be able to

- Create a Compute Engine virtual machine using the Google Cloud Platform (GCP)
  Console.
- Create a Compute Engine virtual machine using the gcloud command-line
  interface.
- Connect between the two instances.

### Steps

#### 1. Create a Virtual Machine using the Google Cloud Platform (Google Cloud Shell).

I activated the Google Cloud Shell 
###### I set the default zone 
        gcloud config set compute/zone us-central1-f

###### I created Virtual Machines via command line
        gcloud compute instances create my-vm-1 --machine-type "n1-standard-1" --image-project "debian-cloud" 
        --image "debian-9-stretch-v20200911" --subnet "default" --tags http

###### I allowed a HTTP traffic to permit my-vm-1 to connect to  the home page of the web server. I also allowed a firewall rule to allow incoming connections to from my-vm-1 instances based on the specified configuration. 
        gcloud compute firewall-rules create  allow-http --action=ALLOW --destination=INGRESS --rules=http:80 
        --target-tags=http

#### 2. Create a Virtual Machine using the Google Cloud Command Line.
         gcloud compute instances create my-vm-2 --machine-type "n1-standard-1" --image-project "debian-cloud" 
        --image "debian-9-stretch-v20200911" --subnet "default"

#### 3. Connect between the two instances.
###### I used the ping command to check that the two vms can connect to each other on the network.
###### Connect to my-vm-2
          gcloud compute ssh my-vm-2
###### Ping my-vm-1 from my-vm-2  # Pings my-vm-1 twice
          ping -c 2 my-vm-1

###### I was prompted about whether to continue connecting to a host with unknown authenticity, I entered yes to confirm that I did.

###### On the my-vm-1 command prompt, I installed the Nginx web server.
          sudo apt-get install nginx-light -y

###### I used the nano text editor to add a custom message to the home page of the web server.
          sudo nano /var/www/html/index.nginx-debian.html

###### I used the arrow keys to move the cursor to the line just below the h1 header. I added the text *Hi, Seghelicious*
          Hi, Seghelicious...

###### I used *Ctrl+O* and *Enter*, to save the edited file, and then *Ctrl+X* to exit the nano text editor.

###### To confirm that the web server is serving my new page. I executed this command.
          curl http://localhost/

###### My custom text will now be viewed on the HTML source of the web server's home page. 
###### To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, I executed the following command.
          curl http://my-vm-1/

###### I exited the command prompt on my-vm-1 and my-vm-2.
          exit

