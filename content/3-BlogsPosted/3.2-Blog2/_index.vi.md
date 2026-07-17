---
title: "Blog 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---
# CHUYỂN ĐỔI NGƯỜI XEM THÀNH NGƯỜI CHƠI VỚI AMAZON GAMELIFT STREAMS

Ngày nay, việc tạo ra những trải nghiệm tương tác trực tiếp đang trở thành xu hướng trong ngành công nghiệp game. Thay vì chỉ xem livestream một cách thụ động, người xem có thể tham gia điều khiển và tương tác với trò chơi theo thời gian thực.

Để giải quyết bài toán này, AWS đã giới thiệu **Amazon GameLift Streams** kết hợp với nhiều dịch vụ khác nhằm xây dựng một hệ thống **Interactive Streaming**, cho phép biến người xem thành người chơi ngay trên trình duyệt mà không cần tải hoặc cài đặt game.

## Những khó khăn trong quá trình phát triển và thử nghiệm game

Các studio game thường gặp nhiều khó khăn như:

- Quá trình tổ chức các buổi playtest mất nhiều thời gian.
- Người chơi phải tải và cài đặt bản build trước khi thử nghiệm.
- Việc thu thập phản hồi từ cộng đồng còn hạn chế.
- Người xem livestream chỉ có thể tương tác thông qua khung chat mà không thể tham gia trực tiếp vào trò chơi.

Những hạn chế này làm giảm hiệu quả của quá trình kiểm thử cũng như khả năng tương tác với cộng đồng.

## Kiến trúc giải pháp

Giải pháp của AWS được xây dựng dựa trên ba thành phần chính.

### 1. Amazon GameLift Streams

Amazon GameLift Streams cho phép truyền trực tiếp trò chơi từ máy chủ đến trình duyệt thông qua giao thức WebRTC.

Một số đặc điểm nổi bật:

- Người chơi không cần tải hoặc cài đặt game.
- Hỗ trợ độ phân giải lên đến **1080p** ở **60 FPS**.
- Độ trễ rất thấp, mang lại trải nghiệm gần như theo thời gian thực.

### 2. Amazon IVS (Interactive Video Service)

Amazon IVS có nhiệm vụ:

- Tiếp nhận luồng video từ máy chủ game.
- Phân phối livestream đến người xem trên toàn cầu.
- Duy trì độ trễ dưới một giây để đảm bảo khả năng tương tác.

### 3. AWS AppSync

AWS AppSync đóng vai trò là cầu nối giữa người xem và trò chơi.

Dịch vụ này cung cấp các WebSocket API giúp:

- Truyền phản hồi từ người xem.
- Gửi các lệnh điều khiển vào trò chơi.
- Đồng bộ trạng thái theo thời gian thực.

## Quy trình hoạt động của hệ thống

Kiến trúc hoạt động theo các bước sau:

1. Người dùng truy cập giao diện React và được xác thực thông qua **Amazon Cognito**.

2. **Amazon API Gateway** kết hợp với **AWS Lambda** xử lý các yêu cầu và khởi tạo phiên phát trực tuyến.

3. Trên máy chủ, **Amazon GameLift Streams** chạy trò chơi và đồng thời khởi động một tiến trình nền có tên là **Broadcast Sidecar**.

4. Broadcast Sidecar thu nhận hình ảnh và âm thanh của trò chơi, mã hóa video bằng chuẩn **H.264** và truyền trực tiếp đến **Amazon IVS** với độ trễ dưới **300 ms**.

## Cơ chế chuyển quyền điều khiển

Một điểm nổi bật của giải pháp là cơ chế **Control Handoff**, cho phép chuyển quyền điều khiển giữa những người tham gia một cách linh hoạt.

Hệ thống sử dụng **AWS AppSync Event API** để đồng bộ trạng thái thông qua các thông điệp như:

- **TAKEOVER_REQUEST:** Người xem gửi yêu cầu xin quyền điều khiển từ người chơi hiện tại.

- **TAKEOVER_APPROVED:** Hệ thống chấp nhận yêu cầu và chia sẻ phiên chơi thông qua API **CreateStreamSessionConnection**.

Nhờ cơ chế này, nhiều người dùng có thể lần lượt tham gia điều khiển trò chơi mà không làm gián đoạn phiên livestream.

## Lợi ích của giải pháp

Giải pháp mang lại nhiều lợi ích cho các studio phát triển game như:

- Rút ngắn thời gian tổ chức các buổi playtest.
- Không yêu cầu người chơi tải hoặc cài đặt game.
- Tăng khả năng tương tác giữa người xem và trò chơi.
- Hỗ trợ tổ chức các sự kiện livestream có tính tương tác cao.
- Cải thiện trải nghiệm người dùng với độ trễ rất thấp.

## Kết luận

Việc kết hợp **Amazon GameLift Streams**, **Amazon IVS** và **AWS AppSync** giúp AWS xây dựng một nền tảng Interactive Streaming mạnh mẽ, cho phép người xem tham gia trực tiếp vào trò chơi ngay trên trình duyệt.

Giải pháp này không chỉ tối ưu quy trình kiểm thử game mà còn mở ra nhiều hình thức tương tác mới giữa nhà phát triển và cộng đồng người chơi, góp phần nâng cao trải nghiệm và tăng mức độ gắn kết của người dùng.

![](/images/3-BlogsPosted/2/img/1.png)

![](/images/3-BlogsPosted/2/img/2.png)

![](/images/3-BlogsPosted/2/img/3.png)

**Link:** https://aws.amazon.com/blogs/gametech/creating-interactive-gaming-experiences-with-amazon-gamelift-streams-and-amazon-interactive-video-service/