---
title: "Week 5 Worklog"
date: 2026-09-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives

* Understand the fundamentals of unit testing in a Spring Boot web application.
* Learn how to write and execute unit tests using JUnit and Mockito.
* Verify application functionality before integrating the project with AWS CodeBuild.
* Understand the Maven commands used to run tests and package the application.
* Prepare the application and test configuration for the automated build process.

### Tasks to be carried out this week

| Day | Task | Start Date | Completion Date | Reference Material |
|-----| --- | --- | --- | --- |
| 1   | - Review the purpose of unit testing in software development. <br> - Understand how unit tests help detect errors before deployment. | 09/12/2026 | 09/12/2026 | [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/) |
| 2   | - Review the existing Spring Boot project structure and test directory. <br> - Identify the application components that need to be tested. | 09/13/2026 | 09/13/2026 | [Spring Boot Testing](https://docs.spring.io/spring-boot/reference/testing/index.html) |
| 3   | - Study how to write unit tests using JUnit. <br> - Explore Mockito for isolating dependencies when testing application components. | 09/14/2026 | 09/14/2026 | [Mockito Documentation](https://site.mockito.org/) |
| 4   | - Write or review unit tests for the application's main functions. <br> - Run the tests and examine the results. <br> - Identify and correct errors found during testing. | 09/15/2026 | 09/16/2026 | [JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/) |
| 5   | - Learn how to use Maven to compile the source code, execute tests, and package the application. <br> - Run `mvnw.cmd clean test` and `mvnw.cmd clean package` in the local development environment. <br> - Review the files and commands needed for the upcoming AWS CodeBuild configuration. | 09/17/2026 | 09/18/2026 | [Maven Build Lifecycle](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html) |

### Week 5 Achievements

* Understood the role of unit testing in verifying application functionality and improving software quality.
* Became familiar with JUnit and the basic principles of writing unit tests.
* Learned how Mockito can be used to isolate dependencies during testing, where applicable.
* Practiced running unit tests and reviewing test results using Maven.
* Understood the Maven build process, including compiling source code, running tests, and packaging the application.
* Identified the application files and test commands that will be used in the AWS CodeBuild stage.
* Prepared the project for the next stage: configuring an automated build process with AWS CodeBuild.
