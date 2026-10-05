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


## Kiểm toán tài liệu Bước 7

Repo đã được kiểm toán lại như một người mới đọc dự án:

- phân biệt rõ phiên bản tài liệu và phiên bản phần mềm;
- bổ sung điểm bắt đầu triển khai bản 0.1;
- kiểm tra lại liên kết nội bộ;
- chuẩn hóa thêm tiếng Việt;
- ghi rõ trạng thái công khai của repo.

Biên bản:

> [Kiểm toán tài liệu phiên bản 1.0 — Bước 7](docs/_kiem-ke/kiem-toan-v1.0-buoc-7-2026-10-05.md)

Hai điểm tồn đọng của Bước 7 đã được xử lý trong Bước 8:

- repo đã dùng **Apache License 2.0**, kèm `NOTICE`;
- infographic README đã được thay từ bản 200×283 px sang bản 230×325 px, vẫn giữ dung lượng nhẹ.

Mốc phát hành tài liệu:

> [Phát hành tài liệu v1.0](PHAT_HANH_V1.0.md)


## Phản biện sau khi chốt v1.0

Sau khi chốt tài liệu v1.0, dự án được rà lại theo vai trò phản biện, tập trung vào các điều kiện có thể làm hệ thống thất bại trong thực tế.

Tài liệu:

> [Phản biện: rủi ro, giới hạn và điều kiện thất bại](docs/18-rui-ro-gioi-han-va-phan-bien.md)

Các rủi ro ưu tiên cao nhất gồm:

- xây quá nhiều lớp trước khi bản 0.1 chứng minh giá trị;
- sai âm thầm ở bước đọc/OCR/truy nguồn;
- truy hồi bỏ sót bằng chứng;
- nguồn có truy xuất nhưng bản thân nguồn không đáng tin;
- chèn lệnh độc hại gián tiếp qua tài liệu;
- phân quyền tìm kiếm và rò dữ liệu;
- Bộ não thứ hai tích lũy tri thức sai/lỗi thời;
- khó đồng bộ nhất quán giữa dữ liệu chuẩn, Markdown và các chỉ mục;
- bản quyền, quyền xử lý dữ liệu và yêu cầu xóa.

Vòng phản biện cũng phát hiện và đã đính chính một lỗi trong Bước 6: PageIndex có chế độ cục bộ, nhưng PageIndex File System nhiều tài liệu hiện là tính năng đám mây.
