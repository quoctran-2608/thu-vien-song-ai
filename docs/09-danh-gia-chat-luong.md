# 9. Đánh giá chất lượng

## 9.1. Vì sao cần bộ đánh giá?

Một hệ RAG có thể trả lời nghe rất hay dù truy hồi sai. Vì vậy phải đo từng tầng riêng.

## 9.2. Bộ thử OCR

Chọn 200–500 trang đại diện:

- PDF text sạch;
- mã hoá lỗi;
- scan đẹp;
- scan mờ;
- giấy vàng;
- lệch/cong;
- hai cột;
- nhiều chú thích;
- bảng;
- nhiều ngôn ngữ.

Đo:

- tỷ lệ sai ký tự;
- lỗi dấu tiếng Việt;
- thứ tự đọc;
- nhận diện tiêu đề;
- gắn số trang;
- tốc độ;
- tài nguyên.

## 9.3. Bộ thử truy hồi

Tạo 100–300 câu hỏi có đáp án chuẩn:

```yaml
cau_hoi: "Tác giả A nói gì về X?"
nguon_dung:
  sach: book_328
  trang: 71-74
```

Đo:

- Recall@5;
- Recall@10;
- MRR;
- nDCG;
- tỷ lệ lấy đúng trang.

So sánh lần lượt:

1. chỉ tìm chữ;
2. chỉ tìm ý nghĩa;
3. tìm kết hợp;
4. tìm kết hợp + xếp hạng lại;
5. thêm phân tầng.

## 9.4. Bộ thử trích dẫn

Kiểm tra:

- câu trả lời có dẫn đúng nguồn không;
- nguồn có thật sự hỗ trợ khẳng định không;
- trang có đúng không;
- OCR thấp confidence có được kiểm tra lại không.

## 9.5. Bộ thử Bộ não thứ hai

Kiểm tra:

- Claim thiếu nguồn;
- Claim suy luận bị gắn nhầm là trích xuất;
- trang trùng;
- liên kết hỏng;
- mâu thuẫn bị che mất;
- cập nhật mới có làm mất thông tin cũ không.

## 9.6. Kiểm tra hồi quy

Mỗi khi thay:

- parser;
- OCR;
- chunker;
- embedding;
- reranker;
- RAG engine;

phải chạy lại bộ thử. Không chấp nhận “model mới hơn” nếu chỉ số trên dữ liệu thực giảm.
