---
title: "Week 8 Worklog"
date: 2026-10-17
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives

* Understand the role of AWS CodeDeploy in the CI/CD pipeline.
* Learn how to prepare the application files and deployment instructions.
* Understand the purpose and structure of the `appspec.yml` file.
* Learn how to configure deployment lifecycle scripts for a Spring Boot application.
* Prepare the deployment process from an application artifact to an Amazon EC2 instance.

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----| --- | --- | --- | --- |
| 1   | - Study AWS CodeDeploy and its role in automating application deployment. <br> - Understand the basic deployment workflow from a build artifact to an EC2 instance. | 10/17/2026 | 10/17/2026 | [AWS CodeDeploy User Guide](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| 2   | - Learn about CodeDeploy applications, deployment groups, and revisions. <br> - Understand how CodeDeploy identifies the target EC2 instances. | 10/18/2026 | 10/18/2026 | [CodeDeploy Components](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps.html) |
| 3   | - Study the structure of the `appspec.yml` file. <br> - Identify how the file specifies application files, destination paths, and deployment lifecycle hooks. | 10/19/2026 | 10/19/2026 | [AppSpec File Reference](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html) |
| 4   | - Prepare or review the deployment scripts, including scripts to stop the existing application, install dependencies, and start the application. <br> - Review script permissions and execution requirements on Linux. | 10/20/2026 | 10/21/2026 | [CodeDeploy Lifecycle Events](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html) |
| 5   | - Review the CodeDeploy agent requirements on the EC2 instance. <br> - Learn how to create a deployment revision containing the application artifact, `appspec.yml`, and required scripts. <br> - Review deployment logs and common failure causes. | 10/22/2026 | 10/23/2026 | [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html) |

### Week 8 Achievements

* Understood the role of AWS CodeDeploy in automating application deployment.
* Became familiar with CodeDeploy applications, deployment groups, and revisions.
* Understood how the `appspec.yml` file defines the deployment process and lifecycle hooks.
* Identified the scripts required to stop and start the Spring Boot application and prepare its runtime environment.
* Learned about the CodeDeploy agent and its role in communicating with the deployment service.
* Understood how to review deployment logs and investigate common deployment errors.
* Prepared the deployment configuration for integration with AWS CodePipeline in the following week.
