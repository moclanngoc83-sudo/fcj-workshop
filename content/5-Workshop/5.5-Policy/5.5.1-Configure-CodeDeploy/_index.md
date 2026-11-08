---
title: "Configure AWS CodeDeploy"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5.1. </b> "
---

## Step 1: Create an IAM Role for CodeDeploy

CodeDeploy needs permission to access EC2 instances and manage deployments.

1. Sign in to the [AWS Management Console](https://console.aws.amazon.com/).
2. Open **IAM** and select **Roles**.
3. Choose **Create role**.
4. Under Trusted entity type, select **AWS service**.
5. Select **CodeDeploy** as the use case.
6. Choose the CodeDeploy use case for EC2/on-premises deployments.
7. Enter the role name:

   `CodeDeployServiceRole`

8. Create the role.

After creation, open the role and verify that its trusted entity allows the CodeDeploy service to assume the role.

## Step 2: Create a CodeDeploy Application

1. Open **AWS CodeDeploy** in the AWS Console.
2. Select **Applications** from the navigation panel.
3. Choose **Create application**.
4. Enter the following configuration:

    - **Application name:** `cicd-aws-demo-app`
    - **Compute platform:** `EC2/On-premises`

5. Choose **Create application**.

The application should now appear in the CodeDeploy application list.

## Step 3: Create a Deployment Group

1. Open `cicd-aws-demo-app`.
2. Choose **Create deployment group**.
3. Enter the following configuration:

    - **Deployment group name:** `cicd-aws-demo-deployment-group`
    - **Service role:** `CodeDeployServiceRole`
    - **Deployment type:** In-place
    - **Environment configuration:** Amazon EC2 instances

4. Configure the EC2 instance selection criteria using tags.

   For example, if the EC2 instance has the tag `Name=ci-cd-demo-server`, select instances matching that tag. The tag key and value must match the actual EC2 instance.

5. Choose **Create deployment group**.

**Important:** The deployment group will not target an instance unless its selection criteria match that instance. The EC2 instance must also have an appropriate IAM instance profile and the CodeDeploy agent installed and running.

## Step 4: Prepare the EC2 Instance

Before deploying the application, verify the following:

- The EC2 instance is running.
- The instance has an IAM instance profile that allows it to access the required deployment artifacts and services.
- The CodeDeploy agent is installed and running.
- The instance can reach the required AWS endpoints.
- The application's security group allows the port used by the web application.

On a Linux EC2 instance, check the agent with:

```bash
sudo systemctl status codedeploy-agent
```

If the agent is installed but stopped, start it:

```bash
sudo systemctl start codedeploy-agent
```

If the command reports that the service does not exist, install the CodeDeploy agent for the instance's operating system and AWS Region before continuing.

## Step 5: Verify the Configuration

Before proceeding to deployment, check these items:

- The application `cicd-aws-demo-app` exists.
- The deployment group `cicd-aws-demo-deployment-group` exists.
- The deployment group targets the intended EC2 instance.
- The service role is selected correctly.
- The EC2 instance has the required instance profile.
- The CodeDeploy agent is running.

Once these checks are complete, continue to **Deploy and Verify the Application**.

## Result

At the end of this section, the CodeDeploy application and deployment group are configured and ready to receive a deployment from AWS CodePipeline or a manually created deployment.