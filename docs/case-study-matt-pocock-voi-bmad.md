# Dùng 14 case study của bộ Matt Pocock với BMAD

Đối chiếu từng [case study của bộ Matt Pocock](../matt-pocock/case-studies/README.md) với BMAD 6.12.4: BMAD có làm được không, làm thế nào, và chỗ nào vẫn nên giữ skill của Matt Pocock. Bối cảnh là Agile Scrum, vai Techlead, Kiro cho công việc (xem [so sánh](./so-sanh-voi-matt-pocock.md)).

Như tài liệu so sánh, phần này **dựa trên mã nguồn, chưa chạy thử**.

## Tóm tắt

Mức độ:

- **Thay được**: BMAD có skill làm đủ việc đó.
- **Một phần**: BMAD làm được một phần; phần còn lại giữ skill Matt hoặc làm tay.
- **Không có**: BMAD không có skill phù hợp.

| # | Tình huống | Mức | Dùng BMAD | Vẫn giữ của Matt | Hợp vai Techlead mới |
|---|---|---|---|---|---|
| [01](#01-nhận-dự-án-không-có-tài-liệu) | Nhận dự án không có tài liệu | Một phần | `bmad-project-context` → `bmad-architecture` (brownfield) | `/domain-modeling`, `/to-questionnaire` | ✔ |
| [02](#02-xây-sản-phẩm-mới-từ-ý-tưởng) | Xây sản phẩm mới từ ý tưởng | **Thay được, mạnh hơn** | Đủ flow plan: forge-idea → brief/PRFAQ → PRD → UX → architecture → epic/story → readiness | Hàng rào repo (`/setup-pre-commit`) | |
| [03](#03-qa-trả-về-loạt-bug) | QA trả về loạt bug | Một phần | `bmad-build` từng bug; `bmad-correct-course` cho bug thật ra là yêu cầu mới | `/triage` | ✔ |
| [04](#04-bug-chập-chờn) | Bug chập chờn, chậm | Không có | — | `/diagnosing-bugs` | |
| [05](#05-refactor-module-cũ) | Refactor module cũ | Một phần | `bmad-architecture` (lát cắt module) → `bmad-spec` → `bmad-build` | `/improve-codebase-architecture`, `/codebase-design` | |
| [06](#06-change-request-mơ-hồ) | Change request mơ hồ, hỏi customer/BA | **Thay được** | `bmad-spec` (câu hỏi mở) → hỏi → `bmad-spec` cập nhật → `bmad-forge-idea` nếu còn tranh cãi | `/to-questionnaire` (tuỳ chọn) | ✔✔ |
| [07](#07-chọn-thư-viện-công-nghệ) | Chọn thư viện, công nghệ, API | **Thay được** | `bmad-deep-recon` (dạng *select*) → `bmad-architecture` ghi `AD-n` | `/prototype` khi phải chạy thử | ✔ |
| [08](#08-nâng-cấp-lớn) | Nâng cấp lớn nhiều phiên | Một phần | `bmad-architecture` → `bmad-spec` → stories → `bmad-build` | `/wayfinder` khi còn mù mờ, `/wizard` cho cutover | ✔ |
| [09](#09-tự-review-trước-mr) | Tự review trước MR | **Thay được** | `bmad-code-review` hoặc `bmad-review`; `bmad-walkthrough` cho người review | `/pr` (mô tả MR) | ✔ |
| [10](#10-bàn-giao-việc) | Bàn giao việc | Một phần | Memlog và trạng thái spec tự cho phép làm tiếp ở phiên khác | `/handoff` cho việc ngoài skill BMAD | |
| [11](#11-domain-lạ) | Vào dự án có domain lạ | Một phần | `bmad-deep-recon` loại *domain* | `/teach`, `/domain-modeling` | ✔✔ |
| [12](#12-agent-lặp-lại-lỗi) | Agent lặp lại cùng một lỗi | **Thay được** | `bmad-project-context` ý định *record* và *audit* | — | ✔ |
| [13](#13-việc-định-kỳ) | Việc định kỳ của bản thân | Không có | — | `/loop-me` | |
| [14](#14-viết-bài-nội-bộ) | Viết bài, tài liệu nội bộ | Một phần | `bmad-review` lens `structure`, `prose` để soát bài | `/writing-fragments`, `/writing-shape`, `/writing-beats` | |

**Nhận xét chung:**

- BMAD **mạnh hơn** ở phía requirement và kế hoạch: 02, 06, 07. Đây cũng là phần việc chính của vai Techlead mới.
- BMAD **thiếu** ở phía sửa lỗi và giữ codebase khoẻ: 04, 05, và một phần 03. Các skill này của Matt không có bản thay thế.
- Matt có vài skill BMAD không có tương đương: `/triage`, `/diagnosing-bugs`, `/wayfinder`, `/teach`, `/loop-me`, `/handoff`, `/wizard`, `/pr`, `/domain-modeling`.

---

## 01. Nhận dự án không có tài liệu

**Mức: Một phần.**

1. **`bmad-project-context`** (ý định *setup*, hoặc *adopt* nếu repo đã có `CLAUDE.md`/`AGENTS.md`): quét repo bằng subagent, kiểm chứng từng lệnh build/test, chỉ hỏi bạn những gì quét không ra (quy định, vùng cấm sửa, lỗi agent hay mắc). Kết quả là khối chỉ dẫn trong `AGENTS.md`. Kiro đọc `AGENTS.md` như steering luôn nạp.
2. **`bmad-architecture`** trên code có sẵn: skill được dặn "đọc code để xác nhận quy ước đang có, không bịa quy ước mới". Chọn Fast path để ra nhanh một spine ghi các bất biến của hệ thống (`AD-n` gắn `[ADOPTED]`).

   ```text
   /bmad-architecture Dựng spine cho codebase hiện có này, chỉ ghi lại quy ước đang dùng. Fast path.
   ```

3. Giữ **`/domain-modeling`** của Matt để dựng `GLOSSARY.md` và ADR, và **`/to-questionnaire`** để hỏi người cũ. BMAD không có glossary riêng.

## 02. Xây sản phẩm mới từ ý tưởng

**Mức: Thay được, mạnh hơn.** Đây là việc BMAD được thiết kế để làm.

```text
bmad-forge-idea (hoặc bmad-brainstorming) → bmad-product-brief / bmad-prfaq → bmad-prd
  → bmad-ux (nếu có UI) → bmad-architecture → bmad-create-epics-and-stories
  → bmad-sprint-planning (readiness) → bmad-build từng story
```

- `bmad-architecture` sẽ gợi ý một **starter** phổ biến (kiểm tra phiên bản trên web) cho dự án mới.
- `bmad-project-context` ở chế độ greenfield ghi các lệnh chưa có dưới dạng TODO, kiểm chứng lại khi đã có code.
- **Trên Kiro:** dừng BMAD ở epic/story, rồi giao từng story cho spec của Kiro (`requirements` → `design` → `tasks`) thay vì `bmad-build`.
- Giữ hàng rào repo của Matt (`/setup-pre-commit`, `/git-guardrails-claude-code` chỉ dùng được trên Claude Code).

## 03. QA trả về loạt bug

**Mức: Một phần.** BMAD không có skill triage.

1. Phân loại bug trên tracker của team (hoặc dùng `/triage` của Matt với tracker local).
2. Bug rõ ràng: **`bmad-build`**, đưa mô tả của QA làm ý định. Bước 1 của skill tự tách nếu một báo cáo chứa nhiều bug độc lập; bug nhỏ đi đường oneshot.

   ```text
   /bmad-build Bug QA-04: lọc đơn theo "Chờ duyệt" ra cả đơn đã huỷ. Bước tái hiện: ...
   ```

3. Bug thật ra là **yêu cầu mới** hoặc đổi phạm vi: **`bmad-correct-course`** để đánh giá ảnh hưởng lên PRD, story, kiến trúc trước khi nhận vào sprint.
4. Hết epic: **`bmad-retrospective`** đối chiếu bằng chứng với AC, ra action item. Khác `/retro` của Matt: retro của BMAD nhìn vào kết quả của epic, không nhìn vào môi trường agent (việc đó xem case 12).

## 04. Bug chập chờn

**Mức: Không có.** `bmad-build` sẽ lập spec rồi sửa, nhưng không có kỷ luật "dựng vòng phản hồi trước, chưa được đoán nguyên nhân". Dùng **`/diagnosing-bugs`** của Matt. Trên Kiro có thể ghép với Bugfix Spec (xem `study\research\kiro-skills`).

## 05. Refactor module cũ

**Mức: Một phần.**

- BMAD làm được phần **kế hoạch**: `bmad-architecture` cho lát cắt module (skill hỗ trợ "the slice a feature touches"), rồi `bmad-spec` → "break this into stories" → `bmad-build`. Giữ quy tắc của Matt: story đầu tiên viết test khoá hành vi hiện tại.
- BMAD **thiếu** phần tìm cơ hội (deepening opportunity) và "thiết kế interface hai lần" bằng nhiều subagent. Dùng `/improve-codebase-architecture` và `/codebase-design` của Matt.

## 06. Change request mơ hồ

**Mức: Thay được.** Đây là tình huống sát nhất với vai Techlead mới.

1. **`bmad-spec`** ở chế độ *express*: chưng cất change request thành `SPEC.md`. Mọi chỗ thiếu thành **`open_questions[]`**. Skill được dặn "đánh dấu, không bao giờ tự bịa câu trả lời". Nó cũng tự nêu các hàm ý của domain mà đầu vào bỏ sót (ví dụ thanh toán mà không nhắc PCI). Cách này tương đương "đánh dấu PENDING" của Matt.

   ```text
   /bmad-spec Express. Khách hàng muốn "cho phép duyệt đơn theo nhóm". Biên bản họp ở docs/cr/cr-12.md.
   ```

2. **Soạn câu hỏi gửi customer/BA**: BMAD không có skill riêng. Nhờ agent "chuyển các open question thành bảng câu hỏi cho BA phía khách hàng, rành nghiệp vụ, không rành kỹ thuật", hoặc dùng `/to-questionnaire` của Matt nếu đã cài.
3. **Có câu trả lời**: gọi lại `bmad-spec` với **cùng slug**. Spec được cập nhật tại chỗ, giữ nguyên mã `CAP-n`, memlog giữ lịch sử thay đổi.
4. Còn điểm customer và team bất đồng: **`bmad-forge-idea`** ("attack this") hoặc **`bmad-party-mode`** với persona khách hàng, BA, QA để tập dượt trước buổi họp.
5. Chốt xong: "break this into stories" ra `stories.yaml`, đưa vào backlog.

Nếu change request sửa một PRD đã có: dùng `bmad-prd` ý định *update*. Nếu đang giữa sprint: `bmad-correct-course`.

## 07. Chọn thư viện, công nghệ

**Mức: Thay được.**

1. **`bmad-deep-recon`** dạng *select* (menu TS của Mary): so sánh các ứng viên bằng ma trận quyết định và đưa khuyến nghị có trích nguồn.

   ```text
   /bmad-deep-recon Chọn giữa thư viện A, B, C để xuất Excel trên 100 nghìn dòng trong Java:
   streaming, bộ nhớ, giấy phép, mức bảo trì. Chỉ dùng tài liệu chính thức và source code.
   ```

2. **`bmad-architecture`** ghi lựa chọn thành một `AD-n` nếu nó ràng buộc các phần khác. Skill tự kiểm tra phiên bản và độ phù hợp trên web trước khi chốt.
3. Cần chạy thử mới biết: `/prototype` của Matt.

Lưu ý môi trường ngân hàng: chỉ đưa câu hỏi kỹ thuật công khai vào research, không đưa dữ liệu hay yêu cầu của khách hàng. `bmad-deep-recon` cũng có cách soạn sẵn prompt để bạn tự chạy ở công cụ được phép.

## 08. Nâng cấp lớn

**Mức: Một phần.**

- Đã rõ hướng: `bmad-architecture` (spine cho việc chuyển đổi) → `bmad-spec` → stories → `bmad-sprint-planning` → `bmad-build` từng story. Memlog và trạng thái spec giúp nối nhiều phiên. Đổi hướng giữa chừng: `bmad-correct-course`.
- Còn mù mờ, nhiều quyết định phụ thuộc nhau: `/wayfinder` của Matt phù hợp hơn.
- Bước cutover người phải làm tay: `/wizard` của Matt.
- `bmad-build` chỉ commit cục bộ, không push, khớp với nhóm không cho agent push.

## 09. Tự review trước MR

**Mức: Thay được.**

- Code làm bằng `bmad-build`: review 3 lớp (Blind Hunter, Edge Case Hunter, Verification Gap) **đã có sẵn** trong bước 4.
- Code làm cách khác: **`bmad-code-review`**, hoặc **`bmad-review`** với lens tuỳ chọn (`adversarial`, `edge-case-hunter`, `verification-gap`).
- Muốn có trục **Standards** như `/code-review` của Matt: đặt `review_guidance` hoặc `style_guide` của `bmad-review` trỏ tới `file:CODING_STANDARDS.md` (qua `bmad-customize`).
- **`bmad-walkthrough`** soạn sẵn đường đi cho người review: để làm gì, chỗ nào cần soi, test thế nào.
- Mô tả MR có bảng AC → test case → kết quả: BMAD không có skill riêng; dùng `/pr` của Matt hoặc nhờ agent viết theo mẫu.

## 10. Bàn giao việc

**Mức: Một phần.**

- **Trong các skill BMAD**, bàn giao gần như tự động: memlog cho phép tiếp tục brief, PRD, spec, architecture ở phiên mới; spec của `bmad-build` có trạng thái (`draft`, `ready-for-dev`, `in-progress`, `in-review`), và lựa chọn "Approve and stop" để phiên khác làm tiếp. Các file nằm trong `_bmad-output/`, commit lên là đồng nghiệp đọc được.
- **Việc ngoài skill BMAD** (một phiên chat điều tra, một việc dở không có spec): dùng `/handoff` của Matt.

## 11. Domain lạ

**Mức: Một phần.** Hợp với việc chuyển sang ngân hàng.

1. **`bmad-deep-recon`** loại *domain* (menu DR của Mary): tổng hợp nghiệp vụ, thuật ngữ, quy định của ngành, có trích nguồn. Chỉ hỏi về kiến thức công khai.
2. **`/teach`** của Matt để học theo từng buổi trong thư mục riêng. BMAD không có skill dạy học.
3. **`/domain-modeling`** của Matt để đưa thuật ngữ đã học vào `GLOSSARY.md` của repo.
4. Khi viết spec, `bmad-spec` tự nêu các hàm ý domain bị bỏ sót, dùng làm danh sách kiểm tra.

## 12. Agent lặp lại lỗi

**Mức: Thay được.** **`bmad-project-context`** có cùng triết lý với `/retro` của Matt:

- Ý định **`record`**: ghi một lỗi agent vừa mắc. Lỗi một lần thì ghi chú; lỗi lặp lại hoặc tốn kém thì thành một dòng pitfall. **Nếu máy bắt được thì đề xuất hook, lint hoặc CI check thay vì viết thành chữ.**
- Ý định **`audit`**: rà lại khối chỉ dẫn, bỏ dòng hết tác dụng, kiểm chứng lại từng lệnh.

```text
/bmad-project-context record: agent hai lần dùng LocalDateTime.now() thay vì Clock của hệ thống.
```

Kết quả nằm trong `AGENTS.md`, nên Kiro, Claude Code và Antigravity đều đọc được.

## 13. Việc định kỳ

**Mức: Không có.** `bmad-build-auto` là vòng lặp code, không phải thiết kế quy trình cá nhân. Dùng `/loop-me` của Matt.

## 14. Viết bài nội bộ

**Mức: Một phần.**

- Tìm ý: `bmad-brainstorming` (tư thế Facilitator để agent không viết thay).
- Soát bản nháp: **`bmad-review`** với lens `structure` (bố cục) và `prose` (câu chữ). Hai lens này giữ nguyên nội dung, chỉ góp ý cách trình bày.
- Dựng bài có lập luận chặt: giữ `/writing-fragments`, `/writing-shape`, `/writing-beats` của Matt.

---

## Tình huống chỉ BMAD có (chưa có trong bộ Matt)

Các tình huống này nên thành case study riêng của BMAD khi chạy thật:

| Tình huống | Skill |
|---|---|
| Đánh giá chéo ý tưởng trước khi viết PRD | [case study 01](../bmad-method/case-studies/01-danh-gia-cheo-y-tuong-bang-party-mode.md) |
| Thẩm định BRD/PRD do BA hoặc khách hàng gửi | `bmad-prd` ý định *validate* (báo cáo HTML), `bmad-review` lens `verification-gap` |
| Cổng Definition of Ready trước Sprint Planning | `bmad-sprint-planning` ý định *readiness* |
| Thay đổi phạm vi giữa sprint | `bmad-correct-course` |
| Nghiệm thu một epic dựa trên bằng chứng | `bmad-retrospective` |
