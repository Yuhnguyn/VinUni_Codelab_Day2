# 03 — AI Log & Reflection (Lab 02: AI Product Scoping)

> Phản ánh cá nhân về quá trình dùng AI (Claude) làm "thought-partner" trong buổi lab
> AI Product Scoping — Vin Smart Future. Viết trung thực: AI giúp gì, AI sai/thiếu ở
> đâu, và tôi đã sửa prompt/ranh giới ra sao để đạt kết quả chuẩn.

---

## 1. Tôi đã dùng AI như thế nào trong buổi lab

Tôi dùng Claude (Claude Code) xuyên suốt cả 2 phần của lab:

1. **Đọc & tổng hợp yêu cầu:** Nhờ AI đọc toàn bộ repo (`README.md`, `01-worksheet.md`,
   `02-deliverable-example.md`, `03-inspiration-kit.md`, `starter-code/prompt_prototype.py`,
   `autograder/autograder.py`) và tóm tắt lại thành một hướng làm rõ ràng: 5 file cần nộp,
   ai chấm điểm gì, autograder kiểm tra chính xác những keyword/hàm nào.
2. **Hoàn thiện `01-worksheet.md`:** Nhờ AI điền Phase 1–5 (SCAN, Quick Cards, Deep-Dive,
   Evaluate) dựa trên một bài toán cụ thể.
3. **Hoàn thiện `starter-code/prompt_prototype.py`:** Nhờ AI viết `SYSTEM_PROMPT`, implement
   `evaluate_prompt()` bằng SDK `google-genai`, và bổ sung `ADVERSARIAL_TESTS`.

## 2. AI đã giúp gì (điểm tốt)

* **Đọc nhanh & chính xác cấu trúc chấm điểm:** AI phát hiện chính xác 5 tiêu chí autograder
  chấm code (`--check-code-1..5`) và 3 keyword bắt buộc trong `SYSTEM_PROMPT`
  (`draft_only`, `5%`, `dispatch_mobile_charger`) — những chi tiết dễ bị bỏ sót nếu tôi tự
  đọc lướt file `autograder.py` dài gần 430 dòng.
* **Code đúng cấu trúc kỹ thuật:** Phần `evaluate_prompt()` được viết đúng theo SDK mới
  `google-genai` (dùng `client.models.generate_content` + `system_instruction`), và AI đã
  tự kiểm tra bằng cách parse AST + chạy thử để xác nhận không lỗi cú pháp trước khi báo
  hoàn thành — thay vì chỉ nói suông "đã xong".
* **Tổ chức lại nội dung theo đúng khuôn mẫu 6-field / AI-Fit Matrix / Fallback** một cách
  nhất quán, giúp tiết kiệm thời gian trình bày.

## 3. AI đã sai/thiếu ở đâu — và tôi đã sửa ra sao

Đây là phần quan trọng nhất, vì lỗi này không phải "hallucination" thông tin sai, mà là
**thiếu ranh giới rõ ràng ngay từ đầu** — rất giống chủ đề Operational Boundary mà chính
bài lab đang dạy:

* **Vấn đề:** Khi tôi yêu cầu "hoàn thiện worksheet", AI đã chọn *đúng* bài toán và gần như
  *đúng* cách trình bày trong `02-deliverable-example.md` (kịch bản Xanh SM xử lý sự cố pin
  thực địa) — chỉ đổi vài con số. Vì file ví dụ được ghi rõ trong README là "mẫu tham khảo
  Xuất Sắc", AI đã hiểu nhầm ý đồ và dùng nó như một "đáp án" để mô phỏng lại, thay vì chỉ
  tham khảo *cấu trúc trình bày* rồi tự đề xuất một bài toán mới.
* **Cách tôi phát hiện:** Tôi đọc lại nội dung và nhận ra nó giống ví dụ mẫu đến mức không
  còn là ý tưởng của nhóm mình — nếu nộp nguyên như vậy sẽ bị đánh giá là thiếu tư duy gốc
  (không đạt tinh thần "Problem First" của rubric G2/G4).
* **Cách tôi sửa ranh giới:** Tôi nói rõ với AI: *"file 02 chỉ là bài mẫu tham khảo cấu trúc
  thôi"* — tức là ra một ranh giới tường minh thay vì để AI tự suy đoán. Sau phản hồi đó, AI
  đã đổi hẳn sang một bài toán khác, **lấy trực tiếp từ quan sát thật trong chính repo đang
  làm** (log kỹ thuật một-dòng của `autograder.py` khiến TA phải giải thích tay lặp lại nhiều
  lần) — vừa nguyên bản, vừa có bằng chứng cụ thể thay vì hư cấu.
* **Bài học rút ra:** Prompt mơ hồ ("hoàn thiện file md") không đủ để ngăn AI dùng file mẫu
  làm khuôn nội dung. Ranh giới phải được nói ra tường minh ngay từ đầu ("chỉ tham khảo cấu
  trúc, không copy nội dung/ý tưởng") — đúng là bài học Operational Boundary ở Phase 3/4:
  AI sẽ làm đúng những gì được cho phép/cấm một cách rõ ràng, chứ không tự đoán được ý đồ ẩn
  của người ra đề.

## 4. Điểm cần cẩn trọng khi dùng AI cho phần code (Phase 4)

* AI tự chạy `ast.parse` và import thử module để xác nhận không lỗi cú pháp, nhưng **chưa
  chạy được lệnh gọi API Gemini thật** vì chưa có `GEMINI_API_KEY` hợp lệ trong phiên làm
  việc — tức là các "Verification Checks" (`✅ Rule 1/2 Passed`) trong `prompt_prototype.py`
  mới chỉ được thiết kế đúng logic, chưa được xác nhận bằng kết quả thực tế từ model. Tôi
  cần tự chạy `python3 prompt_prototype.py` với API key thật trước khi tin tưởng hoàn toàn
  là ranh giới đã đứng vững trước 3 adversarial test cases.

## 5. Kết luận

AI là một thought-partner hiệu quả để đọc nhanh, tổng hợp, và viết code đúng khuôn mẫu kỹ
thuật — nhưng không tự nhận ra ranh giới "tham khảo cấu trúc" khác với "sao chép nội dung"
nếu tôi không nói rõ. Bài học lớn nhất của buổi lab, với tôi, không chỉ nằm ở việc scoping
một bài toán AI cho Vingroup, mà còn ở chính trải nghiệm thực hành: **ranh giới (Operational
Boundary) phải được đặt ra tường minh, không thể để AI tự suy đoán** — dù là AI điều phối xe
điện trong bài toán giả lập, hay AI đang hỗ trợ tôi làm chính bài lab này.
