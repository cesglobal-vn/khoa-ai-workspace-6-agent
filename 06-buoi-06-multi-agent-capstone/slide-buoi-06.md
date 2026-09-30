# Nội dung slide Buổi 06: Toàn Cảnh Hệ Sinh Thái Claude, Vòng Lặp Tự Phản Biện & Thuê Ê-kíp Media

> Dùng cho GV trình chiếu và giảng dạy. Phong cách CES: Nền tối công nghệ cao hoặc nền sáng doanh nghiệp, chữ to rõ, bám sát từng bước thao tác và prompt thực tế.
> Mỗi `---` tương ứng với 1 slide. Tổng cộng: 26 slide chuẩn nhịp 150 phút.

---

## Slide 1: Slide tiêu đề

**KHÓA AI WORKSPACE: LÀM CHỦ AGENT VỚI CLAUDE CODE**

### Buổi 06: Toàn Cảnh Hệ Sinh Thái Claude, Vòng Lặp Tự Phản Biện & Thuê Ê-kíp Media

CES Global | Trung tâm Đào tạo & Ứng dụng Công nghệ  
*Website: nhanvienai.cesglobal.com.vn*

[Ghi chú GV: Buổi đúc kết đỉnh cao. Giúp học viên định vị rõ bức tranh AI Workspace và trang bị 2 vũ khí tối tân: Vòng lặp tự phản biện và Ê-kíp media tự động.]

---

## Slide 2: Khung chương trình Buổi 06 (150 phút)

| Phần | Nội dung | Trọng tâm học viên cầm được |
|---|---|---|
| **A** | Toàn cảnh Hệ sinh thái Claude (25') | 4 cấp độ dùng Claude + Rà soát bộ não 4 tầng |
| **B** | Vũ khí 1: Vòng lặp Maker – Checker (40') | Trưởng phòng thẩm định + Tự sửa sai từ 7/10 lên 9.5/10 |
| | *Giải lao (10')* | *Hỗ trợ kỹ thuật* |
| **C** | Vũ khí 2: Thuê ê-kíp Media làm trailer (50') | Skill `/brag` + Video `.mp4` + Bản dọc TikTok + Caption |
| **D** | Lộ trình Doanh nghiệp & Tổng kết (25') | 3 nguyên tắc vàng đóng gói + Bảng prompt tra nhanh |

---

## Slide 3: Phần A — Toàn cảnh 4 cấp độ dùng Claude

Nhiều người dùng AI cả năm vẫn chỉ "hỏi một câu - đáp một câu". Đâu là sự khác biệt?

1. **Cấp độ 1: Claude Web / App** — Nhắn tin với cộng tác viên online.
2. **Cấp độ 2: Claude Projects (Web)** — Tủ tài liệu dùng chung tĩnh.
3. **Cấp độ 3: Claude Desktop + MCP** — Trợ lý máy tính có công cụ nối dài.
4. **Cấp độ 4: Claude Code / AI Workspace** — Giám đốc điều hành văn phòng AI tự động.

---

## Slide 4: So sánh Cấp độ 1, 2, 3 vs Cấp độ 4 (AI Workspace)

| Tiêu chí | Cấp 1, 2 (Web/Projects) | Cấp 3 (Desktop + MCP) | Cấp 4: Claude Code (AI Workspace) |
|---|---|---|---|
| **Quyền can thiệp file** | Không | Giới hạn | **Toàn quyền đọc, tạo, sửa file** |
| **Lưu trữ ngữ cảnh** | Tạm thời / Tĩnh | Từng phiên chat | **Lưu vĩnh viễn trong CLAUDE.md** |
| **Phân quyền nhân sự** | Không | Không | **Chia phòng riêng, chìa khóa riêng** |
| **Vận hành quy trình** | Thủ công từng câu | Bán tự động | **Khép kín từ đầu đến cuối** |

---

## Slide 5: Xâu chuỗi "Bộ não 4 tầng" của AI Workspace

```text
┌─────────────────────────────────────────────────────────────┐
│ 1. NỘI QUY & VĂN HÓA (CLAUDE.md)                            │
│    -> Giữ AI luôn đúng vai, chuẩn xưng hô, cấm bịa số       │
├─────────────────────────────────────────────────────────────┤
│ 2. QUY TRÌNH THAO TÁC CHUẨN - SOP (Skills)                  │
│    -> Các công thức lặp lại: Tóm tắt văn bản, làm slide     │
├─────────────────────────────────────────────────────────────┤
│ 3. CÁNH TAY NỐI DÀI NGOẠI VI (MCP)                          │
│    -> Chạm ra ngoài máy tính: Google Drive, Gmail...        │
├─────────────────────────────────────────────────────────────┤
│ 4. BIÊN CHẾ NHÂN SỰ CHUYÊN BIỆT (Agents & Subagents)        │
│    -> Nhân viên có phòng riêng, chìa khóa riêng             │
└─────────────────────────────────────────────────────────────┘
```

---

## Slide 6: Thao tác — Kiểm tra "Túi đồ nghề"

Học viên mở Claude Code và gõ lệnh rà soát toàn bộ tài sản:

```text
Liệt kê ngắn gọn giúp tôi:
1. File CLAUDE.md đang có những quy tắc chính nào?
2. Thư mục .claude/skills/ đang có những skill gì?
3. Thư mục .claude/agents/ đang có những agent nào?
```

*Kết quả: Thấy trọn vẹn gia tài AI đã tích lũy sau 5 buổi học.*

---

## Slide 7: Phần B — Vũ khí 1: Vòng lặp Maker – Checker

- Ở **Buổi 5**, chúng ta đã cho 2 nhân viên phối hợp **Nối chuỗi tuần tự**:
  - `nghien-cuu-doi-thu` bàn giao số liệu $\rightarrow$ `chuyen-vien-de-xuat` viết phương án.
- **Nỗi đau thực tế công sở:**
  - Bản thảo đầu tiên thường chỉ đạt mức **7/10 điểm**.
  - Văn phong còn lan man, số liệu chưa đủ chứng minh, thiếu phương án rủi ro.
- **Giải pháp:** Cặp đôi **Maker – Checker** (Chuyên viên soạn – Trưởng phòng soi).

---

## Slide 8: Bước B1 — Tuyển Trưởng phòng thẩm định

Gõ lệnh tuyển nhân sự biên chế (chỉ có quyền đọc file, không sửa):

```text
Tạo cho tôi một agent mới tại đường dẫn: ".claude/agents/truong-phong-tham-dinh.md" ngay trong thư mục này.

Chỉ cấp cho trợ lý này công cụ đọc và tìm kiếm file trong máy. Tuyệt đối KHÔNG cấp công cụ chỉnh sửa hay tạo file mới.

Nhiệm vụ của Trưởng phòng thẩm định:
1. Đóng vai một Trưởng phòng chiến lược dày dạn kinh nghiệm, cực kỳ khó tính và khắt khe.
2. Khi nhận được một bản kế hoạch hoặc báo cáo từ chuyên viên, hãy soi lỗi dựa trên 3 tiêu chí:
   - Tính xác thực của số liệu: Mọi con số đều phải trích dẫn rõ nguồn, không được nhận định chung chung.
   - Tính thực tế và rủi ro: Kế hoạch có tính đến ngân sách, đối thủ và điểm nghẽn thực thi chưa?
   - Văn phong công sở: Gọn gàng, khúc chiết, không dùng từ sáo rỗng, không biểu cảm thừa.
3. Luôn đưa ra nhận xét theo format:
   - Điểm đạt yêu cầu.
   - Điểm chưa đạt (nêu rõ tối đa 3 điểm yếu cần sửa gấp).
   - Yêu cầu sửa đổi cụ thể cho chuyên viên.
```

---

## Slide 9: Bước B2 — Kích hoạt Vòng lặp phản biện

Gõ lệnh điều phối dây chuyền tự động:

```text
Hãy thực hiện quy trình tự phản biện 2 vòng giữa chuyen-vien-de-xuat và truong-phong-tham-dinh:

Vòng 1:
- Nhờ chuyen-vien-de-xuat đọc dữ liệu nghiên cứu sẵn có và soạn một bản Đề xuất chiến lược ra mắt sản phẩm mới, lưu bản nháp vào file "ket-qua/ban-nhap-de-xuat.md".

Vòng 2:
- Nhờ truong-phong-tham-dinh đọc file "ket-qua/ban-nhap-de-xuat.md", đưa ra bản thẩm định khắt khe và chỉ ra các điểm cần sửa, lưu vào file "ket-qua/bien-ban-tham-dinh.md".

Vòng 3 (Chốt bản cuối):
- Nhờ chuyen-vien-de-xuat đọc kỹ "ket-qua/bien-ban-tham-dinh.md", tiếp thu toàn bộ góp ý của Trưởng phòng để chỉnh sửa và xuất bản hoàn chỉnh vào file "ket-qua/de-xuat-hoan-thien.md".
```

---

## Slide 10: Bước B3 — Đối chiếu chất lượng

Gõ câu lệnh so sánh kết quả:

```text
Hãy tóm tắt và chỉ ra 3 điểm khác biệt lớn nhất giữa bản nháp đầu tiên ("ket-qua/ban-nhap-de-xuat.md") và bản đã hoàn thiện sau phản biện ("ket-qua/de-xuat-hoan-thien.md").
```

*Bạn sẽ thấy: Bản hoàn thiện có số liệu minh chứng rõ ràng, không còn câu từ mơ hồ, đạt điểm 9.5/10.*

---

## Slide 11: Phần C — Vũ khí 2: Thuê Ê-kíp Media Ngoại Viện

> **Ví von xuyên suốt:** Sau khi chiến lược xong, công ty thuê ê-kíp làm trailer quảng cáo ra mắt sản phẩm!

### Skill làm video là gì, vì sao cần?
- **Skill là quyển công thức** (buổi 2).
- `/brag` là quyển công thức của cả một **ê-kíp làm trailer**: biên kịch, dựng hình, làm nhạc, viết caption.
- Không có skill, Claude vẫn viết được kịch bản, nhưng chung chung, sản phẩm nào cũng như nhau!

---

## Slide 12: Hai nguyên tắc bảo vệ công ty khi thuê ê-kíp

1. **Cài cấp thư mục dự án:**  
   - Ê-kíp chỉ làm việc trong văn phòng này, không theo sang máy khác.
2. **Kiểm tra lý lịch trước khi cho vào cửa:**  
   - Bắt Claude đọc và báo cáo skill trước khi cài đặt (chống bẫy câu lệnh ẩn từ Buổi 5).

---

## Slide 13: Bước C1 & C2 — Lấy mẫu & Thử làm khi chưa có skill

**Bước 1: Lấy 5 sản phẩm mẫu:**
```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```

**Bước 2: Thử làm khi chưa có ê-kíp:**
```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```

---

## Slide 14: Bước C3 — Cài skill ê-kíp làm trailer

Cài đặt 2 skill `brag` và `brag-slim`:

```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```

*Bạn sẽ thấy: Claude tóm tắt skill rồi tạo `.claude/skills/brag` và `.claude/skills/brag-slim`.*

---

## Slide 15: "Luật sáng tạo" của Skill & 4 thứ nhận về

- **Bốn thứ nhận về trong `brag-output/`:**
  1. `brag-plan.md`: kịch bản phân cảnh.
  2. `brag.mp4`: video trailer hoàn chỉnh.
  3. `brag.jpg`: ảnh bìa đại diện.
  4. `share-copy.txt`: caption mạng xã hội.
- **Luật sáng tạo:** Video ngắn 15–25 giây, 2 giây đầu quyết định tất cả, phải thấy sản phẩm thật, cấm câu chung chung.

---

## Slide 16: Bước C4 — Xuất video đầu tiên với 1 câu lệnh

Gõ câu lệnh vào Claude Code:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```

*Bạn sẽ thấy: Claude dùng bản gọn `/brag-slim`, viết kịch bản, dựng hình và thông báo đường dẫn file `brag.mp4`.*

---

## Slide 17: Bước C5 — So sánh trước và sau khi có skill

So sánh chất lượng kịch bản:

```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```

*Bạn sẽ thấy: Bảng đối chiếu 3 dòng rõ rệt. Mở thêm video `brag.mp4` của tác giả để đối chiếu.*

---

## Slide 18: Đạo diễn bằng lời: Tông & Khổ hình

- **7 phong cách tông có sẵn:** `default`, `polished`, `yc-parody`, `chaotic`, `deadpan`, `cinematic`, `app-store`.
- **Khổ hình:** Ngang (mặc định), Dọc (TikTok/Reels), Vuông.
- Chạy lần hai không ghi đè: Tự động lưu thư mục mới có ngày giờ.

---

## Slide 19: Bước C6 & C7 — Đổi tông & Làm bản dọc TikTok

**Bước 6: Đổi tông mặt lạnh (deadpan):**
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```

**Bước 7: Làm bản dọc TikTok & Reels (1080x1920):**
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```

---

## Slide 20: Bước C8 — Sửa một cảnh, không quay lại từ đầu

Không ưng một chi tiết? Chỉ bảo ê-kíp quay lại đúng cảnh đó:

```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```

*Bạn sẽ thấy: Video mới chỉ khác phần đầu, kèm vài dòng giải thích.*

---

## Slide 21: Bước C9 — Việt hóa 3 caption đa kênh

Viết bài đăng theo văn phong từng nền tảng:

```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```

*Bạn sẽ thấy: 3 caption chuẩn giọng: Facebook sôi nổi, LinkedIn phân tích, Zalo súc tích.*

---

## Slide 22: Bước C10 — Video cho website của bạn

Thực hành trên chính website thực tế của học viên:

```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```

*Lưu ý: Video lấy chữ từ trang của bạn, trang sơ sài thì video sơ sài. Tuyệt đối không chạy trên thư mục chứa dữ liệu mật.*

---

## Slide 23: Phần D — 3 Nguyên tắc vàng tại Doanh nghiệp

1. **"5 lần làm tay rồi mới đóng gói":**  
   Đừng vội tạo agent/skill cho việc mới làm lần đầu. Thấy rõ khuôn mẫu rồi mới đóng gói.
2. **"Chia phòng riêng cho việc nặng":**  
   Đọc tài liệu dài, tra cứu web, dựng video $\rightarrow$ giao Subagent phụ ở phòng riêng. Bàn làm việc chính luôn sạch sẽ.
3. **"Bắt buộc có khâu kiểm duyệt":**  
   Tài liệu quan trọng luôn áp dụng mô hình **Maker – Checker** trước khi người thật duyệt.

---

## Slide 24: Bảng Prompt tra nhanh Buổi 06

| Phần | Mục đích | Lệnh tóm tắt |
|---|---|---|
| **A** | Kiểm tra đồ nghề | `Liệt kê ngắn gọn CLAUDE.md, .claude/skills/, .claude/agents/` |
| **B** | Tuyển Trưởng phòng | `Tạo agent truong-phong-tham-dinh.md chỉ đọc, soi lỗi số liệu...` |
| **B** | Chạy phản biện | `chuyen-vien-de-xuat soạn -> truong-phong soi -> chuyên viên sửa` |
| **C** | Cài skill video | `Cài skill brag và brag-slim từ repo...` |
| **C** | Dựng video | `/brag cho sản phẩm trong san-pham-mau/horse-tinder` |
| **C** | Đổi tông / Bản dọc | Thêm tham số `tông deadpan` hoặc `bản dọc TikTok 18s` |
| **C** | Sửa 1 cảnh | `Làm lại riêng cảnh mở đầu cho mạnh hơn...` |
| **C** | Caption tiếng Việt | `Đọc share-copy.txt viết 3 bản Facebook, LinkedIn, Zalo` |
| **C** | Video website thật | `/brag https://[website-cua-ban]` |

---

## Slide 25: Bức tranh toàn cảnh 6 Buổi học

```text
Buổi 1: Khởi động AI Workspace & Cài đặt Skill đầu tiên
Buổi 2: Đóng gói Skill nghiệp vụ & Kỷ luật Chống bịa số
Buổi 3: Phân tích Dữ liệu, Kết nối MCP & Đặt lịch Routine
Buổi 4: Soạn thảo Đa phương tiện & Điều phối Subagent
Buổi 5: Agent Deep Research & Đội ngũ Nối chuỗi / Song song
Buổi 6: Toàn Cảnh AI Workspace, Vòng Lặp Tự Phản Biện & Thuê Ê-kíp Media
```

---

## Slide 26: Lời kết khóa học — Trở thành Chỉ huy Trưởng AI

> **"Bạn không còn là người gõ từng dòng lệnh đơn lẻ.**  
> **Bạn đã trở thành Giám đốc điều hành của một Văn phòng AI thu nhỏ: từ Nghiên cứu, Chiến lược, Soạn thảo, Thẩm định cho tới Sản xuất Truyền thông!"**

Chúc các anh chị học viên ứng dụng thành công và bứt phá năng suất vượt bậc tại doanh nghiệp!
