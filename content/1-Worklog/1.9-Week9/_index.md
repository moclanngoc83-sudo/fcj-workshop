---
title: "Week 9 Worklog"
date: 2026-10-24
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives

* Understand the role of AWS CodePipeline in automating the CI/CD workflow.
* Learn how to connect a GitHub repository to AWS CodePipeline.
* Integrate AWS CodeBuild and AWS CodeDeploy into a single pipeline.
* Understand how source code changes trigger the build and deployment stages.
* Learn how to monitor pipeline execution and troubleshoot common errors.

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----| --- | --- | --- | --- |
| 1   | - Study AWS CodePipeline and its role in automating software delivery. <br> - Review the Source, Build, and Deploy stages of the planned CI/CD workflow. | 10/24/2026 | 10/24/2026 | [AWS CodePipeline User Guide](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| 2   | - Review the GitHub repository and its connection to AWS CodePipeline. <br> - Understand how source code changes can initiate a pipeline execution. | 10/25/2026 | 10/25/2026 | [CodePipeline Source Actions](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference.html) |
| 3   | - Configure or review the Source stage to retrieve the application source code from GitHub. <br> - Identify the source artifact passed to the build stage. | 10/26/2026 | 10/26/2026 | [CodePipeline Source Actions](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference.html) |
| 4   | - Integrate AWS CodeBuild as the Build stage. <br> - Configure or review the Deploy stage using AWS CodeDeploy. <br> - Check the artifact flow between the pipeline stages. | 10/27/2026 | 10/28/2026 | [CodePipeline Pipeline Structure](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipeline-structure.html) |
| 5   | - Run or review a pipeline execution. <br> - Inspect the status and logs of each stage. <br> - Identify common source, build, permission, and deployment errors and review possible solutions. | 10/29/2026 | 10/30/2026 | [Troubleshooting CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/troubleshooting.html) |

### Week 9 Achievements

* Understood the purpose of AWS CodePipeline in coordinating automated application delivery.
* Identified the responsibilities of the Source, Build, and Deploy stages.
* Understood how GitHub, AWS CodeBuild, and AWS CodeDeploy work together in the CI/CD workflow.
* Learned how source artifacts are passed between pipeline stages.
* Became familiar with monitoring pipeline execution and reviewing stage logs.
* Identified common pipeline failures related to source configuration, build commands, IAM permissions, and deployment settings.
* Prepared the integrated CI/CD workflow for final testing, monitoring, and report completion.
