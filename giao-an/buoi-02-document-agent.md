# Giáo án Buổi 02: Document Agent (Agent đọc tài liệu)

> Khung chuẩn cho giảng viên. Bám sát template. Loại buổi: Thực chiến.

## Thông tin buổi
- **Buổi:** 02 / 6
- **Loại:** Thực chiến
- **Agent xây dựng:** Document Agent (agent chuyên môn đầu tiên lắp vào workspace)
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - File demo chung: 1 bản hợp đồng/biên bản dài (5-15 trang, PDF hoặc Word) đã ẩn thông tin nhạy cảm. Đặt tên dễ nhớ, ví dụ `demo-hop-dong-dich-vu.pdf`. Gửi link file này cho lớp trước giờ học.
  - Tài khoản AI mẫu đã đăng nhập sẵn, đã có workspace + Orchestrator dựng ở Buổi 1.
  - Mở sẵn file `system-prompts/02-document-agent.md` để chiếu system prompt lên màn hình.
  - Chuẩn bị 1 câu "bẫy ảo giác": một câu hỏi mà tài liệu demo KHÔNG có đáp án (ví dụ hỏi số điện thoại người ký, trong khi hợp đồng không ghi) để diễn cảnh AI bịa và cách chặn.
  - Slide tiêu đề buổi (nếu dùng), nền trắng theo chuẩn CES.

## Mục tiêu buổi (học xong học viên làm được gì)
1. Dựng được Document Agent riêng trong workspace và biết upload tài liệu dài (PDF/Word/bài viết) vào để AI đọc.
2. Ra lệnh cho agent tóm tắt ở nhiều mức độ (3 câu, 1 đoạn, 1 trang), trích ý chính, và bóc tách số liệu/ngày tháng/hạn chót.
3. Biết kỹ thuật hỏi nối tiếp: tóm tắt trước, rồi đào sâu từng mục sau.
4. Nhận ra và chặn được "ảo giác" (AI bịa nội dung không có trong file) bằng quy tắc "không có trong tài liệu thì nói không có".
5. Hiểu cách Orchestrator (Buổi 1) giao việc đọc tài liệu cho Document Agent.

## Kết quả cầm về (deliverable)
- 1 Document Agent chạy được trong workspace cá nhân.
- 1 bản tóm tắt + trích ý từ tài liệu công việc thật của chính học viên.
- System prompt Document Agent đã điền tên và văn phong riêng, lưu lại dùng tiếp.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Document Agent là gì:** một "nhân viên AI" chỉ chuyên đọc tài liệu. Bạn đưa file dài, nó đọc hộ rồi tóm tắt, chỉ ra ý quan trọng, trả lời câu hỏi dựa trên file đó. Không phải hỏi lại chatbot từ đầu mỗi lần.
- **Upload file:** đưa file lên cho AI đọc trực tiếp, thay vì copy-paste từng đoạn. Nhanh hơn và giữ nguyên cấu trúc tài liệu.
- **Tóm tắt nhiều mức:** cùng một tài liệu, bạn xin bản 3 câu để nắm nhanh, hoặc bản 1 trang để hiểu kỹ. Tùy lúc bạn cần gì.
- **Hỏi nối tiếp:** đọc tóm tắt xong thấy mục nào quan trọng thì hỏi tiếp về đúng mục đó. Giống bóc củ hành: lớp ngoài trước, lớp trong sau.
- **Ảo giác (AI bịa):** đôi khi AI trả lời rất trôi chảy nhưng nội dung không có thật trong file. Đây là lỗi nguy hiểm nhất khi làm việc với hợp đồng, số liệu. Cách chặn: bắt agent tuân quy tắc "thông tin nào không có trong tài liệu thì phải nói không có, cấm suy đoán".

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap Buổi 1
- **Lời dẫn:** "Chào cả nhà. Buổi trước mình đã dựng xong workspace và một agent điều phối tên Orchestrator, đúng không? Hôm nay mình lắp nhân viên AI đầu tiên vào workspace đó: một agent chuyên đọc tài liệu. Sau buổi này, những hợp đồng dài, biên bản họp, báo cáo mấy chục trang mà bình thường bạn ngại đọc, sẽ có người đọc hộ và tóm tắt cho bạn trong một phút."
- Recap nhanh Buổi 1: workspace là gì, Orchestrator làm nhiệm vụ điều phối (nhận việc tổng, chia việc cho các agent chuyên môn). Hỏi lớp: "Có ai chưa dựng xong Orchestrator không? Giơ tay để mình hỗ trợ nhanh trước khi vào bài."
- Nối sang buổi hôm nay: "Orchestrator là trưởng nhóm nhưng chưa có nhân viên nào để giao việc. Hôm nay tuyển nhân viên đầu tiên: Document Agent, người đọc tài liệu."
- Nêu mục tiêu buổi: dựng Document Agent, tóm tắt nhiều mức, trích số liệu, và quan trọng nhất là chặn AI bịa.

### [00:15-00:35] Lý thuyết ngắn
- Nội dung trình bày (dùng slide hoặc nói kèm ví dụ):
  1. **Vì sao cần một agent riêng để đọc tài liệu.** Nếu mỗi lần đọc file lại phải mở chat mới, dán nội dung, dặn lại cách trình bày thì rất mất công. Đóng gói thành agent: dặn một lần, dùng mãi.
  2. **Ba việc chính Document Agent làm:** tóm tắt (nhiều mức độ), trích ý chính và số liệu quan trọng (ngày, tiền, hạn chót, tên riêng), trả lời câu hỏi dựa trên file.
  3. **Kỹ thuật hỏi nối tiếp.** Đừng hỏi 10 câu một lúc. Xin tóm tắt trước để có bản đồ tổng thể, rồi mới đào sâu từng mục. Ví dụ: tóm tắt hợp đồng trước, sau đó hỏi riêng "điều khoản phạt hợp đồng nói gì".
  4. **Cảnh báo ảo giác.** Giải thích thẳng: AI đôi khi bịa nội dung nghe rất hợp lý nhưng không có trong file. Với hợp đồng và số liệu, một câu bịa có thể gây thiệt hại thật. Quy tắc vàng: "không có trong tài liệu thì nói không có". Ngay trong system prompt hôm nay đã cài sẵn quy tắc này.
- **Câu hỏi tương tác:** "Trong công việc của bạn, tài liệu nào dài mà bạn ngại đọc nhất? Hợp đồng, biên bản họp, báo cáo tháng, hay giáo trình? Gõ vào chat cho mình xem." (GV đọc vài câu trả lời để chọn ví dụ sát với lớp.)

### [00:35-01:00] Demo giảng viên
- GV chia sẻ màn hình, làm mẫu dựng Document Agent từ đầu (xem chi tiết mục Script demo bên dưới). Vừa làm vừa nói to từng thao tác để học viên bắt kịp.
- **Điểm nhấn phải chỉ rõ:**
  - Chỉ đúng nút tạo agent/project mới và ô dán "Instructions / System prompt".
  - Chỉ đúng nút upload file (hình cái kẹp giấy hoặc dấu cộng), demo kéo thả file vào.
  - Cho lớp thấy 3 mức tóm tắt khác nhau trên cùng một file: bản 3 câu, bản 1 đoạn, bản 1 trang.
  - Demo bóc tách số liệu: ra lệnh "liệt kê tất cả ngày tháng và số tiền trong tài liệu".
  - Diễn cảnh ảo giác: hỏi câu mà file KHÔNG có đáp án. Nếu agent trả lời trung thực "Tài liệu không đề cập" thì khen; nếu agent bịa, chỉ cho lớp thấy đây chính là ảo giác và nhắc lại cách chặn bằng quy tắc trong system prompt.

### [01:00-01:30] Thực hành 1 (dữ liệu mẫu chung)
- Đề bài: mỗi học viên dùng đúng file demo chung mà GV đã gửi, tự dựng Document Agent trong workspace của mình và làm 4 việc:
  1. Tóm tắt file ở mức 3 câu.
  2. Xin lại bản tóm tắt 1 trang.
  3. Bóc tách toàn bộ ngày tháng, số tiền, hạn chót trong file.
  4. Đặt 1 câu hỏi mà file KHÔNG có đáp án, kiểm tra xem agent có nói "không đề cập" hay bịa ra.
- GV đi vòng hỗ trợ (theo dõi qua chia sẻ màn hình của học viên hoặc mời vài người share). Lỗi hay gặp xem bảng "Tình huống hay gặp".
- Chốt Thực hành 1: mời 1-2 học viên khoe kết quả bóc tách số liệu và kết quả câu hỏi bẫy.

### [01:30-01:40] Nghỉ giải lao

### [01:40-02:15] Thực hành 2 (dữ liệu công việc của học viên)
- Đề bài: học viên dùng chính tài liệu công việc thật của mình (hợp đồng, biên bản họp, báo cáo dài đã chuẩn bị trước lớp). Thực hiện:
  1. Upload tài liệu của mình vào Document Agent.
  2. Xin tóm tắt 1 đoạn để nắm tổng thể.
  3. Áp kỹ thuật hỏi nối tiếp: chọn mục quan trọng nhất với công việc và đào sâu bằng 2-3 câu hỏi liên tiếp.
  4. Trích ra "điểm cần lưu ý / rủi ro / hạn chót" của tài liệu đó.
  5. Điền tên mình và văn phong mong muốn vào system prompt, lưu agent lại.
- **Nối với Orchestrator (Buổi 1):** GV hướng dẫn thử một lần cho lớp thấy dây chuyền. Vào Orchestrator, giao một yêu cầu tổng, ví dụ: "Đọc hộ tôi file biên bản họp này và cho tôi 5 việc cần làm sau họp." Orchestrator sẽ phân tích và chỉ ra bước này nên giao cho Document Agent. Nhấn: hôm nay hai agent đã bắt đầu phối hợp, đến Buổi 6 sẽ ghép cả 6.
- GV đi vòng hỗ trợ, ưu tiên người dùng file có số liệu/hạn chót để thấy rõ giá trị.

### [02:15-02:35] Chốt & giao bài
- Tổng kết: hôm nay lớp có thêm 1 nhân viên AI biết đọc tài liệu. Nhắc lại 3 điều nhớ nhất: tóm tắt nhiều mức, hỏi nối tiếp, và luôn cảnh giác ảo giác.
- **Lời dẫn chốt:** "Từ hôm nay, mỗi lần nhận một tài liệu dài, đừng đọc từ trang một nữa. Quăng cho Document Agent, xin bản tóm tắt, rồi hỏi sâu chỗ nào bạn quan tâm. Nhưng nhớ: với hợp đồng và số liệu, luôn mở file gốc kiểm tra lại điểm quan trọng, đừng tin AI 100 phần trăm."
- Bài về nhà (xem mục Bài tập).
- Xem trước Buổi 3: "Buổi sau mình tuyển nhân viên thứ hai: Data Analysis Agent, chuyên đọc file Excel, tính toán và gợi ý biểu đồ. Nhớ chuẩn bị 1 file Excel/CSV công việc thật của bạn nhé."

---

## Script demo (các bước GV thao tác)
1. Mở workspace đã có từ Buổi 1. Bấm tạo project/custom agent mới, đặt tên "Document Agent".
2. Mở file `system-prompts/02-document-agent.md`, copy khối trong dấu ``` ``` ```, dán vào ô "Instructions / System prompt". Điền tên mình vào chỗ `[Họ tên]`, chọn văn phong ở dòng cuối (ví dụ để "ngắn gọn").
3. Lưu agent. Mở khung chat của agent vừa tạo.
4. Bấm nút upload (kẹp giấy / dấu cộng), chọn file demo `demo-hop-dong-dich-vu.pdf`. Chờ file nạp xong.
5. Gõ lệnh tóm tắt 3 câu: "Tóm tắt tài liệu này trong đúng 3 câu." Đọc kết quả cho lớp.
6. Gõ tiếp: "Giờ tóm tắt lại thành 1 trang, chia theo mục." Cho lớp so sánh hai mức tóm tắt.
7. Bóc tách số liệu: "Liệt kê tất cả ngày tháng, số tiền và hạn chót có trong tài liệu, kèm vị trí (mục/trang) nếu có."
8. Hỏi nối tiếp: chọn 1 mục, ví dụ "Điều khoản thanh toán nói gì? Trích nguyên văn câu quan trọng nhất."
9. Diễn cảnh ảo giác: hỏi câu file không có, ví dụ "Số điện thoại của bên A là gì?" Chỉ cho lớp thấy agent trả lời "Tài liệu không đề cập" (nhờ quy tắc trong system prompt). Nếu agent bịa, dừng lại, chỉ rõ đây là ảo giác và nhắc quy tắc.
10. Kết demo: nhắc lớp lưu lại agent này để dùng suốt khóa.

## System prompt dùng trong buổi
- Xem `system-prompts/02-document-agent.md`. Chiếu khối prompt lên màn hình để học viên copy đúng. Nhấn mạnh dòng quy tắc: "Nếu tài liệu không có thông tin tôi hỏi, nói rõ Tài liệu không đề cập, KHÔNG suy đoán."

## Câu hỏi tương tác gợi ý
- "Tài liệu nào trong công việc bạn ngại đọc nhất vì dài?"
- "Theo bạn, nếu AI bịa một con số trong hợp đồng thì hậu quả có thể là gì?"
- "Bạn thường cần bản tóm tắt siêu ngắn để lướt, hay bản dài để hiểu kỹ? Khi nào cần loại nào?"
- "Sau khi có tóm tắt, mục nào bạn muốn hỏi sâu thêm nhất?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| **AI bịa nội dung (ảo giác)**: agent trả lời một thông tin nghe hợp lý nhưng không có trong file | Nhắc học viên kiểm tra lại file gốc. Thêm câu vào lệnh: "Chỉ trả lời dựa trên tài liệu, phần nào không có thì nói không có." Nhấn quy tắc đã cài trong system prompt. Với số liệu quan trọng, luôn đối chiếu file gốc. |
| Upload file mà agent báo không đọc được | Kiểm tra định dạng (PDF/Word/txt), dung lượng không quá lớn. Nếu là PDF scan (ảnh chụp), AI khó đọc chữ, hướng dẫn chuyển sang bản có chữ thật hoặc copy-paste phần nội dung. |
| Tài liệu quá dài, agent chỉ tóm phần đầu, bỏ phần sau | Chia tài liệu thành 2-3 phần upload lần lượt, hoặc yêu cầu "đọc hết toàn bộ file rồi mới tóm tắt, đừng bỏ phần cuối". |
| Tóm tắt bị chung chung, không có ý cụ thể | Yêu cầu rõ hơn: "Tóm tắt theo từng mục, mỗi mục 1 gạch đầu dòng, kèm số liệu nếu có." Hỏi nối tiếp vào mục cần. |
| Học viên chưa dựng xong Orchestrator từ Buổi 1 | Hỗ trợ nhanh ở phần mở đầu hoặc giờ nghỉ. Buổi 2 vẫn dựng Document Agent độc lập được, phần nối Orchestrator để cuối, không chặn tiến độ. |
| Agent trả lời bằng tiếng Anh hoặc văn phong sai | Nhắc điền văn phong trong system prompt và thêm "Trả lời bằng tiếng Việt" vào lệnh. |
| File công việc nhạy cảm (hợp đồng thật, dữ liệu khách) | Nhắc học viên ẩn thông tin nhạy cảm trước khi upload nếu lo ngại, hoặc dùng tài liệu ít nhạy cảm hơn để luyện. Không ép ai upload dữ liệu mật. |

## Bài tập
- **Tại lớp:**
  - Thực hành 1: dựng Document Agent, chạy 3 mức tóm tắt + bóc số liệu + câu hỏi bẫy ảo giác trên file demo chung.
  - Thực hành 2: áp Document Agent vào 1 tài liệu công việc thật của mình, dùng kỹ thuật hỏi nối tiếp, trích rủi ro/hạn chót.
- **Về nhà:**
  - Chọn 2 tài liệu dài khác nhau trong công việc (ví dụ 1 hợp đồng và 1 biên bản họp), cho Document Agent tóm tắt và trích điểm cần lưu ý mỗi file.
  - Thử tính năng so sánh: upload 2 tài liệu liên quan (ví dụ hợp đồng bản cũ và bản mới) và hỏi "Hai bản này khác nhau ở đâu, có điểm nào mâu thuẫn không?"
  - Ghi lại 1 lần agent suýt bịa nội dung và cách bạn phát hiện, mang chia sẻ đầu Buổi 3.
  - Chuẩn bị 1 file Excel/CSV công việc thật cho Buổi 3.

## Tiêu chí hoàn thành buổi
- [ ] Học viên dựng được Document Agent trong workspace và upload được tài liệu.
- [ ] Tạo được ít nhất 2 mức tóm tắt khác nhau trên cùng một file.
- [ ] Bóc tách được số liệu/ngày tháng/hạn chót từ tài liệu.
- [ ] Thực hiện được ít nhất 1 chuỗi hỏi nối tiếp (tóm tắt trước, đào sâu sau).
- [ ] Nhận diện được ảo giác: đặt câu hỏi file không có và xác nhận agent nói "không đề cập" thay vì bịa.
- [ ] Áp Document Agent vào tài liệu công việc thật và lưu agent lại để dùng tiếp.
