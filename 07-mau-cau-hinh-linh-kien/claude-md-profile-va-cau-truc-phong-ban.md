# Mẫu: CLAUDE.md theo profile cá nhân và cấu trúc phòng ban

> Dùng cho Buổi 3. Gồm 3 phần: hai cấp CLAUDE.md, mẫu profile theo phòng ban, và mẫu file index.

---

## Phần 1: Hai cấp CLAUDE.md

Có hai chỗ đặt CLAUDE.md, dùng cho hai mục đích khác nhau.

| Cấp | Đặt ở đâu | Áp cho | Nên ghi gì |
|---|---|---|---|
| **Cá nhân** | `C:\Users\<tên máy>\.claude\CLAUDE.md` | Mọi thư mục, mọi việc bạn làm | Bạn là ai, làm phòng ban nào, thói quen chung: tiếng Việt, không emoji, cách xưng hô |
| **Dự án hoặc phòng ban** | `CLAUDE.md` ở gốc thư mục công việc | Chỉ thư mục đó | Thư mục này chứa gì, quy trình riêng của phòng ban, cấu trúc thư mục con |

**Quy tắc khi hai cấp mâu thuẫn: cụ thể hơn thì thắng.** Nói kiểu đời thường: nội quy phòng ban đè nội quy công ty.

Ví dụ dễ hiểu: cấp cá nhân ghi "văn phong thân thiện". Thư mục hồ sơ pháp lý ghi "văn phong trang trọng". Khi làm việc trong thư mục pháp lý thì lấy trang trọng.

---

## Phần 2: Mẫu CLAUDE.md cấp cá nhân (profile)

Tạo file `C:\Users\<tên máy>\.claude\CLAUDE.md`, dán nội dung dưới, sửa phần trong ngoặc.

```markdown
# Hồ sơ cá nhân

## Tôi là ai
- Họ tên: [...]
- Chức danh: [...]
- Phòng ban: [Kinh doanh / Kế toán / Marketing / Nhân sự / Hành chính]
- Công ty, lĩnh vực: [...]

## Tôi làm việc với ai
- Cấp trên: [chức danh], xưng hô: [em / tôi], gọi: [anh / chị]
- Đồng nghiệp cùng phòng: [số người], xưng hô: [...]
- Khách hàng: [loại khách], xưng hô: [Anh/Chị + tên]

## Quy tắc chung, áp cho mọi việc
- Trả lời bằng tiếng Việt, ngắn gọn, đi thẳng vào việc.
- Văn bản gửi ra ngoài: văn phong công sở, KHÔNG dùng emoji.
- Không được tạo ra con số không có trong file nguồn. Thiếu thì ghi [đợi bổ sung].
- Trước khi sửa hoặc xóa file có sẵn, hỏi tôi.
- Đơn vị tiền mặc định: đồng Việt Nam. Định dạng ngày: ngày/tháng/năm.

## Việc tôi làm lặp lại nhiều nhất
1. [...]
2. [...]
3. [...]
```

Giữ dưới 40 dòng. Dài quá thì agent đọc lướt, hiệu quả giảm.

**Tuyệt đối không ghi vào đây:** mật khẩu, token, số tài khoản, thông tin cá nhân của khách hàng.

---

## Phần 3: Cấu trúc thư mục theo phòng ban

Mỗi phòng ban có cách sắp việc riêng. Dựng đúng cấu trúc thì agent tìm file nhanh và làm ít sai.

### Phòng Kinh doanh
```
kinh-doanh/
├── CLAUDE.md
├── 00-index.md
├── 01-khach-hang/       Hồ sơ, lịch sử trao đổi từng khách
├── 02-bao-gia/          Báo giá đã gửi
├── 03-hop-dong/         Hợp đồng đã ký
├── 04-so-lieu/          File doanh số, đơn hàng
└── 05-bao-cao/          Báo cáo tuần, tháng
```

### Phòng Kế toán
```
ke-toan/
├── CLAUDE.md
├── 00-index.md
├── 01-hoa-don/          Hóa đơn đầu vào, đầu ra
├── 02-cong-no/          Theo dõi phải thu, phải trả
├── 03-bao-cao-thue/     Tờ khai, báo cáo thuế
├── 04-luong/            Bảng lương (cân nhắc KHÔNG để trong thư mục agent đọc được)
└── 05-bao-cao/          Báo cáo tài chính
```

### Phòng Marketing
```
marketing/
├── CLAUDE.md
├── 00-index.md
├── 01-noi-dung/         Bài viết, caption, kịch bản
├── 02-chien-dich/       Kế hoạch từng chiến dịch
├── 03-hinh-anh/         Tư liệu hình
├── 04-so-lieu/          Số liệu quảng cáo, tương tác
└── 05-bao-cao/          Báo cáo hiệu quả
```

### Phòng Nhân sự
```
nhan-su/
├── CLAUDE.md
├── 00-index.md
├── 01-tuyen-dung/       Tin tuyển, CV, lịch phỏng vấn
├── 02-ho-so-nhan-vien/  Hồ sơ (cân nhắc quyền riêng tư)
├── 03-dao-tao/          Kế hoạch, tài liệu đào tạo
├── 04-cham-cong/        Bảng công, nghỉ phép
└── 05-bao-cao/          Báo cáo nhân sự
```

### Hành chính, trợ lý
```
hanh-chinh/
├── CLAUDE.md
├── 00-index.md
├── 01-van-ban-den/      Công văn, email nhận
├── 02-van-ban-di/       Văn bản gửi đi
├── 03-bien-ban-hop/     Biên bản các cuộc họp
├── 04-lich/             Lịch làm việc, lịch họp
└── 05-tai-san/          Theo dõi trang thiết bị
```

### Mẫu CLAUDE.md cấp phòng ban (đặt ở gốc thư mục trên)

```markdown
# CLAUDE.md: Thư mục [tên phòng ban]

## Thư mục này dùng để làm gì
[Một câu.]

## Cấu trúc thư mục
- `01-.../` : [chứa gì]
- `02-.../` : [chứa gì]
- `05-bao-cao/` : nơi lưu mọi kết quả agent tạo ra

## Quy trình riêng của phòng
- [Ví dụ Kinh doanh: mọi báo giá phải có hiệu lực 30 ngày và ghi rõ đã gồm thuế hay chưa.]
- [Ví dụ Kế toán: mọi con số phải trích được từ file gốc, ghi rõ lấy ở dòng nào.]

## Nơi lưu kết quả
Mọi file agent tạo ra thì lưu vào `05-bao-cao/`, đặt tên theo mẫu:
`[loai]-[thang]-[nam].md`, ví dụ `bao-cao-thang-03-2027.md`.

## Dữ liệu nhạy cảm
[Liệt kê thư mục KHÔNG được đụng tới, hoặc ghi rõ đã để ngoài thư mục này.]
```

---

## Phần 4: File index, giúp agent tìm nhanh

### Vì sao cần
Khi thư mục có vài chục file, agent phải mở lần lượt để biết file nào chứa gì. Vừa chậm vừa dễ bỏ sót. File index là một danh sách, mỗi file một dòng mô tả. Agent đọc index trước, biết ngay cần mở file nào.

Ví như mục lục cuốn sách: không có mục lục thì phải lật từng trang.

### Mẫu `00-index.md`

```markdown
# Index thư mục [tên phòng ban]

> Mỗi file một dòng. Cập nhật khi thêm hoặc bớt file.

## 01-khach-hang/
| File | Nội dung |
|---|---|
| `minh-long.md` | Hồ sơ Công ty Minh Long, đang tư vấn gói Cao cấp |
| `hai-nam.md` | Cửa hàng Hải Nam, khách cũ, từng hủy 1 đơn |

## 03-hop-dong/
| File | Nội dung |
|---|---|
| `hd-minh-long-2026.md` | Hợp đồng 120 triệu, 2 đợt, hết hạn 10/6/2027 |

## 04-so-lieu/
| File | Nội dung |
|---|---|
| `doanh-thu-quy.csv` | Doanh thu 3 tháng, 2 khu vực, 2 sản phẩm |
| `don-hang.csv` | 10 đơn hàng tháng 3, có trạng thái thanh toán |
```

### Cách nhờ agent tự dựng và tự cập nhật index

```
Đọc toàn bộ thư mục này và tạo file 00-index.md liệt kê mỗi file một dòng: tên file và một câu mô tả nội dung. Nhóm theo thư mục con, trình bày dạng bảng.
```

```
Tôi vừa thêm mấy file mới. Cập nhật lại 00-index.md giúp tôi, giữ nguyên các dòng cũ còn đúng.
```

### Nhắc trong CLAUDE.md để agent luôn dùng index
Thêm dòng này vào CLAUDE.md cấp phòng ban:
```
Trước khi tìm file, đọc 00-index.md để biết file nào chứa gì, đừng mở lần lượt từng file.
```

---

## Ghi chú giảng dạy
- Dạy theo thứ tự: profile cá nhân (rộng) tới phòng ban (hẹp) tới index (công cụ tra cứu).
- Nhấn quy tắc "cụ thể hơn thì thắng" khi hai cấp mâu thuẫn.
- Phần dữ liệu nhạy cảm phải nói rõ: cách chắc chắn duy nhất để agent không đọc file lương là **không để file đó trong thư mục agent làm việc**. Khoanh quyền công cụ không chặn được dữ liệu.
