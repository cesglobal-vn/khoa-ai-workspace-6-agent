# Outline Buổi 04: MCP tạo slide, và lập đội agent hỗ trợ công việc nhân sự

> Đây là OUTLINE để giảng viên duyệt hướng. Duyệt xong sẽ giãn thành giáo án chi tiết đầy đủ như Buổi 3.
> Lối dạy: Nỗi đau trước, khái niệm sau, demo rồi cho làm ngay. Mỗi phân đoạn có prompt sẵn.

## Thông tin buổi
- **Buổi:** 04 / 6
- **Khái niệm chính:** MCP tạo slide (ai-image-gpt-mcp) + Agent + Subagent + Agent Team
- **Bối cảnh áp dụng:** công việc phòng Nhân sự (tuyển dụng, onboarding, đào tạo)
- **Thời lượng:** 150 phút

## Học xong làm được gì
1. Dùng MCP tạo slide được cấp để sinh ảnh slide cho một chủ đề nhân sự.
2. Hiểu và giao được việc cho subagent khi cần đọc nhiều hồ sơ.
3. Tự lập được 2 tới 3 agent chuyên trách cho việc nhân sự.
4. Cho một đội agent phối hợp làm trọn một quy trình nhân sự.

## Bối cảnh demo dùng xuyên suốt (bộ file demo cần chuẩn bị)
Một tình huống thật của phòng Nhân sự: đón một nhân viên mới và làm slide đào tạo nội quy.

Thư mục demo đề xuất `demo/buoi-04/phong-nhan-su/`:
- `01-ung-vien/` : 4 tới 5 hồ sơ ứng viên (CV rút gọn dạng .md)
- `02-nhan-vien-moi/` : thông tin nhân viên sắp vào làm
- `03-noi-quy/` : nội quy công ty, quy trình onboarding
- `04-slide/` : nơi lưu ảnh slide agent tạo ra
- `CLAUDE.md` : hồ sơ phòng Nhân sự (nối tiếp Buổi 3)

> Bộ file demo này chưa có, sẽ tạo khi anh duyệt outline.

---

## Chuẩn bị của giảng viên trước buổi

### Bắt buộc kiểm, phần dễ chết nhất
- [ ] **Cài sẵn MCP ai-image-gpt trên máy lớp hoặc phát cấu hình sẵn.** KHÔNG để học viên tự git clone và đăng nhập OAuth trong lớp, quá kỹ thuật cho khối văn phòng. Xem mục "Ghi chú cài MCP" cuối bài
- [ ] Chạy thử `login_status` xác nhận tài khoản còn đăng nhập, còn quota sinh ảnh
- [ ] Sinh thử 1 ảnh slide nhân sự trước giờ, xem chữ tiếng Việt ra đúng không
- [ ] Test giao subagent đọc thư mục ứng viên và tóm tắt
- [ ] Test lập 1 agent trong `.claude/agents/` rồi mở phiên mới gọi lại
- [ ] Chuẩn bị bộ file demo phòng Nhân sự

### Thường lệ
- [ ] Mở sẵn Claude Code, đứng trong thư mục dự án
- [ ] Gửi Zalo lớp trước buổi: bảng prompt in sẵn, nhắc mở đúng thư mục

---

## Timeline

| Khối | Phút | Nội dung | Kiểu |
|---|---|---|---|
| K0 | 00:00-00:10 | Mở đầu, recap Buổi 3, nêu nỗi đau làm slide | Demo + hỏi lớp |
| K1 | 00:10-00:45 | MCP tạo slide: sinh ảnh slide nhân sự | Demo + thực hành |
| K2 | 00:45-01:10 | Subagent: giao việc nặng cho trợ lý riêng | Lý thuyết + demo + thực hành nhẹ |
| Nghỉ | 01:10-01:20 | Giải lao | |
| K3 | 01:20-01:55 | Lập agent chuyên trách cho nhân sự | Lý thuyết + thực hành |
| K4 | 01:55-02:20 | Agent team: đội agent phối hợp một quy trình nhân sự | Demo + thực hành có kiểm soát |
| K5 | 02:20-02:30 | Chốt, giao bài, xem trước Buổi 5 | |

Mốc cứng: K1 xong trước 00:45, K3 xong trước 01:55. K1 và K3 không cắt.

---

## K0: Mở đầu (10 phút)

**Nỗi đau mở màn:** "Ai từng phải ngồi cả buổi làm slide đào tạo nội quy, hay slide đón nhân viên mới? Tối nay mình để AI làm phần nặng đó, và lập cho anh chị một đội trợ lý lo việc nhân sự."

- Recap Buổi 3 bằng 2 câu hỏi: CLAUDE.md để làm gì, agent đọc file trên máy có cần MCP không.
- Nêu bản đồ tối nay: MCP tạo slide → subagent → lập agent → đội agent.
- **Việc giao lớp gõ ngay (2 phút):** mở thư mục demo phòng Nhân sự, chạy prompt kiểm.

**PROMPT K0:**
```
Bạn đang mở thư mục nào, trong đây có những file gì? Trả lời ngắn gọn.
```

---

## K1: MCP tạo slide (35 phút)

**Ẩn dụ:** MCP tạo slide giống thuê một họa sĩ. Anh chị tả nội dung một trang slide, họa sĩ vẽ ra ảnh trang đó.

### Phần 1: Khái niệm (5 phút)
- MCP này sinh ẢNH. Làm slide nghĩa là mỗi trang slide là một ảnh: anh chị tả trọn nội dung một trang, nó vẽ ra một ảnh trang đó, rồi ghép nhiều ảnh thành bộ slide.
- Nhắc lại: MCP là cổng nối ra công cụ ngoài. Buổi 3 nối Drive và Gmail, tối nay nối công cụ vẽ ảnh.

### Phần 2: Kiểm công cụ đã sẵn sàng (3 phút)
**PROMPT K1-1:**
```
Kiểm tra giúp tôi công cụ tạo ảnh đã đăng nhập chưa và còn dùng được không.
```
Kết quả mong đợi: báo đã đăng nhập, còn quota.

### Phần 3: Demo GV sinh 1 ảnh slide nhân sự (7 phút)
**PROMPT K1-2 (slide bìa buổi đào tạo nội quy):**
```
Tạo cho tôi một ảnh slide bìa, tỷ lệ 16:9, nền trắng, phong cách công sở trang trọng.
Tiêu đề lớn: NỘI QUY CÔNG TY. Dòng phụ: Buổi đào tạo nhân viên mới. Góc dưới: Phòng Nhân sự.
Chữ tiếng Việt có dấu đầy đủ, bố cục gọn, không dùng emoji.
```
Kết quả mong đợi: một ảnh slide bìa, chữ tiếng Việt đúng dấu. GV mở ảnh cho lớp xem.

**PROMPT K1-3 (slide nội dung từ file thật):**
```
Đọc file 03-noi-quy/noi-quy-cong-ty.md, lấy 4 quy định quan trọng nhất, tạo một ảnh slide 16:9 nền trắng liệt kê 4 quy định đó dạng gạch đầu dòng, tiêu đề "4 điều nhân viên mới cần nhớ". Chữ tiếng Việt có dấu.
```
Kết quả mong đợi: ảnh slide có đúng 4 quy định lấy từ file, không bịa thêm.

### Phần 4: Thực hành (20 phút)
Mỗi học viên tạo 2 tới 3 ảnh slide cho một chủ đề nhân sự của mình (onboarding, quy trình nghỉ phép, giới thiệu phúc lợi).

**PROMPT K1-4 (bản học viên tự điền):**
```
Tạo ảnh slide 16:9 nền trắng, phong cách công sở, chủ đề [chủ đề của bạn].
Tiêu đề: [tiêu đề]. Nội dung: [3 tới 4 ý chính]. Chữ tiếng Việt có dấu, không emoji.
```
Mốc cứng phút 45: mỗi người dán 1 ảnh slide vào chat Zoom.

**Ghi chú an toàn:** ảnh sinh ra có thể sai chính tả hoặc thừa chữ. Luôn đọc lại trước khi đưa vào bộ slide thật. Chữ trong ảnh không sửa nhanh được, sai thì sinh lại với prompt rõ hơn.

---

## K2: Subagent, trợ lý cho việc nặng (25 phút)

**Ẩn dụ:** subagent là một trợ lý anh chị gọi tới làm một việc nặng rồi về. Nó ngồi phòng riêng, đọc xong chỉ nộp lại bản tóm tắt, không bày bừa ra bàn của anh chị.

### Phần 1: Khái niệm (8 phút)
- Agent chính: cái Claude đang nói chuyện với anh chị từ đầu khóa.
- Subagent: trợ lý tạm cho việc nặng, ví dụ đọc 10 hồ sơ ứng viên.
- Ba điều về subagent: làm ở phòng riêng nên không bày bừa phiên chính; chỉ nộp bản tóm tắt không đổ nguyên nội dung; các subagent không nói chuyện với nhau, chỉ báo về agent chính.
- Gọi subagent không phải cài gì, chỉ cần nói tự nhiên "dùng một subagent để...".

### Phần 2: Demo GV (6 phút)
**PROMPT K2-1:**
```
Dùng một subagent đọc toàn bộ hồ sơ trong thư mục 01-ung-vien, trả về đúng một bảng: tên ứng viên, vị trí ứng tuyển, điểm mạnh nhất, một điểm cần lưu ý. Chỉ trả bảng, không đổ nguyên nội dung từng hồ sơ.
```
Kết quả mong đợi: một bảng tóm tắt các ứng viên. GV chỉ ra: Claude báo đang dùng subagent, phiên chính vẫn gọn.

### Phần 3: Thực hành nhẹ (11 phút)
Học viên giao subagent đọc một nhóm file thật của mình và tóm tắt.

**PROMPT K2-2 (bản học viên):**
```
Dùng một subagent đọc toàn bộ file trong thư mục [tên thư mục của bạn], trả về đúng [số] dòng tóm tắt những điểm quan trọng nhất. Chỉ trả tóm tắt.
```

---

## Nghỉ giải lao (10 phút)

---

## K3: Lập agent chuyên trách cho nhân sự (35 phút)

**Ẩn dụ:** nếu subagent là trợ lý gọi tạm, thì agent chuyên trách là nhân viên chính thức có bản mô tả công việc riêng, làm mãi một loại việc.

### Phần 1: Khái niệm + cấu trúc file agent (8 phút)
- Agent chuyên trách định nghĩa bằng một file trong `.claude/agents/`.
- Ba dòng cần nhớ: name, description (quyết định khi nào tự được gọi), tools (giới hạn công cụ cho an toàn).
- Nhấn: tạo hoặc sửa agent xong phải mở phiên mới thì mới nạp.

### Phần 2: Demo GV lập agent onboarding (7 phút)
**PROMPT K3-1:**
```
Tạo file .claude/agents/agent-onboarding.md, một agent chuyên chuẩn bị đón nhân viên mới.
- name: agent-onboarding
- description: Chuyên soạn checklist đón nhân viên mới, email chào mừng, và lịch onboarding tuần đầu. Dùng khi có nhân viên mới sắp vào làm.
- tools: Read, Write, Grep, Glob
- Phần thân: đọc thông tin nhân viên mới trong 02-nhan-vien-moi và nội quy trong 03-noi-quy. Soạn: checklist đón, email chào mừng văn phong công sở không emoji, lịch tuần đầu. Chỉ dùng thông tin có thật, thiếu thì ghi [đợi bổ sung], không dừng lại hỏi.
Tạo xong in lại nội dung file.
```
Kết quả mong đợi: file agent đúng cấu trúc. Mở phiên mới, giao thử một việc, xem nó chạy.

### Phần 3: Thực hành (20 phút)
Mỗi học viên lập 1 tới 2 agent cho việc nhân sự của mình. Gợi ý 3 agent theo nghề:
- `agent-tuyen-dung`: sàng lọc và tóm tắt hồ sơ ứng viên.
- `agent-onboarding`: chuẩn bị đón nhân viên mới.
- `agent-dao-tao`: soạn dàn ý và nội dung slide đào tạo.

**PROMPT K3-2 (bản học viên tự điền):**
```
Tạo file .claude/agents/[ten-agent].md.
- name: [ten-agent]
- description: [chuyên việc gì, dùng khi nào]
- tools: Read, Write, Grep, Glob
- Phần thân: [các bước agent làm, quy tắc không bịa, không emoji]
Tạo xong in lại nội dung file.
```
Mốc cứng phút 55: mỗi người dán tên agent vừa tạo vào chat Zoom.

---

## K4: Agent team hỗ trợ một quy trình nhân sự (25 phút)

**Ẩn dụ:** một mình một nhân viên làm tuần tự thì chậm. Đội agent là giao cùng lúc cho nhiều nhân viên, mỗi người một phần, xong trưởng nhóm gom lại.

### Phần 1: Khái niệm + cảnh báo (7 phút)
- Đội agent: một việc lớn chia cho nhiều agent chạy cùng lúc, agent chính đóng vai trưởng nhóm gom kết quả.
- **Cảnh báo nói rõ:** chạy nhiều agent cùng lúc kết quả không phải lúc nào cũng đều, có khi Claude làm tuần tự, có khi tự làm hết. Đó là bình thường. Không giám sát được bên trong từng agent, nên phải bắt mỗi agent tự khai nguồn.
- Quy tắc: việc nào các phần phụ thuộc nhau thì làm tuần tự, chỉ chia song song khi các phần độc lập.

### Phần 2: Demo GV, đội 3 agent đón nhân viên mới (10 phút)
Quy trình đón nhân viên mới chia 3 phần độc lập:
**PROMPT K4-1:**
```
Tôi có một nhân viên mới sắp vào làm, thông tin trong 02-nhan-vien-moi. Hãy giao cho 3 agent chạy cùng lúc, mỗi agent một phần, không tự làm thay:
- agent-onboarding: soạn checklist đón và email chào mừng.
- agent-dao-tao: soạn dàn ý buổi đào tạo nội quy cho nhân viên này.
- một agent tạo 1 ảnh slide bìa buổi đào tạo nội quy.
Mỗi agent kết thúc bằng mục "Nguồn": file đã đọc. Khi cả ba xong, gom lại thành một gói đón nhân viên mới cho tôi.
```
Kết quả mong đợi: một gói gồm checklist, email, dàn ý đào tạo, và 1 ảnh slide bìa.

### Phần 3: Thực hành có kiểm soát (8 phút)
Học viên chọn một quy trình nhân sự của mình, chia 2 tới 3 phần độc lập, giao đội agent.

**PROMPT K4-2 (bản học viên):**
```
Tôi có việc [tên việc]. Giao cho [2 tới 3] agent chạy cùng lúc, mỗi agent một phần:
- [agent 1]: [phần 1].
- [agent 2]: [phần 2].
Mỗi agent kết thúc bằng mục "Nguồn". Xong gom lại thành một bản chung.
```

---

## K5: Chốt và giao bài (10 phút)

**Bốn ý cần nhớ:**
1. MCP tạo slide: tả trọn một trang, nó vẽ ra ảnh trang đó. Luôn đọc lại chữ trong ảnh.
2. Subagent: trợ lý gọi tạm cho việc nặng, chỉ nộp tóm tắt.
3. Agent chuyên trách: nhân viên chính thức, định nghĩa bằng một file, tạo xong phải mở phiên mới.
4. Đội agent: chia việc độc lập cho nhiều agent cùng lúc, bắt mỗi agent khai nguồn.

**Bài về nhà:**
- Tạo bộ 3 tới 5 ảnh slide cho một chủ đề nhân sự thật.
- Lập 1 agent chuyên trách cho việc mình làm nhiều nhất, chạy thử 3 lần.
- Chụp kết quả gửi Zalo lớp.

**Xem trước Buổi 5:** ghép tất cả thành một quy trình nhân sự tự chạy và đặt lịch định kỳ.

---

## Ghi chú cài MCP tạo slide (đọc kỹ trước khi lên lớp)

MCP ai-image-gpt cài khá kỹ thuật: cần git clone, công cụ uv, Python 3.12, và đăng nhập OAuth dán lại đường link callback. Khối văn phòng làm live trong lớp gần như chắc chắn tắc.

**Hướng khuyến nghị:**
1. Anh cài sẵn MCP trên máy lớp, hoặc phát sẵn file cấu hình để học viên chỉ việc dán vào Claude Desktop.
2. Đăng nhập sẵn một tài khoản dùng chung cho lớp, hoặc hướng dẫn đăng nhập ở buổi kỹ thuật riêng.
3. Buổi 4 chỉ dạy DÙNG, không dạy cài. Phần cài để tài liệu riêng cho ai muốn tự dựng ở nhà.

**Phương án B nếu MCP tạo slide chưa sẵn sàng:** dạy K1 bằng cách cho agent soạn NỘI DUNG từng slide dạng văn bản (dàn ý slide), phần vẽ ảnh để làm sau. Cả buổi vẫn chạy trọn vẹn phần agent, subagent, đội agent.

---

## Câu chưa rõ, cần anh chốt trước khi tôi giãn thành giáo án chi tiết
1. MCP tạo slide đã cài sẵn trên máy lớp chưa, hay tối nay mới cài? Quyết định K1 dạy dùng hay dạy cả cài.
2. Tài khoản sinh ảnh dùng chung cho lớp hay mỗi người một tài khoản? Ảnh hưởng quota khi 15 người cùng sinh.
3. Bối cảnh nhân sự có đúng ý không, hay đổi sang bối cảnh khác (ví dụ hỗ trợ nhiều phòng ban)?
4. Agent team: anh muốn cho lớp thực hành thật (như outline này), hay chỉ demo cho biết như giáo án tham khảo?
