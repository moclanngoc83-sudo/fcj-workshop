---
title: "Dọn dẹp tài nguyên"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 4.6. </b> "
---

Chúc mừng bạn đã hoàn thành workshop Simple Web App CI/CD!

Trong workshop này, bạn đã cấu hình quy trình triển khai ứng dụng web bằng các dịch vụ AWS. Trước khi kết thúc, hãy dọn dẹp các tài nguyên được tạo trong quá trình thực hiện workshop để tránh phát sinh chi phí AWS không cần thiết.

## 1. Dừng quy trình CI/CD

1. Mở **AWS CodePipeline** Console.
2. Chọn pipeline đã tạo cho workshop này.
3. Ghi lại tên pipeline để đưa vào báo cáo thực tập.
4. Nếu không còn cần sử dụng pipeline, hãy xóa pipeline tại trang chi tiết và xác nhận thao tác xóa.

Việc xóa pipeline không tự động xóa tất cả các tài nguyên liên quan.

## 2. Xóa các tài nguyên CodeDeploy

1. Mở **AWS CodeDeploy** Console.
2. Chọn **Applications**.
3. Mở ứng dụng `cicd-aws-demo-app`.
4. Xóa Deployment Group `cicd-aws-demo-deployment-group`.
5. Xóa ứng dụng `cicd-aws-demo-app`.

Hãy đảm bảo bạn chỉ chọn những tài nguyên được tạo riêng cho workshop này.

## 3. Xóa dự án CodeBuild

1. Mở **AWS CodeBuild** Console.
2. Chọn **Build projects**.
3. Chọn dự án `cicd-aws-demo-build`.
4. Chọn **Delete build project** và xác nhận thao tác.

Việc xóa dự án CodeBuild không tự động xóa các log group trong CloudWatch hoặc các artifact được lưu trữ trong S3.

## 4. Chấm dứt EC2 Instance

Nếu EC2 instance được tạo riêng cho workshop này và không còn cần sử dụng:

1. Mở **Amazon EC2** Console.
2. Chọn **Instances**.
3. Chọn instance được tạo cho workshop.
4. Chọn **Instance state → Terminate instance**.
5. Xác nhận thao tác chấm dứt.

**Cảnh báo:** Việc chấm dứt instance là thao tác không thể hoàn tác. Không chấm dứt instance đang lưu trữ các ứng dụng khác hoặc được sử dụng chung với dự án khác.

Sau khi chấm dứt instance, hãy kiểm tra xem còn tài nguyên liên quan nào có thể phát sinh chi phí hay không, chẳng hạn như EBS volumes, Elastic IP addresses, load balancers hoặc các tài nguyên khác. Chỉ xóa những tài nguyên không còn cần thiết.

## 5. Xóa các Artifact trong S3

1. Mở **Amazon S3** Console.
2. Xác định bucket được sử dụng để lưu trữ CodePipeline artifacts hoặc các gói triển khai.
3. Kiểm tra và đảm bảo bucket chỉ phục vụ riêng cho workshop này.
4. Làm trống bucket nếu các nội dung bên trong không còn cần thiết.
5. Xóa bucket và xác nhận thao tác.

**Lưu ý quan trọng:** Việc làm trống bucket sẽ xóa vĩnh viễn các object bên trong. Không xóa bucket dùng chung hoặc bucket chứa các tệp cần thiết cho những dự án khác.

Nếu S3 Versioning được bật, hãy xóa các phiên bản object và delete marker cần thiết trước khi xóa bucket.

## 6. Xóa CloudWatch Logs

1. Mở **Amazon CloudWatch** Console.
2. Chọn **Logs → Log groups**.
3. Xác định các log group được tạo bởi CodeBuild và ứng dụng triển khai.
4. Kiểm tra nội dung để đảm bảo các log này không còn cần thiết.
5. Chỉ xóa những log group được tạo riêng cho workshop này.