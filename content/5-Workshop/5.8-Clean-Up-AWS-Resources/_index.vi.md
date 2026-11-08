---
title: "Dọn dẹp tài nguyên"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 4.8. </b> "
---

Sau khi hoàn thành workshop CI/CD, hãy xóa các tài nguyên AWS không còn cần thiết. Việc này giúp tránh phát sinh những khoản chi phí không cần thiết.

**Trước khi xóa tài nguyên:** Hãy lưu lại các ảnh chụp màn hình và logs cần thiết cho báo cáo tốt nghiệp. Xác nhận rằng mỗi tài nguyên thuộc về workshop này và không được sử dụng chung với dự án khác.

## 1. Xóa Pipeline CodePipeline

1. Mở **AWS CodePipeline** Console.
2. Chọn pipeline được tạo cho dự án `cicd-aws-demo`.
3. Xác nhận rằng bạn đã ghi lại kết quả thực thi pipeline.
4. Xóa pipeline và xác nhận thao tác.

Việc xóa pipeline không tự động xóa dự án CodeBuild, ứng dụng CodeDeploy, S3 artifact bucket hoặc các IAM role liên quan.

## 2. Xóa ứng dụng CodeDeploy

1. Mở **AWS CodeDeploy** Console.
2. Chọn **Applications**.
3. Mở ứng dụng `cicd-aws-demo-app`.
4. Xóa Deployment Group `cicd-aws-demo-deployment-group`.
5. Xóa ứng dụng `cicd-aws-demo-app`.

Chỉ xóa ứng dụng và Deployment Group được tạo riêng cho workshop này.

## 3. Xóa dự án CodeBuild

1. Mở **AWS CodeBuild** Console.
2. Chọn **Build projects**.
3. Chọn `cicd-aws-demo-build`.
4. Chọn **Delete build project**.
5. Xác nhận thao tác xóa.

CloudWatch logs và các artifact trong S3 của dự án có thể vẫn còn tồn tại và cần được kiểm tra riêng.

## 4. Chấm dứt EC2 Instance của Workshop

1. Mở **Amazon EC2** Console.
2. Chọn **Instances**.
3. Xác định instance được tạo cho workshop này.
4. Xác nhận rằng không có ứng dụng nào khác phụ thuộc vào instance đó.
5. Chọn **Instance state → Terminate instance** và xác nhận.

Việc chấm dứt sẽ xóa instance vĩnh viễn. Hãy kiểm tra riêng các EBS volume được gắn với instance, Elastic IP address, load balancer và những tài nguyên liên quan khác vì một số tài nguyên vẫn có thể tiếp tục phát sinh chi phí.

Không chấm dứt instance được sử dụng chung hoặc instance đang lưu trữ các ứng dụng khác.

## 5. Xóa S3 Artifact Bucket

1. Mở **Amazon S3** Console.
2. Xác định bucket được sử dụng để lưu trữ CodePipeline artifacts hoặc các gói triển khai.
3. Xác minh rằng bucket chỉ phục vụ riêng cho workshop này.
4. Tải xuống những tệp cần thiết cho báo cáo.
5. Làm trống bucket và xóa bucket nếu không còn cần sử dụng.

Nếu tính năng Versioning được bật, hãy xóa các phiên bản object và delete marker cần thiết trước khi xóa bucket.

Không xóa bucket được sử dụng chung với các dự án khác.

## 6. Xóa CloudWatch Logs không cần thiết

1. Mở **Amazon CloudWatch** Console.
2. Chọn **Logs → Log groups**.
3. Xác định các log group được tạo trong quá trình thực hiện workshop.
4. Lưu lại những logs cần thiết cho tài liệu báo cáo.
5. Chỉ xóa những log group không còn cần thiết.

Giữ lại logs của các ứng dụng và dịch vụ được sử dụng chung.

## 7. Kiểm tra IAM Roles

1. Mở **IAM** Console.
2. Chọn **Roles**.
3. Kiểm tra các role được tạo cho CodeBuild, CodeDeploy và EC2 instance.
4. Kiểm tra xem còn tài nguyên nào đang sử dụng từng role hay không.
5. Chỉ xóa những role không còn được sử dụng và được tạo riêng cho workshop này.

Không xóa các role được sử dụng chung hoặc các role đang phục vụ những workload AWS khác.

## 8. Xác minh quá trình dọn dẹp

Kiểm tra lại các tài nguyên đã tạo trong quá trình thực hiện workshop.

| Tài nguyên | Trạng thái cuối cùng mong đợi |
|---|---|
| CodePipeline | Đã xóa nếu không còn cần thiết |
| CodeDeploy application và Deployment Group | Đã xóa nếu không còn cần thiết |
| CodeBuild project | Đã xóa nếu không còn cần thiết |
| EC2 instance | Đã chấm dứt nếu được tạo riêng cho workshop |
| S3 artifact bucket | Đã xóa nếu được tạo riêng cho workshop |
| CloudWatch log groups | Đã xóa các logs không còn cần thiết |
| IAM roles | Đã xóa các role riêng của workshop không còn được sử dụng |

Cuối cùng, mở **AWS Billing and Cost Management** để kiểm tra các khoản phí hiện tại và những tài nguyên vẫn có thể phát sinh chi phí. Thông tin thanh toán có thể cần một khoảng thời gian mới cập nhật đầy đủ sau khi tài nguyên được xóa.

## Kết quả

Các tài nguyên của workshop đã được kiểm tra và những tài nguyên không cần thiết đã được dọn dẹp. Bằng chứng về quy trình CI/CD hoạt động thành công đã được lưu lại để phục vụ báo cáo tốt nghiệp.