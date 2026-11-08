---
title : "Introduction"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 4.1. </b> "
---

#### VPC endpointsContinuous Integration and Continuous Deployment
+ **Continuous Integration (CI)** is a software development practice in which code changes are frequently integrated into a shared repository and automatically built and tested.

+ **Continuous Deployment (CD)** automates the process of releasing application changes to a target environment after the required build and testing steps have succeeded.

+ **AWS CI/CD services** help automate the software delivery process, reduce manual operations, and improve deployment consistency.

#### Workshop overview
In this workshop, you will build and deploy a simple web application using Java and Spring Boot. You will use AWS services to automate the build, testing, and deployment process.

+ **"Source Repository"** uses GitHub to store the application source code. Changes pushed to the repository trigger the CI/CD workflow.

+ **"Build and Test"** uses AWS CodeBuild to compile the application, run unit tests, and generate a deployment artifact. The pipeline stops if the build or tests fail.

+ **"Deployment"** uses AWS CodeDeploy to deploy the application to an Amazon EC2 instance. Amazon S3 stores the build artifact used during deployment.

+ **"Monitoring"** uses Amazon CloudWatch to collect relevant logs and monitor the deployment process.

The goal is to create a repeatable deployment workflow in which a code change can be built, tested, and deployed automatically.



**Expected outcome**

At the end of this workshop, you will have a simple web application running on Amazon EC2 and an automated pipeline that builds, tests, and deploys application updates from GitHub.

