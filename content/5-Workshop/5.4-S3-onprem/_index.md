---
title: "Build with AWS CodeBuild"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

#### **Overview**

In this section, you will configure **AWS CodeBuild** to build the **Spring Boot web application** and execute unit tests automatically.

**AWS CodeBuild** is a fully managed build service that compiles source code, runs tests, and produces software packages that are ready for deployment.

In this workshop, CodeBuild will retrieve the source code from the **GitHub repository**, use **Maven** to build the application, and run the unit tests defined in the project.

#### **Why use AWS CodeBuild?**

- **Automated Build:** CodeBuild automatically compiles the application without requiring manual commands on your local computer.
- **Automated Testing:** Unit tests are executed during the build process to verify the application's behavior.
- **Build Artifacts:** If the build succeeds, CodeBuild generates a deployable application package that can be stored in **Amazon S3**.
- **CI/CD Integration:** CodeBuild integrates with **AWS CodePipeline** to automate the build stage whenever source code changes are detected.

#### **Build Process Overview**

The build process follows these steps:

1. **Source:** Retrieve the application source code from GitHub.
2. **Build:** Use Maven to compile the Spring Boot application.
3. **Test:** Execute unit tests to verify the application.
4. **Package:** Generate the application JAR file.
5. **Store Artifacts:** Prepare the build output for the deployment stage.

#### **Build Configuration**

The project uses a `buildspec.yml` file to define the commands executed by CodeBuild.

The configuration specifies the **Java runtime environment**, the commands to build and test the application, and the location of the generated artifacts.

The build output will be used in the next stage of the CI/CD pipeline.

#### **Expected Result**

After completing this section, you should have:

- An **AWS CodeBuild project** configured for the application.
- A build process that uses **Maven** to compile the source code.
- Unit tests executed automatically during the build.
- A packaged application artifact ready for the deployment stage.

#### **Content**

- [Configure AWS CodeBuild](5.4.1-configure-codebuild/)
- [Build and Test the Application](5.4.2-build-and-test/)
