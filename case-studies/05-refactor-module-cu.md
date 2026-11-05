# 05. Refactor module cũ

**Khi nào:** một module khó sửa: logic lặp ở nhiều chỗ, phải nhảy qua nhiều file mới hiểu một khái niệm, không có test, sửa chỗ này hỏng chỗ khác.

**Chuỗi skill:** `/improve-codebase-architecture` → `/codebase-design` (thiết kế interface hai lần) → `/grill-with-docs` → `/to-spec` → `/to-tickets` → `/implement`

## Các bước

### 1. Tìm cơ hội

```text
/improve-codebase-architecture Tập trung vào module duyệt đơn (src/.../approval).
```

Agent đọc `GLOSSARY.md` và ADR, khảo sát code, rồi đưa danh sách **deepening opportunity**: chỗ có thể gom nhiều hành vi vào sau một interface nhỏ. Bạn chọn một.

### 2. Thiết kế interface

```text
/codebase-design Thiết kế interface hai lần cho cơ hội số 2: gom logic phạm vi dữ liệu theo người dùng.
```

Agent mô tả bài toán và ràng buộc, rồi cho **3 subagent trở lên** thiết kế song song theo các hướng khác nhau:

- interface tối thiểu (1–3 điểm vào);
- linh hoạt tối đa;
- tối ưu cho trường hợp gọi phổ biến nhất;
- ports & adapters, nếu có phụ thuộc bên ngoài.

Sau đó agent so sánh các thiết kế. Bạn chọn một hoặc ghép lại.

### 3. Main flow

- `/grill-with-docs` chốt phạm vi: giữ nguyên hành vi hay sửa luôn bug cũ, có đổi tên thuật ngữ không.
- `/to-spec` chốt **seam**, thường là chính interface mới.
- `/to-tickets` chia ticket. **Ticket đầu tiên** viết test bắt hành vi hiện tại tại seam mới, để các ticket sau refactor có lưới an toàn.
- `/implement` từng ticket.

## Ví dụ

- **Hiện trạng:** hai controller cùng lọc dữ liệu theo phạm vi người dùng (quản lý thấy cả phòng, nhân viên chỉ thấy của mình), mỗi chỗ một bản code hơi khác nhau.
- **Cơ hội:** một module `ApprovalScope` với một hàm `visibleRequests(user, filter)`.
- **Ticket 1:** test cho 4 vai trò × 3 bộ lọc, chạy trên code cũ qua interface mới.
- **Ticket 2–3:** chuyển từng controller sang dùng module mới, xoá code lặp.

## Lưu ý

- **Phép thử xoá:** tưởng tượng xoá module đi. Độ phức tạp biến mất theo nghĩa là module chỉ chuyển tiếp lời gọi, vô dụng. Độ phức tạp lan ra N chỗ gọi nghĩa là module đáng giữ.
- **Một adapter là seam giả định, hai adapter mới là seam thật.** Đừng tạo interface khi không có gì thay đổi qua nó.
- Phát hiện lỗ hổng bảo mật trong lúc khảo sát thì tách thành việc riêng, báo người phụ trách, không gộp vào refactor.

## Thực tế đã gặp

_Chưa có._
