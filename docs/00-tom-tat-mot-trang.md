# Tóm tắt một trang

## Mục tiêu

Biến kho PDF, EPUB, MOBI thành một thư viện mà AI có thể:

- tìm đúng sách, chương, đoạn, trang;
- tổng hợp nhiều nguồn;
- nhớ lại kết quả nghiên cứu cũ;
- tự tích lũy một Bộ não thứ hai;
- luôn quay lại được nguồn gốc để kiểm chứng;
- giảm tối đa lượng chữ phải gửi vào mô hình AI ở mỗi câu hỏi.

## Phương án tốt nhất

Xây bốn lớp:

1. **Kho nguồn gốc**: PDF/EPUB/MOBI/ảnh trang, giữ nguyên.
2. **Kho dữ liệu chuẩn + RAG**: sách → ấn bản → chương → mục → trang → khối → đoạn tìm kiếm.
3. **Bộ não thứ hai**: các trang tri thức do AI tổng hợp có nguồn, liên kết và lịch sử.
4. **Bộ nhớ làm việc**: gói nhỏ chỉ chứa bằng chứng và tri thức liên quan đến câu hỏi hiện tại.

## Cách xử lý tài liệu

- PDF có chữ tốt: lấy trực tiếp, không OCR.
- PDF scan: OCR theo từng trang.
- Trang dễ: PP-OCRv6.
- Trang khó: PaddleOCR-VL.
- EPUB: lấy XHTML và mục lục trực tiếp.
- MOBI: chuyển sang EPUB/HTML bằng Calibre.

Luôn giữ song song `văn_bản_thô` và `văn_bản_làm_sạch`.

## Cách tìm kiếm

Không chọn một trong hai mà kết hợp:

- tìm theo chữ cho tên riêng, thuật ngữ, câu nguyên văn;
- tìm theo ý nghĩa cho câu hỏi diễn đạt khác từ;
- trộn kết quả;
- dùng bộ xếp hạng lại để chỉ giữ vài đoạn tốt nhất.

AI lớn chỉ nhận một **gói bằng chứng** khoảng vài đoạn thay vì hàng chục đoạn.

## Bộ não thứ hai

Bộ não thứ hai không phải bản sao của sách. Nó là phần tri thức đã được tiêu hoá:

- khái niệm;
- tác giả;
- so sánh;
- điểm đồng thuận;
- điểm mâu thuẫn;
- câu hỏi mở;
- kết quả nghiên cứu trước.

Mỗi khẳng định quan trọng phải biết nó lấy từ đâu. Sách gốc vẫn là trọng tài cuối cùng.

## Công nghệ đề xuất

- Docling/PyMuPDF: đọc tài liệu.
- Calibre: MOBI.
- PaddleOCR: OCR.
- PostgreSQL: dữ liệu mô tả.
- Qdrant hoặc RAGFlow qua bộ chuyển tiếp: kho truy hồi sách.
- Qwen3-Embedding-0.6B: tìm theo ý nghĩa.
- Qwen3-Reranker-0.6B: xếp hạng lại.
- Markdown + Git: Bộ não thứ hai.
- QMD: tìm trong Markdown.
- PageIndex: đọc sâu một số sách dài khi đã chọn được sách.
- MCP/HTTP: giao diện cho AI.

## Quyết định quan trọng nhất

Không để RAGFlow, QMD, Obsidian, PageIndex hay bất kỳ repo nào sở hữu dữ liệu cốt lõi.

Dữ liệu chuẩn + truy nguồn + sổ khẳng định + Bộ não thứ hai phải thuộc repo của mình. Các dự án bên ngoài chỉ là động cơ thay thế được.

## Một câu để nhớ

> **RAG là trí nhớ bằng chứng. Bộ não thứ hai là trí nhớ hiểu biết. Kết hợp cả hai để AI vừa đúng, vừa nhanh, vừa tích lũy được tri thức.**
