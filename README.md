# Khóa AI Workspace: Đội 6 AI Agent trong 6 buổi

> "Từ dùng AI lẻ tẻ đến đội 6 AI Agent làm việc cho bạn."
> Xây dựng AI Workspace cá nhân với 6 agent chuyên trách, không cần biết lập trình.

Đơn vị đào tạo: **CES Global**: Trung tâm Đào tạo & Ứng dụng Công nghệ.
Landing khóa học: https://nhanvienai.cesglobal.com.vn

---

## Khóa này dạy gì

Học viên đi từ chỗ dùng AI rời rạc (mỗi lần mở chat gõ lại từ đầu) sang một **workspace cá nhân** gồm 6 agent, mỗi agent là một "nhân viên AI" chuyên một việc, gọi ra là chạy. Buổi cuối ghép cả 6 thành một quy trình tự động đầu-cuối.

| Buổi | Loại | Agent xây dựng | Kết quả buổi |
|---|---|---|---|
| 1 | Nền tảng | Workspace + Orchestrator (điều phối) | Có workspace + agent điều phối gọi được các agent khác |
| 2 | Thực chiến | Document Agent | Đọc, tóm tắt, trích ý tài liệu dài |
| 3 | Thực chiến | Data Analysis Agent | Phân tích Excel/CSV, vẽ biểu đồ, tìm xu hướng |
| 4 | Thực chiến | Report Agent | Soạn báo cáo, đề xuất, email, slide tự động |
| 5 | Nâng cao | Deep Research Agent | Nghiên cứu thị trường, phân tích đối thủ, tổng hợp đa nguồn |
| 6 | Capstone | Multi-Agent System | Ghép 6 agent thành workflow tự động, chạy dự án thực |

## Thông tin lớp

- **Hình thức:** Online qua Zoom, có ghi hình lên LMS VIP xem lại
- **Lịch:** Tối Thứ Ba & Thứ Sáu, 20:00 - 22:30
- **Thời lượng:** 6 buổi × 2,5 giờ = 15 giờ học trực tiếp
- **Đối tượng:** Khối văn phòng, marketer, sale, kế toán, trợ lý, quản lý vận hành, team lead, freelancer, chủ doanh nghiệp nhỏ, người mới bắt đầu với AI

## Nội dung repo

```
khoa-ai-workspace-6-agent/
├── README.md                     # File này
├── 00-tong-quan-khoa-hoc.md      # Đối tượng, chuẩn đầu ra, công cụ, chuẩn bị trước lớp
├── giao-an/                      # Dành cho GIẢNG VIÊN đứng lớp
│   ├── _template-giao-an.md      # Khung chuẩn mỗi buổi
│   ├── buoi-01-workspace-orchestrator.md
│   ├── buoi-02-document-agent.md
│   ├── buoi-03-data-analysis-agent.md
│   ├── buoi-04-report-agent.md
│   ├── buoi-05-deep-research-agent.md
│   └── buoi-06-multi-agent-capstone.md
├── workbook-hoc-vien/            # Dành cho HỌC VIÊN tự học / thực hành theo
│   ├── buoi-01..06.md
├── system-prompts/               # 6 system prompt của 6 agent: copy dùng ngay
│   ├── 01-orchestrator-agent.md
│   ├── 02-document-agent.md
│   ├── 03-data-analysis-agent.md
│   ├── 04-report-agent.md
│   ├── 05-deep-research-agent.md
│   └── 06-multi-agent-workflow.md
└── tai-lieu-phat/                # Template báo cáo, checklist, file demo học viên
```

## Cách dùng bộ tài liệu này

- **Giảng viên:** đọc `giao-an/buoi-0X.md`: có timeline theo phút, lời dẫn, demo, câu hỏi tương tác, tình huống hay gặp và cách xử lý.
- **Học viên:** dùng `workbook-hoc-vien/buoi-0X.md`: hướng dẫn thao tác từng bước, bài tập tại lớp + về nhà, ô ghi chú, system prompt để copy.
- **Cả hai:** `system-prompts/` là "linh kiện" chính của khóa: mỗi buổi lắp thêm một agent vào workspace.

## Bản quyền

© CES Global. Tài liệu nội bộ phục vụ giảng dạy khóa AI Workspace. Không phát tán ra ngoài khi chưa được duyệt.
