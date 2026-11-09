# Tra cứu các bộ engineering skills

Repo này dùng để tra cứu, hỏi đáp và so sánh các bộ skill cho AI coding agent. Không có code ứng dụng. Mỗi bộ có thư mục riêng, kèm `CLAUDE.md` chỉ đường cho bộ đó.

## Chỉ đường

| Hỏi về | Đọc trước | Mã nguồn |
|---|---|---|
| Bộ Matt Pocock | `matt-pocock/CLAUDE.md` | `matt-pocock/.agents/skills/<tên>/SKILL.md`; bản đồ flow ở `matt-pocock/.agents/skills/ask-matt/SKILL.md` |
| BMAD Method | `bmad-method/CLAUDE.md` | `bmad-method/.agents/skills/bmad-<tên>/SKILL.md`; bản đồ flow ở `bmad-method/_bmad/_config/bmad-help.csv` |
| Chọn giữa các bộ, hoặc một tình huống có thể dùng nhiều bộ | `docs/so-sanh-voi-matt-pocock.md`, `docs/case-study-matt-pocock-voi-bmad.md` | Cả hai thư mục trên |

Trước khi khẳng định một skill làm gì, đọc `SKILL.md` của nó; tài liệu trong `docs/` có thể chậm hơn mã nguồn. Các skill trong repo chỉ để đọc, không chạy, trừ khi người dùng yêu cầu.

## Cách trả lời

- Trả lời bằng tiếng Việt. Giữ nguyên thuật ngữ gốc tiếng Anh (frontier, seam, party mode, memlog…).
- Khi người dùng kể một tình huống, tìm case study khớp nhất trong `<bộ>/case-studies/` và trong `docs/case-study-matt-pocock-voi-bmad.md`. Nếu bộ khác hợp hơn bộ người dùng đang hỏi, nói thẳng.
- Sau khi trả lời, đề nghị ghi kết quả vào mục "Thực tế đã gặp" của case study khớp, hoặc tạo case study mới, theo `case-studies/README.md` của bộ tương ứng.
- Không ghi tên khách hàng, tên công ty, mã nguồn nội bộ hay thông tin bí mật vào repo. Viết case study ở dạng tổng quát.
