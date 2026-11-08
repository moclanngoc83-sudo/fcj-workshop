---
title: "Prerequisites"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

#### Overview

Before starting this workshop, prepare the required development tools, source code repository, and AWS environment.

This workshop uses a simple Java Spring Boot web application and AWS services to automate the build, testing, deployment, and monitoring processes.

#### Development tools

Make sure the following tools are available on your local computer:

+ **Java Development Kit (JDK 17)** - Used to compile and run the Spring Boot application.
+ **Apache Maven** - Used to manage dependencies, build the application, and execute unit tests. The Maven Wrapper (`mvnw`) can be used if it is included in the project.
+ **Git** - Used to manage source code changes.
+ **Visual Studio Code or IntelliJ IDEA** - Used to edit the application source code.
+ **A web browser** - Used to access the deployed application and AWS Management Console.

Verify the Java installation:

```powershell
java -version
```

Verify Git:

```powershell
git --version
```

#### GitHub repository

Create a GitHub repository to store the application source code.

The repository should contain:

+ Spring Boot application source code.
+ Unit tests.
+ `pom.xml` for Maven configuration.
+ `buildspec.yml` for AWS CodeBuild.
+ `appspec.yml` for AWS CodeDeploy.
+ Deployment scripts required by the application.

#### AWS account and permissions

An AWS account with permission to create and configure the required resources is needed.

The workshop uses the following AWS services:

+ **AWS CodePipeline** - Orchestrates the CI/CD workflow.
+ **AWS CodeBuild** - Builds the application and executes unit tests.
+ **Amazon S3** - Stores build artifacts.
+ **AWS CodeDeploy** - Deploys the application to Amazon EC2.
+ **Amazon EC2** - Hosts the web application.
+ **Amazon CloudWatch** - Collects application logs and monitoring information.
+ **AWS Identity and Access Management (IAM)** - Controls access between AWS services.

Use an IAM role or user with only the permissions required for the workshop. Avoid using the AWS root account for routine tasks, and do not share access keys or credentials.

#### Region selection

Choose one AWS Region for the workshop and use it consistently for the supported services.

Record the selected Region before creating resources so that the pipeline, artifact bucket, deployment resources, and monitoring configuration can be located easily.

#### Cost and security considerations

+ AWS resources may incur charges depending on the selected configuration and usage.
+ Review the estimated costs before creating EC2 instances or other billable resources.
+ Restrict inbound access to the application port and administrative access to trusted IP addresses.
+ Do not store AWS credentials in the source code repository.
+ Delete the workshop resources after completing the project.

#### Readiness checklist

Before proceeding to the next section, confirm that:

+ Java and Git are installed and working.
+ The application source code is available locally.
+ The GitHub repository has been created.
+ You can sign in to the AWS Management Console.
+ You have permission to create the required AWS resources.
