# 01 — Problem Scan: Cơ hội AI trong hệ sinh thái Vingroup

**Phase 1 — SCAN & Phase 2 — QUICK-ASSESS · Bản review trước code · 12/09/2026**

## 1. Phạm vi và trạng thái lựa chọn

Quét **6 bài toán độc lập ở 6 đơn vị**: Vinhomes, VinFast, Xanh SM/GSM, Vinmec, Vinpearl và VinUni. Dùng phạm vi hệ sinh thái theo worksheet/inspiration kit của lab; đây không phải báo cáo xác minh cơ cấu sở hữu pháp nhân. Giữ tên Xanh SM theo worksheet; các trang nguồn hiện hiển thị Green SM.

Phase 2 phân tích 3 ứng viên thuộc **Vinhomes, VinFast và Vinpearl**. **Chưa chốt bài toán đi sâu hoặc MVP.** Người dùng sẽ review rồi chọn; quản lý cư dân là một ứng viên, không phải giới hạn áp dụng cho toàn bộ SCAN.

Báo cáo Deep Dive và sơ đồ ResidentCare đã chuẩn bị là **phương án tham khảo riêng cho P1**, dùng nếu người dùng chọn bài toán cư dân. Không gộp 6 bài toán hoặc 3 cards thành một sản phẩm.

## 2. Bằng chứng và giới hạn nghiên cứu

Đã đọc README, worksheet, deliverable example, inspiration kit, starter code và autograder. Nghiên cứu hiện tại là **desk research**: chưa có phỏng vấn, log vận hành nội bộ hoặc phép đo thời gian. Các nguồn dưới đây xác nhận nghiệp vụ/dịch vụ công bố; không tự chứng minh quy trình đang chậm hay có lỗi phổ biến.

| ID | Nguồn và điều quan sát được | Giới hạn sử dụng |
|---|---|---|
| E1 | [Quy định xử lý yêu cầu Vinhomes](https://market-files.vinhomes.vn/public-mngt/d/4804b1d6-546e-44e8-882c-64f7fac864e0), cập nhật 05/05/2025: phân biệt đầu mối tiếp nhận và bộ phận xử lý | Xác nhận có bàn giao; chưa có tỷ lệ chuyển sai hoặc thời gian thao tác tại một tòa |
| E2 | [Vinhomes Resident trên App Store](https://apps.apple.com/vn/app/vinhomes-resident/id6450522818): có gửi yêu cầu dịch vụ và cập nhật trạng thái; review ngày 21/02/2024 phản ánh khó tiếp cận hỗ trợ khi app lỗi | Sản phẩm đã tồn tại; review cũ chỉ là tín hiệu cá nhân, không đại diện hoặc chứng minh lỗi còn tồn tại |
| E3 | [FAQ chính thức VinFast](https://vinfastauto.com/vn_vi/cau-hoi-thuong-gap/cau-hoi-xe-o-to), mục đặt lịch sửa chữa/bảo dưỡng: người dùng chọn dịch vụ, mô tả, địa điểm và thời gian | Xác nhận luồng đặt lịch; chưa biết tỷ lệ phải hỏi lại, đổi lịch hoặc khả năng xưởng đáp ứng |
| E4 | [Trung tâm giải đáp Green SM](https://www.greensm.com/vn-vi/helps) mô tả nhập/xác nhận điểm đón bằng địa chỉ hoặc GPS; [tính năng địa chỉ cũ/mới](https://www.greensm.com/vn-vi/news/tinh-nang-hien-thi-dia-chi-moi-sau-sap-nhap-tinh-thanh-pho-tren-ung-dung-xanh-sm) hỗ trợ cách hiển thị địa chỉ | Xác nhận bài toán địa điểm có ngữ cảnh; không chứng minh tỷ lệ đón nhầm hoặc số cuộc gọi tìm khách |
| E5 | [Tài liệu Vinmec Times City](https://www.vinmec.com/so-tay/ke-hoach-ung-pho-su-co-moi-truong-vinmec-times-city), phần quy trình khám: khách đặt qua tổng đài/quầy, lễ tân kiểm tra lịch và thông tin trong hệ thống | Chỉ dùng phần mô tả tiếp nhận hành chính; không suy ra thiếu sót y khoa hoặc hiệu quả phân luồng chuyên khoa |
| E6 | [Hội họp & Sự kiện Vinpearl](https://vinpearl.com/vi/meeting-events): có dịch vụ tổ chức hội họp, sự kiện và nhu cầu theo đoàn | Xác nhận nghiệp vụ MICE; chưa có email yêu cầu, số vòng hỏi lại hoặc thời gian chuẩn bị báo giá |
| E7 | [Quy trình nộp hồ sơ VinUni](https://admissions.vinuni.edu.vn/undergraduate/apply-to-vinuni/first-year-applicants/application-process/): hồ sơ qua bước sàng lọc và đánh giá; [FAQ tuyển sinh](https://admissions.vinuni.edu.vn/undergraduate/faqs/general-admissions/) có hướng dẫn chuẩn bị tài liệu | Xác nhận có rà hồ sơ; chưa có tỷ lệ thiếu giấy tờ, tải công việc hoặc lỗi kiểm tra |

Truy cập nguồn ngày 12/09/2026. Các pain chưa đo được ghi là **giả thuyết cần kiểm chứng**, không giả danh lời phỏng vấn. Không lấy số liệu ước tính trong bài mẫu làm dữ liệu của doanh nghiệp. Nguồn tiếp thị hoặc FAQ có thể mô tả luồng chuẩn tốt hơn trải nghiệm thực tế; phải đối chiếu bằng quan sát.

## 3. Phase 1 — SCAN: 6 bài toán ở các đơn vị khác nhau

### 3.1. Bảng quét cơ hội — đủ 4 lenses

| ID | Subsidiary / Đơn vị theo lab | Lens | Bài toán cụ thể và ai đang đau | Điểm bắt đầu → Kết quả nghiệp vụ | Căn cứ và khoảng trống |
|---|---|---|---|---|---|
| **P1** | **Vinhomes** | **Lặp lại; Tốn thời gian** | **Phản ánh cư dân thiếu thông tin hoặc chuyển sai đầu mối:** CSKH phải hỏi lại vị trí/sự cố rồi xác định nhóm nhận; cư dân chờ được tiếp nhận đúng | Cư dân báo vấn đề → phiếu đủ dữ kiện được bàn giao đúng bộ phận | E1–E2; chưa xác nhận tỷ lệ thiếu/chuyển sai tại cụm tòa cụ thể |
| **P2** | **VinFast** | **Tốn thời gian** | **Yêu cầu sửa chữa/bảo dưỡng chưa đủ để xếp lịch phù hợp:** cố vấn dịch vụ phải làm rõ nhu cầu và đối chiếu năng lực xưởng; khách có thể phải đổi lịch | Khách yêu cầu dịch vụ → lịch hẹn phù hợp được cố vấn và khách xác nhận | E3; việc hỏi lại/đổi lịch và tần suất là giả thuyết cần log lịch hẹn |
| **P3** | **Xanh SM / GSM** | **Stakeholder Pain** | **Tài xế và khách khó thống nhất điểm đón tại nơi nhiều cổng/lối vào:** phải gọi hoặc nhắn nhiều lần dù đã có ghim bản đồ | Khách đặt chuyến → hai bên xác nhận cùng điểm đón được phép tiếp cận | E4 xác nhận luồng địa điểm; pain cổng/lối vào cần quan sát tại một khu vực, không suy ra từ GPS rằng hệ thống đang lỗi |
| **P4** | **Vinmec** | **Lặp lại; Stakeholder Pain** | **Yêu cầu đặt/đổi lịch khám thiếu thông tin hành chính:** lễ tân phải hỏi lại cơ sở, lịch mong muốn, lịch hẹn cũ và thông tin liên hệ trước khi kiểm tra chỗ | Khách yêu cầu đặt/đổi lịch → lịch hành chính được xác nhận hoặc chuyển nhân viên phù hợp | E5; chưa có số vòng hỏi lại hoặc thời gian xử lý; không đưa chẩn đoán/chọn chuyên khoa bằng AI vào scope |
| **P5** | **Vinpearl** | **AI-upgrade; Tốn thời gian** | **Yêu cầu đoàn/MICE phân tán hoặc mâu thuẫn qua các trao đổi:** nhân viên kinh doanh phải tổng hợp số khách/phòng, ngày, hội họp và dịch vụ trước khi lập phương án | Doanh nghiệp/đại lý gửi nhu cầu đoàn → bản yêu cầu đầy đủ và phương án nháp để nhân viên duyệt | E6; luồng email và mức công tổng hợp cần được đội sales xác minh |
| **P6** | **VinUni** | **Lặp lại; AI-upgrade** | **Hồ sơ tuyển sinh thiếu hoặc không nhất quán dữ kiện:** nhân viên phải đối chiếu tài liệu và nhắc bổ sung trước vòng xét duyệt | Thí sinh nộp hồ sơ → bộ hồ sơ đủ điều kiện chuyển xét duyệt hoặc danh sách cần bổ sung | E7; chưa có tỷ lệ thiếu/sai, không đề xuất AI quyết định trúng tuyển |

### 3.2. Kiểm tra tính độc lập và mức phù hợp AI

| ID | Đối tượng nghiệp vụ | Metric đặc trưng để khảo sát | Hướng giải quyết sơ bộ |
|---|---|---|---|
| P1 | Phiếu phản ánh và nhóm xử lý | Thời gian chuẩn bị phiếu; tỷ lệ bàn giao đúng lần đầu | Form + rule; thử LLM trích dữ kiện và nháp câu hỏi |
| P2 | Lịch hẹn, loại dịch vụ và năng lực xưởng | Thời gian xác nhận lịch; tỷ lệ đổi lịch do sai dịch vụ/năng lực | Rule kiểm slot/năng lực; LLM chỉ làm rõ nhu cầu văn bản |
| P3 | Điểm đón và sự thống nhất khách–tài xế | Số lượt liên hệ; thời gian từ đến khu vực đón đến gặp khách | Danh mục điểm đón hợp lệ + bản đồ; chỉ thử LLM nếu ghi chú ngôn ngữ gây khó hiểu |
| P4 | Lịch khám hành chính | Tỷ lệ yêu cầu đủ thông tin lần đầu; thời gian đặt/đổi lịch | Form + kiểm lịch là baseline; LLM tùy giá trị tăng thêm |
| P5 | Yêu cầu đoàn, phương án dịch vụ | Thời gian tổng hợp yêu cầu; số lần hỏi lại trước lập phương án | LLM trích/tổng hợp có chứng cứ; rule kiểm số lượng, ngày, giá và tồn phòng |
| P6 | Hồ sơ tuyển sinh và checklist | Thời gian rà tính đầy đủ; tỷ lệ phát hiện hồ sơ cần bổ sung | Checklist + rule; LLM hỗ trợ đọc văn bản, người duyệt kết luận |

Sáu bài toán có đầu vào, bên chịu trách nhiệm và kết quả riêng. P1 không được tách tiếp thành “phân loại”, “gộp trùng”, “theo dõi tiến độ” để tăng số dòng. P2 xử lý lịch xưởng, P4 xử lý lịch khám: cùng có yếu tố đặt lịch nhưng thuộc hai quy trình độc lập với điều kiện vận hành và chủ sở hữu khác nhau.

## 4. Insight giả thuyết để dẫn dắt khảo sát

| Bài toán | Insight cần kiểm chứng, không phải lời người đã phỏng vấn | Cách kiểm chứng / điều kiện bác bỏ |
|---|---|---|
| P1 | Cư dân cần việc được hiểu đúng và có người nhận; thêm một chatbot chưa chắc giải quyết được chờ bàn giao | Xem 50 phiếu liên tiếp và phỏng vấn CSKH/cư dân; giảm ưu tiên nếu hệ thống hiện hữu đã tiếp nhận đúng, đủ và nhanh |
| P2 | Khách cần một lần đến xưởng có thể thực hiện công việc, không chỉ một giờ hẹn được ghi nhận | Đối chiếu yêu cầu ban đầu với lịch thực hiện; bác bỏ pain nếu hỏi lại/đổi lịch do tiếp nhận gần như không xảy ra |
| P3 | Một ghim bản đồ có thể chưa diễn đạt được cổng và hướng tiếp cận mà hai bên hiểu giống nhau | Quan sát 20 lượt đón ở nơi nhiều cổng; nếu danh mục điểm đón giải quyết đủ thì không cần LLM |
| P4 | Người đặt lịch cần biết thông tin nào còn thiếu để xác nhận, tránh lặp lại cùng dữ kiện nhiều lần | Đọc 30 lượt đặt/đổi lịch đã giảm định danh; nếu form bắt buộc đã giải quyết đủ thì bỏ phần AI |
| P5 | Nhân viên cần một bản yêu cầu đoàn thống nhất, có thể kiểm tra, hơn là email trả lời trôi chảy nhưng bỏ sót điều kiện | So bản tổng hợp với chuỗi trao đổi trên 20 yêu cầu đoàn; đo thiếu/mâu thuẫn và thời gian sửa |
| P6 | Thí sinh cần biết chính xác thiếu gì và theo checklist nào; câu nhắc chung chưa chắc giúp bổ sung đúng | Kiểm tra 30 hồ sơ và lý do bổ sung; nếu hệ thống đã chặn hết lỗi đơn giản, xác định còn lỗi văn bản nào đáng dùng AI |

Không xem mô hình tự đề xuất insight là nghiên cứu người dùng đã hoàn tất. Mỗi giả thuyết cần một ví dụ thực tế và phản ví dụ trước khi lựa chọn pilot.

## 5. Phase 2 — 3 Quick Problem Cards

Chọn **P1 — Vinhomes, P2 — VinFast, P5 — Vinpearl** để đánh giá sâu hơn trong Phase 2. Đây là ba ứng viên cho người dùng so sánh, chưa chọn một bài làm MVP.

**Quy ước:** toàn bộ số phút hiện trạng dưới đây là giả định thiết kế, chưa đo tại doanh nghiệp. Ngưỡng thành công là mục tiêu đề xuất. Chỉ đo thao tác nhân viên; thời gian chờ khách/nguồn lực tính riêng. “Workflow hiện tại” là mô hình cần xác nhận, không khẳng định đang làm hoàn toàn thủ công.

### Quick Problem Card 1 — P1: Vinhomes — Chuẩn hóa và bàn giao phản ánh cư dân

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | CSKH mất thời gian làm rõ phản ánh tự do để chuyển phiếu đủ thông tin đến đúng nhóm xử lý |
| **Công ty thành viên** | Vinhomes |
| **Actor / Ai đang đau?** | CSKH/BQL thao tác; kỹ thuật/vệ sinh/an ninh nhận việc; cư dân chịu thời gian chờ |
| **Workflow hiện tại — 5 bước** | 1. Nhận và mở phiếu (1 phút) → 2. Đọc/hỏi dữ kiện thiếu (3 phút) → 3. Chọn nhóm (2 phút) → 4. Soạn xác nhận (1 phút) → 5. Ghi nhận bàn giao (1 phút) |
| **Bottleneck** | Bước 2–4: 6/8 phút thao tác giả định; chưa tính chờ cư dân bổ sung và nhóm nhận |
| **AI Solution / Bước hỗ trợ** | Bước 2–4: trích vị trí/sự cố, phát hiện trường thiếu, đề xuất nhóm, nháp câu hỏi hoặc xác nhận có căn cứ |
| **Metric có số** | Median thao tác mục tiêu từ giả định 8 xuống ≤4 phút/phiếu, đồng thời giảm ≥30% so với form + rule trong thử nghiệm; đề xuất nhóm đúng ≥36/40 ca đủ dữ kiện; 0 gửi/đóng phiếu không được duyệt trong bộ test |
| **Dữ liệu cần có** | Phiếu ẩn danh, danh mục tòa/vị trí/nhóm, nhãn nhóm đúng và thời điểm thao tác |
| **Quick Architecture** | **Rule + LLM Feature**; baseline form + rule; không cần Agent |
| **HITL / Fallback** | CSKH xem bản gốc và duyệt trước gửi/bàn giao. Lỗi/thiếu dữ kiện → form thủ công; dấu hiệu nguy hiểm → người trực |
| **Cấm AI** | Tự gửi, đóng việc, phạt cư dân, hứa thời gian sửa hoặc truy xuất căn khác |
| **Điều kiện xem xét tiếp** | Có CSKH xác nhận pain và cho quan sát; nếu công cụ hiện hữu/form + rule đạt ngang hoặc hơn thì bỏ AI |

### Quick Problem Card 2 — P2: VinFast — Chuẩn bị lịch hẹn dịch vụ phù hợp năng lực xưởng

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Cố vấn dịch vụ phải làm rõ yêu cầu sửa chữa/bảo dưỡng và kiểm tra khả năng phục vụ trước khi xác nhận một lịch hẹn phù hợp |
| **Công ty thành viên** | VinFast |
| **Actor / Ai đang đau?** | Cố vấn dịch vụ/nhân viên đặt lịch; điều phối xưởng; khách có nguy cơ phải xác nhận hoặc đổi lịch nhiều lần |
| **Workflow hiện tại — 5 bước** | 1. Nhận yêu cầu dịch vụ (1 phút) → 2. Làm rõ dòng xe, nhu cầu, địa điểm (3 phút) → 3. Đối chiếu loại dịch vụ và năng lực/slot xưởng (4 phút) → 4. Đề xuất giờ phù hợp cho khách (2 phút) → 5. Xác nhận lịch (1 phút) |
| **Bottleneck** | Bước 2–3: 7/11 phút thao tác giả định; lịch khách muốn chưa chắc phù hợp công việc cần làm; chưa đo thời gian chờ khách/xưởng |
| **AI Solution / Bước hỗ trợ** | Bước 2: diễn giải mô tả của khách, xác định dữ kiện thiếu để cố vấn kiểm tra; bước 4: nháp giải thích các lựa chọn do hệ thống lịch cung cấp. Rule lọc slot theo danh mục dịch vụ, năng lực và dữ liệu xưởng |
| **Metric có số** | Median thao tác từ giả định 11 xuống ≤6 phút và giảm ≥30% so với form + rule; trên 40 ca với năng lực/slot chuẩn, ≥36 ca đề xuất được lịch hợp lệ hoặc đúng kết luận cần xác minh; 0 lịch vượt năng lực trong bộ test và 0 đặt lịch khi chưa có xác nhận |
| **Dữ liệu cần có** | Danh mục dịch vụ do xưởng duyệt, dữ kiện xe tối thiểu, lịch/năng lực xưởng, yêu cầu khách và lịch kết quả; demo dùng bảng giả lập, không giả định đã có API nội bộ |
| **Quick Architecture** | **Rule/State machine + LLM Feature**; rule chịu trách nhiệm tính hợp lệ của slot; không cần Agent tự điều phối |
| **HITL / Fallback** | Cố vấn xác minh nhóm dịch vụ, khách đồng ý giờ hẹn, phần mềm kiểm lại slot trước lưu. Không rõ nhu cầu hoặc dữ liệu lịch cũ → cố vấn liên hệ xưởng và xử lý thủ công |
| **Cấm AI** | Chẩn đoán lỗi xe, kết luận xe an toàn để tiếp tục chạy, tự quyết sửa/thay linh kiện hoặc bảo hành, bịa slot/giá và xác nhận hoàn tất sửa chữa |
| **Điều kiện xem xét tiếp** | Đo nguyên nhân đổi lịch trên 50 yêu cầu và khả năng lấy dữ liệu xưởng. Nếu chỉ cần form bắt buộc + lịch chuẩn thì không thêm LLM |

### Quick Problem Card 3 — P5: Vinpearl — Tổng hợp yêu cầu đoàn/MICE trước lập phương án

| Trường | Nội dung |
|---|---|
| **Bài toán (1 câu)** | Nhân viên kinh doanh phải nối các thông tin thiếu/mâu thuẫn trong yêu cầu đoàn để lập phương án lưu trú và sự kiện đúng nhu cầu |
| **Công ty thành viên** | Vinpearl |
| **Actor / Ai đang đau?** | Sales đoàn/MICE, nhân viên đặt phòng và khách doanh nghiệp/đại lý tổ chức đoàn |
| **Workflow hiện tại — 5 bước** | 1. Nhận yêu cầu/chuỗi trao đổi (2 phút) → 2. Tổng hợp ngày, số khách/phòng, yêu cầu sự kiện (5 phút) → 3. Kiểm tra thiếu/mâu thuẫn và hỏi lại (4 phút) → 4. Tra tồn phòng, không gian và bảng giá được duyệt (5 phút) → 5. Soạn phương án nháp (4 phút) |
| **Bottleneck** | Bước 2–3 và 5: 13/20 phút thao tác giả định; chưa tính thời gian chờ khách trả lời hoặc bộ phận đặt phòng xác nhận |
| **AI Solution / Bước hỗ trợ** | Bước 2–3: trích yêu cầu có dẫn chứng từ trao đổi, đánh dấu thay đổi và câu hỏi còn thiếu. Bước 5: nháp phương án chỉ từ tồn phòng/giá đã được cung cấp; phép tính và điều kiện thương mại kiểm bằng rule |
| **Metric có số** | Median tổng thao tác từ giả định 20 xuống ≤10 phút và giảm ≥30% so với mẫu yêu cầu + rule. Trên 30 yêu cầu với 150 trường bắt buộc đã gán nhãn: ≥143 trường trích đúng; ≥18/20 mâu thuẫn được phát hiện; 0 giá/tồn phòng tự bịa và 0 gửi báo giá/giữ phòng không duyệt trong bộ test |
| **Dữ liệu cần có** | Trao đổi đã ẩn danh, schema yêu cầu đoàn, nguồn tồn phòng/không gian, bảng giá/điều kiện còn hiệu lực, bản tổng hợp chuẩn của sales |
| **Quick Architecture** | **LLM Feature + Rule**; mẫu yêu cầu chuẩn là baseline; tra dữ liệu có kiểm soát, không cần Agent tự đặt phòng |
| **HITL / Fallback** | Sales xác nhận bản yêu cầu và phương án trước gửi. Thông tin mâu thuẫn → hỏi lại; không có giá/tồn phòng hợp lệ → để trống và chuyển nhân viên tra cứu |
| **Cấm AI** | Tự giữ phòng, xác nhận booking, tự giảm giá, hứa dịch vụ chưa được xác nhận hoặc gửi báo giá như cam kết chính thức |
| **Điều kiện xem xét tiếp** | Xin 20 yêu cầu đoàn và đo công tổng hợp; giảm ưu tiên nếu mẫu form hiện tại đã chuẩn hóa đủ hoặc không có quyền tiếp cận nguồn giá/tồn phòng |

## 6. Cơ sở chọn 3 cards và trạng thái quyết định

| Ứng viên | Có vào Phase 2? | Lý do sàng lọc sơ bộ |
|---|---|---|
| P1 — Vinhomes | **Có — Card 1** | Quy trình tiếp nhận có căn cứ công khai; phạm vi nhỏ, dữ liệu demo dễ chuẩn bị, phù hợp định hướng cư dân người dùng đang cân nhắc |
| P2 — VinFast | **Có — Card 2** | Kết quả lịch hợp lệ kiểm tra được; thể hiện rõ ranh giới giữa hiểu ngôn ngữ và rule tài nguyên |
| P3 — Xanh SM | Chưa | Cần dữ liệu điểm đón và kiểm chứng thực địa; danh mục cổng/điểm đón có thể giải quyết tốt hơn LLM |
| P4 — Vinmec | Chưa | Form hành chính có thể đủ; chưa có log đặt lịch để chứng minh AI giảm hỏi lại, không mở rộng sang chuyên môn y tế |
| P5 — Vinpearl | **Có — Card 3** | Yêu cầu đoàn có nhiều thuộc tính và điều kiện; đầu ra bản tổng hợp/nháp dễ đánh giá bằng người duyệt |
| P6 — VinUni | Chưa | Nghiệp vụ có thật nhưng chưa có bằng chứng hồ sơ thiếu gây tải đáng kể; cần so với checklist trước |

Đây là sàng lọc phục vụ lab, không phải xếp hạng mức độ đau thực tế của các doanh nghiệp. Cả ba cards đều chưa có baseline hoặc dữ liệu nội bộ; không tự cho điểm độ sẵn sàng cao chỉ vì demo dễ làm.

| Tiêu chí người dùng cần cân nhắc | Card 1 — Vinhomes | Card 2 — VinFast | Card 3 — Vinpearl |
|---|---|---|---|
| Đầu ra MVP | Phiếu chuẩn bị bàn giao | Đề xuất lịch hẹn hợp lệ | Bản yêu cầu đoàn + phương án nháp |
| Phụ thuộc vận hành lớn nhất | Bảng nhóm nhận và quy trình tòa | Lịch/năng lực xưởng đáng tin cậy | Tồn phòng, bảng giá và điều kiện dịch vụ |
| Baseline không AI | Form + rule phân nhóm | Form + bộ lọc slot/năng lực | Form yêu cầu đoàn + mẫu phương án |
| Phần AI cần chứng minh | Giảm đọc/hỏi lại mà không chuyển sai | Giảm làm rõ nhu cầu, không thay kiểm tra slot | Giảm tổng hợp mà không bỏ sót/mâu thuẫn |
| Trạng thái | Chờ người dùng lựa chọn | Chờ người dùng lựa chọn | Chờ người dùng lựa chọn |

**Quyết định chọn bài toán đi sâu: chưa thực hiện.** Sau review, người dùng có thể chọn P1 để tiếp tục hướng quản lý cư dân. Các tài liệu [02-deep-dive-report.md](02-deep-dive-report.md) và [04-workflow-diagram.png](04-workflow-diagram.png) hiện chỉ minh họa phương án P1; chúng không đại diện quyết định đã chốt.

## 7. Việc cần làm sau khi chọn một bài toán

1. Chỉ định chủ sở hữu quy trình và xác nhận hệ thống hiện có đã giải quyết những phần nào.
2. Thu mẫu liên tiếp theo khoảng ngày xác định, giảm định danh; không chỉ chọn ca dễ hoặc ca lỗi để minh họa.
3. Phỏng vấn người trực tiếp làm việc và người nhận kết quả; yêu cầu kể một trường hợp gần nhất thay vì hỏi “có muốn AI không?”.
4. Đo thao tác, chờ, tỷ lệ hỏi lại/sai và công sửa riêng; thay mọi baseline giả định bằng dữ liệu quan sát.
5. So với form/checklist/rule trước khi quyết định thêm LLM. Nếu không có lợi ích tăng thêm, bỏ AI hoặc chọn bài toán khác.

Nếu chọn P1: đề xuất phỏng vấn 5 cư dân, 2 CSKH, 1 kỹ thuật và 1 quản lý; quan sát 10 phiếu và xem 50 phiếu ẩn danh. Đây là kế hoạch chưa thực hiện, không phải kết quả insight đã được xác nhận.

**Đối chiếu yêu cầu:** Phase 1 có đúng 6 bài toán, phủ đủ 4 lenses; Phase 2 có đúng 3 Quick Cards với Actor, workflow 5 bước, bottleneck, AI Solution, metric có số và kiến trúc. Chưa code, chưa chạy prototype, chưa có quyết định GO cho triển khai thực tế.
