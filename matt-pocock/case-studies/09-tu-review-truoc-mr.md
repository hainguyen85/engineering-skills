# 09. Tự review trước khi gửi MR

**Khi nào:** code xong một ticket hoặc một nhánh, muốn tự soát trước khi gửi người review (Leader, đồng nghiệp).

**Chuỗi skill:** `/code-review` → sửa → `/pr`

## Các bước

### 1. Review hai trục

```text
/code-review develop .scratch/duyet-theo-nhom/issues/02-chon-nhom-duyet.md
```

- **Mốc so sánh** (`develop`): nhánh, commit hay tag. Agent so sánh `git diff develop...HEAD`.
- **Spec:** đường dẫn ticket hoặc spec. Bỏ trống thì agent tự tìm trong commit message và `.scratch/`, không thấy thì hỏi.

Agent chạy hai subagent song song, báo cáo tách riêng:

| Trục | Đối chiếu với | Bắt được |
|---|---|---|
| **Standards** | `CODING_STANDARDS.md`, `CONTRIBUTING.md` và các file chuẩn khác, cộng danh sách code smell của Fowler | Vi phạm chuẩn nhóm; code smell (trùng lặp, tên khó hiểu, Feature Envy…), luôn ở mức gợi ý |
| **Spec** | Ticket hoặc spec | Làm thiếu, làm sai, làm thừa so với yêu cầu |

### 2. Sửa

Sửa những gì đồng ý, ghi lại những gì cố ý không sửa để giải thích trong MR.

### 3. Mô tả MR

```text
Viết mô tả MR cho nhánh này. Phần Evidence thêm bảng: AC → test case → kết quả tự test.
```

`/pr` mặc định có ba phần:

- **Summary:** hình nhỏ nhất thể hiện thay đổi.
- **Evidence:** test, output, ảnh trước và sau.
- **Merge Danger:** đảo ngược được không, ảnh hưởng tới đâu.

Nếu người review cần bảng AC, dặn thêm như prompt trên.

## Ví dụ bảng Evidence

| AC | Test case | Kết quả |
|---|---|---|
| AC1: Chọn nhóm duyệt khi tạo đơn | TC1.1 chọn nhóm có 3 người; TC1.2 nhóm rỗng → báo lỗi | Đạt / Đạt |
| AC2: Một người trong nhóm duyệt là đủ | TC2.1 duyệt bởi thành viên thứ 2 | Đạt |

## Lưu ý

- Repo chưa có `CODING_STANDARDS.md` thì trục Standards chỉ còn danh sách code smell. Dùng `/retro` để dần dần xây file này.
- `/code-review` không đọc comment review trên MR. Khi người review góp ý, dán các comment vào phiên và nhờ agent sửa. Góp ý nào lặp lại nhiều lần thì đưa vào `CODING_STANDARDS.md` qua `/retro`.

## Thực tế đã gặp

_Chưa có._
