# Outline Buổi 05 (viết cho người học mới): Lập agent bài bản, agent với skill, tạo và test 2 agent

> Đổi nội dung: hiện lớp chưa có agent nào nên chưa chạy được đội agent, và Buổi 4 chưa dạy kỹ agent.
> Buổi này dạy lập agent cho chắc. Đội agent (nối chuỗi, song song) chuyển sang buổi sau.
> Thứ tự: agent là gì, agent khác skill thế nào, tạo 2 agent, agent dùng tool và skill, cách gọi, rồi mới test.

## Thông tin buổi
- **Buổi:** 05 / 6
- **Khái niệm chính:** agent là gì, agent với skill, tạo agent, tools, tích hợp skill, cách gọi và test agent
- **Bối cảnh:** dùng lại file demo có sẵn (số liệu bán hàng, hồ sơ khách hàng)
- **Thời lượng:** 150 phút

---

## PHẦN NỀN cho người học mới

### 1. Agent là gì (nói kỹ, vì Buổi 4 chưa sâu)

Agent là **một nhân viên AI có bản mô tả công việc riêng**, do mình lập ra bằng một file. Khác với việc mình hỏi Claude lặt vặt, agent là giao hẳn một vai: mình đặt tên nó, ghi rõ nó chuyên việc gì, cho nó dùng công cụ nào, và dặn nó làm theo quy tắc gì.

Mỗi khi được giao việc, agent chạy qua 4 bước:
```
1. NHẬN VIỆC       Bạn giao một yêu cầu.
2. ĐỌC BỐI CẢNH    Agent đọc mô tả công việc của chính nó, đọc các file bạn chỉ, nạp skill nếu cần.
3. DÙNG CÔNG CỤ    Agent dùng đúng các công cụ được cấp (đọc file, ghi file, tra web) làm từng bước.
4. TRẢ KẾT QUẢ     Agent trả kết quả cho bạn.
```

Một file agent gồm 3 dòng khai báo và một phần thân:
- `name`: tên gọi, để mình gọi đích danh.
- `description`: chuyên việc gì, dùng khi nào. Dòng này quyết định khi nào Claude tự gọi nó ra.
- `tools`: danh sách công cụ nó được phép dùng. Đây là cách khoanh vùng cho an toàn.
- Phần thân: dặn nó làm gì, theo quy tắc nào.

### 2. Khi nào tạo agent, khi nào tạo skill (câu hỏi quan trọng nhất buổi)

Cả skill và agent đều để chuẩn hóa một việc. Khác nhau ở chỗ:

- **Skill là tờ công thức.** Claude chính cầm công thức và tự nấu. Vẫn là Claude chính làm, chỉ là làm theo đúng các bước ghi sẵn.
- **Agent là thuê hẳn một đầu bếp chuyên món đó.** Có bếp riêng, dụng cụ riêng, mình giao hẳn việc rồi nhận món.

Bảng chọn:

| Bạn muốn | Nên dùng |
|---|---|
| Chuẩn hóa CÁCH làm một việc, Claude chính tự làm là được | Skill |
| Một quy trình ngắn, dùng lại nhiều lần | Skill |
| Giao hẳn một vai lặp lại cho một "nhân viên" riêng | Agent |
| Giới hạn công cụ cho an toàn (ví dụ chỉ được đọc, không được sửa) | Agent |
| Việc nặng, muốn nó làm ở cửa sổ ngữ cảnh riêng cho khỏi lấp phiên chính | Agent |

Câu chốt cho lớp: **"Chỉ cần công thức thì làm skill. Muốn giao hẳn cho một người có bếp riêng thì lập agent."**

### 3. Agent điều khiển tool và skill thế nào

- **Tool (công cụ):** dòng `tools` trong file agent là danh sách công cụ nó được dùng. Cấp `Read` thì nó đọc được file; cấp `Write` thì ghi được; không cấp `Write` thì nó không sửa được file, dù có muốn. Đây là cách mình điều khiển agent qua công cụ: cho gì dùng nấy.
- **Skill:** agent cũng dùng lại được skill đã có. Nếu trong lúc làm việc nó gặp một bước đã có skill chuẩn (ví dụ tóm tắt tài liệu), nó tự nạp skill đó để làm cho đúng.
- **Khi nào nên tích hợp skill vào agent:** khi một bước con của agent đã có skill tốt rồi thì để agent dùng lại, đừng viết lại quy trình đó vào agent. Nguyên tắc: skill lo "cách làm một việc nhỏ", agent lo "cả một vai". Ghép lại thì agent gọn mà vẫn chuẩn.

---

## Bối cảnh demo (dùng file có sẵn, chạy được ngay)
- `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md` : số liệu bán hàng tháng 3 thô, dùng test agent soạn báo cáo.
- `tai-lieu-phat/demo/buoi-03/phong-kinh-doanh-mau/01-khach-hang/` : 3 hồ sơ khách (Minh Long, Hải Nam, An Phát), dùng test agent rà soát khách.

Hai agent sẽ lập:
- **agent-soan-bao-cao** : soạn báo cáo và email từ số liệu thô. Có quyền ghi file.
- **agent-ra-soat-khach** : đọc hồ sơ khách, chỉ ra khách nào cần hành động. Chỉ đọc, KHÔNG có quyền ghi.

---

## Timeline

| Khối | Phút | Nội dung |
|---|---|---|
| K0 | 00:00-00:10 | Mở đầu, nêu lại vì sao học lập agent |
| K1 | 00:10-00:35 | Agent là gì + khi nào agent, khi nào skill |
| K2 | 00:35-01:05 | Tạo agent 1 (agent-soan-bao-cao), giải thích từng dòng |
| Nghỉ | 01:05-01:15 | |
| K3 | 01:15-01:45 | Tạo agent 2 (agent-ra-soat-khach) + tools + tích hợp skill |
| K4 | 01:45-02:15 | Cách gọi agent + test cả 2 agent |
| K5 | 02:15-02:30 | Chốt |

Mốc cứng: K2 xong trước 01:05. K2 và K4 không cắt.

---

## K0: Mở đầu (10 phút)

**Lời dẫn GV:** "Buổi trước mình đã nghe qua agent, nhưng chưa ai tự tay lập một agent chạy được. Tối nay mình làm cho chắc: hiểu agent là gì, phân biệt với skill, rồi tự tay tạo hai agent, cho chúng dùng công cụ, gọi ra và test. Xong buổi, mỗi anh chị có hai nhân viên AI thật, dùng được ngay."

- Nêu bản đồ: agent là gì, agent vs skill, tạo 2 agent, gọi, test.
- **PROMPT K0 (giao lớp gõ, kiểm thư mục):**
```
Thư mục này đang có những file và thư mục con nào? Trả lời ngắn gọn.
```

---

## K1: Agent là gì và khi nào dùng agent hay skill (25 phút)

### Phần 1: Agent là gì (10 phút)
- Trình bày 4 bước hoạt động và 3 dòng khai báo (phần nền mục 1). Vẽ lên bảng.
- Nhấn: agent là một file, không phải cài đặt gì phức tạp. Mình tả cho Claude, nó tạo file giúp.
- **Câu hỏi tương tác:** "Một agent chuyên soạn báo cáo thì ở bước đọc bối cảnh nó cần đọc gì, bước dùng công cụ nó cần công cụ nào?"

### Phần 2: Agent khác skill thế nào (10 phút)
- Ẩn dụ công thức và đầu bếp (phần nền mục 2). Chiếu bảng chọn.
- Cho lớp phân loại 3 tình huống, giơ tay chọn agent hay skill:
  - "Mỗi lần soạn email chào hàng đều theo đúng một mẫu" (skill, chỉ cần công thức)
  - "Muốn một nhân viên chuyên rà soát công nợ, chỉ được đọc không được sửa" (agent, cần giới hạn công cụ)
  - "Chuẩn hóa cách tóm tắt một hợp đồng" (skill)
- **Câu chốt:** "Chỉ cần công thức thì skill. Muốn giao hẳn một người có bếp riêng thì agent."

### Phần 3: Agent dùng tool và skill (5 phút)
- Giải thích dòng `tools` là cấp quyền công cụ (phần nền mục 3).
- Nói trước: lát tạo agent 1 có quyền ghi file, agent 2 chỉ được đọc, để lớp thấy tác dụng của việc khoanh công cụ.

---

## K2: Tạo agent 1, agent-soan-bao-cao (30 phút)

### Phần 1: Demo GV tạo agent (10 phút)
**PROMPT K2-1 (tạo agent 1, bản GV chạy ngay):**
```
Tạo cho tôi file .claude/agents/agent-soan-bao-cao.md, một agent chuyên soạn báo cáo và email công việc.
- name: agent-soan-bao-cao
- description: Chuyên biến số liệu hoặc ý thô thành báo cáo, đề xuất, email hoàn chỉnh theo văn phong công sở. Dùng khi cần soạn văn bản công việc từ dữ liệu có sẵn.
- tools: Read, Write, Grep, Glob
- Phần thân: đọc dữ liệu tôi chỉ, soạn theo bố cục tôi yêu cầu. Quy tắc: tiếng Việt công sở, KHÔNG dùng emoji trong email và báo cáo, KHÔNG được tạo ra con số không có trong nguồn, thiếu thì ghi [đợi bổ sung]. Nếu thiếu thông tin thì vẫn soạn đầy đủ, chỗ thiếu để [đợi bổ sung], không dừng lại hỏi tôi.
Tạo xong in lại toàn bộ nội dung file cho tôi xem.
```
- **Giải thích từng dòng cho lớp** (đây là phần dạy chính):
  - `name` để gọi đích danh.
  - `description` viết rõ "dùng khi cần soạn văn bản từ dữ liệu" nên Claude biết khi nào gọi nó.
  - `tools` có `Write` vì agent này phải ghi ra văn bản.
  - Phần thân đặt quy tắc không emoji, không bịa số. Dòng "không dừng lại hỏi" vì agent chạy ở cửa sổ riêng, không hỏi lại mình được.

### Phần 2: Thực hành, mỗi học viên tạo agent 1 (20 phút)
Cả lớp gõ đúng PROMPT K2-1 vào thư mục dự án của mình.
- Mốc cứng phút 65 (tức 01:05): mỗi người dán 3 dòng đầu file agent vừa tạo vào chat Zoom.
- **Ghi đỏ:** tạo xong CHƯA gọi vội, phần gọi và test ở K4. Nhắc: phải mở phiên mới thì Claude mới nạp agent.

---

## Nghỉ giải lao (10 phút)

---

## K3: Tạo agent 2, agent-ra-soat-khach, và tích hợp tool skill (30 phút)

### Phần 1: Demo GV tạo agent 2 (10 phút)
**PROMPT K3-1 (tạo agent 2, bản GV chạy ngay):**
```
Tạo cho tôi file .claude/agents/agent-ra-soat-khach.md, một agent chuyên rà soát hồ sơ khách hàng.
- name: agent-ra-soat-khach
- description: Chuyên đọc hồ sơ khách hàng và chỉ ra khách nào cần hành động (nhắc thanh toán, chăm sóc lại, chốt gia hạn). Dùng khi cần rà nhanh danh sách khách để không bỏ sót việc.
- tools: Read, Grep, Glob
- Phần thân: đọc toàn bộ hồ sơ khách trong thư mục tôi chỉ. Trả về một bảng: tên khách, trạng thái, việc cần làm, mức ưu tiên. Chỉ dùng thông tin có trong hồ sơ, không suy đoán. KHÔNG tự sửa hay tạo file, chỉ báo cáo.
Tạo xong in lại toàn bộ nội dung file.
```
- **So sánh 2 agent cho lớp thấy tác dụng của tools:**
  - agent-soan-bao-cao có `Write` vì phải soạn ra văn bản.
  - agent-ra-soat-khach KHÔNG có `Write`, chỉ có Read, Grep, Glob. Đây là "người kiểm tra không được cầm bút sửa bài". Dù có muốn nó cũng không sửa được hồ sơ khách. Đây chính là điều khiển agent qua công cụ.

### Phần 2: Agent dùng lại skill khi nào (5 phút)
- Nhắc lại: nếu một bước con đã có skill chuẩn thì để agent dùng lại.
- Ví dụ: agent-soan-bao-cao khi phải đọc một tài liệu dài trước khi soạn, nó có thể dùng skill tóm tắt tài liệu đã có từ buổi trước, thay vì tự đọc thô.
- **Nguyên tắc tích hợp:** skill lo cách làm một việc nhỏ, agent lo cả một vai. Đừng nhồi mọi thứ vào agent; bước nào đã có skill tốt thì để agent gọi lại.

### Phần 3: Thực hành, mỗi học viên tạo agent 2 (15 phút)
Cả lớp gõ PROMPT K3-1. Ai muốn có thể đổi agent 2 thành agent hợp nghề mình (agent rà công nợ, agent sàng lọc CV), miễn là **cố tình không cấp Write** để tập khoanh công cụ.
- Mốc cứng phút 45 (của giờ thứ hai): dán tên 2 agent vào chat Zoom.

---

## K4: Cách gọi agent và test cả 2 agent (30 phút)

### Phần 1: Ba cách gọi agent (7 phút)
1. **Gọi đích danh:** "nhờ agent-soan-bao-cao làm...". Chắc chắn đúng agent.
2. **Để Claude tự gọi:** nếu `description` rõ, Claude chính tự giao cho agent khớp việc. Không chắc chắn bằng gọi tên.
3. **Bắt buộc:** tạo hoặc sửa agent xong phải mở phiên mới thì Claude mới nạp.

### Phần 2: Test agent 1 (10 phút)
**PROMPT K4-1 (mở phiên mới rồi gọi):**
```
Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3 từ file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md. Bố cục: kết quả tháng 3, số liệu chính, vướng mắc, kế hoạch tháng 4. Chỉ dùng con số có trong file. Cuối bản liệt kê các con số đã dùng kèm dòng lấy từ file.
```
Kết quả mong đợi: báo cáo 4 phần, không emoji, có mục liệt kê nguồn số liệu (1.085 triệu tháng 3, 915 triệu tháng 2, 2 đơn chờ thanh toán, 1 đơn hủy). GV mở file gốc so 2 con số trước lớp để chứng minh agent không bịa.

### Phần 3: Test agent 2 (10 phút)
**PROMPT K4-2 (phiên mới hoặc cùng phiên):**
```
Nhờ agent-ra-soat-khach đọc các hồ sơ trong tai-lieu-phat/demo/buoi-03/phong-kinh-doanh-mau/01-khach-hang và chỉ ra khách nào cần hành động, mức ưu tiên ra sao.
```
Kết quả mong đợi: một bảng: An Phát cần nhắc thanh toán lần 3 (ưu tiên cao), Hải Nam cần chăm sóc lại sau khi hủy đơn, Minh Long cần chốt gia hạn trước 11/5/2027. Agent KHÔNG tạo hay sửa file nào (vì không có Write). GV nhấn: đây là tác dụng của việc khoanh công cụ.

### Phần 4: Thử điều mình chưa cấp quyền (3 phút, điểm nhấn)
**PROMPT K4-3:**
```
Nhờ agent-ra-soat-khach cập nhật lại file hồ sơ khách An Phát, ghi thêm dòng đã nhắc lần 3.
```
Kết quả mong đợi: agent báo nó không có quyền ghi file, chỉ rà soát và báo cáo được. GV chốt: "Thấy chưa, mình chỉ cấp Read nên nó không sửa được, dù mình có nhờ. Đó là cách agent an toàn."

---

## K5: Chốt (15 phút)

**Bốn ý cần nhớ:**
1. Agent là một nhân viên AI lập bằng một file, có 3 dòng khai báo: name, description, tools.
2. Chỉ cần công thức thì làm skill; muốn giao hẳn một vai có bếp riêng thì lập agent.
3. `tools` là cách điều khiển agent: cấp công cụ nào dùng nấy, không cấp thì không làm được, dù có nhờ.
4. Tạo agent xong phải mở phiên mới, rồi gọi đích danh cho chắc.

**Bài về nhà:**
- Lập 1 agent cho việc mình làm nhiều nhất, chọn kỹ dòng tools nên cấp gì.
- Test agent đó 3 lần trên dữ liệu thật.
- Ghi lại một việc bạn nghĩ nên làm skill (không nên làm agent), giải thích vì sao.
- Chụp kết quả gửi Zalo lớp.

**Xem trước buổi sau:** khi đã có nhiều agent, cho chúng phối hợp làm chung một quy trình (đội agent: nối chuỗi và chạy song song).

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt tóm tắt | Khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Thư mục có file gì | K0 | Liệt kê đúng file |
| K2-1 | Tạo agent-soan-bao-cao (có Write) | K2 | File agent 3 dòng khai báo, có Write |
| K3-1 | Tạo agent-ra-soat-khach (không Write) | K3 | File agent chỉ Read, Grep, Glob |
| K4-1 | Test agent 1 soạn báo cáo từ số liệu | K4 | Báo cáo 4 phần, có nguồn, không emoji |
| K4-2 | Test agent 2 rà soát khách | K4 | Bảng khách cần hành động, đúng 3 khách |
| K4-3 | Nhờ agent 2 sửa file (nó không có Write) | K4 | Agent báo không có quyền ghi |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| Tạo agent xong gọi tên không ra | Chưa mở phiên mới. Mở phiên mới rồi gọi |
| Agent đặt file sai chỗ, không nằm trong .claude/agents | Nhờ Claude đặt lại đúng đường dẫn |
| Khối YAML đầu file hỏng, thiếu dấu gạch | Nhờ Claude sửa lại định dạng, đừng để học viên tự sửa tay |
| Học viên không phân biệt được agent với skill | Quay lại ẩn dụ: công thức thì skill, đầu bếp có bếp riêng thì agent |
| Agent bịa số trong báo cáo | Kiểm phần thân có dòng không bịa số chưa. Bắt agent liệt kê nguồn rồi mở file gốc so |
| Agent 2 vẫn sửa được file dù không cấp Write | Kiểm lại dòng tools có đúng chỉ Read, Grep, Glob không. Sửa lại rồi mở phiên mới |
| Cháy giờ | Cắt phần thử chưa cấp quyền K4-3, rồi rút K1 phần 3. Không cắt K2 và K4 test |

## Ba câu kiểm hiểu cuối buổi
1. "Khi nào nên tạo agent, khi nào chỉ cần skill?" (giao hẳn một vai, cần giới hạn công cụ thì agent; chỉ cần chuẩn hóa cách làm thì skill)
2. "Ba dòng khai báo của một agent là gì, dòng nào quyết định khi nào nó tự được gọi?" (name, description, tools; description)
3. "Muốn một agent không sửa được file thì làm sao?" (không cấp Write trong dòng tools)

## Tiêu chí hoàn thành buổi
- [ ] Nói được agent khác skill thế nào, khi nào dùng cái nào
- [ ] Tạo được agent-soan-bao-cao (có Write) chạy đúng
- [ ] Tạo được agent-ra-soat-khach (không Write) chạy đúng
- [ ] Test được cả 2 agent trên file demo, kết quả đúng số liệu
- [ ] Giải thích được tools là cách khoanh công cụ cho an toàn

---

## Câu chưa rõ, cần anh chốt trước khi giãn thành bản chi tiết
1. Giữ 2 agent này (soạn báo cáo, rà soát khách) hay đổi sang bối cảnh nhân sự?
2. Có cần thêm phần demo agent dùng lại skill tóm tắt không, hay chỉ nói khái niệm?
