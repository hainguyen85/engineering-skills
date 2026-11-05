# 08. Nâng cấp lớn kéo dài nhiều phiên

**Khi nào:** lên major version của framework, đổi cơ sở dữ liệu, tách một module thành service riêng. Nhiều quyết định phụ thuộc nhau, một phiên không chứa nổi.

**Chuỗi skill:** `/wayfinder` → `/to-spec` → `/to-tickets` → `/implement-spec` (hoặc `/implement` từng ticket) → `/wizard` cho bước cutover người phải làm

## Các bước

### 1. Lập map

```text
/wayfinder Nâng framework web từ phiên bản 2 lên 3 cho repo này.
Destination: spec chuyển đổi đủ để chia ticket, chưa sửa code.
```

Destination có thể là một spec, một quyết định, hoặc **một thay đổi làm tại chỗ** (ví dụ migration dữ liệu). Nếu muốn map vừa quyết vừa làm, ghi rõ điều đó vào mục **Notes** của map.

Ticket điển hình của loại việc này:

| Loại | Ví dụ |
|---|---|
| `research` | Breaking change của bản mới ảnh hưởng gì tới repo; thư viện nào chưa tương thích |
| `grilling` | Nâng một lần hay từng module; giữ API cũ song song bao lâu |
| `prototype` | Thử nâng một module nhỏ nhất để đo khối lượng sửa |
| `task` | Xin môi trường thử; xin quyền nâng phiên bản JDK trên server build |

Mỗi phiên giải **một ticket**, trừ ticket research.

### 2. Từ map sang code

- `/to-spec` gộp các quyết định trên map thành spec.
- `/to-tickets` chia ticket theo lát cắt: mỗi ticket để repo build được và test xanh.
- `/implement-spec` chạy các ticket không chặn nhau song song, mỗi ticket một worktree. Hoặc `/implement` từng ticket nếu muốn theo sát.

### 3. Cutover

```text
/wizard Viết wizard cho bước chuyển production: backup DB, chạy migration, đổi cấu hình, kiểm tra sức khoẻ.
```

Agent viết một script bash dẫn bạn từng bước, hỏi xác nhận trước mỗi thao tác không đảo ngược được, nhận secret ở chế độ ẩn. Agent không tự chạy script.

## Lưu ý

- Ticket `research` của wayfinder **push** nhánh `research/<name>`. Nếu nhóm không cho agent push, dặn agent *"giữ nhánh research ở local"*.
- `/implement` và `/implement-spec` tự commit lên nhánh. Nếu nhóm không cho agent commit, dặn agent dừng trước bước commit.
- Map dùng tracker GitLab/GitHub thì cả nhóm thấy cùng một map. Map dùng tracker local thì chỉ người giữ repo thấy.

## Thực tế đã gặp

_Chưa có._
