# 07. Chọn thư viện, công nghệ, hoặc đánh giá API bên thứ ba

**Khi nào:** phải chọn giữa vài thư viện hay dịch vụ, hoặc phải biết một API bên ngoài làm được gì trước khi thiết kế.

**Chuỗi skill:** `/research` → (nếu cần chạy thử) `/prototype` → `/grill-with-docs` để quyết → ADR

## Các bước

### 1. Research

```text
/research So sánh thư viện A, B, C để xuất file Excel trên 100 nghìn dòng trong Java:
streaming, bộ nhớ, giấy phép, mức độ bảo trì. Chỉ dùng tài liệu chính thức và source code.
```

- Agent chạy research **ở nền**, đọc **nguồn gốc** (tài liệu chính thức, source code, spec), không đọc bài viết lại của người khác.
- Kết quả là một file Markdown, mỗi nhận định có trích nguồn, lưu theo chỗ repo vẫn để ghi chú, ví dụ `docs/research/`.
- Trong lúc chờ, bạn làm việc khác được.

### 2. Prototype (nếu giấy bút chưa đủ)

```text
/prototype Viết thử xuất 100 nghìn dòng bằng thư viện A và B, đo bộ nhớ và thời gian.
```

Mở `/prototype` trong **session chat mới**, mang kết quả về phiên chính bằng `/handoff`. Prototype dùng xong thì bỏ.

### 3. Quyết định

```text
/grill-with-docs Chọn thư viện xuất Excel dựa trên docs/research/excel-export.md và kết quả prototype.
```

Nếu quyết định đủ 3 điều kiện (khó đảo ngược, gây ngạc nhiên nếu thiếu bối cảnh, là kết quả của một đánh đổi thật), agent đề xuất ghi ADR:

```md
# Dùng thư viện B cho xuất Excel

Cần xuất trên 100 nghìn dòng mà không tràn bộ nhớ. A đơn giản hơn nhưng nạp toàn bộ vào RAM;
B hỗ trợ streaming. Chọn B, chấp nhận API dài dòng hơn.
```

## Ví dụ khác

- Đánh giá API thanh toán của một nhà cung cấp: research, sau đó việc **đăng ký tài khoản sandbox** là việc tay. Nếu thủ tục nhiều bước thì dùng `/wizard` để dẫn bạn làm.

## Lưu ý

- Research chỉ trả lời câu hỏi có thể tra được. Câu hỏi kiểu "nhóm mình quen cái nào hơn" thì đưa vào grilling.
- Không ghi ADR cho lựa chọn hiển nhiên hoặc dễ đổi.

## Thực tế đã gặp

_Chưa có._
