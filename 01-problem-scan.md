# Lab 02 — Problem Scan & Quick Assessment

## Product theme

**Vinpearl AI Journey Copilot — Cá nhân hóa hành trình khách hàng trong hệ sinh thái Vinpearl**

> Phạm vi nghiên cứu: hành trình trước chuyến đi và trong thời gian lưu trú tại một điểm đến tích hợp của Vinpearl. Các nhận định dưới đây là giả thuyết sản phẩm dựa trên nguồn công khai; cần được xác thực bằng phỏng vấn vận hành và dữ liệu nội bộ trước khi triển khai thật.

## Evidence base

- Báo cáo thường niên 2025 của Vinpearl ghi nhận 13,4 triệu lượt khách và định hướng chuyển từ dịch vụ đơn lẻ sang hành trình trải nghiệm trọn gói, cá nhân hóa: [Vinpearl Annual Report 2025](https://statics.vinpearl.com/VINPEARL%20AR25_C1-6_260330_1774881976.pdf).
- Kế hoạch kinh doanh 2026 nêu rõ định hướng dùng AI và data analytics để tối ưu customer journey và conversion, đồng thời phát triển mô hình All-in-One Destination: [Vinpearl Business Plan 2026](https://statics.vinpearl.com/20260416_VPL_CBTT%20dieu%20chinh%20tai%20lieu%20hop%20DHDCD%20thuong%20nien%202026_TA_1776341231.pdf).
- MyVinpearl đã hỗ trợ booking, khuyến mại và online check-in; Vinpearl/VinWonders có nhiều touchpoint số và dịch vụ khác nhau: [Online check-in](https://vinpearl.com/en/online-check-in-safe-travel-save-time), [MyVinpearl promotion](https://vinpearl.com/en/promotion-smart-deal-5-myvinpearl).
- Chính sách dữ liệu của Vinpearl cho phép cá nhân hóa theo nhu cầu thực tế và sở thích trong phạm vi mục đích, sự đồng ý và quy định bảo vệ dữ liệu: [Vinpearl Privacy Policy](https://vinpearl.com/en/privacy-policy).

## Phase 1 — SCAN

| # | Subsidiary | Lens | Vấn đề/cơ hội vận hành | Bằng chứng cần thu thập thêm |
|---:|---|---|---|---|
| 1 | Vinpearl | AI-upgrade | Khách phải tự ghép nhiều lựa chọn phòng, VinWonders, Safari, F&B, spa/golf và vận chuyển thành một lịch trình phù hợp với thời gian, ngân sách và sở thích. | Tỷ lệ khách mở nhiều trang trước khi đặt; thời gian lập lịch; số câu hỏi về lịch trình gửi concierge. |
| 2 | Vinpearl | Time-consuming | Nhân viên concierge/CX phải đọc booking và hỏi lại nhu cầu để tư vấn lịch trình thủ công, đặc biệt với gia đình nhiều thế hệ. | Thời gian tư vấn trung bình; số lượt chỉnh sửa; tỷ lệ khách dùng tư vấn. |
| 3 | Vinpearl | Stakeholder Pain | Lịch trình tĩnh dễ trở nên không phù hợp khi thời tiết, giờ hoạt động, availability hoặc kế hoạch của khách thay đổi. | Số yêu cầu đổi lịch; lý do thay đổi; tỷ lệ hoạt động bị bỏ lỡ. |
| 4 | Vinpearl | Repetitive | Cùng một thông tin về thành viên đoàn, trẻ em, sở thích ăn uống và mức vận động có thể phải được nhập hoặc diễn giải lại tại nhiều touchpoint. | Số lần nhập lại dữ liệu; tỷ lệ profile thiếu; phản hồi của khách và nhân viên. |
| 5 | Vinpearl | AI-upgrade | Gợi ý ưu đãi/dịch vụ có thể chưa đúng thời điểm hoặc bối cảnh của từng khách, làm tăng nhiễu thay vì tăng giá trị hành trình. | CTR/acceptance theo phân khúc; tỷ lệ ẩn ưu đãi; lý do từ chối. |
| 6 | Vinpearl | Stakeholder Pain | Gia đình có trẻ nhỏ, người cao tuổi hoặc nhu cầu tiếp cận đặc biệt khó cân bằng nhịp độ, quãng đường và điều kiện tham gia hoạt động. | Yêu cầu hỗ trợ mobility; giới hạn tuổi/chiều cao; CSAT của nhóm gia đình. |
| 7 | Vinpearl | Time-consuming | Nội dung mô tả điểm đến và lịch trình mẫu cần được cá nhân hóa, dịch và kiểm tra tính nhất quán cho khách quốc tế. | Ngôn ngữ phổ biến; thời gian xử lý; lỗi dịch liên quan chính sách/giờ hoạt động. |

## Phase 2 — QUICK-ASSESS

### Quick Problem Card 1 — Personalized Journey Planner (được chọn)

| Thuộc tính | Nội dung |
|---|---|
| **Bài toán** | Khách lưu trú tại điểm đến tích hợp Vinpearl phải tự tổng hợp nhiều thông tin để tạo lịch trình phù hợp với nhóm đi cùng, thời gian, ngân sách và sở thích. |
| **Actor** | Khách du lịch; nhân viên concierge/CX hỗ trợ khách. |
| **Current workflow** | 1. Đặt phòng/vé → 2. Tìm hoạt động trên web/app → 3. So sánh giờ, vị trí và điều kiện → 4. Hỏi hotline/concierge → 5. Tự ghép và chỉnh lịch. |
| **Bottleneck** | Bước 2–4: tổng hợp nhiều ràng buộc và giải quyết xung đột. Working baseline cần kiểm chứng: 20–30 phút/khách tự lập lịch hoặc 8–12 phút/lượt tư vấn. |
| **AI intervention** | LLM hiểu yêu cầu tự nhiên và tạo lịch trình; rule engine kiểm tra các hard constraint; inventory API xác thực availability; khách/nhân viên xác nhận. |
| **Success metric** | P95 tạo draft <10 giây; ≥90% gợi ý hợp lệ theo catalog; ≤35% mục bị khách xóa/sửa; 100% giao dịch cần xác nhận. |
| **Quick architecture** | **LLM Feature + Retrieval + Rules**, không dùng autonomous agent trong MVP. |

### Quick Problem Card 2 — Real-time Journey Replanner

| Thuộc tính | Nội dung |
|---|---|
| **Bài toán** | Khi thời tiết, availability hoặc kế hoạch cá nhân thay đổi, khách thiếu một cách nhanh để sắp xếp lại phần còn lại của ngày. |
| **Actor** | Khách đang lưu trú; guest service/concierge. |
| **Current workflow** | 1. Phát hiện thay đổi → 2. Kiểm tra lại từng hoạt động → 3. Liên hệ đơn vị dịch vụ → 4. Chọn phương án thay thế → 5. Cập nhật thủ công. |
| **Bottleneck** | Bước 2–4. Chưa có baseline công khai; cần đo số cuộc gọi và thời gian xử lý theo lý do thay đổi. |
| **AI intervention** | Đề xuất phương án B từ catalog đã duyệt, giữ các booking cố định và giải thích thay đổi. |
| **Success metric** | 90% yêu cầu có phương án thay thế hợp lệ trong 30 giây; không làm mất booking đã xác nhận; CSAT sau replan ≥4/5. |
| **Quick architecture** | Rule + LLM Feature. |

### Quick Problem Card 3 — Multi-generational Family Preference Resolver

| Thuộc tính | Nội dung |
|---|---|
| **Bài toán** | Một lịch trình chung khó đồng thời phù hợp với trẻ nhỏ, người lớn và người cao tuổi trong đoàn gia đình. |
| **Actor** | Người đại diện đặt chuyến; concierge. |
| **Current workflow** | 1. Thu thập nhu cầu từng người → 2. Kiểm tra điều kiện hoạt động → 3. Thỏa hiệp lịch chung → 4. Tách/ghép hoạt động → 5. Gửi lịch cho cả đoàn. |
| **Bottleneck** | Bước 2–4; working baseline cần kiểm chứng: 10–15 phút/lượt tư vấn. |
| **AI intervention** | Nhóm hóa preference, phát hiện xung đột, tạo lịch chung và các nhánh tùy chọn trong cùng khung thời gian. |
| **Success metric** | 100% hard constraint tuổi/chiều cao/accessibility được kiểm tra; ≥80% thành viên chấp nhận phần lớn lịch trình trong pilot. |
| **Quick architecture** | LLM Feature + deterministic constraint solver. |

## Lựa chọn để Deep-Dive

Chọn **Card 1 — Personalized Journey Planner** vì phù hợp trực tiếp với định hướng All-in-One và cá nhân hóa của Vinpearl, có giá trị cho cả khách lẫn vận hành, có thể prototype bằng prompt nhưng vẫn thể hiện rõ vai trò của dữ liệu, rule engine, human-in-the-loop và fallback.

Không chọn Card 2 làm đề tài độc lập vì re-planning nên là phase tiếp theo sau khi planner cơ bản đã đáng tin cậy. Card 3 được giữ như một use case ưu tiên của Card 1 thay vì xây thành sản phẩm riêng.
