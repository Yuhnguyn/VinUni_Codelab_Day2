# Phase 1 — SCAN & Phase 2 — QUICK-ASSESS
**Học viên:** Dương  
**Đơn vị:** AI Product Engineer — Vin Smart Future (Tập đoàn Vingroup)  
**Nhánh Git:** `duong`  
**Bài tập:** Cá nhân (Deliverable cá nhân - Lab 02: AI Product Scoping)

---

## 🏛️ Bối cảnh & Vai trò

Tôi là **Dương**, kỹ sư AI Product tại **Vin Smart Future**. Nhiệm vụ của tôi là khảo sát thực địa các hoạt động vận hành hằng ngày trên toàn bộ hệ sinh thái Vingroup (VinFast, Xanh SM, Vinhomes, Vinmec, Vinpearl) nhằm nhận diện các điểm nghẽn (bottlenecks) có thể tối ưu hóa bằng trí tuệ nhân tạo, thiết lập ranh giới an toàn nghiêm ngặt và đề xuất kiến trúc kỹ thuật phù hợp.

---

# 🔍 Phase 1 — SCAN: Quét cơ hội vận hành Vingroup (4 Lenses)

Áp dụng 4 lăng kính cốt lõi:
1. **Lặp lại (Repetitive):** Tác vụ diễn ra tần suất cao, logic chuẩn hóa nhưng hiện xử lý thủ công.
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn hàng chục phút thao tác của con người, gây chậm trễ SLA.
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ hiện tại rập khuôn, thiếu cá nhân hóa hoặc chatbot cũ trả lời sai lệch.
4. **Pain từ người khác (Stakeholder Pain):** Điểm nghẽn gây bức xúc lớn cho tài xế, cư dân, bác sĩ hoặc khách hàng.

### 📝 Bảng quét 6 bài toán thực tế:

| # | Đơn vị thành viên | Lăng kính (Lens) | Tên bài toán / Nghiệp vụ | Mô tả ngắn bài toán & Điểm rò rỉ hiệu suất |
|---|-------------------|------------------|---------------------------|---------------------------------------------|
| 1 | **Xanh SM (GSM)** | Tốn thời gian & Pain | Xử lý điều vận cứu hộ pin xe điện khẩn cấp | Tài xế hết pin giữa đường gọi tổng đài. Điều phối viên mất 12-15 phút tra bản đồ, gọi trạm sạc, dễ chỉ sai trạm xa gây chết máy. |
| 2 | **Vinhomes** | Lặp lại & AI-upgrade | Phân loại & điều phối phản ánh cư dân qua App | Hằng ngày nhận hơn 3.000 phản ánh (mất nước, hỏng đèn, tiếng ồn). Nhân sự CSKH mất 8-10 phút/ticket để đọc, phân loại thủ công về đúng ban kỹ thuật tòa nhà. |
| 3 | **VinFast** | Stakeholder Pain | Phân loại sơ bộ lỗi xe qua mô tả tiếng Việt của khách | Khách hàng liên hệ tổng đài mô tả tiếng Việt không chuẩn kỹ thuật (ví dụ: *"xe đi qua gờ giảm tốc kêu cụp cụp bánh trước"*). Tiếp nhận viên mất 15 phút tra bảng mã DTC. |
| 4 | **Vinmec** | Tốn thời gian | Trích xuất và soạn thảo tóm tắt hồ sơ xuất viện | Bác sĩ mất 20-30 phút/bệnh nhân để đọc lại toàn bộ kết quả xét nghiệm, chẩn đoán hình ảnh và viết tóm tắt xuất viện bằng ngôn ngữ phổ thông cho người bệnh. |
| 5 | **Vinpearl** | AI-upgrade & Lặp lại | Phân tích & cảnh báo khẩn cấp đánh giá tiêu cực (Review) | Review từ Booking, Agoda, Google Maps đổ về liên tục. Trưởng bộ phận không kịp đọc hết, để lọt các phàn nàn nghiêm trọng (phòng ẩm mốc, thái độ nhân viên) quá 24h. |
| 6 | **VinFast** | Lặp lại | Đối soát hóa đơn tiêu thụ điện tại trạm sạc đối tác | So khớp dữ liệu đo đếm điện năng từ 5.000 trụ sạc ngoài với hóa đơn EVN hằng tháng, hiện đang chạy Excel thủ công gây chậm thanh quyết toán 5 ngày. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Từ danh sách trên, tôi chọn ra **Top 3 bài toán tiềm năng nhất** để phân tích nhanh độ khả thi và ranh giới vận hành:
- **Card #1:** [Xanh SM] Điều vận cứu hộ khẩn cấp xe điện kiệt pin
- **Card #2:** [Vinhomes] Phân loại và điều phối tự động phản ánh cư dân App Resident
- **Card #3:** [VinFast] Phân loại sơ bộ triệu chứng lỗi xe qua ngôn ngữ tự nhiên tiếng Việt

---

### 🎴 QUICK PROBLEM CARD #1: Điều vận cứu hộ pin xe điện khẩn cấp

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                                       │
│                                                                             │
│ Bài toán: Tài xế Xanh SM báo pin nguy cấp (< 5%) giữa đường, cần chỉ đường  │
│           trạm sạc gần nhất hoặc điều xe sạc di động (Mobile Charger).      │
│ Đơn vị thành viên: [x] Xanh SM (GSM)     [ ] VinFast     [ ] Vinhomes       │
│                                                                             │
│ Ai đang đau (Actor)?                                                        │
│ - Tài xế Xanh SM: Nguy cơ chết máy giữa đường phố, bị phạt hủy cuốc, stress.│
│ - Điều phối viên (Dispatcher): Quá tải cuộc gọi giờ cao điểm, áp lực xử lý. │
│                                                                             │
│ Workflow thủ công hiện tại (5 bước):                                        │
│   1. Tài xế gọi hotline khẩn cấp báo tọa độ GPS và dung lượng pin hiện tại. │
│   → 2. Điều phối viên mở tab bản đồ VinFast tra cứu bán kính trạm khả dụng. │
│   → 3. Kiểm tra tình trạng cổng sạc (còn trụ sạc nhanh trống hay không).    │
│   → 4. Soạn tin nhắn chỉ đường/hướng dẫn gửi qua App tài xế.                │
│   → 5. Nếu xe cạn pin, gọi điện thoại điều phối xe sạc pin lưu động đến.   │
│                                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                                            │
│ - Bước 2 + 3 + 4: Mất trung bình 12 - 15 phút/cuộc gọi.                     │
│ - Nguy cơ lỗi: Điều phối viên chọn nhầm trạm sạc quá xa (> 5km) khiến xe    │
│   hết pin giữa đường, gây tắc đường và nguy hiểm giao thông.                │
│                                                                             │
│ AI có thể can thiệp hỗ trợ ở bước nào?                                      │
│ - Hỗ trợ Bước 3 & 4: Tự động tổng hợp thông tin, kiểm tra ranh giới pin,    │
│   draft tin nhắn chỉ đường hoặc tự động trả về payload điều xe cứu hộ.      │
│                                                                             │
│ Đo thành công bằng gì (Metric định lượng)?                                  │
│ - Thời gian điều phối (Dispatch SLA): Giảm từ 14 phút xuống dưới 2 phút.    │
│ - Tỉ lệ cứu hộ pin kịp thời: Đạt > 98% không xảy ra sự cố cạn pin giữa phố. │
│                                                                             │
│ Quick Architecture: [ ] No AI   [ ] Pure Rule   [x] LLM Co-pilot   [ ] Agent│
│ Ranh giới an toàn: Mọi output phải có [DRAFT_ONLY]; Pin < 5% cấm đi xa > 5km│
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #2: Phân loại & điều phối ticket phản ánh cư dân Vinhomes

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                                       │
│                                                                             │
│ Bài toán: Tự động đọc, phân loại chuyên mục và phân luồng phản ánh/khiếu nại│
│           của cư dân gửi qua ứng dụng Vinhomes Resident về đúng ban quản lý.│
│ Đơn vị thành viên: [ ] Xanh SM    [ ] VinFast    [x] Vinhomes    [ ] Vinmec │
│                                                                             │
│ Ai đang đau (Actor)?                                                        │
│ - Cư dân: Chờ đợi lâu, phản ánh khẩn cấp (rò rỉ nước, kẹt thang) bị trễ hẹn.│
│ - Nhân viên CSKH/Ban quản lý tòa nhà: Ngập trong 3.000+ tickets/ngày.       │
│                                                                             │
│ Workflow thủ công hiện tại (4 bước):                                        │
│   1. Cư dân gửi form phản ánh kèm ảnh/video trên App Vinhomes Resident.     │
│   → 2. Nhân viên tiếp nhận trung tâm đọc nội dung, xác định tòa nhà và lỗi. │
│   → 3. Gán thẻ chuyên mục (Điện/Nước/An ninh/Vệ sinh) và mức độ ưu tiên.    │
│   → 4. Forward ticket cho Đội kỹ thuật trực tiếp tại phân khu tương ứng.    │
│                                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                                            │
│ - Bước 2 + 3: Mất 8 - 12 phút/ticket, thường xuyên phân loại nhầm ban.      │
│                                                                             │
│ AI có thể can thiệp hỗ trợ ở bước nào?                                      │
│ - Can thiệp Bước 2 + 3: Dùng LLM trích xuất thực thể (phân khu, số căn hộ,  │
│   vấn đề gặp phải), gán nhãn mức độ nghiêm trọng và draft ticket chuyển đi. │
│                                                                             │
│ Đo thành công bằng gì (Metric định lượng)?                                  │
│ - Thời gian phân luồng ticket: Giảm từ 45 phút xuống dưới 30 giây.          │
│ - Độ chính xác phân luồng chuyên môn: Đạt >= 95%.                           │
│                                                                             │
│ Quick Architecture: [ ] No AI   [ ] Pure Rule   [x] LLM Feature   [ ] Agent │
│ Ranh giới an toàn: Các sự cố an ninh/cháy nổ phải trigger còi báo động ngay.│
└─────────────────────────────────────────────────────────────────────────────┘
```

---

### 🎴 QUICK PROBLEM CARD #3: Trợ lý chẩn đoán sơ bộ triệu chứng lỗi xe VinFast

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                                       │
│                                                                             │
│ Bài toán: Phân tích mô tả lỗi bằng tiếng Việt tự nhiên của chủ xe VinFast,   │
│           chuẩn hóa thành mã nghi vấn kỹ thuật trước khi đặt lịch bảo dưỡng.│
│ Đơn vị thành viên: [ ] Xanh SM    [x] VinFast    [ ] Vinhomes    [ ] Vinmec │
│                                                                             │
│ Ai đang đau (Actor)?                                                        │
│ - Chủ xe VinFast: Lo lắng khi xe có âm thanh lạ, không biết xe bị lỗi gì.   │
│ - Cố vấn dịch vụ xưởng (Service Advisor): Mất 20 phút hỏi đi hỏi lại để     │
│   mô tả lại cho kỹ thuật viên kiểm tra.                                     │
│                                                                             │
│ Workflow thủ công hiện tại (4 bước):                                        │
│   1. Khách gọi điện/nhắn tin mô tả triệu chứng xe (tiếng kêu, mùi khét...). │
│   → 2. Cố vấn dịch vụ tra cứu cẩm nang kỹ thuật hướng dẫn xe VF e34/VF8/VF9.│
│   → 3. Đoán nhóm bộ phận nghi vấn (Hệ thống treo, pin cao áp, phanh...).    │
│   → 4. Tạo phiếu hẹn tiếp nhận và chuyển giao kỹ thuật viên xưởng.          │
│                                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                                            │
│ - Bước 2 + 3: Mất 15 - 20 phút/lượt, phụ thuộc lớn vào kinh nghiệm cố vấn.  │
│                                                                             │
│ AI có thể can thiệp hỗ trợ ở bước nào?                                      │
│ - Can thiệp Bước 2: LLM nhận diện từ khóa triệu chứng tiếng Việt dân dã      │
│   ("kêu lọc cọc", "hẫng chân ga") và ánh xạ sang 3 mã lỗi tiềm năng nhất.   │
│                                                                             │
│ Đo thành công bằng gì (Metric định lượng)?                                  │
│ - Thời gian tiếp nhận và lập phiếu: Giảm từ 20 phút xuống dưới 3 phút.      │
│ - Tỉ lệ kỹ thuật viên chuẩn bị đúng phụ tùng trước khi xe vào xưởng: > 80%. │
│                                                                             │
│ Quick Architecture: [ ] No AI   [ ] Pure Rule   [x] LLM Feature   [ ] Agent │
│ Ranh giới an toàn: Cấm tuyệt đối kết luận chẩn đoán thay kỹ sư (chỉ gợi ý)  │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

**Xác nhận của học viên:**  
Tôi đã hoàn thiện đầy đủ 6 bài toán khảo sát theo 4 Lăng kính và 3 Thẻ bài toán Quick Cards. Dữ liệu này đã sẵn sàng để nhóm thảo luận và chọn lọc bài toán bước vào Phase 3 (Deep-Dive).
