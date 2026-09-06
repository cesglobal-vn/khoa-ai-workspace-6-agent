# Giáo án Buổi 01: Xây Dựng AI Workspace, Làm Chủ Claude Code & GitHub Nền Tảng

> Khung chuẩn cho giảng viên CES Global. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:  
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,  
> (3) FILE DEMO: đường dẫn file trong `demo/` của buổi học dùng cho prompt đó,  
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.

---

## Thông tin buổi học
- **Buổi:** 01 / 6
- **Khái niệm chính:** AI Workspace, Cài đặt Claude Desktop (Claude Code), Mode, Model, Effort, Quota, Context Window, file `CLAUDE.md`, GitHub nền tảng, Agent Điều phối.
- **Loại:** Nền tảng (Buổi mở màn quan trọng, định hình tư duy và công cụ cho toàn khóa).
- **Thời lượng:** 150 phút (2,5 giờ).

---

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn ứng dụng **Claude Desktop** trên máy tính, chuyển sang tab **`</> Code` (Claude Code)**.
- [ ] Mở phần **Settings > Privacy** kiểm tra đã tắt *"Help improve our AI models"* để làm mẫu cho lớp.
- [ ] Mở sẵn thư mục demo: `01-buoi-01-ai-workspace-claude-code/demo/`.
- [ ] File demo cần dùng:
  - `01-buoi-01-ai-workspace-claude-code/demo/bien-ban-hop-mau.md`
  - `01-buoi-01-ai-workspace-claude-code/demo/du-an-mau/`
- [ ] Mẫu cấu hình mở sẵn: `07-mau-cau-hinh-linh-kien/claude-md-mau.md`, `07-mau-cau-hinh-linh-kien/github-mcp-va-token.md`.
- [ ] Chuẩn bị sẵn 1 tài khoản GitHub mẫu để chiếu thao tác: tạo tài khoản, xem repo, tải file `.zip` hoặc clone về máy.
- [ ] Chuẩn bị Zalo lớp để gửi link tài liệu và hỗ trợ xử lý lỗi môi trường (PATH Windows) cho học viên.

---

## Mục tiêu buổi học (Học xong học viên làm được gì)
1. **Cài đặt & Vận hành mượt mà:** Mở được Claude Code ngay trong Claude Desktop, biết thiết lập bảo mật dữ liệu công sở (tắt chia sẻ dữ liệu train AI).
2. **Hiểu bản chất giao diện Claude Code:** Giải thích và tự chọn đúng: **Mode** (Auto/Manual/Plan/Accept edits), **Model** (Haiku/Sonnet/Opus/Fable), **Effort** (Faster - Smarter), **Quota & Context Window** (vòng tròn bộ nhớ).
3. **Hiểu lý do và tự tạo file `CLAUDE.md`:** Nắm được tại sao phải có `CLAUDE.md`, cấu trúc file ra sao, và cách viết prompt định hình để AI xác định đúng ngữ cảnh công việc.
4. **Làm chủ GitHub cơ bản:** Hiểu GitHub là gì, biết cách truy cập repo tài liệu khóa học của CES Global, đọc tài liệu online và tải mã nguồn về máy.
5. **Khởi tạo AI Workspace & Agent Điều phối đầu tiên:** Dựng được cây thư mục làm việc chuẩn và giao việc thành công cho Agent Điều phối.

---

## Kết quả cầm về (Deliverable)
- 1 AI Workspace chuẩn trên máy tính cá nhân đã kết nối Claude Code trong Claude Desktop.
- 1 file `CLAUDE.md` chuẩn bối cảnh cá nhân và công việc của học viên.
- Tài khoản GitHub đã kích hoạt và tải trọn bộ tài liệu khóa học về máy.
- 1 Agent Điều phối nhận diện đúng bối cảnh và quy tắc xưng hô, văn phong công sở.

---

## Khái niệm cốt lõi (Giải thích ngôn ngữ đời thường cho dân văn phòng)

### 1. AI Workspace là gì?
Là một **"văn phòng làm việc số"** được tổ chức ngăn nắp trên máy tính của bạn, nơi Claude Code đóng vai trò như một quản lý và đội ngũ nhân viên: có hồ sơ quy định (`CLAUDE.md`), có các kỹ năng chuẩn (`skills/`), có cổng kết nối ngoại vi (`MCP`), và đọc/sửa trực tiếp các file thật trong máy tính mà không cần copy – dán qua lại.

### 2. Bốn thông số quan trọng trên giao diện Claude Desktop:
- **Mode (Chế độ thực thi & cấp quyền):**
  * `Auto [Start]` *(Khuyên dùng)*: Claude tự quyết định các bước và quyền chạy công cụ để hoàn thành việc.
  * `Manual`: Chế độ cẩn thận, mỗi lần mở file, sửa file hay chạy lệnh Claude đều dừng lại hỏi xin phép bạn.
  * `Accept edits`: Tự động chấp nhận các chỉnh sửa file mà không hỏi lại.
  * `Plan`: Bắt buộc Claude phải lên bản kế hoạch từng bước trước khi bắt tay vào chỉnh sửa.
  * `Bypass permissions`: Bỏ qua mọi bước kiểm tra an toàn (chỉ dùng khi tuyệt đối tin cậy).
- **Model (Bộ não AI):**
  * `Haiku 4.5`: Rất nhanh, tiết kiệm token, phù hợp cho việc đơn giản (tóm tắt nhanh 1 email, phân loại văn bản).
  * `Sonnet 5`: Model cân bằng và mạnh mẽ nhất cho công việc văn phòng hằng ngày (đọc tài liệu dài, viết báo cáo, phân tích số liệu).
  * `Opus 5 / Fable 5.1`: Bộ não sâu nhất, suy luận logic phức tạp, giải quyết các bài toán hóc búa cần suy nghĩ nhiều bước.
- **Effort (Thanh trượt nỗ lực suy nghĩ):**
  * Thang đo từ `Faster` (nhanh) đến `Smarter` (thông minh). Đặt `High` khi cần AI phân tích sâu, so sánh đối chiếu đa chiều; đặt mức thấp hơn khi chỉ cần câu trả lời nhanh gọn.
- **Quota, Token & Cửa sổ ngữ cảnh (Context Window):**
  * *Quota:* Hạn mức số lượng câu hỏi/token bạn được dùng trong một khoảng thời gian (ví dụ 5 giờ) theo gói tài khoản.
  * *Context Window (Vòng tròn góc dưới bên phải):* Là **"bộ nhớ làm việc ngắn hạn"** trong một phiên chat. Khi bạn nạp quá nhiều tài liệu dày, vòng tròn sẽ đầy dần. Khi vòng tròn quá đầy, AI sẽ chậm lại, tốn chi phí và có thể bị "lú", quên mất những chỉ dẫn bạn dặn ở đầu phiên.
  * *Nguyên tắc:* Luôn giữ context window gọn gàng, chia việc lớn cho các agent con (subagent) ở phòng riêng.

### 3. File `CLAUDE.md` — Trí nhớ dài hạn của Workspace:
- Là file văn bản Markdown đặt tại gốc thư mục dự án.
- Mỗi khi bạn mở phiên làm việc mới, Claude Code sẽ **tự động đọc file này đầu tiên** để biết: bạn là ai, làm ở phòng ban nào, cách xưng hô với sếp và đối tác ra sao, quy tắc không dùng emoji, và nguyên tắc sống còn: **không bao giờ được bịa số liệu**.

### 4. GitHub là gì?
- Hãy hình dung GitHub như một chiếc "Google Drive chuyên nghiệp dành cho tài liệu và mã nguồn": lưu trữ file trên đám mây, lưu lại toàn bộ lịch sử chỉnh sửa (ai sửa, sửa lúc nào), và chia sẻ cho người khác xem hoặc tải về máy chỉ bằng một cú nhấp chuột.

---

## Timeline chi tiết (150 Phút)

```
[00:00 - 00:15]  Mở đầu: Giới thiệu khóa học, triết lý AI Workspace & Đội ngũ 6 Agent
[00:15 - 00:45]  Lý thuyết 1: Cài đặt, Bảo mật dữ liệu & Làm chủ giao diện Claude Desktop
[00:45 - 01:15]  Demo GV: Khám phá giao diện (Mode, Model, Effort, Context) & Thiết lập CLAUDE.md
[01:15 - 01:25]  Nghỉ giải lao
[01:25 - 01:50]  Thực hành 1: Học viên tự cấu hình Claude Desktop, bảo mật & tạo file CLAUDE.md
[01:50 - 02:15]  Lý thuyết 2 & Demo: GitHub căn bản — Xem tài liệu & Tải trọn bộ tài liệu khóa học
[02:15 - 02:30]  Thực hành 2 & Tổng kết: Khởi tạo Agent Điều phối, giao việc đầu tiên & Hướng dẫn về nhà
```

---

### [00:00 - 00:15] Mở đầu: Triết lý khóa học & Bản đồ 6 Buổi
- **Lời dẫn GV:** "Chào mừng toàn thể anh chị học viên đến với khóa học *Ứng dụng AI cho Văn phòng: Xây Trợ lý AI Cá nhân & 6 AI Agent* của CES Global. Đa phần chúng ta trước đây dùng AI theo kiểu mở một khung chat lên, hỏi một câu, copy câu trả lời rồi đóng tab lại. Ngày mai làm việc mới, ta lại phải gõ lại bối cảnh từ đầu. Khóa học này sẽ thay đổi hoàn toàn cách anh chị làm việc: chúng ta sẽ xây dựng một AI Workspace cá nhân có trí nhớ lâu dài và điều khiển một đội ngũ 6 nhân viên AI Agent làm việc thật cho mình. Hôm nay là Buổi 1 — buổi đặt nền móng vững chắc nhất."
- Giới thiệu tổng quan lộ trình 6 buổi:
  * Buổi 1: AI Workspace & Agent Điều phối (Công cụ, giao diện, CLAUDE.md, GitHub)
  * Buổi 2: Agent Quản lý tài liệu (Đọc tài liệu 40 trang, chống bịa số)
  * Buổi 3: Agent Phân tích dữ liệu (Excel/CSV, vẽ biểu đồ, cắm MCP)
  * Buổi 4: Agent Lập báo cáo & Slide thuyết trình
  * Buổi 5: Agent Deep Research & Phối hợp đội ngũ
  * Buổi 6: Hệ Multi-Agent Capstone Project
- Điểm danh và kiểm tra máy tính học viên đã sẵn sàng mở Zoom và Claude Desktop.

---

### [00:15 - 00:45] Lý thuyết 1: Làm chủ Claude Desktop, Bảo mật & Các Thông số Giao diện

- **Lời dẫn GV:** "Trước khi giao việc cho AI, ta phải hiểu rõ công cụ mình đang cầm trong tay. Trong Claude Desktop, tab Claude Code không đơn thuần là chat, mà là một môi trường làm việc agent có khả năng đọc và chỉnh sửa file trong máy. Chúng ta sẽ cùng nhau làm chủ từng nút bấm và thiết lập bảo mật dữ liệu tuyệt đối cho công ty."

#### 1. Thiết lập Bảo mật dữ liệu doanh nghiệp (Privacy Settings):
- **Vấn đề:** Khi làm việc văn phòng, tài liệu công ty chứa thông tin nội bộ, hợp đồng, báo giá.
- **Thao tác bắt buộc:**
  1. Vào menu **Settings** (biểu tượng bánh răng) > Chọn mục **Privacy**.
  2. Tìm dòng **"Help improve our AI models"** (Cho phép Anthropic dùng dữ liệu chat và code để huấn luyện AI).
  3. **Gạt TẮT (OFF)** công tắc này.
  4. *Cam kết:* Dữ liệu của bạn được bảo mật riêng tư, không bị mang đi train AI công cộng.

#### 2. Giải mã các nút bấm trên thanh điều khiển Claude Desktop:
- **Nút Mode (Chế độ hoạt động):**
  * Hướng dẫn học viên bấm vào nút Mode ở góc dưới bên trái:
  * Giải thích 5 chế độ: `Auto [Start]` (AI tự xử lý linh hoạt), `Manual` (hỏi từng bước), `Accept edits` (tự lưu file sửa), `Plan` (bắt AI lên kế hoạch trước), `Bypass permissions` (bỏ qua xác nhận).
  * *Lời khuyên lớp học:* Để mặc định là `Auto [Start]`.
- **Nút Model (Chọn mô hình AI):**
  * Bấm vào nút tên Model (ví dụ `Fable 5.1` / `Sonnet 5` / `Haiku 4.5`):
  * Phân tích rõ: Dùng `Sonnet 5` cho mọi công việc văn phòng hằng ngày (chuẩn mực, phân tích tốt, chi phí hợp lý). Khi cần tốc độ cao cho tác vụ đơn giản thì chọn `Haiku 4.5`. Khi gặp bài toán hóc búa cần suy luận nhiều tầng thì chọn `Opus 5` hoặc `Fable 5.1`.
- **Nút Effort (Mức độ nỗ lực tư duy):**
  * Mở thanh trượt Effort: Thang từ `Faster` đến `Smarter`.
  * Giải thích: Effort cao (`High`) giúp AI suy nghĩ cẩn trọng hơn, đọc kỹ từng điều khoản trước khi trả lời.
- **Vòng tròn Quota & Context Window (Góc dưới bên phải):**
  * Vòng tròn này chính là "thước đo bộ nhớ ngắn hạn".
  * Mỗi từ ngữ, mỗi trang tài liệu nạp vào sẽ làm vòng tròn này đầy dần.
  * Khi làm việc với tài liệu dài, cần chú ý không nhồi nhét quá nhiều file vào cùng 1 phiên chat để tránh AI bị "ngợp" (tràn context window).

#### 3. Xử lý lỗi thường gặp khi cài đặt Claude Code (PATH Environment):
- Giải thích hiện tượng terminal báo: *"Claude command not recognized"*:
  * Nguyên nhân: Do biến môi trường `PATH` của Windows chưa nhận diện thư mục npm (`C:\Users\<User>\AppData\Roaming\npm`).
  * Cách khắc phục nhanh: Nhờ chính Claude Code trong Claude Desktop kiểm tra đường dẫn hoặc chạy terminal mới bằng quyền Administrator.

#### 4. Khám phá tính năng Claude Memory (Settings > Memory) & So sánh 3 Cấp độ Trí nhớ:
- **Claude Memory là gì?** Là bộ nhớ dài hạn gắn liền với tài khoản Anthropic của bạn, hoạt động xuyên suốt các cuộc trò chuyện trên Desktop, Web và Mobile.
- **Cách quản lý:** Vào **Settings** > Chọn tab **`Memory`** (nằm ngay dưới Capabilities).
  * Bật/Tắt (Toggle On/Off): Cho phép Claude tự động lưu lại sở thích, thói quen và thông tin cá nhân.
  * Xem & Quản lý ký ức: Bấm *View and manage memory* để xem, sửa hoặc xóa từng mẩu thông tin đã lưu.
- **So sánh 3 cấp độ trí nhớ (GV bắt buộc chiếu bảng này cho lớp):**

| Cấp độ | Vị trí lưu trữ | Phạm vi tác dụng | Dùng khi nào |
|---|---|---|---|
| **1. Context Window** *(Ngắn hạn)* | Bộ nhớ RAM phiên chat (vòng tròn góc phải) | Chỉ nhớ **trong đúng phiên chat hiện tại**, đóng phiên là mất | Xử lý tài liệu hiện tại, hết việc thì mở phiên mới |
| **2. Claude Memory** *(Ký ức cá nhân)* | Đám mây tài khoản Anthropic (Settings > Memory) | Toàn cục cho **riêng bạn** ở mọi cuộc chat thông thường | Lưu sở thích cá nhân, cách xưng hô chung |
| **3. `CLAUDE.md`** *(Trí nhớ dự án)* | File vật lý `CLAUDE.md` tại gốc thư mục máy tính | **Chuẩn mực AI Workspace**: Áp dụng cho cả dự án và Agent | **Bắt buộc dùng**: Đưa lên GitHub được, chia sẻ cả phòng dùng chung |

---

### [00:45 - 01:15] Demo Giảng Viên: Thiết Lập CLAUDE.md Chuẩn & Ra Lệnh Tự Sinh Cây Thư Mục Dự Án

**Bước 1: Thiết lập file `CLAUDE.md` chuẩn doanh nghiệp trước — Để AI hiểu tôi là ai, tôi làm gì, nhu cầu của tôi đối với dự án này là gì**
- **Lời dẫn GV:** "Nguyên tắc cốt lõi khi làm việc với AI: Trước khi giao việc, ta phải cho AI biết *tôi là ai, tôi làm việc gì, ở phòng ban nào, và tôi có nhu cầu gì đối với dự án này*. Nếu không thiết lập trước, AI sẽ không hiểu bối cảnh và sinh ra những cấu trúc chung chung. Vì vậy, ta thiết lập file `CLAUDE.md` làm 'Hiến pháp' đầu tiên, nạp toàn bộ danh tính, mục tiêu dự án và quy tắc quản trị toàn cục."
- **Prompt gõ vào Claude Code:**
  ```
  Dựa trên mẫu demo/CLAUDE.md (hoặc 07-mau-cau-hinh-linh-kien/CLAUDE-md-chuan-doanh-nghiep.md), hãy tạo file CLAUDE.md tại thư mục gốc cho tôi:
  - Họ tên: Nguyễn Văn An - Chuyên viên Kinh doanh cấp cao tại CES Global
  - Mục tiêu & Nhu cầu dự án: Quản lý toàn diện quy trình kinh doanh của công ty, lưu trữ và chăm sóc hồ sơ khách hàng, phát hành báo giá, theo dõi hợp đồng dịch vụ, phân tích số liệu doanh thu từ file Excel/CSV, và lập báo cáo bán hàng tuần/tháng.
  - Cấp trên trực tiếp: Chị Mai (Trưởng phòng Kinh doanh), xưng "em", gọi "chị"
  - Tuân thủ nghiêm ngặt toàn bộ hệ thống quy tắc cốt lõi: 100% phông chữ Times New Roman cho Word/Excel/PDF, chuẩn thể thức hành chính Nghị định 30/2020/NĐ-CP, bố cục bảng tính Excel chống dồn chữ, tuyệt đối không bịa số liệu, cấm xóa thư mục, và luôn duy trì _backup/.
  ```
- **File demo tham chiếu:** `demo/CLAUDE.md` (hoặc mẫu đầy đủ tại `07-mau-cau-hinh-linh-kien/CLAUDE-md-chuan-doanh-nghiep.md`)
- **Kết quả mong đợi:** File `CLAUDE.md` xuất hiện tại thư mục gốc với đầy đủ danh tính cá nhân, mục tiêu dự án và bộ quy tắc chuẩn mực doanh nghiệp.

**Bước 2: Dựa trên `CLAUDE.md`, ra lệnh cho Claude tự động phân tích nhu cầu và sinh cây thư mục chuẩn hóa**
- **Lời dẫn GV:** "Bây giờ Claude Code đã hiểu rõ tôi là ai và mục đích của dự án này rồi. Thay vì tôi phải ngồi tự nghĩ tên từng thư mục hay bấm New Folder thủ công, tôi chỉ cần nói một câu: *'Dựa trên vai trò và nhu cầu của tôi trong CLAUDE.md, hãy tự thiết kế và tạo cây thư mục làm việc chuyên nghiệp cho tôi'*. Hãy xem AI phân tích thông minh như thế nào!"
- **Prompt gõ vào Claude Code:**
  ```
  Đọc file CLAUDE.md vừa tạo. Dựa trên vai trò Chuyên viên Kinh doanh, mục tiêu dự án và các quy tắc quản trị trong đó:
  1. Hãy thiết kế và tự động tạo cây thư mục làm việc chuyên nghiệp, tối ưu nhất cho công việc của tôi (bắt buộc áp dụng quy tắc tiền tố 2 chữ số 01-, 02-, 03-...).
  2. Tạo thư mục _backup/ theo đúng quy tắc lưu trữ an toàn phiên bản cũ.
  3. Tạo sẵn file 00-index.md tại thư mục gốc làm bản đồ chỉ huy, mô tả rõ chức năng và danh mục tài liệu của từng thư mục con vừa tạo.
  ```
- **Kết quả mong đợi:** Claude Code đọc hiểu `CLAUDE.md`, tự động sinh ra cây thư mục kinh doanh cực kỳ chuẩn mực:
  * `01-khach-hang/` : Hồ sơ và lịch sử làm việc từng khách hàng
  * `02-bao-gia/`    : Các bản báo giá đã phát hành
  * `03-hop-dong/`   : Hợp đồng đã ký kết
  * `04-so-lieu/`    : File doanh số, đơn hàng Excel/CSV
  * `05-bao-cao/`    : Báo cáo kinh doanh tuần, tháng
  * `_backup/`       : Lưu trữ phiên bản tài liệu cũ
  * `00-index.md`    : Mục lục và bản đồ chỉ dẫn toàn diện của thư mục
  GV mở cây thư mục vừa tạo cho cả lớp đối chiếu.

**Bước 3: Kiểm tra trí nhớ của Claude Code qua phiên mới**
- **Lời dẫn GV:** "Bây giờ tôi mở một phiên làm việc mới (New Session). Tôi không nhắc lại tôi là ai hay thư mục có những gì nữa, mà tôi nhờ Claude soạn một email chào hàng cho khách hàng tên Tuấn và hỏi Claude xem file báo giá sẽ lưu ở đâu."
- **Prompt gõ vào Claude Code:**
  ```
  Hãy soạn giúp tôi một email ngắn gửi anh Tuấn giới thiệu giải pháp phần mềm quản lý của CES Global, và cho tôi biết sau này file báo giá của anh Tuấn sẽ được lưu vào thư mục nào trong dự án này?
  ```
- **Kết quả mong đợi:** Claude Code tự động xưng "em", gọi "anh Tuấn", văn phong trang trọng, **hoàn toàn không có emoji**, đồng thời chỉ ra chính xác: file báo giá sẽ được lưu vào `02-bao-gia/` theo đúng cấu trúc thư mục vừa thiết lập.

---

### [01:15 - 01:25] Nghỉ giải lao (10 phút)
- Trợ giảng hỗ trợ các học viên chưa cài xong Claude Desktop hoặc chưa chuyển được sang tab `</> Code`.

---

### [01:25 - 01:50] Thực hành 1: Học viên Tự Thiết Lập `CLAUDE.md` & Ra Lệnh Tự Dựng Cây Thư Mục Cá Nhân

- **Lời dẫn GV:** "Bây giờ đến lượt cả lớp. Hãy biến máy tính của anh chị thành một văn phòng AI thực thụ theo đúng 2 bước vừa học: Bước 1 là nạp danh tính và nhu cầu vào `CLAUDE.md`, Bước 2 là ra lệnh cho AI tự dựng cây thư mục riêng cho phòng ban của anh chị."
- **Đề bài cho học viên:**
  1. Vào Settings > Privacy: Tắt tính năng *"Help improve our AI models"*.
  2. Mở thư mục làm việc cá nhân trên Claude Desktop.
  3. **Thao tác 1 (Nạp danh tính & nhu cầu):** Ra lệnh cho Claude Code tạo file `CLAUDE.md` với thông tin thật của chính bạn: Họ tên, vị trí, phòng ban (Kinh doanh/Kế toán/HR/Marketing/Hành chính), công ty, mục tiêu dự án, cấp trên, quy tắc không emoji, chống bịa số.
  4. **Thao tác 2 (Tự sinh cây thư mục):** Ra lệnh cho Claude đọc `CLAUDE.md` và tự động sinh ra cây thư mục chuẩn hóa tối ưu cho chính ngành nghề/phòng ban của bạn, kèm `_backup/` và file `00-index.md`.
  5. Mở phiên mới và kiểm tra xem AI đã nhớ bối cảnh và cấu trúc thư mục chưa.
- **Prompt gợi ý cho học viên:**
  * **Prompt 1 (Tạo CLAUDE.md):**
    ```
    Dựa trên file demo/CLAUDE.md, hãy tạo file CLAUDE.md tại thư mục gốc cho tôi:
    - Họ tên: [Họ và tên của bạn]
    - Vị trí & Phòng ban: [Ví dụ: Kế toán viên - Phòng Kế toán / Chuyên viên Tuyển dụng - Phòng Nhân sự]
    - Công ty: [Tên công ty của bạn]
    - Mục tiêu dự án: [Mô tả ngắn công việc hàng ngày bạn cần AI hỗ trợ]
    - Cấp trên: [Tên sếp / Chức danh], xưng "em", gọi [anh/chị]
    - Giữ nguyên toàn bộ hệ thống quy tắc cốt lõi về phông Times New Roman 100%, Nghị định 30, Excel chống tràn chữ, cấm emoji, chống bịa số liệu, cấm xóa thư mục và lưu trữ _backup/.
    ```
  * **Prompt 2 (Sinh cây thư mục từ CLAUDE.md):**
    ```
    Đọc file CLAUDE.md vừa tạo. Dựa trên vai trò, phòng ban và mục tiêu dự án của tôi:
    Hãy thiết kế và tự động tạo cây thư mục làm việc chuyên nghiệp (đánh số 01-, 02-...), thư mục _backup/ và file 00-index.md mô tả mục lục cho tôi.
    ```
- **Hỗ trợ của GV & Trợ giảng:** Đi từng bàn kiểm tra màn hình học viên, hướng dẫn học viên gõ lệnh mở phiên mới để kiểm tra kết quả.

---

### [01:50 - 02:15] Lý thuyết 2 & Demo: GitHub Căn Bản — Xem & Tải Tài Liệu Khóa Học

- **Lời dẫn GV:** "Một kỹ năng cực kỳ giá trị mà dân văn phòng hiện đại cần nắm là GitHub. Anh chị đừng sợ chữ 'code'. Với chúng ta, GitHub đơn giản là một kho lưu trữ tài liệu trực tuyến an toàn nhất thế giới, nơi lưu giữ toàn bộ bài giảng, mẫu file và bài tập của khóa học."

#### 1. Các khái niệm GitHub đơn giản hóa:
- **Repository (Repo):** Một thư mục dự án trên GitHub chứa toàn bộ file bài học và demo.
- **Commit:** Một mốc lưu lịch sử thay đổi (như các phiên bản Version 1, Version 2 trong Word).
- **Clone / Download ZIP:** Tải toàn bộ thư mục bài học từ mạng về máy tính của mình chỉ với 1 cú click.

#### 2. Demo GV hướng dẫn học viên thao tác trên GitHub:
- **Bước 1: Xem tài liệu trực tiếp trên web:**
  - GV mở link repository khóa học của CES Global trên trình duyệt.
  - Hướng dẫn học viên cách bấm vào từng thư mục trọn gói theo buổi: `01-buoi-01-...`, `02-buoi-02-...`, chỉ ra rằng mỗi buổi đều có sẵn giáo án, workbook và toàn bộ file `demo/` thực hành.
- **Bước 2: Tải trọn bộ tài liệu về máy tính:**
  - Bấm vào nút màu xanh **`Code`** > Chọn **`Download ZIP`**.
  - Giải nén file ZIP vào thư mục làm việc trên máy.
  - Mở thư mục vừa giải nén trong Claude Desktop để sẵn sàng thực hành cho các buổi tiếp theo.
- **Bước 3: Giới thiệu Personal Access Token (PAT):**
  - Giải thích khái niệm Token: Chìa khóa bảo mật cấp quyền cho AI tương tác với GitHub thay mình mà không làm lộ mật khẩu chính.

---

### [02:15 - 02:30] Thực hành 2 & Tổng Kết Buổi 1

**Thực hành nhanh: Khởi tạo Agent Điều phối đầu tiên**
- **Lời dẫn GV:** "Để khép lại buổi hôm nay, ta sẽ khởi tạo Agent số 1: Trợ lý Điều phối (Orchestrator). Đây là vị tổng quản của Workspace, người sẽ giúp bạn lên kế hoạch và phân chia công việc cho các buổi sau."
- **Prompt gõ vào Claude Code:**
  ```
  Dựa trên file CLAUDE.md vừa tạo, hãy đóng vai Trợ lý Điều phối (Orchestrator) của tôi. 
  Hãy quét toàn bộ thư mục hiện tại, liệt kê các tài liệu sẵn có và đề xuất 3 công việc ưu tiên tôi nên giao cho đội ngũ AI trong tuần này.
  ```
- **Kết quả mong đợi:** Claude Code đọc thư mục, phản hồi đúng vai trò quản lý điều phối, liệt kê các file tài liệu và đưa ra kế hoạch làm việc mạch lạc.

**Tổng kết & Giao bài về nhà:**
1. **Tổng kết 4 điểm chốt Buổi 1:**
   - Đã cài đặt Claude Desktop, bật Claude Code và khóa bảo mật Privacy.
   - Hiểu rõ Mode (Auto), Model (Sonnet/Haiku/Opus), Effort (High/Faster) và Quota/Context Window.
   - Sở hữu file `CLAUDE.md` — nền tảng trí nhớ cho mọi phiên làm việc sau này.
   - Biết dùng GitHub để xem và tải toàn bộ kho tài liệu demo về máy.
2. **Bài tập về nhà:**
   - Hoàn thiện file `CLAUDE.md` với thông tin chi tiết về 3 đầu việc lặp lại nhiều nhất trong tuần của bạn.
   - Kiểm tra thư mục demo của các buổi (01 đến 06) đã sẵn sàng trên máy tính.
   - Chụp ảnh màn hình giao diện Claude Desktop có file `CLAUDE.md` gửi vào nhóm Zalo lớp để điểm danh.
3. **Xem trước Buổi 2:** Bắt tay vào huấn luyện **Agent Quản lý Tài liệu** — đọc báo cáo 14–40 trang, đóng gói Skill đầu tiên và rèn luyện kỹ thuật chống bịa số liệu!

---

## Bảng prompt tổng hợp Buổi 1 (Tra nhanh khi đứng lớp)

| # | Mục đích | Prompt chính xác gõ vào Claude Code | Kết quả mong đợi |
|---|---|---|---|
| **1** | **Tạo file `CLAUDE.md` chuẩn** | `Dựa trên demo/CLAUDE.md, hãy tạo file CLAUDE.md tại gốc: Họ tên [Tên], Vị trí & Phòng ban [Phòng], Mục tiêu dự án [Mục tiêu], Cấp trên [Tên], tuân thủ 100% Times New Roman, Nghị định 30, Excel chống tràn chữ, cấm emoji, chống bịa số, cấm xóa folder, lưu _backup/.` | File `CLAUDE.md` xuất hiện ở gốc thư mục, nạp đầy đủ danh tính và quy tắc. |
| **2** | **Sinh cây thư mục từ `CLAUDE.md`** | `Đọc file CLAUDE.md vừa tạo. Dựa trên vai trò và mục tiêu dự án của tôi: hãy thiết kế và tự động tạo cây thư mục chuẩn hóa (01-, 02-...), thư mục _backup/ và file 00-index.md mô tả mục lục.` | Tự động sinh cây thư mục tối ưu riêng cho phòng ban, có `_backup/` và `00-index.md`. |
| **3** | **Kiểm tra trí nhớ & liên kết** | `Hãy soạn giúp tôi một email ngắn gửi anh Tuấn đối tác và cho tôi biết sau này file báo giá của anh Tuấn sẽ được lưu vào thư mục nào?` | Email chuẩn mực không emoji, xưng hô đúng vai, chỉ đúng thư mục lưu trữ. |
| **4** | **Khởi tạo Agent Điều phối** | `Dựa trên file CLAUDE.md, hãy đóng vai Trợ lý Điều phối của tôi. Quét thư mục hiện tại và đề xuất kế hoạch làm việc tuần này.` | Phản hồi đúng vai trò điều phối, đưa ra danh mục việc mạch lạc. |

---

## Tình huống hay gặp & Cách xử lý sự cố tại lớp

| Tình huống sự cố | Nguyên nhân | Cách xử lý tức thì của Giảng viên & Trợ giảng |
|---|---|---|
| Báo lỗi `Claude command not recognized` | Máy Windows chưa nhận biến môi trường PATH của Node/npm | Chạy lệnh kiểm tra đường dẫn hoặc hướng dẫn học viên dùng trực tiếp qua giao diện tab `</> Code` của Claude Desktop. |
| AI vẫn dùng emoji dù đã dặn trong chat | Chưa có file `CLAUDE.md` hoặc chưa mở phiên mới | Kiểm tra file `CLAUDE.md` đã lưu ở gốc thư mục chưa. Bắt buộc bấm **New Session** để nạp lại bối cảnh. |
| Vòng tròn Context Window chuyển màu đỏ/đầy | Học viên nạp quá nhiều file nặng hoặc chat quá dài trong 1 phiên | Hướng dẫn học viên gõ lệnh `/clear` hoặc mở phiên mới để làm mới cửa sổ ngữ cảnh. |
| Quên mật khẩu hoặc không tải được file trên GitHub | Chưa quen giao diện web GitHub | Hướng dẫn chọn nút xanh `Code` > `Download ZIP` trực tiếp mà không cần đăng nhập phức tạp. |
| Học viên băn khoăn về bảo mật tài liệu công ty | Lo ngại Anthropic đọc dữ liệu | Chiếu lại màn hình Settings > Privacy, xác nhận đã tắt công tắc *"Help improve our AI models"*. |

---

## Tiêu chí hoàn thành Buổi 1
- [ ] Mở được Claude Desktop và kích hoạt giao diện Claude Code thành công.
- [ ] Tắt tính năng chia sẻ dữ liệu huấn luyện trong Settings > Privacy.
- [ ] Nắm rõ ý nghĩa của Mode, Model, Effort, Quota và Context Window.
- [ ] Tạo được file `CLAUDE.md` cá nhân hóa đúng chuẩn và kiểm tra thành công trên phiên mới.
- [ ] Truy cập được GitHub của khóa học và tải bộ tài liệu thực hành về máy tính.
- [ ] Giao việc thành công cho Agent Điều phối đầu tiên.
