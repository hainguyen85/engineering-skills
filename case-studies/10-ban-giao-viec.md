# 10. Bàn giao việc

**Khi nào:** việc đang dở phải chuyển đi: sang phiên chat mới (context đầy), sang công cụ khác (Claude Code → Antigravity, Copilot), sang đồng nghiệp, hoặc trước khi nghỉ phép.

**Chuỗi skill:** `/handoff` (hoặc `/claude-handoff` để giao cho agent nền làm ngay)

## Các bước

### 1. Tạo file bàn giao

```text
/handoff Phiên sau sẽ làm ticket 03 và 04, ticket 02 đã xong nhưng còn một comment review chưa sửa.
```

- **Nội dung:** agent tóm tắt phiên thành một file, có mục **gợi ý skill** cho phiên sau.
- **Không chép lại nội dung đã có** trong spec, ticket, ADR, commit; chỉ ghi đường dẫn tới chúng.
- **Che** API key, mật khẩu, thông tin cá nhân.
- **Vị trí file:** thư mục temp của hệ điều hành (`%TEMP%` trên Windows), không nằm trong repo.

### 2. Chuyển file đi

| Người hoặc công cụ nhận | Cách chuyển |
|---|---|
| Phiên mới, cùng máy | Dùng thẳng đường dẫn trong `%TEMP%` |
| Công cụ khác, cùng repo | Chép file vào `.scratch/<feature>/handoff.md` |
| Đồng nghiệp | Chép vào repo rồi đưa qua git, hoặc gửi file qua kênh được phép dùng |

### 3. Bên nhận

```text
Đọc .scratch/duyet-theo-nhom/handoff.md và làm tiếp. Dùng các skill được gợi ý trong file.
```

## `/claude-handoff` khác gì?

`/claude-handoff` (chỉ có trên Claude Code) chuyển phiên hiện tại cho **một agent nền mới** và agent đó bắt đầu làm ngay. Dùng khi muốn tách một việc phụ ra chạy song song trong lúc bạn tiếp tục phiên chính.

## Lưu ý

- Bàn giao giữa grill và prototype đi **hai chiều**: phiên grill → `/handoff` → phiên prototype; prototype xong → `/handoff` → quay về phiên grill.
- Không `/clear` phiên gốc trước khi bên nhận đọc xong file, phòng khi cần hỏi lại.

## Thực tế đã gặp

_Chưa có._
