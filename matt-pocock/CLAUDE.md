# Tra cứu bộ skill Matt Pocock

Thư mục `matt-pocock/` dùng để tra cứu và hỏi đáp về bộ skill [mattpocock/skills](https://github.com/mattpocock/skills). Không có code ứng dụng. Mọi đường dẫn dưới đây tính từ thư mục này. So sánh với BMAD Method: `../docs/so-sanh-voi-matt-pocock.md`.

## Nguồn sự thật

- **Mã nguồn skill:** `.agents/skills/<tên>/SKILL.md` và các file nó liên kết. Phiên bản và hash nằm trong `skills-lock.json`. Trước khi khẳng định một skill làm gì, đọc `SKILL.md` của nó; tài liệu trong `docs/` có thể chậm hơn mã nguồn.
- **Bản đồ flow** (skill nào cho tình huống nào): `.agents/skills/ask-matt/SKILL.md` và `PHASE-BOUNDARIES.md` cùng thư mục.
- Các skill ở đây chỉ để đọc. Không chạy chúng trong repo này, trừ khi người dùng yêu cầu.

## Tài liệu

- `docs/matt-pocock-skills.md`: tài liệu tham chiếu, gồm kiến trúc, từng skill và nhật ký cập nhật (mục 9).
- `docs/matt-pocock-skills-onboarding.md`: hướng dẫn nhập môn cho dev, gồm các case study.
- `docs/matt-pocock-autonomous-loops.md`: chạy vòng lặp tự động bằng `/implement-spec`.
- `case-studies/NN-*.md`: mỗi file một tình huống (chuỗi skill, prompt mẫu, ví dụ), cuối file là mục "Thực tế đã gặp". Danh sách trong `case-studies/README.md`.

## Cách trả lời

- Trả lời bằng tiếng Việt. Giữ nguyên thuật ngữ gốc tiếng Anh (frontier, seam, tracer bullet…).
- Khi người dùng kể một tình huống thực tế, tìm file case study khớp nhất và trả lời dựa trên nó cùng `SKILL.md` liên quan. Không có file khớp thì ghép skill theo flow trong `ask-matt`, và nói rõ khi không có skill nào phủ tình huống đó.
- Sau khi trả lời, đề nghị ghi kết quả vào mục "Thực tế đã gặp" của file khớp, hoặc tạo file tình huống mới, theo hướng dẫn trong `case-studies/README.md`.
- Không ghi tên khách hàng, tên công ty, mã nguồn nội bộ hay thông tin bí mật vào repo. Viết case study ở dạng tổng quát.
