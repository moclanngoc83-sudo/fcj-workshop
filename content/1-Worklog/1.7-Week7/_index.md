---
title: "Week 7 Worklog"
date: 2026-10-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives

* Understand the AWS resources required to deploy a Spring Boot web application.
* Learn how to prepare an Amazon EC2 instance for application deployment.
* Understand security groups, key pairs, and SSH connections for accessing EC2.
* Learn about IAM roles and permissions required by AWS deployment services.
* Prepare the deployment environment for the upcoming AWS CodeDeploy configuration.

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----| --- | --- | --- | --- |
| 1   | - Review the architecture of the CI/CD project and identify the AWS resources required for deployment. <br> - Understand the role of Amazon EC2 as the application hosting environment. | 10/03/2026 | 10/03/2026 | [Amazon EC2 Documentation](https://docs.aws.amazon.com/ec2/) |
| 2   | - Study EC2 instance types, Amazon Machine Images (AMIs), and storage options. <br> - Identify a suitable operating system and instance configuration for the demo application. | 10/04/2026 | 10/04/2026 | [EC2 Instance Types](https://docs.aws.amazon.com/ec2/latest/instancetypes/instance-types.html) |
| 3   | - Learn how to configure EC2 security groups to control inbound and outbound traffic. <br> - Review SSH access and the network port required by the Spring Boot application. | 10/05/2026 | 10/05/2026 | [EC2 Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-security-groups.html) |
| 4   | - Study IAM roles and policies for EC2 and AWS deployment services. <br> - Understand the permissions needed for EC2 to communicate with AWS services and retrieve deployment instructions. | 10/06/2026 | 10/07/2026 | [IAM Roles for EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html) |
| 5   | - Prepare or review the EC2 deployment environment. <br> - Check operating system access, required runtime dependencies, and application directory permissions. <br> - Review the prerequisites for installing the CodeDeploy agent. | 10/08/2026 | 10/09/2026 | [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html) |

### Week 7 Achievements

* Identified the AWS resources required to host and deploy the Spring Boot web application.
* Understood the basic EC2 configuration options, including instance types, AMIs, and storage.
* Learned how security groups control network traffic to the EC2 instance.
* Understood the purpose of IAM roles and permissions in enabling AWS services to communicate securely.
* Identified the environment requirements for running the application on EC2.
* Prepared the deployment plan for the next stage: configuring AWS CodeDeploy.
