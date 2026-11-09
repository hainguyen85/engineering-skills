# Case study

Mỗi file là một **tình huống**: khi nào gặp, chuỗi skill, các bước kèm prompt mẫu, lưu ý. Cuối mỗi file có mục **Thực tế đã gặp** để ghi lại kết quả khi áp dụng thật. Bảng tổng hợp nằm ở [onboarding mục 9](../docs/bmad-method-onboarding.md#9-bản-đồ-tình-huống).

| # | Tình huống |
|---|---|
| [01](01-danh-gia-cheo-y-tuong-bang-party-mode.md) | Đánh giá chéo một ý tưởng tính năng trước khi viết PRD |

Tình huống đã có trong bộ Matt Pocock (bug từ QA, change request mơ hồ, domain lạ…): xem cách làm bằng BMAD ở [docs/case-study-matt-pocock-voi-bmad.md (ở gốc repo)](../../docs/case-study-matt-pocock-voi-bmad.md).

## Ghi lại thực tế

Khi áp dụng một tình huống, thêm vào mục **Thực tế đã gặp** của file đó:

```md
### YYYY-MM-DD: <tóm tắt một dòng>

**Phiên bản BMAD:** <version trong _bmad/_config/manifest.yaml> · **Công cụ:** <Claude Code / Copilot / Antigravity / Kiro>

- **Bối cảnh:** đầu vào có gì, muốn đạt gì.
- **Đã làm:** skill nào, thứ tự nào, prompt chính, chế độ (session/subagent); chỗ nào làm khác file này.
- **Kết quả:** ra được gì; chỗ nào chạy tốt, chỗ nào không; tốn khoảng bao nhiêu thời gian, token.
- **Bài học:** lần sau làm khác đi thế nào. Nếu bài học đúng cho mọi lần, sửa luôn phần Các bước phía trên.
```

Tình huống mới chưa có file: tạo file `NN-<slug>.md` theo cấu trúc các file sẵn có, rồi thêm một dòng vào bảng trên và vào onboarding mục 9.

## Không ghi

Tên khách hàng, tên công ty, mã nguồn nội bộ, thông tin bí mật. Thay bằng mô tả chung, ví dụ "một hệ thống quản lý nghỉ phép", "luồng duyệt nhiều cấp".
