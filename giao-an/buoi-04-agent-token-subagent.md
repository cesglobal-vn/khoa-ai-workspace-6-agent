# Outline Buổi 04 (viết cho người học mới): MCP tạo slide, agent, token, subagent

> Outline này viết từ góc người học mới hoàn toàn. Trọng tâm: giúp họ tự trả lời được
> "việc này nên hỏi thẳng, tạo agent, hay gọi subagent". Nhiều ví dụ với file có sẵn, prompt chi tiết.
> Agent team KHÔNG dạy hôm nay, để Buổi 5.

## Thông tin buổi
- **Buổi:** 04 / 6
- **Khái niệm chính:** MCP tạo slide, lập agent và cơ chế hoạt động, cách tính token, subagent
- **Bối cảnh:** công việc phòng Nhân sự
- **Thời lượng:** 150 phút

---

## PHẦN NỀN: người học mới cần gỡ đúng một nút thắt

Là người mới, sau ba buổi họ đã nghe: chat thường, skill, agent, MCP. Giờ thêm subagent. Họ rối vì **nhìn cái nào cũng na ná nhau**. Nút thắt duy nhất cần gỡ tối nay: **việc trước mặt thì nên dùng cái nào?**

### Bốn cách nhờ Claude, và chọn cái nào

| Cách | Dùng khi | Ví dụ một câu |
|---|---|---|
| **Hỏi thẳng** | Việc làm một lần, đơn giản | "Tóm tắt giúp tôi CV của anh Nam" |
| **Skill** (đã học Buổi 2) | Một quy trình lặp lại, mình vẫn là người bấm nút | Mỗi tuần soạn email chào hàng theo đúng mẫu |
| **Agent chuyên trách** | Muốn giao hẳn một vai, có quy tắc riêng, dùng lại nhiều lần | agent-onboarding lo trọn việc đón nhân viên mới |
| **Subagent** | Việc nặng, đọc nhiều file, chỉ cần bản tóm tắt, làm một lần | Đọc 20 CV chọn ra 5 người |

### Sơ đồ 2 câu hỏi để tự quyết (chiếu lên bảng, học viên thuộc lòng)

```
Việc trước mặt của bạn...

CÂU 1: Việc này bạn có làm đi làm lại nhiều lần, cùng một cách không?
   CÓ  ->  Tạo AGENT chuyên trách (giao hẳn một vai)
   KHÔNG ->  sang Câu 2

CÂU 2: Việc này có phải đọc nhiều file, việc nặng, mà bạn chỉ cần bản tóm tắt không?
   CÓ  ->  Gọi SUBAGENT (trợ lý đọc giúp rồi tóm tắt)
   KHÔNG ->  HỎI THẲNG (làm luôn cho nhanh)
```

### Bảng quyết định, nhiều tình huống thật (file đã có sẵn trong máy)

| Tình huống | Nên dùng | Vì sao |
|---|---|---|
| Tóm tắt riêng 1 CV của anh Nam | Hỏi thẳng | Một file, một lần |
| Đọc 20 CV, chọn 5 người hợp vị trí Sale | Subagent | Nặng, nhiều file, chỉ cần bảng tóm tắt, làm một lần |
| Mỗi lần có nhân viên mới, soạn checklist đón + email + lịch | Agent | Lặp lại, giao hẳn một vai |
| Soạn một email trả lời khách hôm nay | Hỏi thẳng | Một lần, đơn giản |
| Quét cả thư mục hợp đồng, tìm cái sắp hết hạn | Subagent | Nặng, đọc nhiều, một lần |
| Mỗi đợt tuyển, sàng lọc CV theo đúng bộ tiêu chí | Agent | Lặp lại, có quy tắc cố định |
| Đọc 30 biên bản họp quý, rút ra các quyết định | Subagent | Nặng, một lần |
| Mỗi tuần soạn báo cáo tuần theo mẫu | Agent hoặc Skill | Lặp lại |

**Câu chốt cho lớp:** "Lặp lại thì nuôi một nhân viên riêng, đó là agent. Việc nặng đọc một lần thì thuê trợ lý đọc giúp, đó là subagent."

---

## Bối cảnh demo, file đã chuẩn bị sẵn

Thư mục `demo/buoi-04/phong-nhan-su/`:
- `01-ung-vien/` : 5 CV rút gọn: `cv-nguyen-van-nam.md`, `cv-tran-thi-hoa.md`, `cv-le-van-hung.md`, `cv-pham-thi-lan.md`, `cv-do-van-minh.md`
- `02-nhan-vien-moi/` : `nhan-vien-moi-hoa.md` (chị Hoa, vào làm vị trí Sale)
- `03-noi-quy/` : `noi-quy-cong-ty.md`, `quy-trinh-onboarding.md`
- `04-slide/` : nơi lưu ảnh slide
- `CLAUDE.md` : hồ sơ phòng Nhân sự

> Bộ file demo này chưa có, sẽ tạo khi anh duyệt outline.

---

## Timeline

| Khối | Phút | Nội dung |
|---|---|---|
| K0 | 00:00-00:12 | Mở đầu + sơ đồ 2 câu hỏi "dùng cái nào" |
| K1 | 00:12-00:40 | MCP tạo slide |
| K2 | 00:40-01:15 | Lập agent, cơ chế hoạt động, ngân hàng ví dụ agent |
| Nghỉ | 01:15-01:25 | |
| K3 | 01:25-01:48 | Cách tính token |
| K4 | 01:48-02:20 | Subagent, cách làm việc, ngân hàng ví dụ subagent |
| K5 | 02:20-02:30 | Chốt, bảng so sánh agent vs subagent |

Mốc cứng: K2 xong trước 01:15, K4 xong trước 02:20. K2 và K4 không cắt.

---

## K0: Mở đầu (12 phút)

**Nỗi đau mở màn:** "Ba buổi rồi cả lớp nghe chat, skill, agent, MCP, giờ thêm subagent. Ai thấy rối chưa biết lúc nào dùng cái nào thì giơ tay. Tối nay tôi gỡ đúng nút đó, và cho anh chị một sơ đồ hai câu hỏi là tự quyết được."

- Chiếu bảng "Bốn cách nhờ Claude" và sơ đồ 2 câu hỏi ở phần nền.
- Đưa 3 tình huống, cho lớp giơ tay chọn hỏi thẳng / agent / subagent. Sửa tại chỗ.
- **PROMPT K0 (giao lớp gõ):**
```
Bạn đang mở thư mục nào, trong đây có những file gì? Trả lời ngắn gọn.
```

---

## K1: MCP tạo slide (28 phút)

**Ẩn dụ:** MCP tạo slide giống thuê họa sĩ. Tả một trang, nó vẽ ra ảnh trang đó.

### Kiểm công cụ (2 phút)
**PROMPT K1-1:**
```
Kiểm tra giúp tôi công cụ tạo ảnh đã đăng nhập chưa và còn dùng được không.
```

### Demo GV (7 phút)
**PROMPT K1-2 (slide bìa):**
```
Tạo cho tôi một ảnh slide bìa, tỷ lệ 16:9, nền trắng, phong cách công sở trang trọng.
Tiêu đề lớn: NỘI QUY CÔNG TY. Dòng phụ: Buổi đào tạo nhân viên mới. Góc dưới: Phòng Nhân sự.
Chữ tiếng Việt có dấu đầy đủ, không dùng emoji.
```
**PROMPT K1-3 (slide lấy nội dung từ file có sẵn):**
```
Đọc file 03-noi-quy/noi-quy-cong-ty.md, lấy 4 quy định quan trọng nhất, tạo một ảnh slide 16:9
nền trắng liệt kê 4 quy định đó dạng gạch đầu dòng, tiêu đề "4 điều nhân viên mới cần nhớ".
Chữ tiếng Việt có dấu.
```
Kết quả mong đợi: ảnh slide đúng 4 quy định lấy từ file, không bịa.

### Thực hành (17 phút)
**PROMPT K1-4 (bản học viên):**
```
Tạo ảnh slide 16:9 nền trắng, phong cách công sở, chủ đề [chủ đề của bạn].
Tiêu đề: [tiêu đề]. Nội dung: [3 tới 4 ý chính]. Chữ tiếng Việt có dấu, không emoji.
```
Mốc cứng phút 40: dán 1 ảnh slide vào chat Zoom.
**An toàn:** chữ trong ảnh sai thì sinh lại với prompt rõ hơn, không sửa tay được.

---

## K2: Lập agent và cơ chế hoạt động (35 phút)

### Phần 1: Cơ chế hoạt động, người mới phải thấy agent không phải hộp đen (8 phút)

Vẽ lên bảng 4 bước một agent chạy khi nhận việc:

```
1. NHẬN VIỆC       Bạn giao một yêu cầu.
2. ĐỌC BỐI CẢNH    Agent đọc CLAUDE.md (biết bạn là ai), đọc các file bạn chỉ,
                   nạp skill phù hợp nếu có.
3. DÙNG CÔNG CỤ    Agent dùng công cụ được cấp (đọc file, ghi file, tra web, gọi MCP)
                   làm từng bước.
4. TRẢ KẾT QUẢ     Agent viết ra kết quả cho bạn.
```

- Người mới cần thấy: agent luôn đi qua đúng 4 bước này. Vì thế CLAUDE.md quan trọng (bước 2), tools quan trọng (bước 3).
- Mỗi lần đọc ở bước 2 và viết ở bước 4 đều tốn token (nối sang K3).

### Phần 2: Người mới hỏi "tạo agent xong thì dùng thế nào?" (nói kỹ, đây là chỗ hay khựng)

Ba việc, đúng thứ tự:
1. **Tạo file agent một lần** trong `.claude/agents/`. Đây là lúc viết bản mô tả công việc.
2. **Mở phiên mới** thì Claude mới nạp agent vừa tạo. Không mở phiên mới là gọi không ra.
3. **Gọi việc bằng tên**: "nhờ agent-onboarding làm...". Agent tự đọc file theo mô tả trong phần thân, mình không phải chỉ lại từng file.

### Phần 3: Demo GV lập agent-onboarding (7 phút)

**PROMPT K2-1 (tạo agent):**
```
Tạo file .claude/agents/agent-onboarding.md, một agent chuyên chuẩn bị đón nhân viên mới.
- name: agent-onboarding
- description: Chuyên soạn checklist đón nhân viên mới, email chào mừng, và lịch onboarding tuần đầu. Dùng khi có nhân viên mới sắp vào làm.
- tools: Read, Write, Grep, Glob
- Phần thân: đọc thông tin nhân viên mới trong 02-nhan-vien-moi và nội quy trong 03-noi-quy. Soạn checklist đón, email chào mừng văn phong công sở không emoji, và lịch tuần đầu. Chỉ dùng thông tin có thật, thiếu thì ghi [đợi bổ sung], không dừng lại hỏi.
Tạo xong in lại nội dung file.
```

**PROMPT K2-2 (mở phiên mới rồi gọi):**
```
Nhờ agent-onboarding chuẩn bị gói đón nhân viên mới theo thông tin trong 02-nhan-vien-moi.
```
Kết quả mong đợi: agent đọc file chị Hoa và nội quy, trả về checklist đón, email chào mừng chị Hoa không emoji, lịch tuần đầu. GV chỉ ra từng bước khớp cơ chế 4 bước.

### Phần 4: Ngân hàng ví dụ agent (người mới xem để bắt chước cho nghề mình)

Ba agent nhân sự, mỗi cái kèm mô tả và một prompt gọi khi file đã có:

**Ví dụ A: agent-tuyen-dung** (dùng mỗi đợt tuyển)
- Mô tả: sàng lọc và chấm CV theo bộ tiêu chí cố định của công ty.
- Prompt gọi khi đã có file:
```
Nhờ agent-tuyen-dung chấm toàn bộ CV trong 01-ung-vien theo tiêu chí vị trí Sale, xếp hạng và giải thích ngắn vì sao.
```

**Ví dụ B: agent-dao-tao** (dùng mỗi lần mở lớp đào tạo)
- Mô tả: soạn dàn ý buổi đào tạo và nội dung từng slide từ tài liệu nội quy.
- Prompt gọi:
```
Nhờ agent-dao-tao soạn dàn ý buổi đào tạo nội quy 45 phút từ 03-noi-quy, chia thành các phần kèm ý chính mỗi phần.
```

**Ví dụ C: agent cho các phòng khác** (gợi ý để học viên tự nghĩ)
| Phòng | Agent | Việc lặp lại nó lo |
|---|---|---|
| Kế toán | agent-cong-no | Rà công nợ quá hạn, soạn email nhắc |
| Kinh doanh | agent-bao-gia | Soạn báo giá theo đúng mẫu và chính sách |
| Quản lý | agent-bao-cao-tuan | Gom số liệu tuần thành báo cáo |
| Marketing | agent-noi-dung | Soạn bài theo giọng thương hiệu |

### Phần 5: Thực hành (13 phút)
Mỗi học viên lập 1 agent cho việc lặp lại của nghề mình, mở phiên mới, gọi thử.
**PROMPT K2-3 (bản học viên):**
```
Tạo file .claude/agents/[ten-agent].md.
- name: [ten-agent]
- description: [chuyên việc gì, dùng khi nào]
- tools: Read, Write, Grep, Glob
- Phần thân: [các bước agent làm, quy tắc không bịa, không emoji]
Tạo xong in lại nội dung file. Sau đó tôi mở phiên mới để gọi.
```
Mốc cứng phút 75: dán tên agent vào chat Zoom.

---

## Nghỉ giải lao (10 phút)

---

## K3: Cách tính token (23 phút)

**Ẩn dụ:** token là đồng hồ taxi. Mỗi chữ đọc vào và viết ra đều tính tiền.

### Token là gì (7 phút)
- Đơn vị đo lượng chữ agent xử lý. Áng chừng: 4 ký tự tiếng Anh khoảng 1 token. Tiếng Việt có dấu tốn hơn, cùng nội dung khoảng 1,5 tới 2 lần.
- Tính cả hai chiều: chữ đọc vào và chữ viết ra đều tốn. Nối lại cơ chế K2: bước 2 đọc bối cảnh tốn đầu vào, bước 4 trả kết quả tốn đầu ra.
- Mỗi phiên giới hạn khoảng 200 nghìn token. Gần đầy thì Claude nén lịch sử cũ, có thể quên đoạn đầu.

### Xem đã dùng bao nhiêu (5 phút)
GV demo lệnh (tên có thể khác theo phiên bản, đã kiểm trước): `/context` xem phiên chứa gì; `/cost` tổng đã dùng; `/compact` nén cho nhẹ.

### Bốn cách tiết kiệm (4 phút)
1. Giữ CLAUDE.md ngắn (đọc lại mỗi phiên).
2. Đừng nạp file không cần.
3. **Giao việc nặng cho subagent** (cầu nối sang K4).
4. Việc dài thì `/compact` hoặc mở phiên mới.

### Hoạt động (7 phút)
**PROMPT K3-1:**
```
1. Ước lượng đoạn văn tiếng Việt 100 chữ này tốn khoảng bao nhiêu token: [dán đoạn của bạn].
2. Dịch sang tiếng Anh, ước lượng lại, so sánh.
3. Ước lượng CLAUDE.md của tôi tốn bao nhiêu token mỗi phiên, gợi ý một chỗ rút gọn.
```
> Nói rõ: con số token là ước lượng để hiểu cơ chế, không phải hóa đơn.

---

## K4: Subagent và cách làm việc với subagent (32 phút)

### Phần 1: Người mới cần hiểu subagent qua đúng một hình ảnh (7 phút)
- Nối từ K3: cách tiết kiệm token số 3 là subagent. Việc đọc nhiều mà chỉ cần tóm tắt thì giao nó.
- **Subagent là trợ lý gọi tạm.** Ba điều:
  1. Nó ngồi phòng riêng, đọc nhiều cỡ nào cũng không làm bừa bộn phiên chính của bạn.
  2. Nó chỉ nộp lại bản tóm tắt, không đổ nguyên nội dung, nên phiên chính đỡ tốn token.
  3. Nó không nói chuyện với subagent khác, chỉ báo về bạn.
- **Không cần cài gì**, chỉ nói "dùng một subagent để...".

### Phần 2: Cách làm việc với subagent (nói kỹ, người mới hay làm sai ở đây)

Vì subagent ngồi phòng riêng, **nó không nghe chuyện nãy giờ của bạn**. Nên khi giao việc phải nói đủ ba thứ:
1. **Đọc ở đâu:** ghi rõ tên thư mục hoặc các file.
2. **Làm gì với chúng:** tóm tắt, so sánh, lọc, xếp hạng.
3. **Trả về dạng gì và bao nhiêu:** một bảng, hay mấy dòng, và nhấn "chỉ trả tóm tắt, đừng đổ nguyên nội dung".

Thiếu một trong ba thứ này là subagent hay trả sai ý.

### Phần 3: Demo GV (6 phút)
**PROMPT K4-1:**
```
Dùng một subagent đọc toàn bộ hồ sơ trong thư mục 01-ung-vien, trả về đúng một bảng:
tên ứng viên, vị trí ứng tuyển, điểm mạnh nhất, một điểm cần lưu ý.
Chỉ trả bảng, không đổ nguyên nội dung từng hồ sơ.
```
Kết quả mong đợi: bảng tóm tắt 5 ứng viên. GV chỉ ra: Claude báo đang dùng subagent; chỉ bảng về tới phiên chính; nội dung 5 CV nằm ở phòng riêng nên phiên chính vẫn gọn.
**So sánh cho lớp thấy:** nếu bảo đọc thẳng 5 CV thì phiên chính ngốn nguyên nội dung 5 file, tốn token hơn nhiều.

### Phần 4: Ngân hàng ví dụ subagent (nhiều ca với file có sẵn)

**Ví dụ 1: chọn người từ nhiều CV**
```
Dùng một subagent đọc 5 CV trong 01-ung-vien, chọn ra 2 người hợp nhất vị trí Sale,
trả về đúng: tên, lý do chọn, một rủi ro. Chỉ trả kết quả chọn, không đổ nội dung CV.
```

**Ví dụ 2: quét thư mục tìm cái sắp tới hạn**
```
Dùng một subagent đọc toàn bộ file trong thư mục 03-hop-dong, liệt kê những hợp đồng
sắp hết hạn trong 60 ngày tới, mỗi dòng ghi tên hợp đồng và ngày hết hạn. Chỉ trả danh sách.
```

**Ví dụ 3: rút quyết định từ nhiều biên bản**
```
Dùng một subagent đọc tất cả biên bản trong thư mục 03-bien-ban-hop, rút ra mọi quyết định
và việc được phân công, trả về một bảng: quyết định, người phụ trách, hạn. Chỉ trả bảng.
```

**Ví dụ 4: tổng hợp phản hồi**
```
Dùng một subagent đọc toàn bộ file khảo sát trong thư mục 04-khao-sat, tóm tắt 5 điều
khách khen nhiều nhất và 5 điều khách phàn nàn nhiều nhất. Chỉ trả 2 danh sách.
```

### Phần 5: Thực hành (13 phút)
**PROMPT K4-2 (bản học viên):**
```
Dùng một subagent đọc toàn bộ file trong thư mục [tên thư mục của bạn], trả về đúng
[số] dòng tóm tắt hoặc một bảng [các cột bạn cần]. Chỉ trả tóm tắt, không đổ nguyên nội dung.
```
*Gợi ý điền: thư mục hồ sơ ứng viên, biên bản họp, hợp đồng, khảo sát.*
Mốc cứng phút 118: dán bản tóm tắt subagent trả về vào chat Zoom.

---

## K5: Chốt (10 phút)

### Bảng so sánh agent và subagent (chiếu lại cho khắc sâu)

| | Agent chuyên trách | Subagent |
|---|---|---|
| Là gì | Nhân viên chính thức, có bản mô tả công việc | Trợ lý gọi tạm cho một việc |
| Có file định nghĩa không | Có, trong `.claude/agents/` | Không, chỉ nói miệng |
| Dùng lại nhiều lần không | Có, gọi bằng tên | Không, xong việc là thôi |
| Hợp với việc | Lặp lại, có quy tắc riêng | Nặng, đọc nhiều, cần tóm tắt, một lần |
| Ví dụ | agent-onboarding lo đón nhân viên mới | đọc 20 CV chọn 5 người |

**Bốn ý cần nhớ:**
1. Sơ đồ 2 câu hỏi: lặp lại thì nuôi agent, việc nặng một lần thì gọi subagent, còn lại hỏi thẳng.
2. Agent chạy qua 4 bước: nhận việc, đọc bối cảnh, dùng công cụ, trả kết quả. Tạo xong phải mở phiên mới.
3. Token là đồng hồ taxi: đọc và ghi đều tốn, tiếng Việt tốn hơn.
4. Giao việc cho subagent phải nói đủ: đọc ở đâu, làm gì, trả về dạng gì.

**Bài về nhà:**
- Lập 1 agent cho việc mình làm nhiều nhất, chạy thử 3 lần.
- Một lần dùng subagent đọc một nhóm file thật.
- Tự phân loại 3 việc trong tuần của mình theo sơ đồ 2 câu hỏi, ghi lại dùng cái nào.
- Chụp kết quả gửi Zalo lớp.

**Xem trước Buổi 5:** khi đã có nhiều agent, cho cả một đội agent phối hợp làm cùng một quy trình.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt tóm tắt | Khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Thư mục này có file gì | K0 | Liệt kê đúng file |
| K1-1 | Kiểm công cụ tạo ảnh | K1 | Đã đăng nhập, còn quota |
| K1-2 | Ảnh slide bìa NỘI QUY | K1 | Ảnh bìa chữ Việt đúng |
| K1-3 | Ảnh slide 4 quy định từ file | K1 | Đúng 4 quy định, không bịa |
| K2-1 | Tạo agent-onboarding | K2 | File agent đúng cấu trúc |
| K2-2 | Gọi agent-onboarding (phiên mới) | K2 | Checklist + email + lịch |
| A | Gọi agent-tuyen-dung chấm CV | K2 | Xếp hạng ứng viên |
| B | Gọi agent-dao-tao soạn dàn ý | K2 | Dàn ý đào tạo từ nội quy |
| K3-1 | Ước lượng token Việt vs Anh | K3 | Thấy Việt tốn hơn |
| K4-1 | Subagent đọc thư mục ứng viên | K4 | Bảng tóm tắt, phiên gọn |
| VD1 | Subagent chọn 2 người từ 5 CV | K4 | Kết quả chọn + rủi ro |
| VD2 | Subagent tìm hợp đồng sắp hết hạn | K4 | Danh sách theo hạn |
| VD3 | Subagent rút quyết định từ biên bản | K4 | Bảng quyết định |
| VD4 | Subagent tổng hợp khảo sát | K4 | 2 danh sách khen/chê |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| Học viên vẫn không biết chọn agent hay subagent | Quay lại sơ đồ 2 câu hỏi. Hỏi: việc này lặp lại không? Nếu không, nặng không? |
| Tạo agent xong gọi tên không ra | Chưa mở phiên mới. Mở phiên mới rồi gọi |
| Subagent trả nguyên nội dung thay vì tóm tắt | Prompt thiếu câu "chỉ trả tóm tắt, không đổ nội dung". Thêm vào, nêu rõ số dòng |
| Subagent trả sai ý | Thiếu một trong ba thứ: đọc ở đâu, làm gì, trả dạng gì. Bổ sung cho đủ |
| Cài MCP slide chưa xong | Phương án B: cho agent soạn nội dung slide dạng văn bản, vẽ ảnh sau |
| Chữ trong ảnh slide sai | Sinh lại với prompt rõ hơn |
| Lệnh xem token khác tên | GV đã kiểm trước. Không có thì dạy token ở mức khái niệm và mẹo tiết kiệm |
| Cháy giờ | Cắt theo thứ tự: demo lệnh token, rồi rút K1 còn 20 phút. Không cắt K2 và K4 |

## Ba câu kiểm hiểu cuối buổi
1. "Việc lặp lại thì dùng agent hay subagent? Việc đọc 20 file một lần thì dùng cái nào?"
2. "Kể 4 bước một agent chạy khi nhận việc."
3. "Giao việc cho subagent phải nói đủ ba thứ nào?" (đọc ở đâu, làm gì, trả về dạng gì)

## Tiêu chí hoàn thành buổi
- [ ] Tự phân loại được một việc thật của mình theo sơ đồ 2 câu hỏi
- [ ] Tạo được 1 ảnh slide nhân sự bằng MCP
- [ ] Lập được 1 agent, mở phiên mới gọi chạy được
- [ ] Nói lại được 4 bước cơ chế của agent
- [ ] Giao được subagent đọc một nhóm file và nhận về bản tóm tắt đúng ý

---

## Ghi chú cài MCP tạo slide
Cài kỹ thuật (git clone, uv, Python, OAuth). Không để học viên tự cài trong lớp. Anh cài sẵn hoặc phát cấu hình sẵn, buổi học chỉ dạy DÙNG. Phương án B nếu chưa sẵn sàng: cho agent soạn nội dung slide dạng văn bản, vẽ ảnh sau.

## Câu chưa rõ, cần anh chốt trước khi giãn thành bản chi tiết đầy đủ
1. MCP tạo slide đã cài sẵn máy lớp chưa?
2. Tài khoản sinh ảnh dùng chung hay riêng?
3. Bối cảnh nhân sự giữ hay đổi?
