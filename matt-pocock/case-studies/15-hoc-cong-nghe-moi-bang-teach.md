# 15. Học một công nghệ mới nhiều phiên bằng `/teach`

**Khi nào:** bạn tự học một công nghệ (ví dụ Kubernetes, Kafka) qua nhiều buổi, mỗi chủ đề một thư mục học riêng, và muốn bài học bám nguồn đáng tin thay vì kiến thức đoán của model.

**Chuỗi skill:** `/teach` làm trục + `/grilling` (chốt mission) + `/research` (đổ nguồn vào `RESOURCES.md`) + `/domain-modeling` (nuôi `GLOSSARY.md`) + `/wait-what` (khi bài không vào) + `/wizard` (bước cài đặt chỉ người làm được)

## Điểm xuất phát thường gặp

Thư mục học chỉ cài mỗi `teach` (trong `skills-lock.json` chỉ có một dòng `teach`), chưa có `AGENTS.md`. Hệ quả:

- `teach` có `disable-model-invocation: true`, nên chỉ chạy khi bạn gõ `/teach`. Các skill hỗ trợ cũng không tự chạy giữa buổi học.
- `teach` không tham chiếu skill nào khác. Mọi liên kết giữa chúng phải do bạn dặn.

Cách dặn bền nhất là một khối trong `AGENTS.md` ở gốc thư mục học: agent đọc nó mỗi phiên, và nó mô tả khi nào làm gì mà không cần bạn nhớ gõ lệnh.

## Các bước

### 1. Đưa skill vào thư mục học

Cài thêm `research`, `grilling`, `domain-modeling`, `wait-what`, `wizard` từ cùng nguồn `mattpocock/skills` với `teach`, để agent đọc được `SKILL.md` gốc thay vì chỉ dựa vào mô tả tóm tắt trong `AGENTS.md`. Cách nhanh là chép nguyên thư mục skill từ `.agents/skills/<tên>/` ở gốc repo này (kèm các file nó liên kết, như `GLOSSARY-FORMAT.md`, `template.sh`) vào cả `.agents/skills/` và `.claude/skills/` của thư mục học. Cách này không cập nhật `skills-lock.json`, nên bản chép có thể lệch bản mới trên GitHub; muốn lock đúng thì cài bằng CLI. Nếu chưa muốn cài, vẫn dùng được: khối `AGENTS.md` dưới đây tự đủ để agent làm đúng ý, chỉ kém chi tiết hơn bản gốc.

### 2. Thêm khối vào `AGENTS.md`

```md
## Skill chủ đạo: `teach`

Thư mục này là workspace của `/teach`. `teach` quyết định cách dạy: cấu trúc workspace, lesson, reference,
learning record, vùng phát triển gần, quy tắc quiz, trích nguồn. Mọi buổi học đi theo `teach`.

Các skill bên dưới chỉ hỗ trợ một khâu trong buổi học. Chúng không đổi cấu trúc, định dạng hay triết lý của `teach`.
Nếu hai bên khác nhau thì `teach` thắng.

## Skill phụ trợ (khi nào dùng)

Nếu có file `.agents/skills/<tên>/SKILL.md` thì đọc nó và làm theo; nếu không thì làm theo phần tóm tắt ở đây.

- **Mission mơ hồ hoặc muốn đổi** (`MISSION.md` trống, hoặc tôi nói mục tiêu đã khác): dùng cách của `grilling`.
  Hỏi theo vòng; mỗi vòng hỏi hết các câu đã đủ điều kiện hỏi, đánh số, kèm đáp án bạn đề xuất,
  sao cho "đồng ý" là chấp nhận đề xuất. Xong khi không còn nhánh nào chưa hỏi.
  Chỉ sửa `MISSION.md` sau khi tôi xác nhận, và ghi một learning record.
- **Cần kiến thức mà `RESOURCES.md` chưa phủ**: dùng cách của `research`. Chạy một background agent với context mới,
  đọc primary source (tài liệu chính thức, source code, spec), không đọc bài viết thứ cấp.
  Mỗi claim kèm nguồn. Kết quả vào `RESOURCES.md` theo `RESOURCES-FORMAT.md`; đừng dạy từ trí nhớ của bạn.
- **Tôi dùng một thuật ngữ mới, mơ hồ hoặc dùng sai**: dùng cách của `domain-modeling`.
  Chỉ ra xung đột với `GLOSSARY.md`, đề xuất thuật ngữ chuẩn, đưa tình huống biên để tôi tự phân biệt.
  Khi một thuật ngữ được chốt thì ghi ngay vào `GLOSSARY.md` theo `GLOSSARY-FORMAT.md` của `teach`.
  Glossary chỉ chứa định nghĩa, không chứa hướng dẫn cấu hình hay quyết định triển khai.
  Bỏ qua phần ADR.
- **Tôi nói "không hiểu", "nói lại đi"**: dùng cách của `wait-what`. Cho một câu bối cảnh, rồi giải thích lại
  bằng câu ngắn, mỗi câu một ý, dùng đúng thuật ngữ trong `GLOSSARY.md`. Không thêm khái niệm mới trong lần nói lại.
- **Bước cài đặt chỉ tôi làm được** (tạo tài khoản, cài engine, mở dashboard, dựng cụm thật): dùng cách của `wizard`.
  Liệt kê các stage theo thứ tự cho tôi xác nhận, rồi sinh script bash dẫn từng bước, chạy được trong WSL.
  Đừng dùng cho việc bạn tự làm được.

## Độ dài và độ sâu của lesson

- Theo `teach`: mỗi bài có một chiến thắng cụ thể, nằm trong vùng phát triển gần, vừa với trí nhớ làm việc của tôi.
- Ngắn không có nghĩa là mỏng. Một bài đủ phải có:
  1. kiến thức tối thiểu để có kỹ năng đó, có trích nguồn;
  2. thực hành có phản hồi tức thì (code hoặc cấu hình chạy được, quiz, thí nghiệm), không chỉ đọc;
  3. một tình huống dễ sai cho thấy cấu hình hay cách làm nào xử lý được vấn đề nào (nếu `NOTES.md` ghi tôi thích kiểu này).
- Nếu bài chứa quá nhiều khái niệm mới: tách thành hai bài, mỗi bài vẫn đủ các phần trên. Không bỏ phần thực hành để giữ bài ngắn.
```

Chỉnh các dòng trong khối cho đúng ngôn ngữ và sở thích của bạn. Phần sở thích học (tiếng Việt, giữ thuật ngữ gốc, thích usecase "oái oăm") vẫn ở `NOTES.md` như `teach` quy định; `AGENTS.md` chỉ trỏ tới nó, không chép lại.

### 3. Mỗi buổi học

```text
/teach <chủ đề của buổi hôm nay>
```

Không cần gọi từng skill hỗ trợ: agent tự áp dụng theo `AGENTS.md` khi gặp đúng tín hiệu (mission mơ hồ, thiếu nguồn, thuật ngữ mới, bạn nói không hiểu, bước cài đặt).

## Lưu ý

- **`wait-what` viết cho tiếng Anh.** Skill gốc yêu cầu ASD-STE100 (Simplified Technical English). Nếu bạn học bằng tiếng Việt, khối trên đã đổi thành "câu ngắn, mỗi câu một ý". Đây là chỉnh có chủ ý, không phải đúng nguyên văn.
- **Đừng để `domain-modeling` ghi đè luật của `teach`.** Trong workspace học, định dạng glossary của `teach` (`GLOSSARY-FORMAT.md`) thắng. Nếu `NOTES.md` có quy ước như "chỉ thêm thuật ngữ khi người học dùng đúng trong quiz/bài tập", quy ước đó vẫn giữ: không nhồi cả glossary của chủ đề vào một lần.
- **Không biến lesson thành báo cáo `research`.** `research` ra một file Markdown dài; `teach` yêu cầu lesson ngắn, vừa working memory. Kết quả `research` chỉ là nguyên liệu cho `RESOURCES.md`, lesson chỉ trích phần đủ cho một kỹ năng.
- **Cân nhắc kỹ trước khi dựng wizard.** Chỉ đáng khi bước cài đặt dài, nhiều chỗ nhập, lặp lại được. Một lệnh `docker run` thì chỉ cần để lesson hướng dẫn.
- **Đừng thêm skill vào chỉ vì nó có sẵn.** `to-spec`, `to-tickets`, `tdd`, `implement` thuộc flow dựng phần mềm, không giúp học.
- **BMAD không có skill tương đương `teach`.** Nếu cần thay thế từng mảnh, phần gần nhất là `bmad-deep-recon` (nghiên cứu, thay cho `research`) và `bmad-advanced-elicitation` (có phương pháp socratic, nhưng để phản biện sản phẩm của agent chứ không để dạy). Không có gì thay cho vòng lesson, learning record, reference. Xem [so sánh Matt Pocock với BMAD](../../docs/case-study-matt-pocock-voi-bmad.md).

## Thực tế đã gặp

### 2026-11-26: Gắn năm skill hỗ trợ vào hai thư mục học (Kubernetes + Argo CD, Kafka)

**Phiên bản skill:** `teach` bản 2026-10-31 (commit `4ae2317` của `mattpocock/skills`); năm skill hỗ trợ chép từ cùng bản trong repo này.

- **Bối cảnh:** hai thư mục học riêng, mỗi thư mục một chủ đề, chỉ cài `teach`, chưa có `AGENTS.md`. Muốn các skill còn lại hỗ trợ việc học mà không phải nhớ gõ từng lệnh.
- **Đã làm:** viết `AGENTS.md` gắn từng skill với một tín hiệu (mission mơ hồ, thiếu nguồn, thuật ngữ mới, "không hiểu", bước chỉ người làm được), kèm `CLAUDE.md` một dòng `@AGENTS.md`. Chép `grilling`, `research`, `domain-modeling`, `wait-what`, `wizard` vào cả `.agents/skills/` và `.claude/skills/`, rồi `diff` từng thư mục với bản gốc để chắc không lệch. Đổi `wait-what` từ tiếng Anh đơn giản (ASD-STE100) sang "câu ngắn, mỗi câu một ý" vì học bằng tiếng Việt. Sau đó người học tự sửa `AGENTS.md` của thư mục Kafka, thêm hai phần mới: **"Skill chủ đạo: `teach`"** (skill phụ chỉ hỗ trợ một khâu, hai bên khác nhau thì `teach` thắng) và **"Độ dài và độ sâu của lesson"** (ngắn không có nghĩa là mỏng: mỗi bài phải có kiến thức tối thiểu kèm nguồn, thực hành có phản hồi tức thì, và ít nhất một usecase "oái oăm").
- **Kết quả:** cài và commit được; bản chép khớp bản gốc. **Chưa quan sát** agent tự gọi đúng skill theo `AGENTS.md` trong một buổi học thật, nên chưa biết các tín hiệu có kích hoạt đủ hay quá nhiều. Hai điểm lệch nhỏ: `skills-lock.json` của thư mục học không ghi năm skill chép tay; và `README` của thư mục học ghi đường dẫn nguồn skill tuyệt đối, bị lỗi thời khi repo này đổi cấu trúc (mã nguồn chuyển lên gốc).
- **Bài học:**
  - Bản `AGENTS.md` đầu tiên liệt kê skill phụ mà không nói skill nào là chủ đạo. Người học phải tự thêm quy tắc "`teach` thắng" và yêu cầu về độ sâu bài. Hai phần này đã được đưa vào khối mẫu ở mục Các bước (bước 2).
  - Cần `CLAUDE.md` import `@AGENTS.md`, vì Claude Code không đọc `AGENTS.md`.
  - Ghi nguồn chép skill bằng tên skill và commit, không bằng đường dẫn tuyệt đối; đường dẫn đổi là README sai.
  - Việc cần làm tiếp: chạy một buổi học thật, ghi lại skill nào được gọi, lúc nào, rồi cập nhật mục này.
