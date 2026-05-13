---
title: 00 — Bối cảnh sản phẩm của nhóm
section: Day 25 — dùng lại cho mọi cuộc trò chuyện với AI
format: Nhóm
time: Điền 5 phút đầu buổi
---

# 00-context.md — Bối cảnh sản phẩm của nhóm

Điền file này một lần ở đầu buổi. Sau đó, mỗi lần dùng AI, hãy đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.

Lý do: AI không tự nhớ bối cảnh giữa các cuộc trò chuyện. Nếu mỗi lần đưa bối cảnh khác nhau, câu trả lời cũng sẽ lệch.

---

## 1. Sản phẩm

- **Tên sản phẩm / bot**: MoneyMindAI
- **Sản phẩm giúp ai làm gì**: MoneyMindAI giúp người trẻ tự quản lý chi tiêu xem lại báo cáo chi tiêu cuối tháng, tổng hợp các nhóm chi tiêu lớn, phát hiện khoản bất thường và so sánh xu hướng tăng/giảm so với tháng trước.
- **Người dùng gặp sản phẩm ở đâu**: Ứng dụng quản lý chi tiêu cá nhân trên mobile app.
- **Giai đoạn hiện tại**: Ý tưởng/demo học tập.

---

## 2. Phạm vi

**AI được làm gì**

- Tổng hợp chi tiêu theo nhóm như ăn uống, đi lại, học tập, sức khỏe, nhà ở, chuyển khoản cá nhân và hỗ trợ gia đình.
- So sánh xu hướng chi tiêu giữa tháng hiện tại và tháng trước nếu dữ liệu đủ rõ.
- Đánh dấu giao dịch hoặc nhóm chi tiêu bất thường để user tự kiểm tra lại.
- Viết tóm tắt ngắn gọn ở mức category, không hiển thị chi tiết giao dịch nhạy cảm.

**AI không được làm gì**

- Không được hiển thị tên người nhận, số tài khoản, số điện thoại, nội dung chuyển khoản riêng tư hoặc thông tin có thể định danh người khác trong báo cáo tổng hợp.
- Không được lặp lại các nội dung nhạy cảm như trả nợ, khám bệnh, tiền thuốc, hỗ trợ người thân hoặc quan hệ gia đình nếu không cần thiết.
- Không được tư vấn đầu tư, vay nợ, cắt khoản chi quan trọng hoặc đưa kết luận tài chính chắc chắn thay user.
- Không được tự động xuất/chia sẻ báo cáo chứa raw transaction hoặc dữ liệu nhạy cảm.

**Vì sao có giới hạn này**

MoneyMindAI xử lý dữ liệu tài chính cá nhân và có thể chứa PII của user hoặc người liên quan trong giao dịch. Nếu AI đưa lại dữ liệu thô vào summary, user có thể bị lộ thông tin riêng tư, người khác trong giao dịch cũng bị ảnh hưởng dù không trực tiếp dùng app. Vì sản phẩm đang ở mức ý tưởng/demo học tập, dữ liệu và cơ chế bảo vệ chưa đủ để cho AI đưa ra lời khuyên tài chính chắc chắn hoặc chia sẻ báo cáo mặc định.

---

## 3. Người dùng

- **Là ai**: Người trẻ tự quản lý chi tiêu, có thể là sinh viên hoặc nhân viên văn phòng mới đi làm, quen dùng mobile app nhưng không nhất thiết có kiến thức tài chính chuyên sâu.
- **Họ hỏi AI khi nào**: Cuối tháng, khi muốn biết tiền đã đi đâu, nhóm nào chi nhiều, khoản nào tăng bất thường hoặc có gì cần kiểm tra lại.
- **Họ cần quyết định gì sau khi hỏi AI**: Có cần kiểm tra lại giao dịch nào không, tháng sau nên chú ý nhóm chi tiêu nào, và có khoản nào cần tự xác nhận lại category.
- **Khi nào họ dễ bị tổn thương / dễ hiểu sai**: Khi đang lo lắng về tiền bạc, đang vội, xem báo cáo ở nơi công cộng, chia sẻ màn hình với người khác, hoặc đọc summary như lời khuyên tài chính chắc chắn.
- **Họ thường tin AI đến mức nào**: Có thể tin khá nhanh nếu báo cáo trình bày tự tin; các kết luận quan trọng vẫn cần user tự kiểm tra lại hoặc xác nhận thủ công.

---

## 4. Bối cảnh ngành

- **Sự cố tương tự đã từng xảy ra**: Các hệ thống AI/chatbot có thể làm lộ dữ liệu nhạy cảm, bịa thông tin hoặc trình bày kết luận quá chắc chắn. Với sản phẩm tài chính cá nhân, rủi ro gần nhất là privacy/data leak trong báo cáo và export/share.
- **Quy định hoặc ràng buộc liên quan**: Cần bảo vệ dữ liệu cá nhân, giảm thu thập/hiển thị dữ liệu không cần thiết, mask thông tin định danh và cảnh báo rõ trước khi chia sẻ báo cáo có dữ liệu tài chính.
- **Nguồn chính thức nên ưu tiên**: Chính sách bảo vệ dữ liệu cá nhân, hướng dẫn bảo mật/riêng tư của sản phẩm tài chính, báo cáo từ cơ quan quản lý hoặc nguồn báo chí uy tín về sự cố rò rỉ dữ liệu/AI.

---

## 5. Ghi chú thêm

- Chủ đề lấy từ Day 24: Track 04 — Trợ lý ghi chú và tổng hợp chi tiêu.
- Flow chính: Flow C — Báo cáo chi tiêu cuối tháng.
- Rủi ro chính cần xử lý: C1 — Privacy / data leak.
- Layer chính: Input; layer phụ: UI.
- Dữ liệu đầu vào có thể gồm giao dịch nhập tay, ví điện tử, ngân hàng, nội dung chuyển khoản, tên người nhận, khoản y tế, khoản trả nợ, khoản hỗ trợ gia đình hoặc giao dịch cá nhân riêng tư.
- Output an toàn nên tổng hợp ở cấp category, mask chi tiết nhạy cảm và khuyến nghị user mở từng giao dịch trong chế độ riêng tư nếu cần kiểm tra.

---

## Cách dùng

```text
1. Mở công cụ AI phù hợp với bước đang làm.
2. Đưa toàn bộ nội dung file này vào đầu cuộc trò chuyện.
3. Chọn prompt tham khảo từ thư mục ../prompts/ và chỉnh lại nếu cần.
4. Đọc lại bản nháp AI tạo ra.
5. Sửa lại cho đúng bối cảnh nhóm.
6. Lưu kết quả vào đúng file trong worksheet/.
```

Ghi chú: nội dung trong `[...]` là chỗ cần điền. Sau khi điền xong, xóa dấu ngoặc nếu không cần giữ.
