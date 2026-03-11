## CI/CD Pipeline using Jenkins, Docker, and AWS
## PROJECT OVERVIEW

This project demonstrates an end-to-end CI/CD pipeline where code pushed to GitHub automatically triggers Jenkins to build and deploy the application using Docker on an AWS EC2 instance.

The objective of this project is to understand DevOps automation, continuous integration, and continuous deployment using industry-standard tools.

## Architecture

Developer pushes code to GitHub which triggers Jenkins via webhook.  
Jenkins builds a Docker image and deploys it to an AWS EC2 instance.

![Architecture](https://github.com/Deepak-2907/devops-cicd-project/blob/3ea1c46a7106ffaeee429f802ad5f4e9d64c429a/Architecture.PNG)

## Tech Stack:

->Git
->GitHub
->Jenkins
->Docker
->AWS EC2
->Linux

## Project Workflow:

## 1. Code Commit

Developer pushes application code to the GitHub repository.

## 2. Webhook Trigger

GitHub webhook triggers Jenkins automatically.

## 3. Jenkins Pipeline Execution

Jenkins pulls the latest code from the repository.

## 4. Docker Build

Jenkins builds a Docker image for the application.

## 5. Deployment

Docker container runs on the AWS EC2 instance.

## Project Screenshots

### Jenkins Pipeline Success
![pipeline](https://github.com/Deepak-2907/devops-cicd-project/blob/16ee90b213fb05b39d5d97be1249a27e0adce2d3/Jenkins%20pipeline%20success.PNG)

### GitHub Webhook Configuration
![Webhook](https://github.com/Deepak-2907/devops-cicd-project/blob/0ffee18a8e904efed31ab395ba36dab9f3fd996e/github-webhook.PNG)

### Jenkins Console Output
![Console](https://github.com/Deepak-2907/devops-cicd-project/blob/25b13838076a730f841bb6f5efc9cf22d8bc68bd/jenkins-console.PNG)

### Application Running on AWS EC2
![App](https://github.com/Deepak-2907/devops-cicd-project/blob/b1b873164908341454730f4a13edd0ee1cb3c41c/app-running.PNG)

## Jenkins Pipeline Stages

1️⃣ **Clone Stage**
- Jenkins pulls latest code from GitHub

2️⃣ **Build Stage**
- Docker image is built using Dockerfile

3️⃣ **Deploy Stage**
- Docker container runs on AWS EC2

4️⃣ **Verification Stage**
- Application becomes available via EC2 public IP

## Jenkins Pipeline

Example Jenkins pipeline used in this project:

pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Deepak-2907/devops-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-cicd .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8081:80 devops-cicd'
            }
        }
    }
}

## Dockerfile:
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html

## How to Run This Project:

->Clone the repository
->git clone https://github.com/Deepak-2907/devops-cicd-project.git
->Build Docker Image
->docker build -t devops-cicd .
->Run Container
->docker run -d -p 8081:80 devops-cicd

Then open in browser:

http://16.171.23.102

## Key Learnings:

->Implemented CI/CD pipeline using Jenkins

->Integrated GitHub webhook with Jenkins

->Built Docker container for application deployment

->Deployed containerized application on AWS EC2

->Automated build and deployment process

 ## DevOps Concepts Used

- Continuous Integration (CI)
- Continuous Deployment (CD)
- Infrastructure Automation
- Containerization
- GitOps Workflow
- Cloud Deployment

## Project Motivation

As someone transitioning into DevOps with a background in networking,
I wanted to understand how modern teams automate software delivery.

This project helped me implement a real CI/CD pipeline that automatically
builds and deploys applications using Jenkins, Docker, and AWS.

## Future Improvements:

->Deploy application using Kubernetes

->Implement monitoring using Prometheus and Grafana

->Add automated testing stage in Jenkins pipeline

## AUTHOR

## Deepak Kumar
DevOps Enthusiast | Networking Engineer
