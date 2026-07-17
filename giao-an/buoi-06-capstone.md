# Giáo án Buổi 06: Capstone, ghép Skill + MCP + Agent Team thành 1 quy trình thật

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi khối thời gian có đủ 4 thành phần:
> (1) LỜI DẪN GV: câu thoại đọc lên được, (2) PROMPT: câu chính xác gõ vào Claude Code,
> (3) FILE DEMO: đường dẫn file trong `tai-lieu-phat/demo/` dùng cho prompt đó,
> (4) KẾT QUẢ MONG ĐỢI: mô tả để GV đối chiếu agent chạy đúng chưa.
>
> Buổi này KHÔNG dạy khái niệm mới. Cả buổi ghép tất cả 5 khái niệm đã học vào một quy trình
> công việc thật, chạy đầu-cuối bằng một lệnh tổng. Phần lớn thời gian để học viên tự dựng và trình bày.

## Thông tin buổi
- **Buổi:** 06 / 6 (buổi cuối, chốt khóa)
- **Khái niệm chính:** ghép Agent + Skill + MCP + Subagent + Agent Team (không thêm khái niệm mới)
- **Loại:** Capstone (tổng hợp toàn khóa)
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đăng nhập tài khoản CES cấp
- [ ] Mở sẵn thư mục dùng lại từ buổi 5: `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/` (3 thư mục con `thi-truong/`, `doi-thu/`, `so-lieu/`)
- [ ] Mở sẵn đề bài: `tai-lieu-phat/demo/buoi-06/de-bai-capstone.md`
- [ ] Kiểm tra 3 thứ đã dựng ở các buổi trước còn nằm trong thư mục dự án:
  - Skill tóm tắt tài liệu: `.claude/skills/tom-tat-tai-lieu/SKILL.md` (buổi 2)
  - MCP đọc file đã cắm và chạy được (buổi 3), test lệnh đọc CSV trước
  - Hai subagent: `.claude/agents/report-agent.md` và `.claude/agents/research-agent.md` (buổi 4)
- [ ] Chạy thử 1 lượt lệnh tổng capstone trước giờ lên lớp, xem ra đủ 5 đầu mục chưa
- [ ] Mở sẵn các mẫu để tra khi cần: `mau-cau-hinh/skill-tom-tat-tai-lieu.md`, `mau-cau-hinh/mcp-cau-hinh-mau.md`, `mau-cau-hinh/agent-report-mau.md`, `mau-cau-hinh/agent-team-mau.md`
- [ ] Chuẩn bị chứng nhận (bản in hoặc bản số) để trao cuối buổi cho học viên đạt
- [ ] Nhắc học viên từ buổi trước: hôm nay mang sẵn 1 quy trình công việc thật của mình, nhiều bước, kèm file dữ liệu

## Mục tiêu buổi (học xong học viên làm được gì)
1. Nhìn được bức tranh tổng: 5 khái niệm ghép lại thành một dây chuyền công việc.
2. Chạy được một quy trình thật đầu-cuối bằng một lệnh tổng (lead điều phối team + skill + MCP + report agent).
3. Tự thiết kế quy trình công việc lặp lại của chính mình dưới dạng dây chuyền agent.
4. Xử lý được 3 lỗi hay gặp khi ghép: số liệu mâu thuẫn, một agent sai kéo bước sau sai, quy trình quá tham.
5. Trình bày được: mình dùng agent, skill, MCP, subagent, team ở đâu trong quy trình.

## Kết quả cầm về (deliverable)
- 1 quy trình công việc thật của học viên chạy được đầu-cuối bằng một lệnh tổng.
- Bộ đầu ra đủ 5 đầu mục (với đề mẫu: tóm tắt thị trường, bảng đối thủ, phân tích số liệu, đề xuất kế hoạch, email gửi sếp không emoji).
- 1 phần trình bày ngắn: chỉ ra chỗ nào dùng agent / skill / MCP / subagent / team.
- Chứng nhận hoàn thành khóa (nếu đạt tiêu chí).

## Khái niệm cốt lõi (nhắc lại cho lớp, không dạy mới)
- **Agent (Claude Code):** trợ lý AI tự làm nhiều bước, đọc và sửa file thật, nhớ bối cảnh nhờ CLAUDE.md.
- **Skill:** gói chỉ dẫn cho một việc lặp lại. Claude tự nạp đúng skill khi gặp việc phù hợp. Trong capstone, skill tóm tắt tài liệu lo phần thị trường.
- **MCP:** cổng cắm để agent chạm vào dữ liệu ngoài (ở đây là đọc file CSV số liệu bán hàng).
- **Subagent:** agent con chuyên một việc. Report Agent gộp kết quả thành đề xuất và email ở bước cuối.
- **Agent Team:** một lead chia việc cho nhiều agent chạy song song, mỗi agent một thư mục con, xong lead ghép lại.
- **Ý chốt khóa:** mỗi việc lặp lại trước đây làm thủ công nhiều bước, giờ gói thành MỘT lệnh tổng. Đó là giá trị lớn nhất của cả khóa.

---

## Timeline chi tiết (theo phút)

Buổi capstone dồn thời gian cho học viên dựng và trình bày. Demo GV chỉ làm mẫu một lượt full quy trình.

### [00:00-00:15] Mở đầu & tổng kết cả khóa
- **Lời dẫn GV:** "Chào cả lớp, đây là buổi cuối. Năm buổi qua ta đi từng viên gạch: buổi 1 làm quen agent, buổi 2 đóng gói skill, buổi 3 cắm MCP, buổi 4 tạo subagent, buổi 5 điều khiển agent team. Hôm nay ta không học thêm gì mới. Hôm nay ta ghép tất cả lại thành một dây chuyền, và biến một việc thật thành một lệnh duy nhất."
- Điểm danh, kiểm tra ai còn giữ đủ trong thư mục dự án: skill tóm tắt, MCP đã cắm, 2 subagent.
- Chiếu lại bản đồ 5 khái niệm và nói mỗi khái niệm sẽ đứng ở đâu trong dây chuyền capstone.
- Nêu nhịp buổi: xem GV chạy mẫu một lượt, rồi cả lớp tự dựng quy trình của mình, cuối buổi lên trình bày và nhận chứng nhận.
- **Câu hỏi tương tác:** "Trước khóa, một việc như làm bộ tài liệu ra mắt sản phẩm cả lớp mất bao lâu và qua mấy bước thủ công? Giữ con số đó trong đầu, cuối buổi ta so lại."

### [00:15-00:35] Lý thuyết ngắn: ghép end-to-end + sơ đồ dây chuyền
- **Lời dẫn GV:** "Ghép 5 thứ nghe phức tạp, nhưng thật ra chỉ là xếp chúng thành một dây chuyền: ai làm gì, dùng công cụ nào, đầu ra của người này là đầu vào của người kia."
- **Nội dung 1: Mỗi khái niệm đứng ở một vị trí trong dây chuyền.**
  - Lead (bạn qua Claude Code): nhận lệnh tổng, chia việc, kiểm số liệu, chốt.
  - Agent team: 3 agent chạy song song, mỗi agent một thư mục con.
  - Skill: agent thị trường gọi skill tóm tắt tài liệu để làm phần bối cảnh.
  - MCP: agent số liệu dùng MCP đọc file CSV, tính tổng và xu hướng.
  - Subagent Report: nhận 3 kết quả trên, viết đề xuất kế hoạch và email gửi sếp.
- **Nội dung 2: Đầu ra bước trước là đầu vào bước sau.** Nhấn: 3 agent song song làm 3 phần độc lập, nhưng bước cuối (đề xuất + email) PHẢI đợi cả 3 xong vì nó tổng hợp. Đây là chỗ phân biệt việc chạy song song và việc chạy tuần tự.
- **Nội dung 3: Một lệnh tổng thay nhiều bước thủ công.** Trước đây mở từng file, đọc, ghi ra giấy, gõ lại thành báo cáo, soạn email. Giờ mô tả một lần trong một lệnh, dây chuyền tự chạy.
- **Sơ đồ dây chuyền (vẽ lên bảng hoặc chiếu):**
  ```
                     LỆNH TỔNG của bạn
                            │
                     LEAD (Claude Code)
              chia việc + phân vùng thư mục
        ┌───────────────────┼───────────────────┐
        ▼                   ▼                   ▼
   Agent Thị trường    Agent Đối thủ      Agent Số liệu
   đọc thi-truong/     đọc doi-thu/       đọc so-lieu/
   + SKILL tóm tắt     lập bảng so sánh   + MCP đọc CSV
        │                   │                   │
        └───────────────────┼───────────────────┘
                            ▼
                  LEAD kiểm số liệu khớp
                            ▼
                REPORT AGENT (subagent)
        gộp 3 phần -> đề xuất kế hoạch + email sếp
                            ▼
              5 ĐẦU MỤC hoàn chỉnh, sẵn dùng
  ```
- **Câu hỏi tương tác:** "Trong sơ đồ này, chỗ nào bắt buộc làm tuần tự, không thể song song? Vì sao?"

### [00:35-01:05] Demo giảng viên: chạy full quy trình bằng một lệnh tổng
> GV chạy mẫu một lượt trên màn hình chia sẻ. Học viên xem, chưa gõ theo. Trình bày theo mẫu 4 dòng.

**Bước 1: Kiểm tra dây chuyền đã sẵn sàng (skill + MCP + 2 subagent)**
- **Lời dẫn GV:** "Trước khi chạy lệnh tổng, tôi kiểm nhanh mấy thứ đã dựng các buổi trước còn dùng được không. Giống thợ kiểm đồ nghề trước khi vào việc."
- **Prompt gõ vào Claude Code:**
  ```
  Liệt kê giúp tôi: các skill đang có trong thư mục này, các subagent đã định nghĩa, và xác nhận MCP đọc file đang chạy được. Rồi đọc thử file so-lieu/so-lieu-ban-hang.csv và cho tôi biết có mấy dòng dữ liệu.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/so-lieu/so-lieu-ban-hang.csv`; tham chiếu skill và subagent đã dựng ở buổi 2 và buổi 4.
- **Kết quả mong đợi:** Agent liệt kê skill `tom-tat-tai-lieu`, hai subagent `report-agent` và `research-agent`, xác nhận đọc được CSV và báo có 6 dòng dữ liệu (3 tháng, mỗi tháng 2 gói sản phẩm). Nếu thiếu thứ nào, dựng lại nhanh từ mẫu tương ứng trước khi đi tiếp.

**Bước 2: Chạy LỆNH TỔNG capstone (lead điều phối team + skill + MCP + report agent)**
- **Lời dẫn GV:** "Đây là khoảnh khắc chính của cả khóa. Chỉ một lệnh, tôi mô tả toàn bộ dây chuyền, rồi để lead tự chia việc cho team và ghép lại. Cả lớp để ý: tôi không dắt từng bước, tôi giao cả quy trình."
- **Prompt gõ vào Claude Code:**
  ```
  Tôi cần một bộ tài liệu ra mắt sản phẩm "Gói Cao cấp Plus" hoàn chỉnh. Dữ liệu nằm trong thư mục du-an-ra-mat-san-pham/ gồm 3 thư mục con: thi-truong/, doi-thu/, so-lieu/.

  Hãy điều phối một agent team chạy SONG SONG, mỗi agent chỉ đọc thư mục của mình:
  - Agent 1: đọc thi-truong/, dùng skill tóm tắt tài liệu để ra bản tóm tắt bối cảnh thị trường và cơ hội.
  - Agent 2: đọc doi-thu/, lập bảng so sánh đối thủ và nêu điểm khác biệt của sản phẩm.
  - Agent 3: đọc so-lieu/, dùng MCP đọc file CSV để phân tích doanh thu, số đơn và xu hướng theo tháng.

  Sau khi cả ba xong, kiểm tra số liệu giữa các phần có khớp nhau không, rồi giao cho report-agent gộp thành:
  4. Một đề xuất kế hoạch ra mắt: thông điệp chính, giá đề xuất, kênh bán, dựa trên 3 phần trên.
  5. Một email ngắn gửi sếp trình bày tóm tắt kế hoạch, văn phong công sở, KHÔNG dùng emoji.

  Xuất ra đủ 5 đầu mục, đánh số rõ ràng.
  ```
- **File demo:** cả thư mục `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/` (`thi-truong/boi-canh-thi-truong.md`, `doi-thu/doi-thu-canh-tranh.md`, `so-lieu/so-lieu-ban-hang.csv`); đề bài `tai-lieu-phat/demo/buoi-06/de-bai-capstone.md`.
- **Kết quả mong đợi:** Agent chạy dây chuyền và trả về đủ 5 đầu mục:
  1. **Tóm tắt thị trường:** doanh nghiệp nhỏ chuyển từ Excel sang phần mềm; khách cần dễ dùng, giá hợp lý, hỗ trợ nhanh, xem báo cáo trên điện thoại; cơ hội nằm ở tính năng điện thoại và cam kết chuyển dữ liệu miễn phí.
  2. **Bảng đối thủ:** A (giá rẻ, khoảng 30 triệu/năm, ít tính năng), B (tầm trung 80-100 triệu, giao diện cũ), C (cao cấp trên 200 triệu, đắt và thừa tính năng). Khoảng trống: gói tầm trung, dễ dùng, có bản điện thoại tốt, hỗ trợ chuyển dữ liệu.
  3. **Phân tích số liệu:** tổng doanh thu 3 tháng khoảng 2.870 triệu; gói Cao cấp tăng đều từ 480 lên 640 triệu (đơn từ 48 lên 64), tăng nhanh hơn gói Tiêu chuẩn; xu hướng nghiêng về gói cao cấp.
  4. **Đề xuất kế hoạch:** định vị tầm trung dễ dùng, thông điệp xoay quanh xem báo cáo trên điện thoại + chuyển dữ liệu miễn phí, giá đặt giữa đối thủ B và C, kênh bán phù hợp doanh nghiệp nhỏ.
  5. **Email gửi sếp:** ngắn gọn, có tiêu đề, tóm tắt 4 phần trên, đề xuất bước tiếp theo, KHÔNG có emoji.
  GV nhấn cho lớp: số liệu ở đề xuất và email phải khớp với phần phân tích (mục 3), không được lệch.

**Bước 3: Kiểm số liệu khớp và soi email không emoji**
- **Lời dẫn GV:** "Chạy xong chưa phải là xong. Lead luôn kiểm lại: con số ở email có đúng con số ở phần phân tích không, email có lỡ dính emoji không. Đây là bước một người làm nghiêm túc luôn phải làm."
- **Prompt gõ vào Claude Code:**
  ```
  Đối chiếu giúp tôi: các con số doanh thu và số đơn trong đề xuất và email có khớp với phần phân tích số liệu không? Nếu lệch, chỉ ra chỗ lệch. Đồng thời rà email xem có ký tự emoji nào không, nếu có thì bỏ hết.
  ```
- **File demo:** dùng chính đầu ra ở Bước 2 (không cần file mới).
- **Kết quả mong đợi:** Agent xác nhận số liệu ở mục 4 và mục 5 khớp với mục 3, hoặc chỉ ra và sửa chỗ lệch. Email được xác nhận không có emoji. GV chốt: đây là quy trình một lệnh thay cho cả buổi làm thủ công.

### [01:05-01:15] Nghỉ giải lao
- GV nhắc: ai chưa chọn được quy trình công việc thật của mình thì tranh thủ giờ nghỉ nghĩ ra một việc lặp lại nhiều bước, hỏi trợ giảng nếu bí. Sau nghỉ cả lớp bắt tay dựng capstone của riêng mình.

### [01:15-02:05] Học viên tự dựng CAPSTONE (quy trình công việc của mình)
- **Lời dẫn GV:** "Giờ là phần quan trọng nhất của buổi và của cả khóa: cả lớp dựng dây chuyền cho một việc THẬT của mình. Ai chưa có ý tưởng, cứ chạy lại đề mẫu ra mắt sản phẩm cũng được, nhưng khuyến khích thử việc của chính mình vì đó là thứ cầm về dùng ngay."
- **Đề bài:** Mỗi học viên chọn một quy trình công việc lặp lại nhiều bước của mình, rồi dựng thành dây chuyền agent chạy bằng một lệnh tổng. Bốn bước:
  1. Vẽ dây chuyền: liệt kê các bước, mỗi bước do agent nào làm, dùng skill hay MCP gì, đầu vào và đầu ra là gì (dùng bảng thiết kế trong workbook).
  2. Bỏ file công việc thật vào các thư mục con tương ứng.
  3. Viết một lệnh tổng mô tả toàn bộ dây chuyền (theo mẫu lệnh tổng ở dưới).
  4. Chạy, kiểm số liệu, soi văn bản gửi đi (không emoji), chỉnh cho tới khi ra đủ đầu mục mình cần.
- **Prompt gợi ý (khung lệnh tổng để học viên điền vào):**
  ```
  Tôi cần [tên bộ kết quả cuối, ví dụ: bộ tài liệu chốt đơn / báo cáo tuần / hồ sơ chào giá]. Dữ liệu nằm trong thư mục [tên thư mục] gồm các thư mục con: [liệt kê].

  Hãy điều phối agent team chạy SONG SONG, mỗi agent chỉ đọc thư mục của mình:
  - Agent 1: đọc [thư mục], [việc cần làm], dùng skill [tên skill nếu có].
  - Agent 2: đọc [thư mục], [việc cần làm].
  - Agent 3: đọc [thư mục], [việc cần làm], dùng MCP đọc file [tên file dữ liệu].

  Sau khi cả ba xong, kiểm số liệu khớp nhau, rồi giao cho report-agent gộp thành:
  - [Đầu mục 4, ví dụ: một đề xuất / kế hoạch].
  - [Đầu mục 5, ví dụ: một email hoặc báo cáo gửi cấp trên, văn phong công sở, KHÔNG emoji].

  Xuất đủ các đầu mục, đánh số rõ ràng.
  ```
- **File demo:** dùng dữ liệu công việc thật của học viên; ai chưa mang thì dùng lại `tai-lieu-phat/demo/buoi-05/du-an-ra-mat-san-pham/` và đề bài `tai-lieu-phat/demo/buoi-06/de-bai-capstone.md`.
- **Kết quả mong đợi:** Mỗi học viên có một quy trình chạy được đầu-cuối bằng một lệnh, ra bộ kết quả đủ các đầu mục mình định nghĩa, số liệu nhất quán, văn bản gửi đi không emoji. GV và trợ giảng đi từng bàn: kiểm dây chuyền có bị "tham" quá không, có phân vùng thư mục rõ không, số liệu có khớp không.

### [02:05-02:30] Học viên trình bày + GV nhận xét + trao chứng nhận + định hướng học tiếp
- **Lời dẫn GV:** "Vòng cuối: một vài bạn lên trình bày nhanh 2 phút. Không cần đẹp, chỉ cần chỉ rõ: quy trình của bạn là gì, agent nào làm gì, bạn dùng skill ở đâu, MCP ở đâu, team ở đâu, và bộ kết quả cuối trông thế nào."
- **Cách chạy phần trình bày:** gọi 4-6 học viên (hoặc theo nhóm nghề). Mỗi người 2 phút, GV nhận xét 1 phút, tập trung khen chỗ ghép đúng và gợi ý một điểm cải thiện.
- **Khung cho học viên trình bày (chiếu lên để cả lớp bám theo):**
  1. Việc thật tôi chọn là gì, trước đây làm thủ công qua mấy bước.
  2. Dây chuyền của tôi: agent nào đọc thư mục nào.
  3. Tôi dùng skill ở đâu, MCP ở đâu, report agent ở đâu.
  4. Bộ kết quả cuối gồm những gì, số liệu có khớp không.
  5. Giờ việc này còn mấy lệnh so với trước.
- **GV nhận xét theo tiêu chí:** chạy được đầu-cuối chưa, có đủ 5 khái niệm chưa, số liệu nhất quán chưa, văn bản gửi đi sạch emoji chưa, học viên có giải thích được mình dùng cái gì ở đâu không.
- **Trao chứng nhận:** GV xác nhận ai đạt tiêu chí hoàn thành khóa (dự tối thiểu 5/6 buổi + có capstone chạy được), trao chứng nhận CES. Nói một câu ghi nhận: cả lớp đã đi từ mở chat gõ câu hỏi đến điều khiển cả một đội agent.
- **Định hướng học tiếp (mục "học gì tiếp theo sau khóa"):**
  - Đào sâu agent team nhiều phiên (lead + teammate ở các phiên riêng, giao tiếp qua tin nhắn) cho việc lớn kéo dài.
  - Cắm thêm MCP theo nghề: Google Drive, cơ sở dữ liệu công ty, công cụ web, khi được cấp quyền.
  - Xây dần một "thư viện skill" cá nhân cho mọi việc lặp lại của mình.
  - Đưa CLAUDE.md và bộ skill vào dùng chung cho cả phòng ban, để cả nhóm cùng một chuẩn.
  - Kênh hỗ trợ sau khóa: nhóm Zalo lớp và LMS VIP để hỏi tiếp khi vướng.
- **Lời chốt khóa:** "Điều lớn nhất cả lớp mang về không phải một công cụ, mà một thói quen: mỗi việc lặp lại, thay vì làm tay nhiều bước, ta gói thành một lệnh. Đó là cách làm việc mới."

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Liệt kê skill, subagent, xác nhận MCP đọc file chạy được; đọc thử so-lieu-ban-hang.csv có mấy dòng. | `demo/buoi-05/.../so-lieu/so-lieu-ban-hang.csv` | Liệt kê skill tóm tắt, 2 subagent, xác nhận đọc CSV 6 dòng |
| 2 | Lệnh tổng: điều phối team 3 agent song song (skill + MCP), report-agent gộp thành đề xuất + email không emoji, ra đủ 5 đầu mục. | cả thư mục `demo/buoi-05/.../du-an-ra-mat-san-pham/` | 5 đầu mục: tóm tắt thị trường, bảng đối thủ, phân tích số liệu, đề xuất, email không emoji |
| 3 | Đối chiếu số liệu trong đề xuất/email có khớp phần phân tích không; rà và bỏ emoji trong email. | đầu ra ở prompt 2 | Số liệu khớp mục 3, email xác nhận sạch emoji |
| 4 | Khung lệnh tổng cho quy trình công việc thật của học viên (điền vào chỗ ngoặc). | dữ liệu thật của học viên | Quy trình riêng chạy đầu-cuối, ra bộ kết quả học viên định nghĩa |

## Câu hỏi tương tác gợi ý
- "Trước khóa, một việc như làm bộ tài liệu ra mắt mất bao lâu và qua mấy bước tay? Cuối buổi so lại còn mấy lệnh."
- "Trong sơ đồ dây chuyền, chỗ nào bắt buộc tuần tự, không thể song song? Vì sao?"
- "Nếu một agent ở giữa ra kết quả sai, chuyện gì xảy ra với bước sau? Làm sao phát hiện sớm?"
- "Quy trình của bạn có đang 'tham' quá không: một lệnh ôm quá nhiều việc? Cắt ở đâu cho gọn?"
- "Bạn dùng skill ở đâu, MCP ở đâu, team ở đâu trong quy trình của mình? Chỉ đúng vị trí."

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Số liệu mâu thuẫn giữa các bước (email ghi khác phần phân tích) | Dặn học viên luôn thêm bước lead kiểm số liệu trước khi chốt (prompt số 3). Bắt agent lấy số liệu từ đúng một nguồn (phần phân tích), không tự tính lại ở bước email. |
| Một agent ra kết quả sai, kéo các bước sau sai theo | Chạy từng agent tách ra kiểm trước khi ghép: "Chỉ chạy Agent 3 phân tích số liệu, cho tôi xem kết quả." Sửa đúng phần đó rồi mới chạy lại dây chuyền. Nhấn: bước cuối chỉ đáng tin khi từng phần đã đúng. |
| Quy trình quá tham, một lệnh ôm quá nhiều việc, agent làm rối hoặc bỏ sót | Cắt nhỏ: tách thành 2-3 lệnh, mỗi lệnh một cụm việc, rồi ghép kết quả. Hoặc giảm số agent song song xuống còn 2. Quy tắc: dây chuyền vừa đủ, không nhồi. |
| Học viên chưa mang dữ liệu công việc thật | Cho dùng lại thư mục demo buổi 5 và đề bài capstone; dặn về nhà chạy lại với dữ liệu thật của mình. |
| Skill hoặc subagent buổi trước bị mất khỏi thư mục dự án | Dựng lại nhanh từ mẫu: `mau-cau-hinh/skill-tom-tat-tai-lieu.md`, `mau-cau-hinh/agent-report-mau.md`, `mau-cau-hinh/agent-research-mau.md`. |
| MCP đọc file chưa chạy được | Kiểm lại kết nối theo `mau-cau-hinh/mcp-cau-hinh-mau.md`; nếu không kịp sửa, tạm cho agent đọc CSV trực tiếp để không kẹt cả dây chuyền, ghi chú sửa MCP sau. |
| Email đầu ra dính emoji | Chạy prompt số 3 để rà và bỏ; nhắc học viên đưa quy tắc "văn bản gửi đi không emoji" vào CLAUDE.md để lần sau agent tự tuân. |
| Agent chạy song song nhưng hai agent ghi đè file của nhau | Nhắc lại nguyên tắc phân vùng: mỗi agent chỉ đọc/ghi thư mục con của mình. Sửa lệnh cho ghi rõ ranh giới thư mục từng agent. |

## Bài tập
- **Tại lớp:** Dựng và chạy được một quy trình capstone đầu-cuối bằng một lệnh tổng, ra đủ các đầu mục đã định nghĩa, số liệu khớp, văn bản gửi đi không emoji; trình bày được mình dùng agent/skill/MCP/subagent/team ở đâu.
- **Về nhà:** Chạy lại capstone với dữ liệu công việc thật của mình (nếu tại lớp mới dùng đề mẫu); tinh chỉnh lệnh tổng cho gọn; lưu lại lệnh tổng thành ghi chú để tái sử dụng hằng tuần; chụp màn hình bộ kết quả gửi Zalo lớp.

## Tiêu chí hoàn thành CAPSTONE
- [ ] Quy trình chạy được đầu-cuối bằng một lệnh tổng (không phải dắt từng bước)
- [ ] Ra đủ các đầu mục đã định nghĩa (đề mẫu: đủ 5 đầu mục)
- [ ] Có agent team chạy song song, mỗi agent một thư mục
- [ ] Có dùng ít nhất 1 skill và 1 MCP trong dây chuyền
- [ ] Có report agent gộp kết quả thành văn bản hoàn chỉnh
- [ ] Số liệu nhất quán giữa các phần
- [ ] Văn bản gửi đi (email/báo cáo) đúng văn phong, không emoji
- [ ] Học viên chỉ ra được dùng agent / skill / MCP / subagent / team ở đâu

## Tiêu chí hoàn thành KHÓA
- [ ] Dự tối thiểu 5/6 buổi
- [ ] Có Claude Code chạy trên máy + thư mục dự án + CLAUDE.md của riêng mình (buổi 1)
- [ ] Có ít nhất 1 skill tự tạo (buổi 2)
- [ ] Có ít nhất 1 MCP đã cắm và dùng được (buổi 3)
- [ ] Có 2 subagent chuyên trách: Report, Research (buổi 4)
- [ ] Có 1 agent team biết chia việc song song (buổi 5)
- [ ] Có 1 capstone multi-agent chạy đầu-cuối cho một quy trình thật (buổi 6)
- [ ] Trình bày được capstone và nhận chứng nhận CES
