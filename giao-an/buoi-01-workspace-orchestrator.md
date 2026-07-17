# Giáo án Buổi 01 - Workspace & Orchestrator Agent

> Khung chuẩn cho giảng viên. Buổi nền tảng, quan trọng nhất của khóa. Học viên xây bộ khung AI Workspace và tạo agent đầu tiên: Orchestrator.

## Thông tin buổi
- **Buổi:** 01 / 6
- **Loại:** Nền tảng
- **Agent xây dựng:** Orchestrator (agent điều phối, "trưởng nhóm")
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - Tài khoản AI mẫu đã đăng nhập sẵn (bản có tính năng tạo project/custom agent + upload file). Chốt công cụ cuối cùng theo tài khoản CES cấp cho lớp.
  - Một Orchestrator mẫu đã dựng sẵn (bối cảnh của một nhân vật giả định, ví dụ "Lan, kế toán") để chiếu khi cần so sánh.
  - File `system-prompts/01-orchestrator-agent.md` mở sẵn để copy phần system prompt.
  - Slide 5-7 trang (khái niệm agent, cấu trúc system prompt, bản đồ 6 buổi). Slide nền trắng theo brand CES.
  - Một yêu cầu công việc mẫu để test Orchestrator, ví dụ: "Giúp tôi làm báo cáo doanh thu tháng 5 cho sếp."

## Mục tiêu buổi (học xong học viên làm được gì)
1. Phân biệt được "agent" và "chat thường", nói được vì sao đóng gói việc lặp lại thành agent thì lợi hơn.
2. Dựng xong bộ khung AI Workspace cá nhân: đặt tên, tổ chức chỗ chứa để buổi sau lắp thêm agent.
3. Tạo được agent đầu tiên (Orchestrator) bằng cách tạo project/custom agent và dán system prompt.
4. Hiểu cấu trúc một system prompt tốt gồm 5 phần: vai trò, nhiệm vụ, quy tắc, bối cảnh, định dạng đầu ra; tự điền được phần bối cảnh cá nhân.
5. Chạy thử Orchestrator với một yêu cầu công việc thật của mình và đọc được kế hoạch chia việc mà nó trả về.

## Kết quả cầm về (deliverable)
- 1 AI Workspace cá nhân đã đặt tên, có cấu trúc rõ ràng.
- 1 Orchestrator Agent chạy được, đã điền bối cảnh cá nhân.
- 1 ảnh chụp màn hình phần trả lời của Orchestrator cho một yêu cầu công việc thật (làm bằng chứng hoàn thành buổi).

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)

- **Chat thường:** mỗi lần mở ra là một tờ giấy trắng. Bạn phải kể lại bạn là ai, làm nghề gì, muốn định dạng gì. Xong việc đóng lại là mất hết, lần sau kể lại từ đầu.
- **Agent:** một ô nhớ đã ghi sẵn vai trò, quy tắc, bối cảnh và cách trình bày. Gọi ra là nó chạy đúng ngay, không cần dặn lại. Giống như bạn có một nhân viên đã được đào tạo, thay vì mỗi ngày tuyển một người lạ rồi phải hướng dẫn lại.
- **Workspace:** cái tủ chứa các agent. Buổi 1 dựng tủ và bỏ vào agent đầu tiên. Năm buổi sau, mỗi buổi thêm một agent vào cùng cái tủ này.
- **Orchestrator (agent điều phối):** "trưởng nhóm". Nó không tự ôm hết việc. Bạn giao một yêu cầu tổng, nó chia nhỏ ra và chỉ rõ phần nào nên đưa cho agent nào (Document đọc tài liệu, Data phân tích Excel, Report viết báo cáo, Research đi tra cứu). Buổi 2-5 mình xây các agent chuyên môn đó, buổi 6 ghép cả dây chuyền.
- **System prompt:** bản mô tả công việc dán vào agent lúc tạo. Một bản tốt có 5 phần: (1) Vai trò: agent là ai; (2) Nhiệm vụ: làm gì, theo trình tự nào; (3) Quy tắc: được và không được làm gì; (4) Bối cảnh: thông tin về bạn và công việc của bạn; (5) Định dạng đầu ra: trình bày kết quả kiểu gì.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & recap
- **Lời dẫn:** "Chào cả nhà. Đây là buổi đầu tiên và cũng là buổi nền tảng nhất của khóa. Hôm nay mình không học lý thuyết suông đâu, cuối buổi mỗi người sẽ có một trợ lý AI của riêng mình, đã biết bạn là ai và làm nghề gì, gọi ra là chạy. Buổi này làm chắc thì năm buổi sau nhẹ nhàng."
- Vì là buổi 1, không có buổi trước để recap. Thay bằng: điểm danh nhanh, hỏi lớp đã chuẩn bị được gì chưa.
- **Kiểm tra chuẩn bị (đọc lên, hỏi giơ tay):**
  - "Ai đã đăng nhập được tài khoản AI theo link CES gửi rồi?"
  - "Ai đã mang theo 2-3 file công việc thật của mình?"
  - Ai chưa có tài khoản: ghép cặp ngồi xem cùng bạn bên cạnh, GV hỗ trợ sau giờ.
- Nêu mục tiêu buổi: hiểu agent là gì, dựng workspace, tạo Orchestrator, chạy thử với việc thật.
- Chiếu nhanh bản đồ 6 buổi (từ file `00-tong-quan-khoa-hoc.md` mục 5) để lớp thấy Orchestrator nằm ở trung tâm.

### [00:15-00:35] Lý thuyết ngắn
- **Nội dung 1: Agent khác chat thường ở đâu.** Dùng ví von "tờ giấy trắng mỗi lần" so với "nhân viên đã được đào tạo". Hỏi lớp trước khi giảng: xem phần Câu hỏi tương tác.
- **Nội dung 2: Vì sao đóng gói việc lặp lại thành agent.** Cho lớp thấy ích lợi: đỡ dặn lại, đầu ra nhất quán, càng dùng càng tinh chỉnh cho hợp mình.
- **Nội dung 3: Orchestrator là gì và vì sao học đầu tiên.** Nhấn: nó là trưởng nhóm điều phối, không phải làm thay. Chiếu bản đồ 6 buổi lần nữa, chỉ tay vào ô Orchestrator ở giữa.
- **Nội dung 4: Cấu trúc 5 phần của một system prompt tốt.** Liệt kê: Vai trò, Nhiệm vụ, Quy tắc, Bối cảnh, Định dạng đầu ra. Nói trước rằng lát nữa demo sẽ chỉ đúng 5 phần này trong system prompt Orchestrator.
- **Câu hỏi tương tác:** "Mỗi ngày các bạn có việc gì phải lặp đi lặp lại và lần nào cũng phải giải thích lại từ đầu cho AI không? Cho mình một ví dụ."

### [00:35-01:00] Demo giảng viên
GV chia màn hình, thao tác thật từng bước, vừa làm vừa nói. Học viên chỉ xem, chưa làm theo (sẽ làm ở Thực hành 1).

- Bước 1: Mở công cụ AI, chỉ cho lớp thấy khu vực tạo "project" hoặc "custom agent" nằm ở đâu trên giao diện.
- Bước 2: Tạo một workspace/project mới, đặt tên rõ ràng, ví dụ "AI Workspace - Lan". Giải thích quy tắc đặt tên để buổi sau dễ tìm.
- Bước 3: Tạo agent mới bên trong, đặt tên "Orchestrator".
- Bước 4: Mở file `system-prompts/01-orchestrator-agent.md`, copy phần trong khối mã, dán vào ô Instructions/System prompt của agent.
- Bước 5: Dừng lại, chỉ cho lớp thấy 5 phần trong system prompt vừa dán: Vai trò (dòng đầu), Nhiệm vụ, Quy tắc, Bối cảnh của tôi, và định dạng đầu ra nằm rải trong phần Nhiệm vụ. Đây là điểm nhấn dạy học, đừng lướt qua.
- Bước 6: Điền phần "Bối cảnh của tôi" cho nhân vật mẫu: công việc chính, loại việc lặp nhiều nhất, định dạng hay cần, văn phong.
- Bước 7: Lưu agent. Gõ thử một yêu cầu mẫu: "Giúp tôi làm báo cáo doanh thu tháng 5 cho sếp." Đọc to phần Orchestrator trả về, chỉ cho lớp thấy nó chia việc và hỏi lại tối đa 3 câu chứ không làm bừa.
- **Điểm nhấn phải chỉ rõ:**
  - Chỗ tạo project/agent nằm ở đâu trên giao diện (dễ lạc nhất).
  - 5 phần của system prompt, chỉ tận nơi trên màn hình.
  - Điền bối cảnh càng kỹ, Orchestrator điều phối càng đúng.
  - Orchestrator chia việc và hỏi lại, chứ không tự bịa ra kết quả.

### [01:00-01:30] Thực hành 1 (dữ liệu mẫu chung)
- **Đề bài:** Mỗi học viên tự dựng lại đúng những gì GV vừa demo, nhưng dùng bối cảnh mẫu chung do GV phát (để cả lớp đồng bộ, GV dễ hỗ trợ).
  - Bối cảnh mẫu chung (GV đọc/gửi qua chat Zoom): "Nhân vật: Minh, nhân viên kinh doanh một công ty phần mềm. Việc lặp nhiều nhất: viết email chào hàng và báo cáo doanh số tuần. Định dạng hay cần: email và bảng. Văn phong: thân thiện, ngắn gọn."
  - Các bước học viên làm: tạo workspace đặt tên của mình → tạo agent Orchestrator → dán system prompt từ file 01 → điền bối cảnh mẫu chung ở trên → lưu → test bằng câu: "Giúp tôi chuẩn bị báo cáo doanh số tuần này gửi trưởng phòng."
- GV đi vòng (theo dõi màn hình chia sẻ hoặc breakout room), tập trung 3 lỗi hay gặp: không tìm thấy chỗ tạo agent, dán thiếu system prompt, quên điền bối cảnh.
- Ai xong sớm: thử đổi văn phong trong bối cảnh từ "ngắn gọn" sang "trang trọng" rồi test lại, xem đầu ra đổi thế nào.

### [01:30-01:40] Nghỉ giải lao
- Nhắc lớp: sau giờ nghỉ sẽ thay bối cảnh mẫu bằng bối cảnh thật của chính mình, nên chuẩn bị sẵn 2-3 câu mô tả công việc của bản thân.

### [01:40-02:15] Thực hành 2 (dữ liệu công việc của học viên)
- **Đề bài:** Sửa lại phần "Bối cảnh của tôi" trong Orchestrator vừa dựng, thay bằng thông tin thật của chính học viên:
  - Công việc chính của bạn là gì.
  - Loại việc bạn phải lặp lại nhiều nhất.
  - Định dạng đầu ra bạn hay cần (báo cáo, email, slide, bảng...).
  - Văn phong bạn muốn (trang trọng, thân thiện, ngắn gọn...).
  - Sửa cả dòng vai trò đầu tiên cho đúng họ tên và chức danh của mình.
- Sau khi điền xong, test bằng một yêu cầu công việc thật đang chờ xử lý của bạn, ví dụ: "Tuần này tôi phải [việc thật]. Giúp tôi lên kế hoạch làm."
- Chụp lại màn hình phần Orchestrator trả về. Đây là bằng chứng hoàn thành buổi.
- GV đi vòng hỗ trợ. Khuyến khích 2-3 học viên chia sẻ màn hình, đọc to yêu cầu và kế hoạch Orchestrator trả về để cả lớp học lẫn nhau.

### [02:15-02:35] Chốt & giao bài
- **Tổng kết:** nhắc lại 3 thứ vừa làm được: dựng workspace, tạo Orchestrator, điền bối cảnh thật và chạy thử. Nhấn: đây là cái tủ và agent nền tảng, năm buổi sau lắp thêm vào đúng cái tủ này.
- Xác nhận nhanh: hỏi lớp ai đã có ảnh chụp Orchestrator trả về rồi, nhắc ai chưa thì làm nốt và nộp qua Zalo.
- **Bài về nhà:** xem phần Bài tập.
- **Xem trước buổi sau:** "Buổi 2 mình xây Document Agent, agent chuyên đọc và tóm tắt tài liệu dài. Nhớ mang theo 1 file tài liệu dài thật của mình, ví dụ hợp đồng, báo cáo, hoặc tài liệu PDF vài chục trang."
- **Câu hỏi tương tác chốt:** "Sau buổi hôm nay, ai thấy có một việc trong công việc của mình mà một agent như thế này sẽ tiết kiệm được kha khá thời gian? Kể một câu."

---

## Script demo (các bước GV thao tác)
1. Mở công cụ AI, chỉ khu vực tạo project/custom agent trên giao diện.
2. Tạo workspace/project mới, đặt tên "AI Workspace - [tên]".
3. Tạo agent con, đặt tên "Orchestrator".
4. Mở file `system-prompts/01-orchestrator-agent.md`, copy khối system prompt.
5. Dán vào ô Instructions/System prompt của agent.
6. Chỉ rõ 5 phần trong system prompt vừa dán (vai trò, nhiệm vụ, quy tắc, bối cảnh, định dạng đầu ra).
7. Điền phần "Bối cảnh của tôi" cho nhân vật mẫu.
8. Lưu agent.
9. Test bằng yêu cầu mẫu, đọc to kết quả, chỉ chỗ Orchestrator chia việc và hỏi lại.

## System prompt dùng trong buổi
- Xem `system-prompts/01-orchestrator-agent.md`. GV dẫn học viên mở đúng file này để copy, không đọc chép lại toàn bộ vào slide.
- Phần học viên phải tự sửa: dòng vai trò đầu tiên (họ tên, chức danh, công ty/lĩnh vực) và toàn bộ mục "BỐI CẢNH CỦA TÔI".

## Câu hỏi tương tác gợi ý
- "Mỗi lần dùng AI, các bạn có phải kể lại từ đầu bạn là ai, làm gì không? Mất bao lâu mỗi lần?"
- "Việc gì trong tuần bạn phải làm đi làm lại và lần nào cũng na ná nhau?"
- "Theo bạn, một trưởng nhóm giỏi thì tự làm hết việc hay chia việc cho đúng người? Orchestrator hoạt động y như vậy."
- "Nhìn phần Orchestrator vừa trả về, nó chia thành mấy bước? Bước nào nó định giao cho agent khác?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Học viên không tìm thấy chỗ tạo project/custom agent | GV chia màn hình chỉ lại vị trí trên giao diện. Công cụ khác nhau đặt nút ở chỗ khác nhau, chốt đúng công cụ CES cấp cho lớp và mô tả vị trí cụ thể. |
| Tài khoản không có tính năng tạo project/agent | Kiểm tra học viên đang dùng bản miễn phí hay bản có tính năng. Nếu chưa đúng bản, hướng dẫn nâng cấp theo tài khoản CES cấp, hoặc ghép cặp ngồi cùng bạn để không mất nhịp buổi. |
| Dán system prompt bị thiếu, mất đoạn | Nhắc chọn toàn bộ khối trong file rồi copy lại. Kiểm tra ô nhập không bị giới hạn ký tự cắt bớt. |
| Điền bối cảnh qua loa, một hai chữ | GV nhắc: bối cảnh càng chi tiết, Orchestrator điều phối càng đúng. Gợi mỗi mục viết ít nhất một câu đủ ý. |
| Orchestrator tự làm luôn thay vì chia việc và hỏi lại | Nhắc học viên kiểm tra đã dán đủ phần NHIỆM VỤ chưa. Có thể do dán thiếu. Test lại sau khi dán đủ. |
| Học viên chưa mang file công việc thật | Không sao ở buổi này vì Orchestrator chưa cần upload file. Dùng tạm một yêu cầu bằng lời. Nhắc bắt buộc mang file cho buổi 2. |
| Học viên hỏi "dùng công cụ nào mới đúng" | Chốt theo tài khoản CES cấp cho lớp. Nhấn: cách làm giống nhau trên các công cụ, học kỹ nguyên lý thì đổi công cụ vẫn làm được. |
| Đầu ra bằng tiếng Anh hoặc văn phong không hợp | Kiểm tra quy tắc "trả lời bằng tiếng Việt" còn trong system prompt không, và mục văn phong trong bối cảnh đã điền chưa. |

## Bài tập
- **Tại lớp:** Dựng xong workspace + Orchestrator, điền bối cảnh thật của mình, chạy thử với một yêu cầu công việc thật, chụp màn hình phần trả về.
- **Về nhà:**
  1. Dùng Orchestrator cho ít nhất 2 việc thật khác nhau trong tuần. Ghi lại 1 chỗ nó điều phối tốt và 1 chỗ chưa hợp ý.
  2. Tinh chỉnh phần bối cảnh hoặc quy tắc trong system prompt cho hợp mình hơn, ghi lại đã sửa gì.
  3. Chuẩn bị cho buổi 2: chọn sẵn 1 tài liệu dài thật (PDF/Word vài chục trang) sẽ dùng để luyện Document Agent.

## Tiêu chí hoàn thành buổi
- [ ] Đã tạo được workspace cá nhân, có tên rõ ràng.
- [ ] Đã tạo được agent Orchestrator và dán đủ system prompt.
- [ ] Nhận ra và chỉ được 5 phần của system prompt.
- [ ] Đã điền phần bối cảnh bằng thông tin thật của bản thân.
- [ ] Đã chạy thử với một yêu cầu công việc thật và có ảnh chụp phần Orchestrator trả về.
- [ ] Nộp ảnh chụp qua Zalo lớp.
