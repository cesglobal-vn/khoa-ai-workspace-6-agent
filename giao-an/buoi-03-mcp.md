# Giáo án Buổi 03: MCP - Cắm công cụ và dữ liệu ngoài cho agent

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

## Thông tin buổi
- **Buổi:** 03 / 6
- **Khái niệm chính:** MCP (Model Context Protocol)
- **Loại:** Thực chiến
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đã đăng nhập tài khoản CES cấp
- [ ] Mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-03/`
- [ ] File demo cần dùng: `doanh-thu-quy.csv`, `don-hang.csv`
- [ ] Đã cắm sẵn 1 MCP Filesystem trỏ vào thư mục demo (để phòng khi cắm live bị lỗi mạng)
- [ ] Mẫu cấu hình liên quan: `mau-cau-hinh/mcp-cau-hinh-mau.md`
- [ ] Tự tính trước con số chuẩn của 2 file demo để đối chiếu khi agent trả kết quả (xem bảng đáp án cuối giáo án)

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu MCP là cổng cắm để agent chạm vào công cụ và dữ liệu ngoài: file trong máy, web, Google Drive, cơ sở dữ liệu.
2. Tự cắm được 1 MCP (Filesystem hoặc Google Drive) qua Claude Desktop và cấp quyền an toàn.
3. Ra lệnh bằng tiếng Việt để agent đọc file dữ liệu thật và phân tích: tính tổng, trung bình, tăng trưởng, top, đếm theo trạng thái.
4. Biết cách kiểm lại con số quan trọng agent đưa ra, không tin ngay 100%.

## Kết quả cầm về (deliverable)
- 1 MCP đã cắm và dùng được trên máy học viên (đọc được ít nhất 1 file dữ liệu công việc thật).
- 1 bản phân tích ngắn do agent tạo ra từ file dữ liệu của chính học viên (có tổng, trung bình hoặc đếm theo nhóm, kèm gợi ý biểu đồ).

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **MCP là cổng cắm.** Buổi 2 học viên dạy agent quy trình LÀM GÌ (skill). Buổi này cắm cho agent một cổng để CHẠM VÀO dữ liệu thật: đọc file Excel/CSV trong máy, tra web, mở Google Drive, hỏi cơ sở dữ liệu công ty.
- **Mỗi công cụ là một MCP server.** Cắm server nào thì agent dùng được các công cụ của server đó. Ví dụ cắm Filesystem thì agent đọc/ghi được file trong một thư mục cụ thể.
- **Cắm xong, tool hiện tên dạng `mcp__<ten-server>__<ten-tool>`.** Học viên không cần nhớ tên này. Cứ ra lệnh tự nhiên bằng tiếng Việt, ví dụ "Đọc file doanh-thu-quy.csv và tính tổng doanh thu theo khu vực", agent tự chọn đúng tool.
- **Cấp quyền là bước quan trọng.** Khi cắm, Claude Desktop hỏi cho phép truy cập thư mục hay tài khoản nào. Chỉ cấp đúng phần cần, ưu tiên quyền chỉ đọc khi chỉ cần xem.
- **Luôn kiểm lại con số quan trọng.** Agent tính nhanh nhưng có thể nhầm nếu file lỗi phông hoặc cột đặt tên khó hiểu. Con số dùng để báo cáo hay ra quyết định thì phải soi lại.

---

## Timeline chi tiết (theo phút)

Mỗi mục demo/thực hành trình bày theo khối 4 dòng dưới đây.

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn GV:** "Chào cả lớp. Buổi trước mình đã dạy agent một quy trình lặp lại bằng skill: tóm tắt tài liệu. Skill là dạy agent LÀM GÌ. Hôm nay mình mở cho agent một cánh cửa mới: cho nó chạm vào dữ liệu thật trong máy anh chị. Đó là MCP."
- Recap buổi 2: skill = gói chỉ dẫn cho quy trình lặp lại, Claude tự nạp đúng skill khi gặp việc phù hợp.
- Nêu mục tiêu buổi hôm nay: cắm 1 MCP, cho agent đọc file dữ liệu, ra lệnh phân tích số, và biết cách kiểm lại kết quả.
- **Câu hỏi khởi động:** "Anh chị nào đang có 1 file Excel doanh thu hay đơn hàng mà tuần nào cũng phải ngồi cộng tay? Giơ tay. Cuối buổi anh chị sẽ để agent làm phần cộng đó."

### [00:15-00:35] Lý thuyết ngắn về MCP
- **Lời dẫn GV:** "MCP viết tắt của Model Context Protocol, nhưng anh chị cứ hiểu đơn giản: nó là cái cổng cắm chuẩn. Giống như cổng USB trên máy tính. Cắm USB chuột thì máy điều khiển được chuột, cắm USB bàn phím thì gõ được. Ở đây, cắm MCP Filesystem thì agent đọc được file, cắm MCP Google Drive thì agent đọc được Drive."
- Nội dung trình bày:
  - Agent một mình chỉ nói chuyện được. Muốn nó chạm vào file, web, Drive, cơ sở dữ liệu thì phải có cổng cắm. Đó là MCP.
  - Mỗi công cụ ngoài là một MCP server. Bảng MCP hay dùng cho khối văn phòng: Filesystem (đọc/ghi file trong 1 thư mục), Google Drive (đọc tài liệu, sheet trên Drive), Web/Fetch (tra web), Cơ sở dữ liệu (hỏi số liệu hệ thống công ty khi được cấp).
  - Hai cách cắm: qua giao diện Claude Desktop phần Connectors (khuyên dùng cho lớp), hoặc bằng lệnh `claude mcp add`. Buổi này dùng cách giao diện.
  - Sau khi cắm, tool hiện tên máy móc dạng `mcp__server__tool`, nhưng học viên chỉ cần ra lệnh tiếng Việt tự nhiên.
  - An toàn: chỉ cắm nguồn tin cậy, cấp quyền tối thiểu, dữ liệu nhạy cảm thì hỏi bộ phận phụ trách trước.
- **Câu hỏi tương tác:** "Theo anh chị, skill và MCP khác nhau chỗ nào?" (Đáp mong muốn: skill dạy agent LÀM GÌ, MCP cho agent CHẠM VÀO CÁI GÌ. Hai cái bổ sung nhau.)

### [00:35-01:00] Demo giảng viên: cắm MCP Filesystem và phân tích doanh-thu-quy.csv

**Bước 1: Cắm MCP Filesystem qua Claude Desktop**
- **Lời dẫn GV:** "Bây giờ mình cắm cổng đầu tiên. Anh chị nhìn màn hình mình. Mình vào phần cài đặt kết nối của Claude Desktop, chọn Filesystem, và trỏ nó vào đúng thư mục chứa file demo. Khi nó hỏi cấp quyền, mình đọc kỹ rồi mới bấm cho phép."
- **Prompt gõ vào Claude Code:**
  ```
  Liệt kê các file trong thư mục demo buoi-03 mà bạn đọc được.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-03/` (cả thư mục)
- **Kết quả mong đợi:** Agent liệt kê được 2 file: `doanh-thu-quy.csv` và `don-hang.csv`. Nếu agent báo không thấy file, tức là MCP chưa trỏ đúng thư mục hoặc chưa cấp quyền, quay lại bước cắm.

**Bước 2: Cho agent đọc file và tính tổng theo khu vực, theo sản phẩm, chỉ ra xu hướng**
- **Lời dẫn GV:** "Cổng đã thông. Giờ mình ra lệnh bằng tiếng Việt bình thường, không cần biết tên tool. Mình bảo nó đọc file doanh thu quý và phân tích cho mình."
- **Prompt gõ vào Claude Code:**
  ```
  Đọc file doanh-thu-quy.csv trong thư mục demo buoi-03. Tính tổng doanh thu
  theo khu vực và theo sản phẩm. Chỉ ra xu hướng doanh thu qua 3 tháng.
  Gợi ý loại biểu đồ phù hợp để trình bày. Đơn vị là triệu đồng.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-03/doanh-thu-quy.csv`
- **Kết quả mong đợi (đối chiếu số thật):**
  - Tổng theo khu vực: TP HCM = 1.565 triệu, Ha Noi = 1.305 triệu. TP HCM cao hơn Ha Noi.
  - Tổng theo sản phẩm: Goi Cao cap = 1.640 triệu, Goi Tieu chuan = 1.230 triệu. Cao cap chiếm phần lớn hơn.
  - Tổng doanh thu cả quý = 2.870 triệu (khoảng 2,87 tỷ đồng).
  - Xu hướng 3 tháng: tăng đều. Tháng 1 = 870, Tháng 2 = 915, Tháng 3 = 1.085 triệu. Goi Cao cap tăng nhanh (Tháng 1 = 480, Tháng 3 = 640 triệu).
  - Gợi ý biểu đồ: biểu đồ cột nhóm so sánh 2 khu vực theo tháng, hoặc biểu đồ đường thể hiện xu hướng tăng của tổng doanh thu.
- **Lời dẫn GV (nhấn kiểm lại):** "Đây là chỗ quan trọng nhất buổi. Agent nói TP HCM 1.565 triệu. Mình không tin ngay. Mình cộng nhanh cột TP HCM trong đầu hoặc bằng máy tính, thấy khớp thì mới dùng. Con số để báo cáo Sếp thì phải soi lại."

**Bước 3: Yêu cầu agent xuất bảng gọn để dễ đối chiếu**
- **Lời dẫn GV:** "Để dễ kiểm, mình bảo nó trình bày lại thành bảng."
- **Prompt gõ vào Claude Code:**
  ```
  Trình bày lại kết quả trên thành 2 bảng: một bảng tổng doanh thu theo tháng
  và theo khu vực, một bảng tổng theo sản phẩm. Ghi rõ đơn vị triệu đồng.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-03/doanh-thu-quy.csv`
- **Kết quả mong đợi:** Agent xuất 2 bảng markdown gọn. Bảng theo tháng có 3 dòng (Tháng 1, 2, 3) với TP HCM và Ha Noi tách cột; tổng mỗi tháng khớp 870 / 915 / 1.085. Bảng theo sản phẩm có Goi Tieu chuan 1.230 và Goi Cao cap 1.640.

### [01:00-01:30] Thực hành 1 (file demo chung: don-hang.csv)
- **Lời dẫn GV:** "Tới lượt anh chị. File thứ hai là danh sách 10 đơn hàng, có cột trạng thái: Da thanh toan, Cho thanh toan, Huy. Sếp hay hỏi: còn bao nhiêu đơn chưa thu tiền, tổng bao nhiêu, có đơn nào hủy không. Anh chị để agent trả lời."
- **Đề bài:** Dùng MCP đã cắm, cho agent đọc `don-hang.csv` và đếm số đơn theo trạng thái, tính tổng giá trị từng nhóm.
- **Prompt gợi ý cho học viên:**
  ```
  Đọc file don-hang.csv trong thư mục demo buoi-03. Cho biết có bao nhiêu đơn
  Cho thanh toan và tổng giá trị của các đơn đó là bao nhiêu. Có bao nhiêu đơn
  Huy và tổng giá trị. Đơn vị triệu đồng.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-03/don-hang.csv`
- **Kết quả mong đợi (đối chiếu số thật):**
  - Cho thanh toan: 3 đơn (DH003, DH005, DH010), tổng = 275 triệu.
  - Huy: 1 đơn (DH007), tổng = 120 triệu.
  - Nếu học viên hỏi thêm: Da thanh toan có 6 đơn, tổng = 380 triệu. Tổng giá trị cả 10 đơn = 775 triệu.
- **Lời dẫn GV (nhấn kiểm lại):** "Agent bảo 3 đơn Cho thanh toan, tổng 275 triệu. File chỉ có 10 dòng nên anh chị soi thẳng vào file đếm tay được. Đếm thấy đúng 3 đơn thì yên tâm. Đây là thói quen phải giữ."

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2 (dữ liệu công việc của học viên)
- **Lời dẫn GV:** "Phần hay nhất. Anh chị mở file Excel hoặc CSV công việc thật mình mang theo: doanh thu, đơn hàng, chấm công, danh sách khách, gì cũng được. Mình sẽ cắm MCP trỏ vào thư mục chứa file đó rồi để agent phân tích giúp."
- **Đề bài:** Mỗi học viên cắm MCP Filesystem trỏ vào thư mục chứa file công việc thật của mình, cho agent đọc và phân tích ít nhất 1 con số có ý nghĩa (tổng, trung bình, đếm theo nhóm), kèm gợi ý biểu đồ.
- **Prompt gợi ý (học viên thay tên file và câu hỏi cho đúng dữ liệu của mình):**
  ```
  Đọc file <ten-file-cua-toi> trong thư mục dự án. Mô tả file có những cột gì.
  Sau đó tính giúp tôi: <ví dụ: tổng doanh thu theo tháng / trung bình mỗi đơn /
  đếm số khách theo khu vực>. Chỉ ra điểm đáng chú ý và gợi ý biểu đồ phù hợp.
  ```
- **File demo:** dữ liệu công việc thật do học viên mang theo (không dùng file trong repo).
- **Kết quả mong đợi:** Agent đọc được file, mô tả đúng các cột, và trả về ít nhất 1 con số phân tích cho học viên. Học viên kiểm lại 1 con số bằng tay hoặc bằng hàm SUM trong Excel để xác nhận khớp.
- **Lời dẫn GV:** "Ai xong sớm, thử hỏi agent thêm: dữ liệu này có gì bất thường không, có dòng nào thiếu không. Đó là lúc agent thật sự đỡ việc cho anh chị."

### [02:15-02:35] Chốt & giao bài
- **Lời dẫn GV:** "Hôm nay anh chị đã mở được cổng cho agent chạm vào dữ liệu thật. Nhớ 3 ý: một, MCP là cổng cắm công cụ và dữ liệu ngoài. Hai, cắm xong cứ ra lệnh tiếng Việt tự nhiên, không cần nhớ tên tool. Ba, con số quan trọng luôn kiểm lại. Buổi sau mình học Subagent: tạo agent con chuyên một việc như làm báo cáo, nghiên cứu."
- Tổng kết: skill (buổi 2) + MCP (buổi 3) là hai mảnh ghép; buổi sau bắt đầu tạo agent chuyên trách.
- Bài về nhà: cắm 1 MCP trên máy nhà, cho agent phân tích 1 file dữ liệu công việc thật, chụp lại kết quả và ghi 1 dòng mình đã kiểm lại con số nào.
- Xem trước: khái niệm Subagent (agent con có vai trò và công cụ riêng).

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Liệt kê các file trong thư mục demo buoi-03 mà bạn đọc được. | thư mục `buoi-03/` | Thấy 2 file: doanh-thu-quy.csv, don-hang.csv |
| 2 | Đọc doanh-thu-quy.csv. Tính tổng doanh thu theo khu vực và sản phẩm, chỉ xu hướng 3 tháng, gợi ý biểu đồ. | `doanh-thu-quy.csv` | TP HCM 1.565 > Ha Noi 1.305; Cao cap 1.640 > Tieu chuan 1.230; tổng quý 2.870; tăng dần 870/915/1.085 |
| 3 | Trình bày lại thành 2 bảng (theo tháng và theo sản phẩm), đơn vị triệu. | `doanh-thu-quy.csv` | 2 bảng markdown, số khớp bước 2 |
| 4 | Trong don-hang.csv có bao nhiêu đơn Cho thanh toan và tổng giá trị, bao nhiêu đơn Huy. | `don-hang.csv` | Cho thanh toan 3 đơn / 275 triệu; Huy 1 đơn / 120 triệu |
| 5 | Đọc file công việc của tôi, mô tả cột, tính 1 con số có ý nghĩa, gợi ý biểu đồ. | file thật của HV | Agent đọc đúng, trả 1 con số phân tích, HV kiểm lại khớp |

## Câu hỏi tương tác gợi ý
- "Skill và MCP khác nhau chỗ nào?" (skill = LÀM GÌ; MCP = CHẠM VÀO CÁI GÌ)
- "Vì sao không nên tin ngay con số agent đưa ra?" (file có thể lỗi phông, cột khó hiểu; số báo cáo phải soi lại)
- "Khi Claude Desktop hỏi cấp quyền truy cập cả ổ đĩa, anh chị làm gì?" (chỉ cấp đúng thư mục cần, ưu tiên quyền chỉ đọc)
- "Ngoài Filesystem, công việc anh chị hay cần cắm MCP nào?" (Google Drive, Web, cơ sở dữ liệu công ty)

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Agent báo không đọc được file / không thấy file | MCP chưa cắm hoặc chưa cấp quyền, hoặc trỏ sai thư mục. Vào lại Connectors, kiểm tra server Filesystem đã bật và trỏ đúng thư mục chứa file. |
| File CSV lỗi phông, chữ tiếng Việt hiển thị sai dấu | Bảo agent đọc lại và bỏ qua lỗi dấu, hoặc lưu file CSV lại theo mã UTF-8 rồi đọc lại. Nhắc học viên: tên cột không dấu (như trong file demo) thường an toàn hơn. |
| Agent tính ra con số lệch với file | Yêu cầu agent liệt kê từng dòng nó dùng để cộng, rồi đối chiếu. File nhỏ thì đếm tay. Nhắc nguyên tắc luôn kiểm lại con số quan trọng. |
| Học viên không rõ đơn vị tiền (nghìn, triệu, tỷ) | Luôn ghi đơn vị vào prompt ("đơn vị triệu đồng"). File demo dùng cột "Doanh thu (trieu)" nên mọi số là triệu đồng; tổng quý 2.870 triệu tức 2,87 tỷ. |
| Claude Desktop xin quyền ghi/xóa trong khi chỉ cần xem | Từ chối quyền ghi/xóa, chỉ cấp quyền đọc. Giải thích: an toàn khi cấp quyền là cấp tối thiểu. |
| Cắm live bị lỗi mạng giữa lớp | Dùng MCP Filesystem GV đã cắm sẵn trước buổi (mục Chuẩn bị), demo tiếp để không gãy mạch. |

## Bài tập
- **Tại lớp:** cắm 1 MCP Filesystem, cho agent phân tích `don-hang.csv` (Thực hành 1) và 1 file công việc thật của mình (Thực hành 2), mỗi kết quả tự kiểm lại 1 con số.
- **Về nhà:** cắm 1 MCP trên máy nhà, cho agent phân tích 1 file dữ liệu công việc thật (tổng, trung bình, hoặc đếm theo nhóm), chụp màn hình kết quả, ghi 1 dòng "tôi đã kiểm lại con số ... bằng cách ...".

## Tiêu chí hoàn thành buổi
- [ ] Học viên cắm được ít nhất 1 MCP và agent đọc được file dữ liệu qua cổng đó.
- [ ] Agent trả về đúng kết quả với 2 file demo (số khớp bảng đáp án).
- [ ] Học viên chạy phân tích trên ít nhất 1 file công việc thật của mình.
- [ ] Học viên thực hiện được thao tác kiểm lại ít nhất 1 con số quan trọng.

---

## Bảng đáp án chuẩn (GV giữ, dùng đối chiếu khi agent trả kết quả)

**doanh-thu-quy.csv (đơn vị: triệu đồng)**

| | Tháng 1 | Tháng 2 | Tháng 3 | Tổng quý |
|---|---|---|---|---|
| Ha Noi | 400 | 405 | 500 | 1.305 |
| TP HCM | 470 | 510 | 585 | 1.565 |
| Tổng tháng | 870 | 915 | 1.085 | 2.870 |

| Sản phẩm | Tổng quý |
|---|---|
| Goi Tieu chuan | 1.230 |
| Goi Cao cap | 1.640 |

Xu hướng: tổng doanh thu tăng đều qua 3 tháng. TP HCM luôn cao hơn Ha Noi. Goi Cao cap tăng nhanh nhất (480 → 520 → 640).

**don-hang.csv (đơn vị: triệu đồng)**

| Trạng thái | Số đơn | Tổng giá trị |
|---|---|---|
| Da thanh toan | 6 | 380 |
| Cho thanh toan | 3 | 275 |
| Huy | 1 | 120 |
| **Tổng** | **10** | **775** |
