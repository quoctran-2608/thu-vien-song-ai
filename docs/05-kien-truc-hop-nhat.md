# 5. Kiến trúc hợp nhất: từ câu hỏi tới tri thức lâu dài

## 5.1. Hai loại trí nhớ

### Trí nhớ bằng chứng

Trả lời:

> Điều này nằm ở nguồn nào?

### Trí nhớ hiểu biết

Trả lời:

> Ta đã hiểu gì về điều này?

Hai loại trí nhớ có vòng đời và cách kiểm chứng khác nhau nên phải tách.

## 5.2. Bộ chọn cách xử lý câu hỏi

Không chạy toàn bộ hệ thống cho mọi câu hỏi.

Ví dụ:

### Tìm câu nguyên văn

```text
tìm theo chữ
→ kiểm tra vài kết quả
→ trả vị trí
```

### Tác giả nói gì về X?

```text
tìm theo chữ
+
tìm theo ý nghĩa
→ xếp hạng lại
→ vài đoạn tốt
```

### So sánh X qua nhiều sách

```text
Bộ não thứ hai
↓
xác định khái niệm / sách liên quan
↓
tìm bằng chứng gốc
↓
không gian nghiên cứu
↓
tổng hợp
```

## 5.3. Luồng hỏi đáp tổng thể

```text
CÂU HỎI
   ↓
BỘ CHỌN CÁCH XỬ LÝ
   │
   ├───────────────┬────────────────┐
   ↓               ↓                ↓
tìm chính xác   hỏi tổng hợp     đọc sách dài
   ↓               ↓                ↓
RAG          Bộ não thứ hai      PageIndex
   │               │                │
   └───────────────┴────────────────┘
                   ↓
             GÓI BẰNG CHỨNG
                   ↓
                AI ĐỌC
                   ↓
              KIỂM CHỨNG
                   ↓
                TRẢ LỜI
                   ↓
       có tri thức đáng lưu?
             ┌─────┴─────┐
             ↓           ↓
           không        có
             ↓           ↓
            xong      đề xuất
                         ↓
                     kiểm tra
                         ↓
                Bộ não thứ hai
```

## 5.4. Không gian nghiên cứu

Câu hỏi khó có một bàn làm việc tạm:

```text
research/
└── chu-de/
    ├── cau-hoi.md
    ├── pham-vi.md
    ├── tai-lieu-ung-vien.json
    ├── bang-chung/
    ├── ghi-chu/
    ├── mau-thuan.md
    ├── tong-hop.md
    └── truy-nguon.json
```

Không viết thẳng kết quả chưa kiểm chứng vào Bộ não thứ hai.

## 5.5. Vòng đời tri thức

```text
ĐỌC
↓
TÌM
↓
HIỂU
↓
NGHIÊN CỨU
↓
KIỂM CHỨNG
↓
GHI NHỚ
↓
LẦN SAU ĐỌC TỐT HƠN
```

Đây là điểm khác biệt lớn nhất so với ứng dụng RAG thông thường.

## 5.6. Ranh giới tự viết và dùng lại

### Không tự viết lại

- máy đọc PDF;
- công cụ nhận dạng chữ;
- cơ sở dữ liệu véc-tơ;
- mô hình biểu diễn ý nghĩa;
- mô hình xếp hạng lại;
- PageIndex;
- QMD;
- công cụ đồ thị.

### Phải tự kiểm soát

- mô hình dữ liệu chuẩn;
- truy nguồn;
- mã tài liệu và mã đoạn;
- bộ chọn cách xử lý;
- sổ khẳng định;
- gói bằng chứng;
- không gian nghiên cứu;
- trình duy trì Bộ não thứ hai;
- cơ chế cập nhật an toàn;
- bộ đánh giá;
- giao diện thống nhất cho AI.

## 5.7. Nguyên tắc thay thế công cụ

AI chỉ gọi các lệnh cấp cao của Thư Viện Sống.

Công cụ phía sau có thể thay mà không làm thay đổi cách AI sử dụng hệ thống.

## 5.8. Tiêu chuẩn sống sót

Một công cụ ngoài chỉ là bộ máy nếu ta có thể xóa nó, dựng lại nó và vẫn còn:

- nguồn;
- dữ liệu chuẩn;
- sổ khẳng định;
- Bộ não thứ hai;
- lịch sử nghiên cứu.
