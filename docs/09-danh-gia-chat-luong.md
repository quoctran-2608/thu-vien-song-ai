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

Có thể dùng các chỉ số kỹ thuật sau, nhưng phải hiểu chúng bằng ý nghĩa thực tế:

- **Recall@5 / Recall@10 — tỷ lệ tìm thấy:** trong 5 hoặc 10 kết quả đầu, hệ thống có đưa nguồn đúng vào hay không.
- **MRR — thứ hạng đối ứng trung bình:** nguồn đúng xuất hiện càng sớm thì điểm càng cao.
- **nDCG — chất lượng thứ hạng có trọng số:** đánh giá thứ tự kết quả khi có nhiều mức độ liên quan khác nhau.
- **Precision — độ chính xác của tập kết quả:** trong những kết quả được trả về, bao nhiêu là đúng/liên quan.
- **F1 — điểm cân bằng:** kết hợp độ chính xác và tỷ lệ tìm thấy thành một chỉ số cân bằng.

Các tên viết tắt được giữ để đối chiếu với công cụ đánh giá, còn quyết định triển khai phải dựa trên ý nghĩa phía trên.

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


## 9.10. Đánh giá theo tuyến đầu 2026

Sau vòng nghiên cứu mới, bộ đánh giá không chỉ kiểm RAG văn bản.

### Tìm kiếm văn bản

So ít nhất:

- BM25;
- tìm theo ý nghĩa;
- tìm kết hợp;
- tìm thưa học được;
- nhiều véc-tơ/tương tác muộn;
- các phương án hợp nhất.

### Tìm trực tiếp từ ảnh trang

Tạo riêng câu hỏi mà đáp án phụ thuộc vào:

- bảng;
- biểu đồ;
- bố cục;
- chú thích;
- vị trí trên trang.

Đo:

- trang đúng có lọt vào top-k không;
- vùng đúng trên trang có được xác định không;
- hợp nhất văn bản + thị giác có tốt hơn từng đường riêng không.

### Tiếng Việt

Chạy:

- phần phù hợp của VN-MTEB;
- ViRE;
- bộ câu hỏi riêng của kho sách.

Không suy ra chất lượng tiếng Việt từ MTEB tiếng Anh.

### Ngữ cảnh dài

Với cùng câu hỏi và cùng ngân sách lượng chữ, so:

- RAG theo đoạn;
- đọc tài liệu giữ nguyên thứ tự/cấu trúc;
- ngữ cảnh dài trực tiếp;
- PageIndex khi phù hợp.

### Chọn số bằng chứng thích ứng

So:

- top-k cố định;
- số đoạn thay đổi theo độ khó/phân bố điểm.

Đo đồng thời:

- độ đúng;
- lượng chữ đưa vào mô hình;
- độ trễ;
- chi phí.

### Nghiên cứu nhiều vòng

Ngoài câu trả lời cuối, đo cả quá trình:

- lượt đầu đã đủ bằng chứng chưa;
- hệ có nhận ra phần còn thiếu không;
- truy vấn tiếp theo có nhắm đúng khoảng trống không;
- có dừng đúng lúc không;
- có tích lũy nhiễu qua các vòng không.

### Tổng hợp dài

Đo tách biệt:

- khẳng định có bằng chứng;
- bằng chứng có hỗ trợ khẳng định;
- **độ phủ**: các khía cạnh quan trọng của câu hỏi đã có đủ bằng chứng chưa;
- phản chứng/mâu thuẫn có được phản ánh không.

---

## 9.11. Nguyên tắc so sánh công bằng

Khi một kỹ thuật mới cạnh tranh với baseline:

- dùng cùng tập dữ liệu;
- cùng tập câu hỏi kín;
- cùng chính sách lọc quyền;
- cùng ngân sách token nếu so RAG/ngữ cảnh dài;
- báo cả chất lượng, độ trễ, bộ nhớ, GPU/CPU và dung lượng chỉ mục;
- không chỉ báo một điểm tổng hợp.

Một kỹ thuật chỉ được đưa vào đường chính khi:

> **cải thiện đủ lớn để bù chi phí, độ phức tạp và rủi ro vận hành mà nó thêm vào.**
