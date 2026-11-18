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
├── .agents/skills/          ← mã nguồn skill của mọi bộ (66 skill), dùng chung
├── _bmad/                   ← cấu hình và script của bộ cài BMAD
├── skills-lock.json         ← nguồn và hash của bộ Matt Pocock
├── docs/                    ← tài liệu so sánh giữa các bộ
├── matt-pocock/             ← chỉ tài liệu về bộ Matt Pocock
│   ├── README.md, CLAUDE.md
│   └── docs/, case-studies/
└── bmad-method/             ← chỉ tài liệu về BMAD
    ├── README.md, CLAUDE.md
    └── docs/, case-studies/
```

Các thư mục `matt-pocock/` và `bmad-method/` chỉ chứa tài liệu tìm hiểu; mã nguồn nằm chung ở gốc, đúng như một dự án thật cài các bộ này. Skill BMAD có tiền tố `bmad-`, skill Matt Pocock thì không, nên không trùng tên.

Vì `.agents/skills/` nằm ở gốc, công cụ nào đọc chuẩn này (Antigravity, Copilot…) khi mở repo ở gốc **có thể nạp cả 66 skill**. Claude Code đọc `.claude/skills/` (thư mục này bị `.gitignore` bỏ qua), nên không tự nạp trừ khi bộ cài tạo symlink ở đó. Một số skill tự commit, push hoặc ghi ra ngoài (xem cảnh báo ở mục 11 của [onboarding Matt Pocock](matt-pocock/docs/matt-pocock-skills-onboarding.md#11-bản-đồ-tình-huống)), nên trong repo này vẫn **chỉ đọc, không chạy** trừ khi người dùng yêu cầu.

Thêm một bộ skill mới: chép mã nguồn vào `.agents/skills/` (và thư mục cấu hình riêng của bộ, nếu có) ở gốc, tạo thư mục `<tên-bộ>/` chứa tài liệu theo cùng khuôn (README, CLAUDE.md, docs, case-studies), rồi thêm một dòng vào bảng trên và vào `CLAUDE.md` ở gốc.

## Dùng với Claude

**Claude Code** (trên máy hoặc trên web): mở repo ở gốc, `CLAUDE.md` được nạp tự động. Hỏi thẳng, ví dụ: *"Tôi nhận một change request mơ hồ, phải hỏi BA. Nên dùng BMAD hay Matt Pocock, làm thế nào?"*.

**Project trên claude.ai:**

1. Tạo project, thêm repo này làm knowledge (kết nối GitHub, hoặc tải lên `docs/` ở gốc, `docs/` và `case-studies/` của từng bộ, cùng `.agents/skills/` và `_bmad/` ở gốc).
2. Chép nội dung `CLAUDE.md` ở gốc vào phần **Project instructions**.
3. Khi repo thay đổi, đồng bộ lại knowledge của project.

## Cập nhật từng bộ

Xem mục "Cập nhật" trong README của [Matt Pocock](matt-pocock/README.md#cập-nhật-bộ-skill) và [BMAD](bmad-method/README.md#cập-nhật-bản-bmad). Lệnh cập nhật chạy **ở gốc repo**, vì mã nguồn nằm ở đó.
