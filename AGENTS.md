# Quy tắc dành cho tác tử AI

Tài liệu này là “hiến pháp vận hành” của các tác tử AI làm việc với Thư Viện Sống AI.

## 1. Nguồn gốc là bất biến

- Không sửa PDF, EPUB, MOBI, ảnh trang hoặc văn bản thô đã lưu làm nguồn.
- Mọi bản làm sạch phải tồn tại song song với bản thô.
- Mọi thay đổi cách trích xuất phải tạo phiên bản xử lý mới, không ghi đè lịch sử.

## 2. Không biến suy luận thành sự kiện

Mỗi khẳng định phải thuộc một trong các loại:

- `TRICH_XUAT`: nội dung có thể xác định trực tiếp từ nguồn.
- `SUY_LUAN`: kết luận do AI tổng hợp từ một hoặc nhiều nguồn.
- `MO_HO`: chưa đủ bằng chứng hoặc các nguồn mâu thuẫn.

Không được ghi `SUY_LUAN` như thể là `TRICH_XUAT`.

## 3. Khẳng định quan trọng phải có nguồn

Một khẳng định đáng tin phải truy ngược được tối thiểu tới:

- mã tài liệu;
- ấn bản;
- chương/mục nếu có;
- số trang hoặc vị trí tương đương;
- đoạn bằng chứng.

## 4. Không tự giải quyết mâu thuẫn bằng cách xoá một bên

Nếu hai nguồn mâu thuẫn:

- ghi rõ cả hai;
- đánh dấu trạng thái mâu thuẫn;
- chỉ đưa ra kết luận khi có quy tắc hoặc bằng chứng rõ ràng;
- nếu chưa chắc, giữ trạng thái `MO_HO`.

## 5. Mọi thay đổi Bộ não thứ hai phải qua đề xuất

Tác tử nghiên cứu không được sửa trực tiếp nội dung chính thức.

Quy trình bắt buộc:

1. tạo đề xuất;
2. liệt kê file cần sửa;
3. liệt kê khẳng định mới/thay đổi;
4. gắn nguồn;
5. chạy kiểm tra;
6. bộ ghi duy nhất mới được áp dụng thay đổi;
7. tạo Git commit bằng tiếng Việt.

## 6. Không đọc quá mức cần thiết

Ưu tiên thứ tự:

1. chỉ mục/tóm tắt;
2. Bộ não thứ hai;
3. đoạn bằng chứng;
4. chương;
5. trang gốc;
6. toàn bộ tài liệu chỉ khi thật sự cần.

## 7. Không tạo graph chỉ vì có thể

Chỉ tạo quan hệ có ích cho một câu hỏi hoặc miền nghiên cứu cụ thể. Không biến toàn bộ kho thành đồ thị nếu chưa có nhu cầu.

## 8. Khi thay động cơ phải chạy bộ đánh giá

Thay parser, OCR, embedding, bộ xếp hạng hay kho tìm kiếm phải chạy lại bộ đo chất lượng. Không nâng cấp chỉ vì model mới hơn.
