# 🚀 Auto Deployment of Flask Application on AWS EC2 using Jenkins, Docker & Terraform

## 📌 Project Overview

This project demonstrates an automated CI/CD pipeline to deploy a Flask web application on AWS EC2 using DevOps tools.

The main objective is to automate the application deployment process and reduce manual work.

Whenever a developer pushes new code to GitHub, Jenkins automatically triggers the pipeline, builds a Docker image, pushes it to Docker Hub, and deploys the latest container on an AWS EC2 instance.

AWS infrastructure is created using Terraform.

---

## 🎯 Project Objectives

- Automate application deployment using Jenkins.
- Containerize the Flask application using Docker.
- Store Docker images in Docker Hub.
- Provision AWS infrastructure using Terraform.
- Implement a CI/CD pipeline.
- Reduce manual deployment efforts.
- Make application deployment faster and more reliable.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| AWS EC2 | Host the Flask application |
| Terraform | Create AWS infrastructure |
| Jenkins | Automate CI/CD pipeline |
| Docker | Containerize the application |
| Docker Hub | Store Docker images |
| GitHub | Source code management |
| Python Flask | Develop the web application |
| Linux Ubuntu | Server operating system |

---

## 🏗️ Project Architecture

### Architecture Diagram

```text
                 Developer
                     |
                     |
                Push Code
                     |
                     v
                  GitHub
                     |
                     |
              GitHub Webhook
                     |
                     v
                  Jenkins
                     |
              ----------------
              |              |
              v              |
          Docker Build       |
              |              |
              v              |
          Docker Image       |
              |              |
              v              |
          Docker Hub         |
              |              |
              v              |
        Pull Latest Image    |
              |              |
              v              |
           AWS EC2           |
              |              |
              v              |
       Docker Container      |
              |              |
              v              |
        Flask Application    |
              |              |
              v              |
          Web Browser        |

       Terraform
           |
           v
    AWS EC2 + Security Group
```

---

## ⚙️ How the Project Works

### Step 1: GitHub

- Created a GitHub repository.
- Uploaded the Flask application source code.
- Stored the Dockerfile and Jenkinsfile.
- GitHub acts as the source code repository.

### Step 2: Jenkins

- Configured a Jenkins Pipeline job.
- Connected Jenkins with GitHub.
- Configured GitHub webhook to trigger builds automatically.
- Jenkins executes the pipeline whenever new code is pushed.

### Step 3: Docker

- Created a Dockerfile for the Flask application.
- Built a Docker image using the Docker build command.
- Docker packages the application and its dependencies into a container image.

### Step 4: Docker Hub

- Configured Docker Hub credentials in Jenkins.
- Logged in to Docker Hub using Jenkins credentials.
- Pushed the Docker image to Docker Hub.

### Step 5: AWS EC2 Deployment

- Created an EC2 instance using Terraform.
- Configured the required Security Group rules.
- Jenkins connects to the application EC2 instance through SSH.
- The latest Docker image is pulled from Docker Hub.
- The Docker container is started on EC2.

### Step 6: Application Verification

- Accessed the Flask application using the EC2 public IP address.
- Verified that the application was running in the browser.

---

## 📂 Project Structure

```text
devops-mini-project/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── Jenkinsfile
│
└── README.md
```

*Note: Update this structure if your actual repository has different file locations.*

---

## 🔄 CI/CD Pipeline Stages

The Jenkins pipeline contains the following stages:

| Stage | Description |
|---|---|
| Checkout | Fetches source code from GitHub |
| Build Image | Builds the Docker image |
| Push to Docker Hub | Uploads the image to Docker Hub |
| Deploy to App Server | Deploys the container on AWS EC2 |
| Health Check | Checks application availability |

### Pipeline Workflow

```text
Checkout
   |
   v
Build Docker Image
   |
   v
Push Image to Docker Hub
   |
   v
Deploy on AWS EC2
   |
   v
Health Check
   |
   v
Application Running
```

---

## 🐳 Docker Commands Used

Build Docker image:

```bash
docker build -t flask-app .
```

View Docker images:

```bash
docker images
```

Run Docker container:

```bash
docker run -d -p 5000:5000 flask-app
```

Check running containers:

```bash
docker ps
```

View container logs:

```bash
docker logs <container_id>
```

---

## ☁️ Terraform Commands Used

Initialize Terraform:

```bash
terraform init
```

Validate configuration:

```bash
terraform validate
```

Preview infrastructure changes:

```bash
terraform plan
```

Create AWS infrastructure:

```bash
terraform apply
```

Destroy infrastructure when no longer required:

```bash
terraform destroy
```

---

## 🔐 Security Configuration

- Used Jenkins credentials to store Docker Hub authentication details.
- Used SSH key-based authentication for EC2 access.
- Configured AWS Security Groups to control inbound traffic.
- Avoided storing passwords, access tokens and private keys in GitHub.
- Used Terraform to manage AWS infrastructure.

**Important:** Never upload `.pem` files, passwords, access tokens or AWS secret keys to a public GitHub repository.

---

## ✅ Expected Outcome

After successful execution:

- Jenkins automatically builds the Docker image.
- Docker image is uploaded to Docker Hub.
- Latest image is deployed on AWS EC2.
- Flask application becomes accessible through the EC2 public IP and application port.

Application URL:

```text
http://<EC2-PUBLIC-IP>:5000
```

Replace the placeholder with your actual EC2 public IP and configured application port.

---

## 💡 Benefits of This Project

1. Reduces manual deployment.
2. Automates the CI/CD process.
3. Provides consistent application deployment using Docker.
4. Simplifies infrastructure management using Terraform.
5. Improves deployment speed.
6. Helps understand real-world DevOps workflows.

---

## 🎓 What I Learned

Through this project, I learned:

- How to create and manage AWS EC2 instances.
- How to write Terraform configuration files.
- How to create Docker images and containers.
- How to configure Jenkins pipelines.
- How to integrate GitHub with Jenkins.
- How to push and pull images from Docker Hub.
- How to deploy applications on AWS EC2.
- How to troubleshoot CI/CD pipeline failures.

---

## 👩‍💻 Project Information

**Project Name:** Auto Deployment of Flask Application on AWS EC2

**Role:** DevOps Engineer (Project)

**Developer:** Disha Patil

**GitHub Repository:** https://github.com/Disha-Patil02/devops-mini-project

**Domain:** DevOps / Cloud Computing

**Project Type:** Hands-on DevOps CI/CD Project

---

## 📌 Conclusion

This project helped me understand how different DevOps tools work together to automate application deployment.

By integrating GitHub, Jenkins, Docker, Docker Hub, Terraform and AWS EC2, I implemented a CI/CD workflow that reduces manual effort and makes application deployment easier and faster.

This project gave me practical experience with DevOps tools and real-world deployment workflows.

---

⭐ If you find this project useful, feel free to explore the repository and learn from it.
