# 06. Change request mơ hồ, phải hỏi khách hàng hoặc BA

**Khi nào:** nhận yêu cầu thay đổi chỉ có vài dòng. Bạn trả lời được phần kỹ thuật, nhưng quy tắc nghiệp vụ phải hỏi người khác.

**Chuỗi skill:** `/grill-with-docs` (đánh dấu PENDING) → `/to-questionnaire` → gửi đi → `/grill-with-docs` tiếp với câu trả lời → `/to-spec`

## Các bước

### 1. Grill, đánh dấu câu chưa biết

```text
/grill-with-docs Khách hàng muốn "cho phép duyệt đơn nghỉ phép theo nhóm".
```

Gặp câu không tự trả lời được, đáp:

```text
Q3: chưa biết, đánh dấu PENDING. Q4 yes. Q5: PENDING, cần hỏi BA.
```

Agent ghi lại câu hỏi và tiếp tục grill các câu khác.

### 2. Tạo bảng câu hỏi (vẫn trong phiên đó)

```text
/to-questionnaire Gom các câu PENDING.
```

Agent chỉ hỏi bạn hai điều:

- **Gửi ai:** vai trò và mức hiểu biết của người nhận, ví dụ *"BA phía khách hàng, rành nghiệp vụ, không rành kỹ thuật"*.
- **Cần lấy lại gì:** những quyết định hay dữ kiện bạn cần.

Kết quả là file `to-questionnaire-<slug>.md`, gồm mục đích, bối cảnh ngắn, câu quan trọng nhất đặt trước, mỗi câu một ý và có chỗ trống để trả lời.

### 3. Gửi và chờ

Gửi file cho người nhận, hoặc mở họp và điền cùng nhau. Chưa chạy `/to-spec` khi còn câu PENDING.

### 4. Grill tiếp với câu trả lời

Nếu phiên cũ còn mở:

```text
BA đã trả lời trong to-questionnaire-duyet-theo-nhom.md. Cập nhật các câu PENDING, grill tiếp phần còn lại.
```

Nếu phiên cũ đã đóng, trước đó chạy `/handoff` rồi mở phiên mới với file bàn giao và file câu trả lời.

### 5. `/to-spec`

Tiêu chí nghiệm thu trong spec là căn cứ để bạn tự test và để người review đối chiếu.

## Ví dụ

Các câu PENDING:

- *"Duyệt theo nhóm có cho phép một người duyệt thay cả nhóm không?"*
- *"Đơn đã có người trong nhóm từ chối thì người khác còn duyệt được không?"*

BA trả lời. Thuật ngữ mới **Nhóm duyệt** và **Kết quả vòng duyệt** được ghi vào `GLOSSARY.md`.

## Lưu ý

- Chọn câu trả lời "PENDING" thay vì đoán. Đáp án đoán sẽ đi thẳng vào spec, ticket và code.
- Một bảng câu hỏi chỉ gửi **một người**. Nhiều người nhận thì tạo nhiều bảng.

## Thực tế đã gặp

_Chưa có._
