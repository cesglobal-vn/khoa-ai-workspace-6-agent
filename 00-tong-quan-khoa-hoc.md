# Tổng quan khóa AI Workspace

## 1. Triết lý khóa học

Phần lớn người đi làm dùng AI theo kiểu "mở chat, gõ câu hỏi, xong đóng". Mỗi lần lại phải giải thích lại bối cảnh, lại nhắc lại yêu cầu định dạng, lại dán lại dữ liệu. AI mạnh nhưng dùng lẻ tẻ nên không tích lũy.

Khóa này chuyển học viên sang cách làm khác: **đóng gói mỗi việc lặp lại thành một agent**. Agent = một ô nhớ chứa sẵn vai trò, quy tắc, định dạng đầu ra. Gọi ra là chạy đúng ngay, không cần dặn lại từ đầu. Sáu buổi xây sáu agent, buổi cuối ghép lại thành một dây chuyền.

Nguyên tắc xuyên suốt:
- **Không code.** Toàn bộ làm bằng ngôn ngữ tự nhiên (tiếng Việt) và thao tác giao diện.
- **Học bằng việc thật.** Mỗi buổi học viên mang dữ liệu công việc của mình vào để luyện.
- **Tích lũy.** Agent buổi trước là nguyên liệu cho buổi sau.

## 2. Chuẩn đầu ra (học xong có gì)

Kết thúc khóa, mỗi học viên sở hữu:
1. **Một AI Workspace cá nhân** đã dựng xong, dùng được ngay cho công việc hằng ngày.
2. **6 AI Agent vận hành:** Orchestrator, Document, Data Analysis, Report, Deep Research, và hệ Multi-Agent ghép nối.
3. **Bộ System Prompt chuẩn** cho từng agent (đã tinh chỉnh, copy dùng lại được).
4. **Template báo cáo / biên bản / email** tạo tự động.
5. **Một quy trình Multi-Agent hoàn chỉnh** chạy end-to-end.
6. **Một capstone project** áp dụng đúng vào công việc của bản thân.

## 3. Công cụ sử dụng

Khóa xây dựng trên nền một công cụ AI hội thoại có khả năng tạo "project / custom agent" và đọc file (ví dụ ChatGPT, Claude, hoặc nền tảng tương đương mà CES hướng dẫn ở Buổi 1). Học viên chỉ cần:
- 1 tài khoản AI (bản có tính năng tạo project/agent + upload file: GV hướng dẫn chọn bản phù hợp buổi 1)
- Trình duyệt web, máy tính (khuyến nghị, không bắt buộc điện thoại)
- Bộ file mẫu công việc của chính mình (tài liệu, file Excel, email...) để thực hành

> Ghi chú GV: chốt danh sách công cụ cuối cùng ở buổi 1 theo bản quyền/tài khoản CES cấp cho lớp. Toàn bộ giáo án viết theo hướng công cụ-độc-lập (tool-agnostic) để dễ thay nền tảng.

## 4. Chuẩn bị trước khi vào lớp (gửi học viên trước Buổi 1)

- [ ] Tạo/đăng nhập sẵn tài khoản AI theo hướng dẫn CES gửi qua Zalo
- [ ] Chuẩn bị 2-3 file công việc thật: 1 tài liệu dài (PDF/Word), 1 file Excel/CSV có số liệu, 1 vài email mẫu
- [ ] Cài Zoom, kiểm tra mic, ngồi máy tính để thao tác theo
- [ ] Tải bộ file demo của khóa (CES gửi link) về một thư mục riêng

## 5. Bản đồ 6 buổi (cách các agent nối nhau)

```
Buổi 1  ──►  Workspace + Orchestrator  (bộ khung + agent điều phối)
                     │
   ┌─────────────────┼─────────────────┬──────────────────┐
   ▼                 ▼                 ▼                  ▼
Buổi 2           Buổi 3            Buổi 4             Buổi 5
Document         Data Analysis     Report             Deep Research
(đọc/tóm tắt)    (Excel→biểu đồ)   (báo cáo/email)    (nghiên cứu)
   └─────────────────┴─────────────────┴──────────────────┘
                     ▼
Buổi 6  ──►  Multi-Agent System  (Orchestrator gọi 5 agent chạy 1 quy trình thật)
```

Orchestrator (buổi 1) là "trưởng nhóm": nhận yêu cầu tổng, chia việc cho Document / Data / Report / Research (buổi 2-5). Buổi 6 lắp cả dây chuyền cho chạy end-to-end trên một dự án thật của học viên.

## 6. Nhịp chuẩn mỗi buổi (2,5 giờ)

| Khối | Thời lượng | Nội dung |
|---|---|---|
| Mở đầu | 15' | Điểm danh, recap buổi trước, nêu mục tiêu buổi |
| Lý thuyết ngắn | 20' | Khái niệm cốt lõi của agent buổi đó (dễ hiểu, không hàn lâm) |
| Demo GV | 25' | GV làm mẫu dựng agent từ đầu, học viên xem |
| Thực hành 1 | 30' | Học viên tự dựng agent với dữ liệu mẫu chung |
| Nghỉ | 10' | |
| Thực hành 2 | 35' | Học viên áp agent vào dữ liệu công việc của mình |
| Chốt + giao bài | 20' | Q&A, tổng kết, giao bài về nhà, xem trước buổi sau |

## 7. Đánh giá & hoàn thành

- **Hoàn thành buổi:** nộp được sản phẩm thực hành của buổi (agent chạy + 1 output mẫu).
- **Hoàn thành khóa:** buổi 6 trình bày capstone: 1 workflow multi-agent giải một bài toán công việc thật.
- CES cấp chứng nhận hoàn thành cho học viên đạt tối thiểu 5/6 buổi + capstone.

## 8. Chính sách học phí (tham khảo: do phòng Sale chốt)

| Gói | Học phí | Ưu đãi |
|---|---|---|
| Cá nhân | 1.899.000₫ | - |
| Nhóm 3 người | 1.710.000₫/người | -10% |
| Nhóm 6 người trở lên | 1.520.000₫/người | -20% |

Tất cả các gói gồm: 6 buổi live, hỗ trợ qua Zalo, truy cập LMS VIP, 6 agent kèm system prompt.
