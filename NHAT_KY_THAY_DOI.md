# Nhật ký thay đổi

## Phiên bản 1.0 — 05/10/2026

### Khởi tạo

- Tạo repo Thư Viện Sống AI.
- Lưu nghiên cứu về số hóa kho sách, RAG và Bộ não thứ hai.
- Thêm infographic minh họa.

### Vòng rà soát tài liệu

Sau khi đối chiếu bản nghiên cứu dài với tài liệu trên GitHub, phát hiện repo giữ đúng hướng nhưng đã rút gọn quá nhiều lý do, ví dụ và chi tiết vận hành.

Đã thực hiện:

- tạo tài liệu tổng thể để một người có thể đọc một mạch và hiểu gần toàn bộ dự án;
- viết lại toàn bộ 14 tài liệu chuyên sâu hiện có;
- bổ sung tài liệu cấu trúc repo kỹ thuật;
- bổ sung chế độ nghiên cứu nghiêm ngặt;
- bổ sung bảng kiểm bảo toàn ý tưởng để các phiên bản sau không vô tình xóa mất quyết định quan trọng;
- đối chiếu lại bản “Bộ tài liệu chuyên sâu” gốc và phục hồi phần liên kết có chủ ý giữa các trang của Bộ não thứ hai.

### Các ý quan trọng được phục hồi hoặc làm rõ

- AI không phải là nguồn.
- Một kết quả tìm được chưa tự động là bằng chứng.
- Một trích dẫn có thật chưa chắc chứng minh được khẳng định.
- Đọc theo độ sâu thích ứng.
- Gói bằng chứng là ranh giới giữa tìm kiếm và suy luận.
- RAG có độ phủ rộng, Bộ não thứ hai có độ sâu tích lũy.
- Các trang Bộ não thứ hai liên kết với nhau có chủ ý, không tạo liên kết máy móc.
- Markdown là dữ liệu lâu dài; Obsidian chỉ là giao diện.
- Không gian nghiên cứu không ghi thẳng vào Bộ não thứ hai.
- Tìm bằng chứng phản bác.
- “Không tìm thấy” không đồng nghĩa “không tồn tại”.
- Nhiều nguồn đồng ý chưa chắc là nhiều nguồn độc lập.
- Sổ khẳng định có hai chiều: cách tạo và tình trạng bằng chứng.
- Cập nhật Bộ não thứ hai phải có tính toàn vẹn.
- Nhiều tác tử được nghiên cứu nhưng chỉ một bộ ghi áp dụng thay đổi.
- Các bộ máy bên ngoài phải thay thế được.

### Vòng kiểm chứng công cụ bên ngoài — Bước 6

Đã kiểm chứng bằng nguồn hiện hành ngày 05/10/2026 và bổ sung báo cáo riêng.

Các thay đổi nhận thức quan trọng:

- Qdrant hiện có thể đảm nhiệm phần lớn tìm kiếm kết hợp, không chỉ lưu véc-tơ.
- PageIndex đã có chế độ cục bộ và lớp nhiều tài liệu.
- RAGFlow Biên dịch tri thức với Wiki/Graph/Tree/PageIndex/... là tính năng thật.
- QMD đã có giao diện thư viện ổn định và công cụ đánh giá.
- Docling hỗ trợ trực tiếp nhiều định dạng, gồm EPUB.
- PP-OCRv6 có liệt kê tiếng Việt nhưng phải kiểm thử riêng vì từng có báo cáo thiếu ký tự có dấu.
- Qwen3-Embedding-0.6B có tối đa 1024 chiều; 512 chỉ là cấu hình có thể chọn để thử.
- Mem0 phân biệt kết quả đánh giá của nền tảng quản lý với bản mã nguồn mở.
- Khoj dùng AGPL-3.0 nên cần thận trọng nếu tái sử dụng mã.

Kiến trúc cốt lõi không đổi: dữ liệu chuẩn thuộc về Thư Viện Sống, các công cụ ngoài là bộ máy có thể thay.


### Kiểm toán toàn repo — Bước 7

Đã đọc repo như một người mới và kiểm tra cơ học 28 liên kết Markdown nội bộ; không phát hiện liên kết nội bộ bị hỏng.

Đã sửa các điểm dễ gây hiểu nhầm:

- phân biệt “tài liệu/đặc tả v1.0” với “phần mềm sản xuất 1.0” trong tương lai;
- ghi rõ repo hiện đang công khai và không nên chứa kho sách/dữ liệu nội bộ;
- bổ sung hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1;
- giải thích các chỉ số đánh giá bằng tiếng Việt;
- chuẩn hóa thêm thuật ngữ tiếng Việt;
- ghi nhận repo hiện chưa có file LICENSE và cần chủ repo quyết định giấy phép.

Xem biên bản: `docs/_kiem-ke/kiem-toan-v1.0-buoc-7-2026-10-05.md`.
