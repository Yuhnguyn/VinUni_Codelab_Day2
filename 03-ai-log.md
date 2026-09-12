# 03 — AI Log & Reflection

**Lab 02 — AI Product Scoping · Phase 6 — Reflection · 12/09/2026**

## 1. Bối cảnh và phạm vi phản ánh

Tài liệu ghi lại quá trình người dùng và trợ lý AI chuẩn bị bộ báo cáo trước code. Nội dung dựa trên các lượt trao đổi và hoạt động thực sự trong phiên làm việc; do AI tổng hợp để người dùng kiểm tra, không giả định người học đã tự thực hiện phỏng vấn hoặc thử nghiệm.

Yêu cầu ban đầu là đọc worksheet, bám README, tìm hiểu insight và chuẩn bị bốn file để review cho hướng quản lý cư dân thông minh. Qua các lượt phản biện, phạm vi được làm rõ: **Phase 1 phải quét rộng các đơn vị trong hệ sinh thái; Phase 2 có ba bài toán để so sánh; sau đó người dùng mới chọn bài toán cư dân nếu phù hợp.**

Trạng thái hiện tại: SCAN giữ 6 bài toán tại Vinhomes, VinFast, Xanh SM/GSM, Vinmec, Vinpearl và VinUni. Ba Quick Cards là **P1 — trợ lý cư dân hai luồng RAG/phản ánh, P2 — lịch dịch vụ VinFast, P5 — yêu cầu đoàn/MICE Vinpearl**. Người dùng đã cung cấp draft làm rõ ý định P1 và yêu cầu sửa báo cáo theo draft. Chưa code hoặc có chấp thuận vận hành thật.

Nguồn yêu cầu mới: bản “Draft tính năng — Trợ lý AI cư dân Vinhomes” do người dùng đính kèm; bản tương ứng trong workspace là [vinhomes-agent-feature-draft.md](vinhomes-agent-feature-draft.md). Đây là yêu cầu sản phẩm, không phải nội quy đã được BQL duyệt.

## 2. AI đã hỗ trợ như thế nào?

AI giúp chuyển yêu cầu bài lab thành cấu trúc có thể kiểm tra: ít nhất năm cơ hội, ba Quick Cards, workflow có handoff và bottleneck, Problem Statement sáu trường, so sánh Rule/LLM/Agent, ranh giới và quyết định readiness. Việc đọc cả worksheet lẫn README giúp xác định file thứ tư phải là sơ đồ PNG/PDF, không phải một báo cáo Markdown thêm.

Trong nghiên cứu, AI tìm nguồn chính thức về nghiệp vụ tiếp nhận phản ánh, đặt lịch dịch vụ xe, đặt xe, tiếp nhận lịch khám, tổ chức đoàn/MICE và hồ sơ tuyển sinh. Các nguồn được tập trung trong [01-problem-scan.md, mục 2](01-problem-scan.md). Giá trị của bước này là xác nhận các quy trình có tồn tại và tránh đề xuất một chức năng như thể doanh nghiệp chưa có sản phẩm tương tự. Nguồn công khai chưa đủ để kết luận pain đang phổ biến hoặc gây tổn thất bao nhiêu.

AI đã chuẩn bị phương án tiếp nhận phản ánh ở bản trước, sau đó sửa theo draft thành hai luồng: hỏi đáp có nguồn và phản ánh có xác nhận. Mỗi luồng có baseline riêng. RAG tìm căn cứ; mô hình đề xuất nội dung/nhóm/ưu tiên; phần mềm kiểm quyền, lưu và định tuyến. So sánh với tìm kiếm tài liệu hoặc form + rule được giữ để kiểm tra giá trị tăng thêm.

## 3. Những sai lệch thật đã xảy ra và cách người dùng sửa

Mục 3.1–3.3 ghi diễn biến các bản trước; mục 3.4 là cập nhật phạm vi hiện tại.

### 3.1. Đủ số dòng nhưng chưa đủ bài toán độc lập

Khi người dùng hỏi file đã có tối thiểu năm bài toán chưa, AI ban đầu trả lời rằng có sáu. Câu trả lời đúng về số lượng nhưng chưa đánh giá chất lượng phân rã. Nhiều mục như phân loại, cập nhật tiến độ, gộp trùng và tổng hợp phản ánh đều nằm trong cùng một quy trình xử lý phản ánh cư dân.

Người dùng chỉ ra: **“này m đang tách 1 bài toán lón thành 6 bài toán nhỏ à ?”**. Sau đó yêu cầu: **“t cần 6 bài toán cho phase 1 và 3 cái quick cards, m phân rã lại cho chuẩn đi”**. AI thừa nhận điểm yếu và sửa tiêu chí: mỗi cơ hội phải có tác nhân khởi tạo, đối tượng dữ liệu và kết quả nghiệp vụ riêng, có thể được chọn làm MVP độc lập.

Đây là lỗi suy luận về cấu trúc bài làm, không phải bằng chứng mô hình bịa một sự kiện doanh nghiệp. Bài học là không dùng việc đáp ứng số lượng để thay cho đánh giá chất lượng nội dung theo mục tiêu của rubric.

### 3.2. Giới hạn SCAN vào Vinhomes quá sớm

Bản sửa tiếp theo đã tách thành các quy trình riêng nhưng vẫn giữ cả sáu tại Vinhomes. Người dùng làm rõ: **“không cần chỉ vinhoem cho 6 bài toán, xong t sẽ chọn cái bài toán cư dân sau”**.

AI đã áp hướng sản phẩm dự kiến lên giai đoạn khám phá quá sớm. Cách sửa là mở SCAN sang sáu đơn vị và ba Quick Cards sang ba nghiệp vụ thuộc Vinhomes, VinFast, Vinpearl. Nhãn P1/P2/P5 được đồng bộ trong các báo cáo; không tiếp tục dùng nghĩa cũ của P2 là đối soát phí hoặc P5 là hồ sơ thi công. Phương án ResidentCare được giữ để review, không mô tả như quyết định đã chốt.

Bài học là phải tách **quét cơ hội → đánh giá ứng viên → chọn bài toán → xây prototype**. Hướng quan tâm của người dùng giúp định hướng lựa chọn sau, không tự động giới hạn bước quét cơ hội.

### 3.3. Các điểm thiếu nhất quán được phát hiện khi chuẩn hóa

Ở vòng chuẩn hóa ba file còn lại, cách đo thời gian được làm rõ để không trộn “duyệt câu hỏi bổ sung” với “duyệt bàn giao” trong cùng metric. Ca đủ dữ kiện được đo đến bàn giao; ca thiếu dữ kiện báo riêng. Nếu trộn hai kết quả khác nhau, hệ thống hỏi lại nhiều có thể trông nhanh hơn mà chưa giúp hoàn tất công việc.

Readiness cũng được tách theo giai đoạn. Bộ dữ liệu và scope rõ là điều kiện bắt đầu xây prototype; kết quả boundary tests là điều kiện xem xét pilot sau khi đã có prototype. Không đòi có kết quả chạy code trước khi được bắt đầu viết code.

Sơ đồ được chuẩn hóa theo cùng số bước, điểm bàn giao và thời gian với Deep Dive. Thời gian chờ được tách khỏi thời gian thao tác; các vòng thiếu dữ kiện/trả lại được thể hiện để không gây hiểu nhầm quy trình chỉ đi một chiều.

### 3.4. Bản trước chưa phản ánh đúng ý định trợ lý cư dân

Người dùng gửi draft và yêu cầu: **“đọc cái này sửa lại cho chuẩn 3 file cái ý định t làm, sửa luôn phase 1 nếu cần”**. Draft xác định hai hướng chính: hỏi đáp quy định bằng RAG và tiếp nhận/phân loại phản ánh trong cùng cuộc hội thoại.

Bản trước do AI đề xuất nghiêng về công cụ cho CSKH chuẩn bị bàn giao. Nó bỏ thiếu luồng hỏi đáp RAG, đặt con người duyệt ở mọi bản nháp và đưa timeline cư dân vào MVP. Những lựa chọn này không khớp draft mới. AI đã sửa Deep Dive và sơ đồ theo hai hành trình; cập nhật P1 và Card 1 nhưng giữ năm cơ hội khác cùng hai Quick Cards để bảo toàn SCAN rộng.

Các điều chỉnh cụ thể:

- RAG lọc tài liệu theo khu/tòa và hiệu lực; câu trả lời có nguồn và giữ ngữ cảnh hỏi tiếp; không đủ căn cứ thì nêu giới hạn, không bịa.
- Hỏi đáp thường có nguồn được trả trực tiếp. Phiếu thường được **cư dân** kiểm tra và xác nhận trước lưu; định tuyến theo cấu hình, BQL có thể chỉnh nhóm/ưu tiên. Không bắt CSKH duyệt mọi câu trả lời.
- Phân loại theo 7 nhóm và ưu tiên P0–P3, xét nguy cơ/phạm vi/độ cấp bách, không xét chỉ giọng điệu. P0 không đợi đủ form hoặc truy hồi RAG để hiển thị kênh khẩn đã cấu hình.
- Chỉ báo mã phiếu khi hệ thống lưu thành công; phân biệt đã lưu/chờ chuyển/đã chuyển; retry không tạo phiếu trùng.
- Tra trạng thái, ảnh, phát hiện trùng sự cố và đánh giá câu trả lời được chuyển ra sau MVP. Chống gửi lặp kỹ thuật vẫn cần trong MVP.

Bài học là phải đối chiếu từng tính năng với tài liệu người dùng đưa, không giữ thiết kế cũ chỉ vì nó đã viết thành báo cáo. Quyết định dùng RAG cũng tạo nhu cầu dữ liệu mới: tài liệu có nguồn, phạm vi và hiệu lực, không chỉ tập phản ánh.

## 4. Kiểm soát hallucination và giới hạn bằng chứng

### 4.1. Không biến số giả định thành kết quả thực tế

Các số luồng hỏi 6→2 phút, luồng phản ánh 8→4 phút và volume minh họa được dùng để thiết kế phép đo cho P1. Hai nhánh đo riêng, không cộng khi chưa biết lượt nghiệp vụ trùng nhau. Chưa có baseline quan sát. Tài liệu ghi rõ giả định/mục tiêu và nêu cách thay bằng dữ liệu thực. Không sao chép các số trong worked example Xanh SM làm số liệu Vinhomes.

### 4.2. Không biến desk research thành phỏng vấn

Review công khai chỉ giúp hình thành câu hỏi cần kiểm chứng. Chưa phỏng vấn cư dân, CSKH, kỹ thuật hay quản lý; không có câu nói người dùng cuối nào do AI sáng tác rồi ghi như lời phỏng vấn. Việc website mô tả một chức năng cũng không chứng minh chức năng đó đang gây đau hoặc hoạt động hoàn hảo.

Trong vòng nghiên cứu đầu, một bài Vinhomes không mở được và một bản PDF báo cáo thường niên bị công cụ từ chối do kích thước. Phần nội dung chỉ tìm thấy qua đoạn lập chỉ mục không được coi là đã đọc toàn tài liệu. Báo cáo SCAN hiện tại dẫn trực tiếp các nguồn dùng cho sáu bài toán; không dựa vào việc đã đọc đầy đủ báo cáo thường niên để đưa ra kết luận.

### 4.3. Chưa có kết quả thử mô hình

Chưa chạy Gemini hoặc prototype, nên chưa có output sai/đúng để đánh giá hallucination khi vận hành. JSON, prompt và adversarial inputs trong Deep Dive đều là **đặc tả hoặc ca dự kiến**, không phải kết quả kiểm thử. Các lỗi ở mục 3 là lỗi phân rã/phạm vi và đo lường, được ghi đúng bản chất thay vì gọi mọi lỗi là hallucination.

Khi code sau này, cần lưu input, output nguyên bản, kết quả kiểm tra và cách sửa prompt cho từng ca. Không điền PASS chỉ vì đọc prompt thấy hợp lý; cũng không xem một bộ test nhỏ đạt là bảo đảm mô hình luôn đúng ngoài thực tế.

## 5. Nhật ký quyết định và ranh giới sử dụng AI

| Vấn đề | Điều chỉnh đã thực hiện | Ý nghĩa |
|---|---|---|
| SCAN thiếu đa dạng | Sáu bài toán độc lập, mở rộng qua sáu đơn vị | Tách phạm vi khám phá khỏi một bộ tính năng |
| Phạm vi chưa đúng ý định | Theo draft mới: P1 có hỏi đáp RAG và phản ánh; scope tiếp tục để review trước code | Tài liệu người dùng là căn cứ thiết kế, không là chứng cứ đã triển khai |
| AI chưa có dữ liệu thực | Tách nguồn công khai, giả thuyết và mục tiêu | Không trình bày suy luận thành kết quả khảo sát |
| Nguy cơ chạy theo AI | Bắt buộc so với form/checklist/rule | Chỉ thêm LLM khi có lợi ích đo được |
| Nháp bị hiểu là hành động | Cư dân xác nhận phiếu thường; phần mềm kiểm quyền/phiên bản, lưu và định tuyến | Không áp DRAFT_ONLY lên mọi câu trả lời RAG; không bịa mã phiếu/trạng thái |
| Yêu cầu review trước code | Chỉ chuẩn bị nội dung và sơ đồ | Chưa triển khai ứng dụng hoặc gọi mô hình cho MVP |

Đã đọc starter/autograder và phát hiện các kiểm tra còn theo ví dụ xe điện. Điểm tương thích này được ghi trong Deep Dive để làm rõ khi chuyển sang code; chưa chỉnh bộ chấm hoặc thêm từ khóa không liên quan để vượt kiểm tra.

## 6. Phản ánh rút ra từ quá trình làm việc

Giá trị của AI trong phiên này nằm ở khả năng đọc nhiều yêu cầu, cấu trúc báo cáo và giúp phản biện một phương án. Tuy nhiên, phản hồi của người dùng mới là yếu tố làm rõ hai sai lệch lớn: phân rã một quy trình thành quá nhiều dòng và thu hẹp phạm vi SCAN quá sớm. Một tài liệu đầy bảng biểu vẫn có thể sai mục đích nếu không kiểm tra xem mỗi bài toán có độc lập và giai đoạn lựa chọn đã thực sự diễn ra chưa.

Một insight tốt cần giải thích hành vi hoặc khó khăn có căn cứ, rồi tạo ra giả thuyết có thể bác bỏ. Trong hướng cư dân, việc “muốn được hiểu đúng và có người nhận” mới là giả thuyết dẫn dắt; cần quan sát phiếu, hỏi người xử lý và xem công cụ hiện có trước khi coi đó là nhu cầu đã được xác nhận. AI chưa thay thế được phần tiếp cận thực tế này.

Khi phát triển, cần giữ liên kết giữa problem, metric và boundary. Nếu mục tiêu là bàn giao đúng, không thể chỉ đo tốc độ sinh văn bản; nếu mọi bản nháp phải duyệt, công sửa của người duyệt phải được tính. Nếu form + rule làm tốt tương đương, quyết định không dùng LLM vẫn là kết quả hợp lý của bài lab.

Tài liệu này là bản tổng hợp để người học review. Phần phản ánh cá nhân khi nộp cần thể hiện lựa chọn, nhận xét và trải nghiệm mà người học thực sự xác nhận; không viết rằng đã phỏng vấn, đo hoặc chạy thử những việc chưa xảy ra.

## 7. Trạng thái bằng chứng và phần cần bổ sung

| Hạng mục | Hiện trạng |
|---|---|
| Đọc hướng dẫn, SCAN 6 bài toán, 3 Quick Cards | Đã chuẩn bị tài liệu |
| Nguồn ngoài | Có link và giới hạn ở 01-problem-scan.md |
| Deep Dive, workflow, metric và boundary cho P1 | Đã có phương án để review |
| Định hướng sản phẩm | Có draft P1 hai luồng; đang review báo cáo trước code |
| Phỏng vấn, baseline, log nội bộ | Chưa có |
| Kho RAG, cấu hình và bộ ca 20 phát triển + 100 đánh giá | Mới đặc tả, chưa tạo dataset/kho tài liệu vận hành |
| Code MVP, Gemini, boundary tests | Chưa thực hiện |
| Hiệu quả thời gian, chi phí, chất lượng | Chưa đo |

Sau review scope theo draft, bổ sung vào nhật ký **quyết định thực tế và lý do**, rồi ghi từng thử nghiệm theo mẫu: mục tiêu → input/prompt → output thật → sai lệch → điều chỉnh → kết quả chạy lại. Không điền trước kết quả mong muốn như kết quả đã đạt.

Tài liệu liên quan: [Problem Scan](01-problem-scan.md), [Deep Dive P1 theo draft](02-deep-dive-report.md), [Current-State Workflow P1](04-workflow-diagram.png).
