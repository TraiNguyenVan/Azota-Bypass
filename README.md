# AZOTA HUYNH DUONG DEV AUTO ĐÁP ÁN (v2.1)

## Giới thiệu

Script Tampermonkey này có tên "AZOTA HUYNH DUONG DEV AUTO ĐÁP ÁN" (phiên bản 2.0) được thiết kế để tự động hóa việc trả lời câu hỏi trên nền tảng Azota.vn. Nó sử dụng Gemini API của Google (thông qua một API Key do người dùng cung cấp) để phân tích câu hỏi và đưa ra câu trả lời dựa trên ngữ cảnh được cung cấp.

**Lưu ý quan trọng**: Script này có tính năng tự động trả lời (auto-answer) có thể dẫn đến việc tài khoản Azota bị khóa nếu bị phát hiện. Người dùng cần chấp nhận rủi ro trước khi sử dụng tính năng này.

## Các tính năng chính

* **Tự động trả lời câu hỏi**: Tự động phân tích và trả lời các câu hỏi trắc nghiệm và tự luận.
* **Gợi ý đáp án**: Hiển thị gợi ý đáp án cho câu hỏi đang hiển thị, kèm theo giải thích ngắn gọn (đối với câu trắc nghiệm).
* **Bảng điều khiển có thể kéo**: Bảng điều khiển script có thể được kéo và thả trên màn hình.
* **Bộ nhớ ngữ cảnh (thử nghiệm)**: Lưu lại lịch sử câu hỏi và câu trả lời để sử dụng làm ngữ cảnh cho các câu hỏi tự luận tiếp theo (tối đa 5 câu).
* **Ghi log chi tiết**: Ghi lại các hoạt động của script, bao gồm câu hỏi, câu trả lời, lỗi, v.v.
* **Tùy chỉnh API Key**: Cho phép người dùng nhập và thay đổi Gemini API Key.
* **Tùy chỉnh giao diện**: Giao diện người dùng thân thiện, có thể thu gọn/mở rộng, và hiển thị thông tin trạng thái.
* **Hỗ trợ câu trắc nghiệm và tự luận**: Script hỗ trợ cả hai loại câu hỏi phổ biến trên Azota.
* **Cảnh báo rủi ro**: Hiển thị cảnh báo rủi ro trước khi sử dụng tính năng tự động trả lời.

## Cách sử dụng

1.  **Cài đặt Tampermonkey**: Cài đặt tiện ích mở rộng Tampermonkey cho trình duyệt của bạn (Chrome, Firefox, v.v.).
2.  **Cài đặt script**: Sao chép mã script và dán vào trình soạn thảo script của Tampermonkey.
3.  **Nhập Gemini API Key**: Nhấn nút "API Key" trên bảng điều khiển và nhập API Key của bạn.
4.  **Sử dụng tính năng**:
    * Nhấn nút "Bắt đầu Auto (Huỳnh Dương)" để tự động trả lời tất cả câu hỏi.
    * Nhấn nút "Huỳnh Dương gợi ý" để xem gợi ý đáp án cho câu hỏi đang hiển thị.
    * Nhấn nút "Hiện Log" để xem log chi tiết.
5.  **Cảnh báo**: Cần chấp nhận rủi ro trước khi sử dụng auto-answer.

## Tùy chọn nhà cung cấp AI (v2.1)

Nút **⚙ AI Provider** ở góc dưới bên phải trang Azota mở bảng cấu hình:

* **Google Gemini** (mặc định)
  * **Model**: để trống sẽ dùng mặc định của script (`gemini-2.0-flash`). Có thể nhập `gemini-1.5-pro`, `gemini-2.5-flash`, ... (tự bỏ tiền tố `models/` nếu có).
  * API Key vẫn nhập qua nút "API Key" của script như trước.
* **OpenAI-compatible endpoint**
  * **Base URL**: `https://api.openai.com/v1`, `https://openrouter.ai/api/v1`, `https://api.groq.com/openai/v1`, `http://localhost:11434/v1` (Ollama), ...
  * **Model**: ví dụ `gpt-4o-mini`, `llama3.1`, `openai/gpt-4o-mini`.
  * **API Key**: gửi dạng `Authorization: Bearer ...`.

Cấu hình được lưu cục bộ bằng `GM_setValue` và áp dụng ngay ở request kế tiếp, không cần tải lại trang. Script chuyển request Gemini `generateContent` sang `POST {Base URL}/chat/completions` rồi dịch kết quả về lại đúng dạng `candidates[0].content.parts[0].text` mà script đang đọc.

Để gọi được endpoint tùy chọn, header userscript có thêm `// @connect *`.

## Yêu cầu

* Trình duyệt có cài đặt Tampermonkey.
* Gemini API Key hợp lệ (hoặc API Key của endpoint OpenAI-compatible nếu dùng chế độ đó).
* Kết nối Internet ổn định.

## Lưu ý

* Sử dụng script này có thể vi phạm điều khoản dịch vụ của Azota.
* Tính năng tự động trả lời có thể không chính xác 100%.
* Script này được phát triển với mục đích hỗ trợ học tập, người dùng nên sử dụng một cách có trách nhiệm.
* Script này chỉ hỗ trợ các câu hỏi phổ biến trên azota, các câu hỏi có định dạng đặc biệt có thể không được xử lý chính xác.
* Người dùng nên sử dụng tính năng "Huỳnh Dương gợi ý" để giảm thiểu rủi ro.

## Cập nhật

* **v2.1**: Thêm tùy chọn nhà cung cấp AI (Google Gemini hoặc endpoint OpenAI-compatible) và cho phép đổi model Gemini.
* **v2.0**: Thêm bộ nhớ ngữ cảnh cho câu hỏi tự luận, cải thiện độ chính xác, sửa lỗi và tối ưu hóa giao diện.
## HUYNH DUONG DEV
