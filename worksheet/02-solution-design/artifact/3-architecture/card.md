---
artifact: 3 — Lớp kiến trúc dữ liệu
bai-tap: 2 — Thiết kế giải pháp
demo: ./demo.md
---

# card.md — Lớp kiến trúc dữ liệu (PII Scrubber)

**Tình huống xử lý**: T-02 (Rò rỉ dữ liệu khi Export/Share)  
Xem `../../1-map-and-format.md` Phần A.

---

## 1. Giải pháp là gì?

Tích hợp một service trung gian gọi là **"PII Scrubber"** (sử dụng các công cụ NER - Named Entity Recognition hoặc Regex) nằm giữa Database và LLM. Dữ liệu giao dịch thô sẽ bị chặn lại ở lớp này để gỡ bỏ tên, số tài khoản, số điện thoại trước khi được gửi làm ngữ cảnh (context) cho AI.

---

## 2. Vì sao sửa ở lớp kiến trúc dữ liệu?

- Nguyên nhân gốc rễ (Root cause) của rò rỉ dữ liệu là do LLM nhìn thấy dữ liệu thô. Nếu LLM không thấy dữ liệu nhạy cảm, nó không thể làm lộ.
- Dựa dẫm hoàn toàn vào Prompt (Lớp 2) là không đủ an toàn, vì LLM có thể bị "jailbreak" hoặc hallucinate khi xử lý chuỗi văn bản dài.
- Data Minimization (chỉ cung cấp dữ liệu cần thiết) là nguyên tắc cốt lõi của Privacy by Design theo NĐ 13/2023.

**Hành động phòng vệ chính**:

- [x] Ngăn lỗi bằng nguồn dữ liệu đúng (Data Masking)
- [x] Phát hiện khi nguồn thiếu hoặc lỗi (Bắt các pattern nhạy cảm)
- [ ] Khắc phục bằng cách chuyển sang người thật
- [ ] Ghi lại lỗi để cải thiện sau

---

## 3. Demo nằm ở đâu?

**File demo**: [`demo.md`](./demo.md)

Demo cần có:
- Sơ đồ luồng dữ liệu (Mermaid) minh họa vị trí của PII Scrubber.
- Cấu trúc Data Payload trước và sau khi đi qua Scrubber.
- Giải thích cách hệ thống xử lý khi có lỗi xảy ra.

---

## 4. Tác dụng phụ

**Có thể gây vấn đề gì?**
- Hệ thống bị chậm (latency) do tốn thời gian xử lý NLP/Regex ở lớp Scrubber.
- PII Scrubber có thể lọc nhầm (false positive), ví dụ lọc nhầm tên quán ăn có chứa tên người thành dấu `***`, làm giảm chất lượng báo cáo.

**Nhóm giảm vấn đề đó bằng cách nào?**
- Chỉ chạy NER cường độ cao trên các nhóm Category nhạy cảm (Chuyển khoản cá nhân, Y tế).
- Giữ lại ID giao dịch ẩn trong hệ thống để UI có thể map ngược lại dữ liệu gốc nếu người dùng muốn xem chi tiết (trong môi trường private).

---

## 5. Checklist trước khi nộp

- [x] Sơ đồ cho thấy dữ liệu đi từ đâu đến đâu.
- [x] Có bước kiểm tra nguồn trước khi AI trả lời.
- [x] Có cách xử lý khi không có dữ liệu.
- [x] Có cách chuyển sang người thật với tình huống rủi ro cao (không áp dụng trực tiếp cho lớp PII, nhưng liên kết với UI).
- [x] Có cách biết lỗi này có đang lặp lại không.

**Người phụ trách**: Chu Minh Quân
