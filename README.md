# Khóa AI Workspace: Làm chủ Agent với Claude Code

> Học viên dùng Claude Code chạy trên Claude Desktop để tự lập agent và điều khiển cả một đội agent làm việc cho mình. Không cần biết lập trình.

Đơn vị đào tạo: CES Global, Trung tâm Đào tạo & Ứng dụng Công nghệ.
Landing khóa học: https://nhanvienai.cesglobal.com.vn

---

## Khóa này dạy gì

Học viên đi từ chỗ dùng AI rời rạc sang làm chủ một công cụ AI dạng agent (Claude Code trên Claude Desktop) và nắm 5 khái niệm cốt lõi, mỗi buổi một bậc:

| Buổi | Tên buổi & Khái niệm | Học viên làm được | Bài thực hành |
|---|---|---|---|
| 1 | **AI Workspace & Agent Điều phối** | Cài đặt Claude Desktop (tab Claude Code), bảo mật Privacy, làm chủ Mode/Model/Effort/Context Window, tạo file `CLAUDE.md`, tải tài liệu qua GitHub | Cấu hình Workspace, tạo CLAUDE.md, khởi tạo Agent Điều phối |
| 2 | **Agent Quản lý Tài liệu** | Xử lý tài liệu dài 14-40 trang, đóng gói quy trình thành Skill `tom-tat-tai-lieu`, kỷ luật chống bịa số liệu | Tóm tắt hợp đồng/báo cáo công việc, Meeting Note |
| 3 | **Agent Phân tích Dữ liệu** | Phân tích dữ liệu Excel/CSV, tìm xu hướng & bất thường, cắm MCP ngoại vi Drive/Gmail an toàn, đặt Routine | Phân tích báo cáo doanh số, tự động hóa Routine |
| 4 | **Agent Lập Báo cáo & Slide** | 4 cách dùng AI (Hỏi thẳng, Skill, Agent, Subagent), lập báo cáo chuẩn công sở, proposal, tạo slide thuyết trình | Soạn báo cáo quản trị & dàn ý deck slide |
| 5 | **Deep Research & Phối hợp Đội ngũ** | Nghiên cứu thị trường đa nguồn có trích dẫn, điều phối đội ngũ phối hợp tuần tự (nối chuỗi) và song song | Báo cáo nghiên cứu đối thủ, kịch bản team 2-3 agent |
| 6 | **Hệ Multi-Agent (Capstone)** | Ghép toàn bộ Workspace (CLAUDE.md + 6 Agent + Skill + MCP) thành quy trình tự động hóa thực tế đầu-cuối | Dự án Capstone thực tế & Thuyết trình tốt nghiệp |

## Thông tin lớp

- **Công cụ chính:** Claude Code chạy trong ứng dụng Claude Desktop (Windows/Mac)
- **Hình thức:** Online qua Zoom, có ghi hình lên LMS VIP xem lại
- **Lịch:** Tối Thứ Ba & Thứ Sáu, 20:00 tới 22:30
- **Thời lượng:** 6 buổi x 2,5 giờ = 15 giờ học trực tiếp
- **Đối tượng:** Khối văn phòng, marketer, sale, kế toán, trợ lý, quản lý vận hành, team lead, freelancer, chủ doanh nghiệp nhỏ, người mới bắt đầu với AI

## Nội dung repo

```
khoa-ai-workspace-6-agent/
├── README.md                                     # File chỉ huy & điều hướng toàn khóa
├── 00-tong-quan/                                 # Tài liệu định hướng & bàn giao chung
│   ├── 00-tong-quan-khoa-hoc.md                  # Khung chương trình, 4 tầng L1-L4, chuẩn bị lớp
│   ├── BAN-GIAO-GIANG-VIEN.md                    # Hướng dẫn chi tiết cho Giảng viên đứng lớp
│   ├── checklist-hoc-vien-toan-khoa.md           # Bảng kiểm tra tiến độ của Học viên
│   └── _template-giao-an.md                      # Khung chuẩn soạn giáo án
│
├── 01-buoi-01-ai-workspace-claude-code/          # TRỌN GÓI BUỔI 01
│   ├── giao-an-buoi-01.md                        # Giáo án đứng lớp
│   ├── workbook-buoi-01.md                       # Sổ tay thực hành học viên
│   ├── slide-buoi-01.md                          # Slide bài giảng
│   ├── slide-pptx/                               # Hình ảnh slide bài giảng (s01 - s12)
│   └── demo/                                     # File demo thực hành Buổi 1 (biên bản họp, dự án mẫu)
│
├── 02-buoi-02-quan-ly-tai-lieu-chong-bia-so/     # TRỌN GÓI BUỔI 02
│   ├── giao-an-buoi-02.md                        # Giáo án đứng lớp
│   ├── workbook-buoi-02.md                       # Sổ tay thực hành (.md)
│   ├── workbook-buoi-02.docx                     # Sổ tay thực hành (.docx)
│   └── demo/                                     # File demo Buổi 2 (báo cáo mẫu, hợp đồng, logo, brand)
│
├── 03-buoi-03-phan-tich-du-lieu-mcp-routine/     # TRỌN GÓI BUỔI 03
│   ├── giao-an-buoi-03.md                        # Giáo án đứng lớp
│   └── demo/                                     # File demo Buổi 3 (CSV doanh thu, đơn hàng, phòng KD mẫu)
│
├── 04-buoi-04-lap-bao-cao-va-slide/              # TRỌN GÓI BUỔI 04
│   ├── giao-an-buoi-04.md                        # Giáo án đứng lớp
│   └── demo/                                     # File demo Buổi 4 (số liệu bán hàng, yêu cầu nghiên cứu)
│
├── 05-buoi-05-deep-research-va-doi-ngu/          # TRỌN GÓI BUỔI 05
│   ├── giao-an-buoi-05.md                        # Giáo án đứng lớp
│   ├── workbook-buoi-05.md                       # Sổ tay thực hành học viên
│   ├── slide-buoi-05.md                          # Slide bài giảng
│   ├── bo-4-agent-va-monitor/                    # Bộ 4 agent chuyên môn & monitor
│   └── demo/                                     # File demo Buổi 5 (dự án ra mắt, Excel, Word, PDF)
│
├── 06-buoi-06-multi-agent-capstone/              # TRỌN GÓI BUỔI 06
│   ├── giao-an-buoi-06.md                        # Giáo án đứng lớp
│   └── demo/                                     # File đề bài Capstone thực tế
│
└── 07-mau-cau-hinh-linh-kien/                    # KHO MẪU LINH KIỆN TÁI SỬ DỤNG
    ├── CLAUDE-md-chuan-doanh-nghiep.md           # Mẫu CLAUDE.md chuẩn doanh nghiệp kế thừa chuẩn GEMINI
    ├── claude-md-mau.md                          # Mẫu CLAUDE.md cơ bản
    ├── claude-md-profile-va-cau-truc-phong-ban.md
    ├── skill-tom-tat-tai-lieu.md                 # Mẫu Skill chuẩn
    ├── mcp-cau-hinh-mau.md                       # Mẫu cấu hình MCP & cấp quyền
    ├── agent-report-mau.md                       # Mẫu Agent Report
    ├── agent-research-mau.md                     # Mẫu Agent Research
    ├── agent-team-mau.md                         # Mẫu Agent Team phối hợp
    ├── github-mcp-va-token.md                    # Mẫu tích hợp GitHub MCP
    └── template-bao-cao-agent.md                 # Mẫu báo cáo đầu ra của Agent
```

## Cách dùng bộ tài liệu này (Mô hình Trọn gói theo Buổi)

- **Đến buổi nào, mở đúng thư mục buổi đó:** Giảng viên và Học viên chỉ cần truy cập vào thư mục của buổi học hiện tại (ví dụ `01-buoi-01-.../` hoặc `02-buoi-02-.../`). Mọi tài liệu, giáo án, bài tập thực hành và file dữ liệu mẫu (`demo/`) đều nằm trọn vẹn bên trong một nơi, không cần chuyển qua lại giữa các thư mục khác.
- **Giảng viên:** Mở file `giao-an-buoi-0X.md` trong thư mục buổi tương ứng để giảng dạy. Mọi prompt, lời dẫn và đường dẫn demo đều đã trỏ chính xác.
- **Học viên:** Mở file `workbook-buoi-0X.md` trong thư mục buổi để thực hành trực tiếp.
- **Lắp ghép mở rộng:** Khi cần linh kiện nâng cao (file cấu hình chuẩn, MCP, Skill mẫu), tham khảo ngay thư mục `07-mau-cau-hinh-linh-kien/`.

## Lưu ý về công cụ

Giáo án viết bám Claude Code trên Claude Desktop. Một vài thao tác giao diện (menu, nút, lệnh gạch chéo) có thể đổi theo phiên bản; giảng viên chốt lại theo bản Claude Code thực tế lớp đang dùng ở Buổi 1. Phần khái niệm và prompt giữ nguyên giá trị dù phiên bản đổi.

## Bản quyền

CES Global. Tài liệu nội bộ phục vụ giảng dạy. Không phát tán ra ngoài khi chưa được duyệt.
