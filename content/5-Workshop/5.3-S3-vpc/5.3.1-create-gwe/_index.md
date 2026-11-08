---
title: "Prepare the Spring Boot Application"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3.1. </b> "
---

#### **1. Check the Development Environment**

Before building the web application, make sure that **Java 17**, **Git**, and **Maven** are available on your computer.

Open **PowerShell** or the terminal in **VS Code** and run the following commands:

```powershell
java -version
git --version
```

To check whether the project includes the Maven Wrapper, navigate to the project directory and run:

```powershell
.\mvnw.cmd -version
```

If the project does not contain `mvnw.cmd`, install Maven or configure the project to use an available Maven installation.

#### **2. Open the Project**

Open the existing **cicd-aws-demo** project in **VS Code**.

The project should contain the following main files and directories:

```text
cicd-aws-demo/
├── src/
│   ├── main/
│   │   └── java/
│   └── test/
│       └── java/
├── pom.xml
├── buildspec.yml
├── appspec.yml
└── scripts/
```

- **`src/main/java/`** contains the application source code.
- **`src/test/java/`** contains the unit tests.
- **`pom.xml`** defines the Maven project and its dependencies.
- **`buildspec.yml`** contains the build instructions for AWS CodeBuild.
- **`appspec.yml`** defines the deployment instructions for AWS CodeDeploy.
- **`scripts/`** contains the deployment scripts.

#### **3. Build the Web Application**

In the VS Code terminal, navigate to the project root directory:

```powershell
cd "cd D:\cicd-aws-demo"
```

If your project is stored in another location, replace the path with your actual project directory.

Run the following command to build the application and execute the unit tests:

```powershell
.\mvnw.cmd clean package
```

If the build succeeds, Maven will generate the application package in the **`target/`** directory.

Look for the generated **`.jar`** file in that directory.

#### **4. Run the Application Locally**

Run the Spring Boot application using the generated JAR file:

```powershell
java -jar target/<application-name>.jar
```

Replace **`<application-name>.jar`** with the actual JAR filename generated in the `target/` directory.

Open a browser and visit the application's configured local URL, typically:

`http://localhost:8080`

If the application starts successfully and the page responds as expected, the local application is ready for the next step.

#### **5. Expected Result**

After completing this section, you should have:

- A working **Spring Boot web application**.
- A successful local **Maven build**.
- Unit tests executed during the build.
- A generated JAR package in the **`target/`** directory.

#### **Content**

- [Push the Source Code to GitHub](../5.3.2-push-to-github/)
