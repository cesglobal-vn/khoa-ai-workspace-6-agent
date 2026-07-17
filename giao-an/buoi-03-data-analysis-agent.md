# Giáo án Buổi 03 - Data Analysis Agent (Agent phân tích dữ liệu)

> Khung chuẩn cho giảng viên. Buổi thực chiến: dựng agent đọc Excel/CSV, hiểu dữ liệu, tính toán, tìm xu hướng, gợi ý biểu đồ.

## Thông tin buổi
- **Buổi:** 03 / 6
- **Loại:** Thực chiến
- **Agent xây dựng:** Data Analysis Agent (agent phân tích số liệu)
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - 1 file Excel demo sạch: `demo-doanh-thu-quy.xlsx` (bảng doanh thu 4 quý, có cột: Tháng, Sản phẩm, Khách hàng, Doanh thu, Chi phí)
  - 1 file Excel demo "bẩn" cố ý: `demo-ban.xlsx` (có ô trống, dòng trùng, cột ngày sai định dạng, đơn vị tiền lẫn lộn) để dạy phần làm sạch
  - 1 file chung cho Thực hành 1: `thuc-hanh-ban-hang.csv` (danh sách đơn hàng 3 tháng)
  - Tài khoản AI mẫu đã đăng nhập, workspace từ Buổi 1 đã có sẵn
  - Slide nền trắng (nếu dùng): 5-6 slide khái niệm
  - Nhắc học viên qua Zalo trước buổi: mang 1 file Excel/CSV công việc thật có số liệu

## Mục tiêu buổi (học xong học viên làm được gì)
1. Dựng được Data Analysis Agent từ system prompt chuẩn, gắn vào workspace của mình.
2. Upload 1 file Excel/CSV và bắt agent mô tả đúng dữ liệu: số dòng, số cột, phát hiện ô trống/trùng/sai định dạng.
3. Đặt được câu hỏi phân tích tốt và đọc hiểu kết quả: tổng, trung bình, tỷ lệ, tăng trưởng, top/bottom, phân nhóm.
4. Đọc được phần gợi ý biểu đồ của agent (loại biểu đồ, trục X-Y, ý nghĩa) và tự vẽ lại trong Excel nếu công cụ không vẽ được.
5. Có thói quen kiểm tra lại 1-2 con số quan trọng bằng tay, không tin AI 100%.

## Kết quả cầm về (deliverable)
- 1 Data Analysis Agent đã dựng xong, chạy được trong workspace.
- 1 bản phân tích mẫu (agent xuất ra) dựa trên file công việc thật của học viên: tổng quan dữ liệu + số liệu chính + nhận định xu hướng + gợi ý biểu đồ.
- 1 file Excel công việc của học viên đã được "làm sạch" 1 phần theo gợi ý của agent.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Data Analysis Agent là gì:** một trợ lý số liệu đóng gói sẵn. Thay vì mỗi lần mở chat lại dặn "đọc file này, tính giúp tôi tổng doanh thu, so sánh các tháng", ta viết dặn dò đó 1 lần vào agent. Sau này chỉ cần thả file vào và hỏi.
- **File sạch quan trọng thế nào:** AI đọc bảng giống người đọc bảng. Nếu bảng có dòng tiêu đề nằm giữa, ô gộp (merge), cột ngày lúc thì "01/02" lúc thì "1 tháng 2", cột tiền lúc có "đ" lúc không, thì AI dễ hiểu sai. Dọn bảng trước khi đưa AI giúp kết quả chính xác hơn nhiều.
- **Câu hỏi phân tích tốt:** hỏi cụ thể, có mốc so sánh. "Phân tích file này" là câu mơ hồ. "So sánh doanh thu quý này với quý trước theo từng sản phẩm" là câu tốt: rõ cái cần tính, rõ cách nhóm, rõ mốc so sánh.
- **Gợi ý biểu đồ:** agent không chỉ ra số, mà nói luôn "số này nên vẽ biểu đồ cột, trục X là tháng, trục Y là doanh thu, để thấy tháng nào cao thấp". Học viên cầm gợi ý đó vẽ trong Excel là xong.
- **AI có thể tính sai:** AI đọc và tính rất nhanh nhưng đôi khi nhầm, nhất là với bảng lớn hoặc ô định dạng lạ. Vì vậy con số nào quan trọng (đưa vào báo cáo, gửi sếp) thì phải kiểm lại bằng tay hoặc bằng hàm SUM trong Excel.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn:** "Chào cả nhà. Hai buổi trước mình đã dựng xong workspace, có Orchestrator điều phối và Document Agent đọc tài liệu chữ. Hôm nay mình làm agent thứ ba, và là agent nhiều người mong nhất: agent xử lý số. Cuối buổi, mỗi người sẽ có một trợ lý biết mở file Excel của mình ra, đọc hiểu, tính toán và mách luôn nên vẽ biểu đồ gì."
- Recap nhanh Buổi 2: Document Agent đọc file chữ (PDF, Word), tóm tắt, trích ý. Hỏi lớp: "Có ai đã dùng Document Agent cho việc thật chưa, kể nhanh 1 câu?"
- Nêu mục tiêu buổi hôm nay: dựng Data Analysis Agent, thực hành trên 1 file chung rồi trên file công việc thật của chính mình.
- Nhắc: "Ai chưa mở sẵn file Excel công việc thì mở ngay bây giờ, lát nữa mình dùng."

### [00:15-00:35] Lý thuyết ngắn
- Nội dung, đi qua 4 ý (dùng slide nền trắng nếu có):
  1. Data Analysis Agent làm được gì: hiểu dữ liệu, làm sạch, tính toán, tìm xu hướng, gợi ý biểu đồ. (chiếu lại 5 nhiệm vụ trong system prompt)
  2. Vì sao phải chuẩn bị file sạch: cho lớp xem nhanh 1 bảng bẩn và 1 bảng sạch cạnh nhau, chỉ ra 3 lỗi hay gặp (ô trống, dòng trùng, cột ngày/tiền sai định dạng).
  3. Cách hỏi phân tích tốt: đưa cặp ví dụ "câu mơ hồ" vs "câu rõ" để lớp thấy khác biệt.
  4. Quy tắc vàng: luôn kiểm lại con số quan trọng. AI nhanh nhưng không phải máy tính, có thể nhầm.
- **Câu hỏi tương tác:** "Theo mọi người, đâu là lỗi hay gặp nhất trong file Excel công việc của mình khiến người khác đọc bị rối?" (gợi để lớp tự nhận ra bảng của họ cũng cần dọn)

### [00:35-01:00] Demo giảng viên
- GV dựng Data Analysis Agent từ đầu, vừa làm vừa nói, học viên xem:
  1. Mở workspace, tạo agent/project mới, đặt tên "Data Analysis Agent".
  2. Mở file `system-prompts/03-data-analysis-agent.md`, copy khối system prompt, dán vào. Điền tên + chức danh mẫu vào chỗ `[Họ tên]`, `[chức danh]`.
  3. Upload file demo sạch `demo-doanh-thu-quy.xlsx`. Gõ: "Đọc file này và cho tôi tổng quan dữ liệu." Đọc to phần agent trả lời, chỉ rõ nó đếm đúng số dòng/cột chưa.
  4. Hỏi phân tích: "Tính tổng doanh thu từng quý và so sánh quý sau với quý trước, cho biết tăng hay giảm bao nhiêu phần trăm." Đọc kết quả, chỉ chỗ agent nêu công thức.
  5. Hỏi top/bottom: "Cho tôi 5 khách hàng có doanh thu cao nhất." Xem bảng agent xuất.
  6. Xem phần **Biểu đồ đề xuất**: agent nói loại biểu đồ + trục X-Y + ý nghĩa. GV nói: "Nếu công cụ vẽ được, mình bấm cho vẽ; nếu không, mình cầm mô tả này qua Excel vẽ 30 giây là xong."
  7. Demo phần kiểm tra: lấy 1 con số agent vừa tính (ví dụ tổng doanh thu quý 1), mở Excel gõ `=SUM(...)` kiểm lại. So khớp. Nhấn mạnh thói quen này.
- **Điểm nhấn phải chỉ rõ:**
  - Agent tự mô tả dữ liệu trước khi tính, đó là bước "hiểu dữ liệu" đừng bỏ qua.
  - Câu hỏi càng cụ thể, kết quả càng đúng ý.
  - Luôn có bước kiểm tra con số quan trọng.

### [01:00-01:30] Thực hành 1 (dữ liệu mẫu chung)
- Đề bài (dùng file chung `thuc-hanh-ban-hang.csv` GV phát): mỗi học viên tự dựng Data Analysis Agent bằng system prompt chuẩn, rồi:
  1. Upload file, yêu cầu agent cho tổng quan dữ liệu (bao nhiêu dòng/cột, có ô trống/trùng không).
  2. Hỏi: "Tổng doanh thu theo từng tháng là bao nhiêu?"
  3. Hỏi: "Tháng nào bán chạy nhất, tháng nào thấp nhất?"
  4. Hỏi: "Gợi ý cho tôi 1 biểu đồ phù hợp để trình bày doanh thu theo tháng."
  5. Tự kiểm lại tổng doanh thu 1 tháng bằng Excel.
- GV đi vòng hỗ trợ. Lỗi hay gặp cần để ý: học viên quên upload file, học viên hỏi quá chung chung ("phân tích đi"), agent trả lời lệch vì file mở sai. Nhắc từng bàn.

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2 (dữ liệu công việc của học viên)
- Đề bài: dùng chính Data Analysis Agent vừa dựng, upload **file Excel/CSV công việc thật** của mình. Làm lần lượt:
  1. Bắt agent mô tả tổng quan + chỉ ra ô trống/trùng/sai định dạng trong file thật (đây là lúc file bẩn lộ ra, đúng ý đồ dạy).
  2. Nếu file bẩn: hỏi agent "nên xử lý các lỗi này thế nào?", sửa 1-2 lỗi trong Excel theo gợi ý.
  3. Đặt 2-3 câu hỏi phân tích gắn với công việc của mình, ví dụ: "So sánh [kỳ này] với [kỳ trước]", "Top 5 [khách hàng/sản phẩm/khoản mục] cao nhất", "Tỷ lệ [A] trên tổng là bao nhiêu".
  4. Lấy phần gợi ý biểu đồ, vẽ thử 1 biểu đồ trong Excel.
  5. **Bắt buộc:** chọn 1 con số quan trọng nhất, kiểm lại bằng tay/hàm Excel, ghi vào workbook đúng hay lệch.
- GV đi vòng, chú ý xử lý các tình huống trong bảng bên dưới (file bẩn, AI tính sai, đơn vị tiền không rõ).

### [02:15-02:35] Chốt & giao bài
- Tổng kết 3 ý: (1) file sạch cho kết quả chuẩn, (2) hỏi cụ thể có mốc so sánh, (3) luôn kiểm lại số quan trọng.
- Mỗi học viên nói nhanh 1 câu: "Agent của mình vừa tìm ra điều gì hữu ích từ file công việc?"
- Bài về nhà (xem mục Bài tập).
- Xem trước Buổi 4: "Buổi sau mình dựng Report Agent: biến những con số hôm nay thành báo cáo và email hoàn chỉnh. Ai giữ lại bản phân tích hôm nay thì buổi sau ghép vào rất nhanh."

---

## Script demo (các bước GV thao tác)
1. Mở workspace Buổi 1 → tạo agent mới → đặt tên "Data Analysis Agent".
2. Copy system prompt từ `system-prompts/03-data-analysis-agent.md` → dán vào phần hướng dẫn của agent → điền `[Họ tên]`, `[chức danh]`, `[bối cảnh dữ liệu]`.
3. Upload `demo-doanh-thu-quy.xlsx` → gõ: "Đọc file này và cho tôi tổng quan dữ liệu."
4. Gõ: "Tính tổng doanh thu từng quý, so sánh quý sau với quý trước theo phần trăm."
5. Gõ: "Cho tôi 5 khách hàng doanh thu cao nhất, xếp từ cao xuống thấp."
6. Gõ: "Đề xuất biểu đồ phù hợp để trình bày doanh thu 4 quý, nói rõ loại biểu đồ và trục X-Y."
7. Nếu công cụ vẽ được: bấm cho vẽ. Nếu không: mở Excel, chọn dữ liệu, Insert → Chart, vẽ theo mô tả.
8. Kiểm tra: mở `demo-doanh-thu-quy.xlsx`, gõ `=SUM(cột doanh thu quý 1)` → so với số agent đưa.
9. (Tùy chọn) Upload `demo-ban.xlsx` → gõ: "File này có lỗi gì về dữ liệu? Liệt kê ô trống, dòng trùng, cột sai định dạng và cách sửa." → cho lớp thấy agent bắt lỗi.

## System prompt dùng trong buổi
- Xem `system-prompts/03-data-analysis-agent.md` (copy nguyên khối, điền tên + chức danh + bối cảnh dữ liệu của học viên).

## Câu hỏi tương tác gợi ý
- "File Excel công việc của mọi người có hay bị lỗi gì khiến người khác đọc bị rối?"
- "Giữa câu 'phân tích file này' và câu 'so sánh doanh thu tháng này với tháng trước theo sản phẩm', câu nào cho kết quả dùng được ngay? Vì sao?"
- "Nếu agent báo tổng doanh thu là 1,2 tỷ mà cảm giác của bạn là phải hơn, bạn làm gì tiếp theo?"
- "Với số liệu vừa phân tích, bạn sẽ trình bày cho sếp bằng loại biểu đồ nào?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| File Excel bẩn: ô trống, dòng trùng, ô gộp (merge), tiêu đề nằm giữa bảng | Bảo agent liệt kê lỗi trước, chưa vội tính. Bỏ ô gộp, đưa tiêu đề lên dòng đầu, xóa dòng trống trong Excel rồi upload lại. Nhắc lớp: dọn 2 phút, đỡ sai cả buổi. |
| AI tính sai (số không khớp khi kiểm bằng tay) | Không mắng agent, làm 3 bước: (1) hỏi lại "bạn tính con số này bằng công thức nào?"; (2) kiểm cột dữ liệu có ô lẫn chữ/khoảng trắng không; (3) chốt bằng hàm SUM/AVERAGE trong Excel. Con số vào báo cáo phải là con số đã kiểm. |
| Đơn vị tiền không rõ: cột số không ghi là đồng, nghìn hay triệu; lẫn "đ", "vnđ", dấu phẩy/chấm | Nói rõ đơn vị cho agent ngay từ đầu: "Cột doanh thu tính bằng triệu đồng." Nếu file lẫn lộn, sửa về một đơn vị trong Excel trước. Agent theo system prompt sẽ tự nêu giả định nếu bạn quên, đọc kỹ phần giả định đó. |
| Agent trả lời quá chung chung | Do câu hỏi mơ hồ. Hỏi lại cụ thể: rõ cột cần tính, rõ cách nhóm, rõ mốc so sánh. Ví dụ đổi "phân tích đi" thành "top 5 sản phẩm doanh thu cao nhất quý 2". |
| File quá lớn/nhiều dòng, agent xử lý chậm hoặc bỏ sót | Cảnh báo lớp: mẫu lớn dễ sai. Chia nhỏ theo kỳ (từng tháng/quý), hoặc lọc cột cần thiết trước khi upload. Kiểm con số tổng cẩn thận hơn. |
| Công cụ không vẽ được biểu đồ trực tiếp | Bình thường. Lấy mô tả biểu đồ của agent (loại + trục X-Y), mở Excel: chọn dữ liệu → Insert → Chart → chọn đúng loại. 30 giây có biểu đồ. |

## Bài tập
- **Tại lớp:** dựng xong Data Analysis Agent + chạy trên 1 file công việc thật, xuất được 1 bản phân tích (tổng quan + số liệu chính + nhận định + gợi ý biểu đồ) và kiểm lại 1 con số quan trọng.
- **Về nhà:**
  1. Lấy thêm 1 file số liệu khác của công việc (khác loại với file ở lớp), chạy qua agent, xuất 1 bản phân tích.
  2. Vẽ ít nhất 1 biểu đồ trong Excel theo gợi ý của agent.
  3. Chọn 2 con số quan trọng, kiểm lại bằng tay, ghi rõ đúng hay lệch và lệch bao nhiêu.
  4. Tinh chỉnh system prompt: thêm 1 câu mô tả loại dữ liệu bạn hay dùng vào phần BỐI CẢNH để lần sau agent hiểu nhanh hơn.

## Tiêu chí hoàn thành buổi
- [ ] Dựng được Data Analysis Agent bằng system prompt chuẩn, chạy trong workspace.
- [ ] Upload được file Excel/CSV và agent mô tả đúng số dòng/cột, chỉ ra được ô trống/trùng/sai định dạng.
- [ ] Đặt được ít nhất 3 câu hỏi phân tích cụ thể và đọc hiểu kết quả (tổng, so sánh, top/bottom).
- [ ] Có 1 gợi ý biểu đồ và vẽ lại được (trong công cụ hoặc Excel).
- [ ] Kiểm lại được ít nhất 1 con số quan trọng bằng tay, biết đúng hay lệch.
- [ ] Cầm về 1 bản phân tích mẫu từ file công việc thật của mình.
