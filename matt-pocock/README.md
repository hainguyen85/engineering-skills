# Bộ skill Matt Pocock: tra cứu và hỏi đáp

Thư mục này (trong repo [`engineering-skills`](../README.md)) gom mã nguồn bộ skill [mattpocock/skills](https://github.com/mattpocock/skills) đã cài và các tài liệu tiếng Việt viết về nó. Dùng để:

- **tra cứu** một skill làm gì, gọi thế nào, nằm ở đâu trong flow;
- **hỏi về tình huống thực tế**: kể bối cảnh, agent đề xuất cách ghép skill và đọc mã nguồn skill để trả lời;
- **gửi tài liệu nhập môn** cho người mới.

Phiên bản skill: repo nguồn ngày 2026-10-31 (commit `4ae2317`), 37 skill. Chi tiết trong `skills-lock.json` và mục 9 của tài liệu tham chiếu.

## Cấu trúc

```text
matt-pocock/
├── CLAUDE.md                  ← chỉ đường cho agent khi hỏi về bộ Matt Pocock
├── docs/
│   ├── matt-pocock-skills.md              ← tài liệu tham chiếu (cả 38 skill, kiến trúc, nhật ký cập nhật)
│   ├── matt-pocock-skills-onboarding.md   ← hướng dẫn nhập môn, có case study
│   └── matt-pocock-autonomous-loops.md    ← vòng lặp tự động với /implement-spec
├── case-studies/              ← tình huống thực tế đã gặp (mẫu trong README của thư mục)
├── .agents/skills/<tên>/      ← mã nguồn 37 skill, chỉ để đọc
└── skills-lock.json           ← nguồn và hash của từng skill
```

## Gửi tài liệu nhập môn

Gửi link tới [`docs/matt-pocock-skills-onboarding.md`](docs/matt-pocock-skills-onboarding.md). Tài liệu này liên kết sang tài liệu tham chiếu khi cần tra chi tiết.

Phân vân giữa bộ này và BMAD Method (khi nào dùng cái nào, theo vai PM, Techlead, Dev): xem [`docs/so-sanh-voi-matt-pocock.md`](../docs/so-sanh-voi-matt-pocock.md) ở gốc repo.

## Cập nhật bộ skill

```bash
cd matt-pocock
npx skills@latest update -p -y   # cập nhật các skill đã có trong skills-lock.json
git diff --stat .agents/skills   # xem skill nào đổi
```

Sau đó đọc `git diff` của từng skill, cập nhật `docs/` và thêm một mục vào nhật ký (mục 9 của tài liệu tham chiếu). Nếu lệnh `update` tạo thêm `.claude/skills/`, thư mục này đã được bỏ qua trong `.gitignore`.
