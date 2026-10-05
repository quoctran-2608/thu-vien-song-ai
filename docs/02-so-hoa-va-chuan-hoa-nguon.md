# 2. Số hóa và kho dữ liệu chuẩn

## 2.1. Nguyên tắc: không nhận dạng chữ từ ảnh toàn bộ PDF

Đối với từng trang:

```text
kiểm tra trang
↓
có lớp chữ tốt?
├── có → lấy chữ trực tiếp
└── không → nhận dạng chữ từ ảnh
```

Có thể kiểm tra:

- có lớp chữ hay không;
- lượng ký tự;
- Unicode có hợp lệ không;
- chữ có bị rác không;
- thứ tự đọc có hợp lý không.

Một cuốn 500 trang có thể chỉ có một phần nhỏ thật sự cần nhận dạng chữ từ ảnh.

## 2.2. Nhận dạng chữ nhiều tầng

Không dùng công cụ mạnh nhất cho mọi trang.

```text
trang cần xử lý
↓
công cụ nhận dạng thông thường
↓
đủ tin cậy?
├── có → dùng
└── không → công cụ hiểu bố cục mạnh hơn
```

Trong lựa chọn hiện tại, PP-OCRv6 và PaddleOCR-VL là các ứng viên đáng thử, nhưng tên công cụ cụ thể phải được kiểm chứng trên dữ liệu thật.

## 2.3. EPUB

EPUB thường đã có:

- XHTML;
- mục lục;
- tiêu đề;
- chương;
- thông tin sách.

Không được biến EPUB thành ảnh rồi nhận dạng chữ.

## 2.4. MOBI

Chuẩn hóa qua Calibre:

```text
MOBI
→ EPUB hoặc HTML
→ đọc cấu trúc
```

## 2.5. Giữ văn bản thô và văn bản sạch

Luôn giữ song song:

```text
text_raw
= chữ lấy trực tiếp từ nguồn hoặc nhận dạng chữ

text_clean
= chữ đã chuẩn hóa
```

Không ghi đè dữ liệu thô.

## 2.6. Thông tin kèm theo mỗi khối

Nên có:

- trang;
- chương/mục;
- phương pháp lấy chữ;
- công cụ đã dùng;
- mức tin cậy;
- vị trí trên trang nếu có;
- ảnh trang nếu cần.

Nếu câu trích quan trọng đến từ kết quả nhận dạng chữ có độ tin cậy thấp, nên kiểm lại ảnh trang hoặc một công cụ khác.

## 2.7. Dấu vân tay số và chống trùng

### Trùng tuyệt đối

Dùng SHA-256 — có thể hiểu là dấu vân tay số của file.

### Gần trùng

Có thể dùng MinHash, SimHash hoặc cách tương đương để phát hiện hai nội dung gần giống.

## 2.8. Không đánh mất ấn bản

Cùng một tác phẩm có thể có:

- nhiều lần xuất bản;
- nhiều bản dịch;
- nhiều bản scan;
- nhiều định dạng.

Không gộp mất thông tin về ấn bản chỉ vì nội dung gần giống.

## 2.9. Mô hình dữ liệu chuẩn

```text
Tác phẩm
↓
Ấn bản
↓
Nguồn file
↓
Chương / mục
↓
Trang
↓
Khối
↓
Đoạn tìm kiếm
```

Một đoạn tìm kiếm phải lần ngược được về đúng file, đúng ấn bản và đúng trang.

## 2.10. Bốn tầng dữ liệu

### Tầng 0 — Danh mục

Tên sách, tác giả, dịch giả, nhà xuất bản, năm, ngôn ngữ, chủ đề.

### Tầng 1 — Cấu trúc

Mục lục, phần, chương, mục, khoảng trang.

### Tầng 2 — Tìm kiếm

Các đoạn đã chuẩn bị cho hệ tìm kiếm.

### Tầng 3 — Nguồn

File gốc, chữ thô, chữ sạch, ảnh trang, vị trí chữ, độ tin cậy.

## 2.11. Phiên bản xử lý

Cần biết tối thiểu:

- phiên bản trình đọc;
- phiên bản nhận dạng chữ;
- phiên bản làm sạch;
- phiên bản chia đoạn;
- phiên bản mô hình tìm theo ý nghĩa.

Nhờ đó khi nâng cấp công cụ, ta biết tài liệu nào cần xử lý lại.
