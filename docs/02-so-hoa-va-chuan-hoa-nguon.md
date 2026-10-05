# 2. Số hoá và chuẩn hoá nguồn

## 2.1. Nguyên tắc: không OCR tất cả

OCR là nhận dạng chữ từ ảnh. Đây là bước có thể gây lỗi và tốn tài nguyên, vì vậy chỉ dùng khi cần.

Đối với từng trang PDF:

1. kiểm tra có lớp chữ không;
2. kiểm tra chữ có đủ và hợp lệ không;
3. kiểm tra mã Unicode có bị rác không;
4. kiểm tra thứ tự đọc có hợp lý không;
5. nếu đạt, lấy chữ trực tiếp;
6. nếu không đạt, mới OCR.

Một cuốn 500 trang có thể chỉ cần OCR 20–50 trang. Không có lý do chạy mô hình nhìn ảnh cho cả cuốn.

## 2.2. EPUB và MOBI

### EPUB

EPUB thường đã có XHTML, mục lục, chương và metadata. Cần giữ cấu trúc này thay vì biến EPUB thành ảnh.

### MOBI

Dùng Calibre để chuyển MOBI sang EPUB hoặc HTML trước rồi xử lý theo luồng EPUB.

## 2.3. Chuỗi OCR đề xuất

```text
Trang cần OCR
   ↓
PP-OCRv6
   ↓
độ tin cậy đạt?
 ├─ có → chấp nhận
 └─ không
      ↓
 PaddleOCR-VL
      ↓
 vẫn nghi ngờ?
      ↓
 đánh dấu kiểm tra hoặc dịch vụ mạnh hơn
```

Lý do dùng chuỗi nhiều tầng: trang dễ không cần công cụ mạnh; trang khó mới trả chi phí cao hơn.

## 2.4. Luôn giữ dữ liệu gốc và dữ liệu làm sạch

Mỗi khối văn bản nên có tối thiểu:

- `text_raw`: chữ lấy trực tiếp từ nguồn/OCR;
- `text_clean`: chữ đã làm sạch;
- `source_method`: lấy trực tiếp hay OCR;
- `ocr_engine` nếu có;
- `ocr_confidence` nếu có;
- `page_id`;
- `bbox` hoặc vị trí trên trang nếu có.

Không xoá `text_raw` sau khi sửa.

## 2.5. Truy nguồn theo trang

Một đoạn tìm kiếm phải có đường quay về:

```text
đoạn tìm kiếm
→ khối
→ trang
→ ấn bản
→ file nguồn
```

Nếu trang là scan, giữ cả ảnh trang để kiểm tra trích dẫn khi OCR có độ tin cậy thấp.

## 2.6. Khử trùng

### Trùng tuyệt đối

Dùng SHA-256 của file.

### Gần trùng

Dùng dấu vân tay văn bản như MinHash/SimHash hoặc so sánh nội dung chuẩn hoá.

Cần phân biệt:

- cùng tác phẩm nhưng khác ấn bản;
- cùng ấn bản nhưng khác file;
- bản scan khác chất lượng;
- PDF và EPUB có cùng nội dung.

Không nên làm mất thông tin về ấn bản chỉ vì nội dung gần giống.

## 2.7. Phiên bản xử lý

Mỗi kết quả cần biết:

- phiên bản parser;
- phiên bản OCR;
- phiên bản quy tắc làm sạch;
- phiên bản embedding.

Nhờ đó khi nâng cấp một công cụ, hệ thống biết chính xác tài liệu nào cần chạy lại.
