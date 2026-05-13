---
artifact: 1 — FINAL kế hoạch giải pháp
bai-tap: 2 — Thiết kế giải pháp
phase: Chọn rủi ro + chọn tầng + chọn demo + chốt 3 lớp giải pháp
time: 11:00-11:55
input: 00-context.md + 01-test-set-review/3-FINAL-test-set-eval-plan.md
nop-cuoi: Có — file cuối Bài 2
---

# 1 — FINAL: Kế hoạch giải pháp

File này ghi lại quyết định chính của Bài 2:

- Rủi ro nào được chọn.
- Vì sao rủi ro đó quan trọng.
- Nguyên nhân gốc là gì.
- Nhóm sẽ xây 3 lớp giải pháp nào.
- Mỗi lớp dùng demo gì.

Lý do cần 3 lớp: một giải pháp đơn lẻ dễ lọt lỗi. Với rủi ro nặng, nhóm cần nhiều lớp cùng đỡ: lớp này ngăn, lớp kia phát hiện, lớp khác khắc phục hoặc thông báo cho người dùng.

Ba lớp giải pháp nằm trong thư mục `artifact/`:

| Lớp | Thư mục | Vai trò |
|---|---|---|
| Giao diện | `artifact/1-uiux/` | Cảnh báo, dẫn nguồn, nút chuyển sang người thật |
| Chỉ dẫn AI | `artifact/2-prompt/` | Hỏi lại, từ chối, bắt buộc dẫn nguồn |
| Kiến trúc dữ liệu | `artifact/3-architecture/` | Tra cứu nguồn đúng, lưu tạm dữ liệu, xử lý khi thiếu nguồn, giám sát |

Ba lớp này bổ sung cho nhau. Nếu một lớp lọt lỗi, lớp khác vẫn có thể chặn hoặc giảm hại.

## Thông tin nhóm

- **Chủ đề**: Trợ lý Quản lý Tài chính Cá nhân (Track 04)
- **Thành viên**: Chu Minh Quân, Lê Đức Thanh
- **Ngày**: 2026-05-13

---

## Phần A — Chọn rủi ro và tầng giải pháp

### Rủi ro chính được chọn

- **ID tình huống**: T-02
- **Mô tả ngắn**: Khi user yêu cầu xuất hoặc chia sẻ báo cáo chi tiêu, AI có xu hướng trích dẫn nguyên văn dữ liệu giao dịch thô (raw transactions), gây rò rỉ thông tin định danh (PII) và nội dung nhạy cảm cho bên thứ ba.
- **Mức độ**: Nặng
- **Điểm rủi ro**: 25
- **Vì sao chọn tình huống này**: Đây là điểm yếu chí mạng của tính năng "Share" - tính năng cốt lõi của Flow C. Nếu lỗi xảy ra, thiệt hại không chỉ dừng lại ở người dùng mà còn ảnh hưởng đến người thân/đối tác của họ, vi phạm nghiêm trọng NĐ 13/2023.

### Tìm nguyên nhân gốc

Đừng chỉ mô tả lỗi. Hãy trả lời: vì sao lỗi xảy ra?

- [x] Thiếu nguồn dữ liệu đúng (Dữ liệu đưa vào AI chưa được ẩn danh hóa).
- [x] AI đoán khi không biết (Hoặc AI quá "nhiệt tình" liệt kê chi tiết để chứng minh tính chính xác).
- [x] Giao diện khiến người dùng tin quá mức (Thiếu bước preview an toàn trước khi bấm nút Share).
- [ ] Quy trình thiếu người duyệt hoặc thiếu bước chuyển sang người thật.
- [ ] Không có theo dõi sau khi ra mắt.
- [ ] Khác: [...]

### Bảng nối nguyên nhân với tầng sửa

| Nguyên nhân gốc | Tầng ưu tiên sửa | Lớp giải pháp liên quan |
|---|---|---|
| Dữ liệu thô đưa vào AI | Kiến trúc dữ liệu / PII Scrubber | `3-architecture` là chính |
| AI liệt kê chi tiết nhạy cảm | Chỉ dẫn hệ thống / Quy tắc Privacy | `2-prompt` là chính |
| Thiếu preview an toàn | Giao diện cảnh báo / Share-safe mode | `1-uiux` là chính |

Nguyên tắc: lỗi ở tầng nào, ưu tiên sửa ở tầng đó. Đừng chỉ thêm cảnh báo giao diện nếu nguyên nhân gốc là thiếu nguồn dữ liệu hoặc AI đoán khi không biết.

### 4 hành động phòng vệ

Mỗi lớp nên làm ít nhất một việc:

- **Ngăn**: giảm khả năng lỗi xảy ra từ đầu.
- **Phát hiện**: nhận ra lỗi hoặc tín hiệu nguy hiểm.
- **Khắc phục**: chuyển sang người thật, dùng câu trả lời dự phòng, hoặc dừng trả lời.
- **Thông báo**: giúp người dùng hiểu mức tin cậy và rủi ro.

Gợi ý theo mức rủi ro:

| Mức rủi ro | Nên có |
|---|---|
| Nặng | Ít nhất 3 hành động |

### Kết luận Phần A

**Nguyên nhân gốc**: Hệ thống chưa có cơ chế ẩn danh hóa dữ liệu trước khi nạp vào LLM, đồng thời Prompt chưa đủ mạnh để ngăn LLM "bê" nguyên xi data vào báo cáo xuất ra.

**Tầng chính cần sửa**: Kiến trúc dữ liệu (PII Scrubber) & Chỉ dẫn AI (Privacy Guardrails).

**Vì sao cần 3 lớp giải pháp**:

- Lớp giao diện: Giúp người dùng kiểm soát bản báo cáo trước khi chia sẻ (Thông báo & Khắc phục).
- Lớp chỉ dẫn AI: Chốt chặn mềm để AI không bao giờ liệt kê chi tiết PII ngay cả khi user ép buộc (Ngăn).
- Lớp kiến trúc dữ liệu: Chốt chặn cứng đảm bảo AI không bao giờ nhìn thấy dữ liệu thô nhạy cảm (Phát hiện & Ngăn).

---

## Phần B — Chọn định dạng demo

Mỗi lớp cần một bản demo. Demo giúp biến ý tưởng thành thứ trực quan để nhóm khác xem, kiểm tra và phản biện.

| Lớp | Thư mục | Định dạng demo chọn | Thời gian dự kiến |
|---|---|---|---|
| Giao diện | `1-uiux` | ASCII UI Flow | 10 phút |
| Chỉ dẫn AI | `2-prompt` | Markdown Prompt + Example | 10 phút |
| Kiến trúc dữ liệu | `3-architecture` | Mermaid Sequence Diagram | 10 phút |

**Lý do chọn demo**

- Giao diện: Thể hiện rõ nút bật "Chế độ chia sẻ an toàn".
- Chỉ dẫn AI: Dễ dàng thử nghiệm độ tuân thủ của AI.
- Kiến trúc dữ liệu: Minh họa rõ vị trí của bộ lọc PII Scrubber trong luồng dữ liệu.

---

## Phần C — Ba lớp giải pháp

Ghi tóm tắt ở đây. Chi tiết nằm trong `card.md` và `demo.*` của từng thư mục.

### Lớp 1 — Giao diện (`artifact/1-uiux/`)

- **Cách tiếp cận**: Thêm màn hình "Share-Safe Preview". Khi user chọn chia sẻ, app tự động hiển thị bản báo cáo đã mask tên người nhận và nội dung nhạy cảm.
- **Hành động phòng vệ bao phủ**: Thông báo / Khắc phục
- **Demo**: ASCII UI
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/1-uiux/card.md`
- `artifact/1-uiux/demo.md`

### Lớp 2 — Chỉ dẫn AI (`artifact/2-prompt/`)

- **Cách tiếp cận**: Thiết lập System Instruction nghiêm ngặt: "Tuyệt đối không liệt kê Tên, Số tài khoản, hoặc nội dung giao dịch nhạy cảm". Cung cấp các Negative Examples về rò rỉ dữ liệu.
- **Hành động phòng vệ bao phủ**: Ngăn
- **Demo**: Markdown Prompt
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/2-prompt/card.md`
- `artifact/2-prompt/demo.md`

### Lớp 3 — Kiến trúc dữ liệu (`artifact/3-architecture/`)

- **Cách tiếp cận**: Triển khai service PII Scrubber sử dụng NLP để phát hiện thực thể (NER) và Regex để ẩn danh hóa dữ liệu trước khi đẩy vào Vector DB hoặc Context Window.
- **Hành động phòng vệ bao phủ**: Ngăn / Phát hiện
- **Demo**: Mermaid Diagram
- **Trạng thái**: Đang làm

Link chi tiết:

- `artifact/3-architecture/card.md`
- `artifact/3-architecture/demo.md`

---

## Tổng kiểm tra

| Câu hỏi | Trả lời |
|---|---|
| Rủi ro chính đã chọn là gì? | T-02 (Rò rỉ dữ liệu khi Export/Share) |
| Nguyên nhân gốc là gì? | Dữ liệu nhạy cảm chưa được lọc trước khi nạp vào AI. |
| 3 lớp giải pháp đã đủ chưa? | Giao diện: Đang làm / Chỉ dẫn AI: Đang làm / Kiến trúc: Đang làm |
| 4 hành động đã bao phủ chưa? | Ngăn: Có / Phát hiện: Có / Khắc phục: Có / Thông báo: Có |
| Nhóm khác đã góp ý chưa? | [Đang chờ] |
| Nhóm đã sửa gì sau phản biện? | [Đang chờ] |
