# Smart Classroom AIoT System

## 1. Mô tả bài toán thực tế

### Bối cảnh
Một phòng học đã được trang bị hệ thống IoT cơ bản, bao gồm:
- Camera giám sát có thể truy cập video stream
- Điều hòa và đèn có thể điều khiển từ xa
- Backend có khả năng thu thập và hiển thị trạng thái thiết bị

Hệ thống hiện tại:
- Hiển thị trạng thái thiết bị
- Cho phép bật/tắt thủ công
- Có thể hoạt động theo rule đơn giản

---

### Vấn đề
- Không biết số lượng người trong phòng
- Không tối ưu nhiệt độ điều hòa theo thực tế sử dụng
- Lãng phí điện khi phòng không có người
- Không phát hiện sử dụng điện bất thường

---

### Người dùng
- Giáo viên
- Quản lý phòng học

---

### Mục tiêu AIoT
- Đếm số lượng người từ camera
- Tối ưu điều hòa và đèn theo mức sử dụng
- Phát hiện bất thường trong tiêu thụ điện
- Tự động hoặc hỗ trợ điều khiển thiết bị

---

## 2. Kiến trúc AIoT

### Các lớp chính

**Device Layer**
- Camera (video stream)
- Điều hòa, đèn (có thể điều khiển từ xa)

**Data Layer**
- Thu thập:
  - people_count
  - ac_state
  - light_state

**Backend + Database**
- Lưu trữ dữ liệu lịch sử
- Quản lý trạng thái thiết bị

**AI Services**
- People Counting
- Anomaly Detection

**Dashboard**
- Hiển thị số người
- Hiển thị trạng thái thiết bị
- Cảnh báo

**Decision + Feedback**
- Ra quyết định dựa trên AI
- Gửi lệnh điều khiển thiết bị

---

## 3. Thiết kế dữ liệu

| Tên dữ liệu        | Nguồn              | Kiểu dữ liệu | Tần suất     | Mục đích AI |
|-------------------|-------------------|-------------|-------------|-------------|
| device_id         | gateway           | string      | mỗi bản tin | định danh |
| timestamp         | hệ thống          | datetime    | mỗi bản tin | time-series |
| people_count      | camera (AI)       | int         | 5–10s       | tối ưu điều hòa |
| ac_state          | điều hòa          | ON/OFF      | khi đổi     | phân tích |
| light_state       | đèn               | ON/OFF      | khi đổi     | phân tích |
| estimated_power   | suy từ thiết bị   | float       | 10s         | anomaly detection |

---

## 4. Module AI

### 1. People Counting
- Input: camera stream
- Output: people_count
- Mục tiêu: xác định số người trong phòng

---

### 2. Anomaly Detection
- Input: estimated_power, people_count
- Output: is_anomaly
- Mục tiêu: phát hiện sử dụng điện bất thường

---

## 5. Rủi ro và an toàn

- Sai số trong đếm người → điều khiển sai
- Ước lượng điện không chính xác
- Tắt thiết bị khi vẫn còn người
- Mất kết nối hệ thống

### Biện pháp
- Chỉ tự động tắt khi people_count = 0
- Cảnh báo trước khi điều khiển
- Cho phép người dùng override

---

## 6. Metric đánh giá

### AI Metric
- People counting accuracy
- Anomaly detection precision / recall

### System Metric
- % giảm điện năng
- Latency
- Uptime hệ thống

---

## 7. Tính triển khai thực tế

- API nhận dữ liệu từ thiết bị
- JSON telemetry chuẩn
- Có thể triển khai trên cloud hoặc local server
- Có dashboard giám sát