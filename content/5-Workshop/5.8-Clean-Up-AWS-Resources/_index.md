---
title: "Clean Up"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

After completing the CI/CD workshop, remove the AWS resources that are no longer required. This helps prevent unnecessary charges.

**Before deleting resources:** Save the screenshots and logs needed for the graduation report. Confirm that each resource belongs to this workshop and is not shared with another project.

## 1. Delete the CodePipeline Pipeline

1. Open the **AWS CodePipeline** console.
2. Select the pipeline created for `cicd-aws-demo`.
3. Confirm that you have recorded the pipeline execution results.
4. Delete the pipeline and confirm the action.

Deleting the pipeline does not automatically delete its CodeBuild project, CodeDeploy application, S3 artifact bucket, or IAM roles.

## 2. Delete the CodeDeploy Application

1. Open the **AWS CodeDeploy** console.
2. Select **Applications**.
3. Open `cicd-aws-demo-app`.
4. Delete the deployment group `cicd-aws-demo-deployment-group`.
5. Delete the application `cicd-aws-demo-app`.

Only delete the application and deployment group created for this workshop.

## 3. Delete the CodeBuild Project

1. Open the **AWS CodeBuild** console.
2. Select **Build projects**.
3. Select `cicd-aws-demo-build`.
4. Choose **Delete build project**.
5. Confirm the deletion.

The project's CloudWatch logs and S3 artifacts may remain and must be reviewed separately.

## 4. Terminate the Workshop EC2 Instance

1. Open the **Amazon EC2** console.
2. Select **Instances**.
3. Identify the instance created for this workshop.
4. Confirm that no other application depends on it.
5. Choose **Instance state → Terminate instance** and confirm.

Termination permanently removes the instance. Review attached EBS volumes, Elastic IP addresses, load balancers, and other related resources separately because some may continue to incur charges.

Do not terminate a shared instance or an instance that hosts other applications.

## 5. Delete the S3 Artifact Bucket

1. Open the **Amazon S3** console.
2. Identify the bucket used for CodePipeline artifacts or deployment packages.
3. Verify that the bucket is dedicated to this workshop.
4. Download any files required for the report.
5. Empty the bucket and delete it if it is no longer needed.

If versioning is enabled, remove the necessary object versions and delete markers before deleting the bucket.

Do not delete a bucket shared with other projects.

## 6. Delete Unneeded CloudWatch Logs

1. Open the **Amazon CloudWatch** console.
2. Select **Logs → Log groups**.
3. Identify the log groups created by the workshop.
4. Save any logs needed for documentation.
5. Delete only the log groups that are no longer required.

Keep logs from shared applications and services.

## 7. Review IAM Roles

1. Open the **IAM** console.
2. Select **Roles**.
3. Review the roles created for CodeBuild, CodeDeploy, and the EC2 instance.
4. Check whether any remaining resource still uses each role.
5. Delete only unused roles that were created specifically for this workshop.

Do not delete shared roles or roles used by other AWS workloads.

## 8. Verify Cleanup

Review the resources created during the workshop.

| Resource | Expected final state |
|---|---|
| CodePipeline | Deleted if no longer needed |
| CodeDeploy application and deployment group | Deleted if no longer needed |
| CodeBuild project | Deleted if no longer needed |
| EC2 instance | Terminated if dedicated to the workshop |
| S3 artifact bucket | Deleted if dedicated to the workshop |
| CloudWatch log groups | Unneeded logs removed |
| IAM roles | Unused workshop-specific roles removed |

Finally, open **AWS Billing and Cost Management** and review current charges and remaining billable resources. Billing information may take time to reflect resource deletion.

## Result

The workshop resources have been reviewed and unnecessary resources have been removed. Evidence of the successful CI/CD workflow has been saved for the graduation report.