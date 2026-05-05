# AI Modules

## 1. People Counting

### Mô tả
Sử dụng camera để đếm số lượng người trong phòng theo thời gian thực.

### Input
- Video stream từ camera

### Output
- people_count (số người)

### Phương pháp
- YOLO / MobileNet SSD

### Metric
- Accuracy (% đếm đúng)
- FPS (tốc độ xử lý)

---

## 2. Anomaly Detection

### Mô tả
Phát hiện các trường hợp sử dụng điện bất thường.

### Input
- estimated_power
- people_count

### Output
- is_anomaly (true/false)

### Phương pháp
- Z-score hoặc rule-based

### Ví dụ
- people_count = 0 nhưng điện cao → bất thường

### Metric
- Precision
- Recall