---
title: "Nhật ký thực tập tuần 9"
date: 2026-10-24
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

* Tìm hiểu vai trò của AWS CodePipeline trong việc tự động hóa quy trình CI/CD.
* Học cách kết nối kho lưu trữ mã nguồn GitHub với AWS CodePipeline.
* Tích hợp AWS CodeBuild và AWS CodeDeploy vào cùng một quy trình triển khai (Pipeline).
* Tìm hiểu cách những thay đổi trong mã nguồn kích hoạt các giai đoạn Build và Deploy.
* Học cách giám sát quá trình thực thi Pipeline và xử lý các lỗi thường gặp.

### Các công việc cần thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----| --- | --- | --- | --- |
| 1 | - Tìm hiểu về AWS CodePipeline và vai trò của dịch vụ này trong việc tự động hóa quá trình phân phối phần mềm. <br> - Xem xét các giai đoạn Source, Build và Deploy trong quy trình CI/CD dự kiến triển khai. | 10/24/2026 | 10/24/2026 | [Hướng dẫn sử dụng AWS CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html) |
| 2 | - Kiểm tra kho lưu trữ mã nguồn GitHub và kết nối của kho lưu trữ này với AWS CodePipeline. <br> - Tìm hiểu cách những thay đổi trong mã nguồn có thể khởi chạy một lần thực thi Pipeline. | 10/25/2026 | 10/25/2026 | [Các tác vụ Source trong CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference.html) |
| 3 | - Cấu hình hoặc kiểm tra giai đoạn Source để lấy mã nguồn ứng dụng từ GitHub. <br> - Xác định tệp tạo tác nguồn (Source Artifact) được chuyển đến giai đoạn Build. | 10/26/2026 | 10/26/2026 | [Các tác vụ Source trong CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference.html) |
| 4 | - Tích hợp AWS CodeBuild làm giai đoạn Build. <br> - Cấu hình hoặc kiểm tra giai đoạn Deploy sử dụng AWS CodeDeploy. <br> - Kiểm tra luồng chuyển giao các tệp tạo tác giữa những giai đoạn trong Pipeline. | 10/27/2026 | 10/28/2026 | [Cấu trúc Pipeline của CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/pipeline-structure.html) |
| 5 | - Chạy thử hoặc kiểm tra quá trình thực thi Pipeline. <br> - Kiểm tra trạng thái và nhật ký hoạt động của từng giai đoạn. <br> - Xác định các lỗi thường gặp liên quan đến mã nguồn, quá trình Build, quyền truy cập và triển khai; đồng thời tìm hiểu các giải pháp khắc phục. | 10/29/2026 | 10/30/2026 | [Xử lý sự cố CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/troubleshooting.html) |

### Kết quả đạt được trong tuần 9

* Hiểu được mục đích của AWS CodePipeline trong việc điều phối quá trình phân phối ứng dụng tự động.
* Xác định được chức năng của các giai đoạn Source, Build và Deploy.
* Hiểu được cách GitHub, AWS CodeBuild và AWS CodeDeploy phối hợp với nhau trong quy trình CI/CD.
* Tìm hiểu cách các tệp tạo tác nguồn được chuyển giao giữa những giai đoạn trong Pipeline.
* Làm quen với việc giám sát quá trình thực thi Pipeline và xem xét nhật ký hoạt động của từng giai đoạn.
* Xác định được các lỗi Pipeline thường gặp liên quan đến cấu hình nguồn, câu lệnh Build, quyền IAM và thiết lập triển khai.
* Chuẩn bị quy trình CI/CD đã tích hợp để thực hiện kiểm thử cuối cùng, giám sát hoạt động và hoàn thiện báo cáo thực tập.