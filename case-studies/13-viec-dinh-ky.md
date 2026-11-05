# 13. Thiết kế quy trình cho việc định kỳ của chính bạn

**Khi nào:** có việc lặp đi lặp lại muốn giao bớt cho agent hoặc script: báo cáo tuần, tổng hợp MR đã merge, phân loại mail, ghi chú standup, theo dõi tin tức công nghệ.

**Chuỗi skill:** `/loop-me` → (khi cần build) `/to-spec` → `/to-tickets` → `/implement`

## Các bước

### 1. Thiết kế quy trình

Chạy trong một thư mục riêng cho các quy trình cá nhân:

```text
/loop-me Báo cáo tuần: mỗi thứ Sáu tôi tổng hợp các MR đã merge, ticket đã xong,
việc còn vướng, rồi gửi cho quản lý.
```

Hoặc chạy `/loop-me` không kèm gì: agent phỏng vấn về công việc của bạn để tìm những vòng lặp đáng giao.

Agent grill theo bốn khái niệm:

| Khái niệm | Câu hỏi | Ví dụ |
|---|---|---|
| **Trigger** | Cái gì kích hoạt mỗi lần chạy? Sự kiện hay lịch? | 16h thứ Sáu |
| **Checkpoint** | Chỗ nào bạn phải xem và quyết? | Duyệt bản nháp báo cáo trước khi gửi |
| **Push right** | Đẩy checkpoint về sau tới mức nào? | Agent gom dữ liệu và viết nháp xong mới hỏi bạn |
| **Brief** | Ở checkpoint bạn đọc gì? | Một tóm tắt ngắn kèm link tới bản nháp, không phải dữ liệu thô |

Kết quả là `workflows/bao-cao-tuan.md`, cộng `NOTES.md` ghi công cụ và thuật ngữ bạn dùng.

### 2. Build (nếu cần)

Spec quy trình xong khi một agent khác đọc là build được mà không cần hỏi thêm. Từ spec đó, đi main flow: `/to-spec` → `/to-tickets` → `/implement`. Kết quả là một script, một lịch chạy, hoặc một skill riêng.

## Lưu ý

- `/loop-me` **không tự chạy vòng lặp**; nó chỉ tạo đặc tả. Vòng lặp code tự động là chuyện khác, xem `docs/matt-pocock-autonomous-loops.md`.
- Quy trình không bắt buộc phải có AI, checkpoint hay lịch. Có khi kết luận là một checklist cho người làm là đủ.

## Thực tế đã gặp

_Chưa có._
