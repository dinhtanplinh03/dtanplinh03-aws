---

title: "Nhật ký công việc Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
-----------------------

### Mục tiêu Tuần 11:

* Triển khai cơ chế gửi nhận tin nhắn bất đồng bộ bằng Amazon SNS và Amazon SQS.
* Cấu hình giám sát và ghi log bằng Amazon CloudWatch.
* Kiểm thử và xác thực luồng xử lý tin nhắn cũng như hệ thống giám sát.
* Chuẩn bị dự án cho giai đoạn triển khai và trình bày cuối cùng.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                    | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | -------------------------------------------------------------------- |
| 72   | - Tìm hiểu các khái niệm của Amazon SNS và quy trình gửi thông báo.<br>- Tạo SNS Topic và cấu hình các Subscription.<br>- Kiểm thử việc gửi thông điệp.      | 06/29/2026   | 06/29/2026      | https://docs.aws.amazon.com/sns/                                     |
| 73   | - Tìm hiểu Amazon SQS (Standard Queue, FIFO Queue, Dead Letter Queue).<br>- Tạo và cấu hình các hàng đợi SQS.<br>- Kiểm thử việc gửi và nhận tin nhắn.       | 06/30/2026   | 06/30/2026      | https://docs.aws.amazon.com/sqs/                                     |
| 74   | - Tích hợp Amazon SNS với Amazon SQS.<br>- Cấu hình chính sách truy cập (Queue Policy).<br>- Kiểm tra việc truyền thông điệp từ đầu đến cuối.                | 07/01/2026   | 07/01/2026      | https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html |
| 75   | - Cấu hình CloudWatch Logs và CloudWatch Metrics.<br>- Tạo CloudWatch Alarm để giám sát trạng thái ứng dụng.<br>- Kiểm tra việc thu thập log.                | 07/02/2026   | 07/02/2026      | https://docs.aws.amazon.com/cloudwatch/                              |
| 76   | - Kiểm thử toàn bộ luồng xử lý tin nhắn.<br>- Phân tích Metrics và Logs trên CloudWatch.<br>- Khắc phục các lỗi cấu hình và hoàn thiện quá trình triển khai. | 07/03/2026   | 07/03/2026      | https://docs.aws.amazon.com/                                         |

### Kết quả đạt được trong Tuần 11:

* Triển khai thành công Amazon SNS để gửi thông báo giữa các thành phần của ứng dụng.

* Cấu hình Amazon SQS nhằm hỗ trợ xử lý tin nhắn bất đồng bộ một cách ổn định và đáng tin cậy.

* Tích hợp thành công Amazon SNS với Amazon SQS và xác minh việc truyền thông điệp hoạt động chính xác.

* Cấu hình Amazon CloudWatch để thu thập log, theo dõi các chỉ số (Metrics) và thiết lập cảnh báo (Alarms) khi hệ thống có dấu hiệu bất thường.

* Kiểm thử hoàn chỉnh luồng xử lý tin nhắn và xác nhận rằng các thông điệp được xử lý đúng như mong đợi.

* Nâng cao hiểu biết về kiến trúc hướng sự kiện (Event-driven Architecture) thông qua việc sử dụng các dịch vụ nhắn tin của AWS.

* Tăng cường khả năng giám sát hệ thống bằng CloudWatch Logs, Metrics và Alarms.

* Hoàn thành việc triển khai và kiểm thử các thành phần nhắn tin và giám sát, sẵn sàng cho buổi trình bày và triển khai cuối cùng của dự án.
