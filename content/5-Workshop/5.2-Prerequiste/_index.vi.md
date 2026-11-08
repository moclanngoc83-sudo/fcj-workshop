---
title: "Các điều kiện cần chuẩn bị"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

#### Tổng quan

Trước khi bắt đầu Workshop này, cần chuẩn bị các công cụ phát triển, kho lưu trữ mã nguồn và môi trường AWS cần thiết.

Workshop sử dụng một ứng dụng web đơn giản được xây dựng bằng Java Spring Boot cùng với các dịch vụ AWS để tự động hóa quá trình xây dựng, kiểm thử, triển khai và giám sát.

#### Công cụ phát triển

Đảm bảo các công cụ sau đã có sẵn trên máy tính cá nhân:

+ **Java Development Kit (JDK 17)** - Được sử dụng để biên dịch và chạy ứng dụng Spring Boot.
+ **Apache Maven** - Được sử dụng để quản lý các thư viện phụ thuộc, xây dựng ứng dụng và thực thi các bài kiểm thử đơn vị. Có thể sử dụng Maven Wrapper (`mvnw`) nếu công cụ này được tích hợp trong dự án.
+ **Git** - Được sử dụng để quản lý các thay đổi của mã nguồn.
+ **Visual Studio Code hoặc IntelliJ IDEA** - Được sử dụng để chỉnh sửa mã nguồn ứng dụng.
+ **Trình duyệt web** - Được sử dụng để truy cập ứng dụng sau khi triển khai và AWS Management Console.

Kiểm tra phiên bản Java đã cài đặt:

```powershell
java -version
```

Kiểm tra phiên bản Git:

```powershell
git --version
```

#### Kho lưu trữ GitHub

Tạo một kho lưu trữ GitHub để lưu trữ mã nguồn của ứng dụng.

Kho lưu trữ cần bao gồm:

+ Mã nguồn ứng dụng Spring Boot.
+ Các bài kiểm thử đơn vị (Unit Test).
+ File `pom.xml` dùng để cấu hình Maven.
+ File `buildspec.yml` dành cho AWS CodeBuild.
+ File `appspec.yml` dành cho AWS CodeDeploy.
+ Các tập lệnh triển khai cần thiết cho ứng dụng.

#### Tài khoản AWS và quyền truy cập

Cần có một tài khoản AWS với quyền tạo và cấu hình các tài nguyên cần thiết.

Workshop sử dụng các dịch vụ AWS sau:

+ **AWS CodePipeline** - Điều phối quy trình CI/CD.
+ **AWS CodeBuild** - Xây dựng ứng dụng và thực thi các bài kiểm thử đơn vị.
+ **Amazon S3** - Lưu trữ các tệp triển khai (Build Artifact).
+ **AWS CodeDeploy** - Triển khai ứng dụng lên Amazon EC2.
+ **Amazon EC2** - Lưu trữ và chạy ứng dụng web.
+ **Amazon CloudWatch** - Thu thập nhật ký ứng dụng và thông tin giám sát.
+ **AWS Identity and Access Management (IAM)** - Kiểm soát quyền truy cập giữa các dịch vụ AWS.

Sử dụng IAM Role hoặc IAM User chỉ với những quyền cần thiết cho Workshop. Tránh sử dụng tài khoản AWS Root cho các công việc thông thường và không chia sẻ Access Key hoặc thông tin xác thực.

#### Lựa chọn Region

Chọn một AWS Region cho Workshop và sử dụng thống nhất Region đó đối với các dịch vụ được hỗ trợ.

Ghi lại Region đã chọn trước khi tạo tài nguyên để có thể dễ dàng xác định vị trí của quy trình CI/CD, S3 Bucket lưu trữ Artifact, các tài nguyên triển khai và cấu hình giám sát.

#### Các lưu ý về chi phí và bảo mật

+ Các tài nguyên AWS có thể phát sinh chi phí tùy thuộc vào cấu hình được lựa chọn và mức độ sử dụng.
+ Kiểm tra chi phí ước tính trước khi tạo các phiên bản EC2 hoặc những tài nguyên có tính phí khác.
+ Giới hạn quyền truy cập đầu vào vào cổng ứng dụng và chỉ cho phép truy cập quản trị từ các địa chỉ IP đáng tin cậy.
+ Không lưu trữ thông tin xác thực AWS trong kho lưu trữ mã nguồn.
+ Xóa các tài nguyên của Workshop sau khi hoàn thành dự án.

#### Danh sách kiểm tra trước khi bắt đầu

Trước khi chuyển sang phần tiếp theo, hãy xác nhận rằng:

+ Java và Git đã được cài đặt và hoạt động bình thường.
+ Mã nguồn ứng dụng đã có sẵn trên máy tính cá nhân.
+ Kho lưu trữ GitHub đã được tạo.
+ Bạn có thể đăng nhập vào AWS Management Console.
+ Bạn có quyền tạo các tài nguyên AWS cần thiết.