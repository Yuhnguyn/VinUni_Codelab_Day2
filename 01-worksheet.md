# Lab 02 — Worksheet: AI Product Scoping (Vin Smart Future)

---

## 🏛️ 1. Bối cảnh thực tế: Vin Smart Future (Vingroup)

**Vingroup** — Tập đoàn tư nhân lớn nhất Việt Nam — vừa sáp nhập toàn bộ các phòng ban công nghệ thuộc các công ty thành viên thành một đơn vị công nghệ thống nhất mang tên **Vin Smart Future**. 

Nhiệm vụ của **Vin Smart Future** là xây dựng các giải pháp AI, số hóa, và tự động hóa cốt lõi để nâng cao hiệu suất vận hành và trải nghiệm khách hàng xuyên suốt các công ty thành viên:
* 🚗 **VinFast:** Hệ thống xe điện thông minh (EV), trợ lý AI ảo trong xe, dự đoán bảo trì pin, và quản lý chuỗi cung ứng sản xuất.
* 🚕 **Xanh SM (GSM):** Vận hành đội xe taxi/xe máy điện thông minh, điều vận thông minh (Smart Dispatching), tối ưu hóa lộ trình di chuyển.
* 🏢 **Vinhomes:** Quản lý đô thị thông minh (Smart Cities), trợ lý cư dân thông minh, tối ưu hóa mức tiêu thụ năng lượng.
* 🏥 **Vinmec:** Y tế thông minh, chẩn đoán hình ảnh bằng AI, tối ưu hóa quản lý hồ sơ bệnh án.
* 🎢 **Vinpearl / VinWonders:** Trải nghiệm du lịch số hóa, quản lý phòng và luồng khách thông minh tại các khu vui chơi.

Trong buổi Lab hôm nay, nhóm của bạn sẽ đóng vai trò là **AI Product Engineer** tại **Vin Smart Future**, tiến hành tìm kiếm, scoping, phân tích độ khả thi, thiết lập ranh giới vận hành, và xây dựng một **bản mẫu kỹ thuật (prompt prototype)** cho một bài toán cụ thể thuộc một trong những mảng kinh doanh trên.

---

## 📊 2. Cơ cấu tính điểm bài lab

### 👥 Điểm nhóm (60 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **G1. Workflow Mapping** | 20 | Problem Deep-Dive | Vẽ chi tiết quy trình hiện tại: các bước, handoff, thời gian, bottleneck |
| **G2. Problem Statement** | 20 | Problem Deep-Dive | Problem Statement 6-field bám sát thực tế, metric có số và ranh giới rõ ràng |
| **G3. AI Fit & Future Flow** | 10 | Problem Deep-Dive | So sánh Rule vs LLM vs Agent, future flow có bước AI, ranh giới và Fallback |
| **G4. Decision Quality** | 10 | Problem Deep-Dive | Quyết định Go/Not Yet/No-Go trung thực và có chứng cứ rõ ràng |

### 👤 Điểm cá nhân (40 điểm)

| Gate | Điểm | Deliverable | Tiêu chí chấm |
|---|---:|---|---|
| **I1. Scan & Cards** | 15 | Quick Cards | Liệt kê 5 problems sử dụng 3 lenses, hoàn thiện 3 quick cards chất lượng |
| **I2. Prototyping** | 10 | 02-lab/ | Chạy thử nghiệm programmatic prompt prototype thành công |
| **I3. AI Log & Reflection** | 15 | 03-ai-log.md | Phản ánh trung thực về việc dùng AI làm thought-partner (giúp gì, sai gì, sửa gì) |

---

# 🚀 Phase 0 — worked Example: Xanh SM Intelligent Dispatcher (15 min)

*Giảng viên walk-through ví dụ thực tế từ Vin Smart Future để bạn hiểu rõ cách scoping một bài toán AI.*
Đọc chi tiết worked example tại file [02-deliverable-example.md](02-deliverable-example.md).

---

# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Pain từ người khác | Điều phối viên phải tự nghe lại ghi âm + đọc ghi chú của tài xế cho từng cuốc bị huỷ để tìm ra pattern lỗi hệ thống (định vị sai, kẹt xe, khách bom hàng...), không có tổng hợp tự động theo tuần. |
| 2 | VinFast | Tốn thời gian | Kỹ thuật viên trạm dịch vụ đọc thủ công hàng loạt log lỗi pin/hệ truyền động gửi về từ xe để phân loại mức độ nghiêm trọng trước khi mở phiếu bảo hành. |
| 3 | Vinhomes | AI có thể tốt hơn | Chatbot CSKH trên App Vinhomes Resident trả lời rập khuôn, không phân biệt được mức độ khẩn cấp giữa phản ánh "mất nước toàn toà" và "bóng đèn hành lang cháy". |
| 4 | Vinmec | Pain từ người khác | Bác sĩ phàn nàn mất 20–30 phút/bệnh nhân để tự tay soạn tóm tắt hồ sơ xuất viện từ bệnh án điện tử và kết quả xét nghiệm. |
| 5 | VinUni (giáo dục) | Lặp lại | Trợ giảng (TA) phải tự đọc log autograder + code từng sinh viên để giải thích lại lý do fail, vì log chỉ in `[PASS]/[FAIL]` một dòng ngắn, không đủ tính sư phạm để sinh viên tự hiểu và tự sửa. |

> Bài #5 xuất phát từ quan sát thực tế khi tôi đọc chính file `autograder/autograder.py` của repo này: log chấm điểm chỉ in kết quả kỹ thuật (VD: `"[FAIL] SYSTEM_PROMPT is missing core safety guidelines"`) mà không giải thích *vì sao* hay *nên sửa hướng nào* — nên rất nhiều câu hỏi lặp lại dồn về cho TA.

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                        │
│                                                               │
│ Bài toán (1 câu): TA phải tự đọc log autograder + code từng   │
│ sinh viên để giải thích lại lý do fail vì log quá kỹ thuật.   │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes    │
│                     [ ] Vinmec   [x] Khác: VinUni (Giáo dục)  │
│                                                               │
│ Ai đang đau (Actor)? Trợ giảng/TA (quá tải trả lời lặp lại),  │
│ Sinh viên (chờ lâu, không tự hiểu lỗi để sửa)                 │
│                                                               │
│ Workflow thủ công hiện tại (5 bước):                          │
│   1. SV push bài lên GitHub Classroom ──> 2. Autograder chạy │
│   `--check-code-*` in `[PASS]/[FAIL]` 1 dòng ──> 3. SV không │
│   hiểu, nhắn hỏi TA trên nhóm chat ──> 4. TA đọc log + đọc    │
│   code SV để tìm nguyên nhân ──> 5. TA gõ tay câu trả lời giải│
│   thích + gợi ý hướng sửa                                     │
│                                                               │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3-4 (⏱ ~5-8 phút/câu hỏi,│
│ lặp lại hàng chục lần cùng 1 lỗi phổ biến mỗi buổi)           │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 4 (đọc log + code, │
│ tự động soạn giải thích sư phạm + gợi ý hướng, KHÔNG sửa code)│
│                                                               │
│ Đo thành công bằng gì (Metric có số)?                          │
│   Giảm số câu hỏi lặp lại TA phải trả lời tay từ ~30 ──> dưới │
│   5 câu/buổi lab; 90% SV tự hiểu lỗi mà không cần hỏi thêm.   │
│                                                               │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent   │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                        │
│                                                               │
│ Bài toán (1 câu): Chatbot CSKH Vinhomes Resident trả lời rập  │
│ khuôn, không phân biệt được phản ánh khẩn cấp và không khẩn.  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes    │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________    │
│                                                               │
│ Ai đang đau (Actor)? Cư dân (chờ phản hồi lâu), Ban quản lý   │
│ toà nhà (bị ngập đơn phản ánh không phân loại)                │
│                                                               │
│ Workflow thủ công hiện tại (4 bước):                          │
│   1. Cư dân gửi phản ánh trên App ──> 2. Nhân viên CSKH đọc   │
│   thủ công ──> 3. Phân loại + chuyển đúng ban quản lý ──>     │
│   4. Ban quản lý xử lý                                        │
│                                                               │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-3 (⏱ ~12 giờ/lượt)    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-3 (tự động phân  │
│ loại mức độ khẩn cấp + route đúng ban quản lý)                │
│                                                               │
│ Đo thành công bằng gì (Metric có số)?                          │
│   Giảm thời gian phân loại + route từ 12 giờ ──> dưới 30 phút.│
│                                                               │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent   │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                        │
│                                                               │
│ Bài toán (1 câu): Bác sĩ Vinmec mất quá nhiều thời gian soạn  │
│ tóm tắt hồ sơ xuất viện thủ công cho mỗi bệnh nhân.           │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes    │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________    │
│                                                               │
│ Ai đang đau (Actor)? Bác sĩ điều trị (quá tải), Bệnh nhân     │
│ (chờ lâu để nhận hồ sơ xuất viện)                             │
│                                                               │
│ Workflow thủ công hiện tại (3 bước):                          │
│   1. Đọc bệnh án điện tử + xét nghiệm ──> 2. Tự tay soạn tóm  │
│   tắt bằng ngôn ngữ dễ hiểu ──> 3. Bác sĩ ký duyệt phát hành  │
│                                                               │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 20-30 phút/bệnh nhân)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 (tự động draft   │
│ tóm tắt từ dữ liệu bệnh án, bác sĩ chỉ cần review & ký duyệt) │
│                                                               │
│ Đo thành công bằng gì (Metric có số)?                          │
│   Giảm thời gian soạn tóm tắt từ 25 phút ──> dưới 5 phút,     │
│   bác sĩ vẫn phải duyệt 100% trước khi phát hành cho bệnh nhân.│
│                                                               │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent   │
└─────────────────────────────────────────────────────────────┘
```

**Quyết định chọn đề tài Deep-Dive:** Nhóm chọn **Card #1 — Trợ lý giải thích lỗi Autograder cho TA/Sinh viên VinUni** vì đây là pain point nhóm *trực tiếp trải nghiệm* trong chính buổi lab này (không phải suy diễn), có input/output rõ ràng (log autograder + code sinh viên → giải thích sư phạm), và ranh giới an toàn dễ kiểm chứng (AI không được sửa bài, không được lộ đáp án). Card #2 (Vinhomes) bị loại vì rủi ro pháp lý/tranh chấp phí quản lý cần rule-based router chắc chắn hơn trước khi đưa AI vào; Card #3 (Vinmec) bị loại vì cần dữ liệu bệnh án chuẩn hoá và thời gian thẩm định y khoa dài hơn phạm vi 1 buổi lab.

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

## 3.1. Current-State Workflow Mapping (25 min)
**Vẽ quy trình hiện tại lên bảng/giấy A3.** Sử dụng các ký hiệu:
* 🔴 **Bottleneck:** Bước gây tắc nghẽn, tốn thời gian, hoặc sai sót nhiều nhất.
* 🔄 **Handoff:** Điểm chuyển giao thông tin giữa người và hệ thống, hoặc giữa các bộ phận.
* Ghi rõ thời gian vận hành trung bình: **Tổng cộng = ~7 phút/câu hỏi** (nhân với hàng chục câu hỏi lặp lại/buổi lab).

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

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Trợ giảng (TA) phụ trách hỗ trợ kỹ thuật trong buổi lab; gián tiếp là sinh viên đang chờ phản hồi. |
| **2. Current Workflow** | `autograder.py` chạy các cờ `--check-code-1..5` và in ra kết quả một dòng dạng `[PASS]`/`[FAIL] <mô tả kỹ thuật ngắn>` (ví dụ: *"SYSTEM_PROMPT is missing core safety guidelines"*). Khi sinh viên không hiểu vì sao fail hoặc phải sửa gì, họ nhắn hỏi trên nhóm chat; TA phải mở lại code của từng sinh viên, tự suy luận nguyên nhân cụ thể rồi gõ tay câu trả lời giải thích + gợi ý hướng sửa. Hoàn toàn thủ công, không có tầng trung gian diễn giải log. |
| **3. Bottleneck** | Bước TA đọc log + code để suy luận nguyên nhân và soạn giải thích sư phạm (3-5 phút/câu hỏi) — bị nhân lên nhiều lần vì phần lớn câu hỏi lặp lại cùng một nhóm lỗi phổ biến, khiến TA không còn thời gian cho các câu hỏi khó/sâu hơn. |
| **4. Business Impact** | Với lớp ~30-40 sinh viên, ước tính ~25-30 câu hỏi lặp lại/buổi lab (mỗi buổi ~3 giờ). TA tốn 1.5-2 giờ chỉ để giải thích lại các lỗi cơ bản đã có sẵn trong log kỹ thuật, làm chậm phản hồi cho sinh viên yếu nhất — vốn là nhóm cần hỗ trợ nhiều nhất nhưng lại chờ lâu nhất trong hàng đợi câu hỏi. |
| **5. Success Metric** | (1) Giảm số câu hỏi lặp lại TA phải trả lời thủ công từ ~30 xuống dưới 5 câu/buổi. (2) ≥ 90% sinh viên tự hiểu được lý do fail và hướng sửa (concept) mà không cần hỏi thêm TA. (3) Thời gian trung bình từ lúc fail đến lúc nhận được giải thích giảm từ vài phút chờ (hàng đợi chat) xuống gần như tức thời. |
| **6. Operational Boundary** | AI **ĐƯỢC PHÉP**: đọc log `[FAIL]` cụ thể + đoạn code liên quan của sinh viên, giải thích khái niệm bị thiếu/sai bằng ngôn ngữ sư phạm dễ hiểu, gợi ý *hướng* sửa (không viết code hoàn chỉnh thay). AI **TUYỆT ĐỐI KHÔNG ĐƯỢC**: tự sửa/viết lại code nộp bài của sinh viên; tiết lộ đáp án mẫu hoặc SYSTEM_PROMPT chuẩn của giảng viên; tự thay đổi hoặc công bố điểm số — điểm số chỉ do `autograder.py` và giảng viên quyết định; phải nêu rõ đây là gợi ý AI, sinh viên/TA có quyền không đồng ý. |

## 3.3. Future-State Flow & AI Fit (25 min)
* **Xác định mức AI Fit (AI-Fit Matrix):** Giải pháp thuộc nhóm nào? [ ] Rule / State-Machine [x] LLM Feature [ ] Agentic Loop.
  * Lý do chọn LLM Feature thay vì Rule/State-Machine: lỗi kỹ thuật rất đa dạng (SYSTEM_PROMPT thiếu keyword, hàm chưa implement, sai cấu trúc dữ liệu...) — viết rule cứng cho từng loại lỗi sẽ phình to và khó bảo trì, trong khi LLM đọc log + code rồi diễn giải ngôn ngữ tự nhiên phù hợp hơn.
  * Lý do không chọn Agentic Loop: input/output cố định theo một vòng duy nhất (nhận log+code → trả về giải thích), không cần AI tự gọi nhiều công cụ hay tự quyết định các bước tiếp theo.
* **Vẽ Future-State Flow:**

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

# 💻 Phase 4 — TECHNICAL PROMPT PROTOTYPE (Nhóm, 30 min)

Để đảm bảo kỹ sư của Vin Smart Future luôn giữ vững năng lực lập trình, nhóm của bạn sẽ tiến hành **lập trình bản mẫu prompt** trực tiếp trên **Gemini 2.5 Flash** bằng Python để stress-test hệ thống.

### Hướng dẫn thực hiện:
> **Lưu ý:** `starter-code/prompt_prototype.py` là bài tập kỹ thuật **chuẩn hoá chung** cho mọi nhóm (kịch bản Xanh SM Dispatcher Co-Pilot xử lý sự cố pin — đã được định sẵn ngay trong comment của starter code và trong autograder), tách biệt với đề tài Deep-Dive nhóm tự chọn ở Phase 3 (Trợ lý giải thích lỗi Autograder). Hai bài toán khác nhau nhưng cùng chung một bài học: **ranh giới an toàn (Operational Boundary) + HITL** là bắt buộc dù AI hỗ trợ ở lĩnh vực nào — điều phối xe điện hay chấm bài lab.

**Trạng thái:** ✅ Đã hoàn thiện `starter-code/prompt_prototype.py` — `SYSTEM_PROMPT` (vai trò, thẻ `[DRAFT_ONLY]`, ngưỡng pin 5%), `evaluate_prompt()` dùng SDK `google-genai`, và 3 `ADVERSARIAL_TESTS` (bypass ngưỡng pin, bỏ thẻ DRAFT_ONLY, prompt injection lộ system prompt/bỏ HITL). Chạy `python3 prompt_prototype.py` với `GEMINI_API_KEY` hợp lệ để xem kết quả kiểm chứng ranh giới.

1. Mở file [starter-code/prompt_prototype.py](starter-code/prompt_prototype.py) bằng VS Code/Cursor.
2. Hoàn thiện các nội dung sau:
   * **System Prompt:** Viết chỉ thị cực kỳ nghiêm ngặt quy định vai trò, nhiệm vụ, định dạng output và **Operational Boundary (Ranh giới cấm)** của mô hình.
   * **Structured Output:** Định nghĩa định dạng JSON output rõ ràng.
   * **Adversarial Test Cases:** Viết ít nhất 3 prompts "tấn công" (Adversarial inputs) cố tình dụ AI vượt ranh giới hoặc đưa ra câu trả lời không được phép để kiểm tra xem ranh giới của bạn có thực sự vững chắc.
3. Chạy file python:
   ```bash
   python3 prompt_prototype.py
   ```
4. Kiểm tra xem các ranh giới an toàn có bị LLM phá vỡ hay không và ghi lại kết quả vào worksheet.

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? (Log `[PASS]/[FAIL]` từ `autograder.py` và code nộp bài của sinh viên là dữ liệu có cấu trúc, sẵn có ngay trong pipeline hiện tại — không cần thu thập thêm).
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)? (AI chỉ *giải thích*, không sửa bài/không đổi điểm; TA vẫn duyệt/kiểm tra trước khi gửi phản hồi chính thức; có fallback "cần TA xem trực tiếp" khi AI không chắc chắn).
3. [ ] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? **Chưa chắc chắn** — cần thống nhất với giảng viên/TA về mức độ AI được phép "gợi ý" tới đâu để không bị xem là làm hộ bài, và cần thử nghiệm trên một lớp nhỏ trước khi áp dụng rộng.

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[ ] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[x] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
> Về mặt kỹ thuật, bài toán khả thi: dữ liệu log + code đã có sẵn, ranh giới an toàn rõ ràng
> (không sửa bài, không lộ đáp án, không tự chấm điểm) và dễ kiểm chứng bằng adversarial
> testing giống như đã thực hành ở Phase 4. Tuy nhiên, nhóm chọn **NOT YET** thay vì GO ngay
> vì hai lý do: (1) chưa có baseline để đo "90% sinh viên tự hiểu lỗi" — cần thử nghiệm thủ
> công (TA dùng AI nháp câu trả lời rồi tự gửi) trong 1-2 buổi lab để đo tỉ lệ sinh viên còn
> phải hỏi lại, trước khi tự động hoá hoàn toàn; (2) cần sự đồng thuận rõ ràng từ giảng viên
> về ranh giới "gợi ý" vs "làm hộ", vì đây là vấn đề học thuật (academic integrity) nhạy cảm
> hơn một quy trình vận hành thông thường. Sau khi có baseline và ranh giới được duyệt chính
> thức, đây là ứng viên tốt để chuyển sang GO ở đợt lab tiếp theo.

---

# 📝 Phase 6 — REFLECTION (Cá nhân)
*Ghi nhận phản ánh của cá nhân bạn về việc phối hợp với AI trong buổi học hôm nay vào file `03-ai-log.md`.*
