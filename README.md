# weather_app_python
Weather app built with Flask and Python. Enter a city, get live temperature and conditions. The app is deployed to a EC2 server by a Jenkins Pipeline which pulls the code, containerizes the app as a Docker  container  and then deploys it using Docker compose.  

## Tech stack 
- *Frontend:* Flask, a lightweight Python web framework  
- *Devops Tools:* Jenkins, GitHub, Docker, Docker Compose
---  
## Table of Contents 
[Project Overview](#project-overview)  
[Architecture Diagram](#arch-diagram)  
[Step 1: AWS EC2 Instance Preparation](#ec2-prep)  
[Step 2: Install Dependencies on EC2](#dependency-installation-ec2)  
[Step 3: Jenkins Installation and Setup](#jenkins-installation)  
[Step 4: GitHub Repository Configuration](#github-repo)  
- [Dockerfile](#dockerfile)  
- [docker-compose.yml](#docker-compose)  
- [Jenkinsfile](#jenkinsfile)  
[Jenkins CI/CD pipeline](#jenkinspipeline)  
[Troubleshooting](#troubleshooting)    
[What problem does this project solve](#problemsolved)    
[Conclusion](#conclusion)  

## Project Overview
**Automated Flask CI/CD Pipeline on AWS EC2**  : Production-grade Flask app deployed via Jenkins on AWS EC2: GitHub push triggers build, Docker image creation, and seamless deployment using Docker compose. Demonstrates CI/CD, containerization, automation mastery for scalable cloud ops.  

## Architecture Diagram

<img src= "images/architecture.jpg">


