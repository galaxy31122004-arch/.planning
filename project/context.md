# Project context

## Product
Đồ án 2: hệ thống giám sát nhiệt độ, độ ẩm dùng PIC16F877A, ESP32 và nền tảng IoT có sẵn theo hướng Core IoT/ThingsBoard. Làm mạch thật kết nối Internet.

## Users
Sinh viên: Phạm Thanh Tuấn, Nguyễn Quốc Sinh; lớp Kỹ thuật điện tử - viễn thông K46. Giảng viên hướng dẫn: TS Nguyễn Đỗ Dũng. Phạm vi sản phẩm ban đầu: một thiết bị, một tài khoản chủ thiết bị.

## Goals
Đo bằng DHT11, gắn thời gian từ DS1307, hiển thị OLED SSD1315 0,96 inch I²C. ESP32 truyền bản ghi lên cloud; dashboard xem dữ liệu mới nhất, lịch sử, biểu đồ, lọc thời gian, xuất CSV và cảnh báo ngưỡng. Đây là mục tiêu thiết kế đã thống nhất, chưa phải tính năng đã triển khai.

## Constraints
Giữ PIC là bộ xử lý đo và hiển thị. Không lưu bù khi mất mạng ở bản đầu. Chưa chọn dịch vụ/bản triển khai cloud, giao thức mạng, chu kỳ gửi hoặc sơ đồ chân. Đối chiếu tính năng nền tảng và module thực tế trước khi triển khai. Tài liệu gốc giữ nguyên; bản cập nhật: `TÓM TẮT ĐỀ TÀI ĐỒ ÁN 2 - IoT OLED.docx`.
