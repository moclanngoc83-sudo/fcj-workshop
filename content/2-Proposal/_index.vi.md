---
title: "Đề xuất dự án"
date: 2026-08-08
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Thiết kế và triển khai quy trình CI/CD tự động cho ứng dụng web trên AWS

## 1. Tóm tắt dự án

Dự án tập trung vào việc thiết kế và triển khai một quy trình Tích hợp liên tục và Phân phối/Triển khai liên tục (Continuous Integration and Continuous Delivery/Deployment – CI/CD) tự động cho ứng dụng web Spring Boot trên nền tảng Amazon Web Services (AWS).

Dự án sử dụng GitHub để quản lý mã nguồn, AWS CodeBuild để biên dịch ứng dụng và thực thi các bài kiểm thử, AWS CodeDeploy để triển khai ứng dụng lên máy chủ Amazon EC2 và AWS CodePipeline để điều phối toàn bộ quy trình. Amazon CloudWatch có thể được sử dụng để xem xét các nhật ký hoạt động hiện có và giám sát những tài nguyên liên quan.

Mục tiêu chính của dự án là giảm thiểu các thao tác triển khai thủ công, nâng cao tính nhất quán và xây dựng một quy trình có thể lặp lại để biên dịch, kiểm thử và triển khai ứng dụng web. Dự án được thiết kế dưới dạng một mô hình thực hành phù hợp với đề tài thực tập và có thể mở rộng bằng cách bổ sung các bước kiểm thử, kiểm tra bảo mật và tính năng giám sát.

## 2. Phát biểu vấn đề

### Vấn đề cần giải quyết

Quá trình triển khai ứng dụng thủ công yêu cầu lập trình viên thực hiện nhiều bước, bao gồm lấy mã nguồn, biên dịch ứng dụng, chạy kiểm thử, chuẩn bị các tệp triển khai và chuyển ứng dụng lên máy chủ.

Những bước này có thể tốn nhiều thời gian và dễ dẫn đến sai sót trong cấu hình hoặc kết quả triển khai không đồng nhất. Khi mã nguồn thay đổi thường xuyên, việc lặp lại toàn bộ quy trình thủ công cũng khiến quá trình phát hành phiên bản ứng dụng khó duy trì tính ổn định và đáng tin cậy.

Đối với một dự án ứng dụng web quy mô nhỏ, việc xây dựng một quy trình triển khai tự động có tính thực tiễn sẽ giúp chuẩn hóa các công việc này và giúp việc kiểm tra kết quả Build, Deploy trở nên thuận tiện hơn.

### Giải pháp đề xuất

Giải pháp được đề xuất là xây dựng một quy trình CI/CD trên AWS, kết nối hoạt động quản lý mã nguồn, biên dịch và kiểm thử tự động với quá trình triển khai ứng dụng.

Mã nguồn được lưu trữ trong kho GitHub. AWS CodePipeline điều phối quy trình, AWS CodeBuild sử dụng Maven để biên dịch và kiểm thử ứng dụng, còn AWS CodeDeploy triển khai ứng dụng đã được đóng gói lên máy chủ Amazon EC2. Ứng dụng sẽ chạy trên EC2 và có thể được truy cập thông qua địa chỉ mạng đã cấu hình.

Quy trình đề xuất:

**GitHub → AWS CodePipeline → AWS CodeBuild → AWS CodeDeploy → Amazon EC2**

Giai đoạn Build sử dụng tệp `buildspec.yml` để xác định các lệnh cần thực hiện trong quá trình biên dịch. Gói triển khai bao gồm tệp `appspec.yml` và các tập lệnh cần thiết cho CodeDeploy. Amazon CloudWatch có thể hỗ trợ quá trình xử lý sự cố thông qua việc cung cấp các nhật ký và chỉ số liên quan khi được cấu hình.

### Lợi ích và giá trị kỳ vọng

Dự án mang lại những lợi ích kỳ vọng sau:

* **Giảm công việc thủ công:** Tự động hóa các bước Build và Deploy được thực hiện thường xuyên.
* **Tính nhất quán:** Sử dụng các lệnh Build và hướng dẫn triển khai được xác định trước.
* **Nâng cao khả năng truy xuất:** Giúp việc kiểm tra kết quả thực thi Pipeline và nhật ký hoạt động thuận tiện hơn.
* **Phát hiện lỗi sớm:** Thực hiện các bài kiểm thử đã cấu hình trước khi chuyển sang giai đoạn triển khai.
* **Kinh nghiệm thực hành AWS:** Minh họa việc sử dụng các công cụ dành cho nhà phát triển của AWS và dịch vụ EC2.
* **Khả năng mở rộng:** Tạo nền tảng để bổ sung các bước kiểm soát chất lượng (Quality Gate), kiểm tra bảo mật, quy trình khôi phục phiên bản và các tính năng giám sát nâng cao.

Dự án chủ yếu phục vụ mục đích học tập và thực hành. Hiệu quả tiết kiệm thời gian, mức độ cải thiện độ tin cậy và chi phí vận hành thực tế cần được đánh giá sau khi hoàn thành triển khai và kiểm thử.

## 3. Kiến trúc giải pháp

Kiến trúc đề xuất bao gồm kho lưu trữ mã nguồn, quy trình Pipeline tự động, môi trường Build, dịch vụ triển khai và máy chủ EC2 dùng để lưu trữ và chạy ứng dụng web.

### Tổng quan kiến trúc

1. **Quản lý mã nguồn:** GitHub lưu trữ mã nguồn ứng dụng Spring Boot và các tệp cấu hình.
2. **Điều phối quy trình:** AWS CodePipeline điều phối các giai đoạn Source, Build và Deploy.
3. **Biên dịch và kiểm thử:** AWS CodeBuild sử dụng Maven để biên dịch ứng dụng, chạy các bài kiểm thử đơn vị đã cấu hình và đóng gói ứng dụng.
4. **Triển khai ứng dụng:** AWS CodeDeploy triển khai gói ứng dụng lên máy chủ EC2 mục tiêu bằng cách sử dụng các hướng dẫn và tập lệnh triển khai.
5. **Môi trường chạy ứng dụng:** Amazon EC2 vận hành ứng dụng Spring Boot sau khi được triển khai.
6. **Giám sát và xử lý sự cố:** Amazon CloudWatch có thể được sử dụng để xem xét các nhật ký đã cấu hình và giám sát những tài nguyên AWS liên quan.

### Các dịch vụ AWS được sử dụng

- **GitHub:** Lưu trữ mã nguồn và theo dõi các thay đổi.
- **AWS CodePipeline:** Điều phối quy trình CI/CD.
- **AWS CodeBuild:** Biên dịch mã nguồn, chạy kiểm thử và tạo gói ứng dụng.
- **AWS CodeDeploy:** Tự động hóa quá trình triển khai ứng dụng lên EC2.
- **Amazon EC2:** Lưu trữ và chạy ứng dụng Spring Boot sau khi triển khai.
- **AWS Identity and Access Management (IAM):** Quản lý quyền truy cập của các thành phần trong Pipeline và tài nguyên AWS.
- **Amazon CloudWatch:** Hỗ trợ giám sát và xử lý sự cố thông qua các chỉ số có sẵn và nhật ký đã được cấu hình.

### Thiết kế các thành phần

- **Kho lưu trữ mã nguồn (Source Repository):** Chứa mã nguồn ứng dụng, `pom.xml`, `buildspec.yml`, `appspec.yml` và các tập lệnh triển khai.
- **Giai đoạn Source:** Lấy mã nguồn dự án từ GitHub.
- **Giai đoạn Build:** Thực thi các lệnh Maven trong CodeBuild để biên dịch, kiểm thử và đóng gói ứng dụng.
- **Luồng chuyển giao Artifact (Artifact Flow):** Chuyển kết quả Build cần thiết đến giai đoạn triển khai.
- **Giai đoạn Deploy:** Sử dụng CodeDeploy để chuyển gói ứng dụng đến máy chủ EC2 mục tiêu.
- **Môi trường chạy ứng dụng (Application Runtime):** Vận hành ứng dụng Spring Boot trên EC2.
- **Giám sát (Monitoring):** Sử dụng kết quả Pipeline, nhật ký triển khai và dữ liệu CloudWatch có sẵn để kiểm tra và xử lý sự cố.

## 4. Triển khai kỹ thuật

### Các giai đoạn triển khai

Dự án được chia thành các giai đoạn sau:

- **Giai đoạn 1 — Phân tích yêu cầu và thiết kế kiến trúc:** Xác định mục tiêu dự án, lựa chọn các dịch vụ AWS cần thiết và thiết kế quy trình CI/CD.
- **Giai đoạn 2 — Chuẩn bị ứng dụng và kho lưu trữ mã nguồn:** Kiểm tra dự án Spring Boot, chuẩn bị môi trường phát triển và tổ chức mã nguồn trên GitHub.
- **Giai đoạn 3 — Tự động hóa Build và kiểm thử:** Chuẩn bị các bài kiểm thử đơn vị và cấu hình AWS CodeBuild bằng tệp `buildspec.yml`.
- **Giai đoạn 4 — Chuẩn bị môi trường triển khai:** Chuẩn bị máy chủ EC2, kiểm tra Security Group, quyền IAM và xác định các yêu cầu về môi trường chạy ứng dụng.
- **Giai đoạn 5 — Tự động hóa triển khai:** Cấu hình CodeDeploy, chuẩn bị tệp `appspec.yml` và các tập lệnh triển khai, đồng thời xác định quy trình triển khai ứng dụng.
- **Giai đoạn 6 — Tích hợp Pipeline và đánh giá:** Tích hợp các giai đoạn Source, Build và Deploy bằng CodePipeline, kiểm tra kết quả thực thi, xử lý lỗi và ghi nhận kết quả.

### Yêu cầu kỹ thuật

**Ứng dụng và môi trường phát triển**

- Một ứng dụng web Spring Boot được viết bằng ngôn ngữ Java.
- Bộ công cụ phát triển Java (JDK) và môi trường Build Maven tương thích.
- Git và kho lưu trữ GitHub để quản lý mã nguồn.
- Các bài kiểm thử đơn vị phù hợp với những chức năng đã được triển khai của ứng dụng.
- Tệp `pom.xml` dùng để khai báo các thư viện phụ thuộc và cấu hình Build của dự án.

**Môi trường AWS**

- Một tài khoản AWS có các quyền cần thiết để cấu hình tài nguyên cho dự án.
- AWS CodePipeline để điều phối quy trình.
- AWS CodeBuild để tự động hóa quá trình Build và kiểm thử.
- AWS CodeDeploy để triển khai ứng dụng.
- Một máy chủ Amazon EC2 được cấu hình để chạy ứng dụng.
- Các IAM Role và IAM Policy có quyền phù hợp với từng dịch vụ.
- Các quy tắc Security Group chỉ cho phép lưu lượng mạng cần thiết đối với ứng dụng và hoạt động quản trị.

**Cấu hình Build và Deploy**

- `buildspec.yml` xác định các giai đoạn và lệnh thực hiện trong quá trình Build.
- `appspec.yml` xác định các tệp và Lifecycle Hooks được sử dụng bởi CodeDeploy.
- Các tập lệnh triển khai quản lý vòng đời hoạt động của ứng dụng khi cần thiết.
- Tệp tạo tác sau Build (Build Artifact) chứa những tệp cần thiết cho quá trình triển khai.

## 5. Tiến độ và các mốc thực hiện

### Kế hoạch thực hiện dự án

Dự án được lên kế hoạch theo các mốc thời gian sau:

- **Tuần 1 — Kiến thức cơ bản về AWS:** Tìm hiểu các dịch vụ AWS cơ bản và xác định những dịch vụ phù hợp với dự án.
- **Tuần 2 — Thiết kế CI/CD:** Tìm hiểu các khái niệm CI/CD và thiết kế quy trình Pipeline dự kiến.
- **Tuần 3 — Chuẩn bị ứng dụng:** Kiểm tra dự án Spring Boot và chuẩn bị môi trường phát triển.
- **Tuần 4 — Quản lý mã nguồn:** Tổ chức kho lưu trữ dự án và quản lý mã nguồn bằng Git và GitHub.
- **Tuần 5 — Kiểm thử đơn vị:** Kiểm tra hoặc viết các bài kiểm thử đơn vị và chuẩn bị quy trình Build bằng Maven.
- **Tuần 6 — AWS CodeBuild:** Chuẩn bị tệp đặc tả Build và cấu hình giai đoạn Build tự động.
- **Tuần 7 — Chuẩn bị môi trường AWS:** Chuẩn bị môi trường triển khai EC2 và kiểm tra các yêu cầu về IAM và mạng.
- **Tuần 8 — AWS CodeDeploy:** Chuẩn bị các hướng dẫn và tập lệnh triển khai.
- **Tuần 9 — AWS CodePipeline:** Tích hợp các giai đoạn Source, Build và Deploy.
- **Tuần 10 — Rà soát cuối cùng:** Kiểm tra quy trình, xem xét các nhật ký hiện có, ghi nhận những hạn chế và hoàn thiện báo cáo thực tập.

Tiến độ trên thể hiện trình tự công việc dự kiến. Ngày hoàn thành và kết quả thực tế cần được cập nhật phù hợp với những công việc đã thực hiện.

## 6. Dự toán ngân sách

Dự án sử dụng các công cụ dành cho nhà phát triển được AWS quản lý và một máy chủ EC2. Chi phí thực tế phụ thuộc vào Khu vực AWS được lựa chọn, loại Instance, mức độ sử dụng tài nguyên, dung lượng lưu trữ, lưu lượng truyền dữ liệu và bảng giá của từng dịch vụ.

Có thể sử dụng AWS Pricing Calculator để ước tính chi phí trước khi triển khai tài nguyên:

[AWS Pricing Calculator](https://calculator.aws/)

### Chi phí hạ tầng

Các thành phần có thể phát sinh chi phí bao gồm:

- **Amazon EC2:** Chi phí vận hành Instance, dung lượng lưu trữ được gắn kèm và các khoản phí liên quan đến địa chỉ IPv4 công khai hoặc truyền dữ liệu (nếu có).
- **AWS CodeBuild:** Chi phí dựa trên số phút Build và môi trường tính toán được lựa chọn.
- **AWS CodePipeline:** Chi phí Pipeline dựa trên loại Pipeline được lựa chọn và mức độ sử dụng tương ứng.
- **AWS CodeDeploy:** Chi phí sử dụng dịch vụ triển khai; ngoài ra có thể phát sinh chi phí từ các tài nguyên EC2 bên dưới.
- **Amazon CloudWatch:** Chi phí tiếp nhận nhật ký, lưu trữ nhật ký, chỉ số và cảnh báo khi có áp dụng.
- **Các tài nguyên AWS khác:** Chi phí lưu trữ, mạng hoặc các dịch vụ hỗ trợ bổ sung nếu cần thiết.

Chi phí hàng tháng cuối cùng cần được tính toán dựa trên cấu hình thực tế và mức độ sử dụng dự kiến. Đề xuất này chưa đưa ra một tổng chi phí cố định vì kích thước tài nguyên, mức độ sử dụng và thông tin giá cụ thể vẫn chưa được xác định.

Để kiểm soát chi phí, dự án nên sử dụng tài nguyên có cấu hình phù hợp, thường xuyên theo dõi mức độ sử dụng và dừng hoặc xóa những tài nguyên không còn cần thiết.

## 7. Đánh giá rủi ro

### Ma trận rủi ro

- **Lỗi Build:** Mức độ ảnh hưởng trung bình, xác suất xảy ra trung bình. Các thư viện phụ thuộc, phiên bản Java hoặc cấu hình Maven không chính xác có thể khiến quá trình Build thất bại.
- **Lỗi triển khai:** Mức độ ảnh hưởng cao, xác suất xảy ra trung bình. Hướng dẫn triển khai, quyền thực thi của tập lệnh hoặc cấu hình môi trường chạy không chính xác có thể khiến ứng dụng không thể khởi động.
- **Lỗi quyền IAM:** Mức độ ảnh hưởng từ trung bình đến cao, xác suất xảy ra trung bình. Việc thiếu quyền hoặc cấp quyền quá mức có thể làm gián đoạn Pipeline hoặc tạo ra rủi ro bảo mật.
- **Sự cố mạng và kết nối:** Mức độ ảnh hưởng trung bình, xác suất xảy ra trung bình. Các quy tắc Security Group hoặc sự cố kết nối có thể khiến người dùng không thể truy cập ứng dụng.
- **Chi phí AWS phát sinh ngoài dự kiến:** Mức độ ảnh hưởng trung bình, xác suất xảy ra từ thấp đến trung bình. Các tài nguyên vẫn hoạt động khi không còn cần thiết hoặc mức sử dụng vượt quá dự toán có thể làm tăng chi phí.

Các mức đánh giá trên chỉ mang tính sơ bộ và cần được xem xét lại trong quá trình triển khai dự án.

### Các biện pháp giảm thiểu rủi ro

- **Đảm bảo độ tin cậy của Build:** Sử dụng các lệnh Build được xác định rõ ràng, chạy kiểm thử đơn vị và kiểm tra nhật ký CodeBuild.
- **Đảm bảo độ tin cậy của triển khai:** Xác thực gói triển khai, kiểm tra các tập lệnh trong vòng đời triển khai và xem xét nhật ký CodeDeploy.
- **Kiểm soát quyền truy cập:** Áp dụng nguyên tắc cấp quyền tối thiểu (Least Privilege) cho IAM và tránh lưu trữ thông tin xác thực trực tiếp trong mã nguồn.
- **Bảo mật mạng:** Hạn chế quyền truy cập từ bên ngoài, chỉ cho phép các cổng và địa chỉ nguồn cần thiết cho dự án.
- **Quản lý chi phí:** Theo dõi thông tin thanh toán AWS, ước tính chi phí trước khi triển khai và thiết lập cảnh báo ngân sách khi phù hợp.

### Kế hoạch dự phòng

- Nếu quá trình Build thất bại, kiểm tra nhật ký Build, sửa cấu hình và thực hiện Build lại.
- Nếu quá trình triển khai thất bại, kiểm tra thông tin chi tiết của lần triển khai trong CodeDeploy và nhật ký ứng dụng, sau đó điều chỉnh cấu hình triển khai.
- Nếu ứng dụng không thể truy cập, kiểm tra máy chủ EC2 và môi trường chạy ứng dụng trước khi thử triển khai lại.
- Nếu không còn cần sử dụng tài nguyên, tiến hành dừng hoặc xóa chúng khi phù hợp sau khi xác nhận thao tác đó không làm mất dữ liệu cần thiết.

## 8. Kết quả dự kiến

### Những cải thiện về mặt kỹ thuật

Dự án kỳ vọng xây dựng được một quy trình CI/CD có thể lặp lại, kết nối hoạt động quản lý mã nguồn, biên dịch và kiểm thử tự động với quá trình triển khai ứng dụng web được lưu trữ trên máy chủ EC2.

Các kết quả kỹ thuật dự kiến bao gồm:

- Một kho lưu trữ GitHub chứa mã nguồn ứng dụng và các tệp cấu hình CI/CD.
- Một dự án AWS CodeBuild có khả năng Build và kiểm thử ứng dụng.
- Một cấu hình AWS CodeDeploy phục vụ triển khai ứng dụng lên EC2.
- Một quy trình AWS CodePipeline điều phối các giai đoạn Source, Build và Deploy.
- Một quy trình được tài liệu hóa để kiểm tra kết quả Build và triển khai.
- Một phương pháp cơ bản để giám sát và xử lý sự cố bằng các nhật ký và chỉ số AWS hiện có.

### Giá trị lâu dài

Dự án mang lại kinh nghiệm thực hành về các nguyên tắc CI/CD và những công cụ dành cho nhà phát triển của AWS. Kiến trúc này có thể được sử dụng làm nền tảng cho những cải tiến trong tương lai, bao gồm bổ sung các bài kiểm thử tự động, kiểm tra chất lượng mã nguồn, quét bảo mật, các bước phê duyệt, chiến lược khôi phục phiên bản và hệ thống giám sát toàn diện hơn.

Phần đánh giá cuối cùng cần ghi nhận những thành phần đã được triển khai thành công, các bài kiểm thử đã thực hiện, những hạn chế gặp phải và các hướng cải thiện có thể tiếp tục thực hiện trong tương lai.