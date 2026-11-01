# Architecture

## Components
- AT89S52: đọc DHT11 và giờ UART từ ESP32, cập nhật OLED, xử lý nút chuyển trang.
- ESP32: Wi-Fi, truyền dữ liệu lên nền tảng, phản hồi trạng thái mạng/gửi dữ liệu cho AT89S52.
- Nền tảng IoT: dự kiến ThingsBoard hoặc tương tự; lưu trữ, dashboard, tài khoản và cảnh báo.

## Data flow
DHT11 → AT89S52 → OLED. AT89S52 ↔ ESP32 qua UART. ESP32 → Wi-Fi/Internet → nền tảng IoT → dashboard web. Bản ghi có mã thiết bị, thời gian đo, nhiệt độ và độ ẩm. Hai trang OLED: đo/ngày giờ; Wi-Fi/cloud/lần gửi thành công.

## Integration boundaries
Kiểm tra nguồn, mức logic I²C/UART và driver SSD1315 trên mạch thật trước khi chốt kết nối. Cảnh báo ngưỡng thuộc nền tảng/web, chưa có còi hay điều khiển tải. Mất mạng vẫn đo và hiển thị; tự kết nối lại, thể hiện khoảng thiếu lịch sử. Dữ liệu cảm biến lỗi không được coi là số đo hợp lệ.

Module TXS0108E: A1/B1 SDA, A2/B2 SCL, A3/B3 AT89S52 TX→ESP RX, A4/B4 ESP TX→AT89S52 RX. VCCA=3,3 V, VCCB=5 V, OE=GPIO6 + kéo xuống 100 kΩ. Burn-E9.00.88 hỗ trợ AT89S52; J3 ISP theo thứ tự RST/VCC/GND/MISO/SCK/MOSI. AT89S52 cần thạch anh 11,0592 MHz và EA31 kéo 5V khi ISP. RST9 active-high với R1 pulldown và C2 10uF power-on reset.

Không dùng RTC ngoài hoặc pin giữ giờ. ESP32 đồng bộ NTP, gắn timestamp lúc nhận frame và gửi giờ cho AT89S52 hiển thị; chưa đồng bộ hoặc UART hết hạn thì AT89S52 báo TIME NOT SYNCED. Telemetry/dashboard dùng time_ok, không còn rtc_ok.
