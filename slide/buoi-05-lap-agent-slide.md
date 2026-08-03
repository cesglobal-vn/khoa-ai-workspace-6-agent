# Nội dung slide Buổi 5: Lập agent bài bản và cho đội agent phối hợp

> Dùng cho GV dựng slide. Kiểu CES: nền trắng, chữ đậm màu navy, điểm nhấn teal/gold.
> Mỗi "---" là 1 slide. Phần [Ghi chú GV] không in lên slide. Tổng: 24 slide cho buổi 150 phút.

---

## Slide 1: Slide tiêu đề

**KHÓA AI WORKSPACE**
Làm chủ Agent với Claude Code

**Buổi 5: Lập agent và cho đội agent phối hợp**

CES Global | Trung tâm Đào tạo & Ứng dụng Công nghệ

[Ghi chú GV: buổi thực chiến. Trấn an lớp: tối nay tự tay lập 2 agent, cho chúng làm việc cùng nhau.]

---

## Slide 2: Hôm nay cả lớp làm được gì

- Hiểu **agent** là gì, khác **skill** ra sao
- Tự tay lập **2 agent** cho công việc thật
- Gọi và **test** cho agent chạy
- Cho 2 agent **nối chuỗi** và **chạy song song**
- Biết cách **khoanh công cụ** cho agent an toàn

Tất cả bằng tiếng Việt, không cần biết lập trình.

---

## Slide 3: Agent là gì

Một **nhân viên AI có bản mô tả công việc riêng**, lập bằng một file.

Bốn bước hoạt động:

```
1. NHẬN VIỆC      Bạn giao yêu cầu
2. ĐỌC BỐI CẢNH   Agent đọc mô tả của nó, đọc file bạn chỉ
3. DÙNG CÔNG CỤ   Làm từng bước bằng công cụ được cấp
4. TRẢ KẾT QUẢ    Trả lại kết quả cho bạn
```

[Ghi chú GV: vẽ 4 bước lên bảng. Nhấn: agent chỉ là một file, mình tả cho Claude tạo giúp.]

---

## Slide 4: Ba dòng khai báo của agent

Một file agent có 3 dòng khai báo và phần thân:

- **name**: tên gọi của agent
- **description**: chuyên việc gì, dùng khi nào
- **tools**: công cụ được phép dùng
- **Phần thân**: dặn việc, đặt quy tắc

Description càng rõ, Claude càng biết khi nào tự gọi agent.

---

## Slide 5: Agent khác skill thế nào

- **Skill là tờ công thức.** Claude chính cầm công thức tự nấu.
- **Agent là thuê hẳn một đầu bếp** chuyên món đó, có bếp riêng, dụng cụ riêng.

| Bạn muốn | Nên dùng |
|---|---|
| Chuẩn hóa cách làm, Claude tự làm là được | **Skill** |
| Quy trình ngắn dùng lại nhiều lần | **Skill** |
| Giao hẳn một vai cho nhân viên riêng | **Agent** |
| Giới hạn công cụ cho an toàn (chỉ đọc) | **Agent** |

Câu chốt: **"Cần công thức thì skill. Giao hẳn cho người có bếp riêng thì agent."**

---

## Slide 6: Tools điều khiển agent

Dòng **tools** là danh sách công cụ agent được dùng. Cấp gì dùng nấy.

- Cấp **Read** thì đọc được
- Cấp **Write** thì ghi được
- **Không cấp Write** thì không sửa được dù có nhờ

```
tools: Read, Write, Grep, Glob   ->  đọc và ghi được
tools: Read, Grep, Glob          ->  chỉ đọc, không sửa
```

Đây là cách khoanh công cụ cho agent an toàn.

---

## Slide 7: Tạo agent 1, agent soạn báo cáo

**Prompt:**
```
Tạo file .claude/agents/agent-soan-bao-cao.md
- name: agent-soan-bao-cao
- description: biến số liệu, ý thô thành báo cáo,
  email công sở. Dùng khi cần soạn văn bản từ dữ liệu.
- tools: Read, Write, Grep, Glob
- Thân: tiếng Việt công sở, không emoji, không bịa số,
  thiếu thì ghi [đợi bổ sung], không dừng lại hỏi.
Tạo xong in lại toàn bộ file.
```

**Kết quả mong đợi:** file agent có Write để ghi văn bản.

---

## Slide 8: Giải thích agent 1 từng dòng

- **description rõ** nên Claude biết khi nào gọi
- **tools có Write** vì phải ghi ra văn bản
- **Phần thân** đặt quy tắc: không emoji, không bịa số

Vì sao "không dừng lại hỏi"?

Agent chạy ở **cửa sổ riêng**, không hỏi lại được. Thiếu gì cứ để `[đợi bổ sung]`.

---

## Slide 9: Tạo agent 2, agent rà soát khách

**Prompt:**
```
Tạo file .claude/agents/agent-ra-soat-khach.md
- name: agent-ra-soat-khach
- description: đọc hồ sơ khách, chỉ ra khách nào
  cần hành động. Dùng khi cần rà nhanh để không bỏ sót.
- tools: Read, Grep, Glob
- Thân: trả về bảng tên khách, trạng thái, việc cần làm,
  mức ưu tiên. Chỉ dùng thông tin có thật. KHÔNG sửa file.
Tạo xong in lại toàn bộ file.
```

**Kết quả mong đợi:** file agent chỉ có Read/Grep/Glob, không Write.

---

## Slide 10: So sánh tools của 2 agent

| Agent | tools | Làm được gì |
|---|---|---|
| **agent-soan-bao-cao** | Read, Write, Grep, Glob | Đọc và **ghi** văn bản |
| **agent-ra-soat-khach** | Read, Grep, Glob | Chỉ **đọc**, không sửa |

Agent 2 là **"người kiểm tra không được cầm bút"**. Dù có nhờ, nó cũng không sửa được hồ sơ.

Đây chính là điều khiển agent qua công cụ.

---

## Slide 11: Ba cách gọi agent

1. **Gọi đích danh**: "nhờ agent-soan-bao-cao làm...". Chắc chắn nhất.
2. **Để Claude tự gọi** nếu description rõ. Không chắc bằng gọi tên.
3. **Bắt buộc**: tạo hoặc sửa agent xong phải **mở phiên mới**.

**Ghi đỏ:** tạo xong chưa gọi vội. Phải mở phiên mới thì Claude mới nạp agent.

[Ghi chú GV: đây là lỗi hay gặp nhất. Nhấn mạnh mở phiên mới.]

---

## Slide 12: Test agent 1, soạn báo cáo

**Prompt:**
```
Nhờ agent-soan-bao-cao soạn báo cáo bán hàng tháng 3 từ
file so-lieu-ban-hang-thang.md. Bố cục: kết quả, số liệu
chính, vướng mắc, kế hoạch tháng 4. Chỉ dùng con số có
trong file. Cuối bản liệt kê các con số đã dùng.
```

**Kết quả mong đợi:** báo cáo 4 phần, không emoji, có mục nguồn số liệu.

[Ghi chú GV: mở file gốc so 2 con số trước lớp cho lớp tin.]

---

## Slide 13: Test agent 2, rà soát khách

**Prompt:**
```
Nhờ agent-ra-soat-khach đọc các hồ sơ trong thư mục
01-khach-hang và chỉ ra khách nào cần hành động,
mức ưu tiên ra sao.
```

**Kết quả mong đợi:** bảng 3 khách:

- An Phát: nhắc thanh toán lần 3 (ưu tiên cao)
- Hải Nam: chăm sóc lại sau khi hủy đơn
- Minh Long: chốt gia hạn

Agent không tạo hay sửa file nào.

---

## Slide 14: Thử điều chưa cấp quyền

**Prompt:**
```
Nhờ agent-ra-soat-khach cập nhật hồ sơ khách An Phát,
ghi thêm dòng đã nhắc lần 3.
```

**Kết quả mong đợi:** agent báo **không có quyền ghi**, chỉ rà soát được.

Chốt: **"Mình chỉ cấp Read nên nó không sửa được dù mình nhờ. Đó là agent an toàn."**

---

## Slide 15: Nghỉ giải lao 10 phút

Phần sau: cho 2 agent phối hợp làm việc cùng nhau.

Ai chưa xong 2 agent, tranh thủ nhờ trợ giảng.

---

## Slide 16: Đội agent là gì

Khi có nhiều agent, mình đóng vai **trưởng nhóm**: chia việc, gom kết quả.

- Người rà soát tìm ra khách cần nhắc
- Chuyển sang người soạn thảo viết email nhắc
- Trưởng nhóm gom lại thành kết quả chung

Giờ mình có 2 nhân viên rồi, cho họ làm chung một việc.

---

## Slide 17: Nối chuỗi hay song song

Hai kiểu phối hợp:

- **Nối chuỗi (tuần tự)**: agent A xong đưa kết quả cho agent B
- **Chạy song song**: nhiều agent làm cùng lúc, mỗi agent một phần độc lập

Sơ đồ một câu hỏi:

```
Phần sau có CẦN kết quả phần trước mới làm được không?
   CÓ CẦN     ->  NỐI CHUỖI (làm lần lượt)
   KHÔNG CẦN  ->  SONG SONG (làm cùng lúc)
```

**"Người sau phải chờ người trước thì tuần tự. Không phải chờ thì song song."**

---

## Slide 18: Cùng phân loại

| Việc | Kiểu | Vì sao |
|---|---|---|
| Chọn ứng viên rồi soạn thư mời | Nối chuỗi | Chưa chọn xong chưa biết mời ai |
| Tổng hợp 3 chi nhánh, mỗi cái một thư mục | Song song | Ba phần độc lập |
| Chốt số liệu quý rồi vẽ biểu đồ | Nối chuỗi | Chưa có số chưa vẽ được |
| Đọc 5 hợp đồng, rút điều khoản mỗi cái | Song song | Năm việc độc lập |
| Rà khách rồi soạn email nhắc đúng khách | Nối chuỗi | Chưa rà xong chưa biết nhắc ai |

[Ghi chú GV: chiếu lên, cho lớp giơ tay phân loại.]

---

## Slide 19: Demo nối chuỗi 2 agent

**Prompt:**
```
Làm lần lượt hai bước, xong bước 1 mới sang bước 2:
Bước 1: nhờ agent-ra-soat-khach rà thư mục 01-khach-hang,
   chỉ ra khách CẦN NHẮC GẤP NHẤT, lưu vào
   ket-qua/khach-can-nhac.md
Bước 2: sau khi có file đó, nhờ agent-soan-bao-cao đọc
   file và soạn email nhắc thanh toán gửi đúng khách đó.
```

**Kết quả mong đợi:** file trung gian + email nhắc gửi An Phát.

---

## Slide 20: Vì sao đây là nối chuỗi

- Bước 2 phải **chờ** bước 1 xong
- Chưa biết khách nào thì chưa soạn email được
- File trung gian `ket-qua/khach-can-nhac.md` là **cầu nối** giữa 2 agent

Mấu chốt khi ra lệnh:

- Nói rõ "làm lần lượt, xong bước 1 mới sang bước 2"
- Chỉ rõ file trung gian A lưu ra để B đọc

---

## Slide 21: Chạy song song và 3 quy tắc

**Prompt:**
```
Giao SONG SONG hai việc độc lập, gọi cùng lúc:
- agent-ra-soat-khach: rà 01-khach-hang, chỉ ra khách
  cần hành động.
- agent-soan-bao-cao: soạn báo cáo bán hàng tháng 3.
Mỗi agent kết thúc bằng mục "Nguồn". Xong gom lại.
```

**Ba quy tắc:**

1. Ép rõ "gọi cùng lúc, không tự làm thay"
2. Mỗi agent một phần độc lập
3. Bắt mỗi agent khai nguồn

[Ghi chú GV: song song đôi khi Claude vẫn làm tuần tự. Bình thường. Nối chuỗi chắc ăn hơn.]

---

## Slide 22: Năm ý cần nhớ

1. Agent là **nhân viên AI** lập bằng một file, có name, description, tools
2. Cần công thức thì **skill**; giao hẳn một vai có bếp riêng thì **agent**
3. **tools** điều khiển agent: cấp gì dùng nấy, không cấp thì không làm được
4. Người sau **chờ** người trước thì **nối chuỗi**, không chờ thì **song song**
5. Tạo agent xong phải **mở phiên mới**, gọi đích danh cho chắc

---

## Slide 23: Bài về nhà

- Lập **1 agent** cho việc mình làm nhiều nhất, chọn kỹ tools
- Dựng một **chuỗi 2 agent** cho việc thật của mình, chạy thử
- Ghi lại một việc **nên làm skill** (không nên làm agent), giải thích vì sao
- Chụp kết quả gửi Zalo lớp

---

## Slide 24: Xem trước Buổi 6 (capstone)

**Buổi 6: Ghép tất cả thành một quy trình thật**

Gộp CLAUDE.md, skill, MCP, agent, đội agent thành một quy trình công việc, chạy đầu-cuối rồi trình bày.

Câu hỏi giữ lại: quy trình nào của bạn muốn cho cả đội agent chạy?

Cảm ơn cả lớp. Hẹn gặp Buổi 6.
