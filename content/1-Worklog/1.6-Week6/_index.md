---
title: "Week 6 Worklog"
date: 2026-09-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives

* Understand the role of AWS CodeBuild in an automated CI/CD pipeline.
* Learn how to configure a build project using source code stored on GitHub.
* Understand the purpose and structure of the `buildspec.yml` file.
* Configure the build environment and commands required to compile and test the Spring Boot application.
* Verify the build output before proceeding to the deployment stage.

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----| --- | --- | --- | --- |
| 1   | - Study AWS CodeBuild and its role in the CI/CD process. <br> - Understand how CodeBuild automates the compilation, testing, and packaging of application source code. | 09/19/2026 | 09/19/2026 | [AWS CodeBuild User Guide](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |
| 2   | - Review the source code repository on GitHub. <br> - Identify the project files required for the build process, including `pom.xml` and the unit test files. | 09/20/2026 | 09/20/2026 | [AWS CodeBuild Source](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) |
| 3   | - Learn the structure of the `buildspec.yml` file. <br> - Identify the install, pre-build, build, and post-build phases. | 09/21/2026 | 09/21/2026 | [Build Specification Reference](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) |
| 4   | - Prepare the build specification for the Spring Boot application. <br> - Configure Maven commands to compile the source code, run unit tests, and package the application into a JAR file. | 09/22/2026 | 09/23/2026 | [Maven Documentation](https://maven.apache.org/guides/) |
| 5   | - Create or review an AWS CodeBuild project and configure its source repository and build environment. <br> - Run a build and inspect the logs, test results, and generated artifacts. <br> - Identify and troubleshoot any build errors. | 09/24/2026 | 09/25/2026 | [AWS CodeBuild User Guide](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |

### Week 6 Achievements

* Understood the purpose of AWS CodeBuild and its role in automating the application build process.
* Became familiar with the structure and main phases of the `buildspec.yml` file.
* Identified the Maven commands required to compile, test, and package the Spring Boot application.
* Learned how to configure the source repository and build environment for an AWS CodeBuild project.
* Understood how to inspect build logs and identify errors during the automated build process.
* Prepared the project for the next stage: preparing the AWS environment for application deployment.
