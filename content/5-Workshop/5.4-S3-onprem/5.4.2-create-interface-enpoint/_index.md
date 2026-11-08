---
title: "Build and Test the Application"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.4.2. </b> "
---

#### **1. Overview**

In this section, you will run and verify the **AWS CodeBuild** process for the **Spring Boot web application**.

CodeBuild uses the project's **`buildspec.yml`** file to execute build commands. The build process compiles the source code, runs unit tests, and prepares the application package for deployment.

#### **2. Start a Build**

1. Open the **AWS CodeBuild console**.
2. Choose **Build projects** from the navigation pane.
3. Select the project named `cicd-aws-demo-build`.
4. Choose **Start build**.
5. Wait for the build to finish.

#### **3. Monitor the Build Logs**

After the build starts, open the build details and review the **Build logs**.

Check the logs for the following stages:

- **Install:** The Java and Maven environment is prepared.
- **Pre-build:** The environment is checked and prepared for testing.
- **Build:** Maven compiles the application and executes the unit tests.
- **Post-build:** The build process completes and the output artifacts are prepared, if configured.

If an error occurs, review the logs to identify the failed command. Common causes include an incorrect Java version, invalid Maven configuration, missing dependencies, or failing unit tests.

#### **4. Verify the Build Result**

After the build completes, check the **Build status** in the CodeBuild console.

A successful build should show the status **Succeeded**.

If the build fails, the status will show **Failed**. Review the error messages, correct the problem in the source code or build configuration, and start another build.

{{% notice info %}}
A successful build indicates that the configured build commands completed successfully. It does not by itself prove that the application has been deployed or that every application feature works correctly.
{{% /notice %}}

#### **5. Verify the Application Artifact**

If the build is configured to produce an artifact, verify that the application package is generated.

For this **Spring Boot Maven project**, the application package is typically a JAR file located in the `target/` directory.

If the project is integrated with **AWS CodePipeline**, verify that the build output is configured correctly for