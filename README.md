# devopsProjects2023
# Psuedo Code Just to show the quality and structure of Code Layout used
# Codes Most Proud Of

<details>
  <summary> Click Block Below To See Code Sample<br>
===============================================================<br>
Docker-Jenkins-K8 integration<br>
===============================================================
  </summary>
  
dockJk.sh-------------------------------------<br>
#!/bin/bash<br>
<<Guide<br>
"Author: NoioLeo Date:02/17/2023<br>
Below is Shell Script to automate<br>
Docekr-Jenkins Integration set up<br>
You require Sudo access to run Script"<br>
Guide<br>
sudo apt update -y<br>
#installing dependencies<br>
sudo apt install docker.io nano wget zip unzip git tar apache2 firewalld nginx vim nano tree net-tools -y<br>
sudo apt-get install fontconfig openjdk-11-jre -y<br>
sudo systemctl enable firewalld<br>
sudo systemctl start firewalld<br>
sudo systemctl status firewalld<br>
sudo firewall-cmd --add-port={80/tcp,443/tcp,22/tcp,8080/tcp,8081/tcp,9000/tcp} --permanent<br>
sudo firewall-cmd --zone=docker --add-port={80/tcp,443/tcp,22/tcp,8080/tcp,8081/tcp,9000/tcp} --permanent<br>
sudo firewall-cmd --reload<br>
sudo firewall-cmd --zone=docker --list-all<br>
#installing docker<br>
sudo systemctl start docker<br>
sudo systemctl enable docker.service<br>
#installing Jenkins<br>
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /etc/apt/trusted.gpg.d/jenkins.io.asc<br>
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'<br>
#Atlernative below<br>
#curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null<br>
#echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null<br>
sudo apt-get update<br>
sudo apt-get install jenkins<br>
sudo systemctl start jenkins<br>
sudo systemctl status jenkins<br>
sudo usermod -aG docker jenkins<br>
sudo usermod -aG sudo jenkins<br>
sudo usermod -aG ubuntu jenkins<br>
systemctl restart docker.service<br>
sudo echo "jenkins ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins<br>
sudo chown -R jenkins:docker /var/run/docker/<br>
sudo chown jenkins /var/run/docker.sock<br>
===========================================<br>


Create IAM role --> Instances --> select Docker-Jenkins server --> Actions --> Security --> modify IAM --> Create Role<br>
                --> use AWS services -->AmazonEC2FullAccess<br> 
                                        AmazonS3FullAccess<br>
                                        IAMFullAccess<br> 
                                        AmazonVPCFullAccess<br>
                                        AmazonRoute53FullAccess<br>
                --> name policy, save role --> select Role for Server --> update IAM role<br>





===========================================

 
</details>  




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
