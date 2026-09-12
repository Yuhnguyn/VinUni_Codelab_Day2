# 01 — Problem Scan (Lab 02: AI Product Scoping — Vin Smart Future)

> Nội dung Phase 1 (SCAN) và Phase 2 (QUICK-ASSESS) được chắt lọc từ `01-worksheet.md`.

---

# 🔍 Phase 1 — SCAN

Quét qua hoạt động vận hành của các công ty thành viên Vingroup bằng **4 Lenses**
(Lặp lại, Tốn thời gian, AI có thể tốt hơn, Pain từ người khác).

### 📝 List bài toán:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM | Pain từ người khác | Điều phối viên phải tự nghe lại ghi âm + đọc ghi chú của tài xế cho từng cuốc bị huỷ để tìm ra pattern lỗi hệ thống (định vị sai, kẹt xe, khách bom hàng...), không có tổng hợp tự động theo tuần. |
| 2 | VinFast | Tốn thời gian | Kỹ thuật viên trạm dịch vụ đọc thủ công hàng loạt log lỗi pin/hệ truyền động gửi về từ xe để phân loại mức độ nghiêm trọng trước khi mở phiếu bảo hành. |
| 3 | Vinhomes | AI có thể tốt hơn | Chatbot CSKH trên App Vinhomes Resident trả lời rập khuôn, không phân biệt được mức độ khẩn cấp giữa phản ánh "mất nước toàn toà" và "bóng đèn hành lang cháy". |
| 4 | Vinmec | Pain từ người khác | Bác sĩ phàn nàn mất 20–30 phút/bệnh nhân để tự tay soạn tóm tắt hồ sơ xuất viện từ bệnh án điện tử và kết quả xét nghiệm. |
| 5 | VinUni (giáo dục) | Lặp lại | Trợ giảng (TA) phải tự đọc log autograder + code từng sinh viên để giải thích lại lý do fail, vì log chỉ in `[PASS]/[FAIL]` một dòng ngắn, không đủ tính sư phạm để sinh viên tự hiểu và tự sửa. |

> Bài #5 xuất phát từ quan sát thực tế khi đọc chính file `autograder/autograder.py` của repo
> này: log chấm điểm chỉ in kết quả kỹ thuật (VD: `"[FAIL] SYSTEM_PROMPT is missing core
> safety guidelines"`) mà không giải thích *vì sao* hay *nên sửa hướng nào* — nên rất nhiều
> câu hỏi lặp lại dồn về cho TA.

---

# 🃏 Phase 2 — QUICK-ASSESS

Chọn top 3 bài toán từ SCAN và hoàn thiện 3 Quick Problem Cards.

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

**Quyết định chọn đề tài Deep-Dive:** Nhóm chọn **Card #1 — Trợ lý giải thích lỗi Autograder
cho TA/Sinh viên VinUni** vì đây là pain point nhóm *trực tiếp trải nghiệm* trong chính buổi
lab này (không phải suy diễn), có input/output rõ ràng (log autograder + code sinh viên →
giải thích sư phạm), và ranh giới an toàn dễ kiểm chứng (AI không được sửa bài, không được lộ
đáp án). Card #2 (Vinhomes) bị loại vì rủi ro pháp lý/tranh chấp phí quản lý cần rule-based
router chắc chắn hơn trước khi đưa AI vào; Card #3 (Vinmec) bị loại vì cần dữ liệu bệnh án
chuẩn hoá và thời gian thẩm định y khoa dài hơn phạm vi 1 buổi lab.
