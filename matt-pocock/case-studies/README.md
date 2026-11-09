# Case study

Mỗi file là một **tình huống**: khi nào gặp, chuỗi skill, các bước kèm prompt mẫu, ví dụ, lưu ý. Cuối mỗi file có mục **Thực tế đã gặp** để ghi lại kết quả khi áp dụng thật. Bảng tổng hợp nằm ở [onboarding mục 11](../docs/matt-pocock-skills-onboarding.md#11-bản-đồ-tình-huống).

| # | Tình huống |
|---|---|
| [01](01-nhan-du-an-khong-tai-lieu.md) | Nhận dự án không có tài liệu |
| [02](02-xay-san-pham-moi-tu-y-tuong.md) | Xây sản phẩm mới từ ý tưởng |
| [03](03-qa-tra-ve-loat-bug.md) | QA trả về một loạt bug cuối đợt |
| [04](04-bug-chap-chon.md) | Bug chập chờn, chậm, không thấy nguyên nhân |
| [05](05-refactor-module-cu.md) | Refactor module cũ |
| [06](06-change-request-mo-ho.md) | Change request mơ hồ, phải hỏi khách hàng hoặc BA |
| [07](07-chon-thu-vien-cong-nghe.md) | Chọn thư viện, công nghệ, đánh giá API bên thứ ba |
| [08](08-nang-cap-lon.md) | Nâng cấp lớn kéo dài nhiều phiên |
| [09](09-tu-review-truoc-mr.md) | Tự review trước khi gửi MR |
| [10](10-ban-giao-viec.md) | Bàn giao việc |
| [11](11-domain-la.md) | Vào dự án có domain lạ |
| [12](12-agent-lap-lai-loi.md) | Agent lặp đi lặp lại cùng một lỗi |
| [13](13-viec-dinh-ky.md) | Thiết kế quy trình cho việc định kỳ |
| [14](14-viet-bai-noi-bo.md) | Viết bài chia sẻ hoặc tài liệu nội bộ |

## Ghi lại thực tế

Khi áp dụng một tình huống, thêm vào mục **Thực tế đã gặp** của file đó:

```md
### YYYY-MM-DD: <tóm tắt một dòng>

**Phiên bản skill:** <ngày hoặc commit trong skills-lock.json>

- **Bối cảnh:** đầu vào có gì, muốn đạt gì.
- **Đã làm:** skill nào, thứ tự nào, prompt chính; chỗ nào làm khác file này.
- **Kết quả:** ra được gì; chỗ nào chạy tốt, chỗ nào không.
- **Bài học:** lần sau làm khác đi thế nào. Nếu bài học đúng cho mọi lần, sửa luôn phần Các bước phía trên.
```

Tình huống mới chưa có file: tạo file `NN-<slug>.md` theo cấu trúc các file sẵn có, rồi thêm một dòng vào bảng trên và vào onboarding mục 11.

## Không ghi

Tên khách hàng, tên công ty, mã nguồn nội bộ, thông tin bí mật. Thay bằng mô tả chung, ví dụ "một hệ thống quản lý nghỉ phép", "module duyệt nhiều cấp".
