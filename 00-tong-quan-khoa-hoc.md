# Tổng quan khóa AI Workspace: Làm chủ Agent với Claude Code

## 1. Triết lý khóa học

Phần lớn người đi làm dùng AI theo kiểu mở chat, gõ câu hỏi, xong đóng. Mỗi lần lại giải thích lại bối cảnh, nhắc lại định dạng, dán lại dữ liệu. AI mạnh nhưng dùng lẻ tẻ nên không tích lũy.

Khóa này chuyển học viên sang một công cụ AI dạng agent: **Claude Code chạy trong Claude Desktop**. Agent khác chat thường ở chỗ nó tự làm nhiều bước, đọc và sửa được file thật trong máy, nhớ bối cảnh dự án, và gọi được công cụ ngoài. Học viên học cách đóng gói việc lặp lại (skill), cắm thêm công cụ (MCP), tạo agent chuyên trách (subagent), rồi điều khiển cả một đội agent (agent team) làm việc song song.

Nguyên tắc xuyên suốt:
- **Không code.** Ra lệnh bằng tiếng Việt, cấu hình bằng file văn bản đơn giản.
- **Học bằng việc thật.** Mỗi buổi học viên mang dữ liệu công việc của mình vào để luyện.
- **Tích lũy.** Khái niệm buổi trước là nền cho buổi sau: agent, skill, MCP, subagent, agent team.

## 2. Năm khái niệm cốt lõi (nói trước để lớp có bản đồ)

| Khái niệm | Hiểu đơn giản |
|---|---|
| **Agent** | Trợ lý AI tự làm nhiều bước, đọc/sửa file thật, nhớ bối cảnh. Đây là Claude Code. |
| **Skill** | Gói chỉ dẫn cho một quy trình lặp lại. Claude tự nạp đúng skill khi gặp việc phù hợp. |
| **MCP** | Cổng cắm để agent dùng công cụ và dữ liệu ngoài: file, web, Google Drive, cơ sở dữ liệu. |
| **Subagent** | Agent con chuyên một việc, có vai trò và công cụ riêng do mình định nghĩa. |
| **Agent Team** | Nhiều agent cùng làm, một lead chia việc và ghép kết quả, chạy song song. |

## 3. Chuẩn đầu ra (học xong có gì)

1. **Claude Code chạy được trên máy** (trong Claude Desktop), có thư mục dự án + CLAUDE.md của riêng học viên.
2. **Ít nhất 1 skill tự tạo** cho một quy trình công việc lặp lại.
3. **Ít nhất 1 MCP đã cắm** và dùng được (đọc dữ liệu hoặc công cụ ngoài).
4. **2 subagent chuyên trách** tự định nghĩa (ví dụ Report, Research).
5. **1 agent team** biết chia việc cho nhiều agent chạy song song.
6. **1 quy trình công việc thật (capstone)** ghép skill + MCP + team, chạy đầu-cuối.

## 4. Công cụ & điều kiện

- Máy tính Windows hoặc Mac, cài **Claude Desktop** (có Claude Code).
- Tài khoản Claude theo hướng dẫn CES cấp cho lớp (bản dùng được Claude Code).
- Trình duyệt, Zoom để học online.
- Bộ file công việc thật của học viên: 1 tài liệu dài, 1 file dữ liệu (Excel/CSV), vài ghi chú/email.
- Bộ file demo của khóa nằm sẵn trong repo tại `tai-lieu-phat/demo/`.

> Ghi chú GV: chốt phiên bản Claude Code + cách cài đặt cụ thể ở Buổi 1 theo tài khoản CES cấp. Giáo án viết theo hướng khái niệm + prompt để không lệ thuộc thay đổi giao diện.

## 5. Chuẩn bị trước khi vào lớp (gửi học viên trước Buổi 1)

- [ ] Cài Claude Desktop theo hướng dẫn CES gửi qua Zalo, đăng nhập sẵn tài khoản
- [ ] Tạo sẵn 1 thư mục trống trên máy để làm thư mục dự án của khóa
- [ ] Chuẩn bị 2-3 file công việc thật (1 tài liệu dài, 1 file Excel/CSV, vài ghi chú/email)
- [ ] Tải bộ file demo của khóa về máy
- [ ] Ngồi máy tính, cài Zoom, kiểm tra mic để thao tác theo

## 6. Bản đồ 6 buổi (cách các khái niệm nối nhau)

```
Buổi 1  Agent        : làm quen Claude Code + thư mục dự án + CLAUDE.md
            │
Buổi 2  Skill        : đóng gói quy trình lặp lại (tóm tắt tài liệu)
            │
Buổi 3  MCP          : cắm công cụ/dữ liệu ngoài (phân tích dữ liệu)
            │
Buổi 4  Subagent     : tạo agent chuyên trách (Report, Research)
            │
Buổi 5  Agent Team   : 1 lead + nhiều agent chạy song song
            │
Buổi 6  Capstone     : ghép Skill + MCP + Team cho 1 quy trình thật
```

## 7. Nhịp chuẩn mỗi buổi (2,5 giờ)

| Khối | Thời lượng | Nội dung |
|---|---|---|
| Mở đầu | 15' | Điểm danh, recap buổi trước, nêu mục tiêu buổi |
| Lý thuyết ngắn | 20' | Khái niệm cốt lõi của buổi (dễ hiểu, không hàn lâm) |
| Demo GV | 25' | GV làm mẫu trên Claude Code với file demo, học viên xem |
| Thực hành 1 | 30' | Học viên tự làm với file demo chung |
| Nghỉ | 10' | |
| Thực hành 2 | 35' | Học viên áp vào dữ liệu công việc của mình |
| Chốt + giao bài | 20' | Q&A, tổng kết, giao bài về nhà, xem trước buổi sau |

Riêng Buổi 6 (capstone) dồn thời gian cho học viên dựng và trình bày.

## 8. Đánh giá & hoàn thành

- **Hoàn thành buổi:** nộp được sản phẩm thực hành của buổi (agent/skill/MCP/team chạy + 1 kết quả mẫu).
- **Hoàn thành khóa:** Buổi 6 trình bày capstone, 1 quy trình multi-agent giải một bài toán công việc thật.
- CES cấp chứng nhận cho học viên đạt tối thiểu 5/6 buổi + capstone.

## 9. Chính sách học phí (tham khảo, do phòng Sale chốt)

| Gói | Học phí | Ưu đãi |
|---|---|---|
| Cá nhân | 1.899.000₫ | - |
| Nhóm 3 người | 1.710.000₫/người | -10% |
| Nhóm 6 người trở lên | 1.520.000₫/người | -20% |

Tất cả các gói gồm: 6 buổi live, hỗ trợ qua Zalo, truy cập LMS VIP, bộ mẫu cấu hình agent/skill/MCP/team.
