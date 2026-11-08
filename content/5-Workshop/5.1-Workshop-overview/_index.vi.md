---
title : "Giới thiệu"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

#### CI/CD – Tích hợp liên tục và Triển khai liên tục

+ **Tích hợp liên tục (Continuous Integration – CI)** là phương pháp phát triển phần mềm trong đó các thay đổi về mã nguồn được tích hợp thường xuyên vào một kho lưu trữ chung, sau đó được tự động xây dựng (Build) và kiểm thử.

+ **Triển khai liên tục (Continuous Deployment – CD)** tự động hóa quá trình phát hành các thay đổi của ứng dụng đến môi trường đích sau khi các bước xây dựng và kiểm thử cần thiết đã hoàn tất thành công.

+ **Các dịch vụ CI/CD của AWS** giúp tự động hóa quy trình phân phối phần mềm, giảm thiểu các thao tác thủ công và nâng cao tính nhất quán trong quá trình triển khai.

#### Tổng quan về Workshop

Trong Workshop này, bạn sẽ xây dựng và triển khai một ứng dụng web đơn giản bằng Java và Spring Boot. Bạn sẽ sử dụng các dịch vụ AWS để tự động hóa quá trình xây dựng, kiểm thử và triển khai ứng dụng.

+ **"Kho lưu trữ mã nguồn (Source Repository)"** sử dụng GitHub để lưu trữ mã nguồn của ứng dụng. Những thay đổi được đẩy lên kho lưu trữ sẽ kích hoạt quy trình CI/CD.

+ **"Xây dựng và kiểm thử (Build and Test)"** sử dụng AWS CodeBuild để biên dịch ứng dụng, chạy các bài kiểm thử đơn vị (Unit Test) và tạo ra tệp triển khai (Deployment Artifact). Quy trình sẽ dừng lại nếu quá trình Build hoặc kiểm thử thất bại.

+ **"Triển khai (Deployment)"** sử dụng AWS CodeDeploy để triển khai ứng dụng lên một máy chủ Amazon EC2. Amazon S3 lưu trữ tệp triển khai được sử dụng trong quá trình này.

+ **"Giám sát (Monitoring)"** sử dụng Amazon CloudWatch để thu thập các nhật ký (Logs) liên quan và theo dõi quá trình triển khai.

Mục tiêu là xây dựng một quy trình triển khai có thể lặp lại, trong đó mỗi khi mã nguồn thay đổi, ứng dụng có thể được tự động xây dựng, kiểm thử và triển khai.

**Kết quả mong đợi**

Sau khi hoàn thành Workshop, bạn sẽ có một ứng dụng web đơn giản đang chạy trên Amazon EC2 và một quy trình CI/CD tự động có khả năng xây dựng, kiểm thử và triển khai các bản cập nhật ứng dụng từ GitHub.