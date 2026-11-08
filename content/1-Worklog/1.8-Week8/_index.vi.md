---
title: "Nhật ký thực tập tuần 8"
date: 2026-10-17
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Tìm hiểu vai trò của AWS CodeDeploy trong quy trình CI/CD.
* Học cách chuẩn bị các tệp ứng dụng và hướng dẫn triển khai.
* Tìm hiểu mục đích và cấu trúc của tệp `appspec.yml`.
* Học cách cấu hình các tập lệnh trong từng giai đoạn của vòng đời triển khai cho ứng dụng Spring Boot.
* Chuẩn bị quy trình triển khai ứng dụng từ tệp tạo tác (artifact) lên máy chủ Amazon EC2.

### Các công việc cần thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----| --- | --- | --- | --- |
| 1 | - Tìm hiểu về AWS CodeDeploy và vai trò của dịch vụ này trong việc tự động hóa quá trình triển khai ứng dụng. <br> - Tìm hiểu quy trình triển khai cơ bản từ tệp tạo tác sau khi Build lên máy chủ EC2. | 10/17/2026 | 10/17/2026 | [Hướng dẫn sử dụng AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| 2 | - Tìm hiểu về CodeDeploy Application, Deployment Group và Revision. <br> - Tìm hiểu cách CodeDeploy xác định các máy chủ EC2 mục tiêu cần triển khai ứng dụng. | 10/18/2026 | 10/18/2026 | [Các thành phần của CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/deployment-steps.html) |
| 3 | - Tìm hiểu cấu trúc của tệp `appspec.yml`. <br> - Xác định cách tệp này khai báo các tệp ứng dụng, đường dẫn đích và các bước thực thi trong vòng đời triển khai (Lifecycle Hooks). | 10/19/2026 | 10/19/2026 | [Tài liệu tham khảo về tệp AppSpec](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file.html) |
| 4 | - Chuẩn bị hoặc kiểm tra lại các tập lệnh triển khai, bao gồm tập lệnh dừng ứng dụng hiện tại, cài đặt các thành phần phụ thuộc và khởi chạy ứng dụng. <br> - Kiểm tra quyền của các tập lệnh và yêu cầu thực thi trên hệ điều hành Linux. | 10/20/2026 | 10/21/2026 | [Các sự kiện trong vòng đời triển khai của CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/reference-appspec-file-structure-hooks.html) |
| 5 | - Kiểm tra các yêu cầu cài đặt CodeDeploy Agent trên máy chủ EC2. <br> - Tìm hiểu cách tạo một gói triển khai (Deployment Revision) bao gồm tệp tạo tác của ứng dụng, `appspec.yml` và các tập lệnh cần thiết. <br> - Xem xét nhật ký triển khai và tìm hiểu các nguyên nhân phổ biến gây ra lỗi. | 10/22/2026 | 10/23/2026 | [CodeDeploy Agent](https://docs.aws.amazon.com/codedeploy/latest/userguide/codedeploy-agent.html) |

### Kết quả đạt được trong tuần 8

* Hiểu được vai trò của AWS CodeDeploy trong việc tự động hóa quá trình triển khai ứng dụng.
* Làm quen với các thành phần CodeDeploy Application, Deployment Group và Revision.
* Hiểu được cách tệp `appspec.yml` định nghĩa quy trình triển khai và các bước thực thi trong vòng đời triển khai.
* Xác định được các tập lệnh cần thiết để dừng và khởi chạy ứng dụng Spring Boot, đồng thời chuẩn bị môi trường chạy ứng dụng.
* Tìm hiểu về CodeDeploy Agent và vai trò của thành phần này trong việc giao tiếp với dịch vụ triển khai.
* Hiểu cách xem xét nhật ký triển khai và kiểm tra các lỗi thường gặp trong quá trình triển khai.
* Chuẩn bị cấu hình triển khai để tích hợp với AWS CodePipeline trong tuần tiếp theo.