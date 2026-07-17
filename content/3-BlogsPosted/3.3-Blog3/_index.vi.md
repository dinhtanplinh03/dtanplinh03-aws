---
title: "Blog 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---
# TĂNG TỐC PHÁT TRIỂN GAME VỚI MULTI-BUILD TRÊN AMAZON GAMELIFT SERVERS

Trong quá trình phát triển game trực tuyến, việc cập nhật và kiểm thử nhiều phiên bản máy chủ (Game Server) diễn ra thường xuyên. Tuy nhiên, mỗi lần triển khai một phiên bản mới đều yêu cầu xây dựng lại và triển khai lại hạ tầng, gây mất nhiều thời gian và ảnh hưởng đến tiến độ phát triển.

Để giải quyết vấn đề này, AWS đã giới thiệu tính năng **Multi-Build** trên **Amazon GameLift Servers**, cho phép nhiều phiên bản Game Server cùng hoạt động trên một Fleet, giúp rút ngắn thời gian triển khai và tăng tốc quá trình kiểm thử.

## Amazon GameLift Servers là gì?

**Amazon GameLift Servers** là dịch vụ lưu trữ và quản lý Game Server được AWS quản lý hoàn toàn. Dịch vụ này giúp các nhà phát triển dễ dàng triển khai, vận hành và mở rộng hệ thống Game Server trên phạm vi toàn cầu.

Nhiều tựa game lớn hiện nay đã sử dụng Amazon GameLift để đảm bảo khả năng mở rộng, hiệu suất ổn định và phục vụ hàng triệu người chơi cùng lúc.

## Những khó khăn trong quá trình phát triển game

Thông thường, mỗi khi có một phiên bản Game Server mới, nhóm phát triển phải thực hiện các bước sau:

- Xây dựng (Build) lại Game Server.
- Triển khai lại lên hạ tầng.
- Kiểm thử và xác nhận chức năng.
- Chuyển đổi giữa các phiên bản khi cần kiểm thử.

Quy trình này khá mất thời gian, đặc biệt trong giai đoạn **Alpha** và **Beta**, khi các bản cập nhật được phát hành liên tục.

## Giải pháp Multi-Build

**Multi-Build** là tính năng cho phép lưu trữ và vận hành nhiều phiên bản Game Server trên cùng một Amazon GameLift Fleet.

Thay vì phải triển khai lại toàn bộ hệ thống, nhà phát triển chỉ cần:

- Tải phiên bản Game Server mới lên **Amazon S3**.
- Hệ thống tự động đồng bộ phiên bản mới đến các máy chủ GameLift.
- Khi tạo **Game Session**, chỉ định **BuildVersion** cần sử dụng.
- Máy chủ sẽ tự động khởi chạy đúng phiên bản tương ứng.

Nhờ đó, việc chuyển đổi giữa các phiên bản trở nên nhanh chóng và linh hoạt hơn.

## Kiến trúc hoạt động

Giải pháp Multi-Build sử dụng hai container chính.

### 1. Game Server Container

Container này có nhiệm vụ:

- Chạy Game Server.
- Tiếp nhận yêu cầu tạo Game Session.
- Khởi động đúng phiên bản Game Server theo **BuildVersion** được chỉ định.

### 2. S3 Sync Container

Container này hoạt động liên tục ở chế độ nền và thực hiện các công việc:

- Kiểm tra các thay đổi trên **Amazon S3**.
- Đồng bộ các bản Build mới về máy chủ.
- Xóa các bản Build cũ không còn sử dụng.
- Đảm bảo dữ liệu được tải đầy đủ trước khi Game Server khởi động.

Hai container sử dụng chung một thư mục để truy cập các phiên bản Build đã được đồng bộ.

## Các dịch vụ AWS được sử dụng

Giải pháp Multi-Build kết hợp nhiều dịch vụ AWS như:

- Amazon GameLift Servers
- Amazon S3
- Amazon ECR
- AWS IAM
- AWS CodeBuild
- AWS CloudFormation
- Amazon CloudWatch Logs

Sự kết hợp này giúp tự động hóa gần như toàn bộ quy trình triển khai và quản lý Game Server.

## Lợi ích của Multi-Build

### Tăng tốc độ phát triển

Nhóm phát triển có thể kiểm thử nhiều phiên bản Game Server cùng lúc mà không cần triển khai lại toàn bộ Fleet.

### Tiết kiệm thời gian

Việc tải lên một bản Build mới chỉ mất vài phút thay vì phải thực hiện toàn bộ quy trình triển khai.

### Hỗ trợ kiểm thử Alpha và Beta

Nhiều phiên bản Game Server có thể cùng tồn tại để phục vụ các nhóm người chơi thử nghiệm khác nhau.

### Dễ dàng quản lý

Các bản Build được lưu trữ tập trung trên Amazon S3 và tự động đồng bộ đến các máy chủ GameLift, giúp việc quản lý trở nên đơn giản và hiệu quả hơn.

## Kết luận

**Amazon GameLift Servers Multi-Build** là một giải pháp hữu ích dành cho các nhóm phát triển game muốn tăng tốc quá trình kiểm thử và phát hành phiên bản mới. Việc cho phép nhiều phiên bản Game Server cùng tồn tại trên một Fleet giúp giảm đáng kể thời gian triển khai, tối ưu quy trình phát triển và nâng cao hiệu quả quản lý.

Đối với các dự án game đang trong giai đoạn **Alpha**, **Beta** hoặc liên tục phát triển tính năng mới, Multi-Build là một giải pháp đáng để tìm hiểu và áp dụng.

![](/images/3-BlogsPosted/3/img/1.png)

![](/images/3-BlogsPosted/3/img/2.png)

**Link:** https://aws.amazon.com/vi/blogs/gametech/rapid-game-server-iteration-on-amazon-gamelift-servers/