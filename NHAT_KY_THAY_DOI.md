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
- PageIndex có chế độ cục bộ, nhưng sau khi kiểm chứng lại, File System nhiều tài liệu hiện là tính năng đám mây; kết luận cũ đã được đính chính.
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


### Chốt phiên bản tài liệu v1.0 — Bước 8

Đã hoàn tất vòng chốt cuối:

- thêm `LICENSE` theo Apache License 2.0;
- thêm `NOTICE` để làm rõ phạm vi bản quyền và nội dung bên thứ ba;
- thêm `PHAT_HANH_V1.0.md` làm mốc phát hành tài liệu/đặc tả v1.0;
- thay infographic 200×283 px bằng bản 230×325 px, vẫn tối ưu dung lượng cho README;
- cập nhật README, thông tin repo, tài liệu phiên bản và biên bản kiểm toán;
- đồng bộ nhánh `v1.0` với commit chốt cuối của `main`.

Từ mốc này, ưu tiên tiếp theo là **triển khai và đo bản kỹ thuật 0.1**, không tiếp tục mở rộng kiến trúc vĩ mô nếu chưa có dữ liệu thực nghiệm mới.


### Vòng phản biện rủi ro — đính chính PageIndex

Khi kiểm tra dự án theo hướng phản biện, phát hiện tài liệu Bước 6 đã ghép sai hai thông tin: “PageIndex có chế độ cục bộ” và “PageIndex có File System nhiều tài liệu”.

Đã đính chính:

- chế độ cục bộ: phù hợp PDF có chữ, lập chỉ mục/truy hồi/trò chuyện bằng mô hình của người dùng;
- OCR/hiểu ảnh, metadata, thư mục, MCP và File System nhiều tài liệu hiện thuộc phía đám mây;
- kiến trúc Thư Viện Sống không dựa vào File System của PageIndex cho định tuyến toàn kho.


### Phản biện rủi ro và giới hạn

Đã bổ sung `docs/18-rui-ro-gioi-han-va-phan-bien.md`.

Vòng này không tìm cách bảo vệ kiến trúc mà chủ động tìm điểm thất bại. Các phát hiện chính:

- nguy cơ xây quá phức tạp trước khi chứng minh nhu cầu;
- sai đầu vào/OCR/truy hồi có thể lan thành bằng chứng sai;
- truy nguồn không đồng nghĩa nguồn đáng tin;
- cần ranh giới “nội dung nguồn không đáng tin” để chống chèn lệnh gián tiếp;
- cần phân quyền ngay ở lớp truy hồi;
- cần thế hệ dữ liệu/chỉ mục và cơ chế nhất quán xuyên nhiều kho;
- cần chính sách nguồn về bản quyền, độ nhạy cảm, xử lý đám mây và lưu giữ;
- cần ngoại lệ xóa có kiểm toán cho nguyên tắc nguồn bất biến;
- cần đánh giá kín/đối kháng để tránh tối ưu quá mức theo bộ câu hỏi chuẩn.

Đã đính chính thêm phạm vi PageIndex: File System nhiều tài liệu hiện là tính năng đám mây.
