# Learning to use cloud platform

This exercise will involve creating a docker container and running it on the Google Cloud 
platform. 


## Google Cloud Credits To run VMs in the cloud

Here is the URL you will need to access in order to request a Google Cloud Platform coupon. 
You will be asked to provide your school email address and name. 
An email will be sent to you to confirm these details before a coupon is sent to you.


[Student Coupon Retrieval Link](https://google.secure.force.com/GCPEDU?cid=wkablVi4ye8beTcVSjzdiH6MmoNQS0RQLO%2B5YWiZ5yzuuPIiCcdZqqX8jFZpaeNk)

[New Student Coupon Retrieval Link](https://google.secure.force.com/GCPEDU?cid=6UK0SVDHVgFQhMNdwnvSzPD%2FUxkqG96OL3od9Enf8%2FAJtVZIkPatzhH4ass%2FPEjQ)

You will be asked for a name and email address, which needs to match the domain. A confirmation email will be sent to you with a coupon code.

You can request a coupon from the URL and redeem it until: 5/8/2020

Coupon valid through: 1/8/2021

You can only request ONE code per unique email address.

GCP requires projects to be linked to a billing account. If you plan to use GCP for your project, you might want to redeem all credits on a single account and add other members of the same team to that project. 

# Assignment 1: Deploying a webserver 

The purpose of the assignment is to familiarize you with the automatic build, containers, and cloud computing

## The due date is Feb 15.

1. Create repo yougithubid/webserver
2. Add Dockerfile, for example as the one in this repo
3. Add index.html with your name in it
4. Create automatic build

       i. on hub.docker.com create id for yourself (if you have not done so before)
       ii. create automated build (pull out from the top menu)
       iii. connect to github repo you have just created
5. make a change on the github repo (to trigger build)
6. Verify that the build succeeded https://hub.docker.com/r/yourdockerhubid/webserver/builds/
7. Create a virual machine on GCP

       i. go to https://console.cloud.google.com/compute/instances select the class project and click on craete instance
       ii. Next to memory click customize and reduce 1G
       iii. Mark checkmark "Deploy a container image to this VM" and enter image 'yourdockerhubid/webserver'
       iv. Mark checkmark "Allow HTTP traffic"
       v. expand "Management, disks, networking, SSH keys"
       vi. in the "startup script" box enter    
```    
#!/bin/bash
docker rm ws
docker run -d --name ws -p80:80 yourdockerhubid/webserver
```
8. Click "Create" button at the bottom
9. Check if the webserver works
       
         i. enter the external ip adress (for the machine you created) in your browser (you should get your name)
         ii. If that does not work connect to the machine
         iii. Open shell
         iv. type gcloud compute ssh "your instance name"
         v. once connected to your instance type 'docker ps': your container should be running
10. Enter ip adress of the machine at the bottom of your netid.md file in the cs340-20/students repo and create a pull request
         
