# Workbook Buổi 01: Xây Dựng AI Workspace, Làm Chủ Claude Code & GitHub Nền Tảng

> Sổ tay thực hành dành cho HỌC VIÊN.  
> In ra hoặc mở song song với Claude Desktop để thao tác theo từng bước. Các câu prompt trong khối xám có thể copy – dán trực tiếp.

---

## Mục tiêu của bạn hôm nay
1. Mở và vận hành trơn tru Claude Code trong Claude Desktop trên máy tính cá nhân.
2. Thiết lập bảo mật dữ liệu doanh nghiệp (tắt tính năng chia sẻ dữ liệu train AI).
3. Làm chủ 4 thông số cốt lõi trên giao diện: **Mode, Model, Effort, Quota & Context Window**.
4. Tự tay viết file `CLAUDE.md` — chiếc "thẻ căn cước" giúp AI luôn nhớ bạn là ai, làm việc ra sao.
5. Làm quen với GitHub: xem tài liệu bài giảng online và tải toàn bộ kho bài tập về máy.
6. Khởi tạo Agent Điều phối (Orchestrator) đầu tiên của bạn.

---

## Chuẩn bị trước khi bắt đầu
- [ ] Máy tính đã cài đặt **Claude Desktop** và đăng nhập tài khoản theo hướng dẫn của CES Global.
- [ ] Tạo sẵn 1 thư mục làm việc trên máy tính (ví dụ: `C:\AI-Workspace` hoặc `D:\Khoa-Hoc-AI`).
- [ ] Mở ứng dụng Claude Desktop và chuyển sang tab **`</> Code` (Claude Code)**.

---

## PHẦN A: Thiết lập Bảo mật Dữ liệu & Khám phá Giao diện

### Bước 1: Khóa bảo mật dữ liệu doanh nghiệp (Bắt buộc)
Khi dùng AI cho công việc, bảo mật là ưu tiên số 1:
1. Trong Claude Desktop, bấm vào biểu tượng **Settings** (bánh răng) ở menu góc trái.
2. Chọn mục **Privacy**.
3. Tìm dòng chữ **"Help improve our AI models"** (Cho phép dùng dữ liệu chat/code để huấn luyện AI).
4. **Gạt TẮT (OFF)** công tắc này.
> *Ý nghĩa:* Dữ liệu hội thoại và các file tài liệu bạn nạp vào sẽ không bao giờ bị sử dụng để huấn luyện AI công cộng.

### Bước 2: Hiểu 4 thông số điều khiển trên thanh công cụ
Quan sát thanh dưới cùng của cửa sổ Claude Code:

| Thông số | Nằm ở đâu | Ý nghĩa thực tế | Bạn nên chọn |
|---|---|---|---|
| **Mode** | Góc dưới bên trái | Chế độ cấp quyền cho AI: `Auto` (AI tự xử lý), `Manual` (hỏi trước khi sửa), `Accept edits` (tự lưu), `Plan` (lên kế hoạch trước). | **Auto [Start]** |
| **Model** | Góc dưới bên phải | Bộ não AI: `Haiku 4.5` (nhanh, nhẹ), `Sonnet 5` (toàn năng văn phòng), `Opus 5` / `Fable 5.1` (suy luận logic sâu). | **Sonnet 5** (hoặc Fable 5.1) |
| **Effort** | Kế bên tên Model | Mức độ nỗ lực tư duy: thanh trượt từ `Faster` (nhanh) đến `Smarter` (thông minh sâu sắc). | **High** khi cần phân tích kỹ |
| **Vòng tròn Context** | Góc dưới cùng bên phải | "Thước đo bộ nhớ ngắn hạn": mỗi từ ngữ và trang tài liệu nạp vào sẽ làm vòng tròn đầy dần. | Giữ vòng tròn thoáng, mở phiên mới khi đầy |

### Bước 3: Kích hoạt & Quản lý Ký ức Cá nhân (Claude Memory)
1. Trong **Settings**, chọn mục **Memory** (ngay dưới Capabilities).
2. Bật công tắc **Memory** sang ON.
3. Bấm **View and manage memory** để xem danh sách các sở thích và thông tin Claude đã ghi nhớ về bạn.
4. *Mẹo chủ động:* Bạn có thể gõ thẳng trong chat: `Hãy nhớ rằng tôi luôn làm việc tại phòng Kinh doanh và xưng em với khách hàng.` để Claude tự nạp vào Memory.

---

## PHẦN B: Tạo File `CLAUDE.md` Chuẩn Doanh Nghiệp (Để AI Hiểu Bạn Là Ai & Nhu Cầu Của Bạn)

> **Nguyên tắc cốt lõi:** Muốn AI làm việc chuẩn xác, trước hết phải dạy AI hiểu *bạn là ai, bạn làm việc gì, ở phòng ban nào, và bạn có nhu cầu gì đối với dự án này*. File `CLAUDE.md` chính là "Hiến pháp" của Workspace — lưu trữ danh tính cá nhân, mục tiêu dự án và toàn bộ quy tắc làm việc chuẩn mực.

Dán câu lệnh sau vào Claude Code để tạo file `CLAUDE.md` cá nhân hóa từ mẫu có sẵn:

```
Dựa trên file demo/CLAUDE.md (hoặc 07-mau-cau-hinh-linh-kien/CLAUDE-md-chuan-doanh-nghiep.md), hãy tạo cho tôi một file CLAUDE.md tại thư mục gốc với các thông tin của tôi:
- Họ và tên: [Điền họ và tên của bạn, ví dụ: Nguyễn Văn An]
- Vị trí & Chức danh: [Ví dụ: Chuyên viên Kinh doanh / Kế toán viên / Trưởng phòng Marketing]
- Phòng ban: [Kinh doanh / Kế toán / Nhân sự / Marketing / Hành chính / Ban Giám đốc]
- Công ty: [Tên công ty hoặc doanh nghiệp của bạn]
- Mục tiêu & Nhu cầu dự án: [Mô tả ngắn gọn công việc hàng ngày và bài toán bạn cần AI hỗ trợ xử lý trong dự án này]
- Cấp trên trực tiếp: [Tên sếp / Chức danh], xưng "em", gọi [anh/chị]

Yêu cầu giữ nguyên toàn bộ hệ thống quy tắc quản trị cốt lõi:
1. Quy định phông chữ bắt buộc: 100% Times New Roman cho Word (.docx), Excel (.xlsx), PDF (.pdf), HTML/báo cáo.
2. Chuẩn thể thức hành chính Việt Nam: Nghị định 30/2020/NĐ-CP (Quốc hiệu, Tiêu ngữ, Body text giãn dòng 1.15-1.5, căn đều 2 bên).
3. Bố cục Excel chống dồn chữ & đè dòng: Tách riêng cột STT (width 6-8, center), cột text rộng rãi (25-40, wrap text), chiều cao dòng động.
4. Kỷ luật chống bịa số liệu: Trích xuất chính xác 100%, thiếu thông tin ghi [Tài liệu không đề cập], luôn khai báo nguồn kiểm chứng.
5. Bảo vệ an toàn file & thư mục: Tuyệt đối không xóa thư mục (Folder), không xóa hàng loạt, chỉ cập nhật cục bộ tại chỗ.
6. Duy trì file duy nhất & auto-archive: Bên ngoài chỉ giữ 1 file mới nhất, tự động lưu bản cũ vào _backup/.
7. Tự động kiểm tra thư mục & đánh số thứ tự tuần tự: Tiền tố 01_, 02_, 03_... và tự động đánh số lại Sheet Excel liên tục.
```

---

## PHẦN C: Ra Lệnh Cho AI Tự Sinh Cây Thư Mục Chuẩn Hóa Dựa Trên `CLAUDE.md`

> Vì Claude Code đã hiểu rõ danh tính, phòng ban và mục tiêu dự án của bạn từ file `CLAUDE.md`, bạn **không cần tạo folder thủ công**. Chỉ cần ra lệnh, AI sẽ tự động phân tích nhu cầu và tạo cây thư mục chuẩn hóa riêng cho bạn!

### Cách 1: Ra lệnh AI tự phân tích và thiết kế tối ưu (Khuyên dùng)
```
Đọc file CLAUDE.md vừa tạo. Dựa trên vị trí công tác, phòng ban và mục tiêu dự án của tôi:
1. Hãy thiết kế và tự động tạo cây thư mục làm việc chuyên nghiệp, tối ưu nhất cho công việc của tôi (bắt buộc đánh số thứ tự 2 chữ số: 01-, 02-, 03-...).
2. Tạo thư mục _backup/ theo đúng quy tắc lưu trữ phiên bản cũ.
3. Tạo sẵn file 00-index.md tại thư mục gốc giải thích mục đích và danh mục tài liệu của từng thư mục con vừa tạo.
```

### Cách 2: Chọn mẫu cây thư mục định sẵn theo phòng ban
Nếu bạn muốn cấu trúc cụ thể ngay, hãy chọn prompt theo phòng ban của bạn:

- **Dành cho Phòng Kinh doanh (Sales):**
  ```
  Đọc CLAUDE.md. Hãy tạo giúp tôi cấu trúc cây thư mục chuyên nghiệp cho Phòng Kinh doanh:
  - 01-khach-hang/ : Hồ sơ, lịch sử trao đổi từng khách hàng
  - 02-bao-gia/    : Các bản báo giá đã gửi
  - 03-hop-dong/   : Hợp đồng kinh tế đã ký
  - 04-so-lieu/    : File Excel/CSV theo dõi doanh số và đơn hàng
  - 05-bao-cao/    : Báo cáo tuần, báo cáo tháng
  - _backup/       : Thư mục lưu trữ phiên bản tài liệu cũ
  Đồng thời tạo file 00-index.md tại thư mục gốc giải thích mục đích từng thư mục trên.
  ```

- **Dành cho Phòng Kế toán & Tài chính:**
  ```
  Đọc CLAUDE.md. Hãy tạo giúp tôi cấu trúc cây thư mục chuyên nghiệp cho Phòng Kế toán:
  - 01-hoa-don/      : Hóa đơn chứng từ đầu vào, đầu ra
  - 02-cong-no/      : Sổ theo dõi công nợ phải thu, phải trả
  - 03-bao-cao-thue/ : Tờ khai thuế, báo cáo thuế định kỳ
  - 04-so-lieu/      : File dữ liệu tài chính, sổ cái Excel/CSV
  - 05-bao-cao/      : Báo cáo tài chính, phân tích chi phí
  - _backup/         : Thư mục lưu trữ phiên bản tài liệu cũ
  Đồng thời tạo file 00-index.md tại thư mục gốc giải thích mục đích từng thư mục trên.
  ```

- **Dành cho Phòng Marketing & Nội dung:**
  ```
  Đọc CLAUDE.md. Hãy tạo giúp tôi cấu trúc cây thư mục chuyên nghiệp cho Phòng Marketing:
  - 01-noi-dung/    : Bài viết fanpage, blog website, kịch bản video
  - 02-chien-dich/  : Kế hoạch và timeline từng chiến dịch
  - 03-hinh-anh/    : Tư liệu hình ảnh, banner, logo thương hiệu
  - 04-so-lieu/     : Số liệu chạy ads, traffic, tỷ lệ chuyển đổi
  - 05-bao-cao/     : Báo cáo hiệu quả chiến dịch hàng tuần/tháng
  - _backup/        : Thư mục lưu trữ phiên bản tài liệu cũ
  Đồng thời tạo file 00-index.md tại thư mục gốc giải thích mục đích từng thư mục trên.
  ```

- **Dành cho Phòng Nhân sự (HR) & Hành chính:**
  ```
  Đọc CLAUDE.md. Hãy tạo giúp tôi cấu trúc cây thư mục chuyên nghiệp cho Phòng Nhân sự:
  - 01-tuyen-dung/  : Hồ sơ ứng viên, CV, bài test đánh giá
  - 02-onboarding/  : Quy trình và tài liệu đón nhân sự mới
  - 03-hop-dong-ld/ : Hợp đồng lao động, phụ lục cam kết
  - 04-cham-cong/   : Bảng theo dõi chấm công và phép năm
  - 05-bao-cao/     : Báo cáo biến động nhân sự, kế hoạch đào tạo
  - _backup/        : Thư mục lưu trữ phiên bản tài liệu cũ
  Đồng thời tạo file 00-index.md tại thư mục gốc giải thích mục đích từng thư mục trên.
  ```

### Bước kiểm tra trí nhớ & cấu trúc qua phiên mới
1. Bấm nút **New Session** (hoặc gõ `/clear`) để mở một phiên chat hoàn toàn mới.
2. Gõ câu lệnh kiểm tra:
```
Hãy soạn giúp tôi một email ngắn gửi anh Tuấn đối tác hẹn lịch làm việc, và cho tôi biết sau này tài liệu gửi anh Tuấn sẽ được lưu vào thư mục nào?
```
3. **Đối chiếu kết quả:**
   - [ ] AI có xưng hô đúng vai vế bạn đã dặn trong `CLAUDE.md` không?
   - [ ] AI có loại bỏ hoàn toàn các icon emoji không?
   - [ ] AI có xác định chính xác tên thư mục lưu tài liệu vừa tạo không?

---

## PHẦN D: Khám Phá GitHub — Xem & Tải Tài Liệu Khóa Học

### 1. GitHub là gì đối với dân văn phòng?
Không cần phải là lập trình viên mới dùng GitHub. Với chúng ta:
- GitHub là kho lưu trữ tài liệu trực tuyến của lớp học.
- Đảm bảo bạn luôn tải được phiên bản giáo án, slide và file demo mới nhất từ giảng viên.

### 2. Hướng dẫn tải tài liệu khóa học về máy
1. Mở đường link GitHub của khóa học do CES Global cung cấp trên trình duyệt.
2. Khám phá các thư mục (Kiến trúc trọn gói theo từng Buổi học):
   - `00-tong-quan/`: Tài liệu tổng quan, định hướng và checklist toàn khóa.
   - `01-buoi-01-ai-workspace-claude-code/`: Trọn gói Buổi 1 (Giáo án, Workbook, Slide, Demo).
   - `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/`: Trọn gói Buổi 2 (Giáo án, Workbook, Demo).
   - `03` đến `06`: Các buổi học tương ứng, mỗi buổi đều có sẵn tài liệu và file thực hành tại chỗ.
   - `07-mau-cau-hinh-linh-kien/`: Kho linh kiện cấu hình chuẩn (CLAUDE.md mẫu, MCP, Skill).
3. **Cách tải nhanh nhất:**
   - Tìm nút màu xanh lá cây ghi chữ **`Code`** ở phía trên bên phải.
   - Bấm vào và chọn **`Download ZIP`**.
   - Lưu file về máy và giải nén vào thư mục học tập của bạn.

---

## PHẦN E: Khởi Tạo Agent Điều Phối (Orchestrator Agent)

Agent Điều phối là "tổng quản" của Workspace — người tiếp nhận yêu cầu lớn và lên kế hoạch làm việc.

Dán prompt sau vào Claude Code:
```
Dựa trên file CLAUDE.md của tôi, bạn hãy đóng vai Trợ lý Điều phối (Orchestrator Agent). 
Hãy quét toàn bộ thư mục hiện tại của tôi, liệt kê danh sách tài liệu đang có và đề xuất kế hoạch 3 bước để số hóa và tự động hóa công việc của tôi trong khóa học này.
```

---

## Checklist Hoàn Thành Buổi 01
Đánh dấu tích khi bạn hoàn thành:
- [ ] Đã tắt tính năng chia sẻ dữ liệu huấn luyện trong Settings > Privacy.
- [ ] Hiểu được ý nghĩa của Mode (Auto), Model (Sonnet), Effort (High) và Context Window.
- [ ] Tạo thành công file `CLAUDE.md` mang thông tin và phong cách của chính mình.
- [ ] Mở phiên mới và xác nhận Claude tự động tuân thủ nội dung `CLAUDE.md`.
- [ ] Biết cách xem và tải trọn bộ file demo từ GitHub về máy.
- [ ] Giao việc thành công cho Agent Điều phối đầu tiên.

---

## Bài Tập Về Nhà
1. **Tinh chỉnh file `CLAUDE.md`:** Bổ sung thêm 3 công việc bạn thường xuyên phải làm lặp lại mỗi tuần (ví dụ: làm báo cáo tuần, soạn báo giá, lọc danh sách công nợ).
2. **Chuẩn bị bộ file demo Buổi 02:** Đảm bảo thư mục `02-buoi-02-quan-ly-tai-lieu-chong-bia-so/demo/` đã có sẵn trên máy để sẵn sàng cho **Buổi 02: Đọc tài liệu dài 40 trang & Kỹ thuật chống bịa số liệu!**
