# devopsProjects2023
# Psuedo Code Just to show the quality and structure of Code Layout used
# Codes Most Proud Of

<details>
  <summary>Click here to expand</summary>
  
  This content is hidden until you click the summary above.
</details>  

===============================================================
Docker-Jenkins-K8 integration
===============================================================

dockJk.sh-------------------------------------
#!/bin/bash
<<Guide
"Author: NoioLeo Date:02/17/2023
Below is Shell Script to automate
Docekr-Jenkins Integration set up
You require Sudo access to run Script"
Guide
sudo apt update -y
#installing dependencies
sudo apt install docker.io nano wget zip unzip git tar apache2 firewalld nginx vim nano tree net-tools -y
sudo apt-get install fontconfig openjdk-11-jre -y
sudo systemctl enable firewalld
sudo systemctl start firewalld
sudo systemctl status firewalld
sudo firewall-cmd --add-port={80/tcp,443/tcp,22/tcp,8080/tcp,8081/tcp,9000/tcp} --permanent
sudo firewall-cmd --zone=docker --add-port={80/tcp,443/tcp,22/tcp,8080/tcp,8081/tcp,9000/tcp} --permanent
sudo firewall-cmd --reload
sudo firewall-cmd --zone=docker --list-all
#installing docker
sudo systemctl start docker
sudo systemctl enable docker.service
#installing Jenkins
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /etc/apt/trusted.gpg.d/jenkins.io.asc
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
#Atlernative below
#curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
#echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
sudo usermod -aG docker jenkins
sudo usermod -aG sudo jenkins
sudo usermod -aG ubuntu jenkins
systemctl restart docker.service
sudo echo "jenkins ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins
sudo chown -R jenkins:docker /var/run/docker/
sudo chown jenkins /var/run/docker.sock
===========================================


Create IAM role --> Instances --> select Docker-Jenkins server --> Actions --> Security --> modify IAM --> Create Role
                --> use AWS services -->AmazonEC2FullAccess 
                                        AmazonS3FullAccess
                                        IAMFullAccess 
                                        AmazonVPCFullAccess
                                        AmazonRoute53FullAccess
                --> name policy, save role --> select Role for Server --> update IAM role





===========================================

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
