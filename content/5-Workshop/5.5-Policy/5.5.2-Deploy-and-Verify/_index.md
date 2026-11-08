---
title: "Deploy and Verify the Application"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.5.2. </b> "
---

## Step 1: Prepare the Deployment Files

AWS CodeDeploy needs an application revision containing the files to deploy and an `appspec.yml` file describing the deployment instructions.

In the project directory, verify that the deployment files exist:

```text
cicd-aws-demo/
├── appspec.yml
├── buildspec.yml
├── pom.xml
├── scripts/
│   ├── install_dependencies.sh
│   ├── start_server.sh
│   └── stop_server.sh
└── src/
```

The filenames and directory structure in the revision must match the paths specified in `appspec.yml`.

For an EC2 deployment, the AppSpec file must be named `appspec.yml` and be located at the root of the deployment revision.

## Step 2: Build the Application

Build and test the Spring Boot application before deploying it.

From the project directory, run:

```powershell
.\mvnw.cmd clean test package
```

Check the build output. Maven should finish successfully, and the application JAR should be generated under `target/`.

For example:

```powershell
Get-ChildItem .\target\*.jar
```

If the tests fail or the JAR is not generated, resolve the build problem before continuing.

## Step 3: Start a Deployment

There are two ways to start a deployment.

### Option A: Deploy through CodePipeline

Use this option when the project is connected to AWS CodePipeline.

1. Open **AWS CodePipeline**.
2. Select the pipeline configured for `cicd-aws-demo`.
3. Choose **Release change** if the pipeline is not triggered automatically.
4. Wait for the Source, Build, and Deploy stages to run.
5. Open the Deploy stage to inspect its status.

The deployment stage should use the CodeDeploy application `cicd-aws-demo-app` and deployment group `cicd-aws-demo-deployment-group`.

### Option B: Create a Manual Deployment

Use this option to test CodeDeploy before connecting it to CodePipeline.

1. Open **AWS CodeDeploy**.
2. Select **Applications** and open `cicd-aws-demo-app`.
3. Select the deployment group `cicd-aws-demo-deployment-group`.
4. Choose **Create deployment**.
5. Select the appropriate revision source.

   For an S3 revision, select the S3 bucket, object key, and version or ETag as required. The uploaded revision must contain `appspec.yml` at its root.

6. Choose **Create deployment**.
7. Wait for the deployment to finish.

A manual deployment requires a packaged revision uploaded to the selected source. Building a JAR locally alone does not create an S3 deployment revision.

## Step 4: Check the Deployment Status

In CodeDeploy, open the deployment and inspect its status.

- **Succeeded:** The deployment lifecycle completed successfully.
- **Failed:** Open the deployment details and inspect the failed lifecycle event.
- **In Progress:** Wait for the deployment to complete before testing the application.

Check the lifecycle events to identify whether the failure occurred during DownloadBundle, Install, ApplicationStart, or another deployment hook.

## Step 5: Check the Application on EC2

Connect to the EC2 instance and inspect the application process and logs.

For a Linux instance, useful commands include:

```bash
ps -ef | grep java
```

```bash
sudo journalctl -u codedeploy-agent --no-pager -n 100
```

If the application writes to a file, inspect the application log at the configured log path.

If the deployment succeeds but the application does not respond, check that:

- The Spring Boot process is running.
- The application listens on the expected port.
- The EC2 security group permits inbound traffic to that port.
- The deployment scripts have the correct file paths and executable permissions.

## Step 6: Test the Web Application

If the Spring Boot application is configured to listen on port `8080`, open the following address in a browser:

```text
http://<EC2-Public-IP>:8080
```

Replace `<EC2-Public-IP>` with the public IPv4 address of the actual EC2 instance.

If the application uses a different port or a specific endpoint, use the configured port and endpoint instead.

If the page does not load, verify the application's health locally on the EC2 instance and check the EC2 security group and network configuration.

## Step 7: Record the Results

Record the following information for the project report:

| Item | Expected result |
|---|---|
| CodeDeploy application | `cicd-aws-demo-app` exists |
| Deployment group | `cicd-aws-demo-deployment-group` exists |
| Deployment status | `Succeeded` |
| Application process | Running on EC2 |
| Web access test | Application responds at the configured address |

Capture screenshots of the deployment status, lifecycle events, and successful browser test as evidence for the graduation report.

## Troubleshooting

| Problem | What to check |
|---|---|
| Deployment fails before installation | Revision source, IAM permissions, and `appspec.yml` location |
| EC2 instance is not selected | Instance tags and deployment group selection criteria |
| CodeDeploy agent is unavailable | Agent installation, service status, and network connectivity |
| Application fails to start | Script permissions, file paths, Java version, and application logs |
| Browser cannot connect | Application port, process status, and EC2 security group |

## Result

The application is deployed to EC2 and verified through deployment status, instance checks, and a browser test. Once manual deployment works, the same application and deployment group can be used by AWS CodePipeline for automated deployments.