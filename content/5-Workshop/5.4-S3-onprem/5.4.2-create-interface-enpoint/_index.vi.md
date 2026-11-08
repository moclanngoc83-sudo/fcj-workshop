---
title: "Xây dựng và kiểm thử ứng dụng"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 4.4.2. </b> "
---

#### **1. Tổng quan**

Trong phần này, bạn sẽ chạy và kiểm tra quy trình **AWS CodeBuild** dành cho **ứng dụng web Spring Boot**.

CodeBuild sử dụng tệp **`buildspec.yml`** của dự án để thực thi các lệnh Build. Quá trình này bao gồm biên dịch mã nguồn, chạy các bài kiểm thử đơn vị và chuẩn bị gói ứng dụng cho giai đoạn triển khai.

#### **2. Bắt đầu quá trình Build**

1. Mở **AWS CodeBuild Console**.
2. Chọn **Build projects** trong thanh điều hướng.
3. Chọn Project có tên `cicd-aws-demo-build`.
4. Nhấn **Start build**.
5. Chờ quá trình Build hoàn tất.

#### **3. Theo dõi Build Logs**

Sau khi quá trình Build bắt đầu, mở phần chi tiết của lần Build và kiểm tra **Build logs**.

Kiểm tra nhật ký ở các giai đoạn sau:

- **Install:** Môi trường Java và Maven được chuẩn bị.
- **Pre-build:** Môi trường được kiểm tra và chuẩn bị cho quá trình kiểm thử.
- **Build:** Maven biên dịch ứng dụng và thực thi các bài kiểm thử đơn vị.
- **Post-build:** Quá trình Build hoàn tất và các Artifacts đầu ra được chuẩn bị, nếu đã được cấu hình.

Nếu xảy ra lỗi, hãy xem lại nhật ký để xác định lệnh bị lỗi. Một số nguyên nhân phổ biến bao gồm phiên bản Java không chính xác, cấu hình Maven không hợp lệ, thiếu thư viện phụ thuộc hoặc các bài kiểm thử đơn vị không đạt yêu cầu.

#### **4. Kiểm tra kết quả Build**

Sau khi quá trình Build hoàn tất, kiểm tra **Build status** trong CodeBuild Console.

Một quá trình Build thành công sẽ hiển thị trạng thái **Succeeded**.

Nếu quá trình Build thất bại, trạng thái sẽ hiển thị **Failed**. Hãy xem lại các thông báo lỗi, khắc phục vấn đề trong mã nguồn hoặc cấu hình Build, sau đó bắt đầu một lần Build mới.

{{% notice info %}}
Một quá trình Build thành công cho biết các lệnh Build đã được cấu hình và thực thi thành công. Tuy nhiên, điều này không đồng nghĩa với việc ứng dụng đã được triển khai hoặc tất cả các chức năng của ứng dụng đều hoạt động chính xác.
{{% /notice %}}

#### **5. Kiểm tra Artifact của ứng dụng**

Nếu quá trình Build được cấu hình để tạo Artifact, hãy kiểm tra xem gói ứng dụng đã được tạo hay chưa.

Đối với dự án **Spring Boot sử dụng Maven**, gói ứng dụng thường là một tệp JAR nằm trong thư mục `target/`.

Nếu dự án được tích hợp với **AWS CodePipeline**, hãy kiểm tra xem kết quả đầu ra của quá trình Build đã được cấu hình chính xác hay chưa.