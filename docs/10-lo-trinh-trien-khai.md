# 10. Lộ trình triển khai

## Giai đoạn 0 — thí nghiệm dữ liệu thật

- lấy 200–500 trang đại diện;
- benchmark Docling/PyMuPDF/PaddleOCR;
- xác định quy tắc preflight;
- xây 100–300 câu hỏi chuẩn.

Mục tiêu: biết chính xác dữ liệu thực khó ở đâu trước khi xây lớn.

## Bản kỹ thuật 0.1 — nguồn và bằng chứng

Làm:

- kho nguồn bất biến;
- SHA-256;
- parser;
- OCR theo tầng;
- mô hình Work/Edition/Section/Page/Block/Chunk;
- tìm theo chữ;
- tìm theo ý nghĩa;
- xếp hạng lại;
- dẫn nguồn trang.

Chưa làm:

- graph;
- tự động Second Brain toàn diện.

## Bản kỹ thuật 0.2 — Bộ não thứ hai

Làm:

- Markdown vault;
- QMD;
- BrainPage;
- Claim/Evidence;
- wikilink;
- Git;
- quy tắc AI.

## Bản kỹ thuật 0.3 — nghiên cứu sâu và tự bảo trì

Làm:

- ResearchWorkspace;
- Proposal;
- single-writer;
- kiểm tra mâu thuẫn;
- chống trùng;
- lint wiki;
- cập nhật gia tăng.

## Bản kỹ thuật 0.4 — đọc sâu và adapter

- adapter RAGFlow;
- PageIndex sau bước chọn sách;
- bộ định tuyến câu hỏi;
- evidence pack tối ưu.

## Bản kỹ thuật 0.5 — graph theo nhu cầu

Chỉ khi có use case rõ:

- LightRAG cho quan hệ xuyên nguồn;
- Graphiti cho tri thức thay đổi theo thời gian;
- Cognee nếu cần bộ nhớ tác tử tổng quát.

## Bản sản xuất 1.0

- web UI;
- MCP server;
- phân quyền;
- sao lưu;
- giám sát;
- kiểm thử tự động;
- tài liệu vận hành;
- chính sách nâng cấp động cơ.

## Thứ tự ưu tiên

1. đúng nguồn;
2. đúng cấu trúc;
3. đúng truy hồi;
4. ít context;
5. tích lũy tri thức;
6. graph và tự động hoá nâng cao.
