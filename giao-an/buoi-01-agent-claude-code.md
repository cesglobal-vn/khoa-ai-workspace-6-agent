# Giáo án Buổi 01: Agent là gì và làm quen Claude Code

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

## Thông tin buổi
- **Buổi:** 01 / 6
- **Khái niệm chính:** Agent
- **Loại:** Nền tảng (buổi nền, quan trọng nhất, làm quen công cụ)
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đăng nhập tài khoản CES cấp
- [ ] Tải và mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-01/du-an-mau/`
- [ ] File demo cần dùng: `ghi-chu-cong-viec.md`, `danh-sach-khach-hang.md`
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/claude-md-mau.md` (mở sẵn để dán khi demo)
- [ ] Test trước 1 lượt: mở thư mục demo, cho agent đọc thư mục, tạo `todo.md`, thêm 1 khách hàng
- [ ] Chuẩn bị Zalo lớp để gửi link tải bộ demo cho học viên chưa có
- [ ] Nhắc học viên mang sẵn 1 thư mục công việc thật (1 tài liệu, 1 file dữ liệu, vài ghi chú)

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu Claude Code trên Claude Desktop là gì và khác chat AI thường ở đâu.
2. Mở được Claude Code, chọn đúng thư mục dự án để agent làm việc.
3. Tạo được file `CLAUDE.md` làm bộ nhớ và chỉ dẫn cho agent.
4. Ra lệnh cho agent đọc cả thư mục và tóm tắt "tôi đang có gì".
5. Ra lệnh cho agent tạo file mới và sửa file có sẵn, biết cách xác nhận khi agent xin sửa.

## Kết quả cầm về (deliverable)
- 1 thư mục dự án của riêng học viên, có file `CLAUDE.md` đã điền thông tin.
- 1 file `todo.md` do agent tạo từ ghi chú công việc.
- 1 lần đọc thư mục thành công: agent tóm tắt đúng nội dung file demo.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Chat AI thường:** bạn gõ câu hỏi, AI trả lời bằng chữ trong khung chat. AI không đụng vào file trong máy, không nhớ bối cảnh sau khi đóng.
- **Agent (Claude Code):** một trợ lý AI biết tự làm nhiều bước liên tiếp, đọc và sửa được file thật trong thư mục bạn chỉ, và nhớ bối cảnh dự án. Bạn ra lệnh bằng tiếng Việt, agent tự thao tác.
- **Thư mục dự án:** một thư mục trên máy bạn chọn cho agent làm việc. Agent chỉ đọc và sửa trong thư mục này, không lục lung tung nơi khác.
- **CLAUDE.md:** một file văn bản đặt ở gốc thư mục dự án. Agent tự đọc file này mỗi lần mở thư mục, nên bạn không phải dặn lại "tôi là ai, làm nghề gì, muốn làm việc kiểu nào" mỗi lần. Đây là bộ nhớ dài hạn của agent về bạn.

---

## Timeline chi tiết (theo phút)

Mỗi mục demo/thực hành trình bày theo khối 4 dòng dưới đây.

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn GV:** "Chào cả lớp. Đây là buổi đầu tiên và cũng là buổi nền quan trọng nhất của khóa. Học xong 6 buổi, cả lớp sẽ có một đội trợ lý AI làm việc thật trên máy mình. Nhưng hôm nay ta đi từ viên gạch đầu tiên: hiểu agent là gì, và tự tay ra lệnh cho nó xử lý file công việc của mình."
- Điểm danh, kiểm tra ai đã cài Claude Desktop và đăng nhập được.
- Giới thiệu bản đồ 6 buổi: Agent (hôm nay), rồi Skill, MCP, Subagent, Agent Team, Capstone. Mỗi buổi là nền cho buổi sau.
- Nêu mục tiêu buổi hôm nay: cuối buổi ai cũng có thư mục dự án + CLAUDE.md, và đã cho agent đọc, tạo, sửa file.
- **Câu hỏi tương tác:** "Cả lớp đang dùng AI kiểu nào? Mở chat gõ câu hỏi, hay đã từng cho AI đụng vào file trong máy?"

### [00:15-00:35] Lý thuyết ngắn: Agent khác chat thế nào + vai trò CLAUDE.md
- **Lời dẫn GV:** "Trước khi thao tác, ta cần phân biệt rõ hai thứ nghe giống nhau nhưng khác hẳn: chat AI thường và agent."
- **Nội dung 1: Chat thường vs Agent.** Vẽ lên bảng 2 cột:
  - Chat thường: gõ câu hỏi, nhận chữ trả lời, tự copy paste, AI không đụng file, quên hết khi đóng.
  - Agent (Claude Code): ra lệnh, agent tự làm nhiều bước, đọc và sửa file thật trong thư mục, nhớ bối cảnh nhờ CLAUDE.md.
- **Nội dung 2: Ba điểm làm agent mạnh hơn.**
  1. Tự làm nhiều bước: một lệnh, agent đọc nhiều file rồi tổng hợp, không cần bạn dắt từng bước.
  2. Đụng file thật: agent tạo file mới, sửa file có sẵn ngay trong thư mục của bạn.
  3. Nhớ bối cảnh: nhờ file CLAUDE.md, agent biết bạn là ai và muốn làm việc kiểu gì mà không phải dặn lại.
- **Nội dung 3: CLAUDE.md là gì.** Đây là "trí nhớ dài hạn" của agent. Một file văn bản ghi: tôi là ai, thư mục này để làm gì, quy tắc khi làm việc với tôi. Càng ghi rõ, agent càng làm đúng ngay lần đầu.
- **Câu hỏi tương tác:** "Theo cả lớp, vì sao agent tự sửa được file lại vừa tiện vừa hơi đáng lo? Ta sẽ thấy cách agent xin phép trước khi sửa ở phần demo."

### [00:35-01:00] Demo giảng viên
> GV làm mẫu trên màn hình chia sẻ, học viên xem trước, chưa gõ theo. Trình bày mỗi bước theo mẫu 4 dòng.

**Bước 1: Mở Claude Code và chọn thư mục dự án demo**
- **Lời dẫn GV:** "Đầu tiên tôi mở Claude Code trong Claude Desktop, rồi trỏ nó vào thư mục demo. Đây là bước quan trọng nhất: agent chỉ làm việc trong thư mục ta chọn."
- **Prompt gõ vào Claude Code:**
  ```
  Thư mục này đang có những file gì? Liệt kê tên file và cho tôi biết mỗi file nói về cái gì.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/du-an-mau/` (cả thư mục, gồm `ghi-chu-cong-viec.md` và `danh-sach-khach-hang.md`)
- **Kết quả mong đợi:** Agent liệt kê đúng 2 file: `ghi-chu-cong-viec.md` (ghi chú việc cần làm tuần này) và `danh-sach-khach-hang.md` (bảng 5 khách hàng). Nhấn cho lớp thấy: agent tự đọc file, không cần ta dán nội dung vào.

**Bước 2: Cho agent đọc cả thư mục và tóm tắt "tôi đang có gì"**
- **Lời dẫn GV:** "Giờ tôi bảo agent đọc hết và tóm tắt tình hình. Đây là điều chat thường không làm được: nó tự mở từng file rồi gộp lại."
- **Prompt gõ vào Claude Code:**
  ```
  Đọc tất cả file trong thư mục này và tóm tắt cho tôi: tôi đang có bao nhiêu việc cần làm, bao nhiêu khách hàng, và việc nào gấp nhất.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/du-an-mau/ghi-chu-cong-viec.md` và `tai-lieu-phat/demo/buoi-01/du-an-mau/danh-sach-khach-hang.md`
- **Kết quả mong đợi:** Agent tóm tắt: **5 việc cần làm** (gọi khách Minh Long, soạn báo cáo doanh thu tháng trước thứ Sáu, chuẩn bị tài liệu họp thứ Tư, trả lời email đối tác Hải Nam, cập nhật danh sách khách hàng mới); **5 khách hàng** trong danh sách; việc gấp nhất là báo cáo doanh thu (hạn thứ Sáu) và họp thứ Tư có sếp dự.

**Bước 3: Cho agent tạo file todo.md từ ghi chú công việc**
- **Lời dẫn GV:** "Tóm tắt xong, tôi nhờ agent biến ghi chú lộn xộn thành một danh sách việc gọn gàng, lưu thành file mới."
- **Prompt gõ vào Claude Code:**
  ```
  Từ file ghi-chu-cong-viec.md, tạo cho tôi một file mới tên todo.md gồm danh sách các việc cần làm dạng checkbox, việc nào có hạn thì ghi rõ hạn.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/du-an-mau/ghi-chu-cong-viec.md` (nguồn), tạo mới `tai-lieu-phat/demo/buoi-01/du-an-mau/todo.md`
- **Kết quả mong đợi:** Agent tạo file `todo.md` mới với 5 dòng checkbox, ví dụ `- [ ] Gọi lại khách Minh Long về báo giá`, `- [ ] Soạn báo cáo doanh thu tháng (hạn: thứ Sáu)`. GV mở file mới ra cho lớp thấy nó có thật trong thư mục.

**Bước 4: Cho agent thêm 1 khách hàng vào danh sách (sửa file có sẵn, agent xin xác nhận)**
- **Lời dẫn GV:** "Bây giờ tôi nhờ agent sửa một file đang có. Chú ý: agent sẽ báo trước nó định sửa gì và chờ tôi đồng ý. Đây là cơ chế an toàn."
- **Prompt gõ vào Claude Code:**
  ```
  Thêm một khách hàng mới vào file danh-sach-khach-hang.md: tên "Công ty Bình Minh", ngành "Giáo dục", trạng thái "Tiềm năng", ghi chú "Mới gọi điện hỏi thông tin".
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/du-an-mau/danh-sach-khach-hang.md`
- **Kết quả mong đợi:** Agent cho xem trước dòng sắp thêm và xin xác nhận. GV bấm đồng ý. File có thêm dòng thứ 6: `| Công ty Bình Minh | Giáo dục | Tiềm năng | Mới gọi điện hỏi thông tin |`. Danh sách giờ có 6 khách. GV nhấn: nếu không đồng ý thì gõ "không" và agent dừng.

**Bước 5: Tạo file CLAUDE.md từ mẫu**
- **Lời dẫn GV:** "Cuối phần demo, tôi tạo bộ nhớ cho agent. Có file này rồi, lần sau mở thư mục agent tự biết tôi là ai, không phải dặn lại."
- **Prompt gõ vào Claude Code:**
  ```
  Tạo cho tôi một file CLAUDE.md ở thư mục này. Tôi tên Trần Văn Minh, làm nhân viên kinh doanh phần mềm. Thư mục này để tôi quản lý việc cần làm và danh sách khách hàng. Quy tắc: trả lời tiếng Việt ngắn gọn, trước khi sửa hay xóa file phải hỏi tôi, không bịa số liệu, văn bản gửi đi không dùng emoji.
  ```
- **File demo:** mẫu tham chiếu `mau-cau-hinh/claude-md-mau.md`; tạo mới `tai-lieu-phat/demo/buoi-01/du-an-mau/CLAUDE.md`
- **Kết quả mong đợi:** Agent tạo file `CLAUDE.md` có các mục: Tôi là ai (Trần Văn Minh, nhân viên kinh doanh phần mềm), Thư mục này để làm gì, Quy tắc khi làm việc. GV mở file cho lớp xem và nói: buổi sau (skill, subagent) đều dựa trên thói quen tổ chức thư mục và file này.

### [01:00-01:30] Thực hành 1 (file demo chung)
- **Lời dẫn GV:** "Đến lượt cả lớp. Mở Claude Code, trỏ vào đúng thư mục demo giống tôi vừa làm, rồi chạy lần lượt các lệnh. Ai kẹt bước nào giơ tay, tôi và trợ giảng qua ngay."
- **Đề bài:** Mỗi học viên tự làm lại 3 việc trên thư mục demo chung: (1) cho agent đọc thư mục và tóm tắt, (2) tạo file `todo.md`, (3) thêm 1 khách hàng vào danh sách.
- **Prompt gợi ý cho học viên (chạy lần lượt):**
  ```
  1. Đọc tất cả file trong thư mục này và tóm tắt: tôi có bao nhiêu việc cần làm và bao nhiêu khách hàng.

  2. Tạo file todo.md từ ghi-chu-cong-viec.md, dạng checkbox, việc nào có hạn thì ghi rõ.

  3. Thêm một khách hàng mới vào danh-sach-khach-hang.md: tên "Công ty Sao Mai", ngành "Logistics", trạng thái "Tiềm năng", ghi chú "Gặp tại hội chợ".
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/du-an-mau/ghi-chu-cong-viec.md`, `tai-lieu-phat/demo/buoi-01/du-an-mau/danh-sach-khach-hang.md`
- **Kết quả mong đợi:** Mỗi học viên có: (1) một đoạn tóm tắt nhận ra 5 việc và 5 khách hàng, (2) file `todo.md` mới với 5 checkbox, (3) file danh sách khách hàng có thêm dòng "Công ty Sao Mai" thành 6 khách, sau khi bấm xác nhận cho agent sửa.

### [01:30-01:40] Nghỉ giải lao
- GV nhắc: ai chưa xong Thực hành 1 tranh thủ giờ nghỉ nhờ trợ giảng. Sau nghỉ ta chuyển sang dữ liệu công việc thật của từng người.

### [01:40-02:15] Thực hành 2 (dữ liệu công việc của học viên)
- **Lời dẫn GV:** "Phần hay nhất: giờ ta không dùng file demo nữa, mà dùng thư mục công việc thật của chính cả lớp. Ai đã mang sẵn 1 tài liệu và vài ghi chú thì bỏ vào một thư mục trống, rồi trỏ Claude Code vào đó."
- **Đề bài:** Học viên tạo thư mục dự án của riêng mình, bỏ vào vài file công việc thật (ghi chú, một tài liệu, một file dữ liệu nếu có), rồi: (1) cho agent đọc và tóm tắt, (2) tạo `CLAUDE.md` cho riêng mình từ mẫu, (3) nhờ agent tạo hoặc sửa một file theo nhu cầu thật.
- **Prompt gợi ý:**
  ```
  1. Đọc tất cả file trong thư mục này và tóm tắt giúp tôi đang có gì và việc nào cần ưu tiên.

  2. Tạo file CLAUDE.md cho thư mục này. Tôi tên [tên bạn], làm [công việc]. Thư mục này để [mục đích]. Quy tắc: trả lời tiếng Việt ngắn gọn, trước khi sửa hay xóa file phải hỏi tôi, không bịa số liệu, văn bản gửi đi không dùng emoji.

  3. [Chọn 1 việc thật] Ví dụ: Từ ghi chú của tôi, tạo file ke-hoach-tuan.md gồm các việc cần làm theo thứ tự ưu tiên.
  ```
- **File demo:** không dùng file demo; dùng dữ liệu công việc thật của học viên (GV nhắc: nếu chưa mang, tạm dùng lại thư mục demo `tai-lieu-phat/demo/buoi-01/du-an-mau/`).
- **Kết quả mong đợi:** Mỗi học viên có 1 thư mục dự án riêng, có `CLAUDE.md` đã điền đúng tên và công việc của mình, và ít nhất 1 file do agent tạo hoặc sửa từ dữ liệu thật. GV đi từng bàn kiểm tra agent đã trỏ đúng thư mục và CLAUDE.md có nội dung thật.

### [02:15-02:30] Chốt & giao bài
- **Lời dẫn GV:** "Tổng kết nhanh: hôm nay cả lớp đã biết agent khác chat ở ba điểm (tự làm nhiều bước, đụng file thật, nhớ bối cảnh), đã tự tay cho agent đọc, tạo, sửa file, và đã có CLAUDE.md của riêng mình. Đây là nền cho buổi sau."
- Tổng kết 3 điều rút ra: chọn đúng thư mục dự án; CLAUDE.md giúp agent nhớ bạn; agent luôn xin phép trước khi sửa file.
- **Bài về nhà:** hoàn thiện CLAUDE.md của mình cho đầy đủ; cho agent xử lý ít nhất 1 việc thật ở nhà (đọc tài liệu, tạo danh sách việc, dọn lại một file). Chụp màn hình kết quả gửi Zalo lớp.
- Xem trước buổi sau: Buổi 2 học **Skill**, đóng gói quy trình lặp lại (ví dụ tóm tắt tài liệu) để không phải dặn lại mỗi lần.
- **Câu hỏi tương tác:** "Ai thấy việc gì mình lặp đi lặp lại hằng tuần? Ghi lại, buổi sau ta biến nó thành skill."

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Thư mục này đang có những file gì? Liệt kê tên file và mỗi file nói về cái gì. | `demo/buoi-01/du-an-mau/` | Liệt kê đúng 2 file: ghi chú công việc + danh sách khách hàng |
| 2 | Đọc tất cả file và tóm tắt: bao nhiêu việc cần làm, bao nhiêu khách hàng, việc nào gấp nhất. | `ghi-chu-cong-viec.md`, `danh-sach-khach-hang.md` | 5 việc, 5 khách, gấp nhất là báo cáo doanh thu (thứ Sáu) và họp thứ Tư |
| 3 | Từ ghi-chu-cong-viec.md tạo file todo.md dạng checkbox, ghi rõ hạn. | `ghi-chu-cong-viec.md` -> tạo `todo.md` | File todo.md mới có 5 checkbox, việc có hạn ghi rõ |
| 4 | Thêm khách hàng "Công ty Bình Minh" vào danh-sach-khach-hang.md. | `danh-sach-khach-hang.md` | Agent xin xác nhận, thêm dòng thứ 6, danh sách còn 6 khách |
| 5 | Tạo CLAUDE.md với thông tin tôi là ai, mục đích thư mục, quy tắc làm việc. | tham chiếu `mau-cau-hinh/claude-md-mau.md` -> tạo `CLAUDE.md` | File CLAUDE.md có 3 mục: tôi là ai, thư mục để làm gì, quy tắc |

## Câu hỏi tương tác gợi ý
- "Cả lớp đang dùng AI kiểu nào: mở chat gõ câu hỏi, hay đã cho AI đụng file trong máy?"
- "Vì sao agent tự sửa được file vừa tiện vừa hơi đáng lo? Cơ chế nào giữ an toàn?"
- "Khác biệt lớn nhất giữa việc dán nội dung file vào chat và việc để agent tự đọc thư mục là gì?"
- "Nếu không có CLAUDE.md, mỗi lần mở agent bạn sẽ phải làm lại việc gì?"
- "Ai thấy việc gì mình lặp lại hằng tuần, có thể đóng gói cho agent làm giúp?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Agent xin xác nhận trước khi sửa file, học viên bối rối | Giải thích: đây là cơ chế an toàn. Đọc nội dung agent định sửa, đồng ý thì gõ "được"/"đồng ý", không muốn thì gõ "không" để agent dừng. |
| Chưa có CLAUDE.md, agent hỏi lại nhiều thông tin | Bình thường vì agent chưa biết bạn. Tạo CLAUDE.md xong, agent tự đọc và không hỏi lại nữa. |
| Chọn nhầm thư mục, agent không thấy file demo | Đóng lại, mở đúng thư mục `demo/buoi-01/du-an-mau/`. Chạy lại prompt số 1 để kiểm tra agent thấy đúng file. |
| Agent tóm tắt thiếu hoặc sai số việc/khách | Nhắc học viên hỏi lại rõ hơn: "Đọc kỹ lại cả 2 file rồi đếm chính xác giúp tôi." Agent đọc lại và sửa. |
| Học viên chưa mang dữ liệu công việc thật | Cho tạm dùng lại thư mục demo cho Thực hành 2, dặn buổi sau mang file thật. |
| Agent tạo file nhưng học viên không thấy file đâu | Hướng dẫn mở lại thư mục dự án trong máy để thấy file mới. Nhắc: file agent tạo là file thật trên ổ đĩa. |
| Máy chưa cài được Claude Desktop hoặc chưa đăng nhập | Trợ giảng hỗ trợ cài trong giờ nghỉ; trong lúc đó ghép cặp ngồi chung máy bạn bên cạnh để không bỏ lỡ thực hành. |

## Bài tập
- **Tại lớp:** Có 1 thư mục dự án riêng + CLAUDE.md đã điền; cho agent đọc thư mục và tóm tắt thành công; tạo được `todo.md`; thêm được 1 khách hàng vào danh sách.
- **Về nhà:** Hoàn thiện CLAUDE.md đầy đủ hơn; cho agent xử lý ít nhất 1 việc thật (đọc 1 tài liệu và tóm tắt, hoặc tạo 1 danh sách việc từ ghi chú); chụp màn hình kết quả gửi Zalo lớp. Nghĩ trước 1 việc lặp lại hằng tuần để buổi sau biến thành skill.

## Tiêu chí hoàn thành buổi
- [ ] Mở được Claude Code và trỏ đúng vào thư mục dự án
- [ ] Cho agent đọc cả thư mục và nhận đúng tóm tắt (5 việc, 5 khách với file demo)
- [ ] Tạo được file `todo.md` mới từ ghi chú công việc
- [ ] Thêm được 1 khách hàng vào danh sách (qua bước agent xin xác nhận)
- [ ] Có file `CLAUDE.md` ở thư mục dự án với thông tin thật của mình
- [ ] Hiểu và nói lại được 3 điểm agent khác chat thường
