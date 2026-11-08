---
title: "Cấu hình AWS CodeBuild"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.4.1. </b> "
---

#### **Tổng quan**

Trong phần này, bạn sẽ cấu hình **AWS CodeBuild** để xây dựng **ứng dụng web Spring Boot** được lưu trữ trong **repository GitHub** của bạn.

AWS CodeBuild là dịch vụ xây dựng ứng dụng được quản lý hoàn toàn, có khả năng biên dịch mã nguồn, chạy các bài kiểm thử đơn vị và tạo ra các sản phẩm đầu ra của quá trình Build (Build Artifacts). Trong workshop này, CodeBuild sẽ sử dụng **Maven** để xây dựng ứng dụng và thực thi các bài kiểm thử.

Trước khi bắt đầu, hãy đảm bảo rằng:

- Mã nguồn ứng dụng đã được đẩy lên **GitHub**.
- Dự án có tệp **`pom.xml`** hợp lệ.
- Dự án có tệp **`buildspec.yml`**.
- Bạn có **tài khoản AWS** với quyền tạo và cấu hình các tài nguyên CodeBuild.

#### **Tạo IAM Service Role**

AWS CodeBuild cần một **IAM Service Role** để truy cập các tài nguyên cần thiết trong quá trình Build.

1. Mở **IAM Console** trong AWS Management Console.
2. Chọn **Roles**, sau đó nhấn **Create role**.
3. Tại mục loại thực thể đáng tin cậy (Trusted entity type), chọn **AWS service**.
4. Chọn **CodeBuild** làm trường hợp sử dụng (Use case).
5. Làm theo hướng dẫn trên Console để tạo Role.
6. Đặt tên mô tả cho Role, ví dụ: `CodeBuildServiceRole`.

Chỉ gắn những quyền cần thiết cho quá trình Build. Nếu quá trình Build lưu trữ Artifacts trên **Amazon S3** hoặc lấy mã nguồn thông qua một kết nối đã cấu hình, hãy đảm bảo Role có các quyền truy cập phù hợp.

{{% notice warning %}}
Tuân thủ nguyên tắc **đặc quyền tối thiểu (Least Privilege)**. Không cấp quyền truy cập không giới hạn đối với tất cả tài nguyên AWS trừ khi thực sự cần thiết.
{{% /notice %}}

#### **Tạo CodeBuild Project**

1. Mở **AWS CodeBuild Console**.
2. Chọn **Build projects**, sau đó nhấn **Create build project**.
3. Trong mục **Project configuration**, nhập tên Project:

   `cicd-aws-demo-build`

4. Trong mục **Source**, chọn nhà cung cấp mã nguồn (Source provider) đã được cấu hình cho dự án. Nếu sử dụng kết nối GitHub, hãy cấp quyền truy cập và chọn đúng repository.
5. Trong mục **Environment**, cấu hình các thiết lập môi trường theo hướng dẫn ở phần tiếp theo.