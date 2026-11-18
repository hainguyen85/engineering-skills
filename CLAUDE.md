# Tra cứu các bộ engineering skills

Repo này dùng để tra cứu, hỏi đáp và so sánh các bộ skill cho AI coding agent. Không có code ứng dụng. Mã nguồn các bộ skill nằm chung ở gốc repo: `.agents/skills/` (skill của mọi bộ), `_bmad/` (cấu hình và script của BMAD) và `skills-lock.json` (nguồn và hash của bộ Matt Pocock). Mỗi bộ có thư mục riêng (`matt-pocock/`, `bmad-method/`) chỉ chứa tài liệu tìm hiểu và case study về bộ đó, kèm `CLAUDE.md` chỉ đường.

## Chỉ đường

| Hỏi về | Đọc trước | Mã nguồn |
|---|---|---|
| Bộ Matt Pocock | `matt-pocock/CLAUDE.md` | `.agents/skills/<tên>/SKILL.md`; bản đồ flow ở `.agents/skills/ask-matt/SKILL.md` |
| BMAD Method | `bmad-method/CLAUDE.md` | `.agents/skills/bmad-<tên>/SKILL.md`; bản đồ flow ở `_bmad/_config/bmad-help.csv` |
| Chọn giữa các bộ, hoặc một tình huống có thể dùng nhiều bộ | `docs/so-sanh-voi-matt-pocock.md`, `docs/case-study-matt-pocock-voi-bmad.md` | Cả hai bộ ở trên |

Skill của BMAD đều có tiền tố `bmad-`; skill của Matt Pocock không có.

Trước khi khẳng định một skill làm gì, đọc `SKILL.md` của nó; tài liệu trong `docs/` có thể chậm hơn mã nguồn. Các skill trong repo chỉ để đọc, không chạy, trừ khi người dùng yêu cầu.

## Cách trả lời

- Trả lời bằng tiếng Việt. Giữ nguyên thuật ngữ gốc tiếng Anh (frontier, seam, party mode, memlog…).
- Khi người dùng kể một tình huống, tìm case study khớp nhất trong `<bộ>/case-studies/` và trong `docs/case-study-matt-pocock-voi-bmad.md`. Nếu bộ khác hợp hơn bộ người dùng đang hỏi, nói thẳng.
- Sau khi trả lời, đề nghị ghi kết quả vào mục "Thực tế đã gặp" của case study khớp, hoặc tạo case study mới, theo `case-studies/README.md` của bộ tương ứng.
- Không ghi tên khách hàng, tên công ty, mã nguồn nội bộ hay thông tin bí mật vào repo. Viết case study ở dạng tổng quát.
