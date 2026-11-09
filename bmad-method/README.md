# BMAD Method: tra cứu và hỏi đáp

Repo gom mã nguồn bộ skill [BMAD Method](https://github.com/bmad-code-org/BMAD-METHOD) đã cài và các tài liệu tiếng Việt viết về nó. Người đọc chính là **PM và Techlead**. Dùng để:

- **tra cứu** một skill hoặc agent làm gì, gọi thế nào, nằm ở đâu trong flow;
- **hỏi về tình huống thực tế**: kể bối cảnh, agent đề xuất cách ghép skill và đọc mã nguồn để trả lời;
- **chọn giữa BMAD và bộ Matt Pocock** cho từng vai và từng loại việc;
- **gửi tài liệu nhập môn** cho người mới.

Phiên bản: BMAD **6.12.4** (module `core` và `bmm`), 29 skill. Chi tiết trong `_bmad/_config/manifest.yaml` và mục 8 của tài liệu tham chiếu.

## Cấu trúc

```text
.
├── CLAUDE.md                       ← chỉ đường cho agent khi hỏi đáp trong repo này
├── docs/
│   ├── bmad-method.md              ← tài liệu tham chiếu: kiến trúc, 29 skill, flow, nhật ký cập nhật
│   ├── bmad-method-onboarding.md   ← hướng dẫn nhập môn cho PM và Techlead
│   ├── so-sanh-voi-matt-pocock.md  ← khi nào dùng BMAD, khi nào dùng Matt Pocock
│   └── case-study-matt-pocock-voi-bmad.md ← 14 case study của Matt Pocock làm bằng BMAD thế nào
├── case-studies/                   ← tình huống thực tế (mẫu trong README của thư mục)
├── .agents/skills/bmad-*/          ← mã nguồn 29 skill, chỉ để đọc
└── _bmad/                          ← cấu hình, script và danh mục skill của bộ cài
```

## Gửi tài liệu nhập môn

Gửi link tới [`docs/bmad-method-onboarding.md`](docs/bmad-method-onboarding.md). Người đang dùng bộ Matt Pocock thì gửi thêm [`docs/so-sanh-voi-matt-pocock.md`](docs/so-sanh-voi-matt-pocock.md).

## Dùng với Claude

**Claude Code** (trên máy hoặc trên web): mở repo, `CLAUDE.md` được nạp tự động. Hỏi thẳng, ví dụ: *"Tôi có ý tưởng một tính năng mới, muốn phản biện trước khi viết PRD thì làm thế nào?"*.

**Project trên claude.ai:**

1. Tạo project, thêm repo này làm knowledge (kết nối GitHub, hoặc tải lên `docs/`, `case-studies/` và `.agents/skills/`).
2. Chép nội dung `CLAUDE.md` vào phần **Project instructions**.
3. Khi repo thay đổi, đồng bộ lại knowledge của project.

## Cập nhật bản BMAD

Bản trong repo này được chép từ một bản cài thật bằng bộ cài chính thức (cài cho `claude-code`, `antigravity-cli` và `kiro`). Để lên bản mới:

```bash
npx bmad-method@latest install      # chạy trong repo này, chọn lại module core + bmm
git diff --stat .agents/skills _bmad  # xem skill nào đổi
```

Sau đó đọc `git diff` của từng skill, cập nhật `docs/` và thêm một mục vào nhật ký (mục 8 của tài liệu tham chiếu). Bộ cài sẽ tạo thêm `.claude/skills/` và `.kiro/skills/`; hai thư mục này đã được bỏ qua trong `.gitignore`.

Lưu ý: `_bmad/config.toml` ghi `project_name = "Tools"` vì bản gốc được cài ở `D:\Workspace\Tools`. Giá trị này chỉ ảnh hưởng khi chạy skill, không ảnh hưởng việc đọc mã nguồn.
