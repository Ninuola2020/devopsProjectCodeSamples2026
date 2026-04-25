# devopsProjects2023

# Code Mos Proud of

---------------------------------------------------------
Terraform
---------------------------------------------------------
Creates State file - Stores state of Architecture

1. Install Terrform CLI (binary)
2. AWS CLI  ---> C:\Users\ninuo\.aws
3. Editor
4. Hashicorp Terraform plugin 

terra.sh-------------------------------------
#!/bin/bash
<<Guide
"Author: NoioLeo Date:02/17/2023
Below is Shell Script to automate
Terraform-Ansible-K8 Integration set up
You require Sudo access to run Script"
Guide
sudo yum update -y
sudo yum install nano wget zip unzip git tar apache2 firewalld nginx vim nano tree net-tools curl sudo apt-get install fontconfig openjdk-11-jre -y -y
curl https://s3.amazonaws.com/aws-cli/awscli-bundle.zip -o awscli-bundle.zip
sudo unzip awscli-bundle.zip
sudo ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
#use code below incase code line above does not work
#sudo apt install awscli
----------------------------------------------------------------


---------------------------------------------------------
Ngrok Private access to local Unit for Testing
---------------------------------------------------------

 GitHub will notify jenkins to trigger bill once there is a change in SCM
   http://192.168.86.131:8080/github-webhook/

   local system Setup:
   choco install ngrok -y
   ngrok http localIpAddress:8080
   open link given in CMD
   register/log in Ngrok
   run provided code on log in page after verification
   ngrok http localIpAddress:8080
   https://8894-108-218-29-105.ngrok.io/github-webhook/
   got to project Reppo-->settings --> webhook --> add webhook --> save
