🚀 Project Overview
This project sets up a complete CI/CD pipeline using Jenkins and Docker, with deployment via Docker Compose and Kubernetes (EKS). It includes image scanning tools like Trivy and Docker Scout, and SonarQube for code quality.

#📋 Prerequisites
AWS EC2 Instance: Name: HR-Leave-App OS: Ubuntu Instance Type: t2.medium or t2.large Storage: 30GB Key Pair: vikas-key

```
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

```

check status of jenkins
```
systemctl status jenkins
```
then login into your jenkins server

```
http://<your server ip>:8080
```
now we need to install docker
```
#!/bin/bash

# Update package manager repositories
sudo apt-get update

# Install necessary dependencies
sudo apt-get install -y ca-certificates curl

# Create directory for Docker GPG key
sudo install -m 0755 -d /etc/apt/keyrings

# Download Docker's GPG key
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

# Ensure proper permissions for the key
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add Docker repository to Apt sources
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package manager repositories
sudo apt-get update

sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

```

