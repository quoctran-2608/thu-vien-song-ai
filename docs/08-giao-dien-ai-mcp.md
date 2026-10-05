# 8. Giao diện cho AI và MCP

## 8.1. Nguyên tắc

AI không nên biết bên dưới đang dùng Qdrant, RAGFlow hay QMD. AI chỉ gọi một số công cụ cấp cao ổn định.

## 8.2. Bộ công cụ đề xuất

### `search_library(query, filters)`

Tìm toàn thư viện và trả danh sách ngắn sách/chương/đoạn.

### `get_book_outline(book_id)`

Lấy mục lục, cây chương/mục và phạm vi trang.

### `search_book(book_id, query)`

Tìm trong một cuốn cụ thể.

### `read_section(section_id)`

Đọc một mục/chương đã chọn.

### `read_pages(book_id, pages)`

Đọc chính xác một số trang.

### `get_page_image(book_id, page)`

Lấy ảnh gốc để kiểm chứng OCR/trích dẫn.

### `search_brain(query)`

Tìm trong Bộ não thứ hai.

### `read_brain_page(page_id)`

Đọc trang tri thức đã tổng hợp.

### `research(question, scope)`

Mở một không gian nghiên cứu, gom bằng chứng và tạo bản tổng hợp nháp.

## 8.3. MCP

MCP là một chuẩn để AI gọi công cụ bên ngoài. Repo nên cung cấp một MCP server riêng, còn các động cơ bên dưới được bọc qua adapter.

Ví dụ:

```text
AI
↓
MCP của Thư Viện Sống
↓
search_library()
↓
adapter
↓
Qdrant hoặc RAGFlow
```

## 8.4. Giới hạn đầu ra

Mỗi tool phải ưu tiên trả thông tin cần thiết, không dump dữ liệu lớn.

Ví dụ `search_library` trả:

- mã sách;
- tiêu đề;
- đường dẫn chương;
- đoạn rất ngắn;
- điểm liên quan;
- trang.

Chỉ khi AI gọi `read_section` hoặc `read_pages` mới trả văn bản dài hơn.

## 8.5. An toàn ghi

Các tool đọc và tool ghi phải tách biệt. Tác tử nghiên cứu mặc định chỉ có quyền đọc và tạo `Proposal`; quyền commit vào Bộ não thứ hai thuộc một bộ ghi riêng.
