# Workbook Buổi 01: Agent là gì và làm quen Claude Code

> Sổ tay thực hành của bạn. Làm theo từng bước, copy prompt mẫu để dùng, ghi chú vào ô trống.
> Cuối buổi bạn sẽ có: 1 thư mục dự án riêng, 1 file CLAUDE.md, và đã cho agent đọc, tạo, sửa file thật.

## 1. Buổi này bạn học được gì

- Hiểu **agent** là gì và khác chat AI thường ra sao.
- Mở được **Claude Code** trên Claude Desktop và chọn đúng thư mục để nó làm việc.
- Tạo file **CLAUDE.md** làm bộ nhớ cho agent (agent tự đọc mỗi lần mở, khỏi dặn lại).
- Ra lệnh cho agent **đọc** cả thư mục, **tạo** file mới, **sửa** file có sẵn.

**Nói ngắn gọn:** chat thường chỉ trả lời bằng chữ. Agent thì tự làm nhiều bước, đụng được file thật trong máy bạn, và nhớ bạn là ai.

## 2. Chuẩn bị trước khi bắt đầu

- [ ] Máy đã cài **Claude Desktop** và đăng nhập tài khoản CES cấp cho lớp.
- [ ] Đã tải bộ file demo của khóa về máy (thư mục `tai-lieu-phat/demo/buoi-01/du-an-mau/`).
- [ ] Có sẵn 1 thư mục trống trên máy để làm thư mục dự án của riêng bạn.
- [ ] (Nếu có) Vài file công việc thật: 1 tài liệu, 1 file dữ liệu, vài ghi chú.

## 3. Các thao tác từng bước

> Làm lần lượt. Mỗi bước có prompt mẫu, bạn copy nguyên văn gõ vào Claude Code (sửa phần trong [ngoặc] cho hợp với mình).

### Bước 1: Mở Claude Code và chọn thư mục dự án

1. Mở **Claude Desktop**, vào **Claude Code**.
2. Chọn thư mục làm việc: trỏ vào thư mục demo `tai-lieu-phat/demo/buoi-01/du-an-mau/`.
3. Kiểm tra agent đã thấy đúng file chưa bằng prompt:

```
Thư mục này đang có những file gì? Liệt kê tên file và cho tôi biết mỗi file nói về cái gì.
```

**Kết quả đúng:** agent liệt kê 2 file: `ghi-chu-cong-viec.md` và `danh-sach-khach-hang.md`.

Ghi chú của bạn (agent thấy đúng file chưa?):
```
...................................................................
...................................................................
```

### Bước 2: Cho agent đọc thư mục và tóm tắt "tôi đang có gì"

```
Đọc tất cả file trong thư mục này và tóm tắt cho tôi: tôi đang có bao nhiêu việc cần làm, bao nhiêu khách hàng, và việc nào gấp nhất.
```

**Kết quả đúng:** 5 việc cần làm, 5 khách hàng; việc gấp nhất là báo cáo doanh thu (hạn thứ Sáu) và họp thứ Tư có sếp dự.

Ghi chú (agent tóm tắt ra mấy việc, mấy khách?):
```
Số việc: ........   Số khách: ........   Việc gấp nhất: ...................
```

### Bước 3: Cho agent tạo file mới (todo.md)

```
Từ file ghi-chu-cong-viec.md, tạo cho tôi một file mới tên todo.md gồm danh sách các việc cần làm dạng checkbox, việc nào có hạn thì ghi rõ hạn.
```

**Kết quả đúng:** có file `todo.md` mới trong thư mục, gồm 5 dòng checkbox. Mở thư mục trong máy để thấy file thật.

Ghi chú (file todo.md đã xuất hiện chưa?):
```
...................................................................
```

### Bước 4: Cho agent sửa file có sẵn (thêm 1 khách hàng)

```
Thêm một khách hàng mới vào file danh-sach-khach-hang.md: tên "Công ty Sao Mai", ngành "Logistics", trạng thái "Tiềm năng", ghi chú "Gặp tại hội chợ".
```

**Lưu ý quan trọng:** agent sẽ **cho bạn xem trước** dòng nó định thêm và **hỏi xác nhận**. Đây là cơ chế an toàn.
- Đồng ý: gõ `được` hoặc `đồng ý`.
- Không muốn: gõ `không`, agent sẽ dừng, không sửa gì.

**Kết quả đúng:** danh sách khách hàng có thêm dòng "Công ty Sao Mai", tổng thành 6 khách.

Ghi chú (bạn đã bấm xác nhận chưa, danh sách còn mấy khách?):
```
...................................................................
```

### Bước 5: Tạo CLAUDE.md làm bộ nhớ cho agent

CLAUDE.md là file agent tự đọc mỗi lần mở thư mục, để biết bạn là ai và muốn làm việc kiểu gì. Tạo bằng prompt:

```
Tạo cho tôi một file CLAUDE.md ở thư mục này. Tôi tên [Họ tên của bạn], làm [công việc của bạn]. Thư mục này để [mục đích, ví dụ: quản lý việc cần làm và khách hàng]. Quy tắc: trả lời tiếng Việt ngắn gọn, trước khi sửa hay xóa file phải hỏi tôi, không bịa số liệu, văn bản gửi đi không dùng emoji.
```

**Kết quả đúng:** có file `CLAUDE.md` ở gốc thư mục, ghi đúng tên và công việc của bạn.

## 4. Mẫu CLAUDE.md để copy

> Nếu muốn tự dán và sửa tay thay vì nhờ agent tạo, copy khối dưới, lưu thành file tên `CLAUDE.md` ở gốc thư mục dự án, rồi sửa phần trong [ngoặc].

```markdown
# CLAUDE.md

## Tôi là ai
- Tên: [Họ tên]
- Vai trò: [chức danh, ví dụ: nhân viên kinh doanh]
- Công ty/lĩnh vực: [...]

## Thư mục này để làm gì
[Ví dụ: nơi tôi để tài liệu, dữ liệu bán hàng, và nhờ agent xử lý báo cáo hằng tuần.]

## Quy tắc khi làm việc với tôi
- Trả lời bằng tiếng Việt, ngắn gọn, dễ hiểu.
- Trước khi sửa hay xóa file, hỏi tôi xác nhận.
- Không bịa số liệu. Thiếu thông tin thì hỏi tôi.
- Văn bản gửi đi (email, báo cáo): văn phong công sở, không dùng emoji.

## Định dạng đầu ra tôi hay cần
[Ví dụ: báo cáo tuần, email khách hàng, bảng tổng hợp số liệu.]

## Cấu trúc thư mục
- `tai-lieu/` : tài liệu cần đọc
- `du-lieu/`  : file Excel/CSV
- `ket-qua/`  : nơi agent lưu output
```

## 5. Bài tập

### Tại lớp (làm với dữ liệu công việc thật của bạn)

1. Tạo 1 thư mục dự án riêng, bỏ vào vài file công việc thật (hoặc tạm dùng lại thư mục demo).
2. Trỏ Claude Code vào thư mục đó, cho agent đọc và tóm tắt: bạn đang có gì, việc nào ưu tiên.
3. Tạo file CLAUDE.md cho riêng bạn (điền đúng tên và công việc).
4. Nhờ agent tạo hoặc sửa 1 file theo nhu cầu thật, ví dụ:

```
Từ ghi chú của tôi, tạo file ke-hoach-tuan.md gồm các việc cần làm theo thứ tự ưu tiên.
```

### Về nhà

- Hoàn thiện CLAUDE.md cho đầy đủ hơn.
- Cho agent xử lý ít nhất 1 việc thật ở nhà (đọc 1 tài liệu và tóm tắt, hoặc dọn lại 1 danh sách việc).
- Chụp màn hình kết quả gửi vào Zalo lớp.
- Nghĩ trước 1 việc bạn lặp đi lặp lại hằng tuần, buổi sau ta biến nó thành skill.

## 6. Checklist tự đánh giá

- [ ] Tôi mở được Claude Code và trỏ đúng vào thư mục dự án.
- [ ] Tôi cho agent đọc cả thư mục và nhận được tóm tắt đúng (5 việc, 5 khách với file demo).
- [ ] Tôi tạo được file `todo.md` mới từ ghi chú công việc.
- [ ] Tôi thêm được 1 khách hàng vào danh sách (qua bước agent xin xác nhận).
- [ ] Tôi có file `CLAUDE.md` ở thư mục dự án, ghi đúng thông tin của mình.
- [ ] Tôi nói lại được 3 điểm agent khác chat thường: tự làm nhiều bước, đụng file thật, nhớ bối cảnh.
