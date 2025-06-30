🚀 Project Overview
This project sets up a complete CI/CD pipeline using Jenkins and Docker, with deployment via Docker Compose and Kubernetes (EKS). It includes image scanning tools like Trivy and Docker Scout, and SonarQube for code quality.

#📋 Prerequisites
AWS EC2 Instance: Name: HR-Leave-App OS: Ubuntu Instance Type: t2.medium or t2.large Storage: 30GB Key Pair: vikas-key

ssh into your server - first of all install jenkins on your ubuntu instance vi jenkins.sh

#!/bin/bash

# Install OpenJDK 17 JRE Headless
sudo apt update
sudo apt install openjdk-17-jdk


# Download Jenkins GPG key
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key

# Add Jenkins repository to package manager sources
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# Update package manager repositories
sudo apt-get update

# Install Jenkins
sudo apt-get install jenkins -y


  

