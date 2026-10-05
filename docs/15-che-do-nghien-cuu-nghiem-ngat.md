# 15. Chế độ nghiên cứu nghiêm ngặt

Chế độ này dành cho những câu hỏi mà “câu trả lời nghe hợp lý” là chưa đủ.

Ví dụ:

- nghiên cứu học thuật;
- viết sách;
- đối chiếu văn bản;
- nghiên cứu lịch sử;
- kiểm chứng câu trích;
- so sánh nhiều nguồn;
- kết luận có thể gây ảnh hưởng lớn nếu sai.

Không cần bật toàn bộ quy trình này cho mọi câu hỏi hằng ngày.

## 15.1. Nguyên tắc đầu tiên: AI không phải nguồn

AI có thể:

- tìm;
- đọc;
- dịch;
- so sánh;
- suy luận.

Nhưng phải phân biệt điều nguồn nói với điều AI suy ra.

## 15.2. Có thể chạy trong chế độ kho nguồn đóng

Trong chế độ này:

- chỉ dùng các nguồn đã được cho phép;
- không âm thầm tìm web;
- không dùng trí nhớ có sẵn của mô hình như bằng chứng;
- không tự điền phần còn thiếu.

Nếu không đủ:

> **CHƯA ĐỦ DỮ LIỆU TRONG KHO NGUỒN ĐƯỢC PHÉP**

là một kết quả hợp lệ.

## 15.3. Chuỗi nghiên cứu bắt buộc

```text
CÂU HỎI
↓
XÁC ĐỊNH PHẠM VI
↓
TÌM
↓
LẤY ĐOẠN NGUỒN
↓
LẤY NGỮ CẢNH
↓
KIỂM TRA CÂU TRÍCH
↓
TẠO KHẲNG ĐỊNH
↓
KIỂM TRA KHẲNG ĐỊNH – BẰNG CHỨNG
↓
TÌM BẰNG CHỨNG PHẢN BÁC
↓
SO SÁNH
↓
KẾT LUẬN CÓ GIỚI HẠN
↓
LƯU HỒ SƠ
```

AI không được nhảy thẳng từ câu hỏi tới kết luận trong những nghiên cứu cần độ tin cậy cao.

## 15.4. Cửa kiểm tra bằng chứng

Một kết quả tìm được chỉ là ứng viên.

Loại nếu:

- chỉ là mục lục;
- chỉ là tên tác phẩm;
- chỉ có thông tin danh mục;
- không có nội dung hỗ trợ;
- ngữ cảnh cho thấy đang dùng từ theo nghĩa khác;
- nguồn nằm ngoài phạm vi;
- vị trí không kiểm tra được;
- là bản trùng.

## 15.5. Kiểm tra câu trích

Phải kiểm tra:

```text
câu trích có thật?
↓
nằm đúng vị trí?
↓
đúng tài liệu?
↓
đúng phiên bản?
```

Nếu AI viết lại nội dung thì phải ghi là diễn đạt lại, không trình bày như nguyên văn.

## 15.6. Kiểm tra khẳng định với bằng chứng

Có thể dùng năm mức:

### TRỰC TIẾP

Nguồn gần như nói đúng khẳng định.

### MẠNH

Khẳng định là cách diễn đạt lại hợp lý và nguồn hỗ trợ rõ.

### YẾU

Có liên quan nhưng cần thêm giả định.

### KHÔNG ĐỦ

Nguồn chưa chứng minh được điều đang nói.

### MÂU THUẪN

Có bằng chứng chống lại.

Quy tắc xuất bản:

- TRỰC TIẾP → dùng được;
- MẠNH → dùng được;
- YẾU → phải ghi giới hạn;
- KHÔNG ĐỦ → không biến thành kết luận chắc chắn;
- MÂU THUẪN → phải trình bày bất đồng.

## 15.7. Tìm bằng chứng phản bác

Sau khi tạo kết luận sơ bộ, hệ thống phải thử tìm trường hợp chống lại nó.

Ví dụ khẳng định:

> “Mọi tác giả trong nhóm này đều cho rằng X.”

Hệ thống phải thử tìm:

- tác giả trong nhóm không nói X;
- nguồn nói ngược X;
- trường hợp ngoại lệ;
- giai đoạn lịch sử khác.

Nếu tìm thấy, khẳng định phải được sửa hoặc hạ mức chắc chắn.

## 15.8. “Không tìm thấy” không đồng nghĩa “không tồn tại”

Không nên viết:

> “Không có nguồn nào nói X.”

nếu chỉ biết hệ thống đã không tìm thấy.

Nên ghi:

> **Không tìm thấy bằng chứng cho X trong phạm vi kho nguồn đã khảo sát.**

Kết quả âm nên lưu:

```text
kho nguồn đã tìm
phiên bản
ngôn ngữ
cách tìm
ngày tìm
giới hạn phạm vi
kết quả
```

## 15.9. Nhiều nguồn đồng ý chưa chắc độc lập

Ba sách nói giống nhau có thể đều dựa trên một nguồn chung.

Khi nghiên cứu yêu cầu cao, nên xem xét:

- quan hệ trích dẫn;
- bản dịch phụ thuộc;
- họ bản thảo;
- nguồn chung;
- tác phẩm phái sinh.

Không được đếm sự lặp lại như các xác nhận độc lập nếu không có căn cứ.

## 15.10. Phân biệt các lớp nội dung

Luôn phân biệt:

```text
NGUYÊN VĂN

BẢN DỊCH XUẤT BẢN

BẢN DỊCH AI

DIỄN ĐẠT LẠI

DIỄN GIẢI CỦA HỌC GIẢ

SUY LUẬN / TỔNG HỢP CỦA AI
```

## 15.11. Phạm vi nguồn quyết định sức mạnh của kết luận

Một kết luận toàn cục cần biết kho nguồn có độ phủ đến đâu.

Trong những dự án nghiên cứu lớn, có thể cần ma trận độ phủ theo:

- thời kỳ;
- vùng;
- ngôn ngữ;
- truyền thống;
- loại nguồn;
- tình trạng bản thảo;
- nghiên cứu hiện đại.

Điều này giúp nhìn thấy thiên lệch của kho dữ liệu.

## 15.12. Hồ sơ lần nghiên cứu

Mỗi lần nghiên cứu sâu nên lưu:

```text
run_id
câu hỏi
ngày

phiên bản kho nguồn
phiên bản hệ thống
phiên bản cấu hình

cách tìm
tham số tìm

bằng chứng đã dùng
bằng chứng phản bác

khẳng định được chấp nhận
khẳng định bị loại

mô hình AI
phiên bản hướng dẫn

kết quả
điểm chưa giải quyết
```

## 15.13. Khả năng tái lập

Không yêu cầu lần chạy sau phải tạo câu văn giống từng chữ.

Nhưng phải có thể giải thích:

- dùng cùng phiên bản nguồn hay không;
- lấy cùng hoặc gần cùng tập bằng chứng hay không;
- vì sao kết quả tìm thay đổi;
- khẳng định nào được hỗ trợ;
- khẳng định nào bị loại.

## 15.14. Nguồn ngoài phải được gắn nhãn

Nếu cho phép tìm web:

```text
nguồn trong kho
≠
nguồn ngoài
```

Không trộn âm thầm.

Nguồn ngoài có thể dùng để:

- phát hiện tài liệu mới;
- kiểm tra thư mục;
- tìm DOI;
- tìm phiên bản mới;
- bổ sung nghiên cứu được người dùng cho phép.

Sau đó cần quyết định có đưa nguồn đó vào kho chính thức hay không.

## 15.15. Không theo đuổi “độ chắc chắn giả”

Không nên biến mọi kết luận thành một con số xác suất đẹp mắt nếu không có cơ sở thống kê.

Có thể dùng ngôn ngữ:

- rất mạnh;
- mạnh;
- trung bình;
- yếu;
- chưa giải quyết.

Và giải thích dựa trên:

- độ trực tiếp của bằng chứng;
- chất lượng nguồn;
- số nguồn độc lập;
- bằng chứng phản bác;
- độ phủ của corpus;
- độ chắc của vị trí trích dẫn.

## 15.16. Kết luận

Mục tiêu của chế độ nghiên cứu nghiêm ngặt không phải:

> **không bao giờ sai**.

Mục tiêu là:

> **không để AI dễ dàng biến một kết quả tìm kiếm, một câu trích hoặc một suy luận chưa đủ căn cứ thành “sự thật” mà không để lại dấu vết để kiểm tra.**
