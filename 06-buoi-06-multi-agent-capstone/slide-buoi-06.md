# Nội dung slide Buổi 06: Thuê Ê-kíp Media — Một Câu Lệnh Ra Video Trailer Quảng Cáo

> Dùng cho GV trình chiếu và giảng dạy. Phong cách CES: Nền tối công nghệ cao hoặc nền sáng doanh nghiệp, chữ to rõ, bám sát từng bước thao tác và prompt thực tế.
> Mỗi `---` tương ứng với 1 slide. Tổng cộng: 22 slide chuẩn nhịp 150 phút.

---

## Slide 1: Slide tiêu đề

**KHÓA AI WORKSPACE: LÀM CHỦ AGENT VỚI CLAUDE CODE**

### Buổi 06: Thuê Ê-kíp Media — Một Câu Lệnh Ra Video Trailer Quảng Cáo

CES Global | Trung tâm Đào tạo & Ứng dụng Công nghệ  
*Website: nhanvienai.cesglobal.com.vn*

[Ghi chú GV: Buổi đúc kết bùng nổ cuối khóa. Nối tiếp hình tượng "Công ty thu nhỏ" từ Buổi 5: Công ty thuê hẳn một ê-kíp sản xuất video trailer quảng cáo chuyên nghiệp.]

---

## Slide 2: Xương sống buổi học hôm nay (150 phút)

| Phần | Nội dung | Học viên cầm được |
|---|---|---|
| **A** | Thuê ê-kíp về công ty | 5 sản phẩm mẫu + Bản kế hoạch trước khi có skill + Đã cài skill |
| **B** | Một câu lệnh ra một video | Video đầu tiên + Bảng so sánh trước & sau |
| **C** | Đạo diễn bằng lời | Video đổi tông (deadpan) + Video bản dọc TikTok |
| **D** | Sửa một cảnh | Video đã sửa cảnh mở đầu + 3 caption tiếng Việt |
| **E** | Sản phẩm thật & Giới hạn | Video trailer cho website của chính mình |

---

## Slide 3: Phần A — Thuê ê-kíp về công ty

### Skill làm video là gì, vì sao cần?

- **Skill là quyển công thức** (đã học từ Buổi 2).
- `/brag` là quyển công thức của cả một **ê-kíp làm trailer**:
  - Biên kịch kịch bản phân cảnh.
  - Họa sĩ dựng hình chuyển động.
  - Nhạc sĩ hòa âm phối khí.
  - Chuyên viên viết caption mạng xã hội.
- Không có skill, Claude vẫn viết được kịch bản, nhưng chung chung, sản phẩm nào cũng như nhau!

---

## Slide 4: Hai nguyên tắc bảo vệ công ty

1. **Cài cấp thư mục dự án:**  
   - Ê-kíp chỉ làm việc trong văn phòng này, không tự ý chạy sang máy khác hay thư mục khác.
2. **Kiểm tra lý lịch trước khi cho vào cửa:**  
   - Trước khi cài skill lạ từ bên ngoài, luôn bắt Claude đọc và báo cáo trước (chống bẫy câu lệnh ẩn *Prompt Injection* từ Buổi 5).

---

## Slide 5: Bước 1 — Lấy 5 sản phẩm mẫu

Gõ câu lệnh vào Claude Code để tải kho tư liệu:

```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```

*Bạn sẽ thấy: 5 sản phẩm mẫu độc lạ (xe đạp cho rắn, app hẹn hò cho ngựa horse-tinder, trường dạy bay cho cá...).*

---

## Slide 6: Bước 2 — Thử làm khi chưa có ê-kíp

Thử thách nhờ Claude viết kịch bản chay:

```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```

*Bạn sẽ thấy: Một kế hoạch đọc được nhưng an toàn, thiếu năng lượng và ít dùng từ ngữ của chính sản phẩm.*

---

## Slide 7: Bước 3 — Cài skill ê-kíp làm trailer

Cài đặt 2 skill `brag` và `brag-slim`:

```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```

*Bạn sẽ thấy: Thư mục `.claude/skills/brag` và `.claude/skills/brag-slim` xuất hiện an toàn.*

---

## Slide 8: Phần B — Một câu lệnh ra một video

### Ê-kíp vận hành thế nào sau 1 câu lệnh?

1. **Khảo sát:** Đọc sâu toàn bộ trang sản phẩm hoặc website.
2. **Biên kịch:** Viết kịch bản phân cảnh chi tiết từng giây (`brag-plan.md`).
3. **Dựng hình & Render:** Tạo chuyển động, nhịp điệu và xuất video (`brag.mp4`).
4. **Viết caption:** Soạn sẵn thông điệp truyền thông (`share-copy.txt`).

---

## Slide 9: "Luật sáng tạo" của Skill

- **Thời lượng vàng:** Video ngắn từ 15 đến 25 giây.
- **2 giây đầu quyết định tất cả:** Phải có "visual hook" đập ngay vào mắt người xem.
- **Hiện thực sống động:** Phải cho thấy sản phẩm thật đang chạy, cấm tuyệt đối các câu khẩu hiệu chung chung!
- *Lưu ý: Quá trình dựng mất vài phút và tốn token.*

---

## Slide 10: Bước 4 — Xuất video đầu tiên

Gõ 1 câu lệnh duy nhất:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```

*Bạn sẽ thấy: Claude chuyển sang dùng bản gọn `/brag-slim`, tự động viết kịch bản, dựng hình và thông báo đường dẫn file `brag.mp4` trong thư mục `brag-output/`.*

---

## Slide 11: Bước 5 — So sánh Trước và Sau

Đối chiếu sự khác biệt giữa "làm chay" và "có Skill ê-kíp":

```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```

*Bạn sẽ thấy: Bảng đối chiếu 3 dòng rõ rệt. Mở thêm video `brag.mp4` của tác giả để chiêm ngưỡng.*

---

## Slide 12: Phần C — Đạo diễn bằng lời

### Cùng một sản phẩm, đổi đạo diễn là ra phim khác!

- **7 phong cách tông có sẵn:**
  - `default` (tiêu chuẩn), `polished` (mượt mà, chỉn chu)
  - `yc-parody` (phong cách startup Thung lũng Silicon)
  - `chaotic` (hỗn loạn, dồn dập, giật gân)
  - `deadpan` (mặt lạnh, nghiêm túc hài hước)
  - `cinematic` (điện ảnh, kịch tính)
  - `app-store` (tươi sáng phong cách kho ứng dụng)
- **Đa dạng khổ hình:** Ngang (màn hình máy tính), Dọc (TikTok/Reels), Vuông (Instagram).

---

## Slide 13: Bước 6 — Đổi tông (Deadpan / Mặt lạnh)

Yêu cầu ê-kíp đổi phong cách diễn xuất:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```

*Bạn sẽ thấy: Thư mục kết quả mới có ngày giờ. Video nhịp chậm hơn, ít cảnh hơn, tạo cảm giác hài hước ngầm.*

---

## Slide 14: Bước 7 — Dựng bản dọc cho TikTok & Reels

Ra lệnh làm định dạng video dọc 1080x1920:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```

*Bạn sẽ thấy: Video xuất ra định dạng dọc 1080x1920, giao diện và hiệu ứng bố cục lại hoàn toàn phù hợp màn hình điện thoại.*

---

## Slide 15: Phần D — Sửa một cảnh, không quay lại từ đầu

### Tư duy chỉ đạo đạo diễn chuyên nghiệp

- Không ưng một chi tiết? **Chỉ yêu cầu quay lại cảnh đó**, không bắt làm lại từ đầu cả bộ phim.
- **Nguyên tắc góp ý:** Nêu rõ cảnh nào $\rightarrow$ chưa được ở đâu $\rightarrow$ muốn sửa thế nào.
- **Caption đa kênh:** Dịch và bản địa hóa tiếng Việt theo đúng ngữ cảnh từng nền tảng, không tự bịa đặt tính năng.

---

## Slide 16: Bước 8 — Sửa cảnh mở đầu

Chỉ đạo sửa riêng đoạn mở đầu:

```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```

*Bạn sẽ thấy: Video mới xuất xưởng chỉ thay đổi phân cảnh đầu tiên, kèm lời báo cáo chi tiết.*

---

## Slide 17: Bước 9 — Viết 3 caption tiếng Việt đa kênh

Yêu cầu ê-kíp viết bài đăng mạng xã hội:

```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```

*Bạn sẽ thấy: 3 bài đăng chuẩn văn phong: Facebook trẻ trung, LinkedIn chuyên nghiệp, Zalo ngắn gọn súc tích.*

---

## Slide 18: Phần E — Áp vào sản phẩm thật & Giới hạn

### Giới hạn cần nói thẳng (Minh bạch)

1. **Chất lượng đầu vào quyết định đầu ra:** Video lấy chữ và hình từ trang web của bạn; trang sơ sài thì video sơ sài.
2. **An toàn dữ liệu:** Mọi thứ trong thư mục đều có thể lên hình, vì vậy **tuyệt đối không chạy trên thư mục chứa dữ liệu mật hoặc danh sách khách hàng**.
3. **Bản đầy đủ (`/brag --full`):** Có thêm lồng tiếng AI và nhạc đồng bộ nhịp nhưng cần công cụ chuyên biệt (Hyperframes).

---

## Slide 19: Bước 10 — Video cho website của bạn

Thực hành trên chính doanh nghiệp của học viên:

```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```

*Bạn sẽ thấy: Video trailer dùng đúng màu sắc nhận diện thương hiệu, phông chữ và thông điệp thực tế của website bạn!*

---

## Slide 20: Bảng tổng kết 10 Bước Tác Chiến

| # | Thao tác chính | Lệnh tóm tắt |
|---|---|---|
| 1 | Lấy mẫu | Tải thư mục examples về `san-pham-mau` |
| 2 | Làm chay | Viết kế hoạch khi chưa có skill |
| 3 | Cài skill | Cài `brag` & `brag-slim` vào `.claude/skills` |
| 4 | Dựng video 1 | `/brag cho sản phẩm trong san-pham-mau/horse-tinder` |
| 5 | So sánh | So `ke-hoach-truoc-khi-co-skill.md` vs `brag-plan.md` |
| 6 | Đổi tông | Thêm tham số tông `deadpan` |
| 7 | Bản dọc | Thêm tham số `bản dọc TikTok 18 giây` |
| 8 | Sửa cảnh | Yêu cầu sửa riêng cảnh mở đầu |
| 9 | Viết caption | Việt hóa 3 caption Facebook, LinkedIn, Zalo |
| 10 | Làm việc thật | `/brag https://[website-cua-ban]` |

---

## Slide 21: Bức tranh toàn cảnh 6 Buổi học

```text
Buổi 1: Khởi động AI Workspace & Cài đặt Skill đầu tiên
Buổi 2: Đóng gói Skill nghiệp vụ & Kỷ luật Chống bịa số
Buổi 3: Phân tích Dữ liệu, Kết nối MCP & Đặt lịch Routine
Buổi 4: Soạn thảo Đa phương tiện & Điều phối Subagent
Buổi 5: Agent Deep Research & Đội ngũ Nối chuỗi / Song song
Buổi 6: Thuê Ê-kíp Media tự động sản xuất Video Trailer
```

---

## Slide 22: Lời kết khóa học — Trở thành Chỉ huy Trưởng AI

> **"Bạn không còn là người gõ từng dòng lệnh đơn lẻ.**  
> **Bạn đã trở thành Giám đốc điều hành của một Văn phòng AI thu nhỏ: từ Nghiên cứu, Chiến lược, Soạn thảo, Thẩm định cho tới Sản xuất Truyền thông!"**

Chúc các anh chị học viên ứng dụng thành công và bứt phá năng suất vượt bậc tại doanh nghiệp!
