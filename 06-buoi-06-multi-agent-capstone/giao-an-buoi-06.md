# Buổi 06: Thuê Ê-kíp Media — Một Câu Lệnh Ra Video Trailer Quảng Cáo

> **Cách dùng file này:** Mỗi phần có hai khúc. Khúc **Giảng** đọc để hiểu mình sắp làm gì và vì sao, có ví von cho dễ nhớ. Khúc **Thao tác** là các bước có sẵn prompt bằng tiếng Việt tự nhiên, cứ copy dán vào Claude Code.
>
> Làm lần lượt, không nhảy cóc. Bước sau dùng kết quả bước trước.
>
> **Ví von xuyên suốt, nối tiếp "công ty thu nhỏ" của buổi 05:** Công ty thuê một ê-kíp làm trailer quảng cáo.
>
> Năm phần đi từ dễ tới khó:
> - **Phần A:** Skill làm video là gì, vì sao cần (Bước 1–3)
> - **Phần B:** Một câu lệnh ra một video (Bước 4–5)
> - **Phần C:** Đạo diễn bằng lời: tông, khổ hình, độ dài (Bước 6–7)
> - **Phần D:** Sửa một cảnh, không quay lại từ đầu (Bước 8–9)
> - **Phần E:** Áp vào sản phẩm thật và giới hạn (Bước 10)

---

## Nhịp buổi học (150 phút)

| Phần | Khái niệm dạy | Học viên cầm được | Thời lượng | Bước |
|---|---|---|---|---|
| **A** | Skill làm video là gì, vì sao cần | Skill đã cài, 5 sản phẩm mẫu, một bản kế hoạch "trước khi có skill" | 30 phút | 1–3 |
| **B** | Một câu lệnh ra một video | Video đầu tiên và bảng so sánh trước/sau | 35 phút | 4–5 |
| | **Nghỉ giải lao** | Trợ giảng hỗ trợ học viên hoàn thiện cài skill | 10 phút | |
| **C** | Đạo diễn bằng lời: tông, khổ hình, độ dài | Một bản video khác tông | 25 phút | 6–7 |
| **D** | Sửa một cảnh, không quay lại từ đầu | Video đã sửa và 3 caption tiếng Việt | 25 phút | 8–9 |
| **E** | Áp vào sản phẩm thật và giới hạn | Video cho website của chính mình | 25 phút | 10 |

---

## Phần A. Thuê ê-kíp về công ty

### Giảng:
- Skill là quyển công thức (buổi 2). `/brag` là quyển công thức của một ê-kíp làm trailer: biên kịch, dựng hình, làm nhạc, viết caption.
- Không có skill, Claude vẫn viết được kế hoạch video, nhưng chung chung, sản phẩm nào cũng dùng được. Bước 2 cho học viên tự thấy điều đó.
- Cài cấp thư mục nghĩa là ê-kíp chỉ làm cho văn phòng này, không theo sang máy khác.
- Trước khi cho người lạ vào công ty phải xem hồ sơ: bảo Claude đọc skill rồi báo lại trước khi cài. Ý này nối với bài "bẫy câu lệnh ẩn" của buổi 05.

---

### Thao tác:

#### Bước 1. Lấy 5 sản phẩm mẫu (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
Tải giúp tôi thư mục "examples" từ repo https://github.com/latent-spaces/brag về máy, đặt vào thư mục "san-pham-mau" ngay trong thư mục làm việc này. Chỉ lấy đúng thư mục examples, không lấy phần còn lại của repo. Xong thì liệt kê 5 sản phẩm mẫu có trong đó, mỗi cái một câu mô tả bằng tiếng Việt.
```

**Bạn sẽ thấy:** 5 thư mục, gồm xe đạp cho rắn, trường dạy bay cho cá, app hẹn hò cho ngựa, bác sĩ tâm lý cho chatbot, taxi chở taxi.

---

#### Bước 2. Thử làm khi chưa có ê-kíp (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
Đọc trang sản phẩm trong thư mục "san-pham-mau/horse-tinder" rồi viết cho tôi kế hoạch một video giới thiệu dài 20 giây: chia cảnh, chữ hiện trên màn hình, thời lượng từng cảnh. Chỉ viết kế hoạch, lưu vào file "ke-hoach-truoc-khi-co-skill.md", chưa dựng video.
```

**Bạn sẽ thấy:** Một kế hoạch đọc được nhưng an toàn, ít dùng chữ của chính sản phẩm.

---

#### Bước 3. Cài skill (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
Cài cho tôi skill từ repo https://github.com/latent-spaces/brag vào thư mục ".claude/skills" ngay trong thư mục làm việc này, cài cấp thư mục, không cài toàn máy. Lấy cả hai skill "brag" và "brag-slim". Chép file thật, không dùng symlink. Trước khi cài, đọc file SKILL.md của cả hai và báo cho tôi skill này sẽ làm những gì trên máy tôi.
```

**Bạn sẽ thấy:** Claude tóm tắt skill rồi tạo `.claude/skills/brag` và `.claude/skills/brag-slim`. Nếu gõ `/brag` chưa nhận thì mở phiên mới.

---

## Phần B. Một câu lệnh ra một video

### Giảng:
- Ê-kíp làm 4 việc theo thứ tự: khảo sát sản phẩm, viết kịch bản phân cảnh, dựng và xuất video, viết caption.
- Bốn thứ nhận về trong `brag-output/`:
  1. `brag-plan.md`: kịch bản.
  2. `brag.mp4`: video.
  3. `brag.jpg`: ảnh bìa.
  4. `share-copy.txt`: caption.
- **Nói thẳng:** Mỗi lần dựng mất vài phút và tốn token. Trong lúc chờ, giảng viên giảng "luật sáng tạo" của skill: video ngắn 15–25 giây, 2 giây đầu quyết định tất cả, phải cho thấy sản phẩm thật, cấm câu chung chung.

---

### Thao tác:

#### Bước 4. Video đầu tiên (học viên tự làm, mỗi bàn một sản phẩm khác nhau)

Gõ câu lệnh sau vào Claude Code:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder"
```

**Bạn sẽ thấy:** Claude báo đang dùng bản gọn `/brag-slim`, viết kịch bản, dựng hình, rồi báo đường dẫn tới `brag.mp4`.

---

#### Bước 5. So trước và sau (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
So sánh hai file "ke-hoach-truoc-khi-co-skill.md" và file "brag-plan.md" trong thư mục kết quả vừa tạo. Chỉ ra 3 điểm khác nhau lớn nhất: cách mở đầu, cách dùng chữ của chính sản phẩm, độ dài từng cảnh. Trả lời ngắn, dạng bảng.
```

**Bạn sẽ thấy:** Bảng 3 dòng. Sau đó mở thêm `brag.mp4` có sẵn trong thư mục mẫu (bản của tác giả) để so với bản của mình.

---

## Phần C. Đạo diễn bằng lời

### Giảng:
- Cùng một sản phẩm, đổi đạo diễn là ra phim khác.
- 7 tông có sẵn: `default`, `polished`, `yc-parody`, `chaotic`, `deadpan`, `cinematic`, `app-store`. Tả bằng lời thường cũng được.
- Khổ hình: ngang (mặc định), dọc cho TikTok/Reels, vuông.
- Chạy lần hai không ghi đè: skill tự tạo thư mục mới có ngày giờ.

---

### Thao tác:

#### Bước 6. Đổi tông (học viên tự làm, mỗi bàn một tông)

Gõ câu lệnh sau vào Claude Code:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", lần này dùng tông deadpan: mặt lạnh, khô khan, coi như không có gì buồn cười.
```

**Bạn sẽ thấy:** Thư mục kết quả thứ hai, video chậm hơn, ít cảnh hơn, nhiều khoảng trống.

---

#### Bước 7. Bản dọc (giảng viên demo, học viên xem, để tiết kiệm thời gian dựng)

Gõ câu lệnh sau vào Claude Code:

```text
/brag cho sản phẩm trong thư mục "san-pham-mau/horse-tinder", làm bản dọc để đăng TikTok và Reels, dài khoảng 18 giây.
```

**Bạn sẽ thấy:** Video 1080x1920, bố cục xếp lại theo chiều dọc.

---

## Phần D. Quay lại một cảnh

### Giảng:
- Không ưng một cảnh thì bảo ê-kíp quay lại cảnh đó, không làm lại cả phim.
- Góp ý phải cụ thể: cảnh nào, chưa được ở đâu, muốn thế nào.
- Caption gốc là tiếng Anh vì trang mẫu viết tiếng Anh. Việt hoá được, nhưng không được thêm lời khen hay con số không có thật.

---

### Thao tác:

#### Bước 8. Sửa cảnh mở đầu (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
Trong video vừa làm, cảnh mở đầu chưa đủ gây chú ý. Làm lại riêng cảnh mở đầu cho mạnh hơn, các cảnh còn lại giữ nguyên. Xong thì xuất lại video và nói cho tôi biết bạn đã đổi gì.
```

**Bạn sẽ thấy:** Video mới chỉ khác phần đầu, kèm vài dòng giải thích.

---

#### Bước 9. Caption tiếng Việt (học viên tự làm)

Gõ câu lệnh sau vào Claude Code:

```text
Đọc file "share-copy.txt" trong thư mục kết quả rồi viết lại thành 3 phiên bản tiếng Việt: một cho Facebook, một cho LinkedIn, một cho nhóm Zalo khách hàng. Giữ đúng tinh thần bản gốc, không thêm số liệu hay lời khen nào không có trên trang sản phẩm.
```

**Bạn sẽ thấy:** 3 caption ngắn, giọng khác nhau theo từng kênh.

---

## Phần E. Sản phẩm thật và giới hạn

### Giảng:
- Bản gọn nhận cả địa chỉ website, không cần có mã nguồn.
- **Giới hạn cần nói thẳng:**
  - Video lấy chữ từ trang của bạn, trang sơ sài thì video sơ sài.
  - Mọi thứ skill đọc được có thể lên hình, nên không chạy trên thư mục chứa dữ liệu khách hàng.
  - Phải xem lại video trước khi đăng.
- **Chỉ cần hiểu, chưa cần làm:** Bản đầy đủ (`/brag --full`) có lồng tiếng và nhạc kèm sẵn, nhưng phải cài thêm Hyperframes.

---

### Thao tác:

#### Bước 10. Video cho website của bạn (học viên tự làm, hoặc bài tập về nhà)

Gõ câu lệnh sau vào Claude Code:

```text
/brag https://[dán địa chỉ website của bạn vào đây], tập trung vào [dán tên sản phẩm hoặc dịch vụ bạn muốn khoe nhất vào đây]. Chỉ dùng chữ và số liệu có thật trên trang, không bịa thêm lời chứng thực hay con số.
```

**Bạn sẽ thấy:** Video dùng đúng màu, phông chữ và câu chữ của website bạn.
