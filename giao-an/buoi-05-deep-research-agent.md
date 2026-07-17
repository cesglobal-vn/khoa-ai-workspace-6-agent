# Giáo án Buổi 05: Deep Research Agent (Agent nghiên cứu thị trường & đối thủ)

> Khung chuẩn cho giảng viên. Bám đúng các mục dưới đây.

## Thông tin buổi
- **Buổi:** 05 / 6
- **Loại:** Nâng cao
- **Agent xây dựng:** Deep Research Agent (nghiên cứu thị trường, phân tích đối thủ, tổng hợp nhiều nguồn thành báo cáo)
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - File demo: 1 báo cáo nghiên cứu mẫu hoàn chỉnh (theo 6 mục định dạng chuẩn) để chiếu đối chiếu.
  - Tài khoản AI có bật sẵn tính năng duyệt web/tìm kiếm (nếu công cụ lớp có). Test trước xem agent có trích được link không.
  - 1 chủ đề nghiên cứu chung cho Thực hành 1 (ví dụ: "thị trường khóa học tiếng Anh online cho người đi làm tại Hà Nội").
  - Slide 6 mục định dạng báo cáo + bảng phân biệt Dữ kiện / Suy luận / Chưa chắc.
  - Mở sẵn system prompt `system-prompts/05-deep-research-agent.md` để dán khi demo.
  - Nhắc học viên buổi trước: mỗi người chọn sẵn 1 thị trường HOẶC 1 đối thủ thật cần tìm hiểu.

## Mục tiêu buổi (học xong học viên làm được gì)
1. Dựng được Deep Research Agent riêng, biết lập khung câu hỏi nghiên cứu (chia 1 chủ đề lớn thành các câu hỏi con trả lời được).
2. Đọc một báo cáo AI và phân biệt được 3 loại thông tin: dữ kiện có nguồn, suy luận của AI, và chỗ AI chưa chắc.
3. Biết cách kiểm chứng thông tin: yêu cầu AI trích link, tự mở link kiểm tra, phát hiện khi AI bịa số liệu hoặc bịa nguồn.
4. Làm được bảng so sánh đối thủ (sản phẩm, giá, điểm mạnh, điểm yếu, định vị).
5. Hiểu cách nối kết quả research sang Report Agent (buổi 4) để viết thành đề xuất/proposal.

## Kết quả cầm về (deliverable)
- 1 Deep Research Agent đã dựng, chạy được.
- 1 khung câu hỏi nghiên cứu (4-6 câu hỏi con) cho chủ đề công việc thật của mình.
- 1 báo cáo nghiên cứu nháp theo đúng 6 mục định dạng chuẩn, trong đó có ít nhất 1 bảng so sánh đối thủ và phần "điểm cần kiểm chứng thêm".

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)

- **Deep Research Agent là gì.** Là một trợ lý nghiên cứu đóng gói sẵn: mình giao một chủ đề, nó tự chia nhỏ chủ đề, tìm và tổng hợp thông tin, rồi trả về một báo cáo có cấu trúc. Khác với hỏi chat lẻ là nó luôn làm theo cùng một khung, nên báo cáo lần nào cũng đầy đủ mục như nhau.

- **Khung câu hỏi nghiên cứu.** Chủ đề lớn ("thị trường X thế nào") thì mơ hồ, AI trả lời chung chung. Cách làm đúng: bẻ chủ đề lớn thành các câu hỏi con cụ thể, mỗi câu trả lời được riêng. Ví dụ chủ đề "thị trường khóa học AI cho người đi làm": câu con là quy mô thị trường bao nhiêu, có mấy đối thủ chính, họ bán giá bao nhiêu, khách hàng phàn nàn điều gì, khoảng trống nào chưa ai làm. Trả lời hết các câu con là hiểu cả chủ đề.

- **Ba loại thông tin phải phân biệt.** Đây là kỹ năng quan trọng nhất của buổi:
  - **Dữ kiện có nguồn:** con số, sự việc lấy từ một nguồn cụ thể, mở link ra kiểm được.
  - **Suy luận của AI:** AI tự suy ra từ dữ kiện, hợp lý nhưng không phải là sự thật đã kiểm chứng.
  - **Chỗ chưa chắc:** AI không có dữ liệu, đang đoán. Phải ghi rõ "cần kiểm chứng", không được trình bày như thật.

- **Vì sao phải kiểm chứng.** AI có thể "bịa cho trơn câu": tự chế ra số liệu thị trường trông rất thật, hoặc dẫn một nguồn không tồn tại. Với nghiên cứu để ra quyết định kinh doanh, một số liệu bịa có thể dẫn tới quyết định sai. Nguyên tắc: số liệu và nguồn nào quan trọng thì phải tự mở ra kiểm, không tin ngay.

- **Bảng so sánh đối thủ.** Cách gọn nhất để nhìn ra vị trí của mình: xếp các đối thủ thành hàng, mỗi cột là một tiêu chí (sản phẩm, giá, điểm mạnh, điểm yếu, định vị). Nhìn bảng là thấy khoảng trống thị trường.

- **Nối sang Report Agent.** Research ra "nguyên liệu thô" (phát hiện, số liệu, bảng so sánh). Report Agent buổi 4 biến nguyên liệu đó thành một đề xuất/proposal có mở bài, thân bài, khuyến nghị. Hai agent nối nhau thành một dây chuyền.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn:** "Bốn buổi qua mình đã có agent đọc tài liệu, agent phân tích số liệu, agent viết báo cáo. Hôm nay là agent khó nhất và cũng đáng tiền nhất: agent đi nghiên cứu thị trường và soi đối thủ. Khó ở chỗ nào? Ở chỗ nó dễ nói dối nhất. Buổi này mình học cách bắt AI nói thật, và tự mình kiểm được đâu là thật đâu là bịa."
- Recap nhanh buổi 4: Report Agent nhận đầu vào có sẵn rồi viết thành báo cáo. Hôm nay đầu vào đó do chính agent research tự đi tìm.
- Điểm danh, hỏi nhanh: ai đã chọn được thị trường/đối thủ thật cần tìm hiểu chưa? (Ai chưa có thì gợi ý ngay: đối thủ trực tiếp của công ty, hoặc một thị trường sản phẩm mình đang cân nhắc.)
- Nêu mục tiêu buổi: dựng agent research + tự kiểm chứng được thông tin.

### [00:15-00:35] Lý thuyết ngắn: phương pháp nghiên cứu + kiểm chứng
- **Nội dung 1 (7'): Lập khung câu hỏi.** Chiếu 1 chủ đề lớn, cùng lớp bẻ thành 4-6 câu hỏi con. Nhấn: câu hỏi con phải cụ thể, trả lời được, không trùng nhau.
- **Nội dung 2 (7'): Ba loại thông tin.** Chiếu 1 đoạn báo cáo mẫu có trộn cả 3 loại. Hỏi lớp: câu nào là dữ kiện, câu nào là suy luận, câu nào đang đoán? Chỉ cho lớp thấy AI hay để lẫn lộn khiến người đọc tưởng tất cả đều là sự thật.
- **Nội dung 3 (6'): Kiểm chứng.** Ba mức: (a) yêu cầu AI ghi rõ nguồn/link, (b) tự mở link xem có đúng nội dung AI nói không, (c) đối chiếu con số với 1 nguồn thứ hai. Nêu thẳng: nếu công cụ lớp có duyệt web thì bật lên và bắt trích link; nếu không có, mọi số liệu coi như "cần kiểm chứng" cho tới khi mình tự tra.
- **Câu hỏi tương tác:** "Nếu AI đưa cho bạn con số 'thị trường này trị giá 500 tỷ mỗi năm' mà không kèm nguồn, bạn tin bao nhiêu phần trăm? Làm gì tiếp theo?"

### [00:35-01:00] Demo giảng viên
- GV dựng Deep Research Agent từ đầu, dán system prompt (xem Script demo bên dưới).
- GV chạy thử với 1 chủ đề, cố tình để AI trả lời, rồi **hỏi vặn ngay tại chỗ**: "chỗ này nguồn đâu?", "số này bạn lấy ở đâu hay bạn đoán?" để lớp thấy agent tự phân loại lại.
- **Điểm nhấn phải chỉ rõ:**
  - Cách agent tự chia chủ đề thành khung câu hỏi con trước khi trả lời.
  - Chỉ tận nơi 3 loại thông tin trong báo cáo agent trả về (dữ kiện / suy luận / chưa chắc).
  - Nếu có duyệt web: mở 1 link agent trích ra, kiểm xem link có thật và có đúng nội dung không.
  - Nếu agent bịa 1 số liệu hoặc 1 nguồn (rất hay xảy ra), dừng lại chỉ cho lớp thấy đây chính là lỗi cần bắt, và cách bắt.
  - Chỉ cho lớp phần bảng so sánh đối thủ và mục "điểm cần kiểm chứng thêm".

### [01:00-01:30] Thực hành 1 (chủ đề chung)
- **Đề bài:** Cả lớp dùng chung 1 chủ đề GV cho (ví dụ: "thị trường khóa học tiếng Anh online cho người đi làm tại Hà Nội"). Mỗi học viên:
  1. Dựng agent (dán system prompt).
  2. Cùng agent lập khung 4-6 câu hỏi con.
  3. Cho agent chạy ra báo cáo nháp.
  4. Tô màu / đánh dấu trong báo cáo: đâu là dữ kiện, đâu là suy luận, đâu là chưa chắc.
- GV đi vòng hỗ trợ. Nhắc mọi người bắt ít nhất 1 chỗ AI chưa có nguồn và yêu cầu agent ghi "cần kiểm chứng".

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2 (thị trường/đối thủ thật của học viên)
- **Đề bài:** Mỗi học viên đổi sang chủ đề thật của mình (thị trường hoặc đối thủ đã chọn). Yêu cầu ra được:
  1. Khung câu hỏi nghiên cứu riêng.
  2. Báo cáo theo 6 mục định dạng chuẩn.
  3. **Bắt buộc có 1 bảng so sánh đối thủ** (ít nhất 2-3 đối thủ, các cột: sản phẩm/giá/điểm mạnh/điểm yếu/định vị).
  4. Mục "điểm cần kiểm chứng thêm" liệt kê các số liệu/nguồn cần tự tra lại.
- Với ai có công cụ duyệt web: bắt agent trích link, tự mở 1-2 link kiểm chứng ngay tại lớp.
- GV đi vòng, ưu tiên soi giúp các bảng so sánh và nhắc mọi người không để số liệu bịa lọt vào.

### [02:15-02:35] Chốt & giao bài
- Tổng kết: nhắc lại 3 loại thông tin + 3 mức kiểm chứng. Nhấn thông điệp: "Agent research giỏi không phải agent biết nhiều, mà là agent biết nói rõ chỗ nào nó chắc, chỗ nào nó đoán."
- Nối buổi sau: "Báo cáo research hôm nay là nguyên liệu. Buổi 6 mình ghép Orchestrator gọi cả 5 agent, trong đó research xong đẩy thẳng sang Report Agent viết proposal. Về nhà cứ nghĩ trước dự án thật mình muốn chạy cả dây chuyền."
- Giao bài về nhà (xem mục Bài tập).
- Xem trước buổi 6: Multi-Agent Capstone.

---

## Script demo (các bước GV thao tác)
1. Tạo agent/project mới, đặt tên "Deep Research Agent".
2. Mở `system-prompts/05-deep-research-agent.md`, dán nguyên khối prompt vào phần hướng dẫn của agent. Điền nhanh [Họ tên] / [chức danh] / [ngành] mẫu để lớp thấy cách cá nhân hóa.
3. Nếu công cụ có tính năng duyệt web/tìm kiếm: bật lên. Nói rõ cho lớp đang bật cái gì.
4. Giao chủ đề: "Nghiên cứu thị trường khóa học AI cho khối văn phòng tại Hà Nội, để tôi cân nhắc có nên mở sản phẩm này không."
5. Để agent hỏi lại phạm vi (mục tiêu, khu vực, mốc thời gian) rồi trả lời agent. Chỉ cho lớp: agent tốt là agent hỏi lại trước khi làm.
6. Để agent lập khung câu hỏi con. Dừng lại đọc to khung cho lớp nghe.
7. Cho agent chạy ra báo cáo. Khi báo cáo về, đọc lướt và chỉ tay vào từng loại thông tin: "đây là dữ kiện có nguồn, đây là suy luận, đây là chỗ nó ghi cần kiểm chứng".
8. Hỏi vặn agent 1 số liệu: "Con số này nguồn ở đâu? Nếu không chắc thì ghi rõ." Cho lớp thấy agent tự sửa lại, hạ số liệu xuống mức "cần kiểm chứng".
9. Nếu có link: mở 1 link agent trích, kiểm nội dung. Nếu link không mở được hoặc nội dung không khớp, chỉ cho lớp đây là dấu hiệu nguồn bịa.
10. Yêu cầu agent làm 1 bảng so sánh 2-3 đối thủ. Chiếu bảng.
11. Chỉ mục cuối "nguồn tham khảo / điểm cần kiểm chứng thêm" và nói: đây là mục mình phải đọc kỹ nhất.

## System prompt dùng trong buổi
- Xem `system-prompts/05-deep-research-agent.md` (dán nguyên khối, cá nhân hóa 3 ô [Họ tên] / [chức danh] / [ngành]).

## Câu hỏi tương tác gợi ý
- "Chủ đề lớn của bạn là gì? Thử bẻ nhanh thành 3 câu hỏi con xem nào."
- "Trong đoạn báo cáo này, chỗ nào là AI đang đoán mà nói như thật?"
- "AI đưa số 500 tỷ không nguồn. Bạn xử lý sao trước khi đưa số này vào đề xuất gửi sếp?"
- "Nhìn bảng so sánh đối thủ của bạn, khoảng trống nào chưa ai làm?"
- "Nếu link agent trích ra mở không được, điều đó nói lên gì?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| AI bịa số liệu thị trường (đưa con số trông rất thật, không nguồn) | Hỏi thẳng agent "số này nguồn ở đâu?". Nếu không có, yêu cầu chuyển sang mục "cần kiểm chứng" và không dùng con số đó cho quyết định cho tới khi tự tra được nguồn thứ hai. |
| AI bịa nguồn (dẫn link/báo cáo không tồn tại) | Tự mở link kiểm. Link chết hoặc nội dung không khớp là dấu hiệu bịa. Bắt agent bỏ nguồn giả, ghi rõ "chưa xác minh được nguồn". |
| Thông tin lỗi thời (số liệu cũ vài năm, đã thay đổi) | Yêu cầu agent ghi mốc thời gian của mọi số liệu. Với thông tin quan trọng, bắt tra lại nguồn mới nhất. Nhắc: dữ liệu không ghi ngày thì coi như không tin được. |
| Agent trả lời chung chung, không đi vào chủ đề | Do khung câu hỏi con còn mơ hồ. Quay lại làm khung cụ thể hơn, mỗi câu hỏi phải trả lời được riêng. |
| Công cụ lớp không có duyệt web | Nói rõ: mọi số liệu agent đưa ra đều là kiến thức nền, phải coi là "cần kiểm chứng". Học viên tự tra nguồn ngoài rồi bổ sung vào báo cáo. |
| Học viên chưa chọn được thị trường/đối thủ | Gợi ý ngay tại lớp: đối thủ trực tiếp của công ty bạn là ai? Hoặc 1 sản phẩm/dịch vụ bạn đang cân nhắc làm. Chọn cái gần công việc nhất. |
| Bảng so sánh sơ sài, thiếu cột | Nhắc đủ 5 cột chuẩn: sản phẩm, giá, điểm mạnh, điểm yếu, định vị. Thiếu cột nào thì bảng chưa dùng để ra quyết định được. |

## Bài tập
- **Tại lớp:** Dựng Deep Research Agent + chạy 1 báo cáo nghiên cứu cho thị trường/đối thủ thật của mình, có ít nhất 1 bảng so sánh đối thủ và mục "điểm cần kiểm chứng thêm".
- **Về nhà:**
  1. Tự mở và kiểm chứng ít nhất 2 số liệu/nguồn trong báo cáo đã làm ở lớp. Ghi lại: cái nào đúng, cái nào sai/không tìm được nguồn.
  2. Chỉnh lại báo cáo sau khi kiểm chứng (hạ các số bịa xuống "cần kiểm chứng", bổ sung nguồn thật).
  3. Nghĩ trước 1 dự án công việc thật để buổi 6 chạy cả dây chuyền: research xong đẩy sang Report Agent viết đề xuất.

## Tiêu chí hoàn thành buổi
- [ ] Dựng xong Deep Research Agent, chạy ra báo cáo theo đúng 6 mục định dạng chuẩn.
- [ ] Lập được khung câu hỏi nghiên cứu (4-6 câu hỏi con) cho chủ đề thật.
- [ ] Chỉ ra được trong báo cáo đâu là dữ kiện, đâu là suy luận, đâu là chỗ chưa chắc.
- [ ] Có 1 bảng so sánh đối thủ đủ 5 cột.
- [ ] Có mục "điểm cần kiểm chứng thêm" và đã kiểm chứng ít nhất 2 mục (hoàn tất khi làm bài về nhà).
- [ ] Hiểu cách nối kết quả research sang Report Agent cho buổi 6.
