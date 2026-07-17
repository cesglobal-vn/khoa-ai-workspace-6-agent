# Mẫu: Tạo repo GitHub, lấy token, cắm GitHub MCP để quản lý skill

> GitHub là nơi lưu và quản lý file trên mạng (có lịch sử thay đổi, chia sẻ được). Ta dùng nó để cất
> các skill của mình cho an toàn và dùng lại. Agent sẽ thao tác GitHub thay bạn qua một MCP tên GitHub.

## Vì sao đưa skill lên GitHub
- Skill là các file trong thư mục `.claude/skills/`. Để trên máy thì dễ mất, khó chia sẻ.
- Đưa lên một repo GitHub: có bản lưu trên mạng, xem được lịch sử sửa, chia cho đồng nghiệp, đồng bộ nhiều máy.
- Sau khi cắm GitHub MCP, bạn chỉ cần ra lệnh tiếng Việt, agent tự tạo repo và đẩy skill lên.

## Bước 1: Tạo tài khoản và repo GitHub
1. Tạo tài khoản tại github.com (nếu chưa có).
2. Tạo một repo mới, ví dụ tên `bo-skill-cua-toi`, để chế độ Private (riêng tư).
3. Ghi nhớ tên đăng nhập GitHub và tên repo.

> Có thể để agent tạo repo giúp sau khi đã cắm GitHub MCP (Bước 3). Ở lớp, GV cho tạo tay 1 lần cho quen.

## Bước 2: Lấy Personal Access Token (chìa khóa cho agent dùng GitHub)
Token là một chuỗi ký tự thay cho mật khẩu, cấp cho agent quyền thao tác GitHub trong giới hạn bạn chọn.

1. Vào github.com, mở: Settings > Developer settings > Personal access tokens.
2. Chọn tạo token (khuyên dùng loại Fine-grained cho an toàn).
3. Đặt tên token, chọn thời hạn, chọn repo được phép truy cập (chỉ repo skill của bạn).
4. Cấp quyền tối thiểu: đọc và ghi nội dung repo (Contents: Read and write).
5. Bấm tạo, COPY token ngay (token chỉ hiện một lần).

### Lưu ý an toàn (rất quan trọng, dạy kỹ)
- Token giống mật khẩu. KHÔNG gửi token cho ai, KHÔNG dán vào khung chat, KHÔNG chụp màn hình gửi nhóm.
- Chỉ dán token vào phần cài đặt MCP của Claude Desktop (Bước 3).
- Cấp quyền tối thiểu và đặt thời hạn ngắn. Khi nghi lộ, vào GitHub thu hồi (revoke) token ngay.

## Bước 3: Cắm GitHub MCP vào Claude Desktop
1. Mở Claude Desktop, vào phần cài đặt kết nối (Connectors / MCP).
2. Thêm server GitHub.
3. Khi được hỏi, dán Personal Access Token ở Bước 2 vào đúng ô token của server GitHub.
4. Lưu lại. Kiểm tra kết nối báo thành công.

> Thao tác giao diện cụ thể chốt theo phiên bản Claude Desktop lớp đang dùng. Bản chất: khai báo server
> GitHub và cung cấp token để agent thay bạn thao tác repo.

## Bước 4: Dùng agent quản lý skill qua GitHub
Sau khi cắm xong, ra lệnh tiếng Việt, ví dụ:

```
Tạo giúp tôi một repo riêng tư tên bo-skill-cua-toi trên GitHub,
rồi đẩy toàn bộ thư mục .claude/skills/ hiện tại lên repo đó.
```

```
Tôi vừa sửa skill tom-tat-tai-lieu. Cập nhật (commit và push) thay đổi
này lên repo bo-skill-cua-toi giúp tôi, kèm mô tả ngắn nội dung sửa.
```

Kết quả: skill của bạn được lưu trên GitHub, có lịch sử thay đổi, chia sẻ và đồng bộ được.

---

## Ghi chú giảng dạy
- Nhấn chuỗi giá trị: skill (đóng gói việc) tới GitHub (cất giữ, chia sẻ) tới MCP (agent tự thao tác GitHub).
- Phần token là chỗ dễ sai và dễ mất an toàn nhất: dành thời gian nhắc kỹ quy tắc bảo mật token.
- Nếu học viên chưa quen GitHub, GV demo trước, học viên làm theo, phần chưa xong để làm nốt ở nhà.
