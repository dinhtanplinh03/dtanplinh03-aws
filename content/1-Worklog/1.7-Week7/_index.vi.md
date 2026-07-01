---
title: "Worklog Tuần 7"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---
# Tuần 7

## Mục tiêu tuần 7

* Hiểu các khái niệm về **tính sẵn sàng cao (High Availability)** và **khả năng mở rộng (Scalability)** trên AWS.
* Học cách phân phối lưu lượng truy cập bằng **Elastic Load Balancing (ELB)** và tự động mở rộng tài nguyên bằng **Auto Scaling**.
* Thực hành xây dựng kiến trúc có tính sẵn sàng cao, khả năng chịu lỗi và đáp ứng tốt khi lưu lượng truy cập thay đổi.

## Công việc thực hiện trong tuần

| Ngày | Công việc                                                                                                                                                                      | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo                      |
| ---- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | --------------- | --------------------------------------- |
| 44   | - Tìm hiểu về High Availability và Scalability trên AWS.<br>- Giới thiệu về Elastic Load Balancing (ELB).<br>- Tìm hiểu các loại Load Balancer trên AWS.                       | 25/05/2026   | 25/05/2026      | https://cloudjourney.awsstudygroup.com/ |
| 45   | - Tìm hiểu về Application Load Balancer (ALB).<br>- Tìm hiểu Target Groups và Health Checks.<br>- Khám phá cơ chế phân phối lưu lượng truy cập (Traffic Distribution).         | 26/05/2026   | 26/05/2026      | https://cloudjourney.awsstudygroup.com/ |
| 46   | - **Thực hành:**<br> + Khởi tạo nhiều EC2 Instances.<br> + Tạo Application Load Balancer.<br> + Cấu hình Target Groups và Health Checks.                                       | 27/05/2026   | 27/05/2026      | https://cloudjourney.awsstudygroup.com/ |
| 47   | - Tìm hiểu về Auto Scaling Groups (ASG).<br>- Tìm hiểu các Scaling Policies.<br>- Hiểu cách AWS tự động điều chỉnh số lượng tài nguyên theo nhu cầu sử dụng.                   | 28/05/2026   | 28/05/2026      | https://cloudjourney.awsstudygroup.com/ |
| 48   | - **Thực hành:**<br> + Tạo Auto Scaling Group.<br> + Cấu hình Scaling Policies.<br> + Mô phỏng lưu lượng truy cập để quan sát quá trình tự động mở rộng và thu hẹp tài nguyên. | 29/05/2026   | 29/05/2026      | https://cloudjourney.awsstudygroup.com/ |

## Kết quả đạt được trong tuần 7

* Nắm vững các khái niệm về **High Availability (Tính sẵn sàng cao)** và **Scalability (Khả năng mở rộng)** trong môi trường điện toán đám mây.

* Hiểu rõ các thành phần chính của **Elastic Load Balancing (ELB)**, bao gồm:

  * Application Load Balancer (ALB).
  * Target Groups.
  * Health Checks.
  * Traffic Routing.

* Cấu hình thành công **Application Load Balancer** để phân phối lưu lượng truy cập đến nhiều EC2 Instances, giúp tăng tính sẵn sàng và hiệu năng của hệ thống.

* Tích lũy kinh nghiệm thực tế trong việc theo dõi tình trạng hoạt động của các EC2 Instances và tự động chuyển hướng lưu lượng truy cập khi một Instance gặp sự cố hoặc không còn khả dụng.

* Hiểu nguyên lý hoạt động của **Auto Scaling** và cách AWS tự động điều chỉnh số lượng tài nguyên tính toán dựa trên nhu cầu thực tế của hệ thống.

* Tạo và cấu hình thành công **Auto Scaling Groups (ASG)** cùng các **Scaling Policies** để:

  * Tự động tăng số lượng EC2 Instances khi lưu lượng truy cập tăng cao.
  * Tự động giảm số lượng EC2 Instances khi nhu cầu sử dụng giảm.
  * Nâng cao tính sẵn sàng của ứng dụng đồng thời tối ưu chi phí vận hành.

* Xây dựng được một kiến trúc có tính sẵn sàng cao, có khả năng xử lý sự thay đổi về lưu lượng truy cập mà vẫn đảm bảo hiệu năng và tính ổn định của ứng dụng.

* Phát triển kỹ năng thực tế trong việc thiết kế hạ tầng AWS có khả năng mở rộng, độ tin cậy cao và đáp ứng các tiêu chuẩn kiến trúc Cloud hiện đại về tính sẵn sàng và khả năng chịu lỗi.
