---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# TĂNG TỐC PHÁT TRIỂN TRÒ CHƠI VỚI MULTI-BUILD TRÊN AMAZON GAMELIFT SERVERS

## Giới thiệu

Trong quá trình phát triển trò chơi trực tuyến, việc cập nhật và kiểm thử nhiều phiên bản máy chủ trò chơi diễn ra thường xuyên. Tuy nhiên, việc triển khai từng phiên bản mới lên hạ tầng có thể tốn nhiều thời gian và ảnh hưởng đến quá trình kiểm thử.

AWS đã giới thiệu giải pháp **Multi-Build** trên **Amazon GameLift Servers**, cho phép nhà phát triển lưu trữ và vận hành nhiều phiên bản máy chủ trò chơi trên cùng một Fleet, giúp đẩy nhanh quá trình phát triển và kiểm thử game.

## Amazon GameLift Servers là gì?

**Amazon GameLift Servers** là dịch vụ lưu trữ máy chủ trò chơi (Game Server Hosting) được AWS quản lý hoàn toàn. Dịch vụ này giúp các nhà phát triển triển khai, quản lý và mở rộng hệ thống máy chủ trò chơi trên phạm vi toàn cầu.

Nhiều tựa game lớn trên thị trường đã sử dụng Amazon GameLift Servers nhằm đảm bảo khả năng mở rộng và tính ổn định cho hàng triệu người chơi.

## Những khó khăn trong quá trình phát triển game

Thông thường, mỗi khi có một phiên bản máy chủ mới, nhóm phát triển phải thực hiện các bước sau:

- Build lại máy chủ trò chơi.
- Triển khai phiên bản mới lên hạ tầng.
- Kiểm thử và xác minh các chức năng.
- Chuyển đổi giữa các phiên bản khi cần kiểm thử.

Quy trình này tiêu tốn khá nhiều thời gian, đặc biệt trong các giai đoạn **Alpha** và **Beta**, khi việc cập nhật diễn ra liên tục.

## Giải pháp Multi-Build

**Multi-Build** là giải pháp cho phép lưu trữ nhiều phiên bản máy chủ trò chơi trên cùng một **Amazon GameLift Fleet**.

Thay vì phải triển khai lại toàn bộ hệ thống, nhà phát triển chỉ cần:

- Tải phiên bản mới lên **Amazon S3**.
- Hệ thống tự động đồng bộ phiên bản mới đến các máy chủ GameLift.
- Khi tạo **Game Session**, chỉ cần chỉ định **BuildVersion** muốn sử dụng.
- Máy chủ sẽ tự động khởi chạy đúng phiên bản tương ứng.

Nhờ đó, việc chuyển đổi giữa các phiên bản trở nên nhanh chóng và linh hoạt hơn.

## Kiến trúc hoạt động

Giải pháp sử dụng hai container chính:

### 1. Game Server Container

Container này có nhiệm vụ:

- Chạy máy chủ trò chơi.
- Nhận yêu cầu tạo Game Session.
- Khởi động đúng phiên bản máy chủ theo **BuildVersion** được chỉ định.

### 2. S3 Sync Container

Container này hoạt động liên tục ở chế độ nền với các chức năng:

- Kiểm tra các thay đổi trên **Amazon S3**.
- Đồng bộ các bản build mới.
- Xóa các bản build cũ không còn sử dụng.
- Đảm bảo dữ liệu được tải xuống đầy đủ trước khi thực thi.

Hai container sử dụng chung một thư mục để truy cập các bản build đã được đồng bộ.

## Các dịch vụ AWS được sử dụng

Giải pháp Multi-Build kết hợp nhiều dịch vụ của AWS, bao gồm:

- Amazon GameLift Servers
- Amazon S3
- Amazon ECR
- AWS IAM
- AWS CodeBuild
- AWS CloudFormation
- Amazon CloudWatch Logs

Việc kết hợp các dịch vụ này giúp tự động hóa gần như toàn bộ quá trình triển khai và quản lý máy chủ trò chơi.

## Lợi ích của Multi-Build

### Tăng tốc quá trình phát triển

Nhóm phát triển có thể kiểm thử đồng thời nhiều phiên bản trò chơi mà không cần triển khai lại Fleet.

### Tiết kiệm thời gian

Việc tải lên một bản build mới chỉ mất vài phút thay vì phải thực hiện toàn bộ quy trình triển khai.

### Hỗ trợ kiểm thử Alpha và Beta

Nhiều phiên bản trò chơi có thể cùng tồn tại để phục vụ các nhóm kiểm thử khác nhau.

### Quản lý dễ dàng

Các bản build được quản lý tập trung trên **Amazon S3** và tự động đồng bộ đến các máy chủ GameLift.

## Tổng kết

**Amazon GameLift Servers Multi-Build** là một giải pháp hữu ích dành cho các nhóm phát triển trò chơi muốn tăng tốc quá trình kiểm thử và phát hành phiên bản mới. Việc cho phép nhiều bản build cùng tồn tại trên một Fleet giúp giảm đáng kể thời gian triển khai và tối ưu quy trình phát triển game.

Đối với các dự án đang trong giai đoạn **Alpha**, **Beta** hoặc phát triển tính năng mới, đây là một giải pháp rất đáng để tìm hiểu và triển khai.

![](img/1.png)

![](img/2.png)

**Link tham khảo:** https://aws.amazon.com/vi/blogs/gametech/rapid-game-server-iteration-on-amazon-gamelift-servers/