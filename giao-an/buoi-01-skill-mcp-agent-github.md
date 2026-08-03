# Giáo án Buổi 01: Skill, MCP, tạo agent đầu tiên và quản lý Skill bằng GitHub

> Khung chuẩn cho giảng viên. BẮT BUỘC mỗi bước demo/thực hành có đủ 4 thành phần:
> (1) LỜI DẪN GV, (2) PROMPT gõ vào Claude Code, (3) FILE DEMO, (4) KẾT QUẢ MONG ĐỢI.

## Thông tin buổi
- **Buổi:** 01 / 6
- **Khái niệm chính:** Skill, MCP, Agent đầu tiên, GitHub để quản lý skill
- **Loại:** Nền tảng (buổi nền, nhiều nội dung, cần bám sát demo)
- **Thời lượng:** 150 phút

## Chuẩn bị của giảng viên trước buổi
- [ ] Mở sẵn Claude Code trên Claude Desktop, đăng nhập tài khoản CES cấp
- [ ] Tải và mở sẵn thư mục demo: `tai-lieu-phat/demo/buoi-01/`
- [ ] File demo cần dùng: `bien-ban-hop-mau.md`
- [ ] Mẫu cấu hình mở sẵn: `mau-cau-hinh/skill-tom-tat-tai-lieu.md`, `mau-cau-hinh/github-mcp-va-token.md`, `mau-cau-hinh/agent-report-mau.md`
- [ ] Có sẵn 1 tài khoản GitHub để demo tạo repo và lấy token (dùng token riêng của GV, không dùng chung)
- [ ] Test trước cả luồng: tạo skill, cắm GitHub MCP, đẩy skill lên repo, tạo 1 agent
- [ ] Chuẩn bị Zalo lớp gửi link demo và các bước GitHub cho học viên làm nốt ở nhà

## Mục tiêu buổi (học xong học viên làm được gì)
1. Hiểu Skill là gì và cách kích hoạt skill (dùng skill có sẵn, gọi thẳng bằng tên).
2. Tự tạo được một skill đầu tiên (file SKILL.md) và chạy thử.
3. Hiểu MCP là gì và vai trò của nó (cắm công cụ, dữ liệu ngoài cho agent).
4. Tạo được repo GitHub, lấy Personal Access Token an toàn, cắm GitHub MCP.
5. Dùng agent đẩy skill lên GitHub để quản lý (lưu, xem lịch sử, chia sẻ).
6. Tạo được agent đầu tiên (một subagent chuyên trách) và giao việc cho nó.

## Kết quả cầm về (deliverable)
- 1 skill tự tạo (`.claude/skills/tom-tat-tai-lieu/SKILL.md`) chạy được.
- GitHub MCP đã cắm, 1 repo skill trên GitHub có nội dung skill của mình.
- 1 agent đầu tiên tự tạo, giao được việc.

## Khái niệm cốt lõi (giải thích cho lớp, ngôn ngữ thường)
- **Claude Code:** một trợ lý AI dạng agent chạy trong Claude Desktop. Nó tự làm nhiều bước, đọc và sửa file thật trong thư mục bạn chọn.
- **Skill:** một gói chỉ dẫn cho một việc lặp lại. Claude tự nạp đúng skill khi gặp việc phù hợp (nhờ dòng mô tả), hoặc bạn gọi thẳng bằng tên. Mỗi skill là một thư mục chứa file `SKILL.md`.
- **Kích hoạt skill:** hai cách. Một là để Claude tự nhận ra và dùng (nhờ description viết rõ "dùng khi nào"). Hai là gọi tên skill trực tiếp trong lệnh.
- **MCP:** cổng cắm chuẩn để agent dùng công cụ và dữ liệu ngoài: GitHub, file, web, Google Drive. Hôm nay ta cắm MCP GitHub để agent thao tác kho lưu skill thay mình.
- **GitHub:** nơi lưu file trên mạng, có lịch sử thay đổi, chia sẻ được. Ta dùng để cất và quản lý skill.
- **Token (Personal Access Token):** chuỗi ký tự thay mật khẩu, cấp cho agent quyền dùng GitHub trong giới hạn. Phải giữ bí mật như mật khẩu.
- **Agent (subagent):** một agent con chuyên một việc, có vai trò và công cụ riêng do bạn định nghĩa trong `.claude/agents/`.

---

## Timeline chi tiết (theo phút)

### [00:00-00:12] Mở đầu & làm quen Claude Code
- **Lời dẫn GV:** "Chào cả lớp. Đây là buổi nền của khóa. Hôm nay hơi nhiều nội dung nhưng đều là những viên gạch quan trọng nhất: ta sẽ biết skill là gì và tự tạo skill, biết MCP là gì, đưa skill lên GitHub để quản lý, và tạo agent đầu tiên. Cứ bám theo tôi từng bước, chỗ nào chưa kịp ghi lại làm nốt ở nhà."
- Điểm danh, kiểm tra ai đã cài Claude Desktop và đăng nhập được. Ai chưa, trợ giảng hỗ trợ ngay.
- Mở Claude Code, trỏ vào thư mục dự án demo. Nhấn: agent chỉ làm việc trong thư mục ta chọn.
- Giới thiệu bản đồ khóa: hôm nay là buổi nền (skill + MCP + agent + GitHub), các buổi sau đào sâu và ghép thành đội agent.
- **Câu hỏi tương tác:** "Có việc gì cả lớp làm đi làm lại mỗi tuần không? Ghi lại, lát ta biến nó thành skill."

### [00:12-00:32] Skill là gì và cách kích hoạt skill
- **Lời dẫn GV:** "Bắt đầu bằng khái niệm quan trọng nhất hôm nay: skill. Hãy hình dung skill như một tờ hướng dẫn nghề: mỗi khi gặp đúng việc, agent lấy tờ đó ra làm theo, nên lần nào cũng làm đúng chuẩn mà bạn không phải dặn lại."
- **Nội dung 1: Skill là gì.** Một gói chỉ dẫn cho một việc lặp lại, nằm trong thư mục `.claude/skills/<ten>/SKILL.md`. Trong file có phần mô tả (description) nói "dùng khi nào", và phần thân là các bước làm.
- **Nội dung 2: Hai cách kích hoạt skill.**
  1. Tự động: viết description rõ, Claude gặp việc phù hợp là tự nạp skill.
  2. Gọi tên: bạn nói thẳng tên skill trong lệnh, ví dụ "dùng skill tom-tat-tai-lieu cho file này".
- **Nội dung 3: Vì sao skill hơn việc gõ lại chỉ dẫn mỗi lần.** Skill lưu lại, dùng mãi, chia sẻ được, ai trong nhóm cũng làm ra kết quả giống nhau.
- **Câu hỏi tương tác:** "Nếu mỗi lần nhờ AI tóm tắt tài liệu, bạn đều phải dặn lại cách trình bày, thì đóng gói thành skill giúp bạn tiết kiệm điều gì?"

### [00:32-00:57] Demo giảng viên: tạo skill đầu tiên và chạy thử
**Bước 1: Tạo skill tom-tat-tai-lieu**
- **Lời dẫn GV:** "Tôi tạo skill đầu tiên: một skill chuyên tóm tắt tài liệu theo chuẩn. Tôi tả cho agent, nó tạo file SKILL.md đúng chỗ."
- **Prompt gõ vào Claude Code:**
  ```
  Tạo cho tôi một skill tên tom-tat-tai-lieu, đặt tại .claude/skills/tom-tat-tai-lieu/SKILL.md.
  Skill dùng khi cần đọc và tóm tắt một tài liệu dài (biên bản, hợp đồng, báo cáo). Đầu ra gồm: tóm tắt nhanh 3 tới 5 gạch đầu dòng, ý chính chi tiết theo mục, danh sách số liệu và hạn chót, điểm cần lưu ý. Quy tắc: chỉ dùng thông tin có trong tài liệu, không có thì ghi "tài liệu không đề cập", không suy đoán.
  ```
- **File demo:** tham chiếu `mau-cau-hinh/skill-tom-tat-tai-lieu.md`; tạo mới `.claude/skills/tom-tat-tai-lieu/SKILL.md`
- **Kết quả mong đợi:** Agent tạo đúng file `.claude/skills/tom-tat-tai-lieu/SKILL.md` có phần đầu gồm name và description, phần thân là các bước tóm tắt. GV mở file cho lớp xem cấu trúc.

**Bước 2: Kích hoạt skill để tóm tắt biên bản họp**
- **Lời dẫn GV:** "Giờ tôi thử skill trên một biên bản họp thật. Tôi gọi thẳng tên skill cho chắc."
- **Prompt gõ vào Claude Code:**
  ```
  Dùng skill tom-tat-tai-lieu để tóm tắt file bien-ban-hop-mau.md giúp tôi.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- **Kết quả mong đợi:** Agent trả về đúng cấu trúc skill: tóm tắt nhanh (doanh thu 1.085 triệu tăng so 915 triệu, đẩy gói Cao cấp ở TP HCM), số liệu và hạn chót (nhắc thanh toán An Phát và Đại Tín hạn thứ Sáu, chốt danh sách khách mời trước ngày 20), phân công theo người. Nhấn cho lớp: đây là sức mạnh của skill, làm đúng chuẩn ngay.

### [00:57-01:20] Thực hành 1: học viên tự tạo và kích hoạt skill
- **Lời dẫn GV:** "Đến lượt cả lớp. Tạo skill tom-tat-tai-lieu giống tôi, rồi chạy thử trên file biên bản demo. Ai kẹt giơ tay."
- **Đề bài:** Mỗi học viên (1) tạo skill tom-tat-tai-lieu, (2) kích hoạt skill trên `bien-ban-hop-mau.md`, (3) thử kích hoạt tự động bằng cách chỉ nói "tóm tắt giúp tôi file này" để xem Claude có tự nạp skill không.
- **Prompt gợi ý cho học viên:**
  ```
  1. Tạo skill tom-tat-tai-lieu tại .claude/skills/tom-tat-tai-lieu/SKILL.md, dùng để tóm tắt tài liệu dài theo cấu trúc: tóm tắt nhanh, ý chính, số liệu và hạn chót, điểm lưu ý. Chỉ dùng thông tin trong tài liệu.

  2. Dùng skill tom-tat-tai-lieu để tóm tắt file bien-ban-hop-mau.md.

  3. Tóm tắt giúp tôi file bien-ban-hop-mau.md.
  ```
- **File demo:** `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- **Kết quả mong đợi:** Mỗi học viên có thư mục `.claude/skills/tom-tat-tai-lieu/` với file SKILL.md, và chạy ra bản tóm tắt đúng cấu trúc. Ở bước 3, Claude tự nạp skill nhờ description (nếu không tự nạp, GV chỉ cách sửa description cho rõ hơn).

### [01:20-01:30] Nghỉ giải lao
- GV nhắc: phần sau ta đưa skill lên GitHub và tạo agent. Ai chưa xong skill tranh thủ nhờ trợ giảng.

### [01:30-01:45] MCP là gì và vì sao đưa skill lên GitHub
- **Lời dẫn GV:** "Trước khi bấm nút, ta cần hiểu hai thứ: MCP và GitHub, vì lát nữa ta ghép chúng lại."
- **Nội dung 1: MCP là gì.** Cổng cắm chuẩn để agent dùng công cụ và dữ liệu ngoài: GitHub, file, web, Google Drive. Cắm một MCP là cho agent thêm một khả năng. Hôm nay ta cắm MCP GitHub.
- **Nội dung 2: Vì sao đưa skill lên GitHub.** Skill để trên máy dễ mất, khó chia sẻ. Đưa lên một repo GitHub thì có bản lưu trên mạng, xem được lịch sử sửa, chia cho đồng nghiệp, đồng bộ nhiều máy.
- **Nội dung 3: Token là gì và vì sao phải giữ bí mật.** Token là chuỗi thay mật khẩu, cấp cho agent quyền dùng GitHub trong giới hạn. Token lộ thì người khác thao tác được GitHub của bạn, nên giữ như mật khẩu.
- **Câu hỏi tương tác:** "Vì sao ta không đưa mật khẩu GitHub cho agent mà lại dùng token? Gợi ý: token giới hạn quyền và thu hồi được."

### [01:45-02:08] Demo giảng viên: GitHub repo, token, cắm MCP, đẩy skill lên
**Bước 1: Tạo repo và lấy token GitHub**
- **Lời dẫn GV:** "Tôi vào GitHub tạo một repo riêng tư để cất skill, rồi lấy một token cấp quyền tối thiểu. Cả lớp xem trước, chưa cần làm theo ngay."
- **Prompt gõ vào Claude Code:** không có (thao tác trên web GitHub theo `mau-cau-hinh/github-mcp-va-token.md`)
- **File demo:** tham chiếu `mau-cau-hinh/github-mcp-va-token.md` (Bước 1 và Bước 2)
- **Kết quả mong đợi:** GV có 1 repo riêng tư (ví dụ `bo-skill-cua-toi`) và 1 token quyền Contents đọc ghi. Nhấn mạnh quy tắc an toàn: copy token ngay, không dán vào chat, chỉ dán vào cài đặt MCP.

**Bước 2: Cắm GitHub MCP bằng token**
- **Lời dẫn GV:** "Tôi mở cài đặt kết nối của Claude Desktop, thêm server GitHub, và dán token vào đúng ô. Đây là chỗ token gặp agent."
- **Prompt gõ vào Claude Code:** không có (thao tác trong cài đặt MCP của Claude Desktop)
- **File demo:** tham chiếu `mau-cau-hinh/github-mcp-va-token.md` (Bước 3)
- **Kết quả mong đợi:** GitHub MCP báo kết nối thành công. GV kiểm bằng một lệnh đơn giản ở bước sau.

**Bước 3: Dùng agent đẩy skill lên GitHub (quản lý skill)**
- **Lời dẫn GV:** "Giờ phần hay nhất: tôi bảo agent tự đẩy skill vừa tạo lên repo. Từ đây skill của tôi được quản lý trên GitHub."
- **Prompt gõ vào Claude Code:**
  ```
  Dùng GitHub, đẩy toàn bộ thư mục .claude/skills/ lên repo bo-skill-cua-toi của tôi. Nếu repo chưa có thì tạo mới ở chế độ riêng tư. Kèm mô tả ngắn: thêm skill tom-tat-tai-lieu.
  ```
- **File demo:** `.claude/skills/tom-tat-tai-lieu/SKILL.md` (tạo ở phần đầu buổi)
- **Kết quả mong đợi:** Agent qua GitHub MCP tạo hoặc cập nhật repo, đẩy file skill lên. GV mở repo trên web cho lớp thấy file SKILL.md đã nằm trên GitHub, có lịch sử commit. Nhấn: sau này sửa skill, chỉ cần bảo agent cập nhật lên GitHub.

### [02:08-02:22] Tạo agent đầu tiên
- **Lời dẫn GV:** "Cuối buổi, ta tạo agent đầu tiên: một trợ lý con chuyên một việc. Tôi làm mẫu agent soạn báo cáo, rồi cả lớp tạo một agent cho việc của mình."
- **Prompt demo GV:**
  ```
  Tạo cho tôi một agent tên report-agent tại .claude/agents/report-agent.md. Vai trò: chuyên soạn báo cáo, email, đề xuất từ số liệu hoặc ý thô. Quy tắc: tiếng Việt công sở, không dùng emoji trong email và báo cáo, không bịa số liệu, thiếu thì để [đợi bổ sung].
  ```
- **File demo:** tham chiếu `mau-cau-hinh/agent-report-mau.md`; tạo mới `.claude/agents/report-agent.md`
- **Kết quả mong đợi:** Agent tạo file `.claude/agents/report-agent.md` có name, description, tools và phần thân chỉ dẫn. GV giao thử: "Nhờ report-agent viết email nhắc thanh toán gửi khách An Phát" và cho lớp xem kết quả không emoji.
- **Thực hành nhanh học viên:** mỗi người tạo 1 agent cho việc lặp lại của nghề mình (ví dụ agent soạn email, agent lên lịch), đặt tên và mô tả rõ.

### [02:22-02:30] Chốt & giao bài
- **Lời dẫn GV:** "Tổng kết: hôm nay cả lớp đã hiểu skill và tự tạo skill, hiểu MCP, tạo repo GitHub và lấy token an toàn, cắm GitHub MCP để quản lý skill, và tạo agent đầu tiên. Đây là bộ nền cho cả khóa."
- Tổng kết 4 điều: skill đóng gói việc lặp lại; MCP cho agent thêm khả năng; GitHub để cất và quản lý skill; token phải giữ bí mật.
- **Bài về nhà:** hoàn tất phần GitHub nếu ở lớp chưa xong (tạo repo, token, cắm MCP, đẩy skill lên); tạo thêm 1 skill cho một việc lặp lại của mình; chụp màn hình repo skill trên GitHub gửi Zalo lớp.
- Xem trước Buổi 2: đào sâu **Skill**, tạo nhiều skill cho quy trình thật và tinh chỉnh cách kích hoạt.
- **Câu hỏi tương tác:** "Việc nào bạn muốn đóng gói thành skill tiếp theo?"

---

## Bảng prompt tổng hợp của buổi (tra nhanh)
| # | Prompt | File demo | Kết quả mong đợi |
|---|---|---|---|
| 1 | Tạo skill tom-tat-tai-lieu tại .claude/skills/tom-tat-tai-lieu/SKILL.md, cấu trúc tóm tắt. | tham chiếu `mau-cau-hinh/skill-tom-tat-tai-lieu.md` | File SKILL.md có name, description, phần thân |
| 2 | Dùng skill tom-tat-tai-lieu để tóm tắt bien-ban-hop-mau.md. | `demo/buoi-01/bien-ban-hop-mau.md` | Bản tóm tắt đúng cấu trúc, đúng số liệu biên bản |
| 3 | Tóm tắt giúp tôi file bien-ban-hop-mau.md. | `demo/buoi-01/bien-ban-hop-mau.md` | Claude tự nạp skill nhờ description |
| 4 | Đẩy thư mục .claude/skills/ lên repo bo-skill-cua-toi (tạo nếu chưa có). | `.claude/skills/tom-tat-tai-lieu/SKILL.md` | Skill nằm trên GitHub, có commit |
| 5 | Tạo agent report-agent tại .claude/agents/report-agent.md. | tham chiếu `mau-cau-hinh/agent-report-mau.md` | File agent có name, description, tools, thân |

## Câu hỏi tương tác gợi ý
- "Việc gì bạn làm đi làm lại hằng tuần, có thể đóng gói thành skill?"
- "Hai cách kích hoạt skill khác nhau ra sao, khi nào nên gọi tên thẳng?"
- "Vì sao dùng token thay vì mật khẩu GitHub cho agent?"
- "MCP giúp agent làm thêm được việc gì mà trước đó không làm được?"
- "Agent (subagent) khác skill ở điểm nào?"

## Tình huống hay gặp & cách xử lý
| Tình huống | Cách xử lý |
|---|---|
| Skill không tự nạp khi chỉ nói "tóm tắt giúp tôi" | Description viết chưa rõ "dùng khi nào". Sửa description cụ thể hơn, hoặc gọi thẳng tên skill. |
| Học viên định dán token vào khung chat | Dừng ngay. Token chỉ dán vào cài đặt MCP của Claude Desktop. Nhắc token như mật khẩu. |
| Token thiếu quyền, agent không đẩy được lên repo | Kiểm lại token có quyền Contents đọc ghi và trỏ đúng repo. Tạo lại token nếu cần. |
| GitHub MCP báo lỗi kết nối | Kiểm token còn hạn, đã dán đúng ô server GitHub, mạng ổn. Cắm lại. |
| Chưa có tài khoản GitHub | Tạo nhanh tại chỗ hoặc ghép cặp xem bạn bên cạnh, làm nốt ở nhà. |
| Agent tạo skill sai chỗ (không nằm trong .claude/skills) | Nhắc agent đặt đúng đường dẫn .claude/skills/<ten>/SKILL.md rồi tạo lại. |
| Nội dung quá nhiều, học viên đuối | Ưu tiên xong skill và tạo agent tại lớp; phần GitHub cho làm nốt ở nhà theo `mau-cau-hinh/github-mcp-va-token.md`. |

## Bài tập
- **Tại lớp:** Tạo được skill tom-tat-tai-lieu và chạy thử; hiểu và nói lại được MCP là gì; tạo được 1 agent đầu tiên. Cắm GitHub MCP và đẩy skill lên nếu kịp.
- **Về nhà:** Hoàn tất phần GitHub (repo, token, cắm MCP, đẩy skill lên); tạo thêm 1 skill cho việc lặp lại của mình; chụp màn hình repo skill trên GitHub gửi Zalo lớp.

## Tiêu chí hoàn thành buổi
- [ ] Hiểu và nói lại được skill là gì và 2 cách kích hoạt
- [ ] Tạo được skill tom-tat-tai-lieu và chạy ra bản tóm tắt đúng cấu trúc
- [ ] Hiểu MCP là gì
- [ ] Tạo được repo GitHub và lấy token đúng cách (an toàn)
- [ ] Cắm GitHub MCP và đẩy được skill lên repo (có thể hoàn tất ở nhà)
- [ ] Tạo được 1 agent đầu tiên và giao thử một việc
