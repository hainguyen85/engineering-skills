# 12. Agent lặp đi lặp lại cùng một lỗi

**Khi nào:** agent cứ mắc cùng một kiểu sai qua nhiều phiên: dùng sai API, đặt file sai chỗ, quên quy ước của nhóm, mất nhiều thời gian mới tìm ra file cần sửa, hoặc người review phải nhắc cùng một điều nhiều lần.

**Chuỗi skill:** `/retro`

## Các bước

```text
/retro Phiên này agent hai lần dùng LocalDateTime.now() thay vì Clock của hệ thống,
và mất khá lâu mới tìm ra chỗ cấu hình phân quyền.
```

Agent đọc lại phiên (mặc định là phiên hiện tại) và đề xuất cải tiến **môi trường** theo các nhóm, xếp theo mức nghiêm trọng:

| Nhóm | Câu hỏi | Kết quả thường thấy |
|---|---|---|
| **Navigation** | Agent có tìm đúng file nhanh không? | Một dòng pointer trong `CLAUDE.md`/`AGENTS.md` |
| **Check tự động** | Lỗi này máy có bắt được không? Repo có pre-commit hay CI không? | Rule linter, pre-commit hook, CI job |
| **Chuẩn code** | Người review có cần thêm quy tắc không? | Một mục trong `CODING_STANDARDS.md` |
| **AGENTS.md quá dài** | Có chỉ dẫn nào nên chuyển sang chuẩn code hay check? | Rút gọn `CLAUDE.md` |
| **Tool economy** | Có lệnh nào tốn token vô ích? | Lệnh hoặc công cụ gọn hơn |
| **No-op** | Có chỉ dẫn nào không làm thay đổi hành vi agent? | Xoá |
| **Tiếp cận thông tin** | Agent có thiếu log, thiếu quyền đọc không? | Ghi log ra file, cấp quyền chỉ đọc |

## Quy tắc phân loại

- **Lỗi máy móc** (API bị cấm, dạng import, vị trí file): **làm check tự động**, không ghi thành chữ. Ví dụ: rule ArchUnit hoặc Checkstyle cấm `LocalDateTime.now()` ngoài package `time`.
- **Việc cần phán đoán** (nhất quán giữa các file, theo đúng style xung quanh): ghi vào `CODING_STANDARDS.md`. File này được đọc lúc review, không phải lúc code.
- **`CLAUDE.md`/`AGENTS.md`** luôn được nạp vào mọi phiên, nên chỉ ghi pointer, ví dụ *"Phân quyền: cấu hình ở `config/security/`, đọc `docs/adr/0003-...` trước khi sửa."*

## Lưu ý

- `/retro` chỉ **đề xuất**; bạn chọn cái nào làm.
- Chạy `/retro` ngay sau khi sửa xong một bug khó (xem [04](04-bug-chap-chon.md)), hoặc sau mỗi đợt ticket.

## Thực tế đã gặp

_Chưa có._
