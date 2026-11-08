---
title: "Nhật ký thực tập tuần 10"
date: 2026-10-31
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

* Rà soát toàn bộ quy trình CI/CD đã triển khai trên nền tảng AWS.
* Kiểm tra quy trình Build và Deploy của ứng dụng web Spring Boot.
* Tìm hiểu cách sử dụng Amazon CloudWatch để giám sát hoạt động của ứng dụng và quá trình triển khai.
* Xác định các lỗi thường gặp và đánh giá tính ổn định của quy trình triển khai.
* Hoàn thiện báo cáo thực tập và tổng kết những kiến thức đã tiếp thu trong quá trình thực tập.

### Các công việc cần thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------| --- | --- | --- | --- |
| 1    | - Rà soát kiến trúc tổng thể của dự án và vai trò của GitHub, AWS CodePipeline, AWS CodeBuild, AWS CodeDeploy và Amazon EC2. <br> - Kiểm tra các tệp cấu hình và tập lệnh được sử dụng trong toàn bộ quy trình. | 10/31/2026 | 10/31/2026 | [Tài liệu CI/CD của AWS](https://docs.aws.amazon.com/) |
| 2    | - Rà soát quy trình Build ứng dụng và thực hiện kiểm thử đơn vị (Unit Test). <br> - Kiểm tra nhật ký hoạt động của CodeBuild và xác nhận tệp tạo tác của ứng dụng có được tạo chính xác hay không. | 11/01/2026 | 11/01/2026 | [Hướng dẫn sử dụng AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html) |
| 3    | - Rà soát quy trình triển khai từ CodeDeploy đến máy chủ EC2. <br> - Kiểm tra nhật ký triển khai và xác minh khả năng truy cập ứng dụng trong trường hợp môi trường triển khai cho phép. | 11/02/2026 | 11/02/2026 | [Hướng dẫn sử dụng AWS CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/welcome.html) |
| 4    | - Tìm hiểu về các chỉ số (Metrics), nhật ký (Logs) và cảnh báo (Alarms) của Amazon CloudWatch. <br> - Xác định những thông tin hữu ích phục vụ việc giám sát hoạt động của ứng dụng và xử lý các sự cố triển khai. | 11/03/2026 | 11/04/2026 | [Tài liệu Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/) |
| 5    | - Tổng hợp quy trình thực hiện dự án, các cấu hình, kết quả kiểm thử và những hạn chế còn tồn tại. <br> - Hoàn thiện báo cáo thực tập, sắp xếp hình ảnh chụp màn hình, sơ đồ và rà soát tính nhất quán của báo cáo. | 11/05/2026 | 11/06/2026 | [Tài liệu Amazon CloudWatch](https://docs.aws.amazon.com/cloudwatch/) |

### Kết quả đạt được trong tuần 10

* Rà soát được kiến trúc tổng thể của quy trình CI/CD tự động trên nền tảng AWS.
* Củng cố kiến thức về vai trò của GitHub, CodePipeline, CodeBuild, CodeDeploy và EC2.
* Rà soát các quy trình Build, Test và Deploy, đồng thời xác định được các loại nhật ký cần thiết để kiểm tra và xử lý lỗi.
* Hiểu được cách Amazon CloudWatch hỗ trợ giám sát thông qua các chỉ số, nhật ký và cảnh báo.
* Tổng hợp được quá trình triển khai, những khó khăn về mặt kỹ thuật và các hướng cải thiện có thể áp dụng cho dự án.
* Sắp xếp tài liệu dự án, sơ đồ kiến trúc và các hình ảnh minh họa cần thiết cho báo cáo thực tập.
* Hoàn thành nhật ký thực tập theo kế hoạch và rà soát lại báo cáo cuối kỳ.