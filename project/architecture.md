# Architecture

## Components
- PIC16F877A: đọc DHT11 và DS1307, cập nhật OLED, xử lý nút chuyển trang.
- ESP32: Wi-Fi, truyền dữ liệu lên nền tảng, phản hồi trạng thái mạng/gửi dữ liệu cho PIC.
- Nền tảng IoT: dự kiến Core IoT/ThingsBoard hoặc tương tự; lưu trữ, dashboard, tài khoản và cảnh báo.

## Data flow
DHT11 + DS1307 → PIC → OLED. PIC ↔ ESP32 qua UART. ESP32 → Wi-Fi/Internet → nền tảng IoT → dashboard web. Bản ghi có mã thiết bị, thời gian đo, nhiệt độ và độ ẩm. Hai trang OLED: đo/ngày giờ; Wi-Fi/cloud/lần gửi thành công.

## Integration boundaries
Kiểm tra nguồn, mức logic I²C/UART và driver SSD1315 trên mạch thật trước khi chốt kết nối. Cảnh báo ngưỡng thuộc nền tảng/web, chưa có còi hay điều khiển tải. Mất mạng vẫn đo và hiển thị; tự kết nối lại, thể hiện khoảng thiếu lịch sử. Dữ liệu cảm biến lỗi không được coi là số đo hợp lệ.

Module TXS0108E: A1/B1 SDA, A2/B2 SCL, A3/B3 PIC TX→ESP RX, A4/B4 ESP TX→PIC RX. VCCA=3,3 V, VCCB=5 V, OE=GPIO27 + kéo xuống 100 kΩ. Nạp PIC ngoài mạch bằng Burn-E; J3 ICSP chỉ là dự phòng và không suy đoán pinout cáp Burn-E.
