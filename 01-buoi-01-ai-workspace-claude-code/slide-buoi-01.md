# Nội dung slide Buổi 1: Skill, MCP, agent đầu tiên và quản lý Skill bằng GitHub

> Dùng cho GV dựng slide. Kiểu CES: nền trắng, chữ đậm màu navy, điểm nhấn teal/gold.
> Mỗi "---" là 1 slide. Phần [Ghi chú GV] không in lên slide. Tổng: 22 slide cho buổi 150 phút.

---

## Slide 1: Slide tiêu đề

**KHÓA AI WORKSPACE**
Làm chủ Agent với Claude Code

**Buổi 1: Skill, MCP, agent đầu tiên và quản lý Skill bằng GitHub**

CES Global | Trung tâm Đào tạo & Ứng dụng Công nghệ

[Ghi chú GV: buổi nền, nhiều nội dung. Trấn an lớp: bám theo từng bước, chưa xong làm nốt ở nhà.]

---

## Slide 2: Hôm nay cả lớp làm được gì

- Hiểu **skill** là gì, tự tạo skill đầu tiên
- Hiểu **MCP** là gì
- Tạo **repo GitHub** và lấy **token** an toàn
- Cắm **GitHub MCP** để quản lý skill
- Tạo **agent đầu tiên** của mình

Tất cả bằng tiếng Việt, không cần biết lập trình.

---

## Slide 3: Bốn viên gạch của buổi nền

```
SKILL  ->  đóng gói việc lặp lại
  MCP  ->  cho agent thêm khả năng (cắm GitHub)
GITHUB ->  cất và quản lý skill (có token)
AGENT  ->  trợ lý con chuyên một việc
```

Bốn thứ này là nền cho cả khóa.

---

## Slide 4: Câu hỏi mở đầu

Việc gì cả lớp làm đi làm lại mỗi tuần?

- Tóm tắt tài liệu?
- Soạn email theo mẫu?
- Lên danh sách việc?

Ghi lại. Lát nữa ta biến nó thành **skill**.

---

## Slide 5: Skill là gì

Một gói chỉ dẫn cho một việc lặp lại.

- Nằm ở `.claude/skills/<ten>/SKILL.md`
- Có phần mô tả (dùng khi nào) và phần thân (các bước làm)
- Đóng gói một lần, dùng lại mãi, chia sẻ được

Ví như một tờ hướng dẫn nghề: gặp đúng việc là lấy ra làm theo.

---

## Slide 6: Hai cách kích hoạt skill

1. **Tự động**
   Description viết rõ "dùng khi nào", Claude tự nạp khi gặp việc phù hợp.

2. **Gọi tên thẳng**
   "Dùng skill tom-tat-tai-lieu cho file này."

[Ghi chú GV: lát demo cả hai cách để lớp thấy khác biệt.]

---

## Slide 7: Demo, tạo skill đầu tiên

**Prompt:**
```
Tạo cho tôi một skill tên tom-tat-tai-lieu tại
.claude/skills/tom-tat-tai-lieu/SKILL.md. Dùng để tóm tắt
tài liệu dài. Đầu ra: tóm tắt nhanh, ý chính, số liệu và
hạn chót, điểm lưu ý. Chỉ dùng thông tin trong tài liệu.
```

**Kết quả mong đợi:** file SKILL.md có phần mô tả + phần thân các bước.

---

## Slide 8: Demo, kích hoạt skill trên biên bản họp

**Prompt:**
```
Dùng skill tom-tat-tai-lieu để tóm tắt file
bien-ban-hop-mau.md giúp tôi.
```

**Kết quả mong đợi:** tóm tắt đúng cấu trúc, đúng số liệu (doanh thu 1.085 triệu tăng so 915 triệu, nhắc thanh toán hạn thứ Sáu, chốt khách mời trước ngày 20).

---

## Slide 9: Thực hành 1, cả lớp tự tạo skill

Làm 3 việc:
1. Tạo skill tom-tat-tai-lieu
2. Gọi thẳng tên skill để tóm tắt `bien-ban-hop-mau.md`
3. Thử chỉ nói "tóm tắt giúp tôi file này", xem skill có tự nạp

Ai kẹt bước nào giơ tay.

---

## Slide 10: Nghỉ giải lao 10 phút

Phần sau: đưa skill lên GitHub và tạo agent.

Ai chưa xong skill, tranh thủ nhờ trợ giảng.

---

## Slide 11: MCP là gì

Cổng cắm chuẩn để agent dùng công cụ và dữ liệu ngoài.

- GitHub, file, web, Google Drive
- Cắm một MCP là cho agent thêm một khả năng
- Hôm nay: cắm **MCP GitHub**

Skill dạy agent LÀM GÌ. MCP cho agent CHẠM VÀO cái gì.

---

## Slide 12: Vì sao đưa skill lên GitHub

- Skill để trên máy: dễ mất, khó chia sẻ
- Đưa lên GitHub: có bản lưu trên mạng, xem được lịch sử, chia cho đồng nghiệp, đồng bộ nhiều máy

GitHub là nơi cất và quản lý skill của bạn.

---

## Slide 13: Token là gì và vì sao giữ bí mật

**Token (Personal Access Token):** chuỗi ký tự thay mật khẩu, cấp cho agent quyền dùng GitHub trong giới hạn.

- Giữ bí mật như mật khẩu
- Không dán vào chat, không gửi cho ai, không chụp gửi nhóm
- Chỉ dán vào cài đặt MCP của Claude Desktop
- Lộ thì vào GitHub thu hồi ngay

---

## Slide 14: Demo, tạo repo và lấy token

Theo `07-mau-cau-hinh-linh-kien/github-mcp-va-token.md`:

1. Tạo repo riêng tư, ví dụ `bo-skill-cua-toi`
2. Settings > Developer settings > Personal access tokens
3. Tạo token, chọn repo skill, quyền Contents đọc và ghi
4. Copy token ngay (chỉ hiện một lần)

[Ghi chú GV: nhắc kỹ an toàn token trước khi bấm.]

---

## Slide 15: Demo, cắm GitHub MCP

1. Mở Claude Desktop, vào cài đặt kết nối
2. Thêm server GitHub
3. Dán token vào đúng ô token
4. Lưu, kiểm tra báo kết nối thành công

Đây là chỗ token gặp agent.

---

## Slide 16: Demo, đưa skill lên GitHub

**Prompt:**
```
Dùng GitHub, đẩy toàn bộ thư mục .claude/skills/ lên repo
bo-skill-cua-toi của tôi. Nếu repo chưa có thì tạo mới ở
chế độ riêng tư. Kèm mô tả ngắn: thêm skill tom-tat-tai-lieu.
```

**Kết quả mong đợi:** file SKILL.md nằm trên GitHub, có lịch sử commit.

Từ nay sửa skill, chỉ cần bảo agent cập nhật lên GitHub.

---

## Slide 17: Agent đầu tiên là gì

**Agent (subagent):** một trợ lý con chuyên một việc.

- Đặt ở `.claude/agents/<ten>.md`
- Có vai trò, chỉ dẫn, giới hạn công cụ riêng
- Bạn giao việc, nó tự làm rồi trả kết quả

---

## Slide 18: Demo, tạo agent đầu tiên

**Prompt:**
```
Tạo cho tôi một agent tên report-agent tại
.claude/agents/report-agent.md. Vai trò: soạn báo cáo,
email, đề xuất từ số liệu hoặc ý thô. Quy tắc: tiếng Việt
công sở, không emoji trong email và báo cáo, không bịa số liệu.
```

**Kết quả mong đợi:** file agent có mô tả và chỉ dẫn. Giao thử: "viết email nhắc thanh toán gửi khách An Phát".

---

## Slide 19: Thực hành, agent cho nghề của bạn

Mỗi người tạo 1 agent cho một việc lặp lại của mình:

- Sale: agent soạn email chào hàng
- Kế toán: agent soạn nhắc công nợ
- Quản lý: agent soạn báo cáo tuần

Đặt tên và mô tả rõ agent làm việc gì.

---

## Slide 20: Bốn điều rút ra hôm nay

1. **Skill** đóng gói việc lặp lại
2. **MCP** cho agent thêm khả năng
3. **GitHub** để cất và quản lý skill
4. **Token** phải giữ bí mật như mật khẩu

---

## Slide 21: Bài về nhà

- Hoàn tất phần GitHub nếu ở lớp chưa xong (repo, token, cắm MCP, đẩy skill lên)
- Tạo thêm 1 skill cho việc lặp lại của bạn
- Chụp màn hình repo skill trên GitHub gửi Zalo lớp

---

## Slide 22: Xem trước Buổi 2

**Buổi 2: Đào sâu Skill**

Tạo nhiều skill cho quy trình thật của bạn và tinh chỉnh cách kích hoạt.

Câu hỏi giữ lại: việc nào bạn muốn đóng gói thành skill tiếp theo?

Cảm ơn cả lớp. Hẹn gặp Buổi 2.
