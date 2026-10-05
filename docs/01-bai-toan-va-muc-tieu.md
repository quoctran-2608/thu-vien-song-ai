# 1. Bài toán và mục tiêu

## 1.1. Bài toán thực tế

Kho tài liệu có thể chứa đồng thời:

- PDF có lớp chữ tốt;
- PDF có lớp chữ nhưng mã hoá lỗi;
- PDF scan từng trang;
- PDF hỗn hợp chữ và ảnh;
- EPUB;
- MOBI;
- sách nhiều ngôn ngữ;
- sách cũ, mờ, lệch, cong trang;
- tài liệu có nhiều chú thích, nhiều cột, bảng, hình.

Nếu chỉ “chuyển tất cả thành chữ rồi nhét vào vector database”, hệ thống sẽ nhanh chóng gặp bốn vấn đề:

1. mất cấu trúc sách;
2. khó truy nguồn;
3. tìm kiếm trả nhiều đoạn gần giống nhưng không đúng ý;
4. AI phải đọc quá nhiều context, gây tốn token và dễ nhiễu.

## 1.2. Mục tiêu thật sự

Hệ thống phải giúp AI làm được năm việc:

### Tìm đúng

Tìm đúng sách, đúng chương, đúng đoạn, đúng trang.

### Hiểu được cấu trúc

AI biết một đoạn thuộc chương nào, quan hệ với mục nào và nằm trong ấn bản nào.

### Tổng hợp được nhiều nguồn

Có thể so sánh hàng chục sách mà không phải đưa nguyên hàng chục sách vào context.

### Tích lũy được hiểu biết

Một câu hỏi nghiên cứu tốt hôm nay phải làm hệ thống thông minh hơn ngày mai, thay vì mất đi khi đóng cuộc trò chuyện.

### Kiểm chứng được

Bất cứ nhận định quan trọng nào cũng có thể quay lại đúng nguồn và trang để kiểm tra.

## 1.3. Các yêu cầu phi chức năng

- Chi phí nhập liệu thấp.
- Không dùng OCR hoặc LLM lớn khi không cần.
- Có thể chạy phần lớn tại máy.
- Không bị khoá vào một nhà cung cấp.
- Có thể thay embedding, reranker, vector database, RAG engine.
- Có lịch sử thay đổi rõ ràng.
- Có bộ kiểm thử chất lượng.
- Có khả năng xử lý gia tăng: chỉ xử lý tài liệu mới hoặc phần thay đổi.

## 1.4. Điều không nên lấy làm mục tiêu

Không cố làm một AI “nhớ toàn bộ sách trong trọng số mô hình”. Fine-tuning không thay thế được kho nguồn có dẫn trang.

Không cố xây graph toàn bộ ngay từ đầu. Graph chỉ có giá trị nếu phục vụ loại câu hỏi cần quan hệ phức tạp.

Không coi “câu trả lời nghe hợp lý” là thước đo chất lượng. Thước đo phải là khả năng tìm đúng bằng chứng và truy nguồn.
