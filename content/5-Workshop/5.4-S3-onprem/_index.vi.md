---
title: "Xây dựng ứng dụng bằng AWS CodeBuild"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

#### **Tổng quan**

Trong phần này, bạn sẽ cấu hình **AWS CodeBuild** để xây dựng **ứng dụng web Spring Boot** và tự động thực thi các bài kiểm thử đơn vị (Unit Test).

**AWS CodeBuild** là dịch vụ xây dựng ứng dụng được quản lý hoàn toàn, có khả năng biên dịch mã nguồn, chạy kiểm thử và tạo các gói phần mềm sẵn sàng cho quá trình triển khai.

Trong workshop này, CodeBuild sẽ lấy mã nguồn từ **repository GitHub**, sử dụng **Maven** để xây dựng ứng dụng và chạy các bài kiểm thử đơn vị được định nghĩa trong dự án.

#### **Tại sao nên sử dụng AWS CodeBuild?**

- **Tự động hóa quá trình Build (Automated Build):** CodeBuild tự động biên dịch ứng dụng mà không cần thực hiện các lệnh thủ công trên máy tính cá nhân.
- **Tự động kiểm thử (Automated Testing):** Các bài kiểm thử đơn vị được thực thi trong quá trình Build nhằm xác minh hoạt động của ứng dụng.
- **Tạo sản phẩm đầu ra (Build Artifacts):** Nếu quá trình Build thành công, CodeBuild sẽ tạo gói ứng dụng sẵn sàng triển khai và có thể lưu trữ trên **Amazon S3**.
- **Tích hợp CI/CD:** CodeBuild tích hợp với **AWS CodePipeline** để tự động thực hiện giai đoạn Build mỗi khi phát hiện thay đổi trong mã nguồn.

#### **Tổng quan quy trình Build**

Quy trình Build bao gồm các bước sau:

1. **Source (Mã nguồn):** Lấy mã nguồn ứng dụng từ GitHub.
2. **Build (Xây dựng):** Sử dụng Maven để biên dịch ứng dụng Spring Boot.
3. **Test (Kiểm thử):** Thực thi các bài kiểm thử đơn vị để xác minh ứng dụng.
4. **Package (Đóng gói):** Tạo tệp JAR của ứng dụng.
5. **Store Artifacts (Lưu trữ sản phẩm đầu ra):** Chuẩn bị kết quả Build để sử dụng trong giai đoạn triển khai.

#### **Cấu hình Build**

Dự án sử dụng tệp `buildspec.yml` để định nghĩa các lệnh được thực thi bởi CodeBuild.

Tệp cấu hình này xác định **môi trường chạy Java**, các lệnh dùng để xây dựng và kiểm thử ứng dụng, cũng như vị trí lưu trữ các sản phẩm đầu ra được tạo ra.

Kết quả Build sẽ được sử dụng trong giai đoạn tiếp theo của quy trình CI/CD.

#### **Kết quả mong đợi**

Sau khi hoàn thành phần này, bạn cần có:

- Một **AWS CodeBuild Project** được cấu hình cho ứng dụng.
- Quy trình Build sử dụng **Maven** để biên dịch mã nguồn.
- Các bài kiểm thử đơn vị được tự động thực thi trong quá trình Build.
- Một gói ứng dụng đã được đóng gói, sẵn sàng cho giai đoạn triển khai.

#### **Nội dung**

- [Cấu hình AWS CodeBuild](5.4.1-configure-codebuild/)
- [Xây dựng và kiểm thử ứng dụng](5.4.2-build-and-test/)