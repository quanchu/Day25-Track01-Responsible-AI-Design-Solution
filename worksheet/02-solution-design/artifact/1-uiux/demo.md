---
artifact: 1 — Demo giao diện
format: phác thảo / ASCII UI
---

# demo.md — Demo giao diện (Share-Safe Preview)

---

## 1. Màn hình chính & Luồng xử lý

```text
[ MÀN HÌNH CHAT TỔNG HỢP ]
---------------------------------------
AI: Tháng này bạn chi tiêu 15.0tr. 
    Khoản lớn nhất là Ăn uống (5tr).
    Có 1 khoản bất thường 2tr cần lưu ý.
---------------------------------------
[ Share Report ] <--- User bấm vào đây
      |
      v
[ MÀN HÌNH PREVIEW CHIA SẺ (SHARE-SAFE) ]
---------------------------------------
! CẢNH BÁO BẢO MẬT !
Bạn đang chuẩn bị chia sẻ báo cáo này.
Chúng tôi đã tự động ẩn các chi tiết nhạy cảm.
---------------------------------------
NỘI DUNG CHIA SẺ:
- Tổng chi: 15,000,000đ
- Ăn uống: 5,000,000đ
- Sức khỏe: 1,200,000đ (Chi tiết: ****)
- Trả nợ: 2,000,000đ (Người nhận: ****)
---------------------------------------
[X] Tôi đã rà soát và đồng ý chia sẻ.
---------------------------------------
   [ HỦY ]      [ XÁC NHẬN CHIA SẺ ]
```

---

## 2. Trạng thái cần minh họa

| Trạng thái | Người dùng thấy gì? | Người dùng làm gì tiếp? |
|---|---|---|
| Có nguồn xác minh | Nhãn "Dữ liệu từ sao kê chính thức" | Yên tâm chia sẻ |
| Chế độ Share-safe | Các trường PII (Tên, Số TK) hiển thị dạng `****` | Rà soát nội dung tóm tắt |
| Cảnh báo rủi ro | Popup cảnh báo về Nghị định 13/2023 | Tích chọn xác nhận trách nhiệm |
| Hủy chia sẻ | Nút [ Hủy ] | Quay lại màn hình chat để chỉnh sửa |

---

## 3. Ghi chú cho từng thành phần

- **Safety Banner**: Nằm ở đầu màn hình Preview, màu vàng cam để gây chú ý mà không gây hoảng sợ.
- **Masked Content**: Tự động thay thế nội dung trường `description` chứa từ khóa nhạy cảm (nợ, bệnh, tên riêng) thành dấu sao.
- **Confirmation Checkbox**: Buộc người dùng thực hiện một hành động chủ động để kích hoạt nút Gửi.

---

## 4. Kiểm tra nhanh

- [x] Nhìn vào demo là hiểu rủi ro rò rỉ dữ liệu được chặn ở bước Preview.
- [x] Có trạng thái khi AI đã ẩn thông tin nhạy cảm.
- [x] Có cơ chế xác nhận trách nhiệm chia sẻ.
- [x] Câu chữ đủ ngắn để đặt trên màn hình mobile.
