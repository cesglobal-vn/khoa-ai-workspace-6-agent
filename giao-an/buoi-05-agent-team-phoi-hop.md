# Outline Buổi 05 (viết cho người học mới): Đội agent phối hợp, nối chuỗi và chạy song song

> Nối tiếp Buổi 4. Học viên đã có agent và subagent. Buổi này cho nhiều agent làm chung một quy trình.
> Trọng tâm người học mới: tự trả lời được "việc này nên cho agent làm nối tiếp hay làm song song".
> Bản cũ `buoi-05-agent-team.md` KHÔNG dùng, thay bằng bản này.

## Thông tin buổi
- **Buổi:** 05 / 6
- **Khái niệm chính:** đội agent, nối chuỗi (tuần tự), chạy song song, quản lý bộ agent
- **Bối cảnh:** công việc phòng Nhân sự (đón nhân viên mới, tuyển dụng)
- **Thời lượng:** 150 phút

---

## PHẦN NỀN: người học mới cần gỡ đúng một nút thắt

Buổi 4 học viên đã biết giao việc cho một agent. Giờ có nhiều agent rồi, nút thắt mới là: **cho chúng làm nối tiếp nhau hay làm cùng lúc?**

### Đội agent là gì
Một việc lớn chia cho nhiều agent làm, mình (qua Claude) đóng vai trưởng nhóm: chia việc, rồi gom kết quả lại. Giống trưởng phòng giao việc cho nhân viên rồi tổng hợp báo cáo.

### Hai kiểu phối hợp

| Kiểu | Nghĩa là | Ví dụ nhân sự |
|---|---|---|
| **Nối chuỗi (tuần tự)** | Agent A xong, đưa kết quả cho agent B làm tiếp | Chọn ứng viên xong mới soạn thư mời người được chọn |
| **Chạy song song** | Nhiều agent làm cùng lúc, mỗi agent một phần độc lập, trưởng nhóm gom lại | Đón nhân viên mới: một agent soạn checklist, một agent soạn slide, một agent soạn email, cùng lúc |

### Sơ đồ một câu hỏi để tự quyết (chiếu lên bảng, học viên thuộc lòng)

```
Chia việc cho nhiều agent...

CÂU HỎI: Phần sau có CẦN kết quả của phần trước mới làm được không?
   CÓ CẦN   ->  NỐI CHUỖI (làm lần lượt)
   KHÔNG CẦN ->  SONG SONG (làm cùng lúc)
```

Câu thuộc lòng cho lớp: **"Người thứ hai phải chờ người thứ nhất thì làm tuần tự. Không phải chờ thì làm song song."**

### Bảng ví dụ để lớp phân loại (giơ tay)

| Việc | Nối chuỗi hay song song | Vì sao |
|---|---|---|
| Chọn 3 ứng viên rồi soạn thư mời cho 3 người đó | Nối chuỗi | Chưa chọn xong thì chưa biết mời ai |
| Tổng hợp báo cáo 3 chi nhánh, mỗi chi nhánh một thư mục | Song song | Ba phần độc lập, không chờ nhau |
| Soạn đề xuất rồi viết email trình sếp dựa trên đề xuất | Nối chuỗi | Không có đề xuất thì chưa viết email được |
| Đón nhân viên mới: checklist + slide + email chào mừng | Song song | Ba việc làm riêng được |
| Chốt số liệu quý rồi mới vẽ biểu đồ | Nối chuỗi | Chưa có số thì chưa vẽ |
| Đọc 5 hợp đồng, mỗi hợp đồng rút điều khoản thanh toán | Song song | Năm việc độc lập |

---

## Cảnh báo thật (đọc trước khi lên lớp)

- **Chạy song song kết quả không phải lúc nào cũng đều.** Có lúc Claude làm tuần tự, có lúc tự làm hết một mình. Đó là bình thường, không phải hỏng. Phải ép rõ trong prompt "gọi cùng lúc, không tự làm thay".
- **Với khối văn phòng, nối chuỗi chắc ăn hơn song song.** Nên dạy nối chuỗi là phần chính, song song là phần nâng cao.
- **Không giám sát được bên trong từng agent.** Chỉ nhận kết quả cuối. Nên bắt mỗi agent tự khai nguồn (ghi file đã đọc) để trưởng nhóm kiểm.

---

## Bối cảnh demo (nối tiếp Buổi 4)
Thư mục `demo/buoi-04/phong-nhan-su/` đã có: `01-ung-vien/` (5 CV), `02-nhan-vien-moi/`, `03-noi-quy/`. Buổi 5 dùng lại, không cần file mới.
Agent đã có từ Buổi 4: `agent-onboarding`, `agent-tuyen-dung`, `agent-dao-tao`.

---

## Timeline

| Khối | Phút | Nội dung |
|---|---|---|
| K0 | 00:00-00:12 | Mở đầu + sơ đồ "tuần tự hay song song" |
| K1 | 00:12-00:52 | Nối chuỗi 2 agent (phần chính) |
| Nghỉ | 00:52-01:02 | |
| K2 | 01:02-01:37 | Chạy song song (nâng cao, có cảnh báo) |
| K3 | 01:37-02:00 | Quản lý bộ agent + thực hành quy trình thật |
| K5 | 02:00-02:30 | Trình bày nhanh + chốt |

Mốc cứng: K1 xong trước 00:52. K1 không cắt (đây là kiểu học viên dùng thật nhiều nhất).

---

## K0: Mở đầu (12 phút)

**Nỗi đau mở màn:** "Buổi trước mỗi anh chị đã có vài agent. Nhưng đón một nhân viên mới cần làm cả checklist, cả slide, cả email, cả lịch. Chẳng lẽ ngồi gọi từng agent một? Tối nay mình cho cả đội làm cùng một lúc, và mình chỉ đóng vai trưởng nhóm."

- Chiếu sơ đồ một câu hỏi và bảng ví dụ ở phần nền, cho lớp giơ tay phân loại 3 việc.
- Nêu bản đồ tối nay: nối chuỗi trước, song song sau, rồi quản lý bộ agent.

**PROMPT K0 (giao lớp gõ, kiểm agent còn sống):**
```
Liệt kê giúp tôi các agent đang có trong thư mục .claude/agents, mỗi agent một dòng: tên và chuyên việc gì.
```
Kết quả mong đợi: liệt kê đúng các agent học viên đã tạo ở Buổi 4.

---

## K1: Nối chuỗi 2 agent (40 phút, phần chính)

**Ẩn dụ:** nối chuỗi giống dây chuyền ở công ty. Phòng tuyển dụng chọn người xong, chuyển hồ sơ sang phòng nhân sự làm thủ tục đón. Việc sau chờ việc trước.

### Phần 1: Khái niệm (6 phút)
- Nối chuỗi: agent A làm xong, kết quả của A thành đầu vào cho agent B.
- Mấu chốt: phải nói rõ "làm lần lượt, xong bước 1 mới sang bước 2", và chỉ rõ file trung gian A lưu ra để B đọc.

### Phần 2: Demo GV, chuỗi tuyển dụng tới đón nhận (10 phút)
**PROMPT K1-1:**
```
Làm lần lượt hai bước, xong bước 1 mới sang bước 2:
Bước 1: nhờ agent-tuyen-dung đọc 5 CV trong 01-ung-vien, chọn 1 người hợp nhất vị trí Sale, lưu kết quả chọn vào ket-qua/ung-vien-duoc-chon.md.
Bước 2: sau khi có file đó, nhờ agent-onboarding đọc ung-vien-duoc-chon.md và chuẩn bị gói đón cho đúng người vừa chọn: checklist, email chào mừng không emoji, lịch tuần đầu.
```
Kết quả mong đợi: có file `ket-qua/ung-vien-duoc-chon.md` (bằng chứng bước 1 chạy thật), rồi gói đón đúng tên người được chọn. GV chỉ ra: bước 2 phải chờ bước 1 vì chưa chọn xong thì chưa biết đón ai.

### Phần 3: Thực hành (24 phút)
Mỗi học viên dựng một chuỗi 2 agent cho việc của mình.

**PROMPT K1-2 (bản học viên tự điền):**
```
Làm lần lượt hai bước, xong bước 1 mới sang bước 2:
Bước 1: nhờ [agent 1] làm [việc 1], lưu kết quả vào ket-qua/[ten-file].md.
Bước 2: sau khi có file đó, nhờ [agent 2] đọc file đó và làm [việc 2].
```
*Gợi ý điền: chọn ứng viên rồi soạn thư mời; phân tích số liệu rồi viết báo cáo; rà công nợ rồi soạn email nhắc.*

Mốc cứng phút 52: mỗi người dán tên file trung gian (kết quả bước 1) vào chat Zoom.

---

## Nghỉ giải lao (10 phút)

---

## K2: Chạy song song (35 phút, nâng cao)

**Ẩn dụ:** song song giống trưởng nhóm giao ba việc độc lập cho ba người cùng lúc, ai xong việc nấy, rồi trưởng nhóm gom lại.

### Phần 1: Khái niệm + ba quy tắc (7 phút)
- Song song: nhiều agent làm cùng lúc, mỗi agent một phần không đụng phần khác.
- **Ba quy tắc bắt buộc nói ra:**
  1. Ép rõ trong prompt: "gọi cùng lúc, không tự làm thay". Nếu không, Claude có thể làm tuần tự hoặc tự làm hết.
  2. Mỗi agent một phần độc lập, không phần nào chờ phần nào.
  3. Bắt mỗi agent kết thúc bằng mục "Nguồn": file đã đọc, để trưởng nhóm kiểm khi gom.

### Phần 2: Demo GV, đội 3 agent đón nhân viên mới (13 phút)
**PROMPT K2-1:**
```
Tôi có một nhân viên mới sắp vào làm, thông tin trong 02-nhan-vien-moi. Giao cho 3 agent chạy SONG SONG, gọi cùng lúc, bạn không tự làm thay:
- agent-onboarding: soạn checklist đón và email chào mừng, không emoji.
- agent-dao-tao: soạn dàn ý buổi đào tạo nội quy cho nhân viên này từ 03-noi-quy.
- một agent tạo dàn ý nội dung cho 3 slide đón nhân viên mới.
Mỗi agent kết thúc bằng mục "Nguồn": file đã đọc. Khi cả ba xong, gom lại thành một gói đón nhân viên mới, và chỉ ra chỗ nào ba phần chưa khớp.
```
Kết quả mong đợi: một gói gồm checklist, email, dàn ý đào tạo, dàn ý slide, mỗi phần có mục Nguồn. GV chỉ ra ba phần làm riêng được nên chạy song song hợp lý.

### Phần 3: Thực hành có kiểm soát (15 phút)
**PROMPT K2-2 (bản học viên tự điền):**
```
Tôi có việc [tên việc]. Giao cho [2 tới 3] agent chạy SONG SONG, gọi cùng lúc, không tự làm thay:
- [agent 1]: [phần 1 độc lập].
- [agent 2]: [phần 2 độc lập].
Mỗi agent kết thúc bằng mục "Nguồn". Xong gom lại thành một bản chung và chỉ ra chỗ chưa khớp.
```
*Gợi ý điền: chọn việc mà các phần KHÔNG chờ nhau. Nếu phần nào phải chờ thì đó là nối chuỗi, không phải song song.*

Mốc cứng phút 37 (của giờ thứ hai): mỗi người dán bản gom vào chat Zoom.

---

## K3: Quản lý bộ agent + thực hành quy trình thật (23 phút)

### Phần 1: Quản lý bộ agent (8 phút)
Tới giờ học viên đã có 4 tới 5 agent, bắt đầu loạn. Dạy dọn dẹp.

**PROMPT K3-1:**
```
Liệt kê tất cả agent trong .claude/agents. Với mỗi agent, tóm tắt một dòng: chuyên việc gì, dùng công cụ nào. Sau đó chỉ ra hai agent nào đang mô tả chồng lấn nhau dễ gọi nhầm, và đề xuất sửa description cho tách bạch.
```
Kết quả mong đợi: bảng các agent, và chỉ ra chỗ chồng lấn nếu có.
- Quy tắc đặt tên: mỗi agent một việc rõ, description ghi rõ "dùng khi nào" để trưởng nhóm gọi đúng.

### Phần 2: Thực hành quy trình thật của mình (15 phút)
Học viên chọn một quy trình công việc thật nhiều bước, tự quyết chỗ nào nối chuỗi chỗ nào song song, viết prompt, chạy.
- Bắt buộc: nói được vì sao chọn kiểu đó cho từng đoạn.
- Đây cũng là bước tập dượt cho capstone Buổi 6.

---

## K5: Trình bày nhanh và chốt (30 phút)

### Trình bày nhanh (15 phút)
Gọi 3 tới 4 học viên share màn hình 3 phút: quy trình của mình, đoạn nào nối chuỗi đoạn nào song song, vì sao. Cả lớp học lẫn nhau.

### Chốt (15 phút)
**Bốn ý cần nhớ:**
1. Đội agent: mình đóng vai trưởng nhóm, chia việc rồi gom kết quả.
2. Câu quyết định: người sau phải chờ người trước thì nối chuỗi, không chờ thì song song.
3. Song song phải ép "gọi cùng lúc, không tự làm thay", và bắt mỗi agent khai nguồn.
4. Nhiều agent thì phải dọn: mỗi agent một việc rõ, tránh mô tả chồng lấn.

**Bài về nhà:**
- Dựng một chuỗi 2 agent cho việc thật của mình, chạy thử.
- Dựng một đội song song cho một việc có các phần độc lập.
- Nghĩ trước một quy trình lớn của mình để làm capstone Buổi 6.
- Chụp kết quả gửi Zalo lớp.

**Xem trước Buổi 6 (capstone):** ghép tất cả những gì đã học (CLAUDE.md, skill, MCP, agent, đội agent) thành một quy trình công việc thật, chạy đầu-cuối rồi trình bày.

---

## Bảng prompt tổng hợp (tra nhanh)

| # | Prompt tóm tắt | Khối | Kết quả mong đợi |
|---|---|---|---|
| K0 | Liệt kê agent đang có | K0 | Danh sách agent của học viên |
| K1-1 | Chuỗi: chọn ứng viên rồi đón nhận | K1 | File trung gian + gói đón đúng người |
| K1-2 | Chuỗi 2 agent của học viên | K1 | File trung gian + kết quả bước 2 |
| K2-1 | Song song 3 agent đón nhân viên mới | K2 | Gói đón, mỗi phần có mục Nguồn |
| K2-2 | Song song của học viên | K2 | Bản gom, chỉ ra chỗ chưa khớp |
| K3-1 | Liệt kê và tìm agent chồng lấn | K3 | Bảng agent, chỗ chồng lấn |

## Tình huống hay gặp và cách xử lý

| Tình huống | Cách xử lý |
|---|---|
| Học viên không biết chọn nối chuỗi hay song song | Quay lại câu hỏi: người sau có phải chờ người trước không |
| Chạy song song nhưng Claude làm tuần tự | Bình thường. Nếu muốn ép, thêm "gọi cùng lúc, không tự làm thay". Nếu vẫn tuần tự thì chấp nhận, kết quả vẫn đúng |
| Bước 2 nối chuỗi chạy khi bước 1 chưa xong | Nhấn trong prompt "xong bước 1 mới sang bước 2", và chỉ rõ file trung gian bước 1 phải lưu ra |
| Gom kết quả bị thiếu một phần | Nhắc trưởng nhóm gom đủ, kiểm mục Nguồn của từng agent |
| Số liệu giữa các agent lệch nhau | Đây là lý do bắt khai nguồn. Mở file gốc so lại |
| Hai agent bị gọi nhầm lẫn nhau | Description chồng lấn. Sửa cho mỗi agent một việc rõ |
| Cháy giờ | Cắt K2 song song xuống chỉ demo GV, bỏ thực hành song song. Không cắt K1 nối chuỗi |

## Ba câu kiểm hiểu cuối buổi
1. "Khi nào cho agent làm nối tiếp, khi nào cho làm cùng lúc?" (người sau chờ người trước thì nối tiếp, không chờ thì cùng lúc)
2. "Chạy song song phải ép câu gì trong prompt?" (gọi cùng lúc, không tự làm thay)
3. "Vì sao bắt mỗi agent khai nguồn?" (để trưởng nhóm kiểm, không giám sát được bên trong agent)

## Tiêu chí hoàn thành buổi
- [ ] Phân loại được một việc thật thành nối chuỗi hay song song, giải thích được vì sao
- [ ] Chạy được một chuỗi 2 agent, có file trung gian
- [ ] Chạy được một đội song song, gom được bản chung
- [ ] Dọn được bộ agent, chỉ ra chỗ chồng lấn nếu có

---

## Câu chưa rõ, cần anh chốt trước khi giãn thành bản chi tiết
1. Có giữ bối cảnh nhân sự không, hay đổi sang bối cảnh khác?
2. Song song cho lớp thực hành thật (như outline), hay chỉ GV demo cho an toàn?
3. Buổi 6 capstone anh muốn học viên trình bày kiểu nào: nộp file, hay share màn hình?
