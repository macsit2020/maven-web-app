# maven-web-app

====================
Docker is a software use to create docker images and run  containerized  apps. 

Docker is used by Developers, Administrator and others to build 
    and run applications as containers.

We maintain a minimun of 3 ENVIRONMENTS = 
   dev ---> 
   stage/testing  -->
   production --> 

  dev branch --> developed -- build -- tested (Unit Testing) --> deploy (TomcatServer - VM)
       running well 
  QA branch --> developed -- build -- tested (add Testing) --> deploy (VM) 
        running well
  Stage branch --> developed -- build -- tested (add Testing) --> deploy (VM)
         NOT running well
  
  virtualisation :
     VM 
  Containerization:     VM 

We maintain a minimun of 3 ENVIRONMENTS = 
    dev branch    --> dev                   =  it is working   
    stage branch  --> staging/UAT/TESTING   =  it is working 
    master branch --> production            =  it is not working 

   virtual machine = ec2 instance 
    tomcat 

 Tomcat 
    patching 
    installation

    scp app.war tomcat@tomcat/webapps/app.war 

  app.war
     tomcat
     java

 --> image ---> contianer 

docker image = app + dependencies 
               app.war + tomcat 
               myapp.jar + java
               app.ear + Jboss

 With containerisation applications will run seamlessly in any ENVIRONMENT

Docker Editions:
    Docker CE --> Comunity Edition --> Open Source (Free)
    Docker EE --> Enterprise Edition --> Commercial

Type: Containerization
Vendor: Docker INC

O.S --> Cross Platform (Docker can be installed in any O.S)

Assignment---> Install docker desktop in your personal computer

    Docker Can Be Installed in Linux, Windows OS, mac OS, etc.  

Docker CE Can be installed in Most of the linux distribution except redhat.
         ubuntu /  centos / Amazon Linux

Docker EE can installed in all O.S including redhat.

Docker CE --> OpenSouce Free

Docker EE --> Commerical :
   DTR --> Docker Trusted Registry(Private Repo to keep docker images)
   UCP --> Universal Control Plane --> It's GUI for managing Docker Machines

Containerzation Platforms/Softwares.     :
    Docker,  = 80%
    CoreOS,  = 10%
    Rocket --= 10%

e-commerce:
  ebay --
   register
   login
   create cart 
   payment
   order

Jenkinsfile    --> pipeline script 

Dockerfile     --> It's a list of instructions used 
                   It's a file used to create docker images.

Docker Image  --> It's a package containing
    application Code e.g ebay.war, paypal.war 
       and
    All it's dependencies (Softwares, ENV Vars ..etc)

   mvn package = 
     app.war = docker iamge = app.war + tomcat/java   
     app.ear = docker image = app.ear + JBOSS/java
     app.jar = docker image = app.jar + java  

   image  = 

Docker Container--> It's a runtime instance of a docker image
                    where our application is running.

     The standard unit where the application service is deployed or running.

 GitHub / Nexus  

  Code are managed by SCM = GitHub 
  Packages (app.war) are uploaded and managed in Nexus 
  Docker images are stored and/or managed in dockerhub  

Docker Repo/Registry. --> We can store and share docker images.   

    Public Repo --> Docker hub 
       is It is generally a public repo. 
      Which contains all the open source softwares as  a docker images. 
       We can think of docker hub as play store for docker images.

    Private Repo (ECR, Nexus, JFrog, D.T.R(Docker Trusted Registory)) --> 
            We can store and share the docker images with in our company
        network using private repos
  

 PaaS  = 
 IaaS  = EC2
 SaaS  = DockerHub, New Relic, GitHub, SonarCloud

Docker Engine/Daemon/Host --> It's a software or program which we can 
                               create images & RUN contianers.

Docker is cross platform.

Docker CE
   Docker CE will not be supported by Redhat.
   
Docker EE
  Docker EE will be support most of the os including redhat.

      
First Create Account in docker hub
https://hub.docker.com

  
What is docker hub?
It's a public repository for docker images. You can think as play store for
docker images.

Install Docker on AWS Ubuntu:
ssh -i "devopskey.pem" ubuntu@ec2-3-80-26-218.compute-1.amazonaws.com
ssh -i devopskey.pem ubuntu@3.80.26.218

############################
#!/bin/bash
Ubuntu Server 18.04 LTS (HVM),
sudo hostname docker
sudo apt update -y 
sudo apt install docker.io -y
sudo usermod -aG docker ubuntu 
===================================

ssh -i "cicd.pem" ubuntu@ec2-18-209-168-14.compute-1.amazonaws.com

ssh -i "cicd.pem" ubuntu@18.209.168.14

  We created ubuntu server
  We installed docker using user-data (Script)
  The default user for ec2 ubuntu server is ubuntu 

sudo -i
echo "jenkins  ALL=(ALL) NOPASSWD:ALL" | sudo tee /etc/sudoers.d/jenkins 
cat /etc/passwd
sudo su - jenkins

sudo apt update -y 
sudo apt install docker.io -y
sudo usermod -aG docker jenkins 
sudo usermod -aG docker ubuntu 

 = User user-data 
NB: apt and apt-get are package managers for ubuntu servers 

sudo docker info

ssh -i "cicd.pem" ubuntu@ec2-54-196-212-249.compute-1.amazonaws.com

ssh -i "cicd.pem" ubuntu@54.196.212.249

https://github.com/LandmakTechnology/maven-web-app/blob/master/ansible-setup

# Check docker is installed or not
   docker info
   docker --version

=# You will get permison denied error as regular user 
    dosn't have permisions to execute docker commands.Add user to docker group.

sudo usermod -aG docker $USER 
or 
sudo usermod -aG docker ubuntu

sudo usermod -aG docker simon

# Exit From Current SSH Terminal & SSH(Login) again.Then execute 
docker ps

Install Docker on AWS RHEL
############################
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo dnf install docker-ce-3:18.09.1-3.el7 -y
sudo systemctl enable docker
sudo systemctl start docker
sudo docker info
adduser simon

# Check docker is installed or not
docker info
##
sudo apt update
sudo apt install openjdk-11-jdk
Confirm installation:
sudo apt install openjdk-11-jdk
checking installation:
java -version
###########
install jenkis in ubuntu:

wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
    /etc/apt/sources.list.d/jenkins.list'
sudo apt-get update
sudo apt-get install jenkins

# You will get permison denied error as regular user dosn't have permisions to execute docker commands.Add user to docker group.

sudo usermod -aG docker $simon 
sudo usermod -aG docker ec2-user

# Exit From Current SSH Terminal & SSH(Login) again .Then execute 
docker ps

Amazon Linux 2
================
sudo yum update -y		
sudo yum install docker -y
sudo systemctl start docker

Add Regural user to dockergroup
sudo usermod -aG docker  <username>

ex:
sudo usermod -aG docker ec2-user

Once you add user to group exit from the server and login again.
# Get docker information
docker info

=#Install Docker in Linux (Works for most of linux flavors).

sudo curl -fsSL get.docker.com | /bin/bash
done with installation of docker 

  curl ifconfig.co 

Docker Home/Working Dir: 
/var/lib/docker

All examples provided here work in RHEL

  git fetch/status/add/commit/push/merge/

docker comes with a cli --- docker 

Docker commands 
  docker build = create an image from a Dockerfile
     docker build -t mylandmarktech/maven-web-app . 
  docker images  = list images
  docker create = create a docker container
  docker start = start the docker container/application
  docker run = create and start a container
  docker ps  = list all running containers
  docker ps -a  = list all running containers and stopped containers
  docker login -u mylandmarktech
  docker push  = push images to Registry / dockerhub 

Your password will be stored unencrypted in /var/lib/jenkins/.docker/config.json

 docker pull   --> open source without authentication 
 docker push mylandmarktech/class26-web-app

  docker pull mylandmarktech/nodejs-app

  docker pull mylandmarktech/nodejs-fe-app

Deploying applications as a docker container:

  docker run -d -p 8000:8080 mylandmarktech/maven-web-app

 users---> (8000)dockerHost ---->container(8080)

   18.209.168.14:8000/maven-web-app

======
#Dockerfile

FROM tomcat:8.0.20-jre8  #(softwares + dependencies)
COPY target/*war /usr/local/tomcat/webapps/maven-web-app.war

Project:
  Jenkins docker integration
