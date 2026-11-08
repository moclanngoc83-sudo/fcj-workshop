---
title: "Configure AWS CodeBuild"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.4.1. </b> "
---

#### **Overview**

In this section, you will configure **AWS CodeBuild** to build the **Spring Boot web application** stored in your **GitHub repository**.

AWS CodeBuild is a fully managed build service that compiles source code, runs unit tests, and generates build artifacts. In this workshop, CodeBuild will use **Maven** to build the application and execute the tests.

Before starting, make sure that:

- The application source code has been pushed to **GitHub**.
- The project contains a valid **`pom.xml`** file.
- The project contains a **`buildspec.yml`** file.
- You have an **AWS account** with permission to create and configure CodeBuild resources.

#### **Create an IAM service role**

AWS CodeBuild needs an **IAM service role** to access the resources required during the build process.

1. Open the **IAM console** in the AWS Management Console.
2. Choose **Roles**, then click **Create role**.
3. For the trusted entity type, select **AWS service**.
4. Select **CodeBuild** as the use case.
5. Follow the console instructions to create the role.
6. Give the role a descriptive name, such as `CodeBuildServiceRole`.

Attach only the permissions required by your build process. If the build stores artifacts in **Amazon S3** or retrieves source code through a configured connection, make sure the role has the appropriate permissions.

{{% notice warning %}}
Follow the principle of **least privilege**. Do not grant unrestricted permissions to all AWS resources unless they are genuinely required.
{{% /notice %}}

#### **Create a CodeBuild project**

1. Open the **AWS CodeBuild console**.
2. Choose **Build projects**, then click **Create build project**.
3. In **Project configuration**, enter the project name:

   `cicd-aws-demo-build`

4. Under **Source**, select the source provider configured for your project. If using a GitHub connection, authorize and select the correct repository.
5. Under **Environment**, configure the