# 7. Mô hình dữ liệu và truy nguồn

## 7.1. Mục tiêu

Mô hình dữ liệu phải cho phép:

- phân biệt tác phẩm và ấn bản;
- bảo tồn file nguồn;
- truy đúng trang;
- giữ văn bản thô và văn bản sạch;
- tạo đoạn phục vụ tìm kiếm mà không làm mất nguồn gốc;
- nối bằng chứng với khẳng định;
- nối khẳng định với trang tri thức;
- lưu lịch sử nghiên cứu.

## 7.2. Thực thể chính

### Tác phẩm — `Work`

Nội dung trí tuệ chung.

### Ấn bản — `Edition`

Một lần xuất bản hoặc bản dịch cụ thể.

### File nguồn — `SourceFile`

PDF, EPUB, MOBI hoặc file thật cùng dấu vân tay số.

### Mục — `Section`

Phần, chương, mục, tiểu mục.

### Trang — `Page`

Trang vật lý hoặc vị trí logic tương đương.

### Khối — `Block`

Tiêu đề, đoạn văn, bảng, chú thích, hình, công thức.

### Đoạn tìm kiếm — `Chunk`

Đơn vị được chuẩn bị cho hệ tìm kiếm.

### Bằng chứng — `Evidence`

Một đoạn nguồn cụ thể được kiểm tra và dùng để hỗ trợ hoặc phản bác khẳng định.

### Khẳng định — `Claim`

Một phát biểu tri thức có nguồn gốc và tình trạng bằng chứng.

### Trang tri thức — `BrainPage`

Trang trong Bộ não thứ hai.

### Không gian nghiên cứu — `ResearchWorkspace`

Bộ dữ liệu tạm cho một câu hỏi sâu.

### Đề xuất thay đổi — `Proposal`

Gói thay đổi chưa được ghi chính thức vào Bộ não thứ hai.

### Hồ sơ lần nghiên cứu — `ResearchRun`

Ghi lại câu hỏi, phiên bản dữ liệu, cách tìm, bằng chứng, khẳng định và kết quả của một lần nghiên cứu.

## 7.3. Quan hệ chính

```text
Tác phẩm
└─ Ấn bản
   └─ File nguồn
      └─ Mục
         └─ Trang
            └─ Khối
               └─ Đoạn tìm kiếm
```

và:

```text
Đoạn nguồn
↓
Bằng chứng
↓
Khẳng định
↓
Trang tri thức
```

Không gian nghiên cứu tạo ra các đề xuất, nhưng đề xuất chỉ vào Bộ não thứ hai sau khi kiểm tra.

## 7.4. Đường truy nguồn bắt buộc

Mỗi đoạn tìm kiếm phải lần ngược được:

```text
đoạn
→ khối
→ trang
→ mục
→ ấn bản
→ file nguồn
```

Mỗi khẳng định quan trọng phải lần ngược:

```text
khẳng định
→ bằng chứng
→ đoạn nguồn
→ nguồn gốc
```

## 7.5. Hai chiều trạng thái của khẳng định

### Cách khẳng định được tạo ra

- `TRICH_XUAT`: nguồn nói trực tiếp;
- `SUY_LUAN`: AI rút ra từ một hoặc nhiều bằng chứng;
- `TONG_HOP`: AI kết hợp nhiều nguồn.

### Tình trạng bằng chứng

- `DUOC_HO_TRO`;
- `CO_TRANH_LUAN`;
- `HO_TRO_YEU`;
- `CHUA_DU_DU_LIEU`;
- `CHUA_BIET`;
- `BI_PHAN_BAC`.

Không nên gộp hai chiều này thành một nhãn.

## 7.6. Bằng chứng phải có vị trí

Tối thiểu nên biết:

- mã tài liệu;
- ấn bản;
- chương/mục;
- trang hoặc mã đoạn;
- nội dung;
- phiên bản nguồn;
- trạng thái kiểm tra.

## 7.7. Phân biệt nguyên văn và các lớp diễn giải

Mô hình phải có khả năng phân biệt:

1. nguyên văn;
2. bản dịch xuất bản;
3. bản dịch AI;
4. diễn đạt lại;
5. diễn giải của học giả;
6. tổng hợp của AI.

## 7.8. Ví dụ bản ghi đoạn tìm kiếm

```json
{
  "chunk_id": "chunk_001",
  "work_id": "work_123",
  "edition_id": "ed_456",
  "section_path": ["Phần II", "Chương 5", "Vô thường"],
  "page_start": 123,
  "page_end": 124,
  "text_raw": "...",
  "text_clean": "...",
  "source_method": "ocr",
  "ocr_engine": "paddleocr",
  "ocr_confidence": 0.96
}
```

Đây chỉ là ví dụ khái niệm. Tên trường cuối cùng sẽ được chốt khi triển khai.

## 7.9. Phiên bản xử lý

Nên lưu:

- phiên bản trình đọc;
- phiên bản làm sạch;
- phiên bản nhận dạng chữ;
- phiên bản chia đoạn;
- phiên bản mô hình tìm theo ý nghĩa.

## 7.10. Dữ liệu không được ghi đè

Không ghi đè:

- file nguồn;
- văn bản thô của một phiên bản xử lý;
- lịch sử khẳng định;
- lịch sử Git của trang tri thức.

Nếu thay đổi, tạo phiên bản mới.

## 7.11. Dữ liệu phát sinh có thể xây lại

Các chỉ mục tìm kiếm, véc-tơ, bộ nhớ đệm và dữ liệu trung gian có thể xóa và dựng lại.

Chúng không phải nguồn dữ liệu chính.
