# Assignment II – Jenkins CI/CD Pipeline Implementation

**Module:** DSO101 – Continuous Integration and Continuous Deployment

**Student Name:** Sonam Lindel

**Student ID:** 02250354

# Introduction

The objective of this assignment was to implement a Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Node.js To-Do application using Jenkins. The pipeline automates the process of retrieving source code from GitHub, installing dependencies, running tests, building a Docker image, and pushing the image to Docker Hub.

# Tools and Technologies Used

* Jenkins
* GitHub
* Node.js
* npm
* Docker
* Docker Hub
* Visual Studio Code
* Windows Operating System

# Steps Performed

## Step 1: Jenkins Installation

1. Downloaded Jenkins from the official Jenkins website.
2. Installed Jenkins on Windows.
3. Accessed Jenkins through:
   http://localhost:8080
4. Retrieved the initial administrator password from the Jenkins installation directory.
5. Installed the suggested plugins during the initial setup.

## Step 2: Plugin Installation

Installed the following plugins through Manage Jenkins:

* NodeJS Plugin
* Pipeline Plugin
* GitHub Integration Plugin
* Docker Pipeline Plugin

These plugins were required for Node.js application builds, GitHub integration, and Docker image management.

## Step 3: NodeJS Configuration

1. Opened Manage Jenkins → Tools.
2. Added a NodeJS installation.
3. Enabled automatic installation.
4. Configured NodeJS as the runtime environment for the pipeline.

## Step 4: GitHub Repository Setup

1. Created and maintained the project repository on GitHub.
2. Uploaded the complete To-Do application source code.
3. Added the Jenkinsfile to the root directory of the project.
4. Ensured all project files were committed and pushed to the main branch.

Repository Structure:

todo-app

├── backend

├── frontend

└── Jenkinsfile

## Step 5: GitHub Personal Access Token

1. Generated a GitHub Personal Access Token (PAT).
2. Enabled repository access permissions.
3. Added the token as Jenkins credentials.

Credential Configuration:

* Username: GitHub Username
* Password: GitHub Personal Access Token
* Credential ID: github-creds

## Step 6: Docker Setup

1. Installed Docker Desktop.
2. Started the Docker Engine.
3. Logged into Docker Hub using Docker credentials.
4. Verified Docker functionality using Docker commands.

## Step 7: Jenkinsfile Creation

A Jenkinsfile was created in the project root directory to define the pipeline stages.

The pipeline included:

### Checkout Stage

Retrieves the latest source code from GitHub.

### Install Dependencies Stage

Runs:

npm install

to install required Node.js packages.

### Test Stage

Runs:

npm test

to verify application functionality.

### Build Docker Image Stage

Builds the backend Docker image using the Dockerfile.

### Push Docker Image Stage

Pushes the generated Docker image to Docker Hub.

## Step 8: Pipeline Job Creation

1. Created a new Jenkins Pipeline project.
2. Selected:

Pipeline Script from SCM

3. Chose Git as the source control system.
4. Configured the GitHub repository URL.
5. Selected the GitHub credentials.
6. Specified Jenkinsfile as the script path.

## Step 9: Pipeline Execution

Executed the pipeline using Build Now.

The pipeline successfully performed:

1. Source code checkout from GitHub.
2. Installation of project dependencies.
3. Execution of test commands.
4. Docker image build process.
5. Preparation for Docker Hub deployment.

# Challenges Faced

Several issues were encountered during the implementation:

### Jenkinsfile Not Found

Initially Jenkins was unable to locate the Jenkinsfile because it had not been pushed to GitHub.

### Incorrect NodeJS Tool Name

The NodeJS installation name configured in Jenkins did not match the name referenced inside the Jenkinsfile.

### GitHub Authentication Error

Authentication failed because the repository URL and credentials were not configured correctly.

### Incorrect Project Directory Path

The backend folder was located inside the todo-app directory, requiring updates to the Jenkins pipeline path configuration.

### Missing Test Script

The package.json file did not contain a test script, causing the pipeline to fail during the testing stage.

### Docker Connectivity Issues

Docker Desktop was not running when Jenkins attempted to build the Docker image, resulting in Docker API connection errors.

# Learning Outcomes

Through this assignment, I learned:

* The fundamentals of Continuous Integration and Continuous Deployment.
* How Jenkins automates software development workflows.
* How to integrate GitHub repositories with Jenkins.
* How Jenkins Pipelines are defined using Jenkinsfiles.
* How Node.js applications are built and tested automatically.
* How Docker images are created and managed.
* How Docker Hub can be used as a container registry.
* How automation improves software quality and deployment efficiency.

# Conclusion

This assignment provided practical experience in implementing a CI/CD pipeline using Jenkins. The integration of GitHub, Jenkins, Node.js, Docker, and Docker Hub demonstrated how modern DevOps practices automate software delivery. The assignment improved my understanding of build automation, testing, containerization, and deployment workflows, which are essential skills in modern software engineering.
