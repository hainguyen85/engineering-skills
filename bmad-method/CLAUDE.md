# Tra cứu BMAD Method

Thư mục `bmad-method/` dùng để tra cứu và hỏi đáp về [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD), bản 6.12.4. Không có code ứng dụng. Người đọc chính là PM (Product Manager) và Techlead. Mọi đường dẫn dưới đây tính từ thư mục này.

## Nguồn sự thật

- **Mã nguồn skill:** `.agents/skills/bmad-<tên>/SKILL.md`, `customize.toml` và các file nó liên kết (`references/`, `steps/`, `assets/`). Trước khi khẳng định một skill làm gì, đọc `SKILL.md` của nó; tài liệu trong `docs/` có thể chậm hơn mã nguồn.
- **Bản đồ flow** (phase, thứ tự, bước bắt buộc, đầu ra): `_bmad/_config/bmad-help.csv`. Persona và tên agent: `_bmad/config.toml`.
- **Phiên bản:** `_bmad/_config/manifest.yaml`; hash từng file trong `_bmad/_config/files-manifest.csv`.
- Các skill ở đây chỉ để đọc. Không chạy chúng trong repo này, trừ khi người dùng yêu cầu.

## Tài liệu

- `docs/bmad-method.md`: tài liệu tham chiếu, gồm kiến trúc, từng skill và nhật ký cập nhật (mục 8).
- `docs/bmad-method-onboarding.md`: hướng dẫn nhập môn cho PM và Techlead.
- `../docs/so-sanh-voi-matt-pocock.md`: chọn giữa BMAD và bộ Matt Pocock. Mã nguồn và tài liệu bộ Matt Pocock nằm ở `../matt-pocock/`.
- `../docs/case-study-matt-pocock-voi-bmad.md`: 14 case study của bộ Matt Pocock, mỗi cái làm bằng BMAD thế nào và chỗ nào vẫn giữ skill Matt. Người dùng kể một tình huống đã có trong bộ Matt thì đọc file này trước.
- `case-studies/NN-*.md`: mỗi file một tình huống, cuối file là mục "Thực tế đã gặp". Danh sách trong `case-studies/README.md`.

## Cách trả lời

- Trả lời bằng tiếng Việt. Giữ nguyên thuật ngữ gốc tiếng Anh (party mode, memlog, spine, headless…).
- Khi người dùng kể một tình huống thực tế, tìm case study khớp nhất và trả lời dựa trên nó cùng `SKILL.md` liên quan. Không có file khớp thì ghép skill theo `bmad-help.csv`, và nói rõ khi không có skill nào phủ tình huống đó. Nếu bộ Matt Pocock hợp hơn, nói thẳng và dẫn sang tài liệu so sánh.
- Sau khi trả lời, đề nghị ghi kết quả vào mục "Thực tế đã gặp" của file khớp, hoặc tạo file tình huống mới, theo hướng dẫn trong `case-studies/README.md`.
- Không ghi tên khách hàng, tên công ty, mã nguồn nội bộ hay thông tin bí mật vào repo. Viết case study ở dạng tổng quát.
