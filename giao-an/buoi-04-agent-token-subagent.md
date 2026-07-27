# Giáo án Buổi 04: MCP tạo slide, lập agent và cơ chế hoạt động, cách tính token, subagent

> Lối dạy: nỗi đau trước, khái niệm sau, demo rồi cho làm ngay. Mỗi phân đoạn có prompt sẵn.
> Agent team KHÔNG dạy hôm nay, để sang Buổi 5.

## Thông tin buổi
- **Buổi:** 04 / 6
- **Khái niệm chính:** MCP tạo slide, lập 1 agent và cơ chế hoạt động của agent, cách tính token, subagent
- **Bối cảnh áp dụng:** công việc phòng Nhân sự (đón nhân viên mới, đào tạo nội quy)
- **Thời lượng:** 150 phút

## Vì sao xếp buổi theo thứ tự này
Bốn phần nối liền nhau thành một mạch, không rời rạc:
1. **MCP tạo slide** mở màn nhẹ, ra sản phẩm nhìn thấy ngay, hâm nóng lại khái niệm MCP của Buổi 3.
2. **Lập agent và cơ chế hoạt động** là lõi: agent làm việc bằng cách đọc bối cảnh, dùng công cụ, rồi trả kết quả.
3. **Cách tính token**: chính việc đọc và ghi ở phần 2 là cái tốn token. Hiểu token để dùng tiết kiệm.
4. **Subagent**: cách giao việc nặng mà không đốt token của phiên chính. Đây là lời giải cho phần 3.

## Học xong làm được gì
1. Dùng MCP được cấp để sinh ảnh slide cho một chủ đề nhân sự.
2. Lập được 1 agent chuyên trách và nói được agent hoạt động qua mấy bước.
3. Hiểu token là gì, biết cách xem đã dùng bao nhiêu và 4 cách tiết kiệm.
4. Giao được việc nặng cho subagent để giữ phiên chính gọn và đỡ tốn token.

## Bối cảnh demo dùng xuyên suốt
Tình huống phòng Nhân sự: đón một nhân viên mới và làm slide đào tạo nội quy.
Thư mục demo đề xuất `demo/buoi-04/phong-nhan-su/`:
- `01-ung-vien/` : 4 tới 5 hồ sơ ứng viên rút gọn (.md), dùng cho phần subagent
- `02-nhan-vien-moi/` : thông tin nhân viên sắp vào làm
- `03-noi-quy/` : nội quy công ty, quy trình onboarding
- `04-slide/` : nơi lưu ảnh slide
- `CLAUDE.md` : hồ sơ phòng Nhân sự (nối tiếp Buổi 3)

> Bộ file demo này chưa có, sẽ tạo khi anh duyệt giáo án.

---

## Chuẩn bị của giảng viên

### Bắt buộc kiểm, phần dễ chết nhất
- [ ] **Cài sẵn MCP tạo slide trên máy lớp hoặc phát cấu hình sẵn.** KHÔNG để học viên tự cài trong lớp (git clone, uv, đăng nhập OAuth quá kỹ thuật). Xem "Ghi chú cài MCP" cuối bài
- [ ] Chạy `login_status` xác nhận còn đăng nhập và còn quota
- [ ] Sinh thử 1 ảnh slide nhân sự, xem chữ tiếng Việt đúng dấu không
- [ ] Lập thử 1 agent trong `.claude/agents/`, mở phiên mới gọi lại xem có nạp không
- [ ] Test lệnh xem token trên bản Claude Desktop lớp dùng (`/context`, `/cost`, `/compact`), ghi lại tên lệnh đúng vì có thể khác theo phiên bản
- [ ] Chuẩn bị bộ file demo phòng Nhân sự

### Thường lệ
- [ ] Mở sẵn Claude Code trong thư mục dự án
- [ ] Gửi Zalo lớp: bảng prompt in sẵn, nhắc mở đúng thư mục

---

## Timeline

| Khối | Phút | Nội dung | Kiểu |
|---|---|---|---|
| K0 | 00:00-00:10 | Mở đầu, recap Buổi 3, nêu nỗi đau | Demo + hỏi lớp |
| K1 | 00:10-00:40 | MCP tạo slide | Demo + thực hành |
| K2 | 00:40-01:15 | Lập 1 agent và cơ chế hoạt động | Lý thuyết + demo + thực hành |
| Nghỉ | 01:15-01:25 | Giải lao | |
| K3 | 01:25-01:50 | Cách tính token | Lý thuyết + hoạt động |
| K4 | 01:50-02:20 | Subagent và cách làm việc với subagent | Lý thuyết + demo + thực hành |
| K5 | 02:20-02:30 | Chốt, giao bài, xem trước Buổi 5 | |

Mốc cứng: K1 xong trước 00:40, K2 xong trước 01:15. K2 và K4 không cắt.

---

## K0: Mở đầu (10 phút)

**Nỗi đau mở màn:** "Ai từng ngồi cả buổi làm slide đào tạo, rồi lại đọc cả chục hồ sơ ứng viên tới hoa mắt? Tối nay mình để AI làm phần nặng đó, và hiểu rõ nó làm việc thế nào, tốn kém ra sao."

- Recap Buổi 3 nhanh, 2 câu: CLAUDE.md để làm gì; agent đọc file trên máy có cần MCP không (không).
- Nêu bản đồ tối nay: tạo slide bằng MCP, lập agent, hiểu token, dùng subagent.
- **Việc giao lớp gõ ngay (2 phút):**

**PROMPT K0:**
```
Bạn đang mở thư mục nào, trong đây có những file gì? Trả lời ngắn gọn.
```

---

## K1: MCP tạo slide (30 phút)

**Ẩn dụ:** MCP tạo slide giống thuê một họa sĩ. Anh chị tả nội dung một trang, họa sĩ vẽ ra ảnh trang đó.

### Phần 1: Khái niệm (4 phút)
- MCP này sinh ẢNH. Làm slide nghĩa là mỗi trang là một ảnh: tả trọn một trang, nó vẽ ra ảnh trang đó, rồi ghép nhiều ảnh thành bộ.
- Nhắc lại từ Buổi 3: MCP là cổng nối ra công cụ ngoài. Buổi 3 nối Drive và Gmail, tối nay nối công cụ vẽ ảnh.

### Phần 2: Kiểm công cụ sẵn sàng (2 phút)
**PROMPT K1-1:**
```
Kiểm tra giúp tôi công cụ tạo ảnh đã đăng nhập chưa và còn dùng được không.
```
Kết quả mong đợi: báo đã đăng nhập, còn quota.

### Phần 3: Demo GV (7 phút)

**PROMPT K1-2 (slide bìa, bản GV chạy ngay):**
```
Tạo cho tôi một ảnh slide bìa, tỷ lệ 16:9, nền trắng, phong cách công sở trang trọng.
Tiêu đề lớn: NỘI QUY CÔNG TY. Dòng phụ: Buổi đào tạo nhân viên mới. Góc dưới: Phòng Nhân sự.
Chữ tiếng Việt có dấu đầy đủ, bố cục gọn, không dùng emoji.
```
Kết quả mong đợi: một ảnh slide bìa, chữ tiếng Việt đúng dấu.

**PROMPT K1-3 (slide nội dung lấy từ file thật):**
```
Đọc file 03-noi-quy/noi-quy-cong-ty.md, lấy 4 quy định quan trọng nhất, tạo một ảnh slide 16:9 nền trắng liệt kê 4 quy định đó dạng gạch đầu dòng, tiêu đề "4 điều nhân viên mới cần nhớ". Chữ tiếng Việt có dấu.
```
Kết quả mong đợi: ảnh slide đúng 4 quy định lấy từ file, không bịa thêm.

### Phần 4: Thực hành (17 phút)
Mỗi học viên tạo 2 tới 3 ảnh slide cho một chủ đề nhân sự của mình.

**PROMPT K1-4 (bản học viên tự điền):**
```
Tạo ảnh slide 16:9 nền trắng, phong cách công sở, chủ đề [chủ đề của bạn].
Tiêu đề: [tiêu đề]. Nội dung: [3 tới 4 ý chính]. Chữ tiếng Việt có dấu, không emoji.
```
*Gợi ý điền: chủ đề như quy trình nghỉ phép, giới thiệu phúc lợi, các bước onboarding.*

Mốc cứng phút 40: mỗi người dán 1 ảnh slide vào chat Zoom.

**Ghi chú an toàn:** ảnh có thể sai chính tả hoặc thừa chữ. Luôn đọc lại trước khi đưa vào bộ slide thật. Chữ trong ảnh sai thì sinh lại với prompt rõ hơn, không sửa tay được.

---

## K2: Lập 1 agent và cơ chế hoạt động (35 phút)

**Ẩn dụ:** agent chuyên trách là một nhân viên chính thức có bản mô tả công việc riêng, làm mãi một loại việc. Khác với anh chị nhờ Claude làm lặt vặt, đây là giao hẳn một vai.

### Phần 1: Cơ chế hoạt động của một agent (10 phút)
Đây là phần lý thuyết quan trọng nhất buổi. Vẽ lên bảng 4 bước một agent chạy khi được giao việc:

```
1. NHẬN VIỆC        Anh chị giao một yêu cầu.
2. ĐỌC BỐI CẢNH     Agent đọc: CLAUDE.md (biết bạn là ai), file liên quan,
                    skill phù hợp nếu có. Đây là lúc nó nạp thông tin.
3. SUY NGHĨ + DÙNG   Agent nghĩ cách làm, dùng công cụ được cấp (đọc file,
   CÔNG CỤ          ghi file, tra web, gọi MCP) để làm từng bước.
4. TRẢ KẾT QUẢ      Agent viết ra kết quả cho anh chị.
```

- Nhấn: agent không phải hộp đen. Nó luôn đi qua đúng 4 bước này. Hiểu vậy thì biết vì sao CLAUDE.md quan trọng (bước 2), vì sao tools quan trọng (bước 3).
- Nhấn: mỗi lần đọc ở bước 2 và viết ở bước 4 đều tốn token. Đây là cầu nối sang K3.
- **Ba dòng khai báo của một agent:** name (tên gọi), description (quyết định khi nào tự được gọi), tools (giới hạn công cụ cho an toàn).

**Câu hỏi tương tác:** "Theo cả lớp, nếu một agent viết báo cáo thì ở bước 2 nó cần đọc gì, bước 3 cần công cụ gì?"

### Phần 2: Demo GV lập agent onboarding (8 phút)
**PROMPT K2-1:**
```
Tạo file .claude/agents/agent-onboarding.md, một agent chuyên chuẩn bị đón nhân viên mới.
- name: agent-onboarding
- description: Chuyên soạn checklist đón nhân viên mới, email chào mừng, và lịch onboarding tuần đầu. Dùng khi có nhân viên mới sắp vào làm.
- tools: Read, Write, Grep, Glob
- Phần thân: đọc thông tin nhân viên mới trong 02-nhan-vien-moi và nội quy trong 03-noi-quy. Soạn checklist đón, email chào mừng văn phong công sở không emoji, và lịch tuần đầu. Chỉ dùng thông tin có thật, thiếu thì ghi [đợi bổ sung], không dừng lại hỏi.
Tạo xong in lại nội dung file.
```
Kết quả mong đợi: file agent đúng cấu trúc, 3 dòng khai báo rõ.

**Bước bắt buộc sau khi tạo (ghi đỏ):** mở phiên mới rồi mới gọi agent, không thì Claude chưa nạp.
**PROMPT K2-2 (giao việc, chạy ở phiên mới):**
```
Nhờ agent-onboarding chuẩn bị gói đón nhân viên mới theo thông tin trong 02-nhan-vien-moi.
```
Kết quả mong đợi: agent trả về checklist, email chào mừng không emoji, lịch tuần đầu. GV chỉ cho lớp thấy đây chính là 4 bước cơ chế vừa học.

### Phần 3: Thực hành (17 phút)
Mỗi học viên lập 1 agent cho việc nhân sự của mình. Gợi ý: agent-tuyen-dung (tóm tắt hồ sơ ứng viên), agent-dao-tao (soạn dàn ý đào tạo).

**PROMPT K2-3 (bản học viên tự điền):**
```
Tạo file .claude/agents/[ten-agent].md.
- name: [ten-agent]
- description: [chuyên việc gì, dùng khi nào]
- tools: Read, Write, Grep, Glob
- Phần thân: [các bước agent làm, quy tắc không bịa, không emoji]
Tạo xong in lại nội dung file. Sau đó tôi sẽ mở phiên mới để gọi.
```
Mốc cứng phút 75: mỗi người dán tên agent vừa tạo vào chat Zoom.

---

## Nghỉ giải lao (10 phút)

---

## K3: Cách tính token (25 phút)

**Ẩn dụ:** token giống đồng hồ taxi. Mỗi chữ agent đọc vào và viết ra đều tính tiền. Đi càng xa (đọc càng nhiều, viết càng dài) thì càng tốn.

### Phần 1: Token là gì và tính thế nào (8 phút)
- **Token là đơn vị đo lượng chữ** agent xử lý. Nhớ mức áng chừng: khoảng 4 ký tự tiếng Anh là 1 token. Tiếng Việt có dấu tốn hơn, cùng một nội dung tốn khoảng 1,5 tới 2 lần tiếng Anh.
- **Tính cả hai chiều:** chữ đọc vào (input) và chữ viết ra (output) đều tốn. Nối lại cơ chế K2: bước 2 đọc bối cảnh tốn token đầu vào, bước 4 trả kết quả tốn token đầu ra.
- **Mỗi phiên có giới hạn**, khoảng 200 nghìn token. Gần đầy thì Claude nén bớt lịch sử cũ, có thể quên đoạn đầu. Đây là lý do việc dài nên tách phiên.

### Phần 2: Xem đã dùng bao nhiêu (5 phút)
GV demo các lệnh kiểm token trên bản lớp dùng. Tên lệnh có thể khác theo phiên bản, GV đã kiểm trước:
- `/context` : xem phiên đang chứa những gì, tốn token vào đâu.
- `/cost` : tổng token và chi phí đã dùng.
- `/compact` : nén lịch sử cũ lại cho nhẹ phiên.

### Phần 3: Bốn cách tiết kiệm token (5 phút)
1. **Giữ CLAUDE.md ngắn.** Nó đọc lại mỗi phiên, dài là tốn mỗi lần.
2. **Đừng nạp file không cần.** Chỉ mở file liên quan tới việc đang làm.
3. **Giao việc nặng cho subagent.** Đọc 10 hồ sơ thì để subagent đọc, phiên chính chỉ nhận tóm tắt. Đây là cầu nối sang K4.
4. **Việc dài thì `/compact` hoặc mở phiên mới.**

### Phần 4: Hoạt động (7 phút)
**PROMPT K3-1:**
```
1. Ước lượng đoạn văn tiếng Việt 100 chữ này tốn khoảng bao nhiêu token: [dán một đoạn của bạn].
2. Dịch sang tiếng Anh rồi ước lượng lại, so sánh hai con số.
3. Ước lượng file CLAUDE.md hiện tại của tôi tốn bao nhiêu token mỗi phiên, gợi ý một chỗ rút gọn.
```
Kết quả rút ra: tiếng Việt tốn hơn, CLAUDE.md nên gọn.

> Ghi chú GV: nói rõ các con số token là ước lượng để hiểu cơ chế, không phải hóa đơn chính xác.

---

## K4: Subagent và cách làm việc với subagent (30 phút)

**Ẩn dụ:** subagent là một trợ lý anh chị gọi tới làm một việc nặng rồi về. Nó ngồi phòng riêng, đọc xong chỉ nộp lại bản tóm tắt, không bày hết giấy tờ ra bàn của anh chị.

### Phần 1: Khái niệm và khi nào dùng (8 phút)
- Nối thẳng từ K3: cách tiết kiệm token số 3 chính là subagent. Việc phải đọc nhiều mà anh chị chỉ cần bản tóm tắt thì giao subagent.
- **Ba điều về subagent:**
  1. Làm ở phòng riêng, đọc nhiều cỡ nào cũng không làm bừa bộn phiên chính của anh chị.
  2. Chỉ nộp lại bản tóm tắt, không đổ nguyên nội dung. Nhờ vậy phiên chính đỡ tốn token.
  3. Các subagent không nói chuyện với nhau, chỉ báo về agent chính.
- **Không cần cài gì.** Chỉ nói tự nhiên "dùng một subagent để...".
- **Khi nào nên dùng:** đọc nhiều file, quét cả thư mục lớn, việc nặng mà chỉ cần kết quả gọn. Khi nào không cần: việc nhỏ một hai file thì làm thẳng cho nhanh.

### Phần 2: Demo GV (7 phút)
**PROMPT K4-1:**
```
Dùng một subagent đọc toàn bộ hồ sơ trong thư mục 01-ung-vien, trả về đúng một bảng: tên ứng viên, vị trí ứng tuyển, điểm mạnh nhất, một điểm cần lưu ý. Chỉ trả bảng, không đổ nguyên nội dung từng hồ sơ.
```
Kết quả mong đợi: một bảng tóm tắt các ứng viên. GV chỉ ra: Claude báo đang dùng subagent; chỉ bảng tóm tắt về tới phiên chính; nội dung đầy đủ nằm ở phòng riêng của subagent nên phiên chính vẫn gọn và đỡ tốn token.

**So sánh cho lớp thấy rõ:** nếu không dùng subagent mà bảo đọc thẳng 5 hồ sơ, phiên chính sẽ ngốn toàn bộ nội dung 5 file đó, tốn token hơn nhiều.

### Phần 3: Thực hành (15 phút)
Học viên giao subagent đọc một nhóm file thật của mình rồi tóm tắt.

**PROMPT K4-2 (bản học viên tự điền):**
```
Dùng một subagent đọc toàn bộ file trong thư mục [tên thư mục của bạn], trả về đúng [số] dòng tóm tắt những điểm quan trọng nhất. Chỉ trả tóm tắt, không đổ nguyên nội dung.
```
*Gợi ý điền: thư mục hồ sơ ứng viên, thư mục biên bản họp, thư mục hợp đồng.*

Mốc cứng phút 118: mỗi người dán bản tóm tắt subagent trả về vào chat Zoom.

---

## K5: Chốt và giao bài (10 phút)

**Bốn ý cần nhớ:**
1. **MCP tạo slide:** tả trọn một trang, nó vẽ ra ảnh. Luôn đọc lại chữ trong ảnh.
2. **Agent chạy qua 4 bước:** nhận việc, đọc bối cảnh, dùng công cụ, trả kết quả. Tạo xong phải mở phiên mới.
3. **Token là đồng hồ taxi:** đọc và ghi đều tốn, tiếng Việt tốn hơn, giữ CLAUDE.md gọn.
4. **Subagent:** giao việc nặng cho trợ lý riêng, chỉ nhận tóm tắt, đỡ tốn token phiên chính.

**Bài về nhà:**
- Tạo bộ 3 tới 5 ảnh slide cho một chủ đề nhân sự thật.
- Lập 1 agent chuyên trách cho việc mình làm nhiều nhất, chạy thử 3 lần.
- Một lần dùng subagent đọc một nhóm file của mình.
- Chụp kết quả gửi Zalo lớp.

**Xem trước Buổi 5:** khi đã có nhiều agent, cách cho cả một đội agent phối hợp làm cùng một quy trình.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt | Dùng ở khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Bạn đang mở thư mục nào, có file gì? | K0 | Liệt kê đúng thư mục và file |
| K1-1 | Kiểm công cụ tạo ảnh đã đăng nhập và còn dùng được không | K1 | Báo đã đăng nhập, còn quota |
| K1-2 | Tạo ảnh slide bìa NỘI QUY CÔNG TY, 16:9 nền trắng | K1 | Ảnh slide bìa, chữ Việt đúng dấu |
| K1-3 | Từ file nội quy, tạo ảnh slide 4 quy định quan trọng | K1 | Ảnh slide đúng 4 quy định từ file |
| K1-4 | Tạo ảnh slide chủ đề của bạn (bản học viên) | K1 | Ảnh slide theo chủ đề học viên |
| K2-1 | Tạo file agent-onboarding trong .claude/agents | K2 | File agent đúng cấu trúc |
| K2-2 | Nhờ agent-onboarding chuẩn bị gói đón nhân viên mới | K2 | Checklist + email + lịch tuần đầu |
| K2-3 | Tạo agent cho việc của bạn (bản học viên) | K2 | File agent của học viên |
| K3-1 | Ước lượng token đoạn Việt, so với Anh, và CLAUDE.md | K3 | Thấy tiếng Việt tốn hơn |
| K4-1 | Dùng subagent đọc thư mục ứng viên, trả về 1 bảng | K4 | Bảng tóm tắt ứng viên, phiên chính gọn |
| K4-2 | Dùng subagent đọc thư mục của bạn (bản học viên) | K4 | Bản tóm tắt do subagent trả |

## Câu hỏi tương tác gợi ý
- "Một agent viết báo cáo thì ở bước đọc bối cảnh nó cần đọc gì?"
- "Vì sao tạo agent xong phải mở phiên mới?"
- "Tiếng Việt hay tiếng Anh tốn token hơn? Vì sao?"
- "Khi nào nên gọi subagent, khi nào làm thẳng cho nhanh?"
- "Dùng subagent giúp tiết kiệm token ở chỗ nào?"

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| **Cài MCP tạo slide chưa xong hoặc lỗi đăng nhập** | Chuyển sang phương án B: cho agent soạn nội dung slide dạng văn bản, phần vẽ ảnh làm sau. Cả buổi vẫn chạy trọn phần agent, token, subagent |
| **Chữ trong ảnh slide sai chính tả** | Sinh lại với prompt rõ hơn. Không sửa tay được vì chữ nằm trong ảnh |
| **Tạo agent xong gọi tên thì Claude không biết** | Chưa mở phiên mới. Mở phiên mới rồi gọi |
| **Agent đặt file sai chỗ, không nằm trong .claude/agents** | Nhờ Claude đặt lại đúng đường dẫn |
| **Lệnh xem token khác tên trên bản lớp dùng** | GV đã kiểm trước giờ. Nếu không có lệnh nào, dạy token ở mức khái niệm và mẹo tiết kiệm, bỏ phần demo lệnh |
| **Subagent trả về nguyên nội dung thay vì tóm tắt** | Nhắc lại trong prompt: chỉ trả tóm tắt, không đổ nguyên nội dung. Nêu rõ số dòng |
| **Học viên hỏi subagent khác agent chuyên trách chỗ nào** | Agent chuyên trách là nhân viên chính thức có file định nghĩa, dùng lại nhiều lần. Subagent là trợ lý gọi tạm cho một việc nặng rồi thôi, không cần file |
| **Cháy giờ** | Cắt theo thứ tự: phần demo lệnh token, rồi rút K1 còn 20 phút. Không cắt K2 (cơ chế agent) và K4 (subagent) |

## Cách kiểm học viên qua Zoom
| Cách | Làm thế nào |
|---|---|
| Dán chat Zoom | Sau mỗi thực hành, dán 3 dòng đầu kết quả vào chat |
| Mốc đồng bộ cứng | Phút 40 có 1 ảnh slide. Phút 75 có 1 agent. Phút 118 có 1 bản tóm tắt subagent |
| Xoay vòng share màn hình | Mỗi buổi gọi 3 tới 4 người share 30 giây |
| Danh sách đỏ | Trợ giảng ghi tên ai chưa làm được, kèm 1-1 sau buổi |

## Ba câu kiểm hiểu cuối buổi
1. "Kể 4 bước một agent chạy khi được giao việc." (nhận việc, đọc bối cảnh, dùng công cụ, trả kết quả)
2. "Vì sao tiếng Việt tốn token hơn tiếng Anh?" (có dấu, cùng nội dung tốn nhiều token hơn)
3. "Dùng subagent tiết kiệm token ở chỗ nào?" (việc nặng làm ở phòng riêng, phiên chính chỉ nhận tóm tắt)

## Tiêu chí hoàn thành buổi
- [ ] Tạo được ít nhất 1 ảnh slide nhân sự bằng MCP
- [ ] Lập được 1 agent chuyên trách, mở phiên mới gọi chạy được
- [ ] Nói lại được 4 bước cơ chế hoạt động của agent
- [ ] Biết xem token đã dùng và nói được 2 cách tiết kiệm
- [ ] Giao được subagent đọc một nhóm file và nhận về bản tóm tắt

---

## Ghi chú cài MCP tạo slide (đọc kỹ trước khi lên lớp)

MCP tạo slide cài khá kỹ thuật: cần git clone, công cụ uv, Python, và đăng nhập OAuth dán lại đường link callback. Khối văn phòng làm live trong lớp gần như chắc chắn tắc.

**Hướng khuyến nghị:**
1. Anh cài sẵn trên máy lớp, hoặc phát sẵn file cấu hình để học viên chỉ dán vào Claude Desktop.
2. Đăng nhập sẵn một tài khoản dùng chung cho lớp, hoặc để buổi kỹ thuật riêng.
3. Buổi 4 chỉ dạy DÙNG, không dạy cài. Phần cài để tài liệu riêng cho ai muốn tự dựng ở nhà.

**Phương án B nếu MCP chưa sẵn sàng:** dạy K1 bằng cách cho agent soạn nội dung từng slide dạng văn bản (dàn ý slide), phần vẽ ảnh để sau. Cả buổi vẫn trọn vẹn phần agent, token, subagent.

---

## Câu chưa rõ, cần anh chốt trước khi tôi giãn thành bản chi tiết đầy đủ
1. MCP tạo slide đã cài sẵn máy lớp chưa, hay tối nay mới cài?
2. Tài khoản sinh ảnh dùng chung cho lớp hay mỗi người một cái? Ảnh hưởng quota khi nhiều người cùng sinh.
3. Bối cảnh nhân sự có giữ không, hay đổi sang bối cảnh khác?
