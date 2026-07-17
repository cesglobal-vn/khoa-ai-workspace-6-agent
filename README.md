# Khóa AI Workspace: Làm chủ Agent với Claude Code

> Học viên dùng Claude Code chạy trên Claude Desktop để tự lập agent và điều khiển cả một đội agent làm việc cho mình. Không cần biết lập trình.

Đơn vị đào tạo: CES Global, Trung tâm Đào tạo & Ứng dụng Công nghệ.
Landing khóa học: https://nhanvienai.cesglobal.com.vn

---

## Khóa này dạy gì

Học viên đi từ chỗ dùng AI rời rạc sang làm chủ một công cụ AI dạng agent (Claude Code trên Claude Desktop) và nắm 5 khái niệm cốt lõi, mỗi buổi một bậc:

| Buổi | Khái niệm | Học viên làm được | Bài thực hành |
|---|---|---|---|
| 1 | **Skill + MCP + Agent + GitHub** | Skill là gì và cách kích hoạt, tự tạo skill; MCP là gì; tạo repo GitHub + lấy token + cắm GitHub MCP để quản lý skill; tạo agent đầu tiên | Tạo skill, đưa skill lên GitHub, tạo 1 agent |
| 2 | **Skill** | Đóng gói một quy trình lặp lại thành skill để Claude tự nạp và làm đúng mỗi lần | Skill đọc & tóm tắt tài liệu |
| 3 | **MCP** | Cắm công cụ và dữ liệu ngoài vào agent (file, web, Google Drive, cơ sở dữ liệu) qua MCP | MCP đọc dữ liệu và phân tích |
| 4 | **Subagent** | Tự định nghĩa agent chuyên trách: đặt vai trò, chỉ dẫn, giới hạn công cụ | Tạo Report Agent + Research Agent |
| 5 | **Agent Team** | Điều khiển đội agent: 1 lead chia việc cho nhiều agent chạy song song | Team 2-3 agent chạy 1 việc song song |
| 6 | **Ghép tất cả (Capstone)** | Lead điều phối team, mỗi agent dùng skill + MCP, chạy một quy trình công việc thật đầu-cuối | Capstone + trình bày |

## Thông tin lớp

- **Công cụ chính:** Claude Code chạy trong ứng dụng Claude Desktop (Windows/Mac)
- **Hình thức:** Online qua Zoom, có ghi hình lên LMS VIP xem lại
- **Lịch:** Tối Thứ Ba & Thứ Sáu, 20:00 tới 22:30
- **Thời lượng:** 6 buổi x 2,5 giờ = 15 giờ học trực tiếp
- **Đối tượng:** Khối văn phòng, marketer, sale, kế toán, trợ lý, quản lý vận hành, team lead, freelancer, chủ doanh nghiệp nhỏ, người mới bắt đầu với AI

## Nội dung repo

```
khoa-ai-workspace-6-agent/
├── README.md                     # File này
├── 00-tong-quan-khoa-hoc.md      # Đối tượng, chuẩn đầu ra, công cụ, chuẩn bị trước lớp
├── giao-an/                      # Dành cho GIẢNG VIÊN đứng lớp
│   ├── _template-giao-an.md      # Khung chuẩn: lời dẫn + prompt + file demo + kết quả mong đợi
│   ├── buoi-01-skill-mcp-agent-github.md
│   ├── buoi-02-skill.md
│   ├── buoi-03-mcp.md
│   ├── buoi-04-subagent.md
│   ├── buoi-05-agent-team.md
│   └── buoi-06-capstone.md
├── workbook-hoc-vien/            # Dành cho HỌC VIÊN tự làm theo
│   └── buoi-01..06.md
├── mau-cau-hinh/                 # Mẫu cấu hình copy dùng ngay
│   ├── claude-md-mau.md          # Mẫu CLAUDE.md cho thư mục dự án
│   ├── skill-tom-tat-tai-lieu.md # Mẫu một SKILL.md
│   ├── mcp-cau-hinh-mau.md       # Mẫu khai báo MCP + cách cấp quyền
│   ├── agent-report-mau.md       # Mẫu định nghĩa subagent (Report)
│   ├── agent-research-mau.md     # Mẫu định nghĩa subagent (Research)
│   ├── agent-team-mau.md         # Mẫu lập agent team + chia việc
│   └── github-mcp-va-token.md    # Tạo repo + lấy token + cắm GitHub MCP quản lý skill
└── tai-lieu-phat/
    ├── checklist-hoc-vien-toan-khoa.md
    ├── template-bao-cao-agent.md
    └── demo/                     # FILE DEMO cho từng buổi, khớp từng prompt trong giáo án
        ├── buoi-01/ ... buoi-06/
```

## Cách dùng bộ tài liệu này

- **Giảng viên:** mở `giao-an/buoi-0X.md`. Mỗi khối thời gian có sẵn: lời dẫn đọc lên được, prompt chính xác gõ vào Claude Code, file demo tương ứng (đường dẫn trong `tai-lieu-phat/demo/`), và kết quả mong đợi để đối chiếu.
- **Học viên:** dùng `workbook-hoc-vien/buoi-0X.md`, làm theo từng bước, dùng chung bộ file demo.
- **Mẫu cấu hình:** `mau-cau-hinh/` là các "linh kiện" học viên copy để lắp agent/skill/MCP/team.

## Lưu ý về công cụ

Giáo án viết bám Claude Code trên Claude Desktop. Một vài thao tác giao diện (menu, nút, lệnh gạch chéo) có thể đổi theo phiên bản; giảng viên chốt lại theo bản Claude Code thực tế lớp đang dùng ở Buổi 1. Phần khái niệm và prompt giữ nguyên giá trị dù phiên bản đổi.

## Bản quyền

CES Global. Tài liệu nội bộ phục vụ giảng dạy. Không phát tán ra ngoài khi chưa được duyệt.
