# HỆ THỐNG QUY TẮC LÀM VIỆC & QUẢN TRỊ AI WORKSPACE (CLAUDE.md)
<!-- DÀNH CHO HỌC VIÊN KHÓA AI WORKSPACE - CES GLOBAL -->
<!-- Học viên sao chép file này vào thư mục làm việc của dự án (CLAUDE.md) hoặc thư mục cá nhân C:\Users\<User>\.claude\CLAUDE.md -->

## 1. HỒ SƠ LÀM VIỆC CÁ NHÂN (USER PROFILE)

- **Họ và tên:** [Điền họ và tên của bạn, ví dụ: Nguyễn Văn An]
- **Vị trí / Chức danh:** [Điền vị trí, ví dụ: Chuyên viên Kinh doanh / Kế toán / Trợ lý / Quản trị vận hành]
- **Phòng ban:** [Kinh doanh / Kế toán / Nhân sự / Marketing / Hành chính / Ban Giám đốc]
- **Đơn vị công tác:** [Tên công ty hoặc doanh nghiệp của bạn]
- **Quy tắc xưng hô nội bộ & đối ngoại:**
  * Với cấp trên ([Tên sếp]): Xưng "em", gọi "[anh/chị]"
  * Với đồng nghiệp: Xưng "mình" hoặc "tôi", gọi tên
  * Với đối tác / khách hàng: Xưng "em" hoặc "bên em", gọi "Anh/Chị + [Tên]"
- **Văn phong bắt buộc:** Trang trọng, rõ ràng, gãy gọn, chuẩn mực công sở.
- **Quy định về Icon / Emoji:** TUYỆT ĐỐI KHÔNG TỰ Ý DÙNG BIỂU TƯỢNG CẢM XÚC (EMOJI) trong hợp đồng, văn bản hành chính, báo cáo quản trị và email gửi đối tác/khách hàng.

---

## 2. QUI ĐỊNH PHÔNG CHỮ BẮT BUỘC (FONT MANDATE)

TẤT CẢ các file tài liệu được tạo ra hoặc chỉnh sửa bao gồm:
- Microsoft Word (`.docx`)
- Microsoft Excel (`.xlsx`)
- File PDF (`.pdf`)
- HTML / Google Docs / Báo cáo văn bản
➔ **BẮT BUỘC 100% sử dụng phông chữ: Times New Roman.**
- Tuyệt đối không tự ý sử dụng Calibri, Arial, Segoe UI, Roboto hay bất kỳ phông chữ mặc định nào khác khi tạo mới hoặc cập nhật các file văn bản / bảng tính / báo cáo.

---

## 3. CHUẨN THỂ THỨC VĂN BẢN HÀNH CHÍNH VIỆT NAM (NGHỊ ĐỊNH 30/2020/NĐ-CP)

Khi tạo mới hoặc cập nhật bất kỳ văn bản, báo cáo, tài liệu Word/PDF/Excel nào bằng tiếng Việt, BẮT BUỘC tuân thủ nghiêm ngặt chuẩn thể thức hành chính Việt Nam:

### A. Định dạng đối với File Word (.docx) & PDF (.pdf)
1. **Bộ mã ký tự:** Sử dụng bộ mã ký tự tiếng Việt Unicode theo tiêu chuẩn Việt Nam TCVN 6909:2001.
2. **Phông chữ & Cỡ chữ chuẩn:**
   - **Quốc hiệu & Tiêu ngữ:** Times New Roman, cỡ chữ 12–13, in hoa/in đậm đúng chuẩn hành chính.
   - **Tên loại văn bản & Trích yếu:** Times New Roman, cỡ chữ 14–15, in hoa, in đậm, căn giữa.
   - **Nội dung văn bản (Body Text):** Times New Roman, cỡ chữ 13–14, chữ đứng, căn đều 2 bên (Justified), thụt đầu dòng (Indent First Line) 1 – 1.27 cm.
   - **Giãn dòng & Giãn đoạn:** Giãn dòng 1.15 đến 1.5 lines; giãn đoạn Before 3–6 pt, After 3–6 pt.
   - **Bảng biểu (Tables):** Times New Roman, tiêu đề bảng in đậm, căn giữa; nội dung căn lề phù hợp với kiểu dữ liệu.

### B. Định dạng đối với File Bảng tính Excel (.xlsx)
1. **Phông chữ:** 100% các ô dữ liệu, ô tiêu đề, ghi chú, chú thích, nhãn biểu đồ trong tất cả các Sheet BẮT BUỘC dùng phông **Times New Roman**.
2. **Căn lề chuẩn:**
   - **Tiêu đề cột / Header:** Times New Roman, in đậm, căn giữa (Center), tự động xuống dòng (Wrap Text).
   - **Cột STT, Mã, Ngày tháng, Trạng thái:** Căn giữa (Center).
   - **Cột Văn bản / Nội dung / Ghi chú:** Căn trái (Left).
   - **Cột Số lượng, Đơn giá, Thành tiền, Tỷ lệ (%):** Căn phải (Right), có định dạng phân cách hàng nghìn (`#,##0`).
3. **Viền bảng & Màu sắc:**
   - Viền bảng mảnh màu xám nhẹ (`#D9D9D9`) hoặc chuẩn nhận diện doanh nghiệp.
   - Màu sắc Header nhã nhặn, chuyên nghiệp (Navy Blue, Dark Slate), tương phản tốt với chữ trắng/chữ đậm.

---

## 4. THỰC THI VÀ TỰ ĐỘNG HÓA CODE (CODE EXECUTION)

Khi viết các đoạn mã Python hoặc tiện ích tạo file Excel (`openpyxl`), Word (`python-docx`), PDF (`reportlab`, `fpdf`):
- Phải khai báo biến font mặc định: `font_family = 'Times New Roman'`.
- Thiết lập font `'Times New Roman'` cho từng Cell / Paragraph / Style được tạo ra.

---

## 5. QUY TẮC BẢO TOÀN DỮ LIỆU & NGUYÊN TẮC CẬP NHẬT FILE (FILE PRESERVATION & INCREMENTAL UPDATE MANDATE)

Khi nhận bất kỳ yêu cầu cập nhật, bổ sung hay chỉnh sửa nào đối với các file sẵn có (File Excel `.xlsx`, Word `.docx`, Code, Markdown, Config, v.v.):
1. **Đọc trực tiếp file trên hệ thống trước:** BẮT BUỘC phải kiểm tra, đọc trực tiếp cấu trúc và nội dung hiện tại của file trên hệ thống trước. Không dựa vào phỏng đoán hay trí nhớ trong hội thoại.
2. **Nhận diện các điều chỉnh thủ công:** Phải nhận diện được toàn bộ các chỉnh sửa, điều chỉnh thiết kế, thay đổi cấu trúc, các sheet/cột/dòng mà người dùng đã tự chỉnh sửa, thêm vào hoặc đã chủ động XÓA BỎ.
3. **Tuyệt đối không ghi đè từ đầu (Never overwrite from scratch):** Tuyệt đối không chạy script tạo mới từ đầu để ghi đè làm mất đi các nội dung, định dạng hoặc cấu trúc mà người dùng đã tinh chỉnh.
4. **Chỉ bổ sung/cập nhật thêm mới (Append / Update incrementally):**
   - **Với file Excel (.xlsx):** Luôn mở file hiện tại (`openpyxl.load_workbook`), kiểm tra các Sheet hiện có, thêm/sửa chính xác sheet hoặc vùng dữ liệu được yêu cầu mà KHÔNG xóa, KHÔNG làm thay đổi các sheet khác, và KHÔNG tự ý tạo lại các Sheet mà người dùng đã xóa (Ví dụ: người dùng đã xóa Sheet 5 thì tuyệt đối không được tự động sinh lại Sheet 5).
   - **Với file văn bản / mã nguồn:** Sử dụng công cụ chỉnh sửa từng khối, không viết đè toàn bộ file nếu không có yêu cầu rõ ràng.
5. **Bảo toàn 100% dữ liệu chuẩn:** Toàn bộ nội dung chữ, số liệu, cách bố trí, thiết kế giao diện, kiểu dáng mà người dùng đã sửa đổi thủ công trong file phải được xem là dữ liệu chuẩn và BẢO TOÀN NGUYÊN VẸN 100%.
6. **Xác nhận khi có xung đột:** Nếu có điểm nào chưa rõ ràng hoặc nghi ngờ xung đột giữa nội dung mới và nội dung người dùng đã sửa, BẮT BUỘC PHẢI HỎI LẠI NGƯỜI DÙNG để xác nhận trước khi thực hiện, không được tự ý suy diễn hoặc tự tiện khôi phục.

---

## 6. QUY TẮC TỰ ĐỘNG ĐÁNH SỐ LẠI THỨ TỰ SHEET (AUTO-RENUMBERING SHEETS)

- Khi có sự thay đổi về số lượng Sheet trong file Excel (do người dùng xóa bỏ, gộp lại hoặc AI bổ sung thêm sheet mới):
  - BẮT BUỘC phải tự động chuẩn hóa và đánh số thứ tự liên tục cho tất cả các Sheet từ `1.` đến `N.` (Ví dụ: khi Sheet 5 bị xóa và có Sheet 6, phải tự động đổi Sheet 6 thành `5. [Tên Sheet]`), tuyệt đối không để số thứ tự bị nhảy cóc (như 1, 2, 3, 4, 6...).

---

## 7. QUY TẮC TỰ ĐỘNG KIỂM TRA THƯ MỤC & ĐÁNH SỐ THỨ TỰ CHO FILE MỚI (SEQUENTIAL FILE AUTO-NUMBERING)

- Trước khi sinh bất kỳ file tài liệu/báo cáo/script mới nào trong thư mục:
  - BẮT BUỘC phải kiểm tra danh sách file hiện có trong thư mục để xác định số thứ tự tiếp theo (`01_...`, `02_...`, `03_...` hoặc theo định dạng đang áp dụng).
  - Tự động gán số thứ tự tiếp theo vào tên file mới để đảm bảo tính tuần tự, ngăn nắp và dễ quản lý, tránh việc đặt tên trùng lặp hoặc không có số thứ tự.

---

## 8. QUY TẮC MÔ HÌNH HÓA TRỰC QUAN (VISUAL GRAPH & DIAGRAM MANDATE)

- Đối với các yêu cầu về sơ đồ, quy trình, luồng vận hành (flowchart, workflow, architecture):
  - **KHÔNG CHỈ DÙNG TEXT THUẦN:** Phải mô hình hóa bằng dạng biểu đồ/graph/diagram trực quan (hình khối có màu sắc phân loại, mũi tên chỉ hướng, swimlane, icon nhận diện) hoặc chèn hình ảnh sơ đồ đồ họa chất lượng cao (High-Resolution Diagram) vào trực tiếp tài liệu/Excel/Markdown.

---

## 9. QUY TẮC BỐ CỤC BẢNG TÍNH EXCEL CHỐNG DỒN CHỮ & ĐÈ DÒNG (EXCEL LAYOUT & ANTI-CLIPPING MANDATE)

Khi tạo mới hoặc cập nhật bất kỳ file Excel (`.xlsx`) nào qua Python (`openpyxl`/`pandas`) hoặc công cụ tự động, BẮT BUỘC phải tuân thủ nghiêm ngặt các nguyên tắc bố cục sau để đảm bảo giao diện luôn thoáng đãng, sang trọng, không bao giờ bị cắt chữ, đè dòng hay dồn chữ:

### A. Phân tách rạch ròi Cột STT và Cột Nội dung / Tiêu đề
1. **Cột STT:** Luôn tách riêng thành một cột độc lập (thường là Cột A), độ rộng cố định từ 6 – 8 ký tự, căn giữa (Center). Ô này CHỈ chứa số thứ tự thuần túy (1, 2, 3...) hoặc mã định danh ngắn.
2. **Tuyệt đối KHÔNG gộp chung số thứ tự với tiêu đề dài** vào cùng một ô trong cột STT (ví dụ: TUYỆT ĐỐI TRÁNH đặt "1. Khảo sát năng lực thực tế" vào Cột A có `width = 8`).
3. **Cột Tên mục / Tiêu đề / Nội dung:** Phải nằm ở cột riêng (thường là Cột B trở đi) với độ rộng tối thiểu từ 24 – 35 ký tự để văn bản có đủ không gian hiển thị thẳng hàng, rõ ràng.

### B. Đồng nhất cấu trúc cột khi có nhiều bảng trong cùng 1 Sheet
1. Trong cùng một Sheet, nếu có nhiều phần/bảng dữ liệu xếp dọc nhau (Phần A, Phần B, Phần C...):
   - Mọi bảng bắt buộc phải chia sẻ cùng một hệ quy chiếu cột (Cột A luôn là STT, Cột B luôn là Tiêu đề, Cột C luôn là Mô tả...).
   - Tuyệt đối không để Bảng 1 dùng Cột A làm STT ngắn (width 8), còn Bảng 2 lại dùng Cột A làm cột văn bản dài.
2. Nếu hai bảng có cấu trúc cột quá khác biệt hoặc bảng dưới có ít cột hơn:
   - **Ưu tiên 1:** Tách thành các Sheet riêng biệt (mỗi Sheet phục vụ một mục đích cụ thể).
   - **Ưu tiên 2:** Sử dụng thao tác gộp ô (Merge Cells liên tiếp các cột ngang, ví dụ merge Cột B đến Cột D) rồi mới thiết lập Wrap Text để nội dung dài có đủ không gian trải rộng.

### C. Tính toán Chiều cao dòng động (Dynamic Row Height) & Tránh gán cứng chiều cao thấp
1. Tuyệt đối KHÔNG gán cứng chiều cao dòng cố định quá thấp (ví dụ `height = 40` hay `height = 45`) cho các ô có văn bản dài hoặc có nhiều dòng xuống dòng (`\n`). Việc gán cứng chiều cao thấp sẽ khiến mép dưới của ô cắt đứt chữ hoặc các dòng chữ đè lên nhau.
2. BẮT BUỘC phải áp dụng cơ chế tính toán chiều cao dòng động dựa trên độ dài văn bản và độ rộng cột:
   - Công thức chuẩn hóa: `row_height = max(min_height, total_estimated_lines * line_height + padding)` (với `line_height` khoảng 16–18pt và `padding` khoảng 10–14pt).
   - Hoặc để Excel tự động tính toán (AutoFit) bằng cách không gán cứng chiều cao đối với các dòng có nội dung văn bản dài.
3. Độ rộng các cột văn bản (`column_dimensions[col].width`) luôn phải được thiết lập rộng rãi, tối thiểu từ 25 – 50 ký tự tùy dung lượng text, có khoảng đệm (padding) tối thiểu 3–5 ký tự để chữ không chạm sát mép viền ô.

---

## 10. NGUYÊN TẮC BẢO VỆ AN TOÀN FILE & THƯ MỤC — CẤM XÓA HÀNG LOẠT VÀ CẤM XÓA FOLDER (ANTI-DELETION & ZERO DATA DESTRUCTION MANDATE)

Đây là **NGUYÊN TẮC BẢO MẬT & AN TOÀN DỮ LIỆU TUYỆT ĐỐI**:

### A. Các hành vi nghiêm cấm tuyệt đối (Strictly Prohibited):
1. **Tuyệt đối KHÔNG xóa thư mục (Folder):** Không bao giờ tự ý xóa bất kỳ thư mục nào trên ổ đĩa, dù là thư mục cha hay thư mục con.
2. **Tuyệt đối KHÔNG xóa toàn bộ file trong thư mục (Mass File Deletion):** Cấm chạy bất kỳ lệnh hoặc đoạn mã nào có tính chất dọn sạch hoặc xóa hàng loạt file (ví dụ: `Remove-Item *`, `rm -rf`, `del *.*`, `rmdir /s /q`, `shutil.rmtree`).
3. **Tuyệt đối KHÔNG tự tiện xóa file cũ để dọn chỗ:** Khi sinh file mới hoặc cập nhật file, chỉ tạo thêm file mới có đánh số thứ tự tiếp theo (`01_...`, `02_...`, `03_...`) hoặc cập nhật trực tiếp tại chỗ. Toàn bộ các file cũ, file nháp, file tài liệu có sẵn trong thư mục phải được giữ nguyên vẹn để làm lịch sử đối chiếu.

### B. Quy định khi cần xóa file:
1. AI CHỈ ĐƯỢC PHÉP XÓA duy nhất một file cụ thể khi và chỉ khi **người dùng chỉ định đích danh tên file đó** và ra lệnh rõ ràng (ví dụ: *"hãy xóa file test.py giúp tôi"*).
2. Khi người dùng không yêu cầu xóa đích danh, AI tuyệt đối không được tự ý phỏng đoán hoặc dọn dẹp thư mục làm việc của người dùng.
3. Nếu có thao tác có nguy cơ ảnh hưởng đến nhiều file, BẮT BUỘC PHẢI DỪNG LẠI HỎI XIN PHÉP VÀ CÓ SỰ XÁC NHẬN CỦA NGƯỜI DÙNG trước khi tiến hành.

---

## 11. QUY TẮC DUY TRÌ FILE DUY NHẤT & TỰ ĐỘNG LƯU TRỮ VÀO THƯ MỤC _BACKUP (SINGLE ACTIVE FILE & AUTO-ARCHIVE MANDATE)

Để đảm bảo cây thư mục làm việc luôn ngăn nắp, trực quan, không gây rối mắt và tránh nhầm lẫn phiên bản:

### A. Nguyên tắc Single Source of Truth
- Trong mỗi thư mục nghiệp vụ/tài liệu, bên ngoài thư mục chỉ duy trì **DUY NHẤT 01 phiên bản mới nhất, hoàn chỉnh nhất** của tài liệu để người dùng sử dụng, gửi đối tác hoặc in ấn.
- Tuyệt đối không để nhiều phiên bản cũ/mới (v1, v2, v3, nháp, chỉnh sửa) nằm cùng cấp thư mục làm rối mắt người dùng.

### B. Quy trình Tự động Lưu trữ (Auto-Archive Workflow)
Khi tạo ra một file phiên bản mới nâng cấp hoặc thay thế cho file cũ trong cùng thư mục:
1. **Tạo thư mục `_backup/`:** Tự động kiểm tra và tạo thư mục con tên là `_backup/` ngay trong thư mục đó (nếu chưa có).
2. **Di chuyển file cũ (Move/Archive):** Di chuyển toàn bộ các file phiên bản cũ, file nháp trước đó vào trong thư mục `_backup/` (tuyệt đối KHÔNG dùng lệnh xóa `del` hay `rm`).
3. **Giữ file mới bên ngoài:** Lưu hoặc đặt file phiên bản mới nhất ở bên ngoài thư mục làm việc làm phiên bản hoạt động chính thức.
4. **Phạm vi phân loại:**
   - Áp dụng khi tạo ra phiên bản thay thế của cùng một tài liệu (Word `.docx`, Excel `.xlsx`, PDF `.pdf`, báo cáo `.md`).
   - Các file có chức năng độc lập khác nhau trong cùng thư mục (ví dụ: 1 file Hợp đồng Word + 1 file Bảng tính tài chính Excel + 1 file Quét chữ ký PDF) thì vẫn được để cùng nhau, không di chuyển nhầm vào backup.
5. **Bảo toàn dữ liệu 100%:** Toàn bộ lịch sử các phiên bản cũ được giữ nguyên vẹn trong `_backup/` để người dùng có thể tra cứu, đối chiếu hoặc khôi phục lại bất kỳ lúc nào khi cần.

---

## 12. KỶ LUẬT CHỐNG BỊA SỐ LIỆU (ANTI-HALLUCINATION MANDATE)

1. **Tuyệt đối không tự suy diễn số liệu:** Mọi con số, ngày tháng, điều khoản, số tiền phải được trích xuất 100% chính xác từ file nguồn được chỉ định.
2. **Xử lý khi thiếu thông tin:** Nếu tài liệu nguồn không đề cập hoặc dữ liệu bị khuyết, ghi rõ `[Tài liệu không đề cập]` hoặc `[Cần xác nhận lại]`, tuyệt đối không tự điền số liệu giả định.
3. **Khai báo nguồn kiểm chứng (Source Citation):** Mọi báo cáo tổng hợp, tóm tắt hoặc nghiên cứu phải kết thúc bằng bảng hoặc mục **"Nguồn dữ liệu kiểm chứng"** (ghi rõ tên file, đoạn văn hoặc dòng số liệu gốc).
