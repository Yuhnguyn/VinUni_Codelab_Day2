# Draft tính năng — Trợ lý AI cư dân Vinhomes

> Bản đề xuất để thảo luận phạm vi sản phẩm. Các nhóm phản ánh, mức ưu tiên và quy trình dưới đây là đề xuất cho prototype, chưa phải quy định vận hành chính thức của Vinhomes.

## 1. Mục tiêu và phạm vi

Xây dựng trợ lý AI giúp cư dân tra cứu quy định và gửi phản ánh ngay trong một cuộc hội thoại. Ban quản lý nhận được phản ánh đã có đủ thông tin, được phân loại và đề xuất mức ưu tiên để xử lý.

Sản phẩm chỉ tập trung vào **2 hướng chính**:

1. **Hỏi đáp quy định bằng RAG:** tìm nội dung liên quan trong tài liệu được ban quản lý cung cấp, rồi trả lời kèm nguồn.
2. **Tiếp nhận phản ánh cư dân:** thu thập thông tin, phân loại vấn đề, đánh giá độ ưu tiên và chuyển đến bộ phận phụ trách; dùng RAG để tra cứu quy trình hoặc quy định liên quan khi cần.

## 2. Hướng 1 — Hỏi đáp quy định bằng RAG

### Nhu cầu

Cư dân muốn biết mình được làm gì, cần thực hiện thủ tục nào và liên hệ ở đâu mà không phải tự tìm trong nhiều tài liệu hoặc chờ ban quản lý trả lời.

### Tính năng đề xuất

| Mã | Tính năng | Hành vi mong muốn | Phạm vi |
|---|---|---|---|
| Q01 | Hỏi đáp bằng ngôn ngữ tự nhiên | Hiểu câu hỏi tiếng Việt, kể cả cách viết tắt hoặc thiếu dấu | MVP |
| Q02 | Tra cứu tài liệu bằng RAG | Tìm nội quy, hướng dẫn thủ tục và thông báo phù hợp với câu hỏi | MVP |
| Q03 | Trả lời kèm nguồn | Hiển thị câu trả lời ngắn, tên tài liệu, mục/trang hoặc liên kết để kiểm tra | MVP |
| Q04 | Lọc đúng khu và hiệu lực | Chỉ dùng tài liệu phù hợp với khu/tòa và thời điểm áp dụng; hỏi lại nếu thiếu thông tin | MVP |
| Q05 | Hỏi tiếp theo ngữ cảnh | Hiểu các câu tiếp nối như “cần giấy tờ gì?” trong cùng một chủ đề | MVP |
| Q06 | Xử lý khi không đủ căn cứ | Báo chưa tìm thấy hoặc tài liệu mâu thuẫn; đề nghị chuyển ban quản lý | MVP |
| Q07 | Ghi nhận chất lượng câu trả lời | Cư dân đánh dấu hữu ích/chưa đúng để cải thiện kho kiến thức | Sau MVP |

### Nhóm nội dung

- Nội quy sinh hoạt: tiếng ồn, thú cưng, sử dụng khu vực chung.
- Tiện ích: điều kiện sử dụng, thời gian hoạt động, cách đăng ký.
- Thủ tục: chuyển đồ, sửa chữa căn hộ, đăng ký khách và phương tiện.
- Phí và dịch vụ: giải thích thông tin có trong tài liệu; tra cứu công nợ cá nhân nằm ngoài MVP.

### Luồng mẫu

**Cư dân:** “Muốn sửa căn hộ thì đăng ký thế nào?”

**Agent:** Xác định khu/tòa → tìm tài liệu còn hiệu lực → tóm tắt các bước và giấy tờ có trong tài liệu → dẫn nguồn → trả lời câu hỏi tiếp theo.

Không tự bổ sung giờ thi công, mức phí hoặc giấy tờ nếu nguồn không có thông tin.

## 3. Hướng 2 — Tiếp nhận và phân loại phản ánh cư dân

### Nhu cầu

Cư dân chỉ cần mô tả vấn đề. Agent hỗ trợ chuẩn hóa phản ánh để ban quản lý biết **chuyện gì xảy ra, ở đâu, mức độ ảnh hưởng và ai cần xử lý**.

### Tính năng đề xuất

| Mã | Tính năng | Hành vi mong muốn | Phạm vi |
|---|---|---|---|
| P01 | Tiếp nhận phản ánh qua chat | Ghi nhận mô tả tự nhiên của cư dân | MVP |
| P02 | Bổ sung thông tin còn thiếu | Hỏi ngắn gọn về vị trí, thời gian, tình trạng hiện tại và mức ảnh hưởng | MVP |
| P03 | Phân loại phản ánh | Gán nhóm chính và nhãn phụ nếu có nhiều vấn đề | MVP |
| P04 | Đề xuất độ ưu tiên | Gán mức ưu tiên kèm lý do dựa trên nguy cơ, phạm vi ảnh hưởng và tính cấp bách | MVP |
| P05 | Tra cứu quy trình bằng RAG | Tìm hướng dẫn tiếp nhận, đơn vị phụ trách và quy định liên quan từ nguồn đã duyệt | MVP |
| P06 | Tóm tắt và tạo phiếu | Cho cư dân kiểm tra nội dung trước khi gửi; trả mã phiếu sau khi lưu thành công | MVP |
| P07 | Chuyển bộ phận xử lý | Định tuyến theo bảng phân công; trường hợp chưa rõ chuyển ban quản lý kiểm tra | MVP |
| P08 | Tra cứu trạng thái | Hiển thị trạng thái thực tế từ hệ thống phiếu của đúng cư dân | Sau MVP |
| P09 | Đính kèm ảnh và phát hiện trùng | Bổ sung bằng chứng, gợi ý các phản ánh có thể cùng một sự cố | Sau MVP |

### Nhóm phân loại ban đầu

| Nhóm | Ví dụ phản ánh | Bộ phận nhận đề xuất |
|---|---|---|
| An ninh, an toàn | Người lạ có hành vi đáng ngờ, mất tài sản, xô xát | An ninh / ban quản lý |
| Kỹ thuật, hạ tầng | Thang máy lỗi, mất điện khu chung, rò nước | Kỹ thuật |
| Vệ sinh, môi trường | Rác tồn đọng, mùi khó chịu, côn trùng | Vệ sinh / môi trường |
| Tiếng ồn, sinh hoạt | Nhạc lớn, thi công gây ồn, sử dụng khu chung sai quy định | Ban quản lý / an ninh |
| Tiện ích, dịch vụ | Thiết bị phòng gym hỏng, phản ánh chất lượng dịch vụ | Vận hành tiện ích / CSKH |
| Phí, thủ tục | Thắc mắc khoản thu, hồ sơ chưa được xử lý | CSKH / kế toán |
| Khác hoặc chưa rõ | Nội dung không đủ thông tin hoặc chưa có nhóm phù hợp | Ban quản lý kiểm tra |

### Mức ưu tiên đề xuất

| Mức | Tiêu chí | Ví dụ | Hành vi của agent |
|---|---|---|---|
| P0 — Khẩn cấp | Có dấu hiệu nguy hiểm tức thời đối với con người | Có người mắc kẹt trong thang máy, báo khói/cháy | Hiển thị kênh khẩn cấp đã được cấu hình ngay; ưu tiên chuyển người trực, không chờ đủ biểu mẫu |
| P1 — Cao | Sự cố đang diễn ra, ảnh hưởng lớn hoặc có nguy cơ tăng nhanh | Nước tràn hành lang, mất điện toàn tầng | Ưu tiên chuyển bộ phận phụ trách và nêu rõ phạm vi ảnh hưởng |
| P2 — Thông thường | Cần xử lý nhưng chưa có dấu hiệu nguy hiểm tức thời | Đèn hành lang hỏng tại một vị trí, rác chưa thu gom | Tạo phiếu vào hàng đợi xử lý thông thường |
| P3 — Thấp | Góp ý cải thiện, không gây gián đoạn hiện tại | Đề xuất thêm ghế ở khu sinh hoạt | Ghi nhận để ban quản lý tổng hợp và phản hồi |

**Nguyên tắc:** Không suy ra độ ưu tiên chỉ từ nhóm phản ánh hoặc giọng điệu bức xúc. Ví dụ, thang máy hỏng nhưng không có người bên trong khác với thang máy có người mắc kẹt. Nếu thiếu thông tin quyết định mức độ nguy hiểm, hỏi ngay một câu làm rõ. Ban quản lý có thể sửa phân loại và ưu tiên; thời hạn xử lý lấy từ cấu hình đã duyệt, không tự hứa với cư dân.

### Thông tin trong một phiếu

- Mã phiếu, thời gian tiếp nhận và người gửi theo tài khoản đăng nhập.
- Nội dung gốc và bản tóm tắt vấn đề.
- Khu/tòa, tầng hoặc vị trí cụ thể.
- Thời điểm xảy ra, tình trạng hiện tại và đối tượng bị ảnh hưởng.
- Nhóm phản ánh, mức ưu tiên đề xuất và lý do.
- Bộ phận phụ trách, trạng thái chuyển giao.
- Nguồn quy trình/quy định đã tra cứu, nếu có.

### Luồng mẫu

**Cư dân:** “Hành lang tầng 12 có nước chảy nhiều từ nãy đến giờ.”

**Agent:** Hỏi tòa và vị trí cụ thể, tình trạng nước hiện tại → phân loại kỹ thuật → đề xuất ưu tiên theo mức ảnh hưởng → tra quy trình và bộ phận nhận → cho cư dân kiểm tra bản tóm tắt → gửi phiếu → trả mã phiếu khi hệ thống xác nhận thành công.

Nếu cư dân hỏi thêm “quy định xử lý việc này thế nào?”, agent chuyển sang hỏi đáp RAG nhưng vẫn giữ ngữ cảnh phản ánh.

## 4. Dữ liệu và khả năng dùng chung

| Thành phần | Cần chuẩn bị |
|---|---|
| Kho kiến thức RAG | Nội quy, hướng dẫn, thông báo, quy trình tiếp nhận đã được ban quản lý duyệt |
| Thông tin tài liệu | Tên, phiên bản, ngày hiệu lực, phạm vi khu/tòa, mục/trang và liên kết nguồn |
| Cấu hình xử lý | Nhóm phản ánh, tiêu chí ưu tiên, bộ phận nhận và kênh liên hệ khẩn cấp đã xác minh |
| Hệ thống phiếu | Khả năng tạo phiếu, ghi nhận chuyển giao và trả mã phiếu; prototype có thể dùng dữ liệu mô phỏng được ghi rõ |
| Phân quyền | Cư dân truy cập dữ liệu của mình; nhân viên truy cập theo phạm vi phụ trách |

RAG dùng để tìm căn cứ trả lời và quy trình. Phân loại và ưu tiên dùng mô hình kết hợp tiêu chí cấu hình; việc tạo phiếu và cập nhật trạng thái phải đi qua hệ thống nghiệp vụ. Không coi nội dung phản ánh của cư dân là nguồn quy định.

## 5. Phạm vi demo MVP

- Một giao diện chat với hai lựa chọn: **Hỏi quy định** và **Gửi phản ánh**; cũng nhận diện ý định từ câu nhập tự do.
- Kho tài liệu mẫu của một khu/tòa, có nguồn và thông tin hiệu lực.
- Hỏi đáp quy định kèm trích dẫn; có tình huống không tìm thấy câu trả lời.
- Nhận phản ánh bằng văn bản, hỏi bổ sung, phân loại và đề xuất một trong bốn mức ưu tiên.
- Tạo phiếu trong hệ thống demo và hiển thị danh sách cho ban quản lý, cho phép chỉnh nhóm/ưu tiên.
- Demo cả trường hợp thông thường và khẩn cấp; ghi rõ chuyển giao mô phỏng nếu chưa kết nối vận hành thật.

**Chưa làm trong MVP:** thanh toán, điều khiển thiết bị, tự quyết định xử phạt hoặc bồi thường, phân tích camera, xử lý ảnh, thông báo đa kênh và tích hợp toàn bộ hệ thống cư dân.

## 6. Tiêu chí kiểm tra bản đầu

| Hạng mục | Cách kiểm tra |
|---|---|
| Hỏi đáp đúng nguồn | Câu trả lời được tài liệu hỗ trợ, trích dẫn truy cập được và đúng khu/tòa |
| Không có căn cứ | Khi tài liệu thiếu hoặc mâu thuẫn, agent nêu rõ giới hạn và chuyển người phụ trách |
| Phân loại và ưu tiên | So sánh với bộ tình huống đã được ban quản lý gán nhãn; kiểm tra riêng các ca khẩn cấp |
| Thu thập thông tin | Phiếu có đủ nội dung và vị trí để xử lý; không hỏi lại thông tin đã cung cấp |
| Tạo và chuyển phiếu | Chỉ báo thành công khi hệ thống xác nhận; gửi lại không tạo phiếu trùng |
| Phân quyền | Cư dân không đọc được phiếu hoặc thông tin riêng của cư dân khác |

Các ngưỡng nghiệm thu cụ thể sẽ được chốt sau khi có bộ dữ liệu đánh giá và phản hồi của ban quản lý.
