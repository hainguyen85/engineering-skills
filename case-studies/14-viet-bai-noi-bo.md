# 14. Viết bài chia sẻ hoặc tài liệu nội bộ

**Khi nào:** cần viết một bài chia sẻ kinh nghiệm, một tài liệu hướng dẫn, hay một bài blog kỹ thuật, và muốn bài có lập luận chặt, không dùng thuật ngữ trước khi giải thích.

**Chuỗi skill:** `/writing-fragments` → `/writing-shape` (bài lập luận) hoặc `/writing-beats` (bài kể chuyện)

## Các bước

### 1. Gom nguyên liệu: `/writing-fragments`

```text
/writing-fragments Tôi muốn viết về bài học khi dùng bộ skill Matt Pocock cho một dự án tiếp nhận không có tài liệu.
```

- **Agent phỏng vấn liên tục** và ghi mỗi ý hay thành một fragment vào `drafts/tiep-nhan-fragments.md`, các fragment ngăn nhau bằng `---`.
- **Chưa có dàn ý.** Fragment có thể là một câu sắc, một ví dụ, một nửa ý.
- **Săn leading word:** một từ gói cả ý tưởng. Ví dụ *"tài liệu mọc dần"* cho ý "tài liệu sinh ra như sản phẩm phụ của công việc".
- **Sửa bất cứ lúc nào:** *"bỏ cái vừa rồi"*, *"viết lại cho sắc hơn"*, *"gộp hai cái đó"*.

### 2. Dựng bài

**Bài lập luận** (hướng dẫn, phân tích):

```text
/writing-shape drafts/tiep-nhan-fragments.md
Lưu bài vào articles/tiep-nhan.md. Người đọc: dev đã dùng agent, chưa biết bộ skill.
```

1. Chốt **prerequisite**: người đọc đã biết gì.
2. Agent đưa 2–3 phần mở đầu với các luận điểm khác nhau. Bạn chọn một.
3. Agent dựng tiếp từng đoạn và tranh luận hình thức từng khối: văn xuôi hay danh sách, bảng hay callout.

**Bài kể chuyện** (blog, newsletter):

```text
/writing-beats drafts/tiep-nhan-fragments.md
```

Ở mỗi bước, agent đưa 2–3 beat khả dĩ tiếp theo. Bạn chọn, agent viết đúng một beat rồi dừng.

## Lưu ý

- **Grounding:** đoạn sau chỉ dùng khái niệm đã được giới thiệu ở đoạn trước, hoặc người đọc biết sẵn. Đây là chỗ khác biệt lớn nhất so với nhờ agent "viết một bài về X".
- File nguyên liệu chỉ để đọc khi dựng bài. Ý nào bị bỏ thì cứ để đó, dùng cho bài sau.
- Tài liệu cho **agent** đọc (skill, `CLAUDE.md`) thì theo nguyên tắc của `writing-for-agents`, không dùng ba skill này.

## Thực tế đã gặp

_Chưa có._
