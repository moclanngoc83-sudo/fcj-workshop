---
title: "Clean Up"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

Congratulations on completing the Simple Web App CI/CD workshop!

In this workshop, you configured a web application deployment workflow using AWS services. Before finishing, clean up the resources created during the workshop to avoid unnecessary AWS charges.

## 1. Stop the CI/CD Pipeline

1. Open the **AWS CodePipeline** console.
2. Select the pipeline created for this workshop.
3. Record the pipeline name for your project report.
4. If the pipeline is no longer needed, delete it from the pipeline details page and confirm the deletion.

Deleting a pipeline does not automatically delete all resources associated with it.

## 2. Delete the CodeDeploy Resources

1. Open the **AWS CodeDeploy** console.
2. Select **Applications**.
3. Open `cicd-aws-demo-app`.
4. Delete the deployment group `cicd-aws-demo-deployment-group`.
5. Delete the application `cicd-aws-demo-app`.

Make sure you select the resources created specifically for this workshop.

## 3. Delete the CodeBuild Project

1. Open the **AWS CodeBuild** console.
2. Select **Build projects**.
3. Choose the project `cicd-aws-demo-build`.
4. Select **Delete build project** and confirm.

Deleting the CodeBuild project does not automatically remove its CloudWatch log groups or S3 artifacts.

## 4. Terminate the EC2 Instance

If the EC2 instance was created only for this workshop and is no longer required:

1. Open the **Amazon EC2** console.
2. Select **Instances**.
3. Select the workshop instance.
4. Choose **Instance state → Terminate instance**.
5. Confirm the termination.

**Warning:** Terminating an instance is irreversible. Do not terminate an instance that hosts other applications or is shared with another project.

After termination, check whether any associated EBS volumes, Elastic IP addresses, load balancers, or other billable resources remain. Delete only resources that are no longer needed.

## 5. Delete the S3 Artifacts

1. Open the **Amazon S3** console.
2. Identify the bucket used to store CodePipeline artifacts or deployment packages.
3. Verify that the bucket is dedicated to this workshop.
4. Empty the bucket if its contents are no longer needed.
5. Delete the bucket and confirm the action.

**Important:** Emptying a bucket permanently removes its objects. Do not delete a shared bucket or a bucket containing files needed by other projects.

If S3 versioning is enabled, remove the required object versions and delete markers before deleting the bucket.

## 6. Delete CloudWatch Logs

1. Open the **Amazon CloudWatch** console.
2. Select **Logs → Log groups**.
3. Identify the log groups created by CodeBuild and the deployment application.
4. Review the contents to ensure that the logs are no longer required.
5. Delete only the workshop-specific log groups.

Keep