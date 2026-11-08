---
title: "Nhật ký thực tập tuần 5"
date: 2026-09-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5

* Hiểu những kiến thức cơ bản về kiểm thử đơn vị (Unit Testing) trong ứng dụng web Spring Boot.
* Tìm hiểu cách viết và thực thi kiểm thử đơn vị bằng JUnit và Mockito.
* Kiểm tra chức năng của ứng dụng trước khi tích hợp dự án với AWS CodeBuild.
* Hiểu các lệnh Maven được sử dụng để chạy kiểm thử và đóng gói ứng dụng.
* Chuẩn bị ứng dụng và cấu hình kiểm thử cho quá trình xây dựng tự động.

### Các công việc thực hiện trong tuần

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - Xem xét mục đích của kiểm thử đơn vị trong quá trình phát triển phần mềm. <br> - Hiểu cách kiểm thử đơn vị giúp phát hiện lỗi trước khi triển khai ứng dụng. | 09/12/2026 | 09/12/2026 | [Hướng dẫn sử dụng JUnit 5](https://junit.org/junit5/docs/current/user-guide/) |
| 2 | - Xem xét cấu trúc dự án Spring Boot hiện có và thư mục chứa các tệp kiểm thử. <br> - Xác định các thành phần của ứng dụng cần được kiểm thử. | 09/13/2026 | 09/13/2026 | [Kiểm thử Spring Boot](https://docs.spring.io/spring-boot/reference/testing/index.html) |
| 3 | - Tìm hiểu cách viết kiểm thử đơn vị bằng JUnit. <br> - Khám phá Mockito để tách biệt các thành phần phụ thuộc khi kiểm thử các thành phần của ứng dụng. | 09/14/2026 | 09/14/2026 | [Tài liệu Mockito](https://site.mockito.org/) |
| 4 | - Viết hoặc xem xét các kiểm thử đơn vị cho những chức năng chính của ứng dụng. <br> - Chạy các bài kiểm thử và kiểm tra kết quả. <br> - Xác định và khắc phục các lỗi được phát hiện trong quá trình kiểm thử. | 09/15/2026 | 09/16/2026 | [Hướng dẫn sử dụng JUnit 5](https://junit.org/junit5/docs/current/user-guide/) |
| 5 | - Tìm hiểu cách sử dụng Maven để biên dịch mã nguồn, thực thi kiểm thử và đóng gói ứng dụng. <br> - Chạy các lệnh `mvnw.cmd clean test` và `mvnw.cmd clean package` trong môi trường phát triển cục bộ. <br> - Xem xét các tệp và câu lệnh cần thiết cho giai đoạn cấu hình AWS CodeBuild tiếp theo. | 09/17/2026 | 09/18/2026 | [Vòng đời xây dựng Maven](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html) |

### Kết quả đạt được trong tuần 5

* Hiểu được vai trò của kiểm thử đơn vị trong việc xác minh chức năng ứng dụng và nâng cao chất lượng phần mềm.
* Làm quen với JUnit và các nguyên tắc cơ bản khi viết kiểm thử đơn vị.
* Tìm hiểu cách Mockito có thể được sử dụng để tách biệt các thành phần phụ thuộc trong quá trình kiểm thử khi phù hợp.
* Thực hành chạy kiểm thử đơn vị và xem xét kết quả kiểm thử bằng Maven.
* Hiểu được quy trình xây dựng của Maven, bao gồm biên dịch mã nguồn, chạy kiểm thử và đóng gói ứng dụng.
* Xác định được các tệp ứng dụng và câu lệnh kiểm thử sẽ được sử dụng trong giai đoạn AWS CodeBuild.
* Chuẩn bị dự án cho giai đoạn tiếp theo: cấu hình quy trình xây dựng tự động bằng AWS CodeBuild.