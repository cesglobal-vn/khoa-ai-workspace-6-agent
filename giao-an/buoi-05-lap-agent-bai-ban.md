# Outline Buổi 05: Lập agent bài bản và cho đội agent phối hợp

> Buổi này gộp hai phần: (A) lập agent cho chắc, (B) cho chính hai agent vừa tạo phối hợp làm việc.
> Mạch: agent là gì, agent khác skill thế nào, tạo 2 agent, gọi và test, rồi cho 2 agent đó nối chuỗi và chạy song song.
> Lý do gộp: Buổi 4 chưa dạy kỹ agent, và lớp chưa có agent nào để chạy đội agent.

## Thông tin buổi
- **Buổi:** 05 / 6
- **Khái niệm chính:** agent là gì, agent với skill, tạo agent, tools, cách gọi, test; đội agent nối chuỗi và song song
- **Bối cảnh:** dùng file demo có sẵn (số liệu bán hàng, hồ sơ khách hàng)
- **Thời lượng:** 150 phút

---

## PHẦN NỀN cho người học mới

### 1. Agent là gì
Agent là **một nhân viên AI có bản mô tả công việc riêng**, lập bằng một file. Mình đặt tên, ghi rõ nó chuyên việc gì, cho dùng công cụ nào, dặn quy tắc gì. Mỗi khi nhận việc, nó chạy 4 bước:
```
1. NHẬN VIỆC     Bạn giao yêu cầu.
2. ĐỌC BỐI CẢNH  Agent đọc mô tả của chính nó, đọc file bạn chỉ, nạp skill nếu cần.
3. DÙNG CÔNG CỤ  Agent dùng đúng công cụ được cấp làm từng bước.
4. TRẢ KẾT QUẢ   Agent trả kết quả.
```
File agent gồm 3 dòng khai báo: `name` (tên gọi), `description` (chuyên gì, dùng khi nào, quyết định khi nào tự được gọi), `tools` (công cụ được phép dùng), và phần thân dặn việc.

### 2. Khi nào tạo agent, khi nào tạo skill
- **Skill là tờ công thức.** Claude chính cầm công thức tự nấu.
- **Agent là thuê hẳn một đầu bếp** chuyên món đó, có bếp riêng, dụng cụ riêng, giao hẳn việc rồi nhận món.

| Bạn muốn | Nên dùng |
|---|---|
| Chuẩn hóa cách làm một việc, Claude chính tự làm là được | Skill |
| Một quy trình ngắn dùng lại nhiều lần | Skill |
| Giao hẳn một vai lặp lại cho một nhân viên riêng | Agent |
| Giới hạn công cụ cho an toàn (ví dụ chỉ đọc, không sửa) | Agent |
| Việc nặng, muốn chạy ở cửa sổ ngữ cảnh riêng | Agent |

Câu chốt: **"Chỉ cần công thức thì skill. Muốn giao hẳn cho người có bếp riêng thì agent."**

### 3. Agent điều khiển tool và skill thế nào
- **Tool:** dòng `tools` là danh sách công cụ agent được dùng. Cấp `Read` thì đọc được, cấp `Write` thì ghi được, không cấp `Write` thì không sửa được dù có nhờ. Đây là cách điều khiển agent qua công cụ.
- **Skill:** agent dùng lại được skill đã có. Bước con nào đã có skill chuẩn thì để agent gọi lại, đừng viết lại vào agent. Skill lo cách làm một việc nhỏ, agent lo cả một vai.

### 4. Đội agent là gì, nối chuỗi hay song song
Khi có nhiều agent, mình đóng vai trưởng nhóm: chia việc, gom kết quả. Hai kiểu phối hợp:

| Kiểu | Nghĩa là | Ví dụ |
|---|---|---|
| **Nối chuỗi (tuần tự)** | Agent A xong đưa kết quả cho agent B | Rà ra khách cần nhắc xong mới soạn email nhắc |
| **Chạy song song** | Nhiều agent làm cùng lúc, mỗi agent một phần độc lập | Một agent rà khách, một agent soạn báo cáo, cùng lúc |

Sơ đồ một câu hỏi (chiếu lên bảng):
```
CÂU HỎI: Phần sau có CẦN kết quả phần trước mới làm được không?
   CÓ CẦN    ->  NỐI CHUỖI (làm lần lượt)
   KHÔNG CẦN ->  SONG SONG (làm cùng lúc)
```
Câu thuộc lòng: **"Người sau phải chờ người trước thì làm tuần tự. Không phải chờ thì làm song song."**

**Bảng ví dụ để lớp phân loại (chiếu lên, cho giơ tay):**

| Việc | Nối chuỗi hay song song | Vì sao |
|---|---|---|
| Chọn 3 ứng viên rồi soạn thư mời cho 3 người đó | Nối chuỗi | Chưa chọn xong thì chưa biết mời ai |
| Tổng hợp báo cáo 3 chi nhánh, mỗi chi nhánh một thư mục | Song song | Ba phần độc lập, không chờ nhau |
| Soạn đề xuất rồi viết email trình sếp dựa trên đề xuất | Nối chuỗi | Không có đề xuất thì chưa viết email được |
| Đón nhân viên mới: checklist + slide + email chào mừng | Song song | Ba việc làm riêng được |
| Chốt số liệu quý rồi mới vẽ biểu đồ | Nối chuỗi | Chưa có số thì chưa vẽ |
| Đọc 5 hợp đồng, mỗi hợp đồng rút điều khoản thanh toán | Song song | Năm việc độc lập |
| Rà khách cần nhắc rồi soạn email nhắc đúng khách đó | Nối chuỗi | Chưa rà xong thì chưa biết nhắc ai |

---

## Bối cảnh demo (file có sẵn, chạy được ngay)
- `tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md` : số liệu bán hàng tháng 3 thô.
- `tai-lieu-phat/demo/buoi-03/phong-kinh-doanh-mau/01-khach-hang/` : 3 hồ sơ khách (Minh Long, Hải Nam, An Phát).

Hai agent sẽ lập rồi cho phối hợp:
- **agent-soan-bao-cao** : soạn báo cáo và email từ dữ liệu. Có quyền Write.
- **agent-ra-soat-khach** : đọc hồ sơ khách, chỉ ra ai cần hành động. Chỉ đọc, KHÔNG Write.

---

## Timeline

| Khối | Phút | Nội dung |
|---|---|---|
| K0 | 00:00-00:08 | Mở đầu, bản đồ buổi |
| K1 | 00:08-00:30 | Agent là gì + agent vs skill + tools |
| K2 | 00:30-00:58 | Tạo 2 agent (giải thích từng dòng) |
| Nghỉ | 00:58-01:08 | |
| K3 | 01:08-01:35 | Gọi và test cả 2 agent |
| K4 | 01:35-02:05 | Đội agent: nối chuỗi 2 agent vừa tạo |
| K5 | 02:05-02:30 | Đội agent: song song + khi nào dùng cái nào + chốt |

Mốc cứng: K2 xong trước 00:58, K3 xong trước 01:35. K2, K3, K4 không cắt.

---

## K0: Mở đầu (8 phút)

**Lời dẫn GV:** "Tối nay mình làm trọn một mạch: hiểu agent là gì, tự tay lập hai agent, test cho chạy, rồi cho chính hai agent đó phối hợp làm chung một việc. Xong buổi, mỗi anh chị có hai nhân viên AI biết làm việc cùng nhau."
- Nêu bản đồ: agent vs skill, tạo 2 agent, test, rồi nối chuỗi và song song.
- **PROMPT K0:**
```
Thư mục này đang có những file và thư mục con nào? Trả lời ngắn gọn.
```

---

## K1: Agent là gì, agent vs skill, tools (22 phút)

### Phần 1: Agent là gì (8 phút)
- Trình bày 4 bước hoạt động và 3 dòng khai báo (phần nền mục 1), vẽ lên bảng.
- Nhấn: agent chỉ là một file, mình tả cho Claude nó tạo giúp.
- **Câu hỏi:** "Agent chuyên soạn báo cáo thì bước đọc bối cảnh cần đọc gì, bước dùng công cụ cần công cụ nào?"

### Phần 2: Agent khác skill (9 phút)
- Ẩn dụ công thức và đầu bếp, chiếu bảng chọn (phần nền mục 2).
- Cho lớp phân loại 3 tình huống, giơ tay agent hay skill:
  - "Mỗi lần soạn email chào hàng theo một mẫu" (skill)
  - "Một nhân viên chuyên rà công nợ, chỉ được đọc không được sửa" (agent)
  - "Chuẩn hóa cách tóm tắt hợp đồng" (skill)

### Phần 3: Agent dùng tool và skill (5 phút)
- Dòng `tools` là cấp quyền công cụ (phần nền mục 3).
- Báo trước: agent 1 có Write, agent 2 không có Write, để lát thấy tác dụng khoanh công cụ.

---

## K2: Tạo 2 agent (28 phút)

### Phần 1: Demo GV tạo agent 1 (7 phút)
**PROMPT K2-1 (agent 1, bản GV chạy ngay):**
```
Tạo cho tôi file .claude/agents/agent-soan-bao-cao.md, một agent chuyên soạn báo cáo và email công việc.
- name: agent-soan-bao-cao
- description: Chuyên biến số liệu hoặc ý thô thành báo cáo, đề xuất, email hoàn chỉnh theo văn phong công sở. Dùng khi cần soạn văn bản công việc từ dữ liệu có sẵn.
- tools: Read, Write, Grep, Glob
- Phần thân: đọc dữ liệu tôi chỉ, soạn theo bố cục tôi yêu cầu. Quy tắc: tiếng Việt công sở, KHÔNG emoji trong email và báo cáo, KHÔNG tạo ra con số không có trong nguồn, thiếu thì ghi [đợi bổ sung]. Nếu thiếu thông tin thì vẫn soạn đầy đủ, chỗ thiếu để [đợi bổ sung], không dừng lại hỏi tôi.
Tạo xong in lại toàn bộ nội dung file.
```
Giải thích từng dòng: `description` rõ nên Claude biết khi nào gọi; `tools` có Write vì phải ghi văn bản; phần thân đặt quy tắc không emoji, không bịa số, không dừng lại hỏi (vì agent chạy cửa sổ riêng, không hỏi lại được).

### Phần 2: Demo GV tạo agent 2 (7 phút)
**PROMPT K2-2 (agent 2, bản GV chạy ngay):**
```
Tạo cho tôi file .claude/agents/agent-ra-soat-khach.md, một agent chuyên rà soát hồ sơ khách hàng.
- name: agent-ra-soat-khach
- description: Chuyên đọc hồ sơ khách hàng và chỉ ra khách nào cần hành động (nhắc thanh toán, chăm sóc lại, chốt gia hạn). Dùng khi cần rà nhanh danh sách khách để không bỏ sót việc.
- tools: Read, Grep, Glob
- Phần thân: đọc toàn bộ hồ sơ khách trong thư mục tôi chỉ. Trả về một bảng: tên khách, trạng thái, việc cần làm, mức ưu tiên. Chỉ dùng thông tin có trong hồ sơ, không suy đoán. KHÔNG tự sửa hay tạo file, chỉ báo cáo.
Tạo xong in lại toàn bộ nội dung file.
```
So sánh 2 agent: agent 1 có `Write` để soạn văn bản; agent 2 KHÔNG có `Write`, chỉ Read/Grep/Glob, là "người kiểm tra không được cầm bút". Dù nhờ nó cũng không sửa được hồ sơ. Đây là điều khiển agent qua công cụ.

### Phần 3: Thực hành, cả lớp tạo 2 agent (14 phút)
Gõ K2-1 rồi K2-2 vào thư mục dự án của mình.
- Mốc cứng phút 58: dán tên 2 agent vào chat Zoom.
- **Ghi đỏ:** tạo xong chưa gọi vội. Phải mở phiên mới thì Claude mới nạp agent.

---

## Nghỉ giải lao (10 phút)

---

## K3: Gọi và test cả 2 agent (27 phút)

### Phần 1: Ba cách gọi agent (5 phút)
1. Gọi đích danh: "nhờ agent-soan-bao-cao làm...". Chắc chắn nhất.
2. Để Claude tự gọi nếu description rõ. Không chắc bằng gọi tên.
3. Bắt buộc: tạo hoặc sửa agent xong phải mở phiên mới.

### Phần 2: Test agent 1 (9 phút)
**PROMPT K3-1 (mở phiên mới rồi gọi):**
```
Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3 từ file tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md. Bố cục: kết quả tháng 3, số liệu chính, vướng mắc, kế hoạch tháng 4. Chỉ dùng con số có trong file. Cuối bản liệt kê các con số đã dùng kèm dòng lấy từ file.
```
Kết quả mong đợi: báo cáo 4 phần, không emoji, có mục nguồn số liệu (1.085 triệu tháng 3, 915 triệu tháng 2, 2 đơn chờ thanh toán, 1 đơn hủy). GV mở file gốc so 2 con số trước lớp.

### Phần 3: Test agent 2 (8 phút)
**PROMPT K3-2:**
```
Nhờ agent-ra-soat-khach đọc các hồ sơ trong tai-lieu-phat/demo/buoi-03/phong-kinh-doanh-mau/01-khach-hang và chỉ ra khách nào cần hành động, mức ưu tiên ra sao.
```
Kết quả mong đợi: bảng: An Phát cần nhắc thanh toán lần 3 (ưu tiên cao), Hải Nam chăm sóc lại sau khi hủy đơn, Minh Long chốt gia hạn trước 11/5/2027. Agent không tạo hay sửa file nào.

### Phần 4: Thử điều chưa cấp quyền (5 phút, điểm nhấn)
**PROMPT K3-3:**
```
Nhờ agent-ra-soat-khach cập nhật file hồ sơ khách An Phát, ghi thêm dòng đã nhắc lần 3.
```
Kết quả mong đợi: agent báo không có quyền ghi, chỉ rà soát được. GV chốt: "Mình chỉ cấp Read nên nó không sửa được dù mình nhờ. Đó là agent an toàn."

---

## K4: Đội agent, nối chuỗi 2 agent vừa tạo (30 phút)

**Ẩn dụ:** giờ mình có hai nhân viên rồi, cho họ làm dây chuyền. Người rà soát tìm ra khách cần nhắc, chuyển sang người soạn thảo viết email nhắc. Việc sau chờ việc trước.

### Phần 1: Khái niệm nối chuỗi (5 phút)
- Nối chuỗi: agent A xong, kết quả thành đầu vào cho agent B.
- Mấu chốt: nói rõ "làm lần lượt, xong bước 1 mới sang bước 2", và chỉ rõ file trung gian A lưu ra để B đọc.

### Phần 2: Demo GV, chuỗi rà khách tới soạn email nhắc (10 phút)
**PROMPT K4-1:**
```
Làm lần lượt hai bước, xong bước 1 mới sang bước 2:
Bước 1: nhờ agent-ra-soat-khach đọc thư mục tai-lieu-phat/demo/buoi-03/phong-kinh-doanh-mau/01-khach-hang, chỉ ra khách CẦN NHẮC THANH TOÁN GẤP NHẤT, lưu kết quả vào ket-qua/khach-can-nhac.md.
Bước 2: sau khi có file đó, nhờ agent-soan-bao-cao đọc ket-qua/khach-can-nhac.md và soạn một email nhắc thanh toán gửi đúng khách đó, văn phong công sở, không emoji.
```
Kết quả mong đợi: có file `ket-qua/khach-can-nhac.md` (agent 2 chỉ ra An Phát), rồi agent 1 soạn email nhắc thanh toán gửi An Phát. GV chỉ ra: bước 2 phải chờ bước 1, vì chưa biết khách nào thì chưa soạn email được. Đây đúng là nối chuỗi.

### Phần 3: Thực hành nối chuỗi (15 phút)
**PROMPT K4-2 (bản học viên):**
```
Làm lần lượt hai bước, xong bước 1 mới sang bước 2:
Bước 1: nhờ [agent 1] làm [việc 1], lưu kết quả vào ket-qua/[ten-file].md.
Bước 2: sau khi có file đó, nhờ [agent 2] đọc file đó và làm [việc 2].
```
*Gợi ý điền: rà công nợ rồi soạn email nhắc; chọn ứng viên rồi soạn thư mời; phân tích số liệu rồi viết báo cáo.*
Mốc cứng phút 65 (giờ hai): dán tên file trung gian vào chat Zoom.

---

## K5: Đội agent song song, khi nào dùng cái nào, và chốt (25 phút)

### Phần 1: Chạy song song (10 phút)
**Ẩn dụ:** song song là giao hai việc độc lập cho hai người cùng lúc, rồi gom lại.
- **Ba quy tắc:** ép rõ "gọi cùng lúc, không tự làm thay"; mỗi agent một phần độc lập; bắt mỗi agent khai nguồn.
- **Demo GV, PROMPT K5-1:**
```
Giao SONG SONG hai việc độc lập, gọi cùng lúc, không tự làm thay:
- agent-ra-soat-khach: rà thư mục 01-khach-hang, chỉ ra khách cần hành động.
- agent-soan-bao-cao: soạn báo cáo bán hàng tháng 3 từ tai-lieu-phat/demo/buoi-04/so-lieu-ban-hang-thang.md.
Mỗi agent kết thúc bằng mục "Nguồn": file đã đọc. Xong gom hai kết quả thành một bản tình hình chung.
```
Kết quả mong đợi: hai phần chạy riêng (rà khách và báo cáo), gom thành một bản. GV nhấn: hai việc này không chờ nhau nên chạy song song được.

### Phần 2: Khi nào tuần tự, khi nào song song (7 phút)
- Chiếu sơ đồ một câu hỏi (phần nền mục 4).
- Cho lớp phân loại nhanh 3 việc: chọn người rồi soạn thư mời (tuần tự); tổng hợp 3 chi nhánh mỗi cái một thư mục (song song); chốt số liệu rồi vẽ biểu đồ (tuần tự).
- **Cảnh báo:** song song kết quả không phải lúc nào cũng đều, Claude có khi làm tuần tự. Bình thường. Nối chuỗi chắc ăn hơn.

### Phần 3: Chốt (8 phút)
**Năm ý cần nhớ:**
1. Agent là nhân viên AI lập bằng một file, có name, description, tools.
2. Chỉ cần công thức thì skill; giao hẳn một vai có bếp riêng thì agent.
3. `tools` điều khiển agent: cấp gì dùng nấy, không cấp thì không làm được.
4. Người sau phải chờ người trước thì nối chuỗi, không chờ thì song song.
5. Tạo agent xong phải mở phiên mới, gọi đích danh cho chắc.

**Bài về nhà:**
- Lập 1 agent cho việc mình làm nhiều nhất, chọn kỹ tools.
- Dựng một chuỗi 2 agent cho việc thật của mình, chạy thử.
- Ghi lại một việc nên làm skill (không nên làm agent), giải thích vì sao.
- Chụp kết quả gửi Zalo lớp.

**Xem trước Buổi 6 (capstone):** ghép tất cả (CLAUDE.md, skill, MCP, agent, đội agent) thành một quy trình công việc thật, chạy đầu-cuối rồi trình bày.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt tóm tắt | Khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Thư mục có file gì | K0 | Liệt kê đúng file |
| K2-1 | Tạo agent-soan-bao-cao (có Write) | K2 | File agent, có Write |
| K2-2 | Tạo agent-ra-soat-khach (không Write) | K2 | File agent, chỉ Read/Grep/Glob |
| K3-1 | Test agent 1 soạn báo cáo | K3 | Báo cáo 4 phần, có nguồn, không emoji |
| K3-2 | Test agent 2 rà khách | K3 | Bảng 3 khách cần hành động |
| K3-3 | Nhờ agent 2 sửa file (không có Write) | K3 | Agent báo không có quyền ghi |
| K4-1 | Nối chuỗi: rà khách rồi soạn email nhắc | K4 | File trung gian + email nhắc An Phát |
| K4-2 | Nối chuỗi của học viên | K4 | File trung gian + kết quả bước 2 |
| K5-1 | Song song: rà khách và soạn báo cáo | K5 | Hai phần + bản gom |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| Tạo agent xong gọi tên không ra | Chưa mở phiên mới. Mở phiên mới rồi gọi |
| Agent đặt file sai chỗ | Nhờ Claude đặt lại đúng .claude/agents |
| Khối YAML đầu file hỏng | Nhờ Claude sửa định dạng, đừng để học viên tự sửa tay |
| Không phân biệt được agent với skill | Ẩn dụ: công thức thì skill, đầu bếp có bếp riêng thì agent |
| Agent bịa số | Kiểm phần thân có dòng không bịa số. Bắt liệt kê nguồn, mở file gốc so |
| Agent 2 vẫn sửa được file dù không cấp Write | Kiểm lại dòng tools, sửa rồi mở phiên mới |
| Bước 2 nối chuỗi chạy khi bước 1 chưa xong | Nhấn "xong bước 1 mới sang bước 2", chỉ rõ file trung gian |
| Song song mà Claude làm tuần tự | Bình thường. Thêm "gọi cùng lúc, không tự làm thay". Vẫn tuần tự thì chấp nhận |
| Cháy giờ | Cắt K5 song song còn demo GV, bỏ K3-3. Không cắt K2, K3 test, K4 nối chuỗi |

## Ba câu kiểm hiểu cuối buổi
1. "Khi nào tạo agent, khi nào chỉ cần skill?"
2. "Muốn một agent không sửa được file thì làm sao?" (không cấp Write trong tools)
3. "Khi nào cho agent làm nối tiếp, khi nào làm cùng lúc?" (người sau chờ người trước thì nối tiếp)

## Tiêu chí hoàn thành buổi
- [ ] Nói được agent khác skill thế nào, khi nào dùng cái nào
- [ ] Tạo được 2 agent (một có Write, một không Write), test chạy đúng
- [ ] Giải thích được tools là cách khoanh công cụ cho an toàn
- [ ] Chạy được một chuỗi 2 agent, có file trung gian
- [ ] Chạy được hoặc hiểu được đội agent song song

---

## Câu chưa rõ, cần anh chốt trước khi giãn thành bản chi tiết
1. Giữ 2 agent này (soạn báo cáo, rà soát khách) hay đổi sang bối cảnh nhân sự?
2. Phần song song cho lớp thực hành thật hay chỉ GV demo cho an toàn?
