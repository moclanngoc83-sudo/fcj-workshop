---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 4. </b> "
---


# CI/CD cho ứng dụng Web đơn giản trên AWS

#### Tổng quan

**Continuous Integration and Continuous Delivery/Deployment (CI/CD)** giúp tự động hóa quy trình xây dựng, kiểm thử và triển khai các ứng dụng phần mềm.

Trong workshop này, bạn sẽ tìm hiểu cách xây dựng một ứng dụng web đơn giản bằng Java và Spring Boot, sau đó triển khai ứng dụng lên Amazon EC2 thông qua một quy trình CI/CD tự động.

Bạn sẽ sử dụng GitHub để lưu trữ mã nguồn, AWS CodePipeline để điều phối quy trình, AWS CodeBuild để xây dựng ứng dụng và chạy các bài kiểm thử đơn vị, Amazon S3 để lưu trữ các build artifact và AWS CodeDeploy để triển khai ứng dụng lên EC2 instance.

Workshop bao gồm các giai đoạn sau:

+ **Source (Mã nguồn)** - Lưu trữ mã nguồn ứng dụng trên GitHub và kích hoạt pipeline khi mã nguồn có thay đổi.
+ **Build and Test (Xây dựng và kiểm thử)** - Sử dụng AWS CodeBuild để biên dịch ứng dụng và thực thi các bài kiểm thử đơn vị tự động.
+ **Quality Gate (Cổng kiểm soát chất lượng)** - Dừng pipeline nếu quá trình build hoặc các bài kiểm thử đơn vị thất bại.
+ **Deploy (Triển khai)** - Sử dụng AWS CodeDeploy để triển khai ứng dụng lên Amazon EC2.
+ **Monitoring (Giám sát)** - Sử dụng Amazon CloudWatch để giám sát logs và các hoạt động triển khai.

#### Nội dung

1. [Tổng quan về Workshop](5.1-Workshop-overview/)
2. [Các điều kiện tiên quyết](5.2-Prerequiste/)
3. [Xây dựng ứng dụng Web](5.3-build-web-application/)
4. [Cấu hình CI với AWS CodeBuild](5.4-codebuild/)
5. [Triển khai ứng dụng bằng AWS CodeDeploy](5.5-codedeploy/)
6. [Tạo quy trình CI/CD](5.6-codepipeline/)
7. [Giám sát và kiểm thử](5.7-monitoring-testing/)
8. [Dọn dẹp tài nguyên AWS](5.8-cleanup/)