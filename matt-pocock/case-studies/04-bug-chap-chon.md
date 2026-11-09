# 04. Bug chập chờn, chậm, hoặc không thấy nguyên nhân

**Khi nào:** bug không tái hiện được ngay, lúc có lúc không, hồi quy giữa hai phiên bản, hoặc hệ thống chậm dần.

**Chuỗi skill:** `/diagnosing-bugs` → (nếu không có seam để test) [05. Refactor module cũ](05-refactor-module-cu.md) → `/retro`

## Các bước

```text
/diagnosing-bugs Báo cáo tuần thỉnh thoảng thiếu dữ liệu của ngày cuối tuần.
Khoảng 1/5 lần chạy. Log ở logs/report-*.log. Lỗi bắt đầu sau bản phát hành ngày 2026-10-20.
```

Skill đi qua 6 pha và **không cho đoán nguyên nhân trước khi có pha 1**:

| Pha | Agent làm gì | Xong khi |
|---|---|---|
| 1. Feedback loop | Dựng **một lệnh** đỏ đúng trên bug này: test, script curl, replay dữ liệu thật, `git bisect run`… | Lệnh đã chạy, nhanh, ổn định, bắt đúng triệu chứng |
| 2. Tái hiện + thu nhỏ | Cắt dần input và bước cho tới kịch bản nhỏ nhất vẫn đỏ | Bỏ thêm bất kỳ phần nào thì xanh |
| 3. Giả thuyết | Đưa 3–5 giả thuyết, xếp hạng, mỗi cái kèm dự đoán kiểm chứng được | Có danh sách |
| 4. Đo đạc | Thêm log hoặc đo có mục tiêu để loại dần giả thuyết | Tìm ra nguyên nhân |
| 5. Sửa + regression test | Sửa, kịch bản ở pha 2 thành regression test | Test đỏ trước khi sửa, xanh sau khi sửa |
| 6. Dọn dẹp | Gỡ log tạm, tổng kết | |

## Bạn làm gì

- **Cung cấp thứ agent không tự lấy được:** log thật, dữ liệu mẫu, quyền vào môi trường tái hiện được. Che secret trước khi đưa.
- **Bug cần người bấm** (UI, thiết bị): agent tạo script `hitl-loop` để dẫn bạn làm từng bước và ghi lại kết quả.
- **Agent nói không dựng được feedback loop:** đó là kết luận hợp lệ. Agent sẽ liệt kê đã thử gì và cần gì thêm, không đoán mò.

## Ví dụ

- **Bug chập chờn:** agent chạy job báo cáo 100 lần với ngày cố định là thứ Hai, bug xuất hiện khoảng 20%.
- **Thu nhỏ:** chỉ còn hai bản ghi, đều có giờ là 23:30 Chủ nhật.
- **Giả thuyết số 1** (múi giờ): *"Nếu do chuyển UTC, đặt TZ=UTC thì bug biến mất."*
- **Kiểm chứng và sửa:** đặt TZ=UTC thì bug biến mất. Sửa chỗ quy đổi múi giờ, regression test giữ đúng hai bản ghi đó.

## Lưu ý

- Dự án chỉ có unit test vẫn dùng được: feedback loop có thể là một unit test, một script, hay một lần replay dữ liệu.
- Sửa xong, chạy `/retro` ngay trong phiên đó: điều gì lẽ ra đã ngăn được bug này?

## Thực tế đã gặp

_Chưa có._
