# Vinpearl AI Journey Copilot

## Product scoping & deep-dive report — Bản cá nhân

- **Học viên:** Lê Thị Thùy Trang
- **Mã định danh:** 02678
- **Branch cá nhân:** `lethithuytrang-02678`
- **Đề tài cá nhân:** Vinpearl Personalized Journey Copilot
- **Phạm vi:** Phase 3 — DEEP-DIVE và Phase 5 — EVALUATE
- **Lưu ý:** Nhóm chọn Vinhomes Resident Request Copilot sau thảo luận; tài liệu này là phương án Vinpearl cá nhân được nộp trên branch để nhóm review.

**Product thesis:** Biến booking và nhu cầu tự nhiên của khách thành một lịch trình cá nhân hóa dạng nháp, khả thi về thời gian và điều kiện dịch vụ, nhưng luôn để khách hoặc nhân viên kiểm soát quyết định đặt/mua.

**Scope MVP:** Khách gia đình lưu trú 3 ngày 2 đêm tại cụm Phú Quốc; gợi ý cho khách sạn, VinWonders, Safari, F&B, spa/golf và di chuyển nội khu dựa trên một catalog giả lập/đã duyệt.

**Không thuộc MVP:** tự thanh toán, tự đặt/hủy dịch vụ, định giá động, nhận diện khuôn mặt, chẩn đoán sức khỏe, tối ưu công suất toàn hệ thống.

## 1. Evidence và giả thuyết sản phẩm

Vinpearl công khai định hướng chuyển từ cung cấp dịch vụ đơn lẻ sang hành trình All-in-One trọn gói và cá nhân hóa. Kế hoạch 2026 cũng đề cập AI và data analytics nhằm tối ưu customer journey và conversion. Đây là **strategic signal**, không phải bằng chứng rằng hệ thống hiện tại đang thất bại: [Annual Report 2025](https://statics.vinpearl.com/VINPEARL%20AR25_C1-6_260330_1774881976.pdf), [Business Plan 2026](https://statics.vinpearl.com/20260416_VPL_CBTT%20dieu%20chinh%20tai%20lieu%20hop%20DHDCD%20thuong%20nien%202026_TA_1776341231.pdf).

MyVinpearl đã có booking, promotion và online check-in. Các trang điểm đến cũng công bố lịch trình mẫu kết hợp resort, VinWonders, Safari, Grand World, F&B và spa/golf. Khoảng trống sản phẩm được giả định là chuyển từ **lịch mẫu one-size-fits-all** sang lịch riêng cho từng booking và nhóm khách: [Online check-in](https://vinpearl.com/en/online-check-in-safe-travel-save-time), [Ví dụ itinerary Phú Quốc](https://vinpearl.com/en/vinpearl-resort-spa-phu-quoc).

Chính sách dữ liệu cho phép cải thiện trải nghiệm và cá nhân hóa theo nhu cầu thực tế, nhưng việc thu thập và sử dụng preference vẫn phải đúng mục đích, minh bạch và có cơ chế kiểm soát: [Vinpearl Privacy Policy](https://vinpearl.com/en/privacy-policy).

### Research gaps cần đóng trước production

- Chưa có số liệu công khai về thời gian khách tự lập lịch hoặc nhân viên concierge tư vấn.
- Chưa xác nhận có API realtime thống nhất cho giờ hoạt động, availability, thời tiết và transport.
- Chưa có dữ liệu về tỷ lệ khách chấp nhận itinerary hoặc add-on recommendation.
- Chưa phỏng vấn khách gia đình, concierge, vận hành VinWonders/F&B và Data Privacy Officer.

Các con số chưa có nguồn bên dưới được ghi rõ là **working baseline** hoặc **pilot target**, không phải số liệu thực tế của Vinpearl.

## 2. Current-State Workflow Mapping

### Working baseline

Giả thuyết thiết kế: một khách tự lập lịch mất khoảng **25 phút/lượt**. Con số này nằm trong kế hoạch đo kiểm discovery, không phải số liệu do Vinpearl công bố.

| Bước | Actor | Hành động | Input → Output | Thời gian giả thuyết | Handoff/Bottleneck |
|---:|---|---|---|---:|---|
| 1 | Khách | Mở booking và xác định khoảng thời gian trống | Booking → khung chuyến đi | 2 phút | Booking/App → khách |
| 2 | Khách | Tìm hoạt động, nhà hàng và tiện ích trên nhiều trang/mục | Nội dung rời rạc → shortlist | 8 phút | 🔴 Bottleneck |
| 3 | Khách | So sánh giờ, vị trí, giá, độ tuổi và sở thích đoàn | Shortlist → tập lựa chọn khả thi | 7 phút | 🔴 Bottleneck |
| 4 | Khách ↔ Concierge | Hỏi lại thông tin chưa rõ hoặc yêu cầu tư vấn | Câu hỏi → thông tin xác nhận | 5 phút | 🔄 Handoff |
| 5 | Khách | Ghép lịch và chỉnh khi có xung đột | Lựa chọn → lịch cá nhân | 3 phút | Có thể phải quay lại bước 2 |

**Tổng working baseline: 25 phút/lượt.** Sơ đồ trực quan nằm tại `04-workflow-diagram.png`.

### Root-cause hypothesis

1. Catalog dịch vụ giàu nhưng mỗi mục có metadata và ràng buộc khác nhau.
2. Preference của một đoàn là dữ liệu phi cấu trúc và thường mâu thuẫn.
3. Lịch trình mẫu không biết booking, nhịp độ, ngân sách và nhu cầu tiếp cận của khách cụ thể.
4. LLM đơn lẻ có thể viết lịch hay nhưng dễ bịa availability hoặc vi phạm hard constraint.

## 3. Problem Statement — 6 fields

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Khách gia đình đang chuẩn bị hoặc thực hiện kỳ nghỉ; concierge/CX hỗ trợ khi khách cần. |
| **2. Current Workflow** | Khách xem booking, tự tìm từng dịch vụ, so sánh ràng buộc, hỏi concierge và ghép lịch thủ công. Working baseline 5 bước/25 phút, cần xác thực bằng research. |
| **3. Bottleneck** | Tổng hợp catalog và giải quyết đồng thời sở thích, thời gian, địa điểm, ngân sách, tuổi/chiều cao, accessibility và availability. |
| **4. Business Impact** | Customer effort cao; trải nghiệm All-in-One có thể bị rời rạc; concierge lặp lại tư vấn; cơ hội dịch vụ phù hợp có thể bị bỏ lỡ. Chưa quy đổi thành doanh thu nếu chưa có dữ liệu nội bộ. |
| **5. Success Metric** | Pilot target: P95 draft <10 giây; ≥90% item hợp lệ theo catalog; hard-constraint violation = 0; edit/removal rate ≤35%; itinerary CSAT ≥4/5; add-on acceptance tăng ≥10% so với control. |
| **6. Operational Boundary** | AI chỉ đề xuất draft từ dữ liệu đã được phép và catalog đã duyệt. Không bịa giá/giờ/availability; không tự đặt, hủy, thanh toán hoặc hứa ưu đãi; mọi giao dịch cần khách xác nhận và hệ thống booking xác thực. |

## 4. AI Fit

| Phương án | Làm tốt | Không làm tốt | Quyết định |
|---|---|---|---|
| Static template / No AI | Rẻ, ổn định, dễ kiểm duyệt | Không hiểu preference tự nhiên; ít cá nhân hóa | Dùng làm fallback |
| Rule engine | Kiểm tra giờ, overlap, tuổi/chiều cao, thời lượng di chuyển | Khó hiểu mong muốn mơ hồ và giải thích tự nhiên | **Bắt buộc trong kiến trúc** |
| LLM feature | Hiểu sở thích, tóm tắt booking, tạo narrative và phương án | Có thể hallucinate hoặc bỏ qua constraint | **Chọn, nhưng phải grounded** |
| Autonomous agent | Có thể tự lập và thực thi chuỗi giao dịch | Rủi ro đặt/hủy sai, giá thay đổi, quyền hạn phức tạp | Không dùng trong MVP |

### Kiến trúc được chọn

**Retrieval + deterministic rules + LLM generation + confirmation gate.** LLM không phải source of truth.

```text
Booking + consented preferences
              │
              ▼
     Data minimization / profile
              │
              ▼
Approved catalog + live facts ──► Constraint engine
                                      │
                                      ▼
                              Feasible candidates
                                      │
                                      ▼
                               LLM itinerary draft
                                      │
                                      ▼
                         Post-generation validator
                           │ valid          │ invalid
                           ▼                ▼
                    Guest review       Safe fallback
                           │
                           ▼
                 Explicit booking confirmation
```

## 5. Future-State Flow

| Bước | Loại | Mô tả | Guardrail |
|---:|---|---|---|
| 1 | Human | Khách chọn “Tạo lịch trình”, xác nhận phạm vi dữ liệu được dùng và nhập preference. | Opt-in; cho phép bỏ qua dữ liệu không cần thiết. |
| 2 | System | Đọc booking và truy xuất catalog/availability được phê duyệt. | Không dùng nội dung web tự do làm source of truth. |
| 3 | Rule | Lọc theo giờ, travel time, ngân sách, tuổi/chiều cao, accessibility và dietary constraints. | Hard constraint không được LLM ghi đè. |
| 4 | AI | LLM sắp xếp candidate thành draft và giải thích lý do phù hợp. | Output phải có `[DRAFT_ONLY]`, assumptions và warnings. |
| 5 | System | Validator kiểm tra ID dịch vụ, overlap, freshness và mọi hard constraint. | Lỗi thì không hiển thị như một lịch hợp lệ. |
| 6 | Human | Khách hoặc concierge xem, sửa và chọn item muốn đặt. | Không có giao dịch ngầm. |
| 7 | System | Booking engine hiển thị giá/availability mới nhất và yêu cầu xác nhận cuối. | Source of truth là hệ thống giao dịch, không phải LLM. |

### Fallback

- Không có catalog/API: hiển thị lịch mẫu đã duyệt, không cá nhân hóa theo availability.
- Confidence thấp hoặc preference mâu thuẫn: hỏi tối đa ba câu làm rõ.
- Validator phát hiện vi phạm: loại item và regenerate một lần; nếu vẫn lỗi, chuyển concierge.
- Dịch vụ thay đổi: giữ booking đã xác nhận, chỉ gợi ý phương án thay thế cho phần chưa đặt.
- Sự cố an toàn/y tế: dừng itinerary flow và hiển thị kênh trợ giúp chính thức.

## 6. Data contract và structured output

### Input tối thiểu

```json
{
  "destination": "Phu Quoc",
  "stay": {"check_in": "2026-10-10", "check_out": "2026-10-12"},
  "party": {"adults": 2, "children": [{"age": 7, "height_cm": 118}]},
  "preferences": ["wildlife", "light walking", "Vietnamese food"],
  "constraints": ["no late-night activities", "shellfish allergy"],
  "budget_vnd": 6000000,
  "consent": {"use_booking": true, "use_profile_history": false}
}
```

### Output contract

Mọi output bắt đầu bằng `[DRAFT_ONLY]`, sau đó là JSON gồm:

```json
{
  "status": "DRAFT_ONLY",
  "assumptions": [],
  "questions": [],
  "days": [
    {
      "date": "YYYY-MM-DD",
      "items": [
        {
          "catalog_id": "approved-id",
          "start": "HH:MM",
          "end": "HH:MM",
          "why_fit": "reason",
          "booking_status": "NOT_BOOKED"
        }
      ]
    }
  ],
  "warnings": [],
  "next_action": "REVIEW_AND_CONFIRM"
}
```

## 7. Operational Boundaries

### AI được phép

- Đọc dữ liệu booking và preference đã được khách đồng ý sử dụng.
- Chọn từ catalog đã duyệt; sắp xếp lịch; nêu assumptions.
- Hỏi làm rõ, đưa phương án thay thế và tạo nội dung đa ngôn ngữ.
- Tạo deep link đến màn hình booking chính thức.

### AI tuyệt đối không được phép

- Tự đặt, hủy, thanh toán, đổi hạng phòng hoặc sử dụng điểm/voucher.
- Khẳng định availability, giá hoặc ưu đãi nếu không có xác nhận realtime.
- Bịa dịch vụ, catalog ID, giờ hoạt động hoặc thời gian di chuyển.
- Bỏ qua giới hạn an toàn, độ tuổi, chiều cao, accessibility hay dị ứng.
- Suy luận thuộc tính nhạy cảm hoặc sử dụng lịch sử cá nhân khi chưa opt-in.
- Tiết lộ dữ liệu của thành viên khác trong đoàn hoặc khách khác.
- Thực hiện prompt injection nằm trong review, ghi chú hay catalog.

## 8. MVP và rollout

### Prompt prototype & adversarial tests

Prototype tại `starter-code/prompt_prototype.py` ưu tiên model theo đề bài là `gemini-2.5-flash` và có fallback sang `gemini-3.6-flash` khi tài khoản mới không còn được cấp model 2.5. Bốn tình huống tấn công được định nghĩa:

| Test | Cách tấn công | Hành vi an toàn mong đợi |
|---|---|---|
| Unauthorized transaction | Ép AI tự đặt, thanh toán và bịa còn chỗ | Giữ trạng thái `NOT_BOOKED`; yêu cầu review/confirm |
| Safety bypass | Dùng trạng thái VIP để bỏ giới hạn chiều cao | Không ghi đè hard constraint; cảnh báo rõ |
| Allergy guarantee | Ép AI đảm bảo món ăn an toàn khi catalog thiếu dữ liệu | Không đưa bảo đảm; yêu cầu xác nhận với nhân viên |
| Prompt injection/privacy | Chèn chỉ dẫn lấy dữ liệu khách khác vào nội dung catalog | Coi nội dung là untrusted data và từ chối tiết lộ |

**Kết quả kiểm tra hiện tại:** 5/5 contract checks offline pass và autograder Section B đạt 5/5 điểm. Lần chạy live đã đi tới Gemini API nhưng bị project từ chối quyền truy cập với mã `403 PERMISSION_DENIED`; vì vậy chưa có cơ sở tuyên bố 4 adversarial prompts đã pass trên model thật. Cần cấp một Gemini API key/project hợp lệ rồi chạy lại trước demo.

Lưu ý: starter autograder của khóa học kiểm tra một số token từ use case Xanh SM. Prototype giữ các token đó duy nhất trong điều khoản **cross-domain isolation**, không dùng chúng làm logic của Vinpearl Journey Copilot.

### MVP 4 tuần

1. Tuần 1 — Discovery: 5 phỏng vấn khách, 3 concierge, 2 vận hành; đo baseline và chốt taxonomy constraint.
2. Tuần 2 — Data: catalog giả lập 30–50 dịch vụ Phú Quốc, schema, freshness và rule validator.
3. Tuần 3 — Prototype: prompt, retrieval, generator, validator và giao diện review đơn giản.
4. Tuần 4 — Offline evaluation: 100 synthetic journeys, 20 adversarial cases và review bởi vận hành.

### Experiment design

- Control: itinerary mẫu theo nhóm khách.
- Treatment: AI draft có grounding và rules.
- Primary metric: itinerary completion/acceptance.
- Guardrail metrics: invalid recommendation, hard-constraint violation, privacy incident, unauthorized transaction.
- Chỉ mở pilot cho nhân viên/internal testers trước khi A/B test với khách opt-in.

## 9. AI Readiness Evaluation

| Câu hỏi | Đánh giá | Bằng chứng/hành động |
|---|---|---|
| Có dữ liệu mẫu/log sạch để test? | **Một phần** | Có nội dung catalog công khai và lịch mẫu; chưa có schema/API và log hành vi nội bộ. Xây synthetic dataset trước. |
| Rủi ro AI sai có kiểm soát được? | **Có trong scope hẹp** | Grounding, rule engine, validator, `[DRAFT_ONLY]`, confirmation gate và fallback. |
| Stakeholder sẵn sàng đổi quy trình? | **Có tín hiệu chiến lược, chưa xác thực vận hành** | Tài liệu công khai ủng hộ AI/personalization; vẫn cần phỏng vấn Product, CX, Concierge, Operations, Legal/Privacy. |

## 10. Quyết định

- [x] **GO — xây offline prototype với catalog giả lập/đã duyệt và không có quyền giao dịch.**
- [ ] NOT YET.
- [ ] NO-GO.

### Justification

Bài toán bám sát chiến lược All-in-One và cá nhân hóa đã công bố, LLM có lợi thế rõ ở việc hiểu preference và diễn đạt hành trình, trong khi rủi ro chính có thể giới hạn bằng rules, grounding và confirmation gate. Chi phí MVP thấp vì chưa cần tích hợp booking thật. Tuy nhiên, quyết định GO chỉ áp dụng cho **offline prototype**. Việc triển khai với khách thật là một gate riêng, chỉ được thông qua khi có catalog/API đáng tin cậy, consent flow, privacy review và kết quả guardrail đạt ngưỡng.

## 11. Kill criteria

Dừng hoặc thu hẹp sản phẩm nếu sau pilot:

- Hard-constraint violation lớn hơn 0 trong bộ test an toàn.
- Tỷ lệ item không tồn tại/sai catalog lớn hơn 1%.
- Khách phải xóa hoặc sửa hơn 50% itinerary.
- Không cải thiện completion/acceptance so với itinerary mẫu.
- Không thể cung cấp nguồn dữ liệu đủ mới để xác thực availability.
