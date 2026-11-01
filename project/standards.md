# Engineering standards

## Coding
Chưa tạo mã nguồn hoặc chọn toolchain. Tách trách nhiệm PIC, ESP32 và nền tảng; ghi rõ giao thức và giới hạn trước khi triển khai. Không tự thêm chức năng chưa thống nhất.

## Testing
Kiểm tra cảm biến, RTC, OLED, nút nhấn, UART, luồng truyền/lưu dữ liệu và dashboard trên mạch thật. Thử lỗi cảm biến, dữ liệu lỗi, vượt ngưỡng, mất mạng, kết nối lại và khởi động lại. Proteus chỉ dùng cho khối có mô hình phù hợp.

## Review
Đối chiếu yêu cầu đã duyệt và phần cứng thực tế; phân biệt mục tiêu, thiết kế và kết quả thực nghiệm. Không ghi số đo hoặc kết quả chưa thực hiện.

## Delivery
Giữ bản Word gốc, tạo bản cập nhật riêng. Chỉ xuất PDF khi được yêu cầu/duyệt. Workspace dùng nhánh main, planning lưu cục bộ trong .planning; chưa thiết lập remote.
