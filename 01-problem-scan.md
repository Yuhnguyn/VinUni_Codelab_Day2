# 01 — Problem Scan & Quick Assessment

## Thông tin bài làm

- **Học viên:** Lê Thị Thùy Trang
- **Branch cá nhân:** `lethithuytrang-02678`
- **Vai trò giả định:** AI Product Engineer, Vin Smart Future
- **Phạm vi:** Phase 1 — SCAN và Phase 2 — QUICK-ASSESS
- **Đề tài cá nhân / Prompt Prototype:** Vinpearl Personalized Journey Copilot
- **Đề tài nhóm sau thảo luận:** Vinhomes Resident Request Copilot

> Đây là bài scan cá nhân dựa trên desk research. Các nguồn công khai xác nhận nghiệp vụ hoặc định hướng sản phẩm, không tự chứng minh doanh nghiệp đang vận hành kém. Những con số chưa có nguồn nội bộ được ghi rõ là **working baseline** hoặc **pilot target** và phải được kiểm chứng trước khi triển khai.

## 1. Evidence base và giới hạn nghiên cứu

| ID | Nguồn công khai và tín hiệu quan sát được | Có thể dùng để kết luận | Chưa thể kết luận |
|---|---|---|---|
| **E1** | [Quy định xử lý yêu cầu Vinhomes](https://market-files.vinhomes.vn/public-mngt/d/4804b1d6-546e-44e8-882c-64f7fac864e0), cập nhật 05/05/2025 | Có sự phân biệt giữa đầu mối tiếp nhận và bộ phận xử lý yêu cầu | Tỷ lệ chuyển sai, thời gian xử lý hoặc mức độ hài lòng tại một khu cụ thể |
| **E2** | [Vinhomes Resident trên App Store](https://apps.apple.com/vn/app/vinhomes-resident/id6450522818) | Ứng dụng có chức năng gửi yêu cầu dịch vụ và cập nhật trạng thái | Một review riêng lẻ không đại diện cho toàn bộ cư dân hoặc chứng minh lỗi còn tồn tại |
| **E3** | [Vinpearl Annual Report 2025](https://statics.vinpearl.com/VINPEARL%20AR25_C1-6_260330_1774881976.pdf) và [Business Plan 2026](https://statics.vinpearl.com/20260416_VPL_CBTT%20dieu%20chinh%20tai%20lieu%20hop%20DHDCD%20thuong%20nien%202026_TA_1776341231.pdf) | Vinpearl theo đuổi All-in-One Destination, hành trình cá nhân hóa và ứng dụng AI/data analytics | Mức độ phân mảnh hiện tại, thời gian khách tự lập lịch hoặc conversion uplift do AI |
| **E4** | [Trang đăng ký khám Vinmec](https://www.vinmec.com/vie/dang-ky-kham/) | Khách nhập lý do khám; yêu cầu lịch hẹn cần tổng đài gọi lại để xác nhận | Thời gian thao tác, tỷ lệ thiếu thông tin hoặc tỷ lệ phân luồng sai |
| **E5** | [FAQ dịch vụ VinFast](https://vinfastauto.com/vn_vi/cau-hoi-thuong-gap/cau-hoi-xe-o-to) | Có luồng chọn dịch vụ, mô tả nhu cầu, địa điểm và thời gian bảo dưỡng/sửa chữa | Tỷ lệ phải hỏi lại, đổi lịch hoặc xưởng không đủ năng lực thực hiện |
| **E6** | [Trung tâm trợ giúp Green SM](https://www.greensm.com/vn-vi/helps) | Điểm đón được nhập/xác nhận bằng địa chỉ hoặc GPS | Không chứng minh hệ thống GPS lỗi hay số lượt khách và tài xế không gặp được nhau |
| **E7** | [Quy trình tuyển sinh VinUni](https://admissions.vinuni.edu.vn/undergraduate/apply-to-vinuni/first-year-applicants/application-process/) | Hồ sơ trải qua bước sàng lọc và đánh giá | Tỷ lệ hồ sơ thiếu, tải công việc hoặc sai sót hiện tại |

### Giới hạn

- Chưa phỏng vấn nhân viên hoặc người dùng trực tiếp.
- Chưa tiếp cận log, SLA, chi phí và dữ liệu vận hành nội bộ.
- Không sử dụng số liệu trong bài mẫu của giảng viên như dữ liệu thật của doanh nghiệp.
- Không chọn AI trước khi so sánh với form, checklist và rule-based baseline.

## 2. Phase 1 — SCAN

### 2.1. Bảng quét 6 bài toán độc lập bằng 4 lenses

| ID | Subsidiary | Lens | Bài toán cụ thể và actor chịu tác động | Điểm bắt đầu → Kết quả nghiệp vụ | Evidence gap cần kiểm chứng |
|---|---|---|---|---|---|
| **P1** | **Vinhomes** | Repetitive; Time-consuming | Phản ánh tự do của cư dân có thể thiếu vị trí, mức độ khẩn cấp hoặc loại sự cố; CSKH phải làm rõ trước khi bàn giao cho kỹ thuật, vệ sinh, an ninh hoặc bộ phận liên quan | Cư dân gửi phản ánh → phiếu đủ dữ kiện được chuyển đúng bộ phận | E1–E2; cần đo tỷ lệ thiếu trường, số lần hỏi lại, thời gian thao tác và first-time-right routing |
| **P2** | **Vinpearl** | AI-upgrade; Stakeholder Pain | Khách gia đình phải tự ghép phòng, VinWonders, Safari, F&B, spa/golf và vận chuyển thành lịch trình phù hợp với thời gian, ngân sách và nhu cầu từng thành viên | Booking đã có → lịch trình cá nhân hóa khả thi để khách xem và xác nhận | E3; cần đo customer effort, số câu hỏi gửi concierge và tỷ lệ chấp nhận gợi ý |
| **P3** | **Vinmec** | Repetitive; Stakeholder Pain | Yêu cầu đặt/đổi lịch có thể thiếu dữ liệu hành chính; tổng đài viên phải đọc lý do khám, gọi lại và làm rõ trước khi xác nhận | Yêu cầu đặt/đổi lịch → lịch hành chính đủ thông tin và được nhân viên xác nhận | E4; cần đo số vòng liên hệ, thời gian xử lý và tỷ lệ yêu cầu đủ ngay lần đầu |
| **P4** | **VinFast** | Time-consuming | Cố vấn dịch vụ cần làm rõ mô tả của khách rồi đối chiếu loại dịch vụ, địa điểm, thời gian và năng lực xưởng trước khi xác nhận lịch | Khách gửi nhu cầu → lịch hẹn phù hợp được cố vấn và khách xác nhận | E5; cần log lịch hẹn và nguyên nhân hỏi lại/đổi lịch |
| **P5** | **Xanh SM / Green SM** | Stakeholder Pain | Tại địa điểm nhiều cổng, một ghim GPS có thể chưa diễn đạt đủ cổng đón và hướng tiếp cận mà khách và tài xế cùng hiểu | Khách đặt chuyến → hai bên thống nhất điểm đón hợp lệ | E6; cần quan sát thực địa, không mặc định GPS đang lỗi |
| **P6** | **VinUni** | Repetitive; AI-upgrade | Nhân viên tuyển sinh phải kiểm tra tính đầy đủ và nhất quán của nhiều tài liệu trước khi hồ sơ được chuyển sang vòng đánh giá | Thí sinh nộp hồ sơ → checklist đủ hoặc danh sách chính xác các mục cần bổ sung | E7; cần tỷ lệ hồ sơ thiếu/sai và thời gian rà soát; AI không được quyết định trúng tuyển |

### 2.2. Kiểm tra tính độc lập và baseline không-AI

| ID | Đơn vị công việc | Metric cần đo | Baseline không-AI phải so sánh trước |
|---|---|---|---|
| P1 | Phiếu phản ánh và nhóm tiếp nhận | Thời gian chuẩn hóa; số lần hỏi lại; routing đúng lần đầu | Form bắt buộc + rule theo loại sự cố/vị trí |
| P2 | Lịch trình của một booking/nhóm khách | Thời gian tạo lịch; edit rate; item hợp lệ | Itinerary template theo nhóm khách + bộ lọc |
| P3 | Một yêu cầu đặt/đổi lịch khám | Thời gian xác nhận; tỷ lệ đủ thông tin lần đầu | Form bắt buộc + workflow tổng đài hiện tại |
| P4 | Một yêu cầu dịch vụ xe | Thời gian xác nhận; tỷ lệ đổi lịch | Form + rule kiểm slot/năng lực xưởng |
| P5 | Một lượt đón tại điểm phức tạp | Số lượt liên hệ; thời gian gặp khách | Danh mục cổng/điểm đón được duyệt + bản đồ |
| P6 | Một bộ hồ sơ tuyển sinh | Thời gian rà; tỷ lệ phát hiện mục thiếu | Checklist + validation rule |

Không tách các tính năng của cùng một sản phẩm thành nhiều dòng để đủ số lượng. Sáu problems có actor, workflow owner, đầu vào và kết quả nghiệp vụ khác nhau.

## 3. Phase 2 — QUICK-ASSESS

Chọn ba bài toán độc lập để đánh giá: **P1 — Vinhomes**, **P2 — Vinpearl** và **P3 — Vinmec**. Các số phút dưới đây là working baseline dùng để thiết kế discovery, chưa phải số liệu được doanh nghiệp xác nhận.

### Quick Problem Card 1 — P1: Vinhomes Resident Request Copilot

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | CSKH/BQL phải đọc, hỏi lại và chuẩn hóa phản ánh tự do của cư dân trước khi chuyển một phiếu đủ dữ kiện đến đúng bộ phận xử lý. |
| **Actor / Ai đang đau?** | CSKH/BQL thao tác; kỹ thuật/vệ sinh/an ninh nhận việc; cư dân chịu thời gian chờ và phải bổ sung thông tin. |
| **Current workflow — 5 bước** | 1. Mở phản ánh (1 phút) → 2. Đọc và trích vị trí/sự cố (2 phút) → 3. Hỏi dữ kiện còn thiếu (2 phút) → 4. Chọn nhóm xử lý (2 phút) → 5. Soạn xác nhận và bàn giao (1 phút). |
| **Bottleneck** | Bước 2–4 chiếm 6/8 phút working baseline; thời gian chờ cư dân phản hồi được đo riêng. |
| **AI intervention** | Trích xuất tòa/căn/khu vực, loại sự cố và mức khẩn cấp; phát hiện trường thiếu; đề xuất nhóm; tạo câu hỏi hoặc nội dung xác nhận dạng nháp. |
| **Success metrics — pilot target** | P50 thao tác ≤4 phút và nhanh hơn ≥30% so với form + rule; routing đúng ≥36/40 phiếu đủ dữ kiện; 100% phiếu gửi/bàn giao có nhân viên duyệt; critical-case recall = 100%. |
| **Dữ liệu cần có** | 50 phiếu đã ẩn danh; taxonomy sự cố; danh mục tòa/vị trí/nhóm; nhãn routing chuẩn; timestamp thao tác. |
| **Quick Architecture** | **Rule + LLM Feature**. Rule chịu trách nhiệm mapping cố định và escalation; LLM chỉ xử lý văn bản tự do/draft. Không cần autonomous agent. |
| **HITL** | CSKH xem phản ánh gốc, dữ liệu trích xuất và nhóm được đề xuất trước khi gửi hoặc bàn giao. |
| **Fallback** | Thiếu dữ kiện/confidence thấp → hiển thị form hỏi lại; không có mapping → chuyển người trực; dấu hiệu nguy hiểm → escalation khẩn cấp. |
| **Operational Boundary** | AI không tự gửi, đóng phiếu, hứa SLA, phạt cư dân, truy cập căn khác hoặc quyết định trách nhiệm pháp lý. |

### Quick Problem Card 2 — P2: Vinpearl Personalized Journey Copilot

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Khách phải tự tổng hợp nhiều dịch vụ trong hệ sinh thái Vinpearl để tạo lịch trình phù hợp với booking, ngân sách, thời gian và nhu cầu của cả đoàn. |
| **Actor / Ai đang đau?** | Khách du lịch; concierge/CX hỗ trợ khách. |
| **Current workflow — 5 bước** | 1. Xem booking (2 phút) → 2. Tìm hoạt động/dịch vụ (8 phút) → 3. So sánh giờ, vị trí và điều kiện (7 phút) → 4. Hỏi concierge (5 phút) → 5. Ghép lịch (3 phút). |
| **Bottleneck** | Bước 2–4 chiếm 20/25 phút working baseline; cần đo bằng usability test và log concierge. |
| **AI intervention** | Hiểu preference tự nhiên, chọn candidate từ catalog đã duyệt và tạo itinerary draft; rule engine kiểm tra giờ, overlap, tuổi/chiều cao, accessibility và travel time. |
| **Success metrics — pilot target** | P95 tạo draft <10 giây; ≥90% item hợp lệ theo catalog; hard-constraint violation = 0; edit/removal rate ≤35%; itinerary CSAT ≥4/5. |
| **Dữ liệu cần có** | Booking tối thiểu; preference có consent; catalog ID, giờ hoạt động, điều kiện tham gia, vị trí, travel time và availability freshness. |
| **Quick Architecture** | **Retrieval + Rules + LLM Feature**; không dùng autonomous agent trong MVP. |
| **HITL** | Khách/concierge review; booking engine xác thực lại giá và availability; khách xác nhận trước giao dịch. |
| **Fallback** | Thiếu API → lịch mẫu đã duyệt; constraint mâu thuẫn → hỏi làm rõ; validator lỗi → không hiển thị draft như lịch hợp lệ. |
| **Operational Boundary** | AI không bịa giá/availability, tự đặt/hủy/thanh toán, bỏ qua giới hạn an toàn hoặc dùng profile chưa opt-in. |

### Quick Problem Card 3 — P3: Vinmec Appointment Intake Copilot

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Tổng đài viên phải làm rõ thông tin hành chính trong yêu cầu đặt/đổi lịch trước khi kiểm tra và xác nhận lịch khám. |
| **Actor / Ai đang đau?** | Tổng đài/CSKH thao tác; khách phải chờ hoặc cung cấp lại thông tin. |
| **Current workflow — 5 bước** | 1. Mở yêu cầu (1 phút) → 2. Đọc lý do và dữ liệu đã nhập (2 phút) → 3. Xác định trường hành chính còn thiếu (2 phút) → 4. Gọi/nhắn hỏi lại (2 phút) → 5. Kiểm lịch và xác nhận (1 phút). |
| **Bottleneck** | Bước 2–4 chiếm 6/8 phút working baseline, chưa tính thời gian chờ khách phản hồi. |
| **AI intervention** | Tóm tắt yêu cầu, phát hiện trường hành chính thiếu, phân loại intent đặt/đổi/hủy và soạn câu hỏi xác nhận; nhân viên chịu trách nhiệm chọn chuyên khoa và lịch. |
| **Success metrics — pilot target** | P50 thao tác ≤4 phút và nhanh hơn ≥30% so với form + rule; phát hiện đúng trường thiếu ≥95%; 100% lịch có nhân viên xác nhận; emergency false-negative = 0 trong safety set. |
| **Dữ liệu cần có** | Yêu cầu đã giảm định danh; schema đặt lịch; trường thiếu; kết quả xử lý; timestamp; bộ safety cases do chuyên môn duyệt. |
| **Quick Architecture** | **Form/Rule + LLM Feature**. LLM không phải công cụ chẩn đoán hoặc quyết định chuyên khoa. |
| **HITL** | Nhân viên đọc nội dung gốc, xác nhận dữ kiện, kiểm slot và quyết định bước tiếp theo. |
| **Fallback** | Nội dung mơ hồ → form/call thủ công; dấu hiệu khẩn cấp → dừng luồng đặt lịch và chuyển kênh cấp cứu chính thức. |
| **Operational Boundary** | AI không chẩn đoán, kê đơn, đánh giá mức độ bệnh, tự chọn chuyên khoa, tự xác nhận lịch hoặc tiết lộ dữ liệu sức khỏe. |

## 4. AI Prompt Log — Brainstorm và Stress-Test

Prompt là công cụ hỗ trợ tư duy, không được dùng thay cho dữ liệu thực tế.

### 4.1. Prompt brainstorm đã sử dụng

> Tôi là AI Product Engineer tại Vin Smart Future. Hãy đề xuất các pain point vận hành cụ thể tại Vinhomes, Vinpearl và Vinmec theo bốn lenses: repetitive, time-consuming, AI-upgrade và stakeholder pain. Với mỗi đề xuất, hãy nêu actor, workflow owner, đầu vào, kết quả nghiệp vụ, phương án không dùng AI và dữ liệu cần có. Không được bịa số liệu nội bộ; mọi con số chưa có nguồn phải ghi là giả thuyết cần kiểm chứng.

### 4.2. Prompt stress-test ba cards

> Đây là ba Quick Problem Cards của tôi. Hãy đóng vai CFO, Trưởng phòng Vận hành và Privacy/Safety Lead. Với từng card, chỉ ra: (1) logic nào chưa có bằng chứng; (2) metric nào thiếu baseline hoặc denominator; (3) phần nào form/rule có thể làm tốt hơn LLM; (4) rủi ro nếu AI sai; và (5) điều kiện nào khiến dự án phải dừng. Không chấp nhận lập luận “dùng AI vì hiện đại”.

### 4.3. Phản biện nhận được và cách sửa

| Card | Phản biện chính | Điều chỉnh sau phản biện |
|---|---|---|
| Vinhomes | Taxonomy cố định có thể chỉ cần rule; chưa có bằng chứng routing sai | Dùng form + rule làm baseline; LLM chỉ trích văn bản tự do; yêu cầu 50 phiếu ẩn danh và routing label trước pilot |
| Vinpearl | LLM có thể bịa availability; ba ý tưởng ban đầu thực chất là các tính năng của cùng planner | Giữ một card Journey Copilot; tách re-planning và family preference thành use case; bắt buộc catalog grounding, validator và confirmation gate |
| Vinmec | Ranh giới giữa hỗ trợ hành chính và tư vấn y khoa dễ bị vượt qua | Thu hẹp về intake hành chính; nhân viên chọn chuyên khoa; thêm emergency escalation và privacy boundary |

## 5. Phân tách quyết định cá nhân và quyết định nhóm

### 5.1. Lựa chọn cá nhân

Tôi chọn **P2 — Vinpearl Personalized Journey Copilot** để tiếp tục làm AI Log và Prompt Prototype cá nhân. Đây là đề tài tôi đã nghiên cứu, xây product thesis và xác định kiến trúc Retrieval + Rules + LLM + Human Confirmation.

| Tiêu chí | Vinhomes | Vinpearl | Vinmec |
|---|---|---|---|
| Workflow có thể quan sát và vẽ rõ | Cao | Trung bình | Cao |
| Dữ liệu synthetic dễ tạo | Cao | Trung bình | Trung bình |
| Giá trị tăng thêm của LLM so với rule | Cần chứng minh | Cao | Trung bình |
| Rủi ro nếu AI sai | Trung bình | Trung bình | Cao |
| HITL/fallback dễ thiết kế | Cao | Cao | Cao |
| Phù hợp prototype cá nhân | Cao | **Cao** | Trung bình |

### Lý do cá nhân chọn Vinpearl

- Phù hợp trực tiếp với định hướng All-in-One Destination và cá nhân hóa được Vinpearl công bố.
- LLM có giá trị rõ trong việc hiểu preference tự nhiên và giải thích lịch trình.
- Hard constraints có thể giao cho rule engine thay vì tin vào LLM.
- Có thể xây prototype bằng catalog synthetic mà không sử dụng dữ liệu khách thật.
- Boundary kiểm thử được: không bịa availability, không bỏ qua giới hạn an toàn và không tự thực hiện giao dịch.

### 5.2. Quyết định của nhóm

Sau khi các thành viên trình bày và thảo luận, nhóm chọn **P1 — Vinhomes Resident Request Copilot** cho `02-deep-dive-report.md` và `04-workflow-diagram`. Quyết định nhóm không thay thế đề tài cá nhân của tôi; code và reflection trên branch cá nhân vẫn theo Vinpearl.

## 6. Kế hoạch xác thực đề tài cá nhân Vinpearl

1. Phỏng vấn 5 khách gia đình, 3 concierge/CX và 2 nhân sự vận hành dịch vụ tại một cụm điểm đến.
2. Quan sát 10 lượt khách tự lập lịch; tách thời gian tìm kiếm, so sánh constraint và chỉnh lịch.
3. Chuẩn bị catalog synthetic 30–50 dịch vụ với ID, giờ, vị trí, điều kiện tham gia và travel time.
4. So sánh AI Journey Copilot với itinerary template + bộ lọc rule trên cùng 30 tình huống.
5. Chỉ tiếp tục nếu item hợp lệ ≥90%, hard-constraint violation = 0 và edit/removal rate ≤35%.

## 7. Checklist đối chiếu yêu cầu

- [x] Có ít nhất 5 bài toán thực tế: **6 bài toán độc lập**.
- [x] Bao phủ đủ 4 lenses.
- [x] Có 3 Quick Problem Cards.
- [x] Mỗi card có Actor và workflow 3–5 bước.
- [x] Có bottleneck và thời gian working baseline.
- [x] Có AI intervention và metric định lượng.
- [x] Có Quick Architecture.
- [x] Bổ sung data needs, baseline không-AI, HITL, fallback và operational boundary.
- [x] Có prompt brainstorm, stress-test, phản biện và cách sửa.
- [x] Ghi rõ Vinpearl là đề tài cá nhân và Vinhomes là đề tài nhóm.
