## 🧠 Câu hỏi tư duy

### 1. Trong use-case của nhóm, dữ liệu nào là quan trọng nhất? Vì sao?

Dữ liệu quan trọng nhất là **people_count**.  
Đây là tín hiệu phản ánh trực tiếp mức sử dụng phòng học và được dùng để đưa ra các quyết định như bật/tắt điều hòa, đèn hoặc đánh giá việc sử dụng điện có hợp lý hay không. Nếu thiếu dữ liệu này, hệ thống không thể tối ưu vận hành.

---

### 2. AI của nhóm nên chạy ở edge, backend hay cloud? Lý do?

Hệ thống nên kết hợp **Edge và Backend**:

- **Edge (camera):** xử lý People Counting để có kết quả theo thời gian thực  
- **Backend/Cloud:** lưu trữ dữ liệu, phân tích lịch sử và phát hiện bất thường  

Cách tiếp cận này giúp đảm bảo vừa nhanh vừa có khả năng phân tích sâu.

---

### 3. Nếu model dự đoán sai, hậu quả thực tế có thể là gì?

Nếu model sai có thể dẫn đến:
- Tắt điều hòa/đèn khi vẫn còn người → ảnh hưởng trải nghiệm  
- Không tắt khi phòng trống → lãng phí điện  
- Cảnh báo sai → gây phiền và mất niềm tin  
- Thiết bị bật/tắt liên tục → giảm tuổi thọ  

---

### 4. Khi nào hệ thống được phép tự động điều khiển? Khi nào cần xác nhận?

- **Được phép tự động:**
  - Khi `people_count = 0` (phòng trống)  
  - Không có dấu hiệu bất thường  

- **Cần xác nhận:**
  - Khi trong phòng có người  
  - Khi hệ thống phát hiện bất thường  
  - Khi thay đổi ảnh hưởng đến trải nghiệm (ví dụ điều hòa)  

Người xác nhận: giáo viên hoặc quản lý phòng học.

---

### 5. Nhóm cần thu thập dữ liệu trong bao lâu?

Nhóm cần thu thập dữ liệu khoảng **1–2 tuần** để:
- Quan sát các khung giờ sử dụng phòng  
- Ghi nhận số lượng người theo thời gian  
- Xây dựng pattern vận hành thiết bị  

Dữ liệu dài hơn sẽ giúp hệ thống ổn định và chính xác hơn.

---

### 6. Metric nào quan trọng nhất?

Metric quan trọng nhất là **false alarm (cảnh báo sai)** vì:
- Nếu cảnh báo sai nhiều, người dùng sẽ mất niềm tin vào hệ thống  

Bên cạnh đó, **people counting accuracy** cũng rất quan trọng vì ảnh hưởng trực tiếp đến quyết định điều khiển.

---

## 🔍 Nhận xét về vai trò của AI trong hệ thống

AI trong bài toán này không chỉ dùng để “dự đoán”, mà đóng vai trò chính trong việc:

- **Nhận thức (Perception):** đếm số người từ camera  
- **Phân tích (Analysis):** phát hiện bất thường trong sử dụng điện  
- **Hỗ trợ quyết định (Decision Support):** đề xuất hoặc tự động điều khiển thiết bị  

Nhờ AI, hệ thống được nâng cấp từ:
- IoT (chỉ thu thập và điều khiển thủ công)

thành:
- AIoT (có khả năng hiểu dữ liệu và ra quyết định thông minh)

Điều này giúp giảm lãng phí điện năng, tăng hiệu quả vận hành và cải thiện trải nghiệm người dùng.
