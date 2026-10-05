# Phiên bản tài liệu và đặc tả 1.0

Ngày chốt nền tảng nghiên cứu: **05/10/2026**

## Trạng thái

Phiên bản 1.0 hiện là **bộ đặc tả nghiên cứu và kiến trúc nền tảng**, chưa phải bản phần mềm sản xuất hoàn chỉnh.

> **Lưu ý:** “v1.0” ở đây là phiên bản tài liệu/đặc tả. Mốc “phần mềm sản xuất 1.0” trong lộ trình là một mục tiêu tương lai sau các bản kỹ thuật 0.x.

Nhánh `v1.0` trên GitHub được dùng làm mốc tài liệu và hiện được đồng bộ với trạng thái tài liệu đã duyệt.

Bộ tài liệu đã được rà soát và viết lại để khắc phục tình trạng bản lưu trong repo bị rút gọn so với quá trình nghiên cứu.

## Bắt đầu triển khai

Kỹ sư mới nên bắt đầu tại:

> [Hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1](docs/17-huong-dan-bat-dau-trien-khai-v0.1.md)

## Tài liệu chính

Tài liệu cần đọc đầu tiên:

> [Thư Viện Sống AI — Kiến trúc tổng thể phiên bản 1.0](docs/00-TAI-LIEU-TONG-THE-V1.0.md)

## Những nội dung đã được bảo toàn

- nguồn gốc bất biến;
- mô hình dữ liệu chuẩn;
- phân biệt tác phẩm và ấn bản;
- số hóa PDF/EPUB/MOBI;
- nhận dạng chữ theo từng trang;
- tìm theo chữ + ý nghĩa + xếp hạng lại;
- tóm tắt và đọc phân tầng;
- đọc theo độ sâu thích ứng;
- hai loại trí nhớ;
- gói bằng chứng;
- Bộ não thứ hai phát triển theo nhu cầu;
- sổ khẳng định;
- kiểm tra quan hệ khẳng định–bằng chứng;
- không gian nghiên cứu;
- tìm bằng chứng phản bác;
- cập nhật gia tăng;
- nhiều tác tử nhưng một bộ ghi;
- cập nhật toàn vẹn;
- MCP và giao diện công cụ cấp cao;
- bộ kiểm thử và kiểm thử hồi quy;
- cấu trúc repo kỹ thuật;
- chế độ nghiên cứu nghiêm ngặt.

## Tuyên bố tương thích dài hạn

Dữ liệu chuẩn của dự án phải tồn tại độc lập với mọi bộ máy bên ngoài.

Việc thay RAGFlow, QMD, PageIndex, Qdrant, mô hình biểu diễn ý nghĩa hoặc mô hình xếp hạng không được làm mất:

- dữ liệu nguồn;
- mô hình dữ liệu chuẩn;
- sổ khẳng định;
- Bộ não thứ hai;
- lịch sử nghiên cứu.

## Kiểm chứng công cụ bên ngoài

Vòng kiểm chứng ngày **05/10/2026** đã hoàn thành cho các thành phần chính: Docling, PaddleOCR, RAGFlow, Qdrant, QMD, PageIndex, claude-obsidian, obsidian-wiki, Hermes Agent/LLM Wiki, Cognee, LightRAG, Graphiti, Mem0, Khoj, Qwen3-Embedding, Qwen3-Reranker và BGE-M3.

Xem chi tiết tại:

> [Kiểm chứng công cụ và dự án tham khảo — 05/10/2026](docs/16-kiem-chung-cong-cu-2026-10-05.md)

Kết quả kiểm chứng **không biến các phiên bản công cụ thành cam kết bất biến**. Trước khi triển khai sản xuất vẫn phải kiểm tra lại phiên bản, giấy phép, yêu cầu phần cứng và chạy bộ đánh giá trên dữ liệu thật.
