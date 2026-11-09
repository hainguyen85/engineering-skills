# Engineering skills: tra cứu và hỏi đáp

Repo nghiên cứu các bộ skill cho AI coding agent (Claude Code, Antigravity, Kiro, Copilot…): gom mã nguồn đã cài để đọc, viết tài liệu tiếng Việt, ghi case study khi dùng thật, và so sánh các bộ với nhau.

| Bộ skill | Thư mục | Người đọc chính | Bắt đầu từ |
|---|---|---|---|
| [Matt Pocock](https://github.com/mattpocock/skills) (37 skill, bản 2026-10-31) | [`matt-pocock/`](matt-pocock/README.md) | Dev | [Nhập môn](matt-pocock/docs/matt-pocock-skills-onboarding.md) |
| [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) (29 skill, bản 6.12.4) | [`bmad-method/`](bmad-method/README.md) | PM (Product Manager), Techlead | [Nhập môn](bmad-method/docs/bmad-method-onboarding.md) |

Tài liệu so sánh giữa các bộ nằm ở [`docs/`](docs/):

- [`so-sanh-voi-matt-pocock.md`](docs/so-sanh-voi-matt-pocock.md): BMAD và Matt Pocock, khi nào dùng cái nào, theo vai PM, Techlead, Dev và theo Agile Scrum.
- [`case-study-matt-pocock-voi-bmad.md`](docs/case-study-matt-pocock-voi-bmad.md): 14 case study của bộ Matt Pocock, mỗi cái làm bằng BMAD thế nào.

## Cấu trúc

```text
.
├── README.md, CLAUDE.md     ← chỉ đường chung
├── docs/                    ← tài liệu so sánh giữa các bộ
├── matt-pocock/
│   ├── README.md, CLAUDE.md
│   ├── docs/, case-studies/
│   ├── .agents/skills/      ← mã nguồn, chỉ đọc
│   └── skills-lock.json
└── bmad-method/
    ├── README.md, CLAUDE.md
    ├── docs/, case-studies/
    ├── .agents/skills/      ← mã nguồn, chỉ đọc
    └── _bmad/               ← cấu hình và script của bộ cài
```

Mã nguồn skill nằm trong thư mục con của từng bộ, nên mở repo ở gốc thì Claude Code, Antigravity hay Kiro **không tự nạp** các skill này. Chúng chỉ để đọc.

Thêm một bộ skill mới: tạo thư mục `<tên-bộ>/` theo cùng khuôn (README, CLAUDE.md, docs, case-studies, mã nguồn), rồi thêm một dòng vào bảng trên và vào `CLAUDE.md` ở gốc.

## Dùng với Claude

**Claude Code** (trên máy hoặc trên web): mở repo ở gốc, `CLAUDE.md` được nạp tự động. Hỏi thẳng, ví dụ: *"Tôi nhận một change request mơ hồ, phải hỏi BA. Nên dùng BMAD hay Matt Pocock, làm thế nào?"*.

**Project trên claude.ai:**

1. Tạo project, thêm repo này làm knowledge (kết nối GitHub, hoặc tải lên `docs/` và các thư mục `docs/`, `case-studies/`, `.agents/skills/` của từng bộ).
2. Chép nội dung `CLAUDE.md` ở gốc vào phần **Project instructions**.
3. Khi repo thay đổi, đồng bộ lại knowledge của project.

## Cập nhật từng bộ

Xem mục "Cập nhật" trong README của [Matt Pocock](matt-pocock/README.md#cập-nhật-bộ-skill) và [BMAD](bmad-method/README.md#cập-nhật-bản-bmad). Lệnh cập nhật chạy **bên trong thư mục của bộ đó**.
