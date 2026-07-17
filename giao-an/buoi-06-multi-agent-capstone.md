# Giáo án Buổi 06: Multi-Agent System + Capstone

> Khung chuẩn cho giảng viên. Buổi cuối khóa: không tạo agent mới, ghép 5 agent thành 1 dây chuyền và chốt khóa bằng phần trình bày capstone của học viên.

## Thông tin buổi
- **Buổi:** 06 / 6
- **Loại:** Capstone
- **Agent xây dựng:** không tạo agent mới. Nâng cấp Orchestrator (buổi 1) để nó điều phối cả 5 agent: Document, Data Analysis, Report, Deep Research chạy một quy trình end-to-end.
- **Thời lượng:** 150 phút
- **Chuẩn bị trước của GV:**
  - Máy đã dựng sẵn đủ 5 agent từ buổi 1-5, đã dán system prompt nâng cấp Orchestrator (file `system-prompts/06-multi-agent-workflow.md`).
  - 1 bộ dữ liệu demo end-to-end đầy đủ: 1 chủ đề để nghiên cứu, 1 tài liệu nội bộ (PDF/Word), 1 file Excel số liệu, để chạy full dây chuyền trước lớp.
  - Slide sơ đồ dây chuyền (bản đồ 6 buổi + luồng gọi agent).
  - Bản mềm giấy chứng nhận / thư định hướng học tiếp để trao cuối buổi.
  - Máy dự phòng đã lưu sẵn output từng bước, phòng khi chạy live bị chậm hoặc lỗi mạng.

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu và giải thích được multi-agent là gì: một Orchestrator điều phối nhiều agent chuyên môn chạy nối tiếp nhau, kết quả bước trước là đầu vào bước sau.
2. Nâng cấp được Orchestrator của mình để nó ra kế hoạch nhiều bước và điều phối cả 5 agent.
3. Tự thiết kế và chạy được 1 quy trình công việc thật của bản thân bằng dây chuyền multi-agent (chạy full-auto nếu công cụ hỗ trợ, hoặc chạy tay có điều phối).
4. Tự rà được mâu thuẫn số liệu giữa các bước và biết cách sửa khi 1 agent ra kết quả sai.
5. Trình bày được capstone: từ nay mỗi việc lặp lại chỉ còn 1 lệnh tổng thay vì làm thủ công nhiều bước.

## Kết quả cầm về (deliverable)
- **1 workflow multi-agent chạy được** giải đúng một quy trình công việc thật của học viên (có kế hoạch các bước + output cuối hoàn chỉnh).
- **1 bài trình bày capstone** (3-5 phút): bài toán của tôi, tôi ghép agent thế nào, kết quả, tiết kiệm được gì.
- **Bộ 6 agent hoàn chỉnh** dùng được ngay cho công việc hằng ngày (Orchestrator nâng cấp + Document + Data + Report + Deep Research).

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Multi-agent = một nhóm làm việc.** Orchestrator là trưởng nhóm, 4 agent kia là nhân viên chuyên môn. Trưởng nhóm nhận việc lớn, chia nhỏ, giao đúng người, rồi gom kết quả lại. Bạn chỉ nói chuyện với trưởng nhóm.
- **Điều phối nhiều bước.** Một yêu cầu lớn được bẻ thành chuỗi bước có thứ tự. Ví dụ: nghiên cứu trước, đọc tài liệu nội bộ, phân tích số liệu, rồi mới viết báo cáo. Sai thứ tự thì bước sau thiếu nguyên liệu.
- **Chuyền kết quả (output bước này thành input bước sau).** Kết quả Deep Research được dán vào cho Report dùng. Đây là "sợi dây" nối các agent. Chuyền sai hoặc chuyền thiếu thì cả dây chuyền lệch.
- **Chạy full-auto và chạy tay có điều phối.** Nếu công cụ cho agent tự gọi agent, ta bấm 1 lệnh là chạy hết. Nếu không, Orchestrator ra kế hoạch, học viên tự copy kết quả giữa các agent theo kế hoạch đó. Cùng một logic, chỉ khác ai bấm nút.
- **Tự rà mâu thuẫn.** Bước cuối, Orchestrator soi lại: số ở báo cáo có khớp số ở phân tích không, có chỗ nào một agent nói một kiểu không. Đây là chốt chặn chất lượng trước khi dùng.

---

## Timeline chi tiết (theo phút)

### [00:00-00:15] Mở đầu & tổng kết cả khóa
- **Lời dẫn:** "Chào cả lớp, đây là buổi cuối. Năm buổi vừa rồi mỗi buổi các bạn dựng 1 người: agent đọc tài liệu, agent phân tích số liệu, agent viết báo cáo, agent nghiên cứu. Hôm nay không thêm người mới nữa. Hôm nay chúng ta cho cả 5 người này làm việc chung trong 1 dây chuyền, và các bạn sẽ dùng chính công việc thật của mình để nghiệm thu."
- Điểm danh nhanh.
- Chiếu lại bản đồ 6 buổi (từ `00-tong-quan-khoa-hoc.md`): 5 agent đã có, buổi 6 là chỗ ghép dây chuyền.
- Hỏi nhanh 2-3 học viên: "Agent nào bạn dùng nhiều nhất sau các buổi qua?" để kích hoạt lại trí nhớ.
- Nêu mục tiêu buổi: ghép dây chuyền + làm capstone + trình bày + nhận chứng nhận.

### [00:15-00:35] Lý thuyết: ghép multi-agent + sơ đồ dây chuyền
- Giải thích 5 khái niệm cốt lõi ở trên, đi kèm sơ đồ dây chuyền chiếu lên màn hình:

```
Yêu cầu tổng (1 câu): "Làm báo cáo đánh giá thị trường X + đề xuất cho sếp"
        │
   [1] Deep Research Agent  → nghiên cứu thị trường X, đối thủ
        │  (đầu ra: phát hiện chính + số liệu)
        ▼
   [2] Document Agent       → đọc tài liệu nội bộ tôi đưa, trích ý liên quan
        │  (đầu ra: tóm tắt tài liệu nội bộ)
        ▼
   [3] Data Analysis Agent  → phân tích file số liệu bán hàng của tôi
        │  (đầu ra: xu hướng + biểu đồ đề xuất)
        ▼
   [4] Report Agent         → gộp [1][2][3] thành báo cáo + đề xuất
        │
        ▼
   Orchestrator             → rà soát tổng thể, kiểm mâu thuẫn, xuất bản cuối
```

- Nhấn 3 điểm:
  1. Orchestrator ra **kế hoạch trước, chạy sau**. Luôn cho học viên duyệt kế hoạch, đừng để nó tự chạy một mạch rồi mới xem.
  2. Thứ tự các bước **tùy bài toán**, không cứng. Có bài Research trước, có bài Data trước.
  3. Bước cuối luôn có **rà mâu thuẫn** trước khi lấy kết quả đi dùng.
- **Câu hỏi tương tác:** "Với công việc của bạn, nếu chỉ được ghép 3 agent thôi thì bạn ghép agent nào, theo thứ tự nào?" Gọi 2-3 người trả lời, GV vẽ nhanh lên bảng.

### [00:35-01:05] Demo GV: chạy 1 quy trình end-to-end mẫu
- GV chạy trực tiếp 1 dây chuyền hoàn chỉnh trước lớp (script chi tiết ở mục "Script demo" bên dưới).
- **Điểm nhấn phải chỉ rõ:**
  - Chỉ ra chỗ dán system prompt nâng cấp vào Orchestrator (đè bản buổi 1).
  - Cho lớp thấy Orchestrator **ra kế hoạch các bước** trước, GV đọc to kế hoạch, "duyệt" rồi mới chạy.
  - Chỉ rõ động tác **chuyền kết quả**: copy đầu ra bước 1 làm đầu vào bước 2 (nếu chạy tay), hoặc chỉ ra chỗ công cụ tự chuyền (nếu full-auto).
  - Cố ý dừng ở bước rà mâu thuẫn: cho lớp thấy Orchestrator soi số liệu, phát hiện 1 chỗ lệch (GV chuẩn bị sẵn tình huống này), rồi sửa.
- Nếu công cụ CES cấp hỗ trợ agent gọi agent tự động: demo bản full-auto trước, sau đó nói rõ "nếu công cụ của bạn không có tính năng này, ta làm cách chạy tay, kết quả như nhau".

### [01:05-01:15] Nghỉ giải lao
- 10 phút. GV nhắc học viên mở sẵn bộ file công việc thật của mình để vào capstone ngay.

### [01:15-02:05] Capstone: học viên tự dựng quy trình công việc của mình
- **Đề bài:** mỗi học viên chọn 1 quy trình công việc THẬT của mình, nhiều bước, hay phải làm lặp lại. Dựng dây chuyền multi-agent giải nó.
- Các bước học viên làm (bám workbook):
  1. Viết ra bằng lời quy trình đang làm thủ công (bước 1, 2, 3...).
  2. Với mỗi bước, chọn agent phù hợp, ghi rõ đầu vào cần gì, đầu ra mong đợi gì.
  3. Dán system prompt nâng cấp vào Orchestrator, điền phần bối cảnh của mình.
  4. Giao yêu cầu tổng, để Orchestrator ra kế hoạch, duyệt kế hoạch.
  5. Chạy dây chuyền (full-auto hoặc chạy tay chuyền kết quả).
  6. Rà mâu thuẫn ở bước cuối, sửa, ra output hoàn chỉnh.
- **GV đi vòng hỗ trợ.** Ưu tiên: (a) chặn học viên chọn bài quá to không xong trong buổi, (b) sửa thứ tự bước sai, (c) xử lý chỗ chuyền kết quả bị đứt.
- Mốc kiểm: đến khoảng 01:45 mỗi học viên phải đã có kế hoạch các bước + chạy được ít nhất tới bước 2-3. GV nhắc mốc để kịp giờ trình bày.

### [02:05-02:30] Trình bày capstone + nhận xét + trao chứng nhận
- Mỗi học viên trình bày 3-5 phút (tùy sĩ số, GV chia thời gian). Nội dung: bài toán của tôi, ghép agent thế nào, kết quả, tiết kiệm được bao nhiêu công so với làm tay.
- GV nhận xét ngắn từng bài: 1 điểm mạnh + 1 điểm cải thiện.
- **Chốt giá trị cả khóa:** "Trước khóa, mỗi việc này các bạn làm tay qua nhiều bước, mỗi lần lại từ đầu. Sau khóa, các bạn có 1 lệnh tổng chạy cả dây chuyền. Đây là thứ các bạn giữ lại và tái sử dụng mãi."
- Trao chứng nhận hoàn thành (đạt tối thiểu 5/6 buổi + capstone) và phần "học gì tiếp theo".
- **Lời dẫn kết khóa:** "Bộ 6 agent này là tài sản của các bạn. Đừng để nó nằm im. Tuần tới, mỗi lần sắp làm một việc lặp lại, tự hỏi: việc này giao cho agent nào được không. Đó là lúc khóa học thật sự bắt đầu có giá trị."

---

## Script demo (các bước GV thao tác)
1. Mở Orchestrator đã dựng từ buổi 1. Vào phần Instructions / System prompt.
2. Dán đè toàn bộ system prompt nâng cấp (khối trong `system-prompts/06-multi-agent-workflow.md`), điền phần [Họ tên] và bối cảnh mẫu. Lưu.
3. Gõ yêu cầu tổng, ví dụ: "Làm cho tôi báo cáo đánh giá thị trường [X] kèm đề xuất cho sếp. Tôi có 1 tài liệu nội bộ và 1 file số liệu bán hàng sẽ đưa khi cần."
4. Orchestrator trả về **kế hoạch các bước**. GV đọc to, chỉ cho lớp thấy: bước nào giao agent nào, đầu ra mong đợi mỗi bước. GV "duyệt".
5. Chạy bước 1 (Deep Research): lấy phát hiện chính + số liệu. Copy kết quả ra.
6. Chạy bước 2 (Document): đưa tài liệu nội bộ, lấy tóm tắt. Chỉ rõ đây là "chuyền": kết quả bước 1 + tài liệu là đầu vào cho bước này.
7. Chạy bước 3 (Data Analysis): đưa file Excel, lấy xu hướng + gợi ý biểu đồ.
8. Chạy bước 4 (Report): dán cả kết quả [1][2][3] vào, lấy báo cáo hoàn chỉnh.
9. Quay lại Orchestrator, yêu cầu **rà mâu thuẫn**: "Soi lại toàn bộ, số liệu giữa các bước có khớp không, có chỗ nào mâu thuẫn hay thiếu." GV cho lớp thấy nó bắt được 1 chỗ lệch (đã cài sẵn), sửa, xuất bản cuối.
10. Nếu công cụ hỗ trợ full-auto: làm lại nhanh bản 1 lệnh, cho lớp thấy cùng ra kết quả nhưng đỡ thao tác tay.

## System prompt dùng trong buổi
- Xem `system-prompts/06-multi-agent-workflow.md` (system prompt nâng cấp Orchestrator + sơ đồ dây chuyền).
- Tham chiếu bản gốc buổi 1: `system-prompts/01-orchestrator-agent.md`.

## Câu hỏi tương tác gợi ý
- "Việc nào trong tuần bạn phải làm đi làm lại qua nhiều bước nhất? Đó chính là ứng viên số 1 cho capstone."
- "Nếu Deep Research ra một số liệu, mà Data Analysis ra số khác, bạn tin số nào? Vì sao?"
- "Trong dây chuyền của bạn, bước nào nếu sai sẽ kéo hỏng nhiều bước sau nhất?"
- "Bạn muốn output cuối cùng ra dạng gì: báo cáo, email, hay slide?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Số liệu mâu thuẫn giữa các bước (Research nói số A, Data nói số B) | Dừng lại, không xuất bản. Yêu cầu Orchestrator chỉ rõ hai số đến từ nguồn nào. Ưu tiên số từ dữ liệu thật của học viên (file Excel) hơn số nghiên cứu ngoài. Nếu vẫn không rõ, ghi chú "cần kiểm tra lại" thay vì chọn bừa. |
| 1 agent ra kết quả sai kéo theo các bước sau sai | Không sửa ở bước cuối. Quay lại đúng bước bị sai, sửa đầu vào hoặc yêu cầu làm lại bước đó, rồi chạy lại các bước từ đó xuống. Nhắc lớp: dây chuyền lỗi ở gốc thì phải vá ở gốc. |
| Học viên chọn bài toán quá to, không xong trong buổi | Cắt nhỏ ngay tại lớp. Chọn 1 lát cắt gọn (ví dụ chỉ 1 tuần, 1 sản phẩm) để chạy trọn dây chuyền, phần còn lại làm ở nhà. Thà chạy hết 1 bài nhỏ còn hơn dở dang 1 bài to. |
| Công cụ không hỗ trợ agent tự gọi agent | Chuyển sang chạy tay có điều phối: Orchestrator ra kế hoạch, học viên copy kết quả bước trước dán sang agent bước sau theo đúng kế hoạch. Kết quả như nhau, chỉ thêm thao tác tay. |
| Orchestrator tự chạy hết không cho duyệt kế hoạch | Nhắc học viên thêm câu "cho tôi xem kế hoạch trước khi chạy" vào yêu cầu, hoặc kiểm tra lại đã dán đúng system prompt nâng cấp chưa (bản này bắt buộc trình kế hoạch trước). |
| Chuyền kết quả bị thiếu, bước sau hỏi lại thông tin đã có | Kiểm tra học viên đã copy đủ đầu ra bước trước chưa. Dạy thói quen: copy nguyên khối kết quả, không copy nửa chừng. |
| Chạy live bị chậm/lỗi mạng lúc demo | GV dùng máy dự phòng đã lưu sẵn output từng bước, chiếu lên giải thích tiếp, không để lớp chờ. |

## Bài tập
- **Tại lớp:** hoàn thành 1 workflow multi-agent giải quy trình công việc thật của mình + trình bày capstone 3-5 phút.
- **Về nhà (sau khóa):**
  - Chạy lại dây chuyền capstone với dữ liệu thật đầy đủ của tuần tới.
  - Dựng thêm 1 dây chuyền thứ 2 cho một việc lặp lại khác.
  - Lưu lại system prompt + kế hoạch các bước thành 1 file "quy trình chuẩn" để tái dùng.

## Tiêu chí hoàn thành capstone
- [ ] Chọn được 1 quy trình công việc thật, nhiều bước, hay lặp lại.
- [ ] Có kế hoạch các bước rõ ràng: bước nào, agent nào, đầu vào, đầu ra.
- [ ] Ghép và chạy được dây chuyền (full-auto hoặc chạy tay có điều phối) ra output cuối hoàn chỉnh.
- [ ] Đã rà mâu thuẫn ở bước cuối và xử lý được nếu có.
- [ ] Trình bày được: bài toán, cách ghép agent, kết quả, công tiết kiệm.

## Tiêu chí hoàn thành KHÓA
- [ ] Tham dự tối thiểu 5/6 buổi.
- [ ] Sở hữu đủ 6 agent dùng được: Orchestrator (nâng cấp) + Document + Data Analysis + Report + Deep Research + hệ Multi-Agent ghép nối.
- [ ] Có bộ system prompt chuẩn cho từng agent, copy dùng lại được.
- [ ] Hoàn thành và trình bày 1 capstone áp dụng vào công việc thật.
- [ ] Đạt điều kiện nhận chứng nhận hoàn thành của CES.

## Học gì tiếp theo sau khóa
- **Đào sâu từng agent.** Tinh chỉnh system prompt cho khớp hơn với đặc thù công việc, thêm ví dụ mẫu để agent bắt chước văn phong của bạn.
- **Mở rộng dây chuyền.** Thêm bước, thêm nhánh, ghép nhiều dây chuyền cho nhiều loại việc khác nhau.
- **Chuẩn hóa cho cả phòng/nhóm.** Chia sẻ agent và system prompt cho đồng nghiệp, để cả nhóm dùng chung 1 quy trình.
- **Tự động hóa sâu hơn.** Với ai muốn đi xa hơn: tìm hiểu cách nối agent với công cụ khác (tự lấy dữ liệu, tự gửi email, tự lên lịch). CES có các khóa nâng cao và workshop chuyên đề cho hướng này.
- **Giữ nhịp thực hành.** Mỗi tuần chọn 1 việc lặp lại mới để đóng gói thành agent. Kỹ năng này chỉ mạnh lên khi dùng đều.
