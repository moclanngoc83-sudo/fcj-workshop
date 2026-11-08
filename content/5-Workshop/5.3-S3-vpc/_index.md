---
title: "Build the Web Application"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

#### **Build the Web Application**

In this section, you will prepare a simple **Java Spring Boot web application** to use in the **CI/CD pipeline on AWS**.

The application will be managed in a **GitHub repository**. When the source code changes, **AWS CodePipeline** will detect the changes and start the pipeline. **AWS CodeBuild** will compile the source code and run **unit tests** using **Maven**.

If the build and tests succeed, the application can continue to the deployment stage. If they fail, the pipeline will stop to prevent an unsuccessful build from being deployed.

#### **Application Overview**

The demo application uses the following technologies:

- **Java 17** – the programming language and runtime.
- **Spring Boot** – the framework used to build the web application.
- **Maven** – manages dependencies and builds the application.
- **JUnit** – runs unit tests to verify application behavior.
- **GitHub** – stores the source code and triggers the pipeline when changes are detected.

#### **Project Structure**

The project should contain the following main files and directories:

```text
cicd-aws-demo/
├── src/
│   ├── main/
│   │   └── java/          # Application source code
│   └── test/
│       └── java/          # Unit tests
├── pom.xml                # Maven configuration
├── buildspec.yml          # AWS CodeBuild instructions
├── appspec.yml             # AWS CodeDeploy instructions
└── scripts/                # Deployment scripts
```

#### **Expected Result**

After completing this section, you should have:

- A **Spring Boot application** that can run locally.
- A **GitHub repository** containing the project source code.
- A **Maven configuration** for building the application and running unit tests.
- The basic files needed for the later **CodeBuild** and **CodeDeploy** stages.

#### **Content**

- [Prepare the Spring Boot application](3.1-create-web-application/)
- [Push the source code to GitHub](3.2-push-to-github/)
