# 11. Vào dự án có domain lạ

**Khi nào:** dự án thuộc lĩnh vực bạn chưa biết, ví dụ ngân hàng, bảo hiểm, quản lý đồng ý xử lý dữ liệu cá nhân, kiểm định chất lượng. Đọc code hiểu được kỹ thuật nhưng không hiểu vì sao nghiệp vụ lại như vậy.

**Chuỗi skill:** `/teach` (thư mục học riêng) + `/domain-modeling` (trên repo dự án)

## Các bước

### 1. Học domain: `/teach` trong thư mục riêng

```text
mkdir hoc-consent && cd hoc-consent
/teach Tôi cần hiểu nghiệp vụ quản lý đồng ý xử lý dữ liệu cá nhân,
đủ để maintain một hệ thống consent trong 2 tuần tới.
```

Agent dựng một thư mục học gồm:

| File | Vai trò |
|---|---|
| `MISSION.md` | Vì sao bạn học; mọi bài học bám theo đây |
| `RESOURCES.md` | Nguồn đáng tin: văn bản luật, chuẩn, tài liệu sản phẩm |
| `lessons/*.html` | Mỗi bài một chủ đề hẹp, có tương tác hoặc quiz |
| `reference/*.html` | Bảng tra nhanh, in được |
| `learning-records/` | Điều bạn đã nắm, để buổi sau học tiếp đúng mức |
| `GLOSSARY.md` | Thuật ngữ của chủ đề đang học |

Mỗi buổi chạy lại `/teach` trong thư mục đó, agent học tiếp từ chỗ bạn đang ở.

### 2. Nối kiến thức vào repo: `/domain-modeling`

```text
/domain-modeling Đối chiếu các khái niệm tôi vừa học (Mục đích xử lý, Rút lại đồng ý,
Thời hạn lưu trữ) với code module consent. Đề xuất thuật ngữ cho GLOSSARY.md, hỏi tôi xác nhận.
```

`GLOSSARY.md` của **repo** chỉ chứa thuật ngữ mà hệ thống thật sự dùng, không chép cả glossary của thư mục học.

## Lưu ý

- Thư mục học không đặt trong repo dự án; nó là của riêng bạn.
- Khái niệm mà luật hay khách hàng định nghĩa khác với cách hiểu của bạn thì đánh dấu PENDING rồi hỏi bằng `/to-questionnaire`, xem [06](06-change-request-mo-ho.md).

## Thực tế đã gặp

_Chưa có._
