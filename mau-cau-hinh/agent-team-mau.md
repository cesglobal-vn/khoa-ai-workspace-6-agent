# Mẫu lập Agent Team (điều khiển đội agent)

> Agent Team là nhiều agent cùng làm một công việc lớn: một lead (chính là bạn qua Claude Code) chia
> việc thành các phần độc lập, giao mỗi phần cho một agent, các agent chạy SONG SONG, rồi lead ghép lại.

## Nguyên tắc cốt lõi (dạy kỹ)
1. **Chia việc độc lập:** mỗi agent làm một phần không đụng vào phần của agent khác.
2. **Phân vùng file (file ownership):** mỗi agent chỉ sửa file của mình, tránh giẫm chân nhau.
3. **Chạy song song:** giao tất cả cùng lúc để rút ngắn thời gian.
4. **Lead tổng hợp:** khi các agent xong, lead gom kết quả, kiểm mâu thuẫn, xuất bản cuối.

## Hai mức làm agent team

### Mức 1: giao nhiều việc song song trong một phiên (đơn giản, dùng cho lớp)
Bạn mô tả cho Claude Code một việc lớn và yêu cầu chia cho nhiều agent chạy song song. Ví dụ prompt:

```
Tôi có một dự án ra mắt sản phẩm. Hãy chia thành các phần độc lập và giao cho nhiều agent chạy SONG SONG:
- Agent 1: đọc thư mục "thi-truong/" và tóm tắt bối cảnh thị trường.
- Agent 2: đọc "doi-thu/" và lập bảng so sánh đối thủ.
- Agent 3: đọc "so-lieu/" và phân tích số liệu bán hàng.
Mỗi agent chỉ đọc thư mục của mình. Sau khi cả ba xong, tổng hợp thành một bản tóm tắt chung cho tôi.
```

### Mức 2: agent team nhiều phiên (nâng cao)
Với việc lớn cần cộng tác lâu, Claude Code có thể lập một team gồm lead + nhiều teammate ở các phiên
riêng, giao tiếp qua tin nhắn và cùng theo dõi danh sách task. Ở lớp chỉ giới thiệu; ai cần đi sâu thì
GV hướng dẫn thêm sau khóa.

## Sơ đồ
```
                 BẠN (lead qua Claude Code)
                 │  chia việc + phân vùng file
     ┌───────────┼───────────┐
     ▼           ▼           ▼
  Agent 1     Agent 2     Agent 3      (chạy song song, mỗi agent 1 thư mục)
     └───────────┼───────────┘
                 ▼
        Lead tổng hợp + kiểm mâu thuẫn + xuất bản cuối
```

## Lưu ý (dạy học viên)
- Việc nào các phần phụ thuộc nhau (phải làm tuần tự) thì KHÔNG chia song song; làm lần lượt.
- Luôn dặn "mỗi agent chỉ sửa file của mình" để tránh xung đột.
- Lead phải kiểm số liệu giữa các phần có khớp nhau không trước khi chốt.

---

## Ghi chú giảng dạy
- Liên hệ đời thực: giống trưởng nhóm giao việc cho 3 nhân viên làm cùng lúc rồi ghép báo cáo.
- Đây là bậc cao nhất trước capstone: buổi 6 mỗi agent trong team sẽ dùng thêm skill + MCP.
