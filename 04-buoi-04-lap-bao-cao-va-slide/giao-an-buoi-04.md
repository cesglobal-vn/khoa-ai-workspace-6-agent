# Giáo án Buổi 04: Hoàn Thiện Slide Với MCP ChatGPT Image, Connectors Ngoại Vi, Routine Tự Động Hóa, Cửa Sổ Ngữ Cảnh & Bản Chất Subagent Chuẩn Anthropic

> **Mục tiêu chiến lược Buổi 04:**
> 1. **Gỡ trọn vẹn 3 nội dung nợ từ Buổi 03:**
>    - Nâng cấp bộ Slide học viên đã tạo ở Buổi 3 bằng **MCP `chatgpt-image-mcp`**: Sinh ảnh infographic, sơ đồ trực quan có chữ tiếng Việt sắc nét nhúng thẳng vào slide và báo cáo.
>    - Nắm vững bản chất **MCP & Connectors ngoại vi** (Google Drive, Gmail, Tools) cùng **3 nguyên tắc an toàn dữ liệu sống còn**.
>    - Thiết kế và vận hành **Routine tự động hóa chạy theo lịch trình** ("Hẹn giờ nồi cơm điện" cho Agent).
> 2. **Giải phẫu chuyên sâu Subagent theo chuẩn kỹ thuật của Anthropic:**
>    - Hiểu bản chất **Agent** (LLM tự điều khiển vòng lặp công cụ) vs **Workflow** (quy trình code sẵn) vs **Subagent** (phiên bản độc lập chạy trong context riêng).
>    - Nắm vững **Ranh giới Context (Context Boundary)**: Cách ly 100%, kênh giao tiếp một chiều qua prompt giao việc, output trung gian tự hủy.
>    - Ẩn dụ kinh điển: *"Trưởng phòng & Tờ giấy giao việc"*.
>    - 2 giới hạn cứng: Không có ủy quyền lồng nhau (No nested subagents) & Không thể hỏi lại người dùng giữa chừng.
>    - Nắm vững **khi nào dùng Subagent** (Output lớn nhưng kết luận nhỏ, "đi tìm X rồi báo đáp án", tránh ô nhiễm context) và **khi nào giữ ở Agent chính** (cần trao đổi qua lại, sửa file, cần người duyệt).
> 3. **Thực hành bốc vác dữ liệu thô:** Cho Subagent quét 5 hồ sơ CV trong `demo/pdf/01-ung-vien/` (hoặc `demo/md/01-ung-vien/`) tuyển nhân sự giao vận Hà Nội cho tháng 4, giữ cửa sổ chính sạch bong để xuất Báo cáo kết quả kinh doanh.

---

## Thông tin buổi học
- **Buổi:** 04 / 6 (Theo lộ trình khóa AI Workspace 6 Agent)
- **Thời lượng:** 150 phút (2,5 giờ)
- **Đối tượng:** Khối văn phòng, kinh doanh, nhân sự, kế toán, quản lý vận hành (người mới bắt đầu với AI, không cần biết code).
- **Bộ file demo làm việc:** `04-buoi-04-lap-bao-cao-va-slide/demo/`
- **Tài liệu tham chiếu chuẩn quốc tế:** 
  * Anthropic: *Building Effective Agents* (anthropic.com/engineering/building-effective-agents)
  * Anthropic: *When to use multi-agent systems* (claude.com/blog/building-multi-agent-systems-when-and-how-to-use-them)
  * Claude Code Official Docs: *Subagents & Context Isolation* (code.claude.com/docs/en/sub-agents)

---

## Nhân vật & Bối cảnh demo xuyên suốt buổi

Để câu chuyện mạch lạc và kế thừa trực tiếp từ Buổi 3:

| Mục | Giá trị chuẩn bị cho Prompt Demo |
|---|---|
| **Nhân vật** | **Trần Văn Minh** — Chuyên viên Giải pháp Doanh nghiệp tại Công ty Cổ phần Công nghệ CES |
| **Cấp trên** | Chị Lan, Trưởng phòng Kinh doanh (xưng "em", gọi "chị") |
| **Bối cảnh thực tế** | Kết thúc tháng 3, Minh vừa có số liệu bán hàng và bộ khung slide báo cáo từ Buổi 3. Minh cần: (1) Vẽ sơ đồ quy trình chăm sóc khách hàng nhúng vào slide; (2) Soạn nháp email đối soát công nợ qua kết nối ngoài an toàn; (3) Hẹn Routine tự động tổng hợp số liệu vào sáng thứ Hai; (4) Tuyển gấp 1 nhân sự giao vận Hà Nội bằng cách giao Subagent lọc 5 CV; (5) Lập Báo cáo điều hành gửi chị Lan mà không làm rác cửa sổ chat. |

---

## Bộ dữ liệu thực hành & Số liệu "Chống bịa" của Buổi 4

Thư mục: `04-buoi-04-lap-bao-cao-va-slide/demo/`
```
demo/
├── md/                                  (Dữ liệu thực hành định dạng Markdown)
│   ├── so-lieu-ban-hang-thang.md        (Số liệu bán hàng tháng 3 thô của Minh)
│   ├── yeu-cau-nghien-cuu.md            (Đề bài nghiên cứu thị trường cho Buổi 5)
│   └── 01-ung-vien/                     (5 hồ sơ ứng viên dạng Markdown)
│       ├── cv-nguyen-van-nam.md         (28 tuổi, 3 năm Viettel Post, lương 9-11 tr)
│       ├── cv-tran-thi-hoa.md           (26 tuổi, 2 năm điều phối GHTK, chỉ làm điều phối)
│       ├── cv-le-van-hung.md            (31 tuổi, 4 năm Điện Máy Xanh, kỹ thuật + giao hàng)
│       ├── cv-pham-thi-lan.md           (24 tuổi, 1 năm Shopee Xpress, chỉ trực hotline)
│       └── cv-do-van-minh.md            (27 tuổi, 2 năm giao chứng từ chuỗi An Khang)
└── pdf/                                 (Dữ liệu thực hành định dạng PDF chuẩn in ấn)
    ├── so-lieu-ban-hang-thang-3.pdf     (Bản PDF chuẩn báo cáo in ấn có bảng biểu số liệu)
    ├── yeu-cau-nghien-cuu-thi-truong.pdf (Bản PDF phiếu yêu cầu nghiên cứu thị trường)
    └── 01-ung-vien/                     (5 hồ sơ ứng viên dạng PDF chuẩn in ấn A4)
        ├── cv-nguyen-van-nam.pdf
        ├── cv-tran-thi-hoa.pdf
        ├── cv-le-van-hung.pdf
        ├── cv-pham-thi-lan.pdf
        └── cv-do-van-minh.pdf
```

### Bộ số liệu kiểm định GV bắt buộc thuộc để soi bài học viên:
1. **File `demo/md/so-lieu-ban-hang-thang.md` (hoặc `demo/pdf/so-lieu-ban-hang-thang-3.pdf`)**:
   - Tổng doanh thu tháng 3: **1.085 triệu đồng** (Tháng 2 là **915 triệu**, tăng trưởng: **170 triệu ~ 18.6%**).
   - Thị trường: **TP HCM bán tốt hơn Hà Nội**, nhất là Gói Cao cấp.
   - Công nợ tồn đọng: **2 đơn chờ thanh toán** (`An Phát`, `Đại Tín`).
   - Đơn hủy: **1 đơn** (`Hải Nam`).
   - Tín hiệu bán chéo: Khách hàng `Minh Long` mua thêm Gói Tiêu chuẩn.
   - Vướng mắc then chốt: **Thiếu nhân sự giao vận ở Hà Nội** làm ảnh hưởng tiến độ bàn giao.
2. **Thư mục `01-ung-vien/`**:
   - Có đúng **5 ứng viên**.
   - Ứng viên phù hợp nhất cho vị trí giao hàng thực địa Hà Nội: `Nguyễn Văn Nam` (chuẩn giao hàng Viettel Post) và `Lê Văn Hùng` (giao hàng kiêm kỹ thuật phần cứng).
   - Ứng viên không phù hợp đi xe máy giao hàng: `Trần Thị Hoa` (chỉ nhận điều phối) và `Phạm Thị Lan` (chỉ trực tổng đài).

---

## Timeline chi tiết buổi học (150 phút)

| Mốc thời gian | Thời lượng | Khối nội dung | Trọng tâm sư phạm & Sản phẩm đầu ra |
|---|---|---|---|
| **00:00 - 00:10** | 10 phút | **K0: Mở đầu & Định vị Buổi 4** | Nối mạch từ Buổi 3 sang Buổi 4; đặt bài toán hoàn thiện Báo cáo, Slide & Tự động hóa. |
| **00:10 - 00:35** | 25 phút | **K1: MCP ChatGPT Image** | Cài đặt/kết nối MCP Image; sinh Infographic quy trình 4 bước tiếng Việt sắc nét nhúng vào Slide Buổi 3. |
| **00:35 - 01:00** | 25 phút | **K2: Bản chất Connectors & MCP Ngoài máy** | Phân biệt Local vs Ngoại vi (Drive, Gmail, Web); 3 nguyên tắc an toàn dữ liệu sống còn. |
| **01:00 - 01:25** | 25 phút | **K3: Thiết kế Routine Tự Động Hóa** | Khung 4 câu hỏi định hình mọi Routine; đặt lịch tự động tổng hợp số liệu 8h sáng thứ Hai. |
| **01:25 - 01:35** | 10 phút | **Nghỉ giải lao** | Trợ giảng hỗ trợ học viên gặp lỗi môi trường hoặc tài khoản MCP. |
| **01:35 - 02:05** | 30 phút | **K4: Giải mã Subagent chuẩn Anthropic** | Ranh giới Context cô lập; ẩn dụ "Tờ giấy giao việc"; 2 giới hạn cứng; khi nào dùng Subagent vs Agent chính. |
| **02:05 - 02:20** | 15 phút | **K5: Thực hành Subagent & Xuất Báo Cáo** | Cho Subagent quét 5 CV không chật bàn chính; Agent chính xuất Báo cáo kinh doanh chuẩn công sở. |
| **02:20 - 02:30** | 10 phút | **K6: Tổng kết & Hướng về Buổi 5** | Đối soát 3 câu hỏi cốt lõi; giao bài tập; hé lộ bài toán Đội ngũ Multi-Agent (song song & chi phí). |

---

## Kịch bản chi tiết từng phần

```
================================================================================
K0: MỞ ĐẦU & ĐỊNH VỊ BẢN ĐỒ NĂNG LỰC BUỔI 04 (10 PHÚT)
================================================================================
```

### Lời dẫn Giảng viên (Đọc nguyên văn):
> "Chào cả lớp. Ở Buổi 3, chúng ta đã xuất được bộ khung Slide thuyết trình từ số liệu bán hàng. Nhưng slide mới chỉ có chữ và số thô, chưa có hình ảnh sơ đồ quy trình trực quan. Hơn nữa, AI của anh chị mới chỉ làm việc cục bộ trong ổ cứng máy tính, chưa vươn ra ngoài Google Drive hay Gmail, và hàng tuần anh chị vẫn phải ngồi gõ lệnh thủ công.
> 
> Tối nay, chúng ta hoàn thiện 3 vũ khí tự động hóa:
> 1. Dùng **MCP ChatGPT Image** vẽ Infographic quy trình có chữ tiếng Việt sắc nét đập ngay vào slide.
> 2. Mở rộng giác quan với **Connectors & MCP ngoài máy** (Drive, Gmail) cùng **3 luật thép bảo mật** tránh rò rỉ dữ liệu.
> 3. Cài đặt **Routine** tự động hóa theo lịch ("Hẹn giờ nồi cơm điện").
> 
> Và trọng tâm đột phá của tối nay: Chúng ta sẽ đi sâu vào **Kiến trúc Subagent chuẩn của Anthropic** — bí quyết giúp các kỹ sư AI xử lý khối lượng tài liệu khổng lồ mà không bao giờ bị tràn bộ nhớ hay làm 'ngáo' AI. Bắt đầu thôi!"

---

```
================================================================================
K1: MCP CHATGPT IMAGE — SINH ẢNH MINH HỌA & HOÀN THIỆN SLIDE (25 PHÚT)
================================================================================
```

### 1. Bản chất công cụ: Vì sao cần MCP `chatgpt-image-mcp`?
- **Nỗi đau**: Muốn vẽ sơ đồ, infographic có chữ tiếng Việt thì hầu hết AI tạo ảnh đều bị lỗi font, sai dấu, méo chữ. Ngoài ra, việc tải ảnh thủ công từ web rồi chèn vào slide rất tốn thời gian.
- **Giải pháp**: MCP `chatgpt-image-mcp` kết nối trực tiếp Claude Code với engine đồ họa của ChatGPT Image / DALL-E 3:
  * Sinh ảnh ngay trong dòng lệnh Claude Code.
  * Hiển thị **chữ tiếng Việt có dấu chuẩn xác**, sắc nét.
  * Tự lưu ảnh `.png` vào thư mục dự án có đánh số thứ tự tuần tự `01_...`.
  * Agent tự động chèn ảnh vào Slide PowerPoint hoặc file Markdown/HTML.

### 2. Kiểm tra công cụ & Thực hành Demo GV:
- **PROMPT K1-1 (Kiểm tra kết nối):**
  ```text
  Kiểm tra giúp tôi công cụ tạo ảnh chatgpt-image đã sẵn sàng hoạt động chưa?
  ```
- **PROMPT K1-2 (Tạo Infographic quy trình B2B tỉ lệ 16:9) - Bản GV dán chạy ngay:**
  ```text
  Sử dụng công cụ chatgpt-image để tạo cho tôi một hình ảnh đồ họa infographic chuyên nghiệp minh họa: "Quy trình 4 bước chăm sóc khách hàng và thu hồi công nợ chuẩn B2B":
  - Bước 1: Tư vấn giải pháp & Ký kết hợp đồng
  - Bước 2: Bàn giao phần mềm & Nghiệm thu đợt 1
  - Bước 3: Đối soát công nợ & Gửi thông báo thanh toán
  - Bước 4: Chăm sóc sau bán & Mở rộng gói dịch vụ

  Yêu cầu phong cách: Đồ họa vector phẳng hiện đại (Modern Flat Vector / Corporate Infographic), nền trắng sạch sẽ, tông màu xanh dương công nghệ cao cấp, các nhãn chữ tiếng Việt hiển thị rõ ràng, sắc nét có dấu.
  Tỉ lệ ảnh 16:9. Lưu ảnh vào thư mục 05-bao-cao/ theo đúng Super Rule tự động đánh số thứ tự tuần tự (ví dụ: 03_so-do-quy-trinh-b2b.png).
  ```

- **PROMPT K1-3 (Chèn ảnh vào Slide đã tạo ở Buổi 3):**
  ```text
  Hãy chèn hình ảnh vừa tạo vào slide cuối cùng của file bài thuyết trình (.pptx hoặc .html) trong thư mục báo cáo.
  ```

---

```
================================================================================
K2: BẢN CHẤT CONNECTORS & MCP NGOÀI MÁY — 3 LUẬT THÉP BẢO MẬT (25 PHÚT)
================================================================================
```

### 1. Phân biệt rạch ròi: Trong máy vs Ngoài máy
- **File trên máy tính (Local):** Claude Code tự đọc/ghi bằng công cụ hệ thống nội tại (Read, Write, Grep, Glob). **KHÔNG CẦN MCP!**
- **Tài nguyên ngoài máy (External):** Google Drive, Gmail, CRM, Database $\rightarrow$ **BẮT BUỘC DÙNG MCP / CONNECTOR** làm cầu nối.

### 2. Ba luật thép an toàn thông tin (Bắt buộc ghi vào sổ tay):
1. **Luật 1 — Quyền "Chỉ đọc" (Read-Only):** Cấp quyền kết nối Drive/Database chỉ để Xem/Đọc. Tuyệt đối không cấp quyền Sửa/Xóa.
2. **Luật 2 — Nguyên tắc "Không bao giờ để AI tự bấm gửi":** AI chỉ được phép **Đọc $\rightarrow$ Tổng hợp $\rightarrow$ Soạn nháp (Draft)**. Nút bấm gửi email hoặc duyệt tiền 100% phải do con người bấm.
3. **Luật 3 — Cảnh giác Prompt Injection:** Nội dung email/tài liệu của đối tác là dữ liệu thụ động để phân tích, không phải là mệnh lệnh để Agent thi hành.

- **PROMPT K2-1 (Soạn nháp email đối soát công nợ an toàn):**
  ```text
  Dựa trên thông tin công nợ trong demo/md/so-lieu-ban-hang-thang.md:
  Khách hàng Công ty An Phát đang có đơn hàng chờ thanh toán kéo dài cần nhắc nhở.
  Hãy soạn giúp tôi một bản nháp email chuyên nghiệp gửi chị Kế toán trưởng bên An Phát:
  - Mục đích: Nhắc nhở lịch đối soát và đề nghị hoàn tất thanh toán trước ngày 05/04.
  - Văn phong: Nhã nhặn, tôn trọng quan hệ đối tác, rõ ràng thời hạn.
  - Ký tên: Trần Văn Minh - Phòng Kinh doanh, Công ty Cổ phần Công nghệ CES.

  LƯU Ý BẢO MẬT: CHỈ xuất bản nháp ra màn hình để tôi duyệt. Tuyệt đối KHÔNG tự ý gửi email hay tương tác với hệ thống gửi thư.
  ```

---

```
================================================================================
K3: THIẾT KẾ ROUTINE TỰ ĐỘNG HÓA CHẠY THEO LỊCH (25 PHÚT)
================================================================================
```

### 1. Routine là gì? "Hẹn giờ nồi cơm điện" cho Agent
- **Khung 4 câu hỏi định hình mọi Routine:**
  1. *Chạy lúc nào?* (Ví dụ: 08:00 sáng Thứ Hai hàng tuần).
  2. *Đọc dữ liệu ở đâu?* (Ví dụ: `demo/md/so-lieu-ban-hang-thang.md` hoặc `demo/pdf/so-lieu-ban-hang-thang-3.pdf`).
  3. *Làm gì với dữ liệu?* (Lọc đơn tồn đọng, tính doanh thu tăng trưởng).
  4. *Lưu kết quả vào đâu?* (Lưu file `.md` vào thư mục báo cáo có số thứ tự tự động).
- **Quy tắc an toàn:** Routine chỉ được **ĐỌC, TÍNH TOÁN và LƯU BÁO CÁO**. Tuyệt đối không tự ý gửi thư hay xóa dữ liệu.

- **PROMPT K3-1 (Thiết lập Routine tự động tổng hợp thứ Hai):**
  ```text
  Hãy thiết lập cho tôi một Routine tự động hóa theo đúng khung 4 câu hỏi:
  1. Lịch chạy: Vào lúc 08:00 sáng thứ Hai hàng tuần.
  2. Nguồn dữ liệu: Đọc file demo/md/so-lieu-ban-hang-thang.md.
  3. Xử lý: Lọc toàn bộ các khách hàng có đơn chờ thanh toán và khách hủy đơn, tính tổng doanh thu và tỷ lệ tăng trưởng so với tháng trước.
  4. Đầu ra: Lưu thành file markdown trong thư mục 05-bao-cao/ theo đúng quy tắc đánh số tự động của Global CLAUDE.md.
  Ràng buộc an toàn: Chỉ đọc và lưu báo cáo nội bộ, không gửi email, không chỉnh sửa file nguồn.
  ```

---

```
================================================================================
NGHỈ GIẢI LAO (10 PHÚT) — 01:25 ĐẾN 01:35
================================================================================
```

---

```
================================================================================
K4: GIẢI MÃ SUBAGENT CHUẨN ANTHROPIC — RANH GIỚI CONTEXT & TỜ GIẤY GIAO VIỆC (30 PHÚT)
================================================================================
```

### 1. Định nghĩa chuẩn xác từ Anthropic (*Building Effective Agents*):
Giảng viên viết lên bảng 3 khái niệm để học viên phân biệt rõ:
- **Workflow (Quy trình):** Các hệ thống mà LLM và công cụ được điều phối theo các đường đi cố định viết sẵn bằng code (ví dụ: chuỗi If/Else, Prompt Chaining cố định).
- **Agent:** Hệ thống mà **LLM tự điều khiển quy trình và cách dùng công cụ trong một vòng lặp (loop)**, tự suy nghĩ (Reasoning) $\rightarrow$ tự chọn công cụ $\rightarrow$ tự quan sát kết quả $\rightarrow$ tự quyết định bước tiếp theo để hoàn thành mục tiêu.
- **Subagent (Agent con):** Là một phiên bản Claude riêng biệt do Agent chính tạo ra để xử lý một công việc có phạm vi rõ ràng. Nó chạy trong **Context Window riêng biệt, với System Prompt riêng và quyền dùng công cụ riêng**. Nó làm phần việc "ồn ào" (đọc quét, lội bùn dữ liệu thô) bên trong context của nó và **chỉ trả về một bản tóm tắt kết quả**.

### 2. Khác biệt cốt lõi: Ranh giới Context (Context Boundary)

> **ĐÂY LÀ ĐIỂM DỄ HIỂU SAI NHẤT TRONG LẬP TRÌNH AGENT!**

1. **Cách ly hoàn toàn (Isolated Context):** 
   - Subagent bắt đầu với một context **hoàn toàn mới, sạch tinh 100%**.
   - Nó **KHÔNG THẤY** lịch sử hội thoại của bạn với Agent chính từ đầu buổi đến giờ.
   - Nó **KHÔNG THẤY** các file mà Agent chính đã từng mở trước đó.
2. **Kênh giao tiếp duy nhất: "Tờ giấy giao việc":**
   - Kênh duy nhất từ Agent chính sang Subagent là **đoạn prompt giao việc**.
   - Nếu Subagent cần đường dẫn file, thông báo lỗi hay quyết định đã chốt, **thông tin đó bắt buộc phải nằm trong prompt giao việc**. Nếu trên "tờ giấy" không ghi, Subagent hoàn toàn mù tịt!
3. **Chiều ngược lại cực kỳ hẹp:**
   - **Chỉ tin nhắn cuối cùng** của Subagent được gửi trả về cho Agent chính.
   - Mọi lệnh gọi công cụ trung gian, các file đã đọc, log rác... **đều bị giữ lại trong context của Subagent và tự hủy khi kết thúc**.
   - Bàn làm việc của Agent chính chỉ nhận được đúng 1 mẩu giấy kết quả, hoàn toàn sạch sẽ!

### 3. Ẩn dụ kinh điển khi dạy: "Trưởng phòng & Tờ giấy giao việc"
- **Agent chính** là **Trưởng phòng** (đang họp trực tiếp với bạn - Giám đốc).
- **Subagent** là **Nhân viên cấp dưới** được giao việc qua **một tờ giấy**.
- Nhân viên này không được vào phòng họp, không nghe được cuộc họp nãy giờ. Cậu ấy chỉ đọc những gì Trưởng phòng ghi trên tờ giấy, sang phòng bên cạnh cày cuốc, rồi nộp lại đúng một tờ báo cáo kết quả.

### 4. Hai giới hạn cứng của Subagent (Bắt buộc phải biết):
1. **Subagent KHÔNG THỂ sinh subagent khác:** Không có ủy quyền lồng nhau (No nested subagents). Subagent chỉ là cấp thi hành cuối cùng.
2. **Subagent KHÔNG THỂ hỏi lại người dùng để làm rõ:** Subagent chạy nền sẽ **tự động từ chối mọi thao tác cần xin phép (permission)**. Vì vậy, prompt giao việc phải rõ ràng, độc lập, không đòi hỏi tương tác giữa chừng.

### 5. Khi nào dùng Subagent vs Khi nào chỉ dùng một Agent chính?

Theo báo cáo nghiên cứu của Anthropic (*When to use multi-agent systems*):

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                 QUY TẮC NGÓN TAY CÁI CỦA ANTHROPIC:                         │
│                                                                             │
│ "Nếu mô tả được việc là: 'ĐI TÌM X RỒI BÁO TÔI ĐÁP ÁN' ──> DÙNG SUBAGENT.   │
│  Không cần sửa gì, không cần quyết định giữa chừng, output lớn nhưng        │
│  kết luận nhỏ. Giữ cho context không bị ô nhiễm."                           │
└─────────────────────────────────────────────────────────────────────────────┘
```

| Tình huống | Nên dùng | Lý do kỹ thuật theo chuẩn Anthropic |
|---|---|---|
| **Điều tra, phân tích, tóm tắt** từ nhiều file thô | **Subagent** | Việc nặng, tạo nhiều output rác không dùng lại; Subagent gánh hết để tránh ô nhiễm context chính. |
| **Tìm kiếm độc lập** trong nhiều thư mục/module | **Subagent** (Chạy song song) | Tách thành các nhánh độc lập, chạy nhanh hơn. |
| **Sửa file code, chỉnh sửa tài liệu thực tế** | **Agent chính** | Cần sự phê duyệt (permission) trực tiếp từ người dùng; Subagent chạy nền sẽ bị chặn nếu cần quyền sửa. |
| **Việc cần trao đổi qua lại, lặp lại nhiều lần** | **Agent chính** | Subagent khởi động từ đầu tốn thời gian gom lại context; Agent chính giữ context liên tục để trao đổi. |
| **Cần người dùng ra quyết định giữa chừng** | **Agent chính** | Subagent không thể dừng lại hỏi người dùng. |

> **Câu chốt khắc sâu cho lớp:**  
> *"Việc tìm hiểu rộng, độc lập, output lớn nhưng kết luận nhỏ $\rightarrow$ DÙNG SUBAGENT.  
> Việc gắn chặt, cần lặp lại, cần bạn quyết định giữa chừng $\rightarrow$ GIỮ Ở AGENT CHÍNH."*

---

```
================================================================================
K5: THỰC HÀNH SUBAGENT & XUẤT BÁO CÁO KINH DOANH (15 PHÚT)
================================================================================
```

### 1. Thực hành điều phối Subagent: "Tờ giấy giao việc chuẩn 3 thành phần"
- **Tình huống thực tế:** Trong file `demo/md/so-lieu-ban-hang-thang.md`, Trần Văn Minh ghi chú: *"Thiếu nhân sự giao hàng ở Hà Nội... Kế hoạch tháng 4: Tuyển thêm 1 nhân sự giao hàng Hà Nội"*. Thư mục `demo/pdf/01-ung-vien/` (và bản `demo/md/01-ung-vien/`) có 5 file CV.
- Đây là bài toán kinh điển: **Output lớn (5 CV dài hàng nghìn từ) nhưng kết luận nhỏ (chọn 2 người). Giao cho Subagent!**

- **PROMPT K5-1 (Bản GV dán chạy ngay):**
  ```text
  Dùng một subagent đọc toàn bộ 5 file hồ sơ ứng viên trong thư mục demo/pdf/01-ung-vien/ (hoặc demo/md/01-ung-vien/).
  Yêu cầu subagent:
  1. Đánh giá từng ứng viên dựa trên tiêu chí: Tuyển nhân viên giao vận Hà Nội (cần người trực tiếp đi xe máy giao hàng nội thành, chăm chỉ, có kinh nghiệm thực địa, mức lương dưới 12 triệu).
  2. Trả về đúng 1 bảng tổng hợp gồm các cột: Tên ứng viên, Năm sinh, Kinh nghiệm chính, Mức lương kỳ vọng, Đánh giá (Phù hợp / Không phù hợp) và Lý do ngắn gọn.
  3. Đề xuất chọn ra 2 ứng viên sáng giá nhất để mời phỏng vấn vòng 1.

  QUY TẮC BẮT BUỘC: Chỉ trả về bảng tổng hợp và đề xuất ngắn gọn. Tuyệt đối không đổ nguyên văn nội dung từng file CV vào cuộc trò chuyện chính.
  ```

> 💡 **Ghi chú Giảng viên:** Học viên có thể chỉ định đọc trực tiếp 5 file `.pdf` (`demo/pdf/01-ung-vien/*.pdf`) hoặc 5 file `.md` (`demo/md/01-ung-vien/*.md`). Thư mục đã phân loại rạch ròi 2 định dạng để học viên cọ xát với tình huống thực tế tại doanh nghiệp (ứng viên gửi CV dạng PDF).

- **KẾT QUẢ MONG ĐỢI & ĐỐI SOÁT:**
  * Subagent đọc 5 file (dù là PDF hay MD) ở context riêng.
  * Chỉ trả về đúng 1 bảng 5 dòng và đề xuất chọn: `Nguyễn Văn Nam` (chuẩn giao hàng Viettel Post) và `Lê Văn Hùng` (giao hàng kiêm kỹ thuật).
  * Phiên chat chính không chứa một chữ thừa thãi nào từ 5 bản CV!

### 2. Agent chính xuất Báo cáo điều hành hoàn chỉnh
Sau khi Subagent đã mang kết quả sạch về, Agent chính kết hợp số liệu tháng 3 + kết quả chọn ứng viên để xuất Báo cáo gửi chị Lan:

- **PROMPT K5-2 (Xuất Báo cáo quản trị):**
  ```text
  Dựa trên số liệu bán hàng trong demo/md/so-lieu-ban-hang-thang.md (hoặc demo/pdf/so-lieu-ban-hang-thang-3.pdf) và kết quả sàng lọc ứng viên giao vận vừa rồi, hãy soạn Báo cáo Kết quả Kinh doanh Tháng 3 gửi chị Lan Trưởng phòng:
  - Cấu trúc: Tiêu đề trang trọng, Tóm tắt điều hành (3 chỉ số chính), Chi tiết doanh thu theo thị trường & sản phẩm, Cảnh báo công nợ (An Phát, Đại Tín, Hải Nam), và Kế hoạch hành động tháng 4 (đẩy mạnh Gói Cao cấp, phương án phỏng vấn 2 ứng viên Nam và Hùng).
  - Văn phong công sở trang trọng, KHÔNG DÙNG EMOJI, số liệu trích dẫn chính xác 100%.
  - Lưu file vào thư mục 05-bao-cao/ theo đúng Super Rule tự động đánh số thứ tự tuần tự (ví dụ: 04_bao-cao-kinh-doanh-thang-3.md).
  ```

---

```
================================================================================
K6: TỔNG KẾT, ĐỐI SOÁT 3 CÂU HỎI CỐT LÕI & HƯỚNG VỀ BUỔI 5 (10 PHÚT)
================================================================================
```

### 1. Ba câu hỏi kiểm tra độ hiểu bài ngay tại lớp (Gõ ô Chat Zoom):
1. *"Vì sao nói kênh giao tiếp từ Agent chính sang Subagent giống như 'tờ giấy giao việc'?"*
   - **Đáp án:** Vì Subagent có Context cách ly hoàn toàn, không thấy lịch sử chat trước đó; mọi thông tin cần thiết bắt buộc phải ghi rõ trong prompt giao việc.
2. *"Hai giới hạn cứng của Subagent là gì?"*
   - **Đáp án:** Không thể sinh subagent lồng nhau (no nested subagents) và không thể dừng lại hỏi người dùng giữa chừng.
3. *"Khi nào nên dùng Subagent và khi nào nên giữ ở Agent chính?"*
   - **Đáp án:** Việc điều tra, đọc nhiều file, output lớn nhưng kết luận nhỏ $\rightarrow$ Subagent. Việc cần trao đổi qua lại, cần duyệt sửa file $\rightarrow$ Agent chính.

### 2. Bài tập về nhà:
1. Hoàn thiện bài thuyết trình có chèn ảnh Infographic sinh từ MCP Image.
2. Lấy một thư mục 3-5 tài liệu thật trong máy tính của bạn, dùng Subagent với prompt chuẩn "tờ giấy giao việc" để rút ra bảng tóm tắt 1 trang.
3. Soạn khung 4 câu hỏi Routine tự động cho công việc tuần tới của bạn.

### 3. Teaser đỉnh cao kết nối sang Buổi 05:
> *"Tối nay anh chị đã hiểu sâu sắc về ranh giới Context của Subagent đơn lẻ. Nhưng khi bước vào các bài toán lớn của doanh nghiệp, chúng ta cần nhiều Agent chuyên môn phối hợp cùng lúc.  
> Buổi 5 chúng ta sẽ trả lời bài toán hóc búa nhất: **Khi nào nhiều Agent thực sự tốt hơn một Agent? Mô hình phối hợp Song song và Nối chuỗi vận hành ra sao? Và bài toán chi phí token 1x vs 4x vs 15x được tính toán thế nào để đem lại hiệu quả vượt trội tới 90.2%?** Hẹn gặp cả lớp ở Buổi 5!"*

---

## Bảng tra cứu nhanh các Prompt của Buổi 4

| Mã Prompt | Mục đích sử dụng | Vị trí trong bài | Kết quả kiểm định mong đợi |
|---|---|---|---|
| **K1-1** | Kiểm tra trạng thái MCP `chatgpt-image` | [K1: 00:10 - 00:35] | Xác nhận tool tạo ảnh đã sẵn sàng |
| **K1-2** | Dùng MCP vẽ Infographic quy trình 4 bước B2B | [K1: 00:10 - 00:35] | Xuất file `.png` 16:9 sắc nét, chữ tiếng Việt chuẩn |
| **K1-3** | Chèn ảnh vào slide thuyết trình Buổi 3 | [K1: 00:10 - 00:35] | Gắn ảnh tự động vào trang slide cuối |
| **K2-1** | Soạn nháp email nhắc nợ đối tác an toàn | [K2: 00:35 - 01:00] | Chỉ in bản nháp ra màn hình, không kích hoạt gửi |
| **K3-1** | Thiết lập Routine tự động tổng hợp số liệu thứ Hai | [K3: 01:00 - 01:25] | Lên lịch chạy 08:00 sáng thứ Hai, lưu file có số |
| **K5-1** | Gọi Subagent quét 5 CV tuyển nhân sự giao vận | [K5: 02:05 - 02:20] | Bảng so sánh 5 dòng, bàn chính không bị lấp đầy |
| **K5-2** | Agent chính xuất Báo cáo quản trị tháng 3 | [K5: 02:05 - 02:20] | Xuất file báo cáo chuẩn công sở, không emoji |
