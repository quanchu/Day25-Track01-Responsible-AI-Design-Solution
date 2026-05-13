---
artifact: 1 — Lớp giao diện
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp giao diện (Share-Safe Preview)

**Tình huống xử lý**: T-02 (Rò rỉ dữ liệu khi Export/Share)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Thêm màn hình trung gian **"Share-Safe Preview"** trước khi người dùng thực hiện chia sẻ báo cáo ra bên ngoài. Giao diện sẽ tự động ẩn (mask) các thông tin nhạy cảm và yêu cầu người dùng xác nhận bản tóm tắt an toàn thay vì chia sẻ dữ liệu thô.

---

## 2. Vì sao sửa ở lớp giao diện?

- Người dùng thường có thói quen chia sẻ nhanh mà không rà soát lại nội dung AI tạo ra.
- Giao diện cần đóng vai trò là "chốt chặn cuối" để người dùng nhìn thấy rõ thông tin gì sẽ bị lộ trước khi bấm nút gửi.
- Chế độ **Privacy-by-Default** trên giao diện giúp giảm thiểu sai sót vô ý của người dùng.

**Hành động phòng vệ chính**:

- [x] Thông báo rõ giới hạn
- [ ] Phát hiện dấu hiệu thiếu nguồn
- [x] Chuyển người thật khi cần (Nút Review riêng tư)
- [x] Giúp người dùng kiểm tra lại nguồn (Bản Preview đã mask)

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

**Định dạng demo**: ASCII UI Flow

**Thành phần cần có trong demo**:
- Màn hình chat với nút "Share Report".
- Màn hình Preview với dữ liệu đã được làm mờ (****).
- Hộp thoại cảnh báo rủi ro Privacy.
- Nút "Confirm Share" và "Cancel".

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**
- Làm tăng thêm 1 bước (friction) trong trải nghiệm người dùng, có thể gây khó chịu nếu người dùng muốn chia sẻ nhanh.

**Nhóm giảm vấn đề đó bằng cách nào?**
- Thiết kế Preview trực quan, ngắn gọn.
- Cho phép người dùng lưu cấu hình "Luôn ẩn thông tin nhạy cảm khi share" để lần sau không cần nhắc lại quá chi tiết.

---

## 5. Checklist trước khi nộp

- [x] Giải pháp gắn đúng với một rủi ro chính.
- [x] Demo nhìn vào là hiểu vấn đề được chặn ở đâu.
- [x] Có đủ trạng thái bình thường và trạng thái lỗi (Preview an toàn).
- [x] Có cách chuyển sang người thật khi AI không nên tự xử lý.
- [x] Câu chữ trong giao diện ngắn, không đổ hết trách nhiệm cho người dùng.

**Người phụ trách**: Chu Minh Quân
