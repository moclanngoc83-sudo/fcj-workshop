---
title: "Push the Source Code to GitHub"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.3.2. </b> "
---

#### **1. Check the Project Files**

Before uploading the source code, make sure that your **Spring Boot project** is stored in the `D:\cicd-aws-demo` directory.

The project should contain the following files and directories:

```text
cicd-aws-demo/
├── src/
├── pom.xml
├── buildspec.yml
├── appspec.yml
└── scripts/
```

The `src/` directory contains the application source code and unit tests. The `pom.xml` file defines the Maven project and its dependencies.

#### **2. Open the Project Terminal**

Open **PowerShell** or the terminal in **VS Code** and navigate to the project directory:

```powershell
cd D:\cicd-aws-demo
```

Check the current Git status:

```powershell
git status
```

If the project is already connected to GitHub, the command will show the current branch and any changes that have not been committed.

#### **3. Check the GitHub Remote Repository**

Check the remote repository configured for the project:

```powershell
git remote -v
```

The expected repository URL is:

`https://github.com/moclanngoc83-sudo/cicd-aws-demo.git`

If the remote repository is already configured correctly, you do not need to add it again.

If the remote URL is incorrect, update it using:

```powershell
git remote set-url origin https://github.com/moclanngoc83-sudo/cicd-aws-demo.git
```

If no remote named `origin` exists, add it using:

```powershell
git remote add origin https://github.com/moclanngoc83-sudo/cicd-aws-demo.git
```

#### **4. Commit the Source Code**

Add the project files to Git's staging area:

```powershell
git add .
```

Commit the changes:

```powershell
git commit -m "Prepare Spring Boot application for CI/CD"
```

If Git reports that there is nothing to commit, the current files may already have been committed.

If Git asks you to configure your identity, set your own name and email address:

```powershell
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Replace the example values with your actual Git name and email address, then retry the commit if necessary.

#### **5. Push the Source Code to GitHub**

Check the current branch:

```powershell
git branch
```

If the branch is named `main`, push the source code using:

```powershell
git push -u origin main
```

If the current branch has another name, replace `main` with the actual branch name.

If Git requests authentication, complete the authentication process using the method supported by your GitHub setup.

#### **6. Verify the GitHub Repository**

Open the following repository in your browser:

[https://github.com/moclanngoc83-sudo/cicd-aws-demo](https://github