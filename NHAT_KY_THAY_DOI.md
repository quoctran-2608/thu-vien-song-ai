# Nhật ký thay đổi

## Phiên bản 1.0 — 05/10/2026

### Đã thêm

- Bản mô tả đầy đủ bài toán số hoá kho sách PDF, EPUB, MOBI.
- Kiến trúc bốn tầng: nguồn gốc, kho dữ liệu chuẩn, RAG bằng chứng, Bộ não thứ hai.
- Cơ chế bộ nhớ làm việc/nghiên cứu tạm thời.
- Chiến lược OCR theo tầng, chỉ OCR trang cần thiết.
- Tìm kiếm kết hợp giữa từ khóa và ý nghĩa, sau đó xếp hạng lại.
- Cơ chế “gói bằng chứng” để giảm lượng chữ gửi vào AI.
- Sổ khẳng định để phân biệt dữ liệu trích từ nguồn với suy luận của AI.
- Cơ chế đề xuất → kiểm chứng → một bộ ghi duy nhất → Git commit khi cập nhật Bộ não thứ hai.
- Đánh giá các repo uy tín và cách tận dụng ưu điểm của từng repo.
- Lộ trình triển khai từ bản 0.1 kỹ thuật đến bản sản xuất.

### Quyết định lớn

- Không lấy RAGFlow làm lõi dữ liệu.
- Không trộn kho bằng chứng và Bộ não thứ hai thành một chỉ mục duy nhất.
- Chưa xây đồ thị tri thức toàn kho ở giai đoạn đầu.
- Không cho AI sửa nguồn gốc.
- Không cho nhiều tác tử ghi trực tiếp vào wiki cùng lúc.
