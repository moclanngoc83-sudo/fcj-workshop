---
title: "Nhật ký thực tập tuần 6"
date: 2026-09-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6

* Hiểu vai trò của AWS CodeBuild trong quy trình CI/CD tự động.
* Tìm hiểu cách cấu hình một dự án Build sử dụng mã nguồn được lưu trữ trên GitHub.
* Hiểu mục đích và cấu trúc của tệp `buildspec.yml`.
* Cấu hình môi trường xây dựng và các câu lệnh cần thiết để biên dịch và kiểm thử ứng dụng Spring Boot.
* Kiểm tra kết quả đầu ra của quá trình Build trước khi chuyển sang giai đoạn triển khai.

### Các công việc thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - Tìm hiểu về AWS CodeBuild và vai trò của dịch vụ này trong quy trình CI/CD. <br> - Hiểu cách CodeBuild tự động hóa quá trình biên dịch, kiểm thử và đóng gói mã nguồn ứng dụng. | 09/19/2026 | 09/19/2026 | [Hướng dẫn sử dụng AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |
| 2 | - Xem xét kho mã nguồn dự án trên GitHub. <br> - Xác định các tệp cần thiết cho quá trình Build, bao gồm `pom.xml` và các tệp kiểm thử đơn vị. | 09/20/2026 | 09/20/2026 | [Nguồn mã nguồn cho AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) |
| 3 | - Tìm hiểu cấu trúc của tệp `buildspec.yml`. <br> - Xác định các giai đoạn Install, Pre-build, Build và Post-build. | 09/21/2026 | 09/21/2026 | [Tài liệu tham khảo Build Specification](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) |
| 4 | - Chuẩn bị tệp cấu hình Build cho ứng dụng Spring Boot. <br> - Cấu hình các câu lệnh Maven để biên dịch mã nguồn, chạy kiểm thử đơn vị và đóng gói ứng dụng thành tệp JAR. | 09/22/2026 | 09/23/2026 | [Tài liệu Maven](https://maven.apache.org/guides/) |
| 5 | - Tạo hoặc xem xét dự án AWS CodeBuild và cấu hình kho mã nguồn cùng môi trường xây dựng. <br> - Chạy quá trình Build và kiểm tra nhật ký hoạt động, kết quả kiểm thử và các tệp đầu ra. <br> - Xác định và xử lý các lỗi phát sinh trong quá trình Build. | 09/24/2026 | 09/25/2026 | [Hướng dẫn sử dụng AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |

### Kết quả đạt được trong tuần 6

* Hiểu được mục đích của AWS CodeBuild và vai trò của dịch vụ này trong việc tự động hóa quá trình xây dựng ứng dụng.
* Làm quen với cấu trúc và các giai đoạn chính của tệp `buildspec.yml`.
* Xác định được các câu lệnh Maven cần thiết để biên dịch, kiểm thử và đóng gói ứng dụng Spring Boot.
* Tìm hiểu cách cấu hình kho mã nguồn và môi trường xây dựng cho một dự án AWS CodeBuild.
* Hiểu cách kiểm tra nhật ký Build và xác định lỗi trong quá trình xây dựng tự động.
* Chuẩn bị dự án cho giai đoạn tiếp theo: chuẩn bị môi trường AWS để triển khai ứng dụng.