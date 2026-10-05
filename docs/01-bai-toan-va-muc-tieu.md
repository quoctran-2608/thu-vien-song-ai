# 1. Bài toán, mục tiêu và nguyên tắc nền tảng

## 1.1. Bài toán thực tế

Kho tài liệu có thể chứa:

- PDF có lớp chữ tốt;
- PDF có chữ nhưng mã hóa lỗi;
- PDF chỉ là ảnh quét;
- PDF hỗn hợp chữ và ảnh;
- EPUB;
- MOBI;
- nhiều ấn bản;
- nhiều bản dịch;
- tài liệu nhiều ngôn ngữ;
- trang mờ, cong, lệch;
- văn bản hai cột;
- chú thích, bảng và hình.

Nếu chỉ lấy chữ, cắt thành các đoạn bằng nhau rồi tìm theo véc-tơ, hệ thống sẽ nhanh chóng gặp các vấn đề:

1. mất cấu trúc sách;
2. khó truy đúng trang và đúng ấn bản;
3. lấy được đoạn gần nghĩa nhưng không thật sự chứng minh kết luận;
4. đưa quá nhiều chữ cho AI;
5. AI phải đọc lại những thứ đã nghiên cứu;
6. thay công cụ có thể kéo theo việc phải xây lại dữ liệu.

## 1.2. Mục tiêu thật sự

Hệ thống phải giúp AI:

### Tìm đúng

Tìm đúng tác phẩm, ấn bản, chương, mục, trang và đoạn.

### Hiểu cấu trúc

Biết một đoạn thuộc đâu và có quan hệ thế nào với phần còn lại.

### Tổng hợp nhiều nguồn

Có thể nghiên cứu hàng chục sách mà không phải đưa nguyên hàng chục sách vào một lần hỏi.

### Tích lũy hiểu biết

Kết quả nghiên cứu tốt hôm nay phải giúp lần nghiên cứu sau tốt hơn.

### Kiểm chứng được

Mọi khẳng định quan trọng phải lần ngược được về bằng chứng.

## 1.3. Hiến pháp của hệ thống

### AI không phải là nguồn

AI là công cụ đọc, tìm, so sánh và suy luận. Quyền uy của kết luận phải đến từ bằng chứng.

### Nguồn phải bất biến

Không sửa file nguồn hoặc văn bản thô của một lần xử lý.

### Kho dữ liệu chuẩn phải độc lập với công cụ

RAGFlow, QMD, PageIndex, Qdrant hay mô hình AI đều có thể thay mà không làm mất dữ liệu cốt lõi.

### Kết quả tìm được chưa phải bằng chứng

Một kết quả tìm kiếm chỉ là ứng viên. Bằng chứng phải được kiểm tra về nguồn, vị trí, ngữ cảnh và mức hỗ trợ.

### Trích dẫn có thật chưa chắc chứng minh được khẳng định

Hệ thống phải kiểm tra quan hệ giữa điều AI nói và đoạn được dẫn.

### Không đủ bằng chứng là một kết quả hợp lệ

AI được phép kết luận “chưa đủ dữ liệu” hoặc “các nguồn mâu thuẫn”.

## 1.4. Các yêu cầu phi chức năng

- chi phí nhập liệu thấp;
- không nhận dạng chữ từ ảnh khi không cần;
- có thể chạy phần lớn tại máy;
- không bị khóa vào một nhà cung cấp;
- có lịch sử thay đổi;
- có bộ kiểm thử;
- xử lý gia tăng, không làm lại toàn bộ khi chỉ thêm vài tài liệu;
- có thể phục hồi sau lỗi.

## 1.5. Điều không lấy làm mục tiêu

- Không cố nhét toàn bộ thư viện vào trọng số của mô hình AI.
- Không xây đồ thị tri thức toàn kho ngay từ đầu.
- Không coi câu trả lời nghe hợp lý là đủ tốt.
- Không xem cơ sở dữ liệu véc-tơ là nguồn chân lý.
