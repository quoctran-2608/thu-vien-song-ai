# 6. Nghiên cứu các repo tham khảo

Tài liệu này ghi lại những repo đáng học nhất và **phần nào nên lấy tư tưởng**, không phải khuyến nghị ghép toàn bộ mã nguồn của chúng vào một siêu-repo.

## 6.1. RAGFlow

Vai trò mạnh:

- RAG đầy đủ;
- quản lý tài liệu;
- truy hồi kết hợp;
- xếp hạng;
- dẫn nguồn;
- tác tử;
- biên dịch tri thức thành các dạng như Wiki, cây, đồ thị, PageIndex.

Điều nên học:

- cách tổ chức một hệ RAG sản xuất;
- cách đánh giá truy hồi;
- ý tưởng “biên dịch tri thức” thay vì chỉ truy hồi thô.

Quyết định của dự án:

- dùng qua bộ chuyển tiếp;
- không để RAGFlow sở hữu duy nhất dữ liệu chuẩn hay Bộ não thứ hai.

## 6.2. Docling

Vai trò mạnh:

- đọc nhiều loại tài liệu;
- bảo tồn cấu trúc;
- hiểu bố cục;
- tạo biểu diễn tài liệu có cấu trúc.

Điều nên học:

- tài liệu phải được chuẩn hoá tốt trước khi nghĩ đến RAG.

Quyết định:

- ứng viên máy đọc mặc định cho PDF/EPUB born-digital.

## 6.3. PaddleOCR

Vai trò mạnh:

- OCR đa ngôn ngữ;
- mô hình nhẹ cho trang dễ;
- VLM cho trang khó và bố cục phức tạp.

Điều nên học:

- OCR theo tầng, không dùng mô hình mạnh cho mọi trang.

## 6.4. QMD

Vai trò mạnh:

- tìm Markdown tại máy;
- từ khóa + ý nghĩa + xếp hạng;
- MCP;
- có tư duy đánh giá chất lượng truy hồi.

Quyết định:

- rất phù hợp cho chỉ mục Bộ não thứ hai.

## 6.5. PageIndex

Vai trò mạnh:

- duyệt tài liệu dài theo cấu trúc cây;
- suy luận chương/mục liên quan.

Quyết định:

- dùng sau khi đã chọn được tài liệu cần đọc;
- không phụ thuộc vào nó cho tìm kiếm toàn kho.

## 6.6. claude-obsidian

Điều đáng học nhất:

- nguồn bất biến;
- AI tổ chức wiki Markdown;
- dữ liệu con người sở hữu;
- thay đổi có thể kiểm toán;
- phân tách mã chương trình và vault tri thức.

Quyết định:

- lấy mạnh tư tưởng vận hành Second Brain.

## 6.7. obsidian-wiki và các LLM Wiki kiểu Karpathy

Điều đáng học:

- nhập nguồn → biên dịch → cập nhật trang cũ;
- liên kết wiki;
- phát hiện mâu thuẫn;
- cập nhật gia tăng;
- chống trùng;
- Git/MCP.

Quyết định:

- dùng làm mẫu cho trình biên dịch Bộ não thứ hai, không làm lõi kho sách.

## 6.8. Hermes Agent — LLM Wiki

Ý nghĩa:

- mô hình LLM Wiki đã trở thành một kỹ năng tác tử được đóng gói, không còn chỉ là ý tưởng cá nhân.

Điều nên học:

- tác tử có thể coi wiki là trí nhớ đã biên dịch để tránh tiêu hoá lại nguồn thô ở mỗi lần hỏi.

## 6.9. Cognee

Vai trò mạnh:

- trí nhớ lâu dài cho tác tử;
- remember/recall/improve/forget;
- thực thể, quan hệ, vector;
- chắt lọc phiên làm việc thành trí nhớ lâu dài.

Quyết định:

- học API tư duy;
- chưa đưa vào lõi bản đầu để tránh trùng kho dữ liệu.

## 6.10. LightRAG

Vai trò mạnh:

- vector + đồ thị tri thức;
- truy vấn quan hệ xuyên tài liệu;
- cập nhật gia tăng.

Quyết định:

- chỉ bật cho miền có nhu cầu graph thật sự.

## 6.11. Graphiti

Vai trò mạnh:

- đồ thị có yếu tố thời gian;
- phù hợp thông tin thay đổi theo thời gian.

Quyết định:

- hữu ích cho lịch sử quyết định/nghiên cứu động;
- không cần cho phần lớn sách bất biến ở bản đầu.

## 6.12. Mem0

Vai trò mạnh:

- trí nhớ của tác tử và người dùng;
- giảm context nhờ lưu những điều đáng nhớ.

Quyết định:

- không phải lõi của thư viện sách;
- có thể dùng về sau cho trí nhớ phiên/người dùng.

## 6.13. Khoj

Vai trò mạnh:

- Second Brain dùng được ngay;
- hỏi nhiều loại tài liệu;
- tự lưu trữ;
- agent/research.

Quyết định:

- tốt để tham khảo trải nghiệm sản phẩm;
- không thay thế mô hình dữ liệu chuẩn riêng.

## 6.14. Kết luận nghiên cứu repo

Không repo nào nên được bê nguyên làm “hệ điều hành tri thức” duy nhất.

Cách tốt nhất là:

- Docling/PaddleOCR xử lý nguồn;
- RAGFlow/Qdrant làm động cơ bằng chứng;
- QMD phục vụ wiki;
- PageIndex đọc sâu;
- LightRAG/Graphiti là tuỳ chọn;
- lõi của mình giữ dữ liệu chuẩn, truy nguồn, sổ khẳng định và quy trình cập nhật.
