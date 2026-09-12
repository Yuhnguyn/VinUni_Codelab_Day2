# Phase 1 & 2 — Problem Scan & Quick Assessment (Vin Smart Future)

**Họ và tên:** Học viên VinUni  
**Đơn vị:** Vin Smart Future (Vingroup)  
**Bài nộp:** Cá nhân (Phase 1: SCAN & Phase 2: QUICK-ASSESS)  

---

## 🔍 Phase 1 — SCAN: Bảng Quét Cơ Hội AI tại Vingroup

Bảng dưới đây quét qua các hoạt động vận hành của các công ty thành viên Vingroup (VinFast, Xanh SM, Vinhomes, Vinmec, Vinpearl) dựa trên **4 Lenses** (Lặp lại, Tốn thời gian, AI-upgrade, Stakeholder Pain) để tìm kiếm các điểm nghẽn hiệu suất thực tế.

| # | Subsidiary | Lens | Mô tả ngắn bài toán / Bottleneck |
|---|------------|------|-----------------------------------|
| 1 | **VinFast** | Time-consuming & AI-upgrade | Chẩn đoán nguyên nhân sự cố kỹ thuật xe điện dựa trên đối chiếu mã lỗi DTC (OBD log) và mô tả tiếng Việt của khách hàng tại Xưởng Dịch Vụ. |
| 2 | **Xanh SM (GSM)** | Repetitive & Stakeholder Pain | Xử lý khiếu nại sai lệch cước phí/lộ trình GPS giữa tài xế và khách hàng khi gặp sự cố giao thông hoặc đường phân luồng cấm. |
| 3 | **Vinhomes** | Repetitive & Time-consuming | Phân loại, trích xuất tọa độ và điều phối tự động các phản ánh hỏng hóc hạ tầng/tiện ích từ cư dân trên App Vinhomes Resident đến đúng Ban Quản Lý. |
| 4 | **Vinmec** | Time-consuming & Stakeholder Pain | Tự động tổng hợp dữ liệu bệnh án điện tử (EHR) để draft **Bản tóm tắt xuất viện (Discharge Summary)** và dặn dò uống thuốc bằng ngôn ngữ dễ hiểu. |
| 5 | **Vinpearl / VinWonders** | Repetitive & Time-consuming | Trích xuất thông tin từ Email đặt đoàn phức tạp (Corporate Group Booking) để kiểm tra quỹ phòng/vé và draft báo giá tự động. |

---

## 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Dưới đây là 3 Thẻ bài toán được phân tích chi tiết từ danh sách trên (#1 VinFast, #4 Vinmec, #5 Vinpearl).

### 📋 QUICK PROBLEM CARD #1: VinFast — Chẩn đoán lỗi xe điện (DTC Logs + Voice/Text Khách hàng)

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Chẩn đoán nguyên nhân lỗi xe điện dựa trên│
│ đối chiếu mã lỗi DTC (OBD log) và mô tả tiếng Việt của khách│
│                                                             │
│ Công ty thành viên: [x] VinFast   [ ] Xanh SM   [ ] Vinhomes│
│                     [ ] Vinmec    [ ] Vinpearl              │
│                                                             │
│ Ai đang đau (Actor)? Kỹ thuật viên (KTV) Xưởng dịch vụ      │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Nhận xe & cắm thiết bị OBD quét mã DTC (5 min)         │
│   ──> 2. Đọc file log PDF hàng nghìn dòng & ghi nhận mô tả  │
│   ──> 3. Lật tài liệu kỹ thuật tra cứu thủ công (25 min) 🔴  │
│   ──> 4. Soạn biên bản chẩn đoán ban đầu cho khách (10 min) │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 25 phút/lượt)    │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3 & 4            │
│ (Phân tích DTC + Text khách ──> Gợi ý 3 nguyên nhân & Draft)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian chẩn đoán từ 40 phút ──> dưới 8 phút/xe.     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM Feature    │
└─────────────────────────────────────────────────────────────┘
```

---

### 📋 QUICK PROBLEM CARD #4: Vinmec — Draft Tóm tắt Hồ sơ xuất viện (Discharge Summary)

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #4                                       │
│                                                             │
│ Bài toán (1 câu): Tự động trích xuất bệnh án điện tử để     │
│ draft Bản tóm tắt xuất viện & dặn dò dùng thuốc dễ hiểu.    │
│                                                             │
│ Công ty thành viên: [ ] VinFast   [ ] Xanh SM   [ ] Vinhomes│
│                     [x] Vinmec    [ ] Vinpearl              │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị & Bệnh nhân xuất viện  │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Mở hệ thống EHR gom thông tin bệnh nhân (5 min)         │
│   ──> 2. Đọc kết quả xét nghiệm, đơn thuốc, ghi chú (10 min)│
│   ──> 3. Tự gõ tay bản tóm tắt dịch sang văn phong dễ hiểu  │
│          dặn dời bệnh nhân uống thuốc (15 min) 🔴           │
│   ──> 4. In ấn, giải thích và giao hồ sơ cho bệnh nhân      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 15 phút/bệnh nhân)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3                │
│ (Trích xuất EHR ──> Draft bảng dặn dò uống thuốc & tóm tắt) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian gõ hồ sơ từ 25 phút ──> dưới 5 phút/bệnh nhân│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM Feature    │
└─────────────────────────────────────────────────────────────┘
```

---

### 📋 QUICK PROBLEM CARD #5: Vinpearl — Xử lý Email đặt phòng/vé đoàn (Corporate Booking)

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #5                                       │
│                                                             │
│ Bài toán (1 câu): Trích xuất thông tin từ Email đặt đoàn    │
│ phức tạp để tra cứu quỹ phòng trống và draft báo giá tự động│
│                                                             │
│ Công ty thành viên: [ ] VinFast   [ ] Xanh SM   [ ] Vinhomes│
│                     [ ] Vinmec    [x] Vinpearl/VinWonders   │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Sales / Chăm sóc Khách đoàn  │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Đọc email yêu cầu từ đại lý lữ hành/doanh nghiệp (5 min)│
│   ──> 2. Bóc tách thủ công loại phòng, ngày đi, số vé (10 min)│
│   ──> 3. Tra phần mềm PMS kiểm tra quỹ phòng & tính giá (15 min)🔴│
│   ──> 4. Soạn email báo giá kèm file Excel chi tiết gửi khách│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 25 phút/email)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 3 & 4         │
│ (AI parse JSON ──> Auto-check API PMS ──> Draft Email giá)  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ Giảm thời gian phản hồi báo giá từ 4 tiếng ──> dưới 15 phút.│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM Feature    │
└─────────────────────────────────────────────────────────────┘
```

---

## 🗳️ Lựa chọn của Cá nhân & Đề xuất cho Nhóm

Sau khi phân tích 3 thẻ bài toán trên, tôi đề xuất chọn **Bài toán #1 (VinFast — Chẩn đoán lỗi kỹ thuật xe điện DTC)** hoặc **Bài toán #4 (Vinmec — Draft Tóm tắt Hồ sơ xuất viện)** cho phần Deep-Dive của nhóm.

* **Lý do chọn:** Cả 2 bài toán đều có nỗi đau thực tế rất lớn, tốn nhiều giờ xử lý thủ công chuyên môn, và mô hình **LLM Feature kết hợp duyệt Human-in-the-loop** hoàn toàn giải quyết mượt mà với độ an toàn cao.
