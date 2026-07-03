---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:

* Triển khai cơ chế gửi nhận tin nhắn bất đồng bộ bằng Amazon SNS và Amazon SQS.

* Cấu hình giám sát và ghi log bằng Amazon CloudWatch.

### Các công việc thực hiện trong tuần:

| Ngày | Công việc                                                                                                                                                           | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                                                   |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | -------------------------------------------------------------------- |
| 72   | - Tìm hiểu các khái niệm của Amazon SNS và quy trình gửi thông báo.<br>- Tạo SNS Topic và cấu hình Subscription.<br>- Kiểm thử việc gửi thông điệp.               | 22/06/2026   | 22/06/2026      | https://docs.aws.amazon.com/sns/                                     |
| 73   | - Tìm hiểu Amazon SQS (Standard Queue, FIFO Queue, Dead Letter Queue).<br>- Tạo và cấu hình các hàng đợi SQS.<br>- Kiểm thử việc gửi và nhận tin nhắn.            | 23/06/2026   | 23/06/2026      | https://docs.aws.amazon.com/sqs/                                     |
| 74   | - Tích hợp Amazon SNS với Amazon SQS.<br>- Cấu hình Queue Policy cho SQS.<br>- Kiểm tra việc truyền thông điệp giữa SNS và SQS.                                   | 24/06/2026   | 24/06/2026      | https://docs.aws.amazon.com/sns/latest/dg/sns-sqs-as-subscriber.html |
| 75   | - Cấu hình Amazon CloudWatch Logs để thu thập log.<br>- Thiết lập CloudWatch Metrics phục vụ giám sát hệ thống.                                                   | 25/06/2026   | 25/06/2026      | https://docs.aws.amazon.com/cloudwatch/                              |
| 76   | - Tạo CloudWatch Alarm theo dõi trạng thái ứng dụng.<br>- Kiểm tra việc ghi log và thu thập Metrics.<br>- Hoàn thiện cấu hình các dịch vụ AWS đã triển khai.     | 26/06/2026   | 26/06/2026      | https://docs.aws.amazon.com/                                         |

### Kết quả đạt được trong Tuần 11:

* Triển khai thành công Amazon SNS để gửi thông báo giữa các thành phần của ứng dụng.

* Cấu hình thành công Amazon SQS hỗ trợ xử lý tin nhắn bất đồng bộ.

* Tích hợp Amazon SNS với Amazon SQS và xác nhận việc truyền thông điệp hoạt động chính xác.

* Cấu hình Amazon CloudWatch để thu thập log, theo dõi Metrics và thiết lập Alarm.

* Hoàn thành việc triển khai các dịch vụ nhắn tin và giám sát, sẵn sàng cho giai đoạn kiểm thử hệ thống.