# Workbook Buổi 1: Skill, MCP, agent đầu tiên và quản lý Skill bằng GitHub

> Làm theo từng bước. Chỗ nào chưa kịp ở lớp thì làm nốt ở nhà theo hướng dẫn này.

## Buổi này bạn sẽ làm được
1. Hiểu skill là gì và 2 cách kích hoạt skill.
2. Tự tạo 1 skill đầu tiên (tóm tắt tài liệu) và chạy thử.
3. Hiểu MCP là gì.
4. Tạo repo GitHub, lấy token an toàn, cắm GitHub MCP.
5. Đưa skill lên GitHub để quản lý.
6. Tạo agent đầu tiên của mình.

## Chuẩn bị
- [ ] Đã cài Claude Desktop, đăng nhập tài khoản CES cấp
- [ ] Tải bộ demo, biết đường dẫn `tai-lieu-phat/demo/buoi-01/bien-ban-hop-mau.md`
- [ ] Có (hoặc tạo) 1 tài khoản GitHub
- [ ] 1 thư mục dự án trống trên máy để làm việc

---

## Phần A: Skill (là gì, tạo, kích hoạt)

**Skill là gì:** một gói chỉ dẫn cho một việc lặp lại, nằm ở `.claude/skills/<ten>/SKILL.md`. Claude tự nạp khi gặp việc phù hợp (nhờ dòng mô tả), hoặc bạn gọi thẳng tên.

**Bước 1: Mở Claude Code, trỏ vào thư mục dự án của bạn.**

**Bước 2: Tạo skill đầu tiên.** Gõ:
```
Tạo cho tôi một skill tên tom-tat-tai-lieu, đặt tại .claude/skills/tom-tat-tai-lieu/SKILL.md.
Skill dùng khi cần đọc và tóm tắt tài liệu dài (biên bản, hợp đồng, báo cáo). Đầu ra gồm: tóm tắt nhanh 3 tới 5 gạch đầu dòng, ý chính theo mục, danh sách số liệu và hạn chót, điểm cần lưu ý. Quy tắc: chỉ dùng thông tin trong tài liệu, không có thì ghi "tài liệu không đề cập".
```

**Bước 3: Kích hoạt skill bằng cách gọi thẳng tên.** Gõ:
```
Dùng skill tom-tat-tai-lieu để tóm tắt file bien-ban-hop-mau.md giúp tôi.
```

**Bước 4: Thử kích hoạt tự động** (không gọi tên, xem Claude có tự nạp không). Gõ:
```
Tóm tắt giúp tôi file bien-ban-hop-mau.md.
```

> Ghi chú của bạn: skill có tự nạp ở Bước 4 không? Nếu không, description cần rõ hơn chỗ nào?
> ......................................................................................

Mẫu nội dung SKILL.md để đối chiếu: xem `mau-cau-hinh/skill-tom-tat-tai-lieu.md`.

---

## Phần B: MCP là gì

**MCP** là cổng cắm chuẩn để agent dùng công cụ và dữ liệu ngoài: GitHub, file, web, Google Drive. Cắm một MCP là cho agent thêm một khả năng.

Hôm nay ta cắm **MCP GitHub** để agent lưu và quản lý skill trên GitHub thay bạn.

> Ghi nhớ: skill dạy agent LÀM GÌ. MCP cho agent CHẠM VÀO cái gì (ở đây là kho lưu trên GitHub).

---

## Phần C: GitHub, token, cắm MCP, đưa skill lên (quản lý skill)

Làm theo chi tiết trong `mau-cau-hinh/github-mcp-va-token.md`. Tóm tắt các bước:

**Bước 5: Tạo repo GitHub.** Vào github.com, tạo repo riêng tư, ví dụ `bo-skill-cua-toi`.

**Bước 6: Lấy Personal Access Token.** Settings > Developer settings > Personal access tokens. Tạo token (loại Fine-grained), chọn repo skill của bạn, cấp quyền Contents đọc và ghi, tạo và COPY token ngay.

> An toàn (bắt buộc nhớ): token như mật khẩu. KHÔNG dán token vào khung chat, KHÔNG gửi cho ai, KHÔNG chụp màn hình gửi nhóm. Chỉ dán token vào cài đặt MCP của Claude Desktop.

**Bước 7: Cắm GitHub MCP.** Trong Claude Desktop, mở cài đặt kết nối, thêm server GitHub, dán token vào ô token, lưu lại, kiểm tra báo thành công.

**Bước 8: Đưa skill lên GitHub.** Quay lại Claude Code, gõ:
```
Dùng GitHub, đẩy toàn bộ thư mục .claude/skills/ lên repo bo-skill-cua-toi của tôi. Nếu repo chưa có thì tạo mới ở chế độ riêng tư. Kèm mô tả ngắn: thêm skill tom-tat-tai-lieu.
```

**Bước 9: Kiểm tra.** Mở repo trên web, thấy file `SKILL.md` đã nằm trên GitHub là đạt.

> Ghi chú của bạn: tên repo skill: ................................  Đã đẩy được lên chưa? .........

---

## Phần D: Tạo agent đầu tiên

**Agent (subagent)** là một trợ lý con chuyên một việc, đặt ở `.claude/agents/<ten>.md`.

**Bước 10: Tạo agent đầu tiên.** Gõ:
```
Tạo cho tôi một agent tên report-agent tại .claude/agents/report-agent.md. Vai trò: chuyên soạn báo cáo, email, đề xuất từ số liệu hoặc ý thô. Quy tắc: tiếng Việt công sở, không dùng emoji trong email và báo cáo, không bịa số liệu, thiếu thì để [đợi bổ sung].
```

**Bước 11: Giao thử một việc.** Gõ:
```
Nhờ report-agent viết email nhắc thanh toán gửi khách An Phát, lịch sự, ngắn gọn.
```

Mẫu agent để đối chiếu: xem `mau-cau-hinh/agent-report-mau.md`.

> Ghi chú của bạn: tên agent bạn muốn tạo cho nghề của mình: ...................................

---

## Bài tập
- **Tại lớp:** tạo xong skill tom-tat-tai-lieu và chạy thử; tạo được 1 agent đầu tiên; cắm GitHub MCP và đẩy skill lên nếu kịp.
- **Về nhà:** hoàn tất phần GitHub (repo, token, cắm MCP, đẩy skill); tạo thêm 1 skill cho việc lặp lại của bạn; chụp màn hình repo skill trên GitHub gửi Zalo lớp.

## Checklist tự đánh giá
- [ ] Nói lại được skill là gì và 2 cách kích hoạt
- [ ] Có skill tom-tat-tai-lieu chạy ra bản tóm tắt đúng cấu trúc
- [ ] Hiểu MCP là gì
- [ ] Tạo được repo GitHub và token (giữ token bí mật)
- [ ] Cắm GitHub MCP và đẩy skill lên repo
- [ ] Tạo được 1 agent đầu tiên và giao thử một việc
