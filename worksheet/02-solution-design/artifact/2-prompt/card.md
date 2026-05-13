---
artifact: 2 — Lớp chỉ dẫn AI
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp chỉ dẫn AI (Privacy Guardrails)

**Tình huống xử lý**: T-02 (Rò rỉ dữ liệu khi Export/Share)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Thiết lập các quy tắc cứng trong System Prompt (System Instructions) để tạo thành một "chốt chặn mềm" (Soft Guardrail). AI sẽ được chỉ định rõ ranh giới giữa việc "tổng hợp dữ liệu" và "liệt kê dữ liệu thô", đồng thời được cung cấp các kịch bản mẫu (few-shot) để biết cách từ chối khi người dùng cố tình ép buộc tiết lộ thông tin nhạy cảm.

---

## 2. Vì sao sửa ở lớp chỉ dẫn AI?

- AI LLM theo mặc định có xu hướng chiều theo ý người dùng (sycophancy). Nếu user ép liệt kê chi tiết, LLM dễ dàng vi phạm nguyên tắc bảo mật.
- Cần có luật rõ: khi nào được tổng hợp, khi nào phải từ chối việc liệt kê thông tin định danh (PII).
- Sửa bằng prompt là phương pháp can thiệp nhanh, linh hoạt để xử lý các câu lệnh (user prompt) biến hóa đa dạng.

**Hành động phòng vệ chính**:

- [x] Ngăn câu trả lời sai ngay từ đầu (bằng System Rules)
- [ ] Bắt buộc nêu nguồn khi nói về thông tin quan trọng
- [x] Từ chối trả lời khi thiếu căn cứ (hoặc khi bị ép vi phạm Privacy)
- [ ] Chuyển người thật khi vượt phạm vi

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo cần có:
- Luật chính (System Prompt) cho AI về Data Privacy.
- Mẫu câu từ chối khi user yêu cầu liệt kê chi tiết nhạy cảm.
- 3 ví dụ hỏi đáp kiểm tra (Bình thường, Ép buộc, Mơ hồ).

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**
- AI từ chối quá mức (Over-refusal), ngay cả khi user hỏi những chi tiết không thực sự nhạy cảm (vd: "Tháng này tôi mua bao nhiêu ly cafe?").

**Nhóm giảm vấn đề đó bằng cách nào?**
- Liệt kê cụ thể các loại dữ liệu được định nghĩa là "nhạy cảm" (Tên riêng, Số điện thoại, ID tài khoản, thông tin y tế, trả nợ tín dụng đen) trong prompt để AI không nhầm lẫn với các chi tiêu tiêu dùng bình thường.

---

## 5. Checklist trước khi nộp

- [x] Luật viết đủ cụ thể để AI làm theo.
- [x] Có mẫu câu khi AI không có đủ thông tin (hoặc từ chối).
- [x] Có ví dụ cho tình huống dễ sai.
- [x] Có thử lại bằng tình huống trong Bài 1.
- [x] Không dùng prompt như cách duy nhất nếu lỗi nằm ở dữ liệu hoặc quy trình (Đã có Architecture layer hỗ trợ).

**Người phụ trách**: Lê Đức Thanh
