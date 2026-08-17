# 23646721_NguyenThiHong_cabsystem
# CAB System – Nền tảng đặt xe trực tuyến

## 1. Giới thiệu

 CAB System là một nền tảng đặt xe trực tuyến được thiết kế cho công ty ABC, nhằm thay thế cho mô hình vận hành hiện tại chủ yếu dựa trên một ứng dụng đơn giản hay thông qua tổng đài.
 Mục tiêu của dự án không chỉ dừng lại ở trình thiết lập quy trình số hóa, mà hướng dẫn xây dựng nền tảng có khả năng mở rộng lâu dài,
 phục vụ đồng thời cho ba người dùng chính của nhóm: khách hàng , tài xế và nhân viên vận hành.

 ---
 
## 2. Khó khăn của phương pháp/hệ thống truyền thống

Hệ thống hiện tại của Công ty ABC (tổng đài + app đơn giản) đang gặp phải các hạn chế sau:

| Vấn đề | Mô tả |
|---|---|
| **Phân công tài xế thủ công** | Việc ghép tài xế với khách hàng chủ yếu do con người xử lý, tốn thời gian, dễ sai sót, không tối ưu theo vị trí thực tế và không thể mở rộng khi lượng đơn tăng cao. |
| **Thiếu khả năng theo dõi trạng thái chuyến đi** | Khách hàng không biết hệ thống đang tìm tài xế, tài xế nào đã nhận chuyến, thời gian dự kiến đến hay trạng thái hiện tại — gây trải nghiệm mờ mịt, thiếu tin tưởng. |
| **Thông tin thanh toán phân tán** | Dữ liệu thanh toán chưa được quản lý tập trung, gây khó khăn cho việc đối soát, báo cáo doanh thu và xử lý sự cố giao dịch. |
| **Khó mở rộng hệ thống** | Kiến trúc hiện tại không hỗ trợ tốt việc bổ sung dịch vụ mới, phương thức thanh toán mới hay kênh thông báo mới mà không ảnh hưởng đến toàn bộ hệ thống. |
| **Rủi ro vận hành khi tải cao** | Một lỗi nhỏ (ví dụ ở chức năng thanh toán hoặc thông báo) có thể làm ngưng trệ toàn bộ hoạt động đặt xe, vì các thành phần không tách biệt và không thể scale độc lập. |
| **Thiếu công cụ quản trị & báo cáo tập trung** | Nhân viên vận hành khó theo dõi chuyến đang diễn ra, khó tra cứu lịch sử, và ban lãnh đạo thiếu dữ liệu tổng hợp về số chuyến, doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả tài xế. |
| **Bảo mật & kiểm soát truy cập hạn chế** | Chưa có cơ chế xác thực, phân quyền và lưu vết thao tác rõ ràng cho dữ liệu nhạy cảm (cá nhân, vị trí, giao dịch). |

---
## 3. Những điểm mạnh mà CAB System đáp ứng

### 3.1. Trải nghiệm khách hàng liền mạch
- Đăng ký, đăng nhập, cập nhật thông tin cá nhân
- Đặt xe theo điểm đón/điểm đến, chọn loại xe
- Theo dõi trạng thái chuyến đi theo thời gian thực (đang tìm tài xế → đã nhận chuyến → đang đến → hoàn thành)
- Xem lịch sử chuyến đi, chi phí, đánh giá tài xế sau chuyến

### 3.2. Quản lý tài xế chủ động
- Đăng ký/khởi tạo tài khoản tài xế, cập nhật hồ sơ & phương tiện
- Chuyển đổi trạng thái sẵn sàng nhận chuyến
- Nhận thông báo chuyến mới, chấp nhận/từ chối chuyến
- Cập nhật trạng thái thực hiện chuyến (đến điểm đón, đón khách, di chuyển, hoàn thành)
- Ghi nhận vị trí tài xế để hỗ trợ tìm tài xế gần khách hàng và ước tính thời gian đến chính xác hơn

### 3.3. Cơ chế tìm & phân công tài xế thông minh
- Tự động xác định tài xế phù hợp dựa trên vị trí, trạng thái sẵn sàng và tiêu chí vận hành
- Ưu tiên tài xế gần và phù hợp nhất
- Tự động chuyển sang tài xế khác nếu tài xế được đề xuất không phản hồi/từ chối, **không yêu cầu khách hàng tạo lại yêu cầu**
- Thông báo rõ ràng cho khách hàng khi không tìm được tài xế phù hợp

### 3.4. Thanh toán & tính cước tập trung, an toàn
- Tự động tính cước dựa trên loại dịch vụ và thông tin chuyến đi
- Hỗ trợ đa phương thức: tiền mặt và thanh toán điện tử
- Tích hợp nhà cung cấp thanh toán bên ngoài, **không lưu trữ trực tiếp thông tin nhạy cảm của thẻ/tài khoản** trong hệ thống CAB
- Có cơ chế thông báo và xử lý lại khi giao dịch điện tử thất bại

### 3.5. Thông báo đa kênh, dễ mở rộng
- Thông báo xuyên suốt vòng đời chuyến đi cho cả khách hàng và tài xế (tiếp nhận yêu cầu, nhận chuyến, đến điểm đón, hoàn thành, kết quả thanh toán)
- Kiến trúc cho phép **bổ sung kênh thông báo mới trong tương lai mà không cần thay đổi toàn bộ hệ thống**

### 3.6. Công cụ quản trị vận hành tập trung
- Giao diện quản trị cho nhân viên vận hành: quản lý khách hàng, tài xế, phương tiện, chuyến đi
- Theo dõi chuyến đang diễn ra, xử lý chuyến gặp sự cố, tra cứu lịch sử giao dịch
- Phân quyền chặt chẽ cho các thao tác nhạy cảm
- Báo cáo tổng hợp: số lượng chuyến, doanh thu, tỷ lệ hoàn thành/hủy, hiệu quả hoạt động của tài xế

### 3.7. Kiến trúc ổn định, có khả năng mở rộng
- Các thành phần (đặt xe, thanh toán, thông báo...) hoạt động **độc lập** — lỗi ở một chức năng không làm sập toàn hệ thống
- Có thể **scale riêng từng thành phần** khi tải tăng vào giờ cao điểm
- Hỗ trợ **triển khai từng phần** (incremental deployment) cho tính năng mới, hạn chế ảnh hưởng đến hệ thống đang chạy
- Kiến trúc linh hoạt để bổ sung loại dịch vụ mới, phương thức thanh toán mới, nhà cung cấp thông báo mới, hoặc thay đổi thành phần kỹ thuật mà **không cần xây dựng lại toàn bộ ứng dụng**

### 3.8. Bảo mật & minh bạch
- Xác thực bắt buộc đối với khách hàng và tài xế trước khi sử dụng chức năng yêu cầu tài khoản
- Kiểm soát quyền truy cập chặt chẽ cho các thao tác quản trị
- Bảo vệ dữ liệu cá nhân, thông tin phương tiện, dữ liệu vị trí và dữ liệu giao dịch
- Lưu vết (audit log) các thao tác quan trọng phục vụ kiểm tra khi có sự cố

---


