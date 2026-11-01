# Project context

## Product
Đồ án 2: hệ thống giám sát nhiệt độ, độ ẩm dùng AT89S52, ESP32 và nền tảng IoT có sẵn theo hướng ThingsBoard. Làm mạch thật kết nối Internet.

## Users
Sinh viên: Phạm Thanh Tuấn, Nguyễn Quốc Sinh; lớp Kỹ thuật điện tử - viễn thông K46. Giảng viên hướng dẫn: TS Nguyễn Đỗ Dũng. Phạm vi sản phẩm ban đầu: một thiết bị, một tài khoản chủ thiết bị.

## Goals
Đo bằng DHT11, gắn thời gian NTP từ ESP32, hiển thị OLED SSD1315 0,96 inch I²C. ESP32 truyền bản ghi lên cloud; dashboard xem dữ liệu mới nhất, lịch sử, biểu đồ, lọc thời gian, xuất CSV và cảnh báo ngưỡng. Đây là mục tiêu thiết kế đã thống nhất, chưa phải tính năng đã triển khai.

## Constraints
Giữ AT89S52 là bộ xử lý đo và hiển thị. Không lưu bù khi mất mạng ở bản đầu. Chưa chọn dịch vụ/bản triển khai cloud cụ thể. Bản triển khai dùng HTTPS, chu kỳ gửi 10 giây và bảng chân tại hardware/wiring.md. Đối chiếu tính năng nền tảng và module thực tế trước khi triển khai. Tài liệu gốc giữ nguyên; bản cập nhật: `TÓM TẮT ĐỀ TÀI ĐỒ ÁN 2 - IoT OLED.docx`.

## Bản triển khai 2026-11-01
Đã có firmware AT89S52/ESP32, giao thức CRC-8 UART, gửi HTTPS ThingsBoard mỗi 10 giây, dashboard native 11 widget, BOM 38 chi tiết và sơ đồ nối dây. Đã đổi sang module TXS0108E cho I²C/UART, OE từ GPIO6; ESP32 bật OE sau 100 ms và AT89S52 thử lại khởi tạo OLED. Đã chuyển hoàn toàn sang SDCC 8051, có HEX/release memory report cho AT89S52; không dùng XC8. Burn-E9.00.88 đã chọn AT89S52, người dùng tự thực hiện Verify. Chưa nạp chip.

Không dùng RTC ngoài hoặc pin giữ giờ. ESP32 đồng bộ NTP, gắn timestamp lúc nhận frame và gửi giờ cho AT89S52 hiển thị; chưa đồng bộ hoặc UART hết hạn thì AT89S52 báo TIME NOT SYNCED. Telemetry/dashboard dùng time_ok, không còn rtc_ok.

Đã chốt ESP32-C3 SuperMini (UART1 GPIO4/5, OE GPIO6) và ThingsBoard. Local CE4.3.1.8 tại127.0.0.1:18080 đã import dashboard tiếng Anh, phát dữ liệu giả lập và kiểm tra lưu ngưỡng/cảnh báo. BOM38chi tiết; giá mua đã có +PCB120.000đ là403.500đ, chưa cộng F1 chưa xác minh. Chi tiết tại hardware/cost-estimate.md. Chưa triển khai thiết bị thật hoặc dịch vụ Internet.
