# Giáo án Buổi 04 - Report Agent (Agent soạn báo cáo & văn bản)

> Khung chuẩn cho giảng viên. File này bám đúng `_template-giao-an.md`.

## Thông tin buổi
- **Buổi:** 04 / 6
- **Loại:** Thực chiến
- **Agent xây dựng:** Report Agent (agent biến ý và số liệu thô thành văn bản hoàn chỉnh)
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - File demo: 1 bảng số liệu bán hàng thô (5-7 dòng, dạng gạch đầu dòng hoặc bảng đơn giản) để demo soạn báo cáo.
  - 1 mẩu email thô (vài ý rời) để demo soạn email công sở.
  - Nếu có: lấy sẵn 1 output số liệu từ Data Analysis Agent (buổi 3) để show mạch nối buổi 3 sang buổi 4.
  - Slide (nếu dùng): 4 khung cấu trúc văn bản (báo cáo / đề xuất / email / dàn ý slide).
  - Chuẩn bị sẵn 1 "văn phong công ty mẫu" (2-3 câu mô tả tone) để dạy cách lưu vào bối cảnh agent.
  - Tài khoản AI đã đăng nhập, tạo sẵn 1 project trống để dựng agent trực tiếp.

## Mục tiêu buổi (học xong học viên làm được gì)
1. Dựng được Report Agent riêng: dán system prompt, điền tên, chức danh, công ty, văn phong công ty vào bối cảnh agent.
2. Từ số liệu hoặc ý thô, soạn ra 4 loại văn bản công việc: báo cáo (tuần/tháng/dự án), đề xuất, email, dàn ý slide, đúng cấu trúc từng loại.
3. Nối được đầu ra buổi 3 (số liệu từ Data Analysis Agent) thành báo cáo hoàn chỉnh ở buổi 4.
4. Áp đúng 3 quy tắc CES: email gửi đi không emoji, văn phong chuyên nghiệp công sở, không bịa số (chỗ thiếu để `[đợi bổ sung]`).

## Kết quả cầm về (deliverable)
- 1 Report Agent đã dựng xong, chạy được ngay.
- Tối thiểu 2 văn bản hoàn chỉnh: 1 báo cáo (hoặc đề xuất) + 1 email công việc, soạn từ dữ liệu thật của học viên.
- System prompt Report Agent đã điền thông tin cá nhân, lưu lại dùng tiếp.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)

**1. Report Agent làm gì.** Đây là agent chuyên "viết văn bản công việc". Bạn đưa ý rời hoặc số liệu thô, agent trả về một bản hoàn chỉnh đúng bố cục, đúng giọng công ty. Bạn không phải viết lại từ đầu mỗi lần; chỉ đưa nguyên liệu và nói rõ loại văn bản cần.

**2. Mỗi loại văn bản có một bộ khung cố định.** Viết nhanh và chuẩn là nhờ khung. Bốn khung dùng trong buổi:

| Loại văn bản | Khung (thứ tự các phần) | Dùng khi nào |
|---|---|---|
| Báo cáo tuần/tháng/dự án | Mở đầu (kỳ báo cáo) → Nội dung chính (việc đã làm) → Kết quả (số liệu) → Vướng mắc → Đề xuất/Kế hoạch tới | Báo cáo định kỳ cho sếp |
| Đề xuất / Proposal | Bối cảnh → Vấn đề → Giải pháp → Lợi ích → Chi phí → Kế hoạch triển khai | Xin duyệt ngân sách, đề xuất ý tưởng |
| Email công sở | Tiêu đề rõ → Lời chào → Thân email (1 ý chính, gọn) → Đề nghị/hành động → Lời kết + chữ ký | Gửi sếp, khách, đồng nghiệp, đối tác |
| Dàn ý slide | Liệt kê từng slide: tiêu đề slide + 3-5 gạch ý + gợi ý hình/biểu đồ | Chuẩn bị thuyết trình nhanh |

**3. Lưu văn phong công ty vào bối cảnh agent.** "Văn phong" là cách công ty bạn hay viết: xưng hô thế nào, trang trọng hay thân thiện, có ký tên chức danh gì. Bạn viết 2-3 câu mô tả văn phong đó, dán vào phần bối cảnh của agent một lần. Từ đó mọi văn bản agent viết đều giữ đúng giọng, không phải dặn lại.

**4. Ba quy tắc CES bắt buộc (nhấn mạnh cả buổi):**
- Email gửi đi KHÔNG emoji. Văn bản công sở là văn bản chuyên nghiệp, không chèn icon.
- Văn phong chuyên nghiệp công sở: câu rõ ràng, tránh sáo rỗng, không dùng từ suồng sã.
- KHÔNG bịa số. Agent chỉ được dùng số bạn cung cấp. Chỗ nào thiếu số, agent để dấu `[đợi bổ sung]` để bạn tự điền, tuyệt đối không tự "đoán" số cho đẹp báo cáo.

**5. Mạch nối buổi 3 sang buổi 4.** Buổi 3 (Data Analysis Agent) cho ra con số và nhận xét từ file Excel. Buổi 4 lấy đúng những con số đó làm nguyên liệu, biến thành báo cáo chữ hoàn chỉnh. Data Agent lo phần "ra số", Report Agent lo phần "viết thành văn bản".

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn:** "Chào cả lớp. Ba buổi qua mình đã có bộ khung workspace, agent điều phối, agent đọc tài liệu và agent phân tích số liệu. Hôm nay mình xây mắt xích còn thiếu: agent viết văn bản. Sau buổi này, bạn đưa vài dòng số liệu thô, agent trả lại một báo cáo hoàn chỉnh gửi sếp được luôn."
- Recap nhanh buổi 3: Data Analysis Agent nhận file Excel, trả về con số và nhận xét. Hỏi lớp: "Buổi 3 xong, bạn có con số rồi. Nhưng sếp đâu đọc file Excel thô, sếp cần một bản báo cáo. Ai đang phải tự ngồi gõ lại báo cáo từ số liệu?" (chờ vài cánh tay).
- Nêu mục tiêu buổi: dựng Report Agent, soạn được 4 loại văn bản, nối số liệu buổi 3 thành báo cáo.
- Nhắc trước 3 quy tắc CES sẽ gặp cả buổi: không emoji trong email, văn phong công sở, không bịa số.

### [00:15-00:35] Lý thuyết ngắn (cấu trúc văn bản)
- Trình bày bảng 4 khung văn bản (mục Khái niệm cốt lõi số 2). Với mỗi khung, đọc lướt thứ tự các phần, nói 1 câu "vì sao phần này đứng ở đây".
  - Báo cáo: sếp cần biết ngay "làm gì, ra kết quả gì, vướng gì, tới đây làm gì" nên đặt kết quả và vướng mắc lên trước phần dài dòng.
  - Đề xuất: phải nêu vấn đề trước, rồi mới tới giải pháp, cuối cùng là chi phí, để người duyệt thấy lý do trước con số tiền.
  - Email: một email một ý chính, tiêu đề phải nói đúng việc, đọc tiêu đề là biết mở hay để sau.
  - Dàn ý slide: mỗi slide một tiêu đề, 3-5 gạch ý, không nhồi chữ.
- Giải thích cách lưu văn phong công ty vào bối cảnh agent (mục cốt lõi số 3): cho lớp xem 1 đoạn mô tả văn phong mẫu.
- Nhấn 3 quy tắc CES kèm ví dụ ngắn (mục cốt lõi số 4).
- **Câu hỏi tương tác:** "Trong công việc của bạn, loại văn bản nào bạn phải viết đi viết lại nhiều nhất: báo cáo, email, hay đề xuất?" (để học viên tự chọn thứ sẽ luyện ở thực hành 2).

### [00:35-01:00] Demo giảng viên (soạn 1 báo cáo từ số liệu)
- GV dựng Report Agent trực tiếp: tạo project mới, dán khối system prompt từ `system-prompts/04-report-agent.md`, điền tên, chức danh, công ty, văn phong mặc định, người nhận thường là "sếp".
- **Điểm nhấn phải chỉ rõ:**
  - Chỉ vào dòng "KHÔNG bịa số liệu, chỗ thiếu để `[đợi bổ sung]`" và dòng "KHÔNG dùng emoji trong email và báo cáo trang trọng" trong system prompt. Nói rõ đây là 2 quy tắc CES đã nhúng sẵn vào agent.
  - Cho lớp thấy agent hỏi lại tối đa 3 câu khi thiếu thông tin cốt lõi (đối tượng nhận, mục đích, số liệu) trước khi viết.
- GV đưa bảng số liệu thô demo (số bán hàng tuần), yêu cầu agent soạn "báo cáo tuần". Đọc to output, chỉ ra: bố cục đúng khung báo cáo, số liệu khớp đúng số GV đưa, chỗ GV cố tình bỏ trống thì agent để `[đợi bổ sung]` chứ không tự bịa.
- Demo 1 vòng chỉnh: gõ "trang trọng hơn" hoặc "rút gọn còn nửa trang" để lớp thấy agent tinh chỉnh được.
- Nếu có sẵn output số liệu từ Data Agent buổi 3: dán vào, cho agent viết báo cáo, chốt thông điệp "đây là mạch nối buổi 3 sang buổi 4".

### [01:00-01:30] Thực hành 1 (dữ liệu mẫu chung)
- Đề bài: cả lớp dùng chung 1 bộ dữ liệu thô GV phát (gợi ý: vài dòng số liệu công việc + vài ý rời cho email). Mỗi học viên:
  1. Dựng Report Agent của mình (dán system prompt, điền thông tin cá nhân).
  2. Soạn 1 báo cáo tuần từ bộ số liệu mẫu.
  3. Soạn 1 email công việc từ mấy ý rời mẫu, kiểm tra email KHÔNG có emoji.
- GV đi vòng hỗ trợ, soi 3 lỗi hay gặp: chưa điền văn phong nên giọng chung chung; email lỡ có emoji; agent bịa số ở chỗ thiếu (nhắc học viên yêu cầu agent để `[đợi bổ sung]`).

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2 (văn bản công việc thật của học viên)
- Đề bài: học viên lấy đúng việc soạn thảo thật mình mang tới (báo cáo, email, hoặc đề xuất đang phải viết) và dùng Report Agent xử lý.
  1. Nạp văn phong công ty của mình vào bối cảnh agent (2-3 câu mô tả tone thật).
  2. Đưa số liệu hoặc ý thô thật, chọn đúng loại văn bản, cho agent soạn.
  3. Tinh chỉnh 1-2 vòng (trang trọng hơn / rút gọn / đổi giọng) tới khi dùng được.
  4. Tự kiểm tra 3 quy tắc CES: không emoji trong email, giọng công sở, số liệu khớp và chỗ thiếu để `[đợi bổ sung]`.
- GV đi vòng, ưu tiên giúp học viên chọn đúng khung văn bản và sửa chỗ agent bịa số.

### [02:15-02:35] Chốt & giao bài
- Tổng kết: mỗi người giờ có Report Agent chạy được + tối thiểu 2 văn bản hoàn chỉnh.
- Nhắc lại 3 quy tắc CES một lần cuối.
- Giao bài về nhà (xem mục Bài tập).
- Xem trước buổi 5: Deep Research Agent (agent đi nghiên cứu, tổng hợp thông tin nhiều nguồn). Nhắc học viên mang 1 chủ đề cần tìm hiểu cho buổi sau.

---

## Script demo (các bước GV thao tác)
1. Mở tài khoản AI, tạo project/agent mới, đặt tên "Report Agent".
2. Mở `system-prompts/04-report-agent.md`, copy khối trong dấu ``` ```, dán vào phần chỉ dẫn của agent.
3. Điền chỗ ngoặc vuông: `[Họ tên]`, `[chức danh]`, `[công ty]`, văn phong mặc định (chọn "thân thiện chuyên nghiệp"), người nhận thường là "sếp".
4. Dán 2-3 câu mô tả văn phong công ty mẫu vào phần bối cảnh.
5. Đưa bảng số liệu thô demo, gõ: "Soạn báo cáo tuần từ số liệu này."
6. Chỉ cho lớp: agent hỏi lại (nếu thiếu), rồi trả báo cáo đúng khung. Đọc to, đối chiếu số liệu, chỉ chỗ `[đợi bổ sung]`.
7. Gõ 1 lệnh tinh chỉnh: "Rút gọn còn nửa trang, trang trọng hơn."
8. Chuyển demo email: đưa vài ý rời, gõ "Soạn email báo cáo tiến độ gửi sếp." Chỉ rõ output không có emoji.
9. (Nếu có) Dán output số liệu từ Data Agent buổi 3, cho agent viết báo cáo, chốt mạch nối buổi 3 sang buổi 4.

## System prompt dùng trong buổi
- Xem `system-prompts/04-report-agent.md` (bản đầy đủ để copy nằm trong workbook học viên).

## Câu hỏi tương tác gợi ý
- "Loại văn bản nào bạn phải viết đi viết lại nhiều nhất: báo cáo, email hay đề xuất?"
- "Nếu agent tự điền một con số không có trong dữ liệu bạn đưa, hậu quả là gì khi báo cáo tới tay sếp?"
- "Văn phong công ty bạn: xưng hô thế nào, trang trọng hay thân thiện? Ai tả thử trong 1 câu?"
- "Email của bạn hôm nay có hay chèn emoji không? Vì sao email công việc nên bỏ emoji?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Văn phong output chưa đúng giọng công ty (quá cứng hoặc quá suồng sã) | Học viên chưa nạp văn phong vào bối cảnh. Hướng dẫn viết 2-3 câu mô tả tone thật rồi dán vào phần bối cảnh agent; hoặc gõ lệnh "đổi sang giọng trang trọng hơn / thân thiện hơn". |
| AI bịa số không có trong dữ liệu | Nhắc lại quy tắc CES. Yêu cầu học viên thêm vào lệnh: "Chỉ dùng số tôi cung cấp, chỗ nào thiếu để `[đợi bổ sung]`, tuyệt đối không tự điền số." Kiểm tra system prompt đã có dòng cấm bịa số chưa. |
| Email lỡ có emoji | Chỉ ra quy tắc CES: email gửi đi không emoji. Gõ lệnh "Bỏ hết emoji, viết lại theo văn phong công sở chuyên nghiệp." Nhắc kiểm tra lại trước khi gửi. |
| Agent viết dài dòng, lan man | Gõ "Rút gọn còn [số] dòng, mỗi ý một gạch đầu dòng, bỏ câu sáo rỗng." |
| Học viên không biết chọn loại văn bản nào | GV hỏi mục đích và người nhận, rồi map vào 1 trong 4 khung. Ví dụ xin duyệt tiền thì dùng khung đề xuất. |
| Agent hỏi lại quá nhiều câu | Bình thường: agent hỏi tối đa 3 câu khi thiếu thông tin cốt lõi. Hướng dẫn học viên đưa đủ đối tượng nhận, mục đích, số liệu ngay từ đầu để agent viết luôn. |
| Số liệu buổi 3 dán vào bị rối | Hướng dẫn dán phần kết luận/con số gọn của Data Agent, không dán cả bảng thô dài; nói rõ với agent "đây là số liệu đã phân tích, viết thành báo cáo tuần." |

## Bài tập
- **Tại lớp:** Dựng xong Report Agent + soạn tối thiểu 2 văn bản hoàn chỉnh (1 báo cáo hoặc đề xuất + 1 email) từ dữ liệu thật của mình, đạt 3 quy tắc CES.
- **Về nhà:**
  1. Nạp văn phong công ty thật vào Report Agent và lưu lại.
  2. Soạn 1 báo cáo tuần thật của công việc mình, kiểm tra không có số bịa (chỗ thiếu để `[đợi bổ sung]`).
  3. Soạn 1 email công việc thật gửi sếp hoặc đối tác, rà kỹ không còn emoji.
  4. (Nếu đã có agent buổi 3) Thử nối: cho Data Agent ra số, đưa số đó sang Report Agent viết báo cáo.

## Tiêu chí hoàn thành buổi
- [ ] Dựng xong Report Agent, đã điền tên/chức danh/công ty/văn phong.
- [ ] Soạn được tối thiểu 2 văn bản hoàn chỉnh đúng khung (báo cáo/đề xuất + email).
- [ ] Email không có emoji, văn phong chuyên nghiệp công sở.
- [ ] Không có số bịa; chỗ thiếu số để `[đợi bổ sung]`.
- [ ] Hiểu và làm được mạch nối số liệu buổi 3 thành báo cáo buổi 4 (ít nhất thử 1 lần).
