---
title: "Xây dựng ứng dụng Web"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

#### **Xây dựng ứng dụng Web**

Trong phần này, bạn sẽ chuẩn bị một **ứng dụng web Java Spring Boot đơn giản** để sử dụng trong **quy trình CI/CD trên AWS**.

Ứng dụng sẽ được quản lý trong một **kho lưu trữ GitHub**. Khi mã nguồn có thay đổi, **AWS CodePipeline** sẽ phát hiện những thay đổi đó và khởi chạy quy trình CI/CD. **AWS CodeBuild** sẽ biên dịch mã nguồn và chạy các **bài kiểm thử đơn vị (Unit Test)** bằng **Maven**.

Nếu quá trình Build và kiểm thử thành công, ứng dụng sẽ được chuyển sang giai đoạn triển khai. Nếu xảy ra lỗi, quy trình CI/CD sẽ dừng lại để ngăn chặn việc triển khai một phiên bản ứng dụng chưa được xây dựng thành công.

#### **Tổng quan về ứng dụng**

Ứng dụng minh họa sử dụng các công nghệ sau:

- **Java 17** – Ngôn ngữ lập trình và môi trường thực thi ứng dụng.
- **Spring Boot** – Framework được sử dụng để xây dựng ứng dụng web.
- **Maven** – Công cụ quản lý các thư viện phụ thuộc và xây dựng ứng dụng.
- **JUnit** – Công cụ thực thi các bài kiểm thử đơn vị nhằm xác minh hoạt động của ứng dụng.
- **GitHub** – Nơi lưu trữ mã nguồn và kích hoạt quy trình CI/CD khi phát hiện các thay đổi.

#### **Cấu trúc dự án**

Dự án cần có các thư mục và tệp chính sau:

```text
cicd-aws-demo/
├── src/
│   ├── main/
│   │   └── java/          # Mã nguồn ứng dụng
│   └── test/
│       └── java/          # Các bài kiểm thử đơn vị
├── pom.xml                # Cấu hình Maven
├── buildspec.yml          # Các chỉ dẫn dành cho AWS CodeBuild
├── appspec.yml            # Các chỉ dẫn dành cho AWS CodeDeploy
└── scripts/               # Các tập lệnh triển khai
```

#### **Kết quả mong đợi**

Sau khi hoàn thành phần này, bạn sẽ có:

- Một **ứng dụng Spring Boot** có thể chạy trên máy tính cá nhân.
- Một **kho lưu trữ GitHub** chứa mã nguồn của dự án.
- Một **cấu hình Maven** phục vụ việc xây dựng ứng dụng và chạy các bài kiểm thử đơn vị.
- Các tệp cơ bản cần thiết cho những giai đoạn **CodeBuild** và **CodeDeploy** tiếp theo.

#### **Nội dung**

- [Chuẩn bị ứng dụng Spring Boot](3.1-create-web-application/)
- [Đẩy mã nguồn lên GitHub](3.2-push-to-github/)