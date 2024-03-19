# CI/CD pipeline using Git, GitHub, Jenkins and Maven

<p align="justify">This project aims to set up a CI/CD pipeline using Git, GitHub, Jenkins, and Maven to automate the build and deployment process for a Java application. Below is an overview of the project setup and configuration steps:</p>

![image](https://github.com/DDMateus/DevOps/assets/88774178/b81d3433-1850-4f15-b6cd-228e90cda86d)

## Overview

1. **Project Components**:
   - Java application hosted on GitHub.

2. **Tools and Technologies**:
   - Git: Version control system for managing source code.
   - Jenkins: Automation server for CI/CD processes.
   - Maven: Build automation tool for Java projects.

## Setup Instructions

### 1. Jenkins Server Setup
- Provision a Linux EC2 Instance.

![image](https://github.com/DDMateus/DevOps/assets/88774178/f93339a4-d967-4d45-8480-868e94c9fc27)

Using PuTTY, ssh into the instance.

![image](https://github.com/DDMateus/DevOps/assets/88774178/5bfb01c1-2988-453d-871c-1d104ebc0813)

- Add Jenkins repository, import the repository key and install Java.

```bash
wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
amazon-linux-extras install epel
amazon-linux-extras install java-openjdk11
```

- Install and start Jenkins service.

```bash
yum install jenkins
service start jenkins
```

- Access the Jenkins Web UI on port 8080.

![image](https://github.com/DDMateus/DevOps/assets/88774178/c0b97520-b115-4de2-97f0-ffcbf8879fc6)

![image](https://github.com/DDMateus/DevOps/assets/88774178/8fefafe4-5517-40a6-b188-383b74a3e26e)

### 3. Access Jenkins Dashboard
- Retrieve the initial admin password from `/var/lib/jenkins/secrets/initialAdminPassword`.
- Access Jenkins dashboard through a web browser and complete the setup.

![image](https://github.com/DDMateus/DevOps/assets/88774178/84ab774a-2767-44b0-a994-a8da90b4c38b)

### 4. Jenkins Job Configuration
- Integrate Git with Jenkins using Jenkins CLI.

```bash
yum install git
```

![image](https://github.com/DDMateus/DevOps/assets/88774178/4ecd6c00-a225-43a6-87df-3942c70cdf89)

![image](https://github.com/DDMateus/DevOps/assets/88774178/8a49f0a2-b42c-4ec2-8614-8b4f1766747f)

- Install Git and GitHub plugin on Jenkins GUI.

![image](https://github.com/DDMateus/DevOps/assets/88774178/1b5df3f9-185f-4ab0-b56d-ef17eb53b86c)

- Configure Git on Jenkins GUI.

![image](https://github.com/DDMateus/DevOps/assets/88774178/db292c5e-8bd9-47fe-844f-b3fe80cbc0c6)

- Create a Jenkins job to pull the code from the GitHub repository.

![image](https://github.com/DDMateus/DevOps/assets/88774178/fa1f50ae-49f5-4898-8d7b-95256ea71fa8)

### 5. Maven Setup
- Install Maven on the Jenkins server.

![image](https://github.com/DDMateus/DevOps/assets/88774178/db2ea07d-f7e8-4e2c-9091-79d956438f90)

![image](https://github.com/DDMateus/DevOps/assets/88774178/0b2ebbe0-7801-4d0d-8a33-6503eda5554d)

- Extract and configure Maven binaries.

![image](https://github.com/DDMateus/DevOps/assets/88774178/308a317b-08d7-460d-914b-1423208941bc)

Rename it.

![image](https://github.com/DDMateus/DevOps/assets/88774178/cd7be324-94fe-4a98-a828-6dc230e21d27)

![image](https://github.com/DDMateus/DevOps/assets/88774178/b1459ec1-1495-4933-a480-44531962408c)

Executable is in /bin directory.

![image](https://github.com/DDMateus/DevOps/assets/88774178/25da0b5a-c347-475e-96f8-7aeae6eadde5)

- Set up Environment variables: JAVA_HOME (java path, where JDK is available), M2 (binary directory), M2_HOME (path where Maven is available).

![image](https://github.com/DDMateus/DevOps/assets/88774178/61de3a84-4298-4f73-ac84-34b4335e9c0a)

- Install Maven plugin on Jenkins GUI.

![image](https://github.com/DDMateus/DevOps/assets/88774178/38d657fa-ffb9-417c-8a64-7744cd7b45f1)

- Configure Maven and Java on Jenkins GUI.

![image](https://github.com/DDMateus/DevOps/assets/88774178/f8c6e364-1cf9-4fa8-937c-24f6979b48bf)

![image](https://github.com/DDMateus/DevOps/assets/88774178/419ab471-de4f-45c4-8a33-422fc352ecc2)

### 6. Build Java Project
- Create a Jenkins job to build the Java project using Maven.
- Execute the Jenkins job to build the project and generate artifacts.

![image](https://github.com/DDMateus/DevOps/assets/88774178/50604e52-b51e-4241-b302-2e1ebc6da91d)

![image](https://github.com/DDMateus/DevOps/assets/88774178/b9d91cba-ac70-4e5d-ac91-c72a342f6891)

![image](https://github.com/DDMateus/DevOps/assets/88774178/6a251ad3-6041-4a26-a9f6-71a4b484d46d)

Jenkins GUI.

![image](https://github.com/DDMateus/DevOps/assets/88774178/75a24ab6-7f4e-4da7-813d-a0c63e1cddfb)

## Folder Structure

- `/var/lib/jenkins/workspace/`: Jenkins workspace directory where all build-related information is stored.
- `/bin/`: Directory containing Maven binaries for executing Maven commands.
