# BỘ SLIDE BÀI GIẢNG BUỔI 01: XÂY DỰNG AI WORKSPACE, LÀM CHỦ CLAUDE CODE & GITHUB NỀN TẢNG

> **Đơn vị đào tạo:** CES Global — Trung tâm Đào tạo & Ứng dụng Công nghệ  
> **Chương trình:** Khóa AI Workspace — Làm chủ Agent với Claude Code  
> **Thời lượng:** 150 phút (2,5 giờ) | Live Zoom & VIP LMS  
> **Quy chuẩn hiển thị:** Mỗi cặp dấu ngăn cách `---` tương ứng với 01 slide trình chiếu độc lập. Phần `[Ghi chú Giảng viên]` cung cấp lời dẫn trực tiếp và prompt chính xác để giảng viên đứng lớp.

---

## Slide 01: Slide Tiêu Đề

# KHÓA HỌC: AI WORKSPACE
## Làm Chủ 6 AI Agent Thực Chiến Với Claude Code

### BUỔI 01: XÂY DỰNG AI WORKSPACE, LÀM CHỦ CLAUDE CODE & GITHUB NỀN TẢNG

- **Đơn vị tổ chức:** CES Global — AI Technology & Training Center
- **Website đào tạo:** https://nhanvienai.cesglobal.com.vn
- **Thời lượng:** 150 phút (20:00 – 22:30)
- **Phương châm:** *"Từ dùng AI lẻ tẻ đến sở hữu đội ngũ 6 AI Agent tự động hóa công việc"*

[Ghi chú Giảng viên]: Chào mừng học viên, giới thiệu không khí lớp học. Trấn an học viên không cần biết lập trình, 100% giao tiếp bằng tiếng Việt tự nhiên và tư duy quản trị văn phòng.

---

## Slide 02: Mục Tiêu & Chuẩn Đầu Ra Buổi 01

### Học xong buổi hôm nay, bạn sẽ làm chủ:

1. **Cài đặt & Giao diện:** Kích hoạt Claude Desktop, chuyển sang tab Claude Code (`</> Code`).
2. **Bảo mật dữ liệu:** Thiết lập Privacy Settings để 100% tài liệu không bị đưa vào tập huấn luyện AI.
3. **Bộ thông số vận hành:** Nắm vững Mode, Model, Effort, Quota và kiểm soát Context Window.
4. **Hiến pháp `CLAUDE.md`:** Thiết lập hồ sơ cá nhân và nhu cầu dự án trước tiên để AI hiểu đúng bối cảnh.
5. **Tự động sinh cây thư mục:** Dùng prompt để AI tự thiết kế cây thư mục chuẩn hóa `01-`, `02-`..., `_backup/` và `00-index.md`.
6. **Làm chủ GitHub & Agent Điều phối:** Tải trọn bộ học liệu về máy và giao việc cho Agent số 1.

---

## Slide 03: Thực Trạng Dùng AI Hiện Nay vs Giải Pháp AI Workspace

### Nỗi đau khi dùng AI rời rạc (Chatbot thông thường):
- **Hỏi từng câu rồi tắt:** Mỗi lần mở phiên chat mới lại phải giải thích lại từ đầu: *"Tôi là ai, công ty tôi làm gì..."*.
- **Copy - Dán thủ công:** Mất thời gian sao chép dữ liệu qua lại giữa Word, Excel và cửa sổ chat.
- **Không có trí nhớ & dữ liệu riêng:** Không đọc được file trong máy tính, dễ bịa số liệu, kết quả hên xui.

### Bước chuyển mình lên AI Workspace (Claude Code):
- **Cắm trực tiếp vào thư mục máy tính:** AI đọc, hiểu và xử lý trực tiếp toàn bộ kho tài liệu của bạn.
- **Có trí nhớ dài hạn (`CLAUDE.md`):** Luôn nhớ chức danh, quy tắc văn phong, chuẩn mực doanh nghiệp.
- **Làm việc theo cơ chế Agent:** Nhận lệnh lớn, tự lập kế hoạch nhiều bước và chủ động báo cáo kết quả.

---

## Slide 04: Mô Hình AI Workspace 4 Tầng Cốt Lõi

```
┌─────────────────────────────────────────────────────────────────┐
│  TẦNG 1: TRỢ LÝ ĐIỀU PHỐI (Orchestrator Agent)                  │
│  Bộ não tiếp nhận bài toán lớn, lập kế hoạch, chia việc cho đội │
├─────────────────────────────────────────────────────────────────┤
│  TẦNG 2: 5 AGENT CHUYÊN MÔN THỰC THI (Execution Layer)          │
│  Tài liệu (Buổi 2) · Dữ liệu (Buổi 3) · Báo cáo (Buổi 4)        │
│  Deep Research (Buổi 5) · Hệ thống Capstone (Buổi 6)           │
├─────────────────────────────────────────────────────────────────┤
│  TẦNG 3: SKILL & SYSTEM PROMPT (Reusability Layer)              │
│  Đóng gói quy trình 5 bước thành Skill, tái sử dụng vĩnh viễn  │
├─────────────────────────────────────────────────────────────────┤
│  TẦNG 4: KNOWLEDGE & CONTEXT (Grounding Layer)                  │
│  Hồ sơ CLAUDE.md, cây thư mục 01-, 02-..., dữ liệu thật của bạn │
└─────────────────────────────────────────────────────────────────┘
```

> **Nguyên tắc vàng:** Muốn tầng 1 và tầng 2 chạy chuẩn, tầng 4 (CLAUDE.md & Dữ liệu) phải được xây dựng vững chắc ngay từ Buổi 1!

---

## Slide 05: Đội Ngũ 6 AI Agent Đồng Hành Cùng Bạn

| STT | Tên Agent | Nhiệm vụ chính trong doanh nghiệp | Buổi học |
|:---:|---|---|:---:|
| **1** | **Trợ lý Điều phối** *(Orchestrator)* | Tiếp nhận đề bài lớn, điều phối công việc cho cả đội ngũ | **Buổi 1** |
| **2** | **Quản lý Tài liệu** *(Document Agent)* | Đọc tài liệu dài 40 trang, tóm tắt hợp đồng, chống bịa số | **Buổi 2** |
| **3** | **Phân tích Dữ liệu** *(Data Agent)* | Xử lý file Excel/CSV, vẽ biểu đồ, cắm MCP Drive/Gmail | **Buổi 3** |
| **4** | **Lập Báo cáo** *(Reporting Agent)* | Soạn báo cáo quản trị, đề xuất proposal, tạo dàn ý slide | **Buổi 4** |
| **5** | **Deep Research** *(Research Agent)* | Nghiên cứu đối thủ cạnh tranh, dẫn nguồn kiểm chứng | **Buổi 5** |
| **6** | **Hệ Multi-Agent** *(Capstone)* | Ráp nối 5 agent thành quy trình tự động hóa đầu-cuối | **Buổi 6** |

---

## Slide 06: Khám Phá Claude Desktop & Kích Hoạt Tab Claude Code

### Hai không gian làm việc bên trong Claude Desktop:

1. **Tab Chat thông thường:**
   - Dùng để hỏi đáp ngắn, tra cứu nhanh.
   - Không can thiệp được vào file hệ thống máy tính.

2. **Tab Claude Code (`</> Code`):**
   - Không gian làm việc của Agentic AI.
   - Có khả năng đọc file, tạo file, chỉnh sửa bảng tính, chạy lệnh và điều hành thư mục dự án.
   - Giao diện có thanh nhập lệnh, danh sách file bên trái và cửa sổ lệnh tương tác.

---

## Slide 07: Bảo Mật Dữ Liệu Doanh Nghiệp (Privacy Settings)

### Quy tắc số 1 khi mang AI vào doanh nghiệp: Bảo vệ bí mật kinh doanh

- **Nguy cơ:** Mặc định một số nền tảng AI dùng dữ liệu người dùng chat để huấn luyện (train) mô hình AI thế hệ tiếp theo.
- **Thao tác bắt buộc trước khi học:**
  1. Mở ứng dụng Claude Desktop.
  2. Bấm vào ảnh đại diện / góc tài khoản > Chọn **`Settings`**.
  3. Chọn mục **`Privacy`**.
  4. Tắt công tắc: **`Help improve our AI models`** (Turn OFF).
- **Kết quả:** Toàn bộ file hợp đồng, bảng lương, báo cáo tài chính của công ty bạn được bảo mật tuyệt đối, Anthropic cam kết không dùng để huấn luyện AI.

---

## Slide 08: Làm Chủ Chế Độ Cấp Quyền Thực Thi (Mode)

| Chế độ (Mode) | Cơ chế hoạt động | Khuyên dùng khi nào? |
|---|---|---|
| **`Auto`** *(Mặc định)* | AI tự động phân tích và ra quyết định thực thi các bước thông thường. | Thực hành hàng ngày trong lớp học. |
| **`Manual`** | Mỗi lần đọc/sửa file hay chạy lệnh, AI đều dừng lại hỏi xin phép con người. | Khi rà soát dữ liệu cực kỳ nhạy cảm. |
| **`Accept edits`** | Tự động đồng ý cho AI sửa nội dung file mà không cần bấm xác nhận từng lần. | Khi giao việc chỉnh sửa văn bản hàng loạt. |
| **`Plan`** | AI chỉ lập kế hoạch chi tiết từng bước ra màn hình, chưa chạm vào file. | Khi giải quyết bài toán lớn, phức tạp. |
| **`Bypass permissions`**| Cho phép chạy toàn quyền, bỏ qua mọi thông báo xác nhận. | Dành cho chuyên gia chạy script tự động. |

---

## Slide 09: Lựa Chọn Model AI & Thanh Trượt Tư Duy (Effort)

### 1. Bộ 3 mô hình Claude thế hệ mới:
- **`Haiku 4.5`:** Tốc độ cực nhanh, chi phí thấp, tối ưu cho tác vụ phân loại, lọc email, sắp xếp dữ liệu đơn giản.
- **`Sonnet 5`:** Mô hình cân bằng hoàn hảo nhất, lập luận sắc bén, viết báo cáo hay, là "ngựa chiến" chính của khóa học.
- **`Opus 5` / `Fable 5.1`:** Bộ não suy luận sâu, xử lý bài toán logic phức tạp, chiến lược đa tầng và tài chính cao cấp.

### 2. Thanh trượt nỗ lực suy nghĩ (Effort Slider):
- **`Faster` (Low):** Phản hồi tức thì, trả lời thẳng vào câu hỏi.
- **`Smarter` (Medium / High):** AI kích hoạt cơ chế suy nghĩ ngầm (Thinking Process), tự phản biện trước khi xuất kết quả.

---

## Slide 10: Quota, Token & Cửa Sổ Ngữ Cảnh (Context Window)

### Tại sao dùng AI một lúc lâu thì AI bắt đầu "bị lú" và trả lời ngớ ngẩn?

- **Cửa sổ ngữ cảnh (Context Window):** Bộ nhớ ngắn hạn trong 1 phiên làm việc. Biểu thị bằng **vòng tròn phần trăm** ở góc dưới giao diện.
- **Cơ chế:** Khi bạn nạp quá nhiều file nặng (file Excel hàng chục ngàn dòng hoặc tài liệu vài trăm trang), Context Window bị đầy (chuyển sang màu vàng/đỏ).
- **Hậu quả:** AI bị quá tải, bắt đầu quên chỉ thị ban đầu và sinh ra hiện tượng bịa số liệu.
- **Giải pháp chuyên nghiệp:**
  * Thường xuyên dùng lệnh `/clear` hoặc mở phiên mới (**New Session**) sau khi hoàn thành xong 1 tác vụ.
  * Chỉ nạp đúng file cần xử lý, không nạp cả ổ đĩa vào context.

---

## Slide 11: Phân Biệt 3 Tầng Ký Ức Khi Dùng AI

```
┌─────────────────────────────────────────────────────────────────────────┐
│ 1. CHAT PROMPT (Tạm thời): Chỉ nhớ trong 1 câu chat, tắt đi là mất      │
├─────────────────────────────────────────────────────────────────────────┤
│ 2. CLAUDE MEMORY (Cá nhân): Lưu trên đám mây tài khoản (Settings>Memory)│
│    Áp dụng riêng cho tài khoản của bạn ở mọi phiên chat thông thường    │
├─────────────────────────────────────────────────────────────────────────┤
│ 3. FILE CLAUDE.md (Dự án & Doanh nghiệp) - BẮT BUỘC DÙNG CHO WORKSPACE:  │
│    Lưu thành file vật lý ngay tại thư mục dự án trên ổ đĩa máy tính     │
│    Áp dụng đồng bộ cho cả bạn, đồng nghiệp và toàn bộ đội ngũ AI Agent │
│    Đưa lên GitHub được, chuyển giao công việc chỉ bằng 1 cú click!      │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Slide 12: Triết Lý Nền Tảng: Thiết Lập `CLAUDE.md` TRƯỚC HẾT

> **NGUYÊN TẮC CỐT LÕI CỦA AI WORKSPACE:**  
> *"Muốn AI làm việc đúng, trước hết phải dạy AI hiểu TÔI LÀ AI, TÔI LÀM VIỆC GÌ, Ở PHÒNG BAN NÀO, VÀ TÔI CÓ NHU CẦU GÌ ĐỐI VỚI DỰ ÁN NÀY."*

### Sai lầm kinh điển của người mới:
- Nhảy vào ra lệnh cho AI tạo thư mục ngay ➔ AI tạo ra cây thư mục chung chung, không sát với thực tế công việc.

### Cách tiếp cận chuyên nghiệp của CES Global:
- **Bước 1:** Nạp file `CLAUDE.md` trước để AI hiểu rõ danh tính, vị trí công tác và mục tiêu cụ thể của dự án.
- **Bước 2:** Ra lệnh cho AI tự đọc `CLAUDE.md` để suy luận và tự động kiến tạo không gian làm việc tối ưu nhất cho chính bạn!

---

## Slide 13: "Hiến Pháp" `CLAUDE.md` Chuẩn Doanh Nghiệp Gồm Những Gì?

1. **Hồ sơ làm việc cá nhân:** Họ tên, vị trí, phòng ban, công ty, quy tắc xưng hô cấp trên/đối tác.
2. **Quy định phông chữ bắt buộc:** 100% sử dụng **Times New Roman** cho Word, Excel, PDF, Báo cáo.
3. **Chuẩn thể thức hành chính Việt Nam:** Tuân thủ Nghị định 30/2020/NĐ-CP (cỡ chữ, lề, giãn dòng).
4. **Bố cục Excel chống dồn chữ:** Tách riêng cột STT, độ rộng cột rộng rãi, tự động tính chiều cao dòng.
5. **Kỷ luật chống bịa số liệu:** Không có trong tài liệu phải ghi `[Tài liệu không đề cập]`, luôn khai báo nguồn.
6. **Bảo vệ an toàn thư mục:** Tuyệt đối cấm xóa thư mục, cấm xóa hàng loạt, chỉ cập nhật cục bộ.
7. **Quy tắc Single Active File & `_backup/`:** Bên ngoài chỉ giữ 1 file mới nhất, bản cũ đưa vào `_backup/`.
8. **Quy ước đánh số 2 chữ số:** Mọi thư mục theo quy trình phải có tiền tố `01-`, `02-`, `03-`...

---

## Slide 14: Demo GV — Bước 1: Khởi Tạo File `CLAUDE.md` Chuẩn

- **Lời dẫn GV:** *"Tôi bắt đầu bằng việc nạp danh tính và nhu cầu dự án của tôi vào file CLAUDE.md để Claude Code hiểu rõ tôi là ai."*
- **Prompt gõ vào Claude Code:**
  ```
  Dựa trên mẫu demo/CLAUDE.md, hãy tạo file CLAUDE.md tại thư mục gốc cho tôi:
  - Họ tên: Nguyễn Văn An - Chuyên viên Kinh doanh cấp cao tại CES Global
  - Mục tiêu & Nhu cầu dự án: Quản lý toàn diện quy trình kinh doanh, lưu trữ hồ sơ khách hàng, phát hành báo giá, theo dõi hợp đồng, phân tích doanh số Excel/CSV và lập báo cáo tuần/tháng.
  - Cấp trên: Chị Mai (Trưởng phòng), xưng "em", gọi "chị"
  - Tuân thủ nghiêm ngặt: 100% Times New Roman, Nghị định 30/2020/NĐ-CP, bố cục Excel chống tràn chữ, tuyệt đối không bịa số liệu, cấm xóa folder, và duy trì _backup/.
  ```
- **Kết quả:** File `CLAUDE.md` xuất hiện tại thư mục gốc mang đầy đủ danh tính và các quy tắc doanh nghiệp.

---

## Slide 15: Demo GV — Bước 2: AI Tự Động Sinh Cây Thư Mục Từ `CLAUDE.md`

- **Lời dẫn GV:** *"Bây giờ AI đã hiểu rõ tôi là ai và công việc của tôi rồi. Tôi không cần nghĩ tên folder nữa, mà ra lệnh cho AI tự động thiết kế cây thư mục tối ưu!"*
- **Prompt gõ vào Claude Code:**
  ```
  Đọc file CLAUDE.md vừa tạo. Dựa trên vai trò Chuyên viên Kinh doanh, mục tiêu dự án và các quy tắc quản trị trong đó:
  1. Hãy thiết kế và tự động tạo cây thư mục làm việc chuyên nghiệp (đánh số thứ tự 01-, 02-, 03-...).
  2. Tạo thư mục _backup/ theo đúng quy tắc lưu trữ an toàn.
  3. Tạo sẵn file 00-index.md tại thư mục gốc giải thích mục đích từng thư mục con.
  ```
- **Kết quả:** Claude tự động tạo cấu trúc hoàn chỉnh:
  * `01-khach-hang/` | `02-bao-gia/` | `03-hop-dong/` | `04-so-lieu/` | `05-bao-cao/`
  * `_backup/` và file mục lục `00-index.md`!

---

## Slide 16: Demo GV — Bước 3: Mở Phiên Mới Kiểm Tra Sự Đồng Bộ

- **Lời dẫn GV:** *"Bây giờ tôi mở phiên mới bằng lệnh /clear hoặc nút New Session. Tôi không nhắc lại tôi là ai nữa, xem AI có nhớ và định vị được thư mục không."*
- **Prompt gõ vào Claude Code:**
  ```
  Hãy soạn giúp tôi một email ngắn gửi anh Tuấn giới thiệu giải pháp phần mềm của CES Global, và cho tôi biết sau này file báo giá của anh Tuấn sẽ được lưu vào thư mục nào trong dự án này?
  ```
- **Kết quả mong đợi:**
  - Xưng hô đúng chuẩn: Xưng *"em"*, gọi *"anh Tuấn"*.
  - Văn phong công sở trang trọng, **hoàn toàn không có icon emoji**.
  - Trả lời chính xác: File báo giá sẽ được lưu vào thư mục **`02-bao-gia/`**!

---

## Slide 17: Thực Hành 1 Dành Cho Học Viên (25 Phút)

### Đề bài thực hành trực tiếp trên máy của bạn:

1. **Bước 1 (Bảo mật):** Kiểm tra Settings > Privacy, đảm bảo đã tắt tính năng luyện AI.
2. **Bước 2 (Nạp Hiến pháp `CLAUDE.md`):**
   - Ra lệnh cho Claude tạo file `CLAUDE.md` mang thông tin thật của bạn (Họ tên, phòng ban Kế toán/Sale/HR/Marketing, công ty, cấp trên và mục tiêu công việc).
3. **Bước 3 (AI tự sinh cây thư mục):**
   - Ra lệnh cho Claude đọc `CLAUDE.md` và tự động sinh cây thư mục phòng ban có đánh số `01-`, `02-`..., thư mục `_backup/` và file `00-index.md`.
4. **Bước 4 (Kiểm tra trí nhớ):**
   - Mở New Session (`/clear`), soạn thử một email công việc để xác nhận AI đã thuộc lòng quy tắc và cấu trúc thư mục của bạn.

---

## Slide 18: GitHub Nền Tảng Cho Người Không Phải Lập Trình Viên

### GitHub là gì đối với dân văn phòng?
- **Không phải công cụ viết mã phức tạp!**
- GitHub là một **kho lưu trữ tài liệu đám mây an toàn nhất hành tinh**, có khả năng lưu giữ toàn bộ lịch sử thay đổi phiên bản.

### 4 khái niệm cần nắm:
1. **Repository (Repo):** Một thư mục dự án chứa toàn bộ học liệu của khóa học.
2. **Commit:** Một mốc lưu lịch sử phiên bản (như bản v1, v2, v3 nhưng không bao giờ bị ghi đè mất file).
3. **Clone / Download ZIP:** Tải toàn bộ kho tài liệu từ mạng về máy tính trong 1 giây.
4. **Personal Access Token (PAT):** Chìa khóa cấp quyền an toàn để AI tự đồng bộ tài liệu lên kho lưu trữ.

---

## Slide 19: Demo GV: Khám Phá Repo & Tải Bộ Học Liệu Về Máy

### 2 thao tác học viên cần làm ngay tại lớp:

1. **Xem tài liệu trực tiếp trên Web:**
   - Mở link GitHub khóa học do CES Global cung cấp.
   - Thấy cấu trúc trọn gói từng buổi: `01-buoi-01-...`, `02-buoi-02-...`. Mỗi buổi có sẵn Giáo án, Workbook và file `demo/`.

2. **Tải trọn bộ về máy tính:**
   - Bấm nút màu xanh lá cây **`Code`** ở góc trên bên phải.
   - Chọn **`Download ZIP`**.
   - Giải nén vào thư mục học tập trên máy tính để sẵn sàng cho các buổi tiếp theo.

---

## Slide 20: Khởi Tạo Agent Số 1 — Trợ Lý Điều Phối (Orchestrator)

- **Vai trò:** Vị "tổng quản" của Workspace — người nhận yêu cầu lớn, phân chia công việc và chỉ huy các agent chuyên môn trong các buổi sau.
- **Prompt gõ vào Claude Code:**
  ```
  Dựa trên file CLAUDE.md vừa tạo, bạn hãy đóng vai Trợ lý Điều phối (Orchestrator Agent) của tôi.
  Hãy quét toàn bộ thư mục hiện tại của tôi, liệt kê danh sách tài liệu đang có và đề xuất kế hoạch 3 bước để tự động hóa công việc của tôi trong tuần này.
  ```
- **Kết quả mong đợi:** AI phản hồi đúng vai trò quản lý điều phối, quét sạch cây thư mục vừa dựng và đưa ra lộ trình làm việc mạch lạc.

---

## Slide 21: Bảng Tra Nhanh 4 Câu Prompt Cốt Lõi Buổi 01

| # | Nhiệm vụ | Câu lệnh Prompt chính xác gõ vào Claude Code |
|:---:|---|---|
| **1** | **Tạo `CLAUDE.md`** | `Dựa trên demo/CLAUDE.md, hãy tạo file CLAUDE.md tại gốc: Họ tên [Tên], Vị trí & Phòng ban [Phòng], Mục tiêu dự án [Mục tiêu], Cấp trên [Tên], tuân thủ 100% Times New Roman, Nghị định 30, Excel chống tràn chữ, cấm emoji, chống bịa số, cấm xóa folder, lưu _backup/.` |
| **2** | **Sinh cây thư mục** | `Đọc file CLAUDE.md vừa tạo. Dựa trên vai trò và mục tiêu dự án của tôi: hãy thiết kế và tự động tạo cây thư mục chuẩn hóa (01-, 02-...), thư mục _backup/ và file 00-index.md mô tả mục lục.` |
| **3** | **Kiểm tra trí nhớ** | `Hãy soạn giúp tôi một email ngắn gửi anh Tuấn đối tác và cho tôi biết sau này file báo giá của anh Tuấn sẽ được lưu vào thư mục nào?` |
| **4** | **Khởi tạo Agent 1** | `Dựa trên file CLAUDE.md, hãy đóng vai Trợ lý Điều phối của tôi. Quét thư mục hiện tại và đề xuất kế hoạch làm việc tuần này.` |

---

## Slide 22: Tổng Kết Buổi 01 & Xem Trước Buổi 02

### 4 thành tựu bạn cầm về hôm nay:
- [x] AI Workspace hoàn chỉnh trên Claude Desktop, bảo mật an toàn 100%.
- [x] Làm chủ Mode, Model, Effort, Quota & Context Window.
- [x] Sở hữu "Hiến pháp" `CLAUDE.md` và cây thư mục phòng ban chuẩn hóa.
- [x] Kích hoạt thành công Agent Điều phối đầu tiên.

### Bài tập về nhà:
1. Tinh chỉnh `CLAUDE.md` với 3 đầu việc thường xuyên lặp lại trong tuần của bạn.
2. Mở thư mục `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/` để sẵn sàng dữ liệu.

### Xem trước Buổi 02:
> **Agent Quản Lý Tài Liệu:** Đọc báo cáo 40 trang trong 3 phút, đóng gói quy trình thành Skill `tom-tat-tai-lieu` và thực chiến kỹ thuật thép **Chống bịa số liệu!**
