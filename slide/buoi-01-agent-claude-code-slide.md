# Nội dung slide Buổi 1: Agent là gì và làm quen Claude Code

> Dùng cho GV dựng slide trình chiếu. Kiểu CES: nền trắng, chữ đậm màu navy, điểm nhấn màu teal/gold.
> Mỗi mục "---" là 1 slide. Phần [Ghi chú GV] là lời nói thêm, không in lên slide.
> Tổng: 22 slide cho buổi 150 phút.

---

## Slide 1: Slide tiêu đề

**KHÓA AI WORKSPACE**
Làm chủ Agent với Claude Code

**Buổi 1: Agent là gì và làm quen Claude Code**

CES Global | Trung tâm Đào tạo & Ứng dụng Công nghệ

[Ghi chú GV: đây là buổi nền, quan trọng nhất. Chào lớp, tạo không khí.]

---

## Slide 2: Sau 6 buổi cả lớp có gì

Một đội trợ lý AI làm việc thật trên máy của bạn.

- Biết đọc, tóm tắt, xử lý file
- Phân tích dữ liệu, soạn báo cáo
- Nghiên cứu thị trường
- Nhiều agent chạy song song cho một quy trình

Tất cả bằng tiếng Việt, không cần biết lập trình.

---

## Slide 3: Bản đồ 6 buổi

| Buổi | Học gì |
|---|---|
| **1. Agent** | Làm quen Claude Code, ra lệnh cho agent (hôm nay) |
| 2. Skill | Đóng gói quy trình lặp lại |
| 3. MCP | Cắm công cụ và dữ liệu ngoài |
| 4. Subagent | Tạo agent chuyên trách |
| 5. Agent Team | Đội agent chạy song song |
| 6. Capstone | Ghép tất cả cho việc thật |

Mỗi buổi là nền cho buổi sau.

---

## Slide 4: Mục tiêu buổi hôm nay

Cuối buổi, ai cũng làm được:

1. Hiểu agent khác chat AI thường ở đâu
2. Mở Claude Code, chọn đúng thư mục dự án
3. Tạo file CLAUDE.md làm bộ nhớ cho agent
4. Ra lệnh cho agent đọc cả thư mục và tóm tắt
5. Cho agent tạo file mới và sửa file có sẵn

---

## Slide 5: Câu hỏi mở đầu

Cả lớp đang dùng AI kiểu nào?

- Mở chat, gõ câu hỏi, đọc trả lời?
- Hay đã từng cho AI đụng vào file trong máy?

[Ghi chú GV: để 2-3 học viên trả lời, dẫn vào phần phân biệt chat và agent.]

---

## Slide 6: Chat AI thường vs Agent

| Chat AI thường | Agent (Claude Code) |
|---|---|
| Gõ câu hỏi, nhận chữ trả lời | Ra lệnh, agent tự làm nhiều bước |
| Bạn tự copy paste | Agent đọc và sửa file thật |
| Không đụng file trong máy | Làm việc trong thư mục bạn chọn |
| Quên hết khi đóng | Nhớ bối cảnh nhờ CLAUDE.md |

---

## Slide 7: Ba điểm làm agent mạnh hơn

1. **Tự làm nhiều bước**
   Một lệnh, agent đọc nhiều file rồi tổng hợp, không cần dắt từng bước.

2. **Đụng file thật**
   Agent tạo file mới, sửa file có sẵn ngay trong thư mục của bạn.

3. **Nhớ bối cảnh**
   Nhờ CLAUDE.md, agent biết bạn là ai và muốn làm việc kiểu gì.

---

## Slide 8: Thư mục dự án là gì

Một thư mục trên máy bạn chọn cho agent làm việc.

- Agent chỉ đọc và sửa trong thư mục này
- Không lục lung tung nơi khác
- Đây là "bàn làm việc" của agent

[Ghi chú GV: nhấn đây là bước quan trọng nhất, chọn đúng thư mục.]

---

## Slide 9: CLAUDE.md là bộ nhớ của agent

Một file văn bản đặt ở gốc thư mục dự án. Agent tự đọc mỗi lần mở.

Ghi 3 thứ:
- Tôi là ai (tên, nghề)
- Thư mục này để làm gì
- Quy tắc khi làm việc với tôi

Càng ghi rõ, agent càng làm đúng ngay lần đầu. Không phải dặn lại mỗi lần.

---

## Slide 10: Phần demo, 5 bước

GV làm mẫu, cả lớp xem trước, chưa gõ theo.

1. Mở Claude Code, chọn thư mục demo
2. Cho agent đọc và tóm tắt "tôi đang có gì"
3. Cho agent tạo file todo.md
4. Cho agent sửa file (thêm khách hàng)
5. Tạo file CLAUDE.md

---

## Slide 11: Demo bước 1, xem thư mục có gì

**Prompt:**
```
Thư mục này đang có những file gì? Liệt kê tên file
và cho tôi biết mỗi file nói về cái gì.
```

**Kết quả mong đợi:** agent liệt kê đúng 2 file: ghi chú công việc + danh sách khách hàng.

Điểm nhấn: agent tự đọc file, không cần ta dán nội dung.

---

## Slide 12: Demo bước 2, đọc và tóm tắt

**Prompt:**
```
Đọc tất cả file trong thư mục này và tóm tắt cho tôi:
tôi đang có bao nhiêu việc cần làm, bao nhiêu khách hàng,
và việc nào gấp nhất.
```

**Kết quả mong đợi:** 5 việc cần làm, 5 khách hàng, gấp nhất là báo cáo doanh thu (hạn thứ Sáu) và họp thứ Tư có sếp dự.

Điều chat thường không làm được: tự mở từng file rồi gộp lại.

---

## Slide 13: Demo bước 3, tạo file todo.md

**Prompt:**
```
Từ file ghi-chu-cong-viec.md, tạo cho tôi một file mới
tên todo.md gồm danh sách việc dạng checkbox,
việc nào có hạn thì ghi rõ hạn.
```

**Kết quả mong đợi:** file todo.md mới, 5 dòng checkbox, việc có hạn ghi rõ.

[Ghi chú GV: mở file mới ra cho lớp thấy nó có thật trong thư mục.]

---

## Slide 14: Demo bước 4, sửa file và cơ chế an toàn

**Prompt:**
```
Thêm một khách hàng mới vào danh-sach-khach-hang.md:
tên "Công ty Bình Minh", ngành "Giáo dục",
trạng thái "Tiềm năng", ghi chú "Mới gọi điện hỏi thông tin".
```

**Kết quả mong đợi:** agent cho xem trước dòng sắp thêm và **xin xác nhận**. Đồng ý thì file có thêm dòng thứ 6.

Điểm nhấn an toàn: không đồng ý thì gõ "không", agent dừng.

---

## Slide 15: Demo bước 5, tạo bộ nhớ CLAUDE.md

**Prompt:**
```
Tạo cho tôi một file CLAUDE.md ở thư mục này. Tôi tên
Trần Văn Minh, làm nhân viên kinh doanh phần mềm. Thư mục
này để quản lý việc cần làm và danh sách khách hàng. Quy tắc:
trả lời tiếng Việt ngắn gọn, trước khi sửa hay xóa file phải
hỏi tôi, không bịa số liệu, văn bản gửi đi không dùng emoji.
```

**Kết quả mong đợi:** file CLAUDE.md có 3 mục: tôi là ai, thư mục để làm gì, quy tắc.

---

## Slide 16: Thực hành 1, cả lớp cùng làm

Trỏ Claude Code vào thư mục demo, chạy lần lượt:

```
1. Đọc tất cả file và tóm tắt: bao nhiêu việc, bao nhiêu khách.

2. Tạo file todo.md từ ghi-chu-cong-viec.md, dạng checkbox.

3. Thêm khách hàng "Công ty Sao Mai", ngành "Logistics",
   trạng thái "Tiềm năng", ghi chú "Gặp tại hội chợ".
```

Ai kẹt bước nào giơ tay, GV và trợ giảng qua ngay.

---

## Slide 17: Nghỉ giải lao 10 phút

Ai chưa xong Thực hành 1, tranh thủ nhờ trợ giảng.

Sau nghỉ: dùng dữ liệu công việc thật của chính bạn.

---

## Slide 18: Thực hành 2, dữ liệu thật của bạn

Bỏ vài file công việc thật vào một thư mục trống, trỏ Claude Code vào đó, rồi:

1. Cho agent đọc và tóm tắt "tôi đang có gì, ưu tiên việc nào"
2. Tạo CLAUDE.md cho riêng mình (tên, nghề, mục đích, quy tắc)
3. Nhờ agent tạo hoặc sửa một file theo nhu cầu thật

[Ghi chú GV: đi từng bàn, kiểm agent trỏ đúng thư mục và CLAUDE.md có nội dung thật.]

---

## Slide 19: Tình huống hay gặp

| Tình huống | Cách xử lý |
|---|---|
| Agent xin xác nhận trước khi sửa | Đây là an toàn. Đồng ý gõ "được", không thì gõ "không" |
| Chọn nhầm thư mục | Mở lại đúng thư mục demo, chạy lại lệnh số 1 |
| Agent tạo file mà không thấy đâu | Mở lại thư mục trong máy, file là file thật trên ổ đĩa |
| Tóm tắt thiếu số việc/khách | Nhắc agent: "đọc kỹ lại cả 2 file rồi đếm chính xác" |

---

## Slide 20: Ba điều rút ra hôm nay

1. Chọn đúng **thư mục dự án** cho agent làm việc
2. **CLAUDE.md** giúp agent nhớ bạn, không phải dặn lại
3. Agent **luôn xin phép** trước khi sửa file

Agent khác chat ở ba điểm: tự làm nhiều bước, đụng file thật, nhớ bối cảnh.

---

## Slide 21: Bài về nhà

- Hoàn thiện CLAUDE.md của mình cho đầy đủ
- Cho agent xử lý ít nhất 1 việc thật (đọc tài liệu và tóm tắt, hoặc tạo danh sách việc từ ghi chú)
- Chụp màn hình kết quả gửi Zalo lớp
- Nghĩ trước 1 việc bạn lặp lại hằng tuần, buổi sau biến thành skill

---

## Slide 22: Xem trước Buổi 2

**Buổi 2: Skill**

Đóng gói một quy trình lặp lại (ví dụ tóm tắt tài liệu) thành skill, để agent tự làm đúng mỗi lần mà không phải dặn lại.

Câu hỏi giữ lại: việc gì bạn làm đi làm lại hằng tuần?

Cảm ơn cả lớp. Hẹn gặp Buổi 2.
