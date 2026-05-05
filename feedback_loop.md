# Feedback Loop

## Luồng hệ thống

Camera → AI → Gateway → Backend → AI Services → Decision → Device

---

## Logic quyết định

IF anomaly == true:
    gửi cảnh báo
    tạm dừng điều khiển tự động

ELSE:
    IF people_count == 0:
        tắt điều hòa và đèn
    ELSE:
        duy trì trạng thái hoạt động

---

## Cơ chế an toàn

- Không tự động tắt nếu còn người
- Có cảnh báo trước khi hành động
- Cho phép người dùng override