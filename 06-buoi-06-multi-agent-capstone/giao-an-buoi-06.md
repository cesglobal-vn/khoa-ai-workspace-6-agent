# Buổi 06: Toàn Cảnh Hệ Sinh Thái Claude, Vòng Lặp Tự Phản Biện & Thuê Ê-kíp Media

> **Cách dùng file này:** Mỗi phần có hai khúc. Khúc **Giảng** đọc để hiểu mình sắp làm gì và vì sao, có ví von cho dễ nhớ. Khúc **Thao tác** là các bước có sẵn prompt bằng tiếng Việt tự nhiên, cứ copy dán vào Claude Code.
>
> Làm lần lượt, không nhảy cóc. Bước sau dùng kết quả bước trước.
>
> **Bốn phần đi từ nền tảng đến thực chiến đỉnh cao:**
> - **Phần A:** Toàn cảnh Hệ sinh thái Claude & Bản đồ AI Workspace (Rà soát túi đồ nghề)
> - **Phần B:** Vũ khí mới 1 — Vòng lặp Tự phản biện Maker – Checker (Chuyên viên soạn, Trưởng phòng soi)
> - **Phần C:** Vũ khí mới 2 — Thuê ê-kíp media ngoại viện làm video trailer quảng cáo (`/brag-slim`)
> - **Phần D:** Lộ trình ứng dụng tại Doanh nghiệp & Tổng kết khóa học

---

## Nhịp buổi học (150 phút)

| Phần | Nội dung | Học viên cầm được | Thời lượng | Bước thực hành |
|---|---|---|---|---|
| **A** | Toàn cảnh Hệ sinh thái Claude & AI Workspace | Hiểu rõ 4 cấp độ dùng Claude, rà soát đủ bộ não 4 tầng | 25 phút | Kiểm tra túi đồ nghề |
| **B** | Vòng lặp Tự phản biện (Maker – Checker) | Trưởng phòng thẩm định, quy trình tự sửa sai từ 7/10 lên 9.5/10 | 40 phút | Tuyển Trưởng phòng & Chạy phản biện |
| | **Nghỉ giải lao** | Trợ giảng hỗ trợ học viên kiểm tra agent và skill | 10 phút | |
| **C** | Thuê ê-kíp Media: 1 câu lệnh ra video trailer | Skill video đã cài, video trailer `.mp4`, bản dọc TikTok, 3 caption | 50 phút | 10 bước tác chiến video |
| **D** | Lộ trình Doanh nghiệp & Tổng kết khóa | 3 nguyên tắc vàng đóng gói quy trình, bảng prompt tra nhanh | 25 phút | Q&A theo ngành nghề |

---

## PHẦN A. Toàn Cảnh Hệ Sinh Thái Claude & Bản Đồ AI Workspace

### 1. Giảng (Nội dung nói / đọc):

Nhiều người dùng AI cả năm trời nhưng vẫn chỉ dừng lại ở mức "hỏi một câu - máy đáp một câu". Để làm chủ AI thực sự trong công việc, ta cần nhìn rõ **4 cấp độ dùng Claude**:

1. **Cấp độ 1 — Claude Web / App (Nhắn tin với cộng tác viên online):**
   - *Đặc điểm:* Giao diện chat quen thuộc trên trình duyệt hoặc điện thoại.
   - *Hạn chế:* Đóng cửa sổ là hết phiên làm việc. Tải file lên bị giới hạn dung lượng. AI không chạm được vào thư mục trên máy tính của bạn. Phù hợp cho việc tra cứu nhanh, giải thích khái niệm.
2. **Cấp độ 2 — Claude Projects trên Web (Tủ tài liệu dùng chung):**
   - *Đặc điểm:* Cho phép tải sẵn tài liệu nền tảng và hướng dẫn tùy chỉnh.
   - *Hạn chế:* AI chỉ đọc tài liệu thụ động. Không thể tự tạo file mới lưu về máy, không chạy được lệnh và không kết nối được hệ thống nội bộ.
3. **Cấp độ 3 — Claude Desktop + MCP (Trợ lý có công cụ kết nối):**
   - *Đặc điểm:* Cài trên máy tính, gắn thêm được các cổng MCP (đọc Drive, Gmail...).
   - *Hạn chế:* Vẫn là giao diện đóng khung, thao tác từng lượt chat đơn lẻ, chưa có khả năng tự động điều phối nhiều nhân viên làm việc độc lập.
4. **Cấp độ 4 — Claude Code / AI Workspace (Giám đốc điều hành văn phòng AI):**
   - *Đặc điểm:* Đây chính là môi trường cả lớp đã thực hành suốt 5 buổi qua. AI ngồi trực tiếp tại thư mục làm việc, có toàn quyền đọc/ghi file, tự chạy kiểm tra, tự gọi trợ lý phụ (subagent) và ghi nhớ toàn bộ văn hóa làm việc của công ty.

---

### 2. Xâu chuỗi "Bộ não 4 tầng" của AI Workspace

```text
┌─────────────────────────────────────────────────────────────┐
│ 1. NỘI QUY & VĂN HÓA (CLAUDE.md)                            │
│    -> Giữ AI luôn đúng vai, đúng xưng hô, cấm bịa số        │
├─────────────────────────────────────────────────────────────┤
│ 2. QUY TRÌNH THAO TÁC CHUẨN - SOP (Skills)                  │
│    -> Các công thức lặp lại: Tóm tắt tài liệu, làm slide    │
├─────────────────────────────────────────────────────────────┤
│ 3. CÁNH TAY NỐI DÀI NGOẠI VI (MCP)                          │
│    -> Chạm ra ngoài máy: Google Drive, Gmail...             │
├─────────────────────────────────────────────────────────────┤
│ 4. BIÊN CHẾ NHÂN SỰ CHUYÊN BIỆT (Agents & Subagents)        │
│    -> Nhân viên chuyên trách có phòng riêng & chìa khóa riêng│
└─────────────────────────────────────────────────────────────┘
```

---

### 3. Thao tác: Kiểm tra "Túi đồ nghề"

Học viên mở Claude Code tại thư mục làm việc và gõ câu lệnh sau:

```text
Liệt kê ngắn gọn giúp tôi:
1. File CLAUDE.md đang có những quy tắc chính nào?
2. Thư mục .claude/skills/ đang có những skill gì?
3. Thư mục .claude/agents/ đang có những agent nào?
```

> **Bạn sẽ thấy:** Claude rà soát toàn bộ thư mục và báo cáo danh sách tài sản AI mà học viên đang sở hữu sau 5 buổi học.

---

## PHẦN B. Vũ Khí Mới 1: Vòng Lặp Tự Phản Biện (Maker – Checker Loop)

### 1. Giảng: Tại sao cần "Trưởng phòng soi lỗi"?

- Ở **Buổi 5**, chúng ta đã cho 2 nhân viên phối hợp **Nối chuỗi tuần tự**: Nhân viên nghiên cứu (`nghien-cuu-doi-thu`) bàn giao số liệu -> Nhân viên đề xuất (`chuyen-vien-de-xuat`) viết phương án.
- **Vấn đề thực tế công sở:** Bản thảo đầu tiên của nhân viên viết ra thường chỉ đạt mức 7/10 điểm: có thể văn phong còn chung chung, số liệu thiếu nguồn chứng minh, hoặc giải pháp thiếu tính khả thi.
- Nếu người dùng phải tự ngồi đọc từng dòng để sửa thì rất mất thời gian.
- **Giải pháp:** Thiết lập mô hình **Maker – Checker (Người làm – Người duyệt)**:
  - **Maker (`chuyen-vien-de-xuat`):** Chuyên viên soạn thảo bản kế hoạch/báo cáo.
  - **Checker (`truong-phong-tham-dinh`):** Vị Trưởng phòng khó tính, nắm giữ bộ tiêu chuẩn thẩm định khắt khe. Trưởng phòng đọc bản thảo, chỉ ra đúng 3 điểm yếu kém, bắt Chuyên viên sửa lại.
  - Sau 1–2 vòng phản biện tự động, văn bản nộp lên bạn sẽ đạt chất lượng **9.5/10 điểm**.

---

### 2. Thao tác:

#### Bước B1. Tuyển Trưởng phòng thẩm định (`truong-phong-tham-dinh`)

Gõ câu lệnh sau vào Claude Code:

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

> **Bạn sẽ thấy:** File `.claude/agents/truong-phong-tham-dinh.md` xuất hiện. Người này chỉ có quyền đọc (`Read`), là một giám định viên khách quan không tự ý viết đè vào tài liệu.

---

#### Bước B2. Kích hoạt Vòng lặp phản biện: Soạn thảo -> Thẩm định -> Hoàn thiện

Gõ câu lệnh kích hoạt vòng lặp tự động:

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

#### Bước B3. Soi kết quả: Bản nháp ban đầu vs Bản sau khi phản biện

Gõ lệnh mở và đối chiếu 2 file:

```text
Hãy tóm tắt và chỉ ra 3 điểm khác biệt lớn nhất giữa bản nháp đầu tiên ("ket-qua/ban-nhap-de-xuat.md") và bản đã hoàn thiện sau phản biện ("ket-qua/de-xuat-hoan-thien.md").
```

> **Bạn sẽ thấy:** Bản hoàn thiện đã được bổ sung số liệu minh chứng rõ ràng, loại bỏ các câu từ mơ hồ và có thêm phương án phòng ngừa rủi ro — đúng chuẩn một báo cáo cấp quản lý mong muốn.

---

## PHẦN C. Vũ Khí Mới 2: Thuê Ê-kíp Media Ngoại Viện — Một Câu Lệnh Ra Video Trailer (`/brag`)

> **Ví von xuyên suốt, nối tiếp "công ty thu nhỏ" của buổi 05:** Công ty thuê một ê-kíp làm trailer quảng cáo.

### C1. Thuê ê-kíp về công ty

#### Giảng:
- Skill là quyển công thức (buổi 2). `/brag` là quyển công thức của một ê-kíp làm trailer: biên kịch, dựng hình, làm nhạc, viết caption.
- Không có skill, Claude vẫn viết được kế hoạch video, nhưng chung chung, sản phẩm nào cũng dùng được. Bước 2 cho học viên tự thấy điều đó.
- Cài cấp thư mục nghĩa là ê-kíp chỉ làm cho văn phòng này, không theo sang máy khác.
- Trước khi cho người lạ vào công ty phải xem hồ sơ: bảo Claude đọc skill rồi báo lại trước khi cài. Ý này nối với bài "bẫy câu lệnh ẩn" của buổi 05.

#### Bước 1. Lấy 5 sản phẩm mẫu (học viên tự làm)
```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```
**Bạn sẽ thấy:** 5 thư mục, gồm xe đạp cho rắn, trường dạy bay cho cá, app hẹn hò cho ngựa, bác sĩ tâm lý cho chatbot, taxi chở taxi.

#### Bước 2. Thử làm khi chưa có ê-kíp (học viên tự làm)
```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```
**Bạn sẽ thấy:** Một kế hoạch đọc được nhưng an toàn, ít dùng chữ của chính sản phẩm.

#### Bước 3. Cài skill (học viên tự làm)
```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```
**Bạn sẽ thấy:** Claude tóm tắt skill rồi tạo `.claude/skills/brag` và `.claude/skills/brag-slim`. Nếu gõ `/brag` chưa nhận thì mở phiên mới.

---

### C2. Một câu lệnh ra một video

#### Giảng:
- Ê-kíp làm 4 việc theo thứ tự: khảo sát sản phẩm, viết kịch bản phân cảnh, dựng và xuất video, viết caption.
- Bốn thứ nhận về trong `brag-output/`:
  - `brag-plan.md`: kịch bản.
  - `brag.mp4`: video.
  - `brag.jpg`: ảnh bìa.
  - `share-copy.txt`: caption.
- **Nói thẳng:** Mỗi lần dựng mất vài phút và tốn token. Trong lúc chờ, giảng viên giảng "luật sáng tạo" của skill: video ngắn 15–25 giây, 2 giây đầu quyết định tất cả, phải cho thấy sản phẩm thật, cấm câu chung chung.

#### Bước 4. Video đầu tiên (học viên tự làm, mỗi bàn một sản phẩm khác nhau)
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```
**Bạn sẽ thấy:** Claude báo đang dùng bản gọn `/brag-slim`, viết kịch bản, dựng hình, rồi báo đường dẫn tới `brag.mp4`.

#### Bước 5. So trước và sau (học viên tự làm)
```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```
**Bạn sẽ thấy:** Bảng 3 dòng. Sau đó mở thêm `brag.mp4` có sẵn trong thư mục mẫu (bản của tác giả) để so với bản của mình.

---

### C3. Đạo diễn bằng lời

#### Giảng:
- Cùng một sản phẩm, đổi đạo diễn là ra phim khác.
- 7 tông có sẵn: `default`, `polished`, `yc-parody`, `chaotic`, `deadpan`, `cinematic`, `app-store`. Tả bằng lời thường cũng được.
- Khổ hình: ngang (mặc định), dọc cho TikTok/Reels, vuông.
- Chạy lần hai không ghi đè: skill tự tạo thư mục mới có ngày giờ.

#### Bước 6. Đổi tông (học viên tự làm, mỗi bàn một tông)
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```
**Bạn sẽ thấy:** Thư mục kết quả thứ hai, video chậm hơn, ít cảnh hơn, nhiều khoảng trống.

#### Bước 7. Bản dọc (giảng viên demo, học viên xem, để tiết kiệm thời gian dựng)
```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```
**Bạn sẽ thấy:** Video 1080x1920, bố cục xếp lại theo chiều dọc.

---

### C4. Quay lại một cảnh

#### Giảng:
- Không ưng một cảnh thì bảo ê-kíp quay lại cảnh đó, không làm lại cả phim.
- Góp ý phải cụ thể: cảnh nào, chưa được ở đâu, muốn thế nào.
- Caption gốc là tiếng Anh vì trang mẫu viết tiếng Anh. Việt hoá được, nhưng không được thêm lời khen hay con số không có thật.

#### Bước 8. Sửa cảnh mở đầu (học viên tự làm)
```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```
**Bạn sẽ thấy:** Video mới chỉ khác phần đầu, kèm vài dòng giải thích.

#### Bước 9. Caption tiếng Việt (học viên tự làm)
```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```
**Bạn sẽ thấy:** 3 caption ngắn, giọng khác nhau theo từng kênh.

---

### C5. Sản phẩm thật và giới hạn

#### Giảng:
- Bản gọn nhận cả địa chỉ website, không cần có mã nguồn.
- **Giới hạn cần nói thẳng:**
  - Video lấy chữ từ trang của bạn, trang sơ sài thì video sơ sài.
  - Mọi thứ skill đọc được có thể lên hình, nên không chạy trên thư mục chứa dữ liệu khách hàng.
  - Phải xem lại video trước khi đăng.
- **Chỉ cần hiểu, chưa cần làm:** Bản đầy đủ (`/brag --full`) có lồng tiếng và nhạc kèm sẵn, nhưng phải cài thêm Hyperframes.

#### Bước 10. Video cho website của bạn (học viên tự làm, hoặc bài tập về nhà)
```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```
**Bạn sẽ thấy:** Video dùng đúng màu, phông chữ và câu chữ của website bạn.

---

## PHẦN D. Lộ Trình Ứng Dụng Tại Doanh Nghiệp & Tổng Kết Khóa

### 1. Ba nguyên tắc vàng khi tự đóng gói quy trình tại cơ quan

1. **Nguyên tắc "5 lần làm tay rồi mới đóng gói":**  
   Đừng vội tạo agent hay skill cho một việc bạn mới làm lần đầu. Hãy làm việc đó bằng tay 4–5 lần với Claude, khi đã thấy rõ mẫu số chung thì mới đóng gói thành Skill hoặc Agent.
2. **Nguyên tắc "Chia phòng riêng cho việc nặng":**  
   Việc gì liên quan đến đọc hàng chục tài liệu hoặc tra cứu ngoài mạng thì luôn giao cho Agent/Subagent phụ. Bàn làm việc chính chỉ nhận file báo cáo tổng hợp cuối cùng.
3. **Nguyên tắc "Bắt buộc có khâu kiểm duyệt":**  
   Với các tài liệu quan trọng gửi sếp, khách hàng hay đối tác, luôn áp dụng cặp đôi **Maker – Checker**: Một trợ lý soạn và một trợ lý soi lỗi trước khi người thật duyệt lần cuối.

---

### 2. Bảng Prompt Tra Nhanh Của Buổi Học

| STT | Mục đích | Câu lệnh mẫu (Tiếng Việt tự nhiên) |
|---|---|---|
| **A** | Rà soát đồ nghề | `Liệt kê ngắn gọn CLAUDE.md, thư mục .claude/skills/ và .claude/agents/ của tôi.` |
| **B1** | Tuyển Trưởng phòng thẩm định | `Tạo agent truong-phong-tham-dinh.md, chỉ có quyền đọc file, chuyên soi lỗi số liệu và văn phong...` |
| **B2** | Chạy Maker – Checker | `Nhờ chuyen-vien-de-xuat soạn nháp -> truong-phong-tham-dinh nhận xét -> chuyen-vien-de-xuat sửa lại và xuất bản-hoan-thien.md.` |
| **C1** | Tải 5 mẫu video | `Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy...` |
| **C2** | Thử làm trước khi có skill | `Đọc trang sản phẩm trong san-pham-mau/horse-tinder rồi viết kế hoạch video 20s...` |
| **C3** | Cài skill brag | `Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào .claude/skills...` |
| **C4** | Ra lệnh xuất video | `/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"` |
| **C5** | So sánh trước và sau | `So sánh hai file ke-hoach-truoc-khi-co-skill.md và brag-plan.md...` |
| **C6** | Đổi tông cảm xúc | `/brag cho sản phẩm..., lần này dùng tông deadpan...` |
| **C7** | Bản dọc TikTok | `/brag cho sản phẩm..., làm bản dọc để đăng TikTok và Reels, dài 18 giây.` |
| **C8** | Sửa cảnh mở đầu | `Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên...` |
| **C9** | 3 Caption tiếng Việt | `Đọc share-copy.txt viết lại thành 3 phiên bản tiếng Việt: Facebook, LinkedIn, Zalo...` |
| **C10** | Video cho website thật | `/brag https://[website-cua-ban], tập trung vào [san-pham]...` |
