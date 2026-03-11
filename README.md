CI/CD Pipeline using Jenkins, Docker, and AWS
Project Overview

This project demonstrates an end-to-end CI/CD pipeline where code pushed to GitHub automatically triggers Jenkins to build and deploy the application using Docker on an AWS EC2 instance.

The objective of this project is to understand DevOps automation, continuous integration, and continuous deployment using industry-standard tools.

Architecture

Developer pushes code → GitHub → Jenkins Pipeline → Docker Build → AWS EC2 Deployment

Developer
   │
   ▼
GitHub Repository
   │  (Webhook Trigger)
   ▼
Jenkins Pipeline
   │
   ▼
Docker Build & Run
   │
   ▼
AWS EC2 Instance

Tech Stack:

->Git
->GitHub
->Jenkins
->Docker
->AWS EC2
->Linux

Project Workflow:

1. Code Commit

Developer pushes application code to the GitHub repository.

2. Webhook Trigger

GitHub webhook triggers Jenkins automatically.

3. Jenkins Pipeline Execution

Jenkins pulls the latest code from the repository.

4. Docker Build

Jenkins builds a Docker image for the application.

5. Deployment

Docker container runs on the AWS EC2 instance.

Repository Structure:
devops-cicd-project
│
├── index.html
├── Dockerfile
├── Jenkinsfile
├── README.md

## Project Screenshots

### Jenkins Pipeline Success
![pipeline](https://github.com/Deepak-2907/devops-cicd-project/blob/16ee90b213fb05b39d5d97be1249a27e0adce2d3/Jenkins%20pipeline%20success.PNG)

### GitHub Webhook Configuration
![Webhook](https://github.com/Deepak-2907/devops-cicd-project/blob/0ffee18a8e904efed31ab395ba36dab9f3fd996e/github-webhook.PNG)

### Jenkins Console Output
![Console](https://github.com/Deepak-2907/devops-cicd-project/blob/25b13838076a730f841bb6f5efc9cf22d8bc68bd/jenkins-console.PNG)

### Application Running on AWS EC2
![App](https://github.com/Deepak-2907/devops-cicd-project/blob/b1b873164908341454730f4a13edd0ee1cb3c41c/app-running.PNG)

Jenkins Pipeline

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

Dockerfile:
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html

How to Run This Project:

->Clone the repository
->git clone https://github.com/Deepak-2907/devops-cicd-project.git
->Build Docker Image
->docker build -t devops-cicd .
->Run Container
->docker run -d -p 8081:80 devops-cicd

Then open in browser:

http://16.171.23.102

Key Learnings:

->Implemented CI/CD pipeline using Jenkins

->Integrated GitHub webhook with Jenkins

->Built Docker container for application deployment

->Deployed containerized application on AWS EC2

->Automated build and deployment process

Future Improvements:

->Deploy application using Kubernetes

->Implement monitoring using Prometheus and Grafana

->Add automated testing stage in Jenkins pipeline

AUTHOR

Deepak Kumar
DevOps Enthusiast | Networking Engineer
