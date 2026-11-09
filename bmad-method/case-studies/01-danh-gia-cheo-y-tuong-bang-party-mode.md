# 01. Đánh giá chéo một ý tưởng tính năng trước khi viết PRD

**Nguồn:** bài [Tại sao Product Manager nên dùng BMad Method để thiết kế và phát triển Product?](https://blog.datht.com/p/tai-sao-product-manager-nen-dung), viết lại ở dạng tổng quát và đối chiếu với BMAD 6.12.4.

## Khi nào gặp

PM có ý tưởng cho một tính năng phức tạp và một user flow sơ bộ. Muốn biết sớm ý tưởng vướng gì về kỹ thuật và trải nghiệm, **trước khi** viết PRD và trước khi kéo dev, designer vào họp. Thường gặp khi team nhỏ, PM kiêm nhiều vai, hoặc làm một mình ngoài giờ.

## Chuỗi skill

```text
bmad-party-mode (--mode subagent)  →  bmad-forge-idea  →  bmad-prd
     tìm điểm yếu                       chốt từng điểm        viết PRD
```

Bài viết gốc chỉ dùng bước 1 rồi tự viết PRD. Hai bước sau là đề xuất thêm, dựa trên mã nguồn: party mode không sinh tài liệu và không tự tổng kết, nên cần một bước chốt quyết định trước khi viết PRD.

## Các bước

### 1. Mở bàn tròn với đúng người

Chuẩn bị mô tả ý tưởng và user flow (dán vào chat hoặc để trong một file). Gọi party mode, gọi đích danh người cần mời và giao việc cho từng người:

```text
/bmad-party-mode --mode subagent
Tôi là PM. Mời Winston (Architect) và Sally (UX).
Ý tưởng và user flow nằm ở docs/y-tuong/<tên>.md.
Winston: tìm điểm yếu về khả năng mở rộng — nếu lượng người dùng tăng gấp 10 lần thì hỏng ở đâu.
Sally: chỉ ra những bước người dùng dễ bị vướng (friction), số màn hình có quá nhiều không.
Cứ tranh luận với nhau, đừng vội thống nhất.
```

- **Vì sao `--mode subagent`:** mặc định (`session`) là một model nói thay cả phòng, nên các giọng dễ vô tình đồng ý với nhau. `subagent` cho mỗi persona một context riêng. Tốn token hơn; chỉ dùng cho lượt quan trọng, hoặc dùng `--mode auto` để agent tự quyết khi nào cần tách.
- Muốn thêm góc nhìn "chống đồng thuận" thì đổi sang `--party anti-consensus-club` ở giữa phiên. Nhóm này gồm người sinh phương án, người kiểm bằng chứng, người dừng vòng lặp và người thách thức giả định.
- Muốn có giọng không có sẵn (CFO, trưởng CSKH, một khách hàng khó tính) thì gọi tên và mô tả họ ngay trong câu lệnh.

### 2. Hỏi vặn, kéo cuộc tranh luận sang hướng cần

Party chạy đến khi bạn nói dừng. Trong lúc chạy:

- Hỏi lại từng persona về cảnh báo của họ: *"Winston, bottleneck cụ thể nằm ở bước nào của flow? Cần số liệu gì để biết chắc?"*
- Đẩy hai người vào thế đối lập: *"Sally muốn gộp màn hình, Winston có thấy việc đó làm khó phần dữ liệu không?"*
- Khi đã đủ, nói *"tổng kết lại các điểm yếu chính"*. Agent đọc lại các ý đáng giá và đề nghị xuất HTML kỷ niệm (lưu ở `_bmad-output/party-mode/`).

### 3. Chốt từng điểm yếu bằng `bmad-forge-idea`

Mở phiên mới:

```text
/bmad-forge-idea
Ý tưởng: <tên>. Mục tiêu: kiểm tra xem nó có đứng vững không.
Đây là các điểm yếu từ buổi party mode: <dán phần tổng kết>.
Attack this.
```

Forge-idea hỏi mỗi lần một câu, theo thứ tự phụ thuộc, và ghi từng quyết định vào memlog. Kết thúc ở một trong ba trạng thái:

- **Hardened**: có `forged-idea.md` ngắn gọn, ghi các quyết định đã chốt và phương án đã loại.
- **Killed**: ý tưởng không đứng vững; ghi lý do. Phát hiện sớm cũng là một kết quả tốt.
- **Clearer**: hiểu rõ hơn nhưng chưa đủ chốt.

Cả ba trường hợp đều có `forge-report.html` trong `_bmad-output/forge/<slug>/`.

### 4. Viết PRD từ kết quả đã chốt

```text
/bmad-prd
Tạo PRD mới. Đầu vào: _bmad-output/forge/<slug>/forged-idea.md và docs/y-tuong/<tên>.md.
```

Trong lúc viết PRD, khi tới mục rủi ro hoặc NFR, có thể gọi lại `bmad-party-mode` hoặc `bmad-advanced-elicitation` (ví dụ pre-mortem) cho riêng mục đó.

## Khác với bài viết

| Bài viết nói | Bản 6.12.4 thực tế |
|---|---|
| "Hơn 12 Specialized Agents" như PM, Architect, UX, **Scrum Master**… | Chỉ có **5 agent có persona**: Mary (Analyst), John (PM), Sally (UX), Winston (Architect), Amelia (Dev). **Không có Scrum Master**: phần việc đó nằm trong `bmad-sprint-planning`. Party mode có thêm 9 persona dựng sẵn trong 2 nhóm (`code-review-crew`, `anti-consensus-club`); cộng lại 14, nhưng 9 persona này không phải agent. Bài có thể dựa trên một bản cũ hơn |
| "Tích hợp vào Cursor, Claude Code, VS Code" | Bộ cài bản này được chọn cho Claude Code, Antigravity, Kiro. Danh sách công cụ đầy đủ của bộ cài chưa được kiểm tra ở đây |
| Architect "lập tức" chỉ ra bottleneck khi tải tăng 10 lần | Đây là kết quả của một phiên cụ thể. Ở chế độ mặc định, mọi persona do **một model** nói thay, nên đây là một góc nhìn được nhập vai, không phải chuyên gia độc lập. Cảnh báo kiểu này cần được kiểm lại bằng số liệu thật |
| PRD cuối "phủ 90% edge case" | Con số tự đánh giá của tác giả, không đo được từ công cụ |
| Party mode cho ra "một màn cross-evaluate toàn diện" | Party mode được dặn **không tự tổng kết**, để bất đồng tồn tại. Phần đánh giá có cấu trúc phải tự hỏi, hoặc chuyển sang `bmad-forge-idea` |
| Không nhắc | `bmad-forge-idea` (2 giọng mỗi lượt, có kết luận Hardened/Killed) và `bmad-advanced-elicitation` (pre-mortem, red team…) phục vụ đúng mục đích "tự phản biện" của bài, có khi còn hợp hơn party mode |

## Lưu ý

- Ý tưởng nhạy cảm: nói rõ không tra web. Brief, PRD và PRFAQ mặc định giao subagent đi tra web.
- Party mode **không thay** buổi họp thật với dev và designer; nó giúp bạn đến buổi họp đó với ít lỗ hổng hiển nhiên hơn.
- Mọi persona đều do model nhập vai. Coi cảnh báo của chúng là **giả thuyết cần kiểm chứng**, không phải kết luận.

## Thực tế đã gặp

_Chưa có. Ghi lại theo mẫu trong [README](README.md) sau lần chạy đầu tiên (dự kiến là case study 02 khi có ý tưởng thật)._
