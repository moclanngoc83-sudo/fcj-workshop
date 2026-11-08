---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 4. </b> "
---


# Simple Web App CI/CD on AWS

#### Overview

**Continuous Integration and Continuous Delivery/Deployment (CI/CD)** phelp automate the process of building, testing, and deploying software applications.

In this workshop, you will learn how to build a simple web application using Java and Spring Boot, then deploy it to Amazon EC2 through an automated CI/CD pipeline.

You will use GitHub to store the source code, AWS CodePipeline to orchestrate the workflow, AWS CodeBuild to build the application and run unit tests, Amazon S3 to store build artifacts, and AWS CodeDeploy to deploy the application to an EC2 instance.

The workshop includes the following stages:
+ **Source** - Store application source code in GitHub and trigger the pipeline when code changes.
+ **Build and Test** - Use AWS CodeBuild to compile the application and execute automated unit tests.
+ **Quality Gate** - Stop the pipeline if the build or unit tests fail.
+ **Deploy** - Use AWS CodeDeploy to deploy the application to Amazon EC2.
+ **Monitoring** - Use Amazon CloudWatch to monitor logs and deployment activities.

#### Content

1. [Workshop overview](5.1-Workshop-overview)
2. [Prerequiste](5.2-Prerequiste/)
3. [Build the Web Application](5.3-build-web-application/)
4. [Configure CI with AWS CodeBuild](5.4-codebuild/)
5. [Deploy the Application with AWS CodeDeploy](5.5-codedeploy/)
6. [Create the CI/CD Pipeline](5.6-codepipeline/)
7. [Monitoring and Testing](5.7-monitoring-testing/)
8. [Clean Up AWS Resources](5.8-cleanup/)