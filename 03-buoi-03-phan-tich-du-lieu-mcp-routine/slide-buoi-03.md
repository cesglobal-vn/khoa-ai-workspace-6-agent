# BỘ SLIDE BÀI GIẢNG BUỔI 03: CLAUDE.MD GLOBAL VS CÁ NHÂN, TỐI ƯU TOKEN MARKITDOWN, SKILL PPT-MASTER, MCP VÀ ROUTINE TỰ ĐỘNG HÓA

> **Đơn vị đào tạo:** CES Global — Trung tâm Đào tạo & Ứng dụng Công nghệ Trí tuệ Nhân tạo  
> **Chương trình:** Khóa AI Workspace — Làm chủ 6 AI Agent Thực Chiến với Claude Code  
> **Thời lượng:** 150 phút (2,5 giờ) | Live Zoom & VIP LMS  
> **Quy chuẩn hiển thị:** Mỗi cặp dấu ngăn cách `---` tương ứng với 01 slide trình chiếu độc lập. Phần `[Ghi chú Giảng viên]` cung cấp lời dẫn trực tiếp và prompt chính xác để giảng viên đứng lớp.

---

## Slide 01: Slide Tiêu Đề

# KHÓA HỌC: AI WORKSPACE
## Làm Chủ 6 AI Agent Thực Chiến Với Claude Code

### BUỔI 03: CLAUDE.MD GLOBAL VS CÁ NHÂN, TỐI ƯU TOKEN MARKITDOWN, SKILL PPT-MASTER, MCP & ROUTINE TỰ ĐỘNG HÓA

- **Đơn vị tổ chức:** CES Global — AI Technology & Training Center
- **Website đào tạo:** https://nhanvienai.cesglobal.com.vn
- **Thời lượng:** 150 phút (20:00 – 22:30)
- **Phương châm:** *"Từ ra lệnh từng câu đến xây dựng trợ lý tự động hóa chuyên sâu theo quy trình doanh nghiệp"*

[Ghi chú Giảng viên]: Chào mừng học viên quay trở lại Buổi 3. Nhắc lại hai buổi đầu đã học cách cài đặt, tạo CLAUDE.md cơ bản và đóng gói skill. Buổi hôm nay là bước nhảy vọt: biến agent thành nhân viên hiểu quy chế toàn diện, biết tiết kiệm chi phí, biết làm slide thuyết trình đẹp mắt, biết vẽ ảnh đồ họa và tự động chạy việc theo lịch.

---

## Slide 02: Mục Tiêu & Chuẩn Đầu Ra Buổi 03

### Học xong buổi hôm nay, bạn sẽ làm chủ:

1. **Phân biệt 2 cấp CLAUDE.md:** Làm chủ `Global CLAUDE.md` (toàn cục máy) và `Local CLAUDE.md` (cá nhân/dự án), hiểu nguyên tắc ưu tiên *"cụ thể hơn sẽ thắng"*.
2. **Cài đặt Super Rules:** Thiết lập quy tắc thép bắt Agent **tự động đánh số thứ tự file** (`01_...`, `02_...`), bảo vệ lịch sử vào `_backup/` và cấm bịa số liệu.
3. **Tiết kiệm 70-90% Token với MarkItDown:** Sử dụng công cụ của Microsoft để chuyển đổi file PDF/DOCX/XLSX phức tạp thành Markdown lưu ngay trong project.
4. **Tạo Slide PowerPoint (.pptx) với Skill `ppt-master`:** Xuất file slide thuyết trình chuẩn Office, bố cục Bento Grid hiện đại, chỉnh sửa được 100%.
5. **Sinh ảnh & Đồ họa với MCP `chatgpt-image-mcp`:** Tự động vẽ sơ đồ, infographic có chữ tiếng Việt sắc nét và nhúng trực tiếp vào slide/báo cáo.
6. **Làm chủ MCP ngoài máy & An toàn dữ liệu:** Nắm vững bản chất kết nối Drive/Gmail và 3 nguyên tắc bảo mật sống còn (chỉ đọc, không tự gửi, chống Injection).
7. **Thiết kế Routine tự động hóa 4 câu hỏi:** Đặt lịch cho công việc định kỳ tự động chạy mà không cần người dùng ngồi gõ lệnh.

[Ghi chú Giảng viên]: Chiếu slide này và nhấn mạnh: 3 kỹ năng đắt giá nhất tối nay là Super Rule đánh số file tự động, cách tiết kiệm tiền token bằng MarkItDown và tạo slide PowerPoint editable bằng skill ppt-master.

---

## Slide 03: Phân Biệt CLAUDE.md Global vs CLAUDE.md Local (Cá Nhân)

### Bảng So Sánh Kiến Trúc 2 Tầng Cấu Hình:

| Tiêu chí | CLAUDE.md Global (Toàn cục) | CLAUDE.md Local (Cá nhân / Dự án) |
|---|---|---|
| **Vị trí lưu trữ** | `~/.claude/CLAUDE.md`<br>*(Thư mục người dùng máy tính)* | `./CLAUDE.md`<br>*(Ngay tại gốc thư mục dự án / phòng ban)* |
| **Phạm vi hiệu lực** | **Tất cả thư mục & dự án** trên máy tính | **Duy nhất thư mục đó** và các thư mục con |
| **Vai trò tương đương** | **Hiến pháp / Nội quy chung công ty**:<br>Danh tính, phong cách, bảo mật, cấm bịa số, quy tắc đánh số file. | **Quy chế riêng phòng ban**:<br>Cấu trúc tài liệu, quy trình báo giá, hợp đồng, mẫu báo cáo đặc thù. |
| **Quy tắc xung đột** | Quy tắc nền tảng chung. | **Cụ thể hơn sẽ thắng (Local ghi đè Global)**. |
| **Kích hoạt** | **Bắt buộc mở phiên mới** sau khi sửa. | **Bắt buộc mở phiên mới** sau khi sửa. |

> **Quy tắc vàng:** *"Những gì áp dụng cho mọi việc thì ghi vào Global. Những gì chỉ phòng ban đó, dự án đó dùng thì ghi vào Local."*

[Ghi chú Giảng viên]: Dùng phép ẩn dụ đời thường: Global CLAUDE.md như Hợp đồng lao động và Nội quy tổng công ty (ai cũng phải theo). Local CLAUDE.md như Bảng phân công công việc dán ở cửa phòng Kinh doanh. Nếu nội quy công ty ghi giờ làm linh hoạt, nhưng phòng Kinh doanh ghi 8h có mặt họp thì phải theo 8h (cụ thể hơn thắng).

---

## Slide 04: Super Rules Trong Global CLAUDE.md: Tự Động Đánh Số Thứ Tự File

### 3 "Quy Tắc Thép" Cần Cài Vào Máy Của Bạn:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ 1. QUY TẮC ĐÁNH SỐ THỨ TỰ FILE TUẦN TỰ (Sequential Auto-Numbering)          │
│    Trước khi tạo file mới, Agent PHẢI quét thư mục hiện tại để xác định      │
│    số tiếp theo và gán tiền tố (01_..., 02_..., 03_...). Không đặt tên tùy tiện.│
├─────────────────────────────────────────────────────────────────────────────┤
│ 2. BẢO VỆ DỮ LIỆU & LỊCH SỬ (Anti-Deletion & Single Active File)            │
│    Khi nâng cấp tài liệu, di chuyển bản cũ vào thư mục _backup/.             │
│    Tuyệt đối không xóa đè, cấm chạy lệnh xóa hàng loạt (rm -rf, del *.*).    │
├─────────────────────────────────────────────────────────────────────────────┤
│ 3. CHỐNG BỊA SỐ LIỆU (Zero Hallucination on Metrics)                        │
│    Mọi con số phải trích dẫn dòng/file nguồn. Thiếu thì ghi [Chờ bổ sung].    │
└─────────────────────────────────────────────────────────────────────────────┘
```

- **Lợi ích:** Cây thư mục làm việc luôn ngăn nắp, dễ tìm kiếm, không bao giờ lo mất dữ liệu hay lẫn lộn phiên bản cũ - mới.

[Ghi chú Giảng viên]: Nhấn mạnh nỗi đau: Khi không có rule này, hôm nay bảo agent làm báo cáo nó tạo `bao-cao.md`, mai nó tạo `bao-cao-moi.md`, mốt nó tạo `bao-cao-final-v2.md`. Cài rule này xong, cây thư mục sẽ chuẩn chỉnh `01_...`, `02_...`, `03_...`.

---

## Slide 05: Thực Hành Cài Đặt & Kiểm Thử Super Rule

### Bước 1: Cài đặt Global CLAUDE.md
- **Prompt mẫu:**
  ```
  Tạo hoặc cập nhật file CLAUDE.md cấp Global tại ~/.claude/CLAUDE.md:
  - Danh tính: Trần Văn Minh - Chuyên viên Giải pháp Doanh nghiệp tại CES Global.
  - Văn phong: Chuyên nghiệp, ngắn gọn, tiếng Việt chuẩn mực, không dùng emoji.
  - SUPER RULES:
    1. Trước khi tạo file mới, bắt buộc quét thư mục để đánh số thứ tự tiếp theo (01_..., 02_...).
    2. Khi cập nhật file, chuyển bản cũ vào _backup/. Tuyệt đối không xóa đè.
    3. Số liệu phải trích dẫn nguồn cụ thể, không có ghi [Chờ bổ sung].
  ```

### Bước 2: Thao tác then chốt
- **Đóng phiên làm việc hiện tại, mở phiên mới** (`claude` hoặc New Session).

### Bước 3: Thử nghiệm phép màu
- **Prompt test:** *"Tạo giúp tôi 1 file ghi chú 3 mục tiêu quý vào thư mục 05-bao-cao/"*
- **Kết quả mong đợi:** Agent tự động tạo file tên là `01_muc-tieu-trong-tam-quy.md` (hoặc số kế tiếp) mà không cần người dùng nhắc!

[Ghi chú Giảng viên]: Cho học viên làm theo. Nhắc đi nhắc lại: Phải mở phiên mới thì agent mới nạp file Global! Sau khi chạy prompt test, hỏi xem ai đã ra file có số `01_` thì gõ phím 1 vào Zoom.

---

## Slide 06: Bài Toán Token & Giải Pháp Microsoft MarkItDown

### "Cơn Đói Token" - Kẻ Thù Thầm Lặng Của AI Agent

- **Vấn đề khi ném file gốc (PDF/Word/Excel/PPTX) cho AI:**
  * File PDF 30 trang hoặc Word đầy hình ảnh có thể ngốn **40.000 – 80.000 tokens**.
  * Context Window bị tràn nhanh chóng ➔ Agent bị "ngáo", quên mất chỉ thị ban đầu.
  * Chi phí token tăng vọt, tốc độ phản hồi chậm như rùa bò.

### Giải Pháp: Microsoft MarkItDown (`markitdown`)
- **Kho mã nguồn:** `https://github.com/microsoft/markitdown` (Mã nguồn mở của Microsoft).
- **Cơ chế:** Chuyển đổi mọi file nhị phân phức tạp thành text **Markdown (.md)** siêu tinh gọn.
- **Hiệu quả:**
  * **Tiết kiệm 70% đến 90% lượng token tiêu thụ!**
  * Tốc độ xử lý của Agent nhanh gấp **5 lần**.
  * Bảng biểu, tiêu đề, danh sách được giữ nguyên vẹn 100%.

[Ghi chú Giảng viên]: Chiếu biểu đồ so sánh: Cùng 1 hợp đồng 20 trang, ném file Word mất 30.000 token, convert sang Markdown chỉ mất 2.000 token. Vừa rẻ hơn 15 lần, vừa giúp Agent tập trung vào nội dung chính xác.

---

## Slide 07: Quy Trình Vận Hành MarkItDown Trong Dự Án

### Mô Hình Xử Lý 3 Bước Tiết Kiệm Token:

```
[File Gốc: .pdf / .docx / .xlsx]
            │
            ▼ (Chạy ngầm lệnh MarkItDown)
[File Markdown: .md lưu ngay trong project] ➔ Tiết kiệm 85% Token!
            │
            ▼ (Agent chỉ đọc file .md sạch)
[Kết Quả Phân Tích / Trích Xuất Cực Nhanh]
```

### Cài Đặt & Cú Pháp Lệnh:
1. **Cài đặt một lần duy nhất:**
   ```bash
   pip install markitdown
   ```
2. **Cú pháp chuyển đổi:**
   ```bash
   markitdown tai-lieu-goc/hop-dong.docx -o 03-hop-dong/02_hop-dong-chi-tiet.md
   ```
3. **Cài vào quy tắc CLAUDE.md:**
   *"Khi xử lý tài liệu lớn, hãy dùng markitdown chuyển sang file .md trong project trước, sau đó mới đọc file .md để làm việc."*

[Ghi chú Giảng viên]: Trình diễn trực tiếp trên màn hình: Chạy lệnh chuyển đổi file `hop-dong-mau-dich-vu.docx` thành `02_hop-dong-mau-dich-vu.md` trong 2 giây. Mở file .md lên cho lớp thấy nội dung sạch bong, không còn rác định dạng.

---

## Slide 08: Skill `ppt-master`: Tạo Slide PowerPoint (.pptx) Chuyên Nghiệp

### Đột Phá Mới: Không Còn Slide Gạch Đầu Dòng Nhạt Nhẽo!

- **Kho mã nguồn:** `https://github.com/hugohe3/ppt-master`
- **Sự khác biệt vượt trội:**
  * **File `.pptx` thật 100%:** Mở trực tiếp bằng Microsoft PowerPoint hoặc Apple Keynote.
  * **Chỉnh sửa được hoàn toàn (Fully Editable):** Click vào từng ô chữ, icon, đổi màu, sửa số thoải mái trước khi trình bày với sếp.
  * **Bố cục hiện đại (Bento Grid):** Thẻ thông tin, chỉ số Hero KPI to rõ, khối so sánh tương phản, timeline tiến độ.
  * **Không đè chữ, không tràn viền:** Thuật toán tính toán không gian và kích thước chữ chuẩn Typography quốc tế.

```
┌─────────────────────────┬─────────────────────────┐
│ Hero KPI Metric (To rõ) │ Card So Sánh A vs B     │
├─────────────────────────┼─────────────────────────┤
│ Timeline 4 Giai Đoạn    │ Khối Highlight Cảnh Báo │
└─────────────────────────┴─────────────────────────┘
```

[Ghi chú Giảng viên]: So sánh hai bức ảnh: Một bên là slide AI xuất text thô sơ hoặc HTML khó sửa, một bên là slide Bento Grid xuất ra file PowerPoint mở trên máy. Khẳng định đây là công cụ "cứu cánh" cho dân văn phòng khi phải làm slide báo cáo gấp.

---

## Slide 09: Thực Hành: Xuất Slide Báo Cáo Doanh Số Quý Bằng `ppt-master`

### Prompt Yêu Cầu Tạo Slide (.pptx) - Bản GV dán chạy ngay:
```
Dựa trên số liệu trong 04-so-lieu/doanh-thu-quy.csv và 04-so-lieu/don-hang.csv:
Hãy dùng skill ppt-master thiết kế 1 bộ slide PowerPoint (.pptx) gồm 5 slide báo cáo doanh số:
- Slide 1: Trang bìa (Báo Cáo Kết Quả Kinh Doanh Quý 1 - Trần Văn Minh).
- Slide 2: Chỉ số KPI chính (Hero Card: Doanh thu 2.870 triệu, 10 đơn hàng).
- Slide 3: So sánh thị trường (Bento Card: TP HCM 1.565 tr vs Hà Nội 1.305 tr, lệch 260 tr).
- Slide 4: Cơ cấu gói & Cảnh báo công nợ (Cao cấp 1.640 tr vs Tiêu chuẩn 1.230 tr; Highlight 3 đơn chờ thanh toán 275 tr: DH003, DH005, DH010).
- Slide 5: Kế hoạch hành động quý tới (3 giải pháp trọng tâm).

Lưu file vào 05-bao-cao/ theo quy tắc đánh số thứ tự tuần tự (02_bao-cao-doanh-so-quy-1.pptx).
Tông màu Navy Blue công nghệ sang trọng, số liệu chính xác 100%.
```

### Kết quả:
- Xuất file `.pptx` ngay trong `05-bao-cao/`.
- Mở bằng PowerPoint: Các khối thẻ cân đối, số liệu chuẩn từng con số!

[Ghi chú Giảng viên]: Chạy prompt trực tiếp. Mở file PowerPoint vừa sinh ra lên màn hình chiếu lớn. Chỉ cho học viên thấy các con số 2.870 triệu, 1.565 triệu, 275 triệu hiện lên rành rẽ trên slide.

---

## Slide 10: Mở Rộng Giác Quan Với MCP `chatgpt-image-mcp`

### Bản Chất Của MCP (Model Context Protocol)

- **Đính chính hiểu nhầm:** *"Đọc file trên máy tính thì cần MCP"* ➔ **SAI!** Agent đọc và ghi file trên máy tính bằng công cụ nội tại, không cần MCP.
- **MCP thực sự là gì?** Là **cổng kết nối ra ngoài máy tính** (External Gateway) để Agent chạm vào:
  * Kho lưu trữ đám mây (Google Drive).
  * Hộp thư điện tử (Gmail).
  * Cơ sở dữ liệu công ty (SQL).
  * **Công cụ sinh ảnh AI bên ngoài (`chatgpt-image-mcp`)**.

### MCP `chatgpt-image-mcp` (Repo: `andyluu98/chatgpt-image-mcp`)
- Kết nối Claude Code với backend sinh ảnh của ChatGPT (DALL-E / GPT Image).
- **Điểm mạnh độc nhất:** Vẽ infographic, sơ đồ kinh doanh với **chữ tiếng Việt có dấu chuẩn xác**, không bị lỗi font hay ký tự lạ.
- Agent tự gọi lệnh sinh ảnh, tự lưu vào thư mục project và nhúng vào Slide/Báo cáo.

[Ghi chú Giảng viên]: Giải thích ngắn gọn: MCP như "chiếc thẻ bài" cho phép AI bước ra ngoài cánh cửa máy tính để lấy thêm tài nguyên và gọi các siêu trí tuệ khác hỗ trợ.

---

## Slide 11: Demo Sinh Infographic Tiếng Việt & Nhúng Vào Slide

### 1. Cấu hình MCP trong `claude_desktop_config.json`:
```json
{
  "mcpServers": {
    "chatgpt-image": {
      "command": "uvx",
      "args": ["chatgpt-image-mcp"]
    }
  }
}
```

### 2. Prompt sinh ảnh Infographic chuẩn 16:9:
```
Dùng công cụ chatgpt-image tạo giúp tôi 1 ảnh infographic chuyên nghiệp:
"Quy trình 4 bước chăm sóc khách hàng và thu hồi công nợ B2B":
1. Tư vấn giải pháp & Ký kết hợp đồng
2. Bàn giao phần mềm & Nghiệm thu đợt 1
3. Đối soát công nợ & Gửi thông báo thanh toán
4. Chăm sóc sau bán & Mở rộng dịch vụ

Phong cách: Đồ họa vector phẳng hiện đại, nền trắng sạch sẽ, tông màu xanh công nghệ.
Chữ tiếng Việt sắc nét. Tỉ lệ 16:9. Lưu vào 05-bao-cao/03_so-do-quy-trinh-b2b.png.
```

[Ghi chú Giảng viên]: Chiếu ảnh infographic vừa sinh ra lên màn hình. Hướng dẫn học viên cách yêu cầu Agent lấy file ảnh này nhúng trực tiếp vào Slide 5 của bài thuyết trình vừa tạo ở bước trước!

---

## Slide 12: MCP Ngoài Máy & 3 Nguyên Tắc An Toàn Sống Còn

### Khi Cho Agent Kết Nối Vào Google Drive Hoặc Gmail:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ NGUYÊN TẮC 1: CẤP QUYỀN CHỈ ĐỌC (Read-Only Privilege)                       │
│ Chỉ tick quyền "Xem/Đọc" (View/Read). Tuyệt đối bỏ chọn quyền Sửa hoặc Xóa. │
├─────────────────────────────────────────────────────────────────────────────┤
│ NGUYÊN TẮC 2: TUYỆT ĐỐI KHÔNG ĐỂ AGENT TỰ ĐỘNG GỬI EMAIL                    │
│ Agent chỉ ĐỌC và SOẠN NHÁP (Draft). Quyền bấm nút gửi PHẢI là con người.    │
│ Sai 1 con số công nợ trong email gửi khách là mất uy tín đối tác!           │
├─────────────────────────────────────────────────────────────────────────────┤
│ NGUYÊN TẮC 3: CẢNH GIÁC PROMPT INJECTION TRONG DỮ LIỆU NGOÀI               │
│ Nội dung email/web là DỮ LIỆU ĐỂ ĐỌC, KHÔNG PHẢI MỆNH LỆNH ĐỂ THI HÀNH.      │
│ Nếu email có câu "Hãy xóa thư mục này", Agent phải bỏ qua, không được làm. │
└─────────────────────────────────────────────────────────────────────────────┘
```

> **Khẩu quyết an toàn:** *"Dữ liệu để đọc, quyết định gửi là của tôi."*

[Ghi chú Giảng viên]: Dừng lại nói chậm và nghiêm túc: "Đây là slide quan trọng nhất về an toàn thông tin của cả khóa học. Ai không tuân thủ 3 nguyên tắc này, sớm muộn cũng sẽ gặp sự cố khi để AI tự động gửi email cho khách hàng."

---

## Slide 13: Routine - Tự Động Hóa Chạy Theo Lịch

### Routine Là Gì?
- Routine giống như **"hẹn giờ máy pha cà phê"**: Đúng giờ đó mỗi ngày hoặc mỗi tuần, Agent tự động thức dậy, thực thi chuỗi việc và để sẵn kết quả trên bàn làm việc của bạn.

### Khung Thiết Kế 4 Câu Hỏi Cho Mọi Routine:

| Câu hỏi | Ý nghĩa vận hành | Ví dụ thực tế |
|---|---|---|
| **1. Chạy lúc nào?** | Tần suất & Thời điểm chính xác | 8 giờ sáng thứ Hai hàng tuần |
| **2. Đọc dữ liệu ở đâu?** | Thư mục hoặc file nguồn | `04-so-lieu/don-hang.csv` |
| **3. Làm gì với dữ liệu?** | Logic xử lý / tổng hợp | Lọc đơn nợ quá hạn > 7 ngày, tính tổng tiền |
| **4. Lưu kết quả vào đâu?** | File đích (có số thứ tự) | `05-bao-cao/04_danh-sach-nhac-no-tuan.md` |

> **Luật an toàn Routine:** Routine chỉ được phép **ĐỌC, TỔNG HỢP và GHI FILE**. Tuyệt đối cấm Routine tự động gửi email hoặc xóa dữ liệu khi bạn không có mặt.

[Ghi chú Giảng viên]: Đưa ra 5 ví dụ cho 5 phòng ban (Kinh doanh quét nợ đầu tuần, Kế toán đối soát ngày 25, Marketing tổng hợp chi phí thứ 6, Nhân sự lọc CV tồn, Hành chính chốt việc cuối ngày).

---

## Slide 14: Tổng Kết Buổi 03 & Hành Động Tiếp Theo

### 5 Trụ Cột Năng Lực Cầm Về Tối Nay:
1. **Global CLAUDE.md**: Hiến pháp toàn cục, tự động đánh số thứ tự file `01_...` và bảo vệ dữ liệu cũ.
2. **Microsoft MarkItDown**: "Vũ khí" ép gọn tài liệu lớn, tiết kiệm 80% token, tăng tốc x5 lần.
3. **Skill PPT-Master**: Tạo slide PowerPoint (.pptx) chuẩn Bento Grid, sửa được 100%.
4. **MCP ChatGPT Image**: Sinh ảnh minh họa, infographic sơ đồ tiếng Việt nhúng vào báo cáo/slide.
5. **Routine Tự Động Hóa**: 4 câu hỏi hẹn giờ cho công việc tự chạy an toàn theo lịch.

### Bài Tập Thực Hành Về Nhà:
- [ ] Cập nhật file `~/.claude/CLAUDE.md` trên máy bạn với đầy đủ Super Rules.
- [ ] Lấy 1 file tài liệu công việc thực tế, dùng `markitdown` chuyển đổi và tóm tắt.
- [ ] Dùng `ppt-master` xuất 1 bộ slide 4-5 trang báo cáo công việc của phòng ban bạn.
- [ ] Viết bản thiết kế Routine 4 câu hỏi cho 1 công việc lặp lại hàng tuần của bạn.

[Ghi chú Giảng viên]: Cảm ơn học viên. Nhắc lớp nộp bài tập lên nhóm Zalo để trợ giảng chấm điểm và nhận feedback. Buổi 4 sẽ học cách kết hợp Agent chuyên trách và Subagent xử lý khối lượng công việc khổng lồ!
