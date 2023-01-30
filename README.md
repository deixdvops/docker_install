Install docker on ubuntu

# docker_install

#!/bin/bash

    #Author : DeixDevops
    #Date : 01-30-2023

## ---------- script to install docker on ubuntu and start it-----------------

#To install docker, you need the 64-bit version of the Ubuntu 18.04 OS or any recent Ubuntu version. You also need a user account with sudo priviledges 

#Step 1: Clean up the system 
#Make sure the system is clean by removing any old version of docker that might be installed: 

sudo apt-get remove docker docker-engine docker.io containerd runc

#it’s ok if apt-get reports that none of these packages are installed.

#Step 2: Setup the docker repository

#To do that, run the following commands: 

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release

#Now, add Docker’s official GPG key with the command
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

#Then, use the following command to setup the stable repository
 echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/kyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null 

 #Step 3: Intall Docker Engine
#Update the apt package index and install the latest version of Docker Engine

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

#You can check the status of the daemon with 

sudo systemctl status docker


#Docker installation on a Centos 7 server (recommended method)

#!/bin/bash

    #Author : DeixDevops
    #Date : 01-30-2023

## ---------- script to install docker on centos -----------------

#Docker installation on a Centos 7 server (recommended method)
#First boot up a Centos 7 server and connect remotely to it. 

#Step1: Clean up the system
#Make sure the system is clean by removing any old version of docker that might be installed: 

#it’s ok if yum reports that none of these packages are installed

sudo yum remove docker docker-client docker-client-latest docker-common docker-latest docker-latest-logrotate docker-logrotate docker-engine

#Step 2: Setup the docker repository
#To do that, run the following commands: 


sudo yum install -y yum-utils
sleep 3
echo "utils is successfully installed"
sleep 3
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sleep 3
echo "Repo is successufully added"
sleep 3
#Step 3: Install the docker engine
#Use the following command to install the latest version of Docker Engine on your system:

 sudo yum install -y docker-ce docker-ce-cli containerd.io
sleep 3
echo "docker-ce is successfully installed"
#Step 4: Check the status, start and enable docker daemon
#Check the status of the docker daemon with the command
 sudo systemctl status docker
#If the daemon is not up and running, start and enable it with  the commands

sudo systemctl start docker
sudo systemctl enable docker
#Check the status of the daemon to make sure it is up and running with
sleep 3
echo "docker is up and running, please check status"
sleep 3
sudo systemctl status docker

echo "you are good to go"
