# 13. Tài liệu và dự án tham khảo

> Danh mục này là nơi lưu nguồn chính thức. Các thông tin dễ thay đổi như phiên bản, giấy phép, tính năng mới và tình trạng dự án sẽ được kiểm chứng lại trong vòng rà nguồn bên ngoài trước khi chốt tài liệu.

## 13.1. Cách ghi một dự án tham khảo

Mỗi dự án nên có:

```text
Tên
Vai trò trong kiến trúc
Điểm đáng học
Phần không dùng làm lõi
Ngày kiểm tra gần nhất
Phiên bản/tình trạng khi kiểm tra
Đường dẫn chính thức
```

## 13.2. Xử lý tài liệu và nhận dạng chữ

- Docling — https://github.com/docling-project/docling
- PaddleOCR — https://github.com/PaddlePaddle/PaddleOCR
- Calibre — https://calibre-ebook.com/
- PyMuPDF — https://github.com/pymupdf/PyMuPDF
- Marker — https://github.com/datalab-to/marker
- MinerU — https://github.com/opendatalab/MinerU

## 13.3. Tìm kiếm và RAG

- RAGFlow — https://github.com/infiniflow/ragflow
- Qdrant — https://github.com/qdrant/qdrant
- PageIndex — https://github.com/VectifyAI/PageIndex
- QMD — https://github.com/tobi/qmd

## 13.4. Bộ não thứ hai và trí nhớ tác tử

- claude-obsidian — https://github.com/AgriciDaniel/claude-obsidian
- obsidian-wiki — https://github.com/Ar9av/obsidian-wiki
- Hermes Agent — https://github.com/NousResearch/hermes-agent
- Cognee — https://github.com/topoteretes/cognee
- Mem0 — https://github.com/mem0ai/mem0
- Khoj — https://github.com/khoj-ai/khoj

## 13.5. Đồ thị

- LightRAG — https://github.com/HKUDS/LightRAG
- Graphiti — https://github.com/getzep/graphiti

## 13.6. Mô hình biểu diễn ý nghĩa và xếp hạng

Các ứng viên từng được nghiên cứu gồm:

- Qwen3-Embedding;
- Qwen3-Reranker;
- BGE-M3.

Không chốt mô hình chỉ dựa trên bảng xếp hạng chung. Phải chạy bộ kiểm thử của thư viện.

## 13.7. Các ý tưởng nghiên cứu liên quan

- Contextual Retrieval của Anthropic;
- RAPTOR và các cách truy hồi phân tầng;
- chia đoạn theo cấu trúc;
- kiểm tra quan hệ khẳng định–bằng chứng;
- tìm bằng chứng phản bác;
- nghiên cứu theo kho nguồn đóng.

## 13.8. Nguyên tắc sử dụng nguồn tham khảo

Repo bên ngoài thay đổi liên tục.

Trước khi triển khai phải kiểm tra lại:

- giấy phép;
- phiên bản;
- yêu cầu phần cứng;
- giao diện lập trình;
- khả năng chạy cục bộ;
- hỗ trợ tiếng Việt;
- độ phù hợp với dữ liệu thật;
- phần nào là mã nguồn mở và phần nào là dịch vụ riêng.

Không đưa một tính năng vào kiến trúc chỉ vì dự án bên ngoài quảng bá nó.
