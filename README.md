CI/CD Pipeline using Jenkins, Docker & AWS EC2

📌 Project Overview

This project demonstrates the implementation of a CI/CD pipeline using Jenkins, Docker, Docker Compose, GitHub, and AWS EC2.
The pipeline automates the process of retrieving source code from GitHub, building a Docker image using Jenkins, and deploying the application in a containerized environment on an AWS EC2 instance.

🎯 Objective

The main objective of this project is to understand and implement an automated Continuous Integration and Continuous Deployment (CI/CD) workflow.

The project demonstrates:

Source code management using GitHub
Continuous Integration using Jenkins
Docker image creation
Containerized application deployment
Docker Compose-based deployment
Application hosting on AWS EC2
🛠️ Technologies Used
Technology	Purpose
GitHub	Source code repository
Jenkins	CI/CD automation
Docker	Application containerization
Docker Compose	Application deployment
AWS EC2	Cloud server for Jenkins and application
Linux/SSH	Server access and administration

🏗️ System Architecture

Developer
    |
    | Push Code
    v
 GitHub
    |
    | Jenkins pulls source code
    v
 Jenkins on AWS EC2
    |
    | Continuous Integration
    v
Build Docker Image
    |
    | Continuous Deployment
    v
Docker Compose
    |
    v
Docker Container
    |
    v
Application
    |
    v
AWS EC2 Public IP

The project documentation describes the flow as:

Developer → GitHub → Jenkins → Docker Image → Docker Compose → Application on AWS EC2.

🔹 Part A — Continuous Integration (CI)

1. Create CI Project Files

A folder containing the required CI files was created and pushed to a GitHub repository named:

CI-CD

This repository acts as the source for the Jenkins pipeline.

2. Create AWS EC2 Instance

An EC2 instance was created to host Jenkins and Docker.

An inbound security rule was configured to allow access to Jenkins through:

Port: 8080

Jenkins was accessed through:

http://<EC2-PUBLIC-IP>:8080

3. Connect to EC2 using SSH

The EC2 instance was accessed through SSH from the terminal.

ssh -i <key-name> aws@<instance-ip-address>

4. Install Jenkins and Docker

Jenkins and Docker were installed inside the EC2 instance.

Jenkins was then accessed through its web interface using port 8080.

5. Configure Jenkins

The required Jenkins plugins were installed.

The Docker Pipeline plugin was specifically installed to support Docker-related pipeline operations.

6. Connect Jenkins with GitHub

Jenkins was configured to retrieve the source code from the GitHub repository.

The pipeline then pulls the project files and executes the configured build process.

🔹 Part B — Continuous Deployment (CD)

1. Create CD Project Files

A separate folder was created for the deployment-related files and pushed to GitHub.

GitHub repository:

Jenkins-continue

2. Create AWS EC2 Instance

Another EC2 instance was created for the CD environment.

Two inbound rules were configured:

Port 8080 → Jenkins
Port 8081 → Application

Port 8081 was used to avoid a port conflict and provide access to the deployed application.

3. Install Required Tools

The following tools were installed inside the EC2 instance:

Jenkins
Docker
Docker Compose

Jenkins was accessed through:

http://<EC2-PUBLIC-IP>:8080

4. Configure Jenkins

The required Jenkins plugins were installed, including the Docker Pipeline plugin.

After configuration, Jenkins was used to retrieve and execute the files from GitHub.

5. Deploy Application

Jenkins executes the deployment workflow using Docker and Docker Compose.

The application is deployed inside a Docker container on the EC2 instance.

The deployed application can then be accessed through:

http://<EC2-PUBLIC-IP>:8081

🔄 Complete CI/CD Workflow
                    
                    Developer
                        |
                        v
                     GitHub
                        |
                        v
                  Jenkins on EC2
                        |
                  +-----+-----+
                  |           |
                  v           v
             Pull Code    Build Docker
                            Image
                              |
                              v
                        Docker Compose
                              |
                              v
                       Docker Container
                              |
                              v
                         Application
                              |
                              v
                    EC2 Public IP:8081

🔑 Key Features

Automated source code retrieval from GitHub
Jenkins-based CI/CD pipeline
Docker image creation
Docker containerization
Docker Compose deployment
Jenkins hosted on AWS EC2
Application deployed on AWS EC2
SSH-based EC2 administration

📚 Key Learnings

Through this project, I gained hands-on experience with:

Jenkins
CI/CD concepts
GitHub integration
Docker
Docker image creation
Docker containers
Docker Compose
AWS EC2
Linux server administration
SSH
Jenkins plugin configuration
Automated application deployment

📁 Project Structure

A suggested GitHub structure for documenting this project:

jenkins-ci-cd/
│
├── README.md
│
├── CI/
│   ├── Jenkinsfile
│   └── application-files
│
└── CD/
    ├── Jenkinsfile
    ├── Dockerfile
    ├── docker-compose.yml
    └── application-files

Keep only the files that actually exist in your project. Do not create placeholder files just to match this structure.

📌 Project Status

Completed

This project demonstrates the implementation of a CI/CD workflow using GitHub, Jenkins, Docker, Docker Compose, and AWS EC2, from retrieving source code through automated build and deployment.

The deployed application was accessed through the EC2 public IP on port 8081.
