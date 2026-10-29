BÀI LÀM: HỆ THỐNG HÓA KIẾN THỨC VÀ BÀI TOÁN FASTSHIP COLD CHAIN
1. Mục tiêu
Hệ thống hóa kiến thức về Ngành CNTT, Vai trò IT, IPO, DIKW, và Lưu trữ.
2. Bối cảnh
FastShip mở rộng sang mảng 'Giao hàng lạnh' (Cold Chain) cho vắc-xin và thực phẩm đông lạnh. Yêu cầu giám sát nhiệt độ xe tải liên tục 24/7.
PHẦN 1: XÁC ĐỊNH CẤU TRÚC
1. Mô hình IPO của Hệ thống Cảm biến Nhiệt độ
Input (Đầu vào):
Dữ liệu vật lý thu thập từ cảm biến: Giá trị nhiệt độ (°C), độ ẩm (%).
Dữ liệu trạng thái xe: Tọa độ GPS, trạng thái cửa thùng xe (Đóng/Mở), mã định danh xe/thiết bị (Device ID), mốc thời gian (Timestamp).
Process (Xử lý):
Tiền xử lý & Lọc nhiễu tín hiệu gửi về qua sóng 4G/NB-IoT.
So sánh giá trị nhiệt độ thực tế với ngưỡng an toàn cài đặt sẵn (ví dụ: Vắc-xin 2°C -> 8°C, Thực phẩm đông lạnh <= -18°C).
Định dạng dữ liệu, tính toán tốc độ biến thiên nhiệt độ (tăng/giảm nhanh bất thường).
Output (Đầu ra):
Màn hình giám sát thời gian thực (Real-time Dashboard) hiển thị biểu đồ nhiệt độ & vị trí xe.
Tín hiệu cảnh báo tức thì (Còi/Đèn báo trên cabin tài xế, Thông báo Push Notification / SMS đến bộ phận vận hành).
Báo cáo nhật ký hành trình nhiệt độ (Temperature Log Report) phục vụ kiểm toán chất lượng.
2. Phân biệt vai trò BA và SE trong Giai đoạn Đầu Dự án
Tiêu chí
Chuyên viên Phân tích Nghiệp vụ (BA)
Kỹ sư Phần mềm (SE)
Vai trò chính
Làm cầu nối giữa bộ phận vận hành FastShip và đội ngũ kỹ thuật; làm rõ yêu cầu nghiệp vụ.
Thiết kế kiến trúc kỹ thuật và hiện thực hóa hệ thống bằng mã nguồn/công nghệ.
Nhiệm vụ 1
Phỏng vấn quản lý kho/vận hành để xác định quy trình Cold Chain.
Nghiên cứu & Lựa chọn công nghệ/giao thức truyền tải (MQTT, HTTP, RESTful API).
Nhiệm vụ 2
Phân tích các tiêu chuẩn bắt buộc (như tiêu chuẩn lưu trữ vắc-xin GDP/GSP).
Thiết kế cơ sở dữ liệu chuỗi thời gian (Time-series Database) để lưu trữ log sensor.
Nhiệm vụ 3
Viết tài liệu tả yêu cầu hệ thống (BRD, SRS), vẽ biểu đồ luồng nghiệp vụ (Business Process Flow).
Xây dựng kiến trúc phần mềm, chọn Cloud Platform (AWS, GCP, Azure).
Nhiệm vụ 4
Định nghĩa quy tắc cảnh báo (vượt ngưỡng bao nhiêu lâu thì bắn SMS, gửi cho ai).
Lập kế hoạch phân chia module (Backend, Frontend, Mobile App cho tài xế).

PHẦN 2: XỬ LÝ TÌNH HUỐNG
3. Áp dụng Tháp DIKW
Số liệu 2°C, 3°C thu về liên tục:
Đây là Data (Dữ liệu thô). Đó là các con số/ký tự riêng lẻ, chưa được gán ngữ cảnh hay ý nghĩa cụ thể.
Phát hiện "Thùng xe số 5 đang tăng nhiệt độ quá mức an toàn":
Đây là Information (Thông tin). Dữ liệu thô đã được xử lý bằng cách gắn ngữ cảnh (Thùng xe số 5) và so sánh với quy tắc nghiệp vụ (Vượt mức an toàn) để mang lại ý nghĩa rõ ràng.
4. Tính toán Dung lượng Lưu trữ Phần cứng
A. Tính toán cho 1 xe tải trong 1 ngày (24 giờ):
Số giây trong 1 ngày = 24 giờ x 60 phút x 60 giây = 86,400 giây.
Dung lượng = 86,400 giây x 1 KB/giây = 86,400 KB.
Quy đổi ra Megabyte (MB): 86,400 / 1024 ≈ 84.375 MB/ngày (hoặc 86.4 MB/ngày theo hệ thập phân).
B. Tính toán cho 1,000 xe tải trong 1 ngày:
Tổng dung lượng = 84.375 MB/xe/ngày x 1,000 xe = 84,375 MB.
Quy đổi ra Gigabyte (GB): 84,375 / 1024 ≈ 82.4 GB/ngày (hoặc 84.375 GB/ngày theo hệ thập phân).

