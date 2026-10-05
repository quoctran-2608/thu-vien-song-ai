# 8. Giao diện cho AI và MCP

## 8.1. Nguyên tắc

AI không nên biết bên dưới đang dùng:

- Qdrant;
- RAGFlow;
- QMD;
- PageIndex;
- hay một công cụ khác.

AI chỉ gọi một số lệnh cấp cao ổn định của Thư Viện Sống.

## 8.2. Bộ lệnh đề xuất

### `search_library(query, filters)`

Tìm toàn thư viện.

Kết quả nên ngắn:

- mã sách;
- tiêu đề;
- chương/mục;
- đoạn rất ngắn;
- trang;
- điểm liên quan;
- trạng thái kiểm tra nếu có.

### `get_book_outline(book_id)`

Lấy cây chương/mục và phạm vi trang.

### `search_book(book_id, query)`

Tìm trong một cuốn.

### `read_section(section_id)`

Đọc một mục/chương đã chọn.

### `read_pages(book_id, pages)`

Đọc chính xác một số trang.

### `get_page_image(book_id, page)`

Lấy ảnh trang gốc để kiểm chứng nhận dạng chữ hoặc trích dẫn.

### `search_brain(query)`

Tìm trong Bộ não thứ hai.

### `read_brain_page(page_id)`

Đọc một trang tri thức.

### `research(question, scope)`

Mở một không gian nghiên cứu sâu, gom bằng chứng và tạo bản tổng hợp nháp.

## 8.3. MCP

MCP là tên một chuẩn giao tiếp giúp AI gọi công cụ và dữ liệu bên ngoài theo cách thống nhất.

```text
AI
↓
MCP của Thư Viện Sống
↓
lệnh cấp cao
↓
bộ chuyển tiếp
↓
công cụ thật
```

Mục tiêu:

> thay công cụ phía sau mà không bắt tác tử AI phải học lại toàn bộ giao diện.

## 8.4. Giới hạn đầu ra

Các lệnh tìm kiếm phải ưu tiên trả thông tin tối thiểu cần thiết.

Không “đổ” cả sách cho AI.

Luồng nên là:

```text
tìm
↓
xem ứng viên
↓
chọn
↓
đọc phần cần thiết
```

## 8.5. Quyền đọc và quyền ghi phải tách

Tác tử nghiên cứu mặc định được:

- đọc;
- tìm;
- tạo không gian nghiên cứu;
- tạo đề xuất thay đổi.

Không mặc định được sửa Bộ não thứ hai.

## 8.6. Một bộ ghi duy nhất

Các đề xuất của nhiều tác tử đi tới một bộ ghi duy nhất:

```text
đề xuất
↓
kiểm tra
↓
ghi tất cả hoặc không ghi
↓
Git commit
```

## 8.7. Bộ chuyển tiếp

Mỗi công cụ bên ngoài nên đứng sau một bộ chuyển tiếp riêng.

Ví dụ:

```text
search_library()
↓
giao diện tìm kiếm nội bộ
↓
bộ chuyển tiếp RAGFlow / Qdrant / công cụ khác
```

Nhờ vậy dữ liệu chuẩn và giao diện AI không bị khóa vào một nhà cung cấp.
