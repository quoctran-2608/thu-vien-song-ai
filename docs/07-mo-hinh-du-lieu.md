# 7. Mô hình dữ liệu và truy nguồn

## 7.1. Thực thể chính

### Tác phẩm (`Work`)

Nội dung trí tuệ chung, ví dụ một cuốn sách với nhiều ấn bản.

### Ấn bản (`Edition`)

Một lần xuất bản cụ thể: nhà xuất bản, năm, người dịch, ISBN, ngôn ngữ.

### Nguồn file (`SourceFile`)

PDF/EPUB/MOBI/ảnh thực tế cùng SHA-256.

### Mục (`Section`)

Phần, chương, mục, tiểu mục.

### Trang (`Page`)

Trang vật lý hoặc trang logic tương đương.

### Khối (`Block`)

Tiêu đề, đoạn văn, bảng, chú thích, hình, công thức.

### Đoạn tìm kiếm (`Chunk`)

Đơn vị tối ưu cho truy hồi, có thể bao gồm nhiều block nhỏ.

### Khẳng định (`Claim`)

Một phát biểu có loại và nguồn.

### Bằng chứng (`Evidence`)

Liên kết Claim với một hoặc nhiều đoạn nguồn.

### Trang tri thức (`BrainPage`)

Trang Markdown trong Bộ não thứ hai.

### Không gian nghiên cứu (`ResearchWorkspace`)

Bộ dữ liệu tạm cho một câu hỏi sâu.

### Đề xuất thay đổi (`Proposal`)

Gói thay đổi chưa được áp dụng vào Bộ não thứ hai.

## 7.2. Sơ đồ quan hệ tối giản

```text
Work
 └─ Edition
     └─ SourceFile
         └─ Section
             └─ Page
                 └─ Block
                     └─ Chunk

Chunk ─→ Evidence ─→ Claim ─→ BrainPage
ResearchWorkspace ─→ Proposal ─→ BrainPage
```

## 7.3. Nguyên tắc nguồn gốc

Mọi Claim quan trọng phải có ít nhất một Evidence hoặc được đánh dấu rõ là giả thuyết chưa có bằng chứng.

## 7.4. Phiên bản xử lý

Chunk cần lưu:

- parser_version;
- cleaner_version;
- ocr_version;
- chunker_version;
- embedding_version.

Điều này giúp tái tạo và kiểm tra hồi quy.

## 7.5. Ví dụ bản ghi chunk

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

## 7.6. Dữ liệu không được ghi đè

- file nguồn;
- text_raw của một phiên bản xử lý;
- lịch sử Claim;
- lịch sử Git của BrainPage.

Nếu sửa, tạo phiên bản mới.
