# 9. Đánh giá chất lượng

## 9.1. Vì sao đánh giá là một phần của kiến trúc?

Một hệ thống có thể trả lời rất trôi chảy dù:

- lấy sai trang;
- lấy sai ấn bản;
- dẫn nguồn thật nhưng không hỗ trợ kết luận;
- bỏ sót nguồn quan trọng;
- làm hỏng dấu tiếng Việt;
- tóm tắt lệch nguồn.

Vì vậy phải đo từng tầng riêng.

## 9.2. Bộ thử số hóa

Chọn 200–500 trang đại diện:

- PDF chữ sạch;
- mã hóa lỗi;
- scan đẹp;
- scan mờ;
- giấy vàng;
- lệch/cong;
- hai cột;
- nhiều chú thích;
- bảng;
- nhiều ngôn ngữ.

Đo:

- tỷ lệ lỗi ký tự;
- lỗi dấu tiếng Việt;
- thứ tự đọc;
- tiêu đề;
- số trang;
- tốc độ;
- tài nguyên.

## 9.3. Bộ thử tìm kiếm

Tạo 100–300 câu hỏi có đáp án chuẩn.

Ví dụ:

```yaml
cau_hoi: "Tác giả A nói gì về X?"
nguon_dung:
  sach: book_328
  trang: 71-74
```

Đo:

- tỷ lệ tìm thấy nguồn đúng trong nhóm kết quả đầu;
- thứ hạng của nguồn đúng;
- tỷ lệ lấy đúng trang;
- chất lượng sau khi xếp hạng lại.

Có thể dùng các chỉ số kỹ thuật như Recall@5, Recall@10, MRR và nDCG; trong tài liệu cho người dùng cần giải thích chúng bằng tiếng Việt.

## 9.4. So sánh các phương án

Ít nhất so sánh:

1. chỉ tìm theo chữ;
2. chỉ tìm theo ý nghĩa;
3. tìm kết hợp;
4. tìm kết hợp + xếp hạng lại;
5. thêm phân tầng.

Không giả định công nghệ phức tạp hơn luôn tốt hơn.

## 9.5. Bộ thử trích dẫn

Kiểm tra:

- nguồn có thật không;
- đúng ấn bản không;
- đúng trang không;
- câu trích có đúng không;
- đoạn được dẫn có thật sự hỗ trợ khẳng định không.

## 9.6. Bộ thử Bộ não thứ hai

Tìm:

- khẳng định thiếu nguồn;
- suy luận bị biến thành sự kiện;
- trang trùng;
- liên kết hỏng;
- mâu thuẫn bị che mất;
- cập nhật mới làm mất thông tin cũ;
- trang đã lỗi thời.

## 9.7. Bộ thử nghiên cứu sâu

Kiểm tra:

- có lưu phạm vi nghiên cứu không;
- có bằng chứng phản bác không;
- khẳng định yếu có bị ghi quá chắc chắn không;
- kết quả âm có nói rõ phạm vi đã tìm không;
- hồ sơ nghiên cứu có đủ để tái dựng quá trình không.

## 9.8. Kiểm thử hồi quy

Mỗi khi thay:

- trình đọc;
- nhận dạng chữ;
- cách chia đoạn;
- mô hình tìm theo ý nghĩa;
- bộ xếp hạng lại;
- công cụ RAG;
- cách duy trì Bộ não thứ hai;

phải chạy lại cùng bộ câu hỏi chuẩn.

Nếu chất lượng giảm, không triển khai chỉ vì công cụ mới hơn.

## 9.9. Mục tiêu thực tế

Không tuyên bố loại bỏ hoàn toàn sai sót.

Mục tiêu là:

> **sai sót khó lọt qua kiểm tra hơn, dễ phát hiện hơn, truy được nguyên nhân và sửa được.**
