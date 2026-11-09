# Bộ skill Matt Pocock: tra cứu và hỏi đáp

Repo gom mã nguồn bộ skill [mattpocock/skills](https://github.com/mattpocock/skills) đã cài và các tài liệu tiếng Việt viết về nó. Dùng để:

- **tra cứu** một skill làm gì, gọi thế nào, nằm ở đâu trong flow;
- **hỏi về tình huống thực tế**: kể bối cảnh, agent đề xuất cách ghép skill và đọc mã nguồn skill để trả lời;
- **gửi tài liệu nhập môn** cho người mới.

Phiên bản skill: repo nguồn ngày 2026-10-31 (commit `4ae2317`), 37 skill. Chi tiết trong `skills-lock.json` và mục 9 của tài liệu tham chiếu.

## Cấu trúc

```text
.
├── CLAUDE.md                  ← chỉ đường cho agent khi hỏi đáp trong repo này
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

Phân vân giữa bộ này và BMAD Method (khi nào dùng cái nào, theo vai PM, Techlead, Dev): xem [`study/bmad-method/docs/so-sanh-voi-matt-pocock.md`](../bmad-method/docs/so-sanh-voi-matt-pocock.md).

## Dùng với Claude

**Claude Code** (trên máy hoặc trên web): mở repo, `CLAUDE.md` được nạp tự động. Hỏi thẳng, ví dụ: *"Tôi nhận một dự án không có tài liệu, nên bắt đầu thế nào?"*.

**Project trên claude.ai:**

1. Tạo project, thêm repo này làm knowledge (kết nối GitHub, hoặc tải lên thư mục `docs/`, `case-studies/` và `.agents/skills/`).
2. Chép nội dung `CLAUDE.md` vào phần **Project instructions**.
3. Khi repo thay đổi, đồng bộ lại knowledge của project.

## Cập nhật bộ skill

```bash
npx skills@latest update -p -y   # cập nhật các skill đã có trong skills-lock.json
git diff --stat .agents/skills   # xem skill nào đổi
```

Sau đó đọc `git diff` của từng skill, cập nhật `docs/` và thêm một mục vào nhật ký (mục 9 của tài liệu tham chiếu). Nếu lệnh `update` tạo thêm `.claude/skills/`, thư mục này đã được bỏ qua trong `.gitignore`.
