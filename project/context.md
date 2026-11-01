# Project context

## Product
Đồ án 2: hệ thống giám sát nhiệt độ, độ ẩm dùng PIC16F877A, ESP32 và nền tảng IoT có sẵn theo hướng Core IoT/ThingsBoard. Làm mạch thật kết nối Internet.

## Users
Sinh viên: Phạm Thanh Tuấn, Nguyễn Quốc Sinh; lớp Kỹ thuật điện tử - viễn thông K46. Giảng viên hướng dẫn: TS Nguyễn Đỗ Dũng. Phạm vi sản phẩm ban đầu: một thiết bị, một tài khoản chủ thiết bị.

## Goals
Đo bằng DHT11, gắn thời gian từ DS1307, hiển thị OLED SSD1315 0,96 inch I²C. ESP32 truyền bản ghi lên cloud; dashboard xem dữ liệu mới nhất, lịch sử, biểu đồ, lọc thời gian, xuất CSV và cảnh báo ngưỡng. Đây là mục tiêu thiết kế đã thống nhất, chưa phải tính năng đã triển khai.

## Constraints
Giữ PIC là bộ xử lý đo và hiển thị. Không lưu bù khi mất mạng ở bản đầu. Chưa chọn dịch vụ/bản triển khai cloud cụ thể. Bản triển khai dùng HTTPS, chu kỳ gửi 10 giây và bảng chân tại hardware/wiring.md. Đối chiếu tính năng nền tảng và module thực tế trước khi triển khai. Tài liệu gốc giữ nguyên; bản cập nhật: `TÓM TẮT ĐỀ TÀI ĐỒ ÁN 2 - IoT OLED.docx`.

## Bản triển khai 2026-11-01
Đã có firmware PIC/ESP32, giao thức CRC-8 UART, gửi HTTPS ThingsBoard mỗi 10 giây, dashboard native 11 widget, BOM 43 chi tiết và sơ đồ nối dây. Đã đổi sang module TXS0108E cho I²C/UART, OE từ GPIO27; ESP32 bật OE sau 100 ms và PIC thử lại khởi tạo OLED. Người dùng dùng Burn-E nạp PIC và yêu cầu bỏ bước cài/build compiler trên máy này. Mã PIC hiện giữ cú pháp XC8, chưa có HEX/build/bộ nhớ PIC được kiểm chứng. Dashboard cần tenant thật.
