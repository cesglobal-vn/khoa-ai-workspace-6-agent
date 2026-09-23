# BỘ SLIDE BÀI GIẢNG BUỔI 04: HOÀN THIỆN SLIDE, CONNECTORS NGOẠI VI, ROUTINE TỰ ĐỘNG HÓA & BẢN CHẤT SUBAGENT CHUẨN ANTHROPIC

> **Đơn vị đào tạo:** CES Global — Trung tâm Đào tạo & Ứng dụng Công nghệ  
> **Chương trình:** Khóa AI Workspace — Làm chủ 6 AI Agent Thực Chiến với Claude Code  
> **Thời lượng:** 150 phút (2,5 giờ) | Live Zoom & VIP LMS  
> **Tài liệu tham chiếu chuẩn:** *Building Effective Agents* (Anthropic) & *Claude Code Subagent Docs*

---

## Slide 01: Slide Tiêu Đề

# KHÓA HỌC: AI WORKSPACE
## Làm Chủ 6 AI Agent Thực Chiến Với Claude Code

### BUỔI 04: HOÀN THIỆN SLIDE VỚI MCP CHATGPT IMAGE, CONNECTORS NGOẠI VI, ROUTINE TỰ ĐỘNG HÓA & BẢN CHẤT SUBAGENT CHUẨN ANTHROPIC

- **Đơn vị tổ chức:** CES Global — AI Technology & Training Center
- **Giảng viên:** Lưu Tuấn Anh · CES Lead Trainer
- **Thời lượng:** 150 phút (20:00 – 22:30)
- **Phương châm:** *"Từ hỏi-đáp đơn lẻ sang điều phối Subagent bốc vác việc nặng và tự động hóa vận hành định kỳ"*

[Ghi chú Giảng viên]: Chào mừng học viên quay trở lại Buổi 4! Buổi trước cả lớp đã tạo được bộ khung Slide thuyết trình. Tối nay chúng ta sẽ mở rộng năng lực toàn diện: Vẽ infographic tiếng Việt đập vào slide, cắm connectors an toàn, hẹn giờ Routine 24/7, và làm chủ ranh giới Context cô lập của Subagent chuẩn Anthropic!

---

## Slide 02: Mục Tiêu & Bản Đồ Năng Lực Buổi 04

### 5 Mảnh Ghép Chuyển Hóa Tự Động Hóa Tối Nay:

1. **MCP `chatgpt-image-mcp`:** Sinh hình ảnh infographic, sơ đồ quy trình 16:9 có chữ tiếng Việt chuẩn sắc nét để chèn vào slide và báo cáo.
2. **Connectors & MCP ngoài máy:** Phân biệt rõ Local File (không cần MCP) vs Đám mây (Drive, Gmail). Nắm vững 3 luật thép bảo mật: Read-only, Không tự gửi mail, Chống Prompt Injection.
3. **Routine 24/7:** "Hẹn giờ nồi cơm điện" cho Agent theo khung 4 câu hỏi (Chạy khi nào - Đọc ở đâu - Làm gì - Lưu vào đâu).
4. **Giải mã Subagent chuẩn Anthropic:** Nắm vững ranh giới Context cô lập 100%, ẩn dụ "Trưởng phòng & Tờ giấy giao việc", 2 giới hạn cứng, và quy tắc ngón tay cái: *"Đi tìm X rồi báo đáp án"* $\rightarrow$ Giao Subagent.
5. **Thực hành xuất Báo cáo điều hành:** Điều phối Subagent đọc 5 CV trong `demo/pdf/01-ung-vien/` (hoặc `demo/md/01-ung-vien/`) chọn 2 nhân sự giao vận Hà Nội, giữ bàn chính sạch bong để xuất Báo cáo kinh doanh chuẩn công sở.

[Ghi chú Giảng viên]: Nhấn mạnh tính liên kết: Từng mảnh ghép đều phục vụ cho chu trình làm việc thực tế của một nhân viên công sở, đi từ dữ liệu thô sang báo cáo và slide hoàn chỉnh.

---

## Slide 03: MCP ChatGPT Image — Nâng Cấp Hình Ảnh Cho Slide

### 1. Tại Sao Slide Cần Ảnh Infographic Sinh Bởi AI?
- **Slide thông thường:** Rất dễ rơi vào cảnh "rừng chữ", người xem lười đọc.
- **Giải pháp:** Dùng MCP `chatgpt-image-mcp` (Model DALL-E 3) sinh infographic, sơ đồ trực quan 16:9 sắc nét, hỗ trợ chữ tiếng Việt rõ ràng.

### 2. Các Lệnh Cốt Lõi Của MCP ChatGPT Image:
- `login_status`: Kiểm tra trạng thái kết nối tài khoản.
- `generate_image`: Tạo ảnh đơn lẻ theo prompt mô tả chi tiết.
- `build_pptx` / `generate_slide_deck`: Tạo slide deck hoàn chỉnh kết hợp ảnh tự sinh.

```text
[Prompt Thực Hành]: Dùng tool generate_image tạo một ảnh infographic tỷ lệ 16:9 
về 'Quy trình 3 bước xử lý đơn hàng và đối soát công nợ', phong cách phẳng hiện đại, 
tông màu xanh công nghệ (Navy Blue & Sky Blue), chữ tiếng Việt sắc nét.
```

[Ghi chú Giảng viên]: Trình diễn ngay trên màn hình: 1 câu lệnh sinh ra bức ảnh sắc nét, kéo thả thẳng vào slide hoặc file báo cáo.

---

## Slide 04: Bản Chất Connectors & MCP — Mở Rộng Ra Ngoài Máy Tính

### Phân Biệt Tường Minh: Local Files vs Cloud Connectors

| Loại kết nối | Phạm vi hoạt động | Cần MCP không? | Ví dụ thực tế |
|---|---|---|---|
| **Local File System** | File trong máy tính cá nhân | ❌ **KHÔNG** (Claude Code đọc trực tiếp cực nhanh) | Đọc file `.xlsx`, `.csv`, `.md`, `.pdf` trong thư mục |
| **Cloud Connectors** | Dịch vụ đám mây bên thứ 3 | ✅ **CÓ** (Cần MCP làm cầu nối an toàn) | Google Drive, Gmail, CRM, MISA, GitHub |

```
┌─────────────────┐       MCP Server       ┌────────────────────────┐
│  AI Workspace   │ ─────────────────────> │  Google Drive / Gmail  │
│  (Claude Code)  │ <───────────────────── │  (Dữ liệu trực tuyến)  │
└─────────────────┘       Bảo mật          └────────────────────────┘
```

[Ghi chú Giảng viên]: Nhấn mạnh quy tắc: Đọc file trong máy KHÔNG CẦN cài MCP gì cả! Chỉ khi nào muốn thò tay lên Drive hay gửi mail mới cần Connector.

---

## Slide 05: 3 Luật Thép An Toàn Khi Dùng Connectors Ngoài Máy

1. **Luật 1 — Quyền "Chỉ đọc" (Read-Only Privilege):** Khi cấp quyền kết nối Google Drive hoặc Cơ sở dữ liệu, **chỉ cấp quyền Xem/Đọc**. Tuyệt đối không cấp quyền Sửa/Xóa tài liệu chung.
2. **Luật 2 — Nguyên tắc "Không bao giờ để AI tự bấm gửi":** AI chỉ được phép **Đọc $\rightarrow$ Phân tích $\rightarrow$ Soạn bản nháp (Draft)**. Nút bấm gửi email hoặc duyệt tiền 100% phải do con người kiểm tra (Human-in-the-loop).
3. **Luật 3 — Cảnh giác Prompt Injection:** Nội dung email hay file của người ngoài là dữ liệu thụ động để phân tích, không phải là mệnh lệnh hệ thống để Agent thi hành.

```text
[Prompt K2-1]: Đọc thông tin công nợ An Phát trong demo/md/so-lieu-ban-hang-thang.md, 
soạn giúp tôi một bản nháp email nhắc thanh toán trước ngày 05/04.
LƯU Ý BẢO MẬT: CHỈ xuất bản nháp ra màn hình để tôi duyệt, TUYỆT ĐỐI KHÔNG tự gửi mail!
```

[Ghi chú Giảng viên]: Kể câu chuyện thực tế: AI đọc nhầm số liệu công nợ và tự động gửi email đòi nợ sai cho khách VIP $\rightarrow$ Hậu quả không thể cứu vãn. AI soạn nháp cực tốt, nhưng gửi phải là con người.

---

## Slide 06: Routine — Tự Động Hóa Chạy Theo Lịch (24/7)

### Ẩn Dụ "Hẹn Giờ Nồi Cơm Điện" Cho Agent:

Không cần mỗi tuần phải ngồi gõ lại prompt. Đúng giờ định kỳ, cỗ máy tự động thức dậy, thực thi chuỗi việc và bày sẵn kết quả ra bàn làm việc.

### Khung 4 Câu Hỏi Định Hình Mọi Routine:
1. **Chạy lúc nào?** $\rightarrow$ 08:00 sáng Thứ Hai hàng tuần.
2. **Đọc ở đâu?** $\rightarrow$ File `demo/md/so-lieu-ban-hang-thang.md` (hoặc `demo/pdf/so-lieu-ban-hang-thang-3.pdf`).
3. **Làm gì với dữ liệu?** $\rightarrow$ Lọc đơn tồn đọng, tính doanh thu tăng trưởng so với tháng trước.
4. **Lưu vào đâu?** $\rightarrow$ `05-bao-cao/` với tên file tự động đánh số thứ tự tuần tự.

```text
[Quy tắc an toàn Routine]: Routine chỉ được ĐỌC, TÍNH TOÁN và LƯU BÁO CÁO NỘI BỘ. 
Tuyệt đối không cài Routine tự ý gửi email ra ngoài hay xóa sửa file dữ liệu gốc.
```

[Ghi chú Giảng viên]: Hướng dẫn học viên cách đặt Routine và cách kiểm tra danh sách Routine đang chạy trong hệ thống.

---

## Slide 07: Định Nghĩa Chuẩn Anthropic: Workflow vs Agent vs Subagent

### Báo Cáo Nghiên Cứu *Building Effective Agents* (Anthropic):

- **Workflow (Quy trình):** LLM và công cụ được điều phối theo các đường đi cố định viết sẵn bằng code (chuỗi If/Else, Prompt Chaining). Không có tính tự quyết.
- **Agent:** LLM **tự điều khiển quy trình và cách dùng công cụ trong một vòng lặp (loop)**: Tự suy nghĩ (Reasoning) $\rightarrow$ Tự chọn tool $\rightarrow$ Tự quan sát kết quả $\rightarrow$ Tự quyết định bước tiếp theo.
- **Subagent (Agent con):** Phiên bản Claude riêng biệt do Agent chính sinh ra để **xử lý một việc có phạm vi rõ ràng**. Nó chạy trong **Context Window riêng biệt**, với System Prompt và Tool riêng, làm phần việc ồn ào và **chỉ trả về một bản tóm tắt kết quả**.

> **Câu chốt Anthropic:** *"Agent là LLM tự dùng công cụ trong vòng lặp; Subagent là agent con chạy ở phòng riêng để bảo vệ context cho agent chính!"*

[Ghi chú Giảng viên]: Giải thích cho lớp thấy: Khi ta tự viết code điều hướng cố định thì là Workflow. Khi AI tự quyết định chọn tool trong vòng lặp thì là Agent. Và khi Agent đẻ ra nhánh độc lập thì là Subagent.

---

## Slide 08: Ranh Giới Context Cô Lập (Context Boundary)

### Điểm Dễ Hiểu Sai Nhất Về Subagent:

1. **Cách ly 100% (Isolated Context):**
   - Subagent bắt đầu với context **hoàn toàn mới, sạch tinh**.
   - Nó **KHÔNG THẤY** lịch sử hội thoại của bạn với Agent chính từ đầu buổi.
   - Nó **KHÔNG THẤY** các file Agent chính đã từng mở trước đó.
2. **Kênh truyền duy nhất — Đoạn Prompt giao việc:**
   - Nếu trên câu lệnh bạn không ghi rõ đường dẫn file hay tiêu chí $\rightarrow$ Subagent hoàn toàn mù tịt!
3. **Chiều về cực hẹp — Chỉ nộp bản tóm tắt:**
   - **Chỉ tin nhắn cuối cùng** của Subagent được trả về bàn chính.
   - Mọi log gọi công cụ, file đọc rác, output trung gian... **đều ở lại trong context của Subagent và tự hủy**.
   - Giữ cho Context Window của phiên chính luôn trong sạch, không bị "ngáo" (Context Pollution).

[Ghi chú Giảng viên]: Nhấn mạnh: Subagent không có mắt thần nhìn lại lịch sử chat. Tất cả thông tin cần thiết phải gói gọn trong đoạn Prompt giao việc!

---

## Slide 09: Ẩn Dụ Sư Phạm: "Trưởng Phòng & Tờ Giấy Giao Việc"

### Mô Hình Hóa Trực Quan Hoạt Động Của Subagent:

- **Agent Chính (Trưởng phòng):** Ngồi họp trực tiếp với Giám đốc (Bạn). Nắm toàn bộ bối cảnh dự án, lịch sử trao đổi. Khi nhận 50 bộ hồ sơ CV dày cộp, Trưởng phòng không tự ôm đọc vì mặt bàn sẽ bị chật.
- **Subagent (Trợ lý phòng riêng):** Nhận một **TỜ GIẤY GIAO VIỆC** từ Trưởng phòng. Sang phòng làm việc bên cạnh, đọc 50 hồ sơ trên bàn riêng, rút ra đúng **1 trang A4 tóm tắt** mang sang nộp rồi giải tán!

### Hai Giới Hạn Cứng Của Subagent:
1. **Không có ủy quyền lồng nhau:** Subagent KHÔNG THỂ sinh subagent khác (No nested subagents).
2. **Không thể hỏi lại người dùng:** Subagent chạy nền sẽ tự động từ chối mọi thao tác cần xin phép (permission).

[Ghi chú Giảng viên]: Cho học viên thuộc lòng ẩn dụ này: Trưởng phòng viết giấy giao việc, nhân viên sang phòng riêng cày cuốc nộp lại 1 trang A4. Mặt bàn phòng họp luôn sạch bong!

---

## Slide 10: Khi Nào Dùng Subagent vs Giữ Ở Agent Chính?

### Bảng Phân Định Chuẩn Kỹ Thuật Anthropic:

| Tình huống công việc | Lựa chọn | Lý do cốt lõi |
|---|---|---|
| **Đọc quét, điều tra nhiều file thô** (20 CV, 10 hợp đồng) | **DÙNG SUBAGENT** | Output lớn nhưng kết luận nhỏ. Tránh ô nhiễm context chính. |
| **Tìm kiếm song song độc lập** trong nhiều thư mục | **DÙNG SUBAGENT** | Chạy các nhánh độc lập cùng lúc để tiết kiệm thời gian. |
| **Sửa file thực tế, chạy lệnh cần cấp quyền** | **GIỮ AGENT CHÍNH** | Cần người dùng phê duyệt trực tiếp. Subagent chạy nền sẽ tự từ chối. |
| **Việc cần trao đổi qua lại nhiều vòng** | **GIỮ AGENT CHÍNH** | Cần giữ mạch ngữ cảnh liên tục. |

> ⭐ **Quy tắc ngón tay cái Anthropic:**  
> *"Nếu mô tả được việc là: **'ĐI TÌM X RỒI BÁO TÔI ĐÁP ÁN'** $\rightarrow$ DÙNG SUBAGENT.  
> Việc gắn chặt, cần lặp lại, cần bạn ra quyết định giữa chừng $\rightarrow$ GIỮ Ở AGENT CHÍNH!"*

[Ghi chú Giảng viên]: Chiếu bảng và cho học viên nhẩm lại câu quy tắc ngón tay cái.

---

## Slide 11: Thực Hành Thực Chiến: Điều Phối Subagent Quét 5 CV

### Tình Huống: Tuyển Giao Vận Hà Nội Cho Tháng 4 (`demo/pdf/01-ung-vien/` hoặc `demo/md/01-ung-vien/`)

```text
[Prompt K5-1 - Tờ Giấy Giao Việc Cho Subagent]:
Dùng một subagent đọc toàn bộ 5 file hồ sơ ứng viên trong thư mục demo/pdf/01-ung-vien/ (hoặc demo/md/01-ung-vien/).
Yêu cầu subagent:
1. Đánh giá từng ứng viên theo tiêu chí: Tuyển nhân viên giao vận Hà Nội (đi xe máy nội thành, 
   cẩn thận, có kinh nghiệm thực địa, mức lương dưới 12 triệu).
2. Trả về đúng 1 bảng tổng hợp: Tên, Năm sinh, Kinh nghiệm, Mức lương, Đánh giá, Lý do.
3. Đề xuất chọn ra 2 ứng viên sáng giá nhất để mời phỏng vấn vòng 1.
QUY TẮC BẮT BUỘC: Chỉ trả về bảng tổng hợp và đề xuất ngắn gọn. 
Tuyệt đối không đổ nguyên văn nội dung từng file CV vào cuộc trò chuyện chính.
```

- **Kết quả trả về trên bàn chính:** Đúng 1 bảng tổng hợp 5 dòng và đề xuất chọn `Nguyễn Văn Nam` (3 năm Viettel Post) và `Lê Văn Hùng` (4 năm Điện Máy Xanh).
- **Thành quả:** Bàn làm việc chính sạch bóng 100%, không tốn một chút dung lượng context nào!

[Ghi chú Giảng viên]: Cho cả lớp gõ prompt, có thể cho đọc trực tiếp 5 file .pdf (`demo/pdf/01-ung-vien/*.pdf`) hoặc 5 file .md (`demo/md/01-ung-vien/*.md`) đã phân loại rạch ròi. Quan sát màn hình trả về đúng một bảng 5 dòng tinh gọn.

---

## Slide 12: Agent Chính Xuất Báo Cáo Quản Trị Điều Hành

### Kết Tinh Thành Quả Tháng 3 Gửi Ban Lãnh Đạo:

```text
[Prompt K5-2]: Dựa trên số liệu bán hàng trong demo/md/so-lieu-ban-hang-thang.md (hoặc demo/pdf/so-lieu-ban-hang-thang-3.pdf) và kết quả 
sàng lọc ứng viên giao vận vừa rồi, hãy soạn Báo cáo Kết quả Kinh doanh Tháng 3 gửi chị Lan Trưởng phòng:
- Cấu trúc: Tiêu đề trang trọng, Tóm tắt điều hành (3 chỉ số chính), Chi tiết doanh thu theo thị trường & 
  sản phẩm, Cảnh báo công nợ (An Phát, Đại Tín, Hải Nam), Kế hoạch hành động tháng 4 (đẩy Gói Cao cấp, 
  phương án phỏng vấn 2 ứng viên Nam và Hùng).
- Văn phong công sở trang trọng, KHÔNG DÙNG EMOJI, số liệu trích dẫn chính xác 100%.
- Lưu file vào thư mục 05-bao-cao/ theo Super Rule tự động đánh số thứ tự tuần tự.
```

- **Tiêu chuẩn chất lượng:** Không emoji, chống bịa số (doanh thu 1.085 tr, tăng 170 tr), tự lưu tại `05-bao-cao/04_bao-cao-kinh-doanh-thang-3.md`.

[Ghi chú Giảng viên]: Mở file báo cáo vừa tạo ra cho học viên xem: Đầy đủ các phần, giải pháp rõ ràng, số liệu chính xác 100%.

---

## Slide 13: Đối Soát 3 Câu Hỏi Hiểu Bài Ngay Tại Lớp

### Học Viên Gõ Đáp Án Vào Ô Chat Zoom:

1. **Câu 1:** *"Vì sao nói kênh giao tiếp sang Subagent giống như 'Tờ giấy giao việc'?"*  
   $\rightarrow$ **Đáp án:** Vì Subagent có Context cách ly hoàn toàn, không thấy lịch sử chat trước đó; mọi thông tin cần thiết bắt buộc phải ghi rõ trong prompt giao việc.
2. **Câu 2:** *"Hai giới hạn cứng của Subagent là gì?"*  
   $\rightarrow$ **Đáp án:** (1) Không có ủy quyền lồng nhau (không thể sinh subagent con); (2) Không thể dừng lại hỏi người dùng để làm rõ.
3. **Câu 3:** *"Khi nào nên dùng Subagent và khi nào nên giữ ở Agent chính?"*  
   $\rightarrow$ **Đáp án:** Output lớn nhưng kết luận nhỏ, "đi tìm X rồi báo đáp án" $\rightarrow$ Subagent. Cần trao đổi qua lại, cần duyệt sửa file $\rightarrow$ Agent chính.

[Ghi chú Giảng viên]: Dành 3 phút cho lớp gõ câu trả lời vào ô chat, đọc tên và khen ngợi các học viên trả lời nhanh và chính xác.

---

## Slide 14: Bệ Phóng Sang Buổi 05: Đội Ngũ Multi-Agent & Chi Phí 15x

### Khi Đã Làm Chủ Subagent, Làm Sao Điều Phối Cả Một Đội Ngũ?

- **Điểm nhấn 1 — Hai mô hình phối hợp:**
  * *Nối chuỗi (Tuần tự):* Agent A xong chuyền kết quả cho Agent B làm tiếp.
  * *Chạy song song:* Nhiều Agent chạy độc lập cùng lúc để tiết kiệm thời gian.
- **Điểm nhấn 2 — Bài toán chi phí Token:**
  * Chat thường (1x) $\rightarrow$ Agent đơn (~4x) $\rightarrow$ **Multi-agent (~15x)**.
  * Học cách tính toán kinh tế khi nào đáng đầu tư hệ Multi-Agent.
- **Điểm nhấn 3 — Benchmark đột phá 90.2%:**
  * Hệ thống Multi-Agent nghiên cứu của Anthropic (Opus 4 + Sonnet 4) đã **vượt trội hơn Agent đơn tới 90.2%** trong các bài toán nghiên cứu phức tạp!

[Ghi chú Giảng viên]: Gợi mở sự tò mò cho Buổi 5: Tự tay nuôi 2 nhân viên AI biên chế và cho phối hợp làm việc nhịp nhàng như một phòng ban thực tế!

---

## Slide 15: Bài Tập Về Nhà & Chuẩn Bị Buổi 05

### 4 Nhiệm Vụ Thực Chiến Bắt Buộc:

1. **Nhiệm vụ 1:** Dùng MCP Image vẽ 1 ảnh Infographic sơ đồ quy trình tiếng Việt và nhúng vào bộ Slide thuyết trình của bạn.
2. **Nhiệm vụ 2:** Soạn thảo bản thiết kế Routine theo khung 4 câu hỏi cho 1 công việc lặp lại hàng tuần tại cơ quan bạn.
3. **Nhiệm vụ 3:** Gom 3–5 file tài liệu thật vào một thư mục, dùng Subagent với prompt chuẩn "tờ giấy giao việc" để rút ra 1 bảng so sánh tóm tắt.
4. **Nhiệm vụ 4:** Chụp ảnh màn hình kết quả chạy Subagent và file Báo cáo quản trị nộp lên nhóm Zalo lớp trước 12:00 trưa buổi học kế tiếp.

**CẢM ƠN QUÝ HỌC VIÊN! HẸN GẶP LẠI Ở BUỔI 05 BÙNG NỔ!**

[Ghi chú Giảng viên]: Cảm ơn sự tập trung của cả lớp, nhắc nhở lịch nộp bài tập và động viên học viên thực hành trên dữ liệu thật của mình.
