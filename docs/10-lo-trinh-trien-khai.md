# 10. Lộ trình triển khai

## Giai đoạn 0 — Thử nghiệm dữ liệu thật

Chọn 200–500 trang đại diện cho những tình huống khó khác nhau.

Làm:

- thử các cách đọc PDF;
- thử nhận dạng chữ;
- kiểm tra EPUB/MOBI;
- xác định quy tắc chọn trang cần nhận dạng chữ;
- xây 100–300 câu hỏi chuẩn.

Mục tiêu:

> biết dữ liệu thật khó ở đâu trước khi xây lớn.

## Bản kỹ thuật 0.1 — Nguồn và bằng chứng

Làm:

- kho nguồn bất biến;
- SHA-256;
- mô hình tác phẩm/ấn bản/trang;
- lấy chữ trực tiếp;
- nhận dạng chữ theo tầng;
- chống trùng;
- tìm theo chữ;
- tìm theo ý nghĩa;
- xếp hạng lại;
- dẫn nguồn trang;
- bộ kiểm thử cơ bản.

Chưa làm:

- đồ thị toàn kho;
- tự động hóa Bộ não thứ hai toàn diện.

## Bản kỹ thuật 0.2 — Bộ não thứ hai

Làm:

- Markdown;
- tìm trong Markdown;
- trang tri thức;
- sổ khẳng định;
- liên kết giữa các trang;
- Git;
- quy tắc dành cho AI.

Chưa cho AI sửa tự động hoàn toàn.

## Bản kỹ thuật 0.3 — Nghiên cứu sâu và tự bảo trì

Làm:

- gói bằng chứng;
- không gian nghiên cứu;
- kiểm tra câu trích;
- kiểm tra khẳng định;
- tìm bằng chứng phản bác;
- đề xuất;
- một bộ ghi;
- cập nhật toàn vẹn;
- chống trùng;
- phát hiện mâu thuẫn;
- kiểm tra wiki.

## Bản kỹ thuật 0.4 — Điều phối và đọc sâu

Làm:

- bộ chọn cách xử lý câu hỏi;
- PageIndex cho đọc sâu;
- bộ chuyển tiếp RAGFlow hoặc công cụ tương đương;
- tối ưu gói bằng chứng;
- MCP ổn định.

## Bản kỹ thuật 0.5 — Quan hệ phức tạp

Chỉ khi có bài toán thực sự cần:

- đồ thị quan hệ;
- LightRAG hoặc công cụ tương đương;
- Graphiti cho tri thức thay đổi theo thời gian;
- các hệ trí nhớ tác tử như Cognee nếu chứng minh được giá trị.

## Mốc phần mềm sản xuất 1.0 — tương lai

> Mốc này **khác** với “tài liệu/đặc tả v1.0” hiện tại của repo. Đây là phiên bản phần mềm tương lai sau khi các bản kỹ thuật 0.x đạt tiêu chí chất lượng.

Hoàn thiện:

- giao diện web;
- phân quyền;
- sao lưu;
- phục hồi;
- giám sát;
- kiểm thử tự động;
- tài liệu vận hành;
- chính sách nâng cấp công cụ.

## Thứ tự ưu tiên

```text
1. Đúng nguồn
2. Đúng cấu trúc
3. Đúng trang
4. Tìm đúng
5. Trích dẫn đúng
6. Giảm lượng chữ AI phải đọc
7. Tích lũy hiểu biết
8. Tự động hóa
9. Đồ thị và tính năng nâng cao
```

Không đảo ngược thứ tự này.


## Bắt đầu thực thi

Để chuyển lộ trình này thành công việc cụ thể, xem:

> [Hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1](17-huong-dan-bat-dau-trien-khai-v0.1.md)
