# 02 — Deep-Dive Report (Lab 02: AI Product Scoping — Vin Smart Future)

> Nội dung Phase 3 (DEEP-DIVE) và Phase 5 (EVALUATE) được chắt lọc từ `01-worksheet.md`.
> Đề tài: **Trợ lý giải thích lỗi Autograder cho TA/Sinh viên VinUni** (chọn từ Quick Card #1
> trong [`01-problem-scan.md`](01-problem-scan.md)).

---

# 🏗️ Phase 3 — DEEP-DIVE

## 3.1. Current-State Workflow Mapping
**Tổng cộng = ~7 phút/câu hỏi** (nhân với hàng chục câu hỏi lặp lại/buổi lab).

```text
┌──────────────┐ 🔄  ┌──────────────┐ 🔄  ┌──────────────┐ 🔄  ┌──────────────┐
│ B1. SV push  │     │ B2. Autograder│    │ B3. SV không │     │ B4. TA đọc   │
│ bài lên GitHub│──▶ │ chạy, in ra  │ ──▶ │ hiểu log, nhắn│──▶ │ log + đọc code│
│ Classroom    │     │ `[PASS]/     │     │ hỏi trên nhóm│     │ SV để tìm    │
│              │     │ [FAIL]` 1 dòng│    │ chat của lớp │     │ nguyên nhân🔴│
│ Ai: Sinh viên│     │ Ai: Hệ thống │     │ Ai: Sinh viên│     │ Ai: TA       │
│ ⏱ tự động    │     │ ⏱ ~10 giây   │     │ ⏱ chờ (chưa  │     │ ⏱ 3-5 phút 🔴│
│              │     │              │     │ đo được)     │     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────┬───────┘
                                                                       │ 🔄
                                                                       ▼
                                                                ┌──────────────┐
                                                                │ B5. TA gõ tay│
                                                                │ câu trả lời  │
                                                                │ giải thích 🔴│
                                                                │ ⏱ 2-3 phút   │
                                                                └──────────────┘
🔴 Bottleneck: Bước 4 & 5 — TA phải tự đọc log kỹ thuật + code từng sinh viên
   rồi gõ tay lời giải thích, dù phần lớn câu hỏi lặp lại cùng vài lỗi phổ biến
   (VD: quên xoá "TODO:", thiếu keyword trong SYSTEM_PROMPT, quên import SDK...).
```

## 3.2. Problem Statement (6-field) & Metrics

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Trợ giảng (TA) phụ trách hỗ trợ kỹ thuật trong buổi lab; gián tiếp là sinh viên đang chờ phản hồi. |
| **2. Current Workflow** | `autograder.py` chạy các cờ `--check-code-1..5` và in ra kết quả một dòng dạng `[PASS]`/`[FAIL] <mô tả kỹ thuật ngắn>` (ví dụ: *"SYSTEM_PROMPT is missing core safety guidelines"*). Khi sinh viên không hiểu vì sao fail hoặc phải sửa gì, họ nhắn hỏi trên nhóm chat; TA phải mở lại code của từng sinh viên, tự suy luận nguyên nhân cụ thể rồi gõ tay câu trả lời giải thích + gợi ý hướng sửa. Hoàn toàn thủ công, không có tầng trung gian diễn giải log. |
| **3. Bottleneck** | Bước TA đọc log + code để suy luận nguyên nhân và soạn giải thích sư phạm (3-5 phút/câu hỏi) — bị nhân lên nhiều lần vì phần lớn câu hỏi lặp lại cùng một nhóm lỗi phổ biến, khiến TA không còn thời gian cho các câu hỏi khó/sâu hơn. |
| **4. Business Impact** | Với lớp ~30-40 sinh viên, ước tính ~25-30 câu hỏi lặp lại/buổi lab (mỗi buổi ~3 giờ). TA tốn 1.5-2 giờ chỉ để giải thích lại các lỗi cơ bản đã có sẵn trong log kỹ thuật, làm chậm phản hồi cho sinh viên yếu nhất — vốn là nhóm cần hỗ trợ nhiều nhất nhưng lại chờ lâu nhất trong hàng đợi câu hỏi. |
| **5. Success Metric** | (1) Giảm số câu hỏi lặp lại TA phải trả lời thủ công từ ~30 xuống dưới 5 câu/buổi. (2) ≥ 90% sinh viên tự hiểu được lý do fail và hướng sửa (concept) mà không cần hỏi thêm TA. (3) Thời gian trung bình từ lúc fail đến lúc nhận được giải thích giảm từ vài phút chờ (hàng đợi chat) xuống gần như tức thời. |
| **6. Operational Boundary** | AI **ĐƯỢC PHÉP**: đọc log `[FAIL]` cụ thể + đoạn code liên quan của sinh viên, giải thích khái niệm bị thiếu/sai bằng ngôn ngữ sư phạm dễ hiểu, gợi ý *hướng* sửa (không viết code hoàn chỉnh thay). AI **TUYỆT ĐỐI KHÔNG ĐƯỢC**: tự sửa/viết lại code nộp bài của sinh viên; tiết lộ đáp án mẫu hoặc SYSTEM_PROMPT chuẩn của giảng viên; tự thay đổi hoặc công bố điểm số — điểm số chỉ do `autograder.py` và giảng viên quyết định; phải nêu rõ đây là gợi ý AI, sinh viên/TA có quyền không đồng ý. |

## 3.3. Future-State Flow & AI Fit
* **AI Fit:** [ ] Rule / State-Machine  [x] **LLM Feature**  [ ] Agentic Loop.
  * Lý do chọn LLM Feature thay vì Rule/State-Machine: lỗi kỹ thuật rất đa dạng (SYSTEM_PROMPT thiếu keyword, hàm chưa implement, sai cấu trúc dữ liệu...) — viết rule cứng cho từng loại lỗi sẽ phình to và khó bảo trì, trong khi LLM đọc log + code rồi diễn giải ngôn ngữ tự nhiên phù hợp hơn.
  * Lý do không chọn Agentic Loop: input/output cố định theo một vòng duy nhất (nhận log+code → trả về giải thích), không cần AI tự gọi nhiều công cụ hay tự quyết định các bước tiếp theo.

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ B1. Autograder│    │ 🔵 B2. AI đọc│     │ 🔵 B3. AI    │     │ 🟢 B4. TA/SV │
│ in [FAIL] +  │ ──▶ │ log lỗi + code│──▶ │ draft giải   │ ──▶ │ xem giải thích│
│ mã lỗi kỹ thuật│    │ liên quan    │     │ thích sư phạm│     │ [AI_HINT], có│
│              │     │              │     │ + gợi ý hướng│     │ thể hỏi thêm │
└──────────────┘     └──────────────┘     └──────┬───────┘     └──────────────┘
                                                  │
                                    (không chắc chắn nguyên nhân,
                                     lỗi ngoài phạm vi check cố định)
                                                  ▼
                                          ↩️ Fallback: AI trả lời "Chưa đủ tự
                                          tin để giải thích — cần TA xem trực
                                          tiếp", KHÔNG được đoán bừa hay tự
                                          sửa bài; TA vẫn là người xử lý cuối.
```

---

# 🏁 Phase 5 — EVALUATE

### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? (Log `[PASS]/[FAIL]` từ `autograder.py` và code nộp bài của sinh viên là dữ liệu có cấu trúc, sẵn có ngay trong pipeline hiện tại — không cần thu thập thêm).
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)? (AI chỉ *giải thích*, không sửa bài/không đổi điểm; TA vẫn duyệt/kiểm tra trước khi gửi phản hồi chính thức; có fallback "cần TA xem trực tiếp" khi AI không chắc chắn).
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? **Chưa chắc chắn** — cần thống nhất với giảng viên/TA về mức độ AI được phép "gợi ý" tới đâu để không bị xem là làm hộ bài, và cần thử nghiệm trên một lớp nhỏ trước khi áp dụng rộng.

### Quyết định cuối cùng:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[x] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification:**
> Về mặt kỹ thuật, bài toán khả thi: dữ liệu log + code đã có sẵn, ranh giới an toàn rõ ràng
> (không sửa bài, không lộ đáp án, không tự chấm điểm) và dễ kiểm chứng bằng adversarial
> testing giống như đã thực hành ở Phase 4. Tuy nhiên, nhóm chọn **NOT YET** thay vì GO ngay
> vì hai lý do: (1) chưa có baseline để đo "90% sinh viên tự hiểu lỗi" — cần thử nghiệm thủ
> công (TA dùng AI nháp câu trả lời rồi tự gửi) trong 1-2 buổi lab để đo tỉ lệ sinh viên còn
> phải hỏi lại, trước khi tự động hoá hoàn toàn; (2) cần sự đồng thuận rõ ràng từ giảng viên
> về ranh giới "gợi ý" vs "làm hộ", vì đây là vấn đề học thuật (academic integrity) nhạy cảm
> hơn một quy trình vận hành thông thường. Sau khi có baseline và ranh giới được duyệt chính
> thức, đây là ứng viên tốt để chuyển sang GO ở đợt lab tiếp theo.
