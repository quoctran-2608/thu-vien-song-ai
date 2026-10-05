# Quy tắc dành cho tác tử AI

Tài liệu này là “hiến pháp vận hành” của các tác tử AI làm việc với Thư Viện Sống AI.

## 1. AI không phải là nguồn

Không dùng kiến thức có sẵn trong mô hình như bằng chứng mà không nói rõ.

Nguồn và bằng chứng phải đến từ kho dữ liệu được xác định hoặc nguồn bên ngoài được người dùng cho phép.

## 2. Nguồn gốc là bất biến

- Không sửa PDF, EPUB, MOBI, ảnh trang hoặc văn bản thô đã lưu làm nguồn.
- Mọi bản làm sạch tồn tại song song với bản thô.
- Thay cách trích xuất phải tạo phiên bản xử lý mới.

## 3. Kết quả tìm được chưa phải bằng chứng

Một đoạn do hệ tìm kiếm trả về chỉ là ứng viên.

Trước khi dùng cho kết luận quan trọng, phải kiểm tra:

- đúng nguồn;
- đúng vị trí;
- đủ ngữ cảnh;
- thật sự hỗ trợ khẳng định.

## 4. Không biến suy luận thành sự kiện

Phải phân biệt:

- `TRICH_XUAT`: nguồn nói trực tiếp;
- `SUY_LUAN`: AI rút ra;
- `TONG_HOP`: AI kết hợp nhiều nguồn.

Đồng thời phải theo dõi tình trạng bằng chứng:

- được hỗ trợ;
- có tranh luận;
- hỗ trợ yếu;
- chưa đủ dữ liệu;
- chưa biết;
- bị phản bác.

## 5. Khẳng định quan trọng phải có nguồn

Khẳng định đáng tin phải truy được tối thiểu tới:

- mã tài liệu;
- ấn bản;
- chương/mục nếu có;
- trang hoặc vị trí tương đương;
- đoạn bằng chứng;
- phiên bản nguồn.

## 6. Trích dẫn thật chưa chắc chứng minh được khẳng định

Không chỉ kiểm tra citation có tồn tại.

Phải kiểm tra đoạn được dẫn có thực sự hỗ trợ điều đang nói.

## 7. Không tự giải quyết mâu thuẫn bằng cách xóa một bên

Nếu hai nguồn mâu thuẫn:

- ghi rõ cả hai;
- đánh dấu trạng thái mâu thuẫn;
- không tự chọn người thắng nếu chưa đủ căn cứ;
- không biến bất đồng thành một kết luận chắc chắn.

## 8. “Không tìm thấy” không đồng nghĩa “không tồn tại”

Nếu không tìm thấy, phải nói rõ phạm vi đã khảo sát.

Không biến giới hạn của kho dữ liệu thành khẳng định tuyệt đối.

## 9. Tìm bằng chứng phản bác trong nghiên cứu sâu

Sau khi có kết luận sơ bộ quan trọng, chủ động tìm:

- ngoại lệ;
- nguồn trái chiều;
- trường hợp giới hạn kết luận.

Đặc biệt với các từ “tất cả”, “luôn”, “duy nhất”, “không có”, “sớm nhất”.

## 10. Mọi thay đổi Bộ não thứ hai phải qua đề xuất

Tác tử nghiên cứu không sửa trực tiếp nội dung chính thức.

Quy trình:

1. tạo đề xuất;
2. liệt kê file cần sửa;
3. liệt kê khẳng định mới/thay đổi;
4. gắn nguồn;
5. chạy kiểm tra;
6. bộ ghi duy nhất áp dụng thay đổi;
7. tạo Git commit bằng tiếng Việt.

## 11. Cập nhật phải có tính toàn vẹn

Nếu một đề xuất sửa nhiều file:

> hoặc ghi thành công toàn bộ, hoặc không ghi gì.

Không để wiki ở trạng thái nửa cập nhật.

## 12. Không đọc quá mức cần thiết

Ưu tiên:

1. chỉ mục/tóm tắt;
2. Bộ não thứ hai;
3. đoạn bằng chứng;
4. chương;
5. trang gốc;
6. toàn bộ tài liệu chỉ khi thật sự cần.

Đây là nguyên tắc **đọc theo độ sâu thích ứng**.

## 13. Không tạo đồ thị chỉ vì có thể

Chỉ tạo quan hệ hoặc bật bộ máy đồ thị khi có bài toán thực sự cần.

## 14. Không tiêu hóa toàn bộ thư viện trước

Toàn bộ nguồn có thể được lập chỉ mục, nhưng Bộ não thứ hai chỉ phát triển sâu theo nhu cầu sử dụng.

## 15. Khi thay bộ máy phải chạy bộ đánh giá

Thay trình đọc, nhận dạng chữ, cách chia đoạn, mô hình tìm theo ý nghĩa, bộ xếp hạng hoặc công cụ RAG phải chạy lại bộ kiểm thử.

Không nâng cấp chỉ vì công cụ mới hơn.

## 16. Giữ tiếng Việt rõ ràng trong tài liệu

Ưu tiên tiếng Việt.

Nếu phải dùng thuật ngữ kỹ thuật tiếng Anh, lần đầu xuất hiện phải giải thích bằng tiếng Việt.

Không viết kiểu pha trộn khó đọc khi đã có cách nói tiếng Việt rõ ràng.

## 17. Quy tắc cao nhất

> **Nguồn sống lâu hơn bản tóm tắt. Bằng chứng sống lâu hơn suy luận. Dữ liệu chuẩn sống lâu hơn công cụ.**
