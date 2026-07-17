# Workbook Buổi 01 - Workspace & Orchestrator Agent

> Tài liệu để bạn tự làm theo trong lớp và làm lại ở nhà. Làm tới đâu, đánh dấu tới đó.

## Buổi này bạn sẽ làm được gì

Kết thúc buổi, bạn có một trợ lý AI của riêng mình, đã biết bạn là ai và làm nghề gì, gọi ra là chạy đúng ngay, không cần kể lại từ đầu mỗi lần. Cụ thể:

1. Hiểu "agent" khác "chat thường" ở đâu.
2. Dựng xong bộ khung AI Workspace: cái tủ để năm buổi sau lắp thêm agent.
3. Tạo được agent đầu tiên tên Orchestrator, agent "trưởng nhóm" nhận yêu cầu tổng rồi chia việc.
4. Điền được bối cảnh công việc thật của mình vào agent.
5. Chạy thử agent với một việc thật và đọc được kế hoạch nó trả về.

## Vài từ cần hiểu trước

- **Chat thường:** mỗi lần mở ra là tờ giấy trắng. Bạn phải kể lại bạn là ai, muốn gì. Đóng lại là mất hết.
- **Agent:** một ô nhớ đã ghi sẵn vai trò, quy tắc, bối cảnh, cách trình bày. Giống một nhân viên đã được đào tạo, gọi ra là làm đúng ngay.
- **Workspace:** cái tủ chứa các agent. Buổi 1 dựng tủ, các buổi sau bỏ thêm agent vào.
- **Orchestrator:** trưởng nhóm. Không tự ôm hết việc, mà chia yêu cầu của bạn thành các bước và chỉ rõ phần nào nên đưa cho agent chuyên môn nào.
- **System prompt:** bản mô tả công việc bạn dán vào agent lúc tạo. Một bản tốt có 5 phần: vai trò, nhiệm vụ, quy tắc, bối cảnh, định dạng đầu ra.

---

## Chuẩn bị

Trước khi bắt đầu, kiểm tra bạn đã có:

- [ ] Tài khoản AI đã đăng nhập (bản có tính năng tạo project/custom agent và upload file, theo hướng dẫn CES gửi).
- [ ] Máy tính, trình duyệt web, Zoom đã mở, mic hoạt động.
- [ ] File `system-prompts/01-orchestrator-agent.md` mở sẵn để lát copy.
- [ ] 2-3 câu mô tả công việc thật của bạn (dùng ở phần bối cảnh). Nếu chưa nghĩ ra, để trống rồi điền sau.

---

## Hướng dẫn thao tác từng bước

Làm lần lượt. Công cụ AI mỗi loại đặt nút hơi khác nhau; nếu không thấy đúng chữ, tìm nút có nghĩa tương đương và hỏi giảng viên.

**Bước 1. Mở khu vực tạo project / custom agent.**
Trong công cụ AI, tìm mục cho phép tạo "project" hoặc "custom agent" (chỗ này khác với ô chat bình thường). Giảng viên sẽ chỉ vị trí cụ thể trên công cụ lớp đang dùng.

**Bước 2. Tạo workspace và đặt tên.**
Tạo một project/workspace mới. Đặt tên rõ ràng, ví dụ: `AI Workspace - [Tên bạn]`. Đặt tên gọn và dễ nhận để buổi sau bạn tìm lại nhanh.

**Bước 3. Tạo agent đầu tiên, đặt tên Orchestrator.**
Bên trong workspace, tạo một agent mới. Đặt tên: `Orchestrator`.

**Bước 4. Lấy system prompt.**
Mở file `system-prompts/01-orchestrator-agent.md`. Bôi chọn toàn bộ nội dung trong khối mã (đoạn bắt đầu bằng "Bạn là Orchestrator..."), copy lại. Bản để copy cũng có sẵn ở cuối workbook này.

**Bước 5. Dán vào agent.**
Dán nội dung vừa copy vào ô "Instructions" hoặc "System prompt" của agent. Kiểm tra không bị thiếu đoạn.

**Bước 6. Nhận diện 5 phần của system prompt.**
Nhìn vào nội dung vừa dán, tìm cho ra 5 phần: vai trò (dòng đầu), nhiệm vụ, quy tắc, bối cảnh của tôi, định dạng đầu ra. Đây là khung của mọi agent bạn sẽ làm trong khóa.

**Bước 7. Sửa dòng vai trò.**
Sửa dòng đầu tiên cho đúng bạn: thay `[Họ tên]`, `[chức danh]`, `[công ty/lĩnh vực]` bằng thông tin của bạn.

**Bước 8. Điền phần "Bối cảnh của tôi".**
Điền 4 mục ở cuối system prompt bằng thông tin thật:
- Công việc chính của bạn.
- Loại việc bạn lặp lại nhiều nhất.
- Định dạng đầu ra bạn hay cần (báo cáo, email, slide, bảng...).
- Văn phong (trang trọng, thân thiện, ngắn gọn...).

Điền càng chi tiết, agent điều phối càng đúng ý bạn.

**Bước 9. Lưu agent.**

**Bước 10. Chạy thử.**
Gõ cho Orchestrator một yêu cầu công việc thật, ví dụ: `Tuần này tôi phải [việc thật của bạn]. Giúp tôi lên kế hoạch làm.` Đọc phần nó trả về: nó chia việc thành các bước, chỉ rõ bước nào giao agent nào, và hỏi lại bạn tối đa 3 câu chứ không làm bừa.

**Bước 11. Chụp màn hình.**
Chụp lại phần Orchestrator trả về. Đây là bằng chứng hoàn thành buổi, nộp qua Zalo lớp.

---

## Ô ghi chú của bạn

Điền vào để nhớ và để tinh chỉnh sau này.

**Tên workspace tôi đặt:**
> ....................................................

**Bối cảnh tôi đã điền (chép lại ngắn gọn):**

| Mục | Nội dung tôi điền |
|---|---|
| Công việc chính | |
| Việc lặp nhiều nhất | |
| Định dạng hay cần | |
| Văn phong | |

**Yêu cầu tôi dùng để test Orchestrator:**
> ....................................................

**Orchestrator chia việc thành mấy bước? Bước nào nó định giao cho agent khác?**
> ....................................................

**Một chỗ nó làm tốt / một chỗ chưa hợp ý:**
> ....................................................

---

## System prompt để copy

Dán nguyên khối dưới vào ô Instructions/System prompt của agent. Sau đó sửa phần trong `[ngoặc vuông]` cho đúng bạn. Bản gốc và ghi chú chi tiết ở `system-prompts/01-orchestrator-agent.md`.

```
Bạn là Orchestrator, trợ lý điều phối công việc của [Họ tên], làm [chức danh] tại [công ty/lĩnh vực].

NHIỆM VỤ
Khi tôi giao một yêu cầu, bạn KHÔNG tự làm hết ngay. Bạn:
1. Làm rõ yêu cầu: nếu thiếu thông tin, hỏi tôi tối đa 3 câu quan trọng nhất trước khi làm.
2. Phân rã việc thành các bước, chỉ rõ bước nào nên giao cho agent nào:
   - Document Agent: đọc, tóm tắt, trích ý từ tài liệu dài.
   - Data Analysis Agent: phân tích Excel/CSV, tính toán, tìm xu hướng, gợi ý biểu đồ.
   - Report Agent: soạn báo cáo, đề xuất, email, dàn ý slide.
   - Deep Research Agent: nghiên cứu thị trường, đối thủ, tổng hợp nhiều nguồn.
3. Trình bày kế hoạch dạng danh sách bước, đánh số, kèm đầu ra mong đợi mỗi bước.
4. Nếu tôi xác nhận, hướng dẫn tôi copy nội dung sang đúng agent, hoặc tự làm bước đó nếu nằm trong khả năng của bạn.
5. Cuối cùng tổng hợp kết quả các bước thành một đầu ra gọn cho tôi.

QUY TẮC
- Trả lời bằng tiếng Việt, rõ ràng, không dùng thuật ngữ khó khi không cần.
- Ưu tiên hành động: đưa 1 phương án nên làm, kèm 1 lựa chọn thay thế nếu có.
- Luôn kết thúc bằng câu hỏi: "Bạn muốn tôi làm bước nào tiếp theo?"
- Không bịa số liệu. Thiếu dữ liệu thì nói rõ cần bổ sung gì.

BỐI CẢNH CỦA TÔI (điền để agent hiểu công việc)
- Công việc chính: [...]
- Loại việc lặp lại nhiều nhất: [...]
- Định dạng đầu ra tôi hay cần: [báo cáo / email / slide / bảng ...]
- Văn phong: [trang trọng / thân thiện / ngắn gọn ...]
```

---

## Bài tập

**Tại lớp:**
Dựng xong workspace và Orchestrator, điền bối cảnh thật, chạy thử với một việc thật, chụp màn hình phần trả về và nộp qua Zalo.

**Về nhà:**
1. Dùng Orchestrator cho ít nhất 2 việc thật khác nhau trong tuần. Ghi lại 1 chỗ nó điều phối tốt và 1 chỗ chưa hợp ý.
2. Tinh chỉnh phần bối cảnh hoặc quy tắc trong system prompt cho hợp mình hơn. Ghi lại bạn đã sửa gì.
3. Chọn sẵn 1 tài liệu dài thật (PDF/Word vài chục trang) để dùng cho buổi 2 (Document Agent).

---

## Checklist tự đánh giá: buổi này tôi đã làm được

- [ ] Tôi nói được agent khác chat thường ở đâu.
- [ ] Tôi đã tạo workspace cá nhân và đặt tên rõ ràng.
- [ ] Tôi đã tạo agent Orchestrator và dán đủ system prompt.
- [ ] Tôi chỉ ra được 5 phần của system prompt.
- [ ] Tôi đã điền phần bối cảnh bằng thông tin thật của mình.
- [ ] Tôi đã chạy thử với một việc thật và có ảnh chụp phần Orchestrator trả về.
- [ ] Tôi đã nộp ảnh chụp qua Zalo lớp.
- [ ] Tôi đã chuẩn bị 1 tài liệu dài để mang tới buổi 2.
