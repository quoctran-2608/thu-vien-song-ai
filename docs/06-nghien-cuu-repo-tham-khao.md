# 6. Vai trò các công cụ và dự án tham khảo

**Ngày kiểm chứng gần nhất: 05/10/2026**

> Tài liệu này phân biệt rõ ba điều: **dự án bên ngoài thật sự có gì**, **Thư Viện Sống học gì từ họ**, và **quyết định kiến trúc của chính Thư Viện Sống**. Chi tiết nguồn và phiên bản nằm trong [Báo cáo kiểm chứng công cụ ngày 05/10/2026](16-kiem-chung-cong-cu-2026-10-05.md).

## 6.1. Nguyên tắc sử dụng dự án bên ngoài

Không lấy nguyên một dự án lớn làm “chủ” hệ thống.

Thay vào đó:

- dùng đúng phần nó làm tốt;
- kết nối qua bộ chuyển tiếp;
- giữ dữ liệu chuẩn ở Thư Viện Sống;
- đo chất lượng trên dữ liệu thật;
- có khả năng thay công cụ về sau.

Một tính năng có trong dự án bên ngoài không tự động trở thành một phần kiến trúc của Thư Viện Sống.

---

## 6.2. Docling

### Họ thật sự có gì?

Docling hiện hỗ trợ nhiều định dạng, trong đó có PDF, EPUB, HTML/XHTML, Markdown và nhiều định dạng văn phòng. Nó có thể xuất dữ liệu có cấu trúc và các dạng thuận tiện cho RAG.

### Ta học và dùng gì?

- bảo tồn cấu trúc và thứ tự đọc;
- giảm số bộ đọc tài liệu phải tự viết;
- dùng một biểu diễn trung gian giàu cấu trúc.

### Quyết định

**Docling là ứng viên trình đọc mặc định để thử nghiệm.**

Nhưng kết quả của Docling phải được chuyển vào mô hình dữ liệu chuẩn của Thư Viện Sống. Không để định dạng nội bộ của Docling trở thành nguồn chân lý.

---

## 6.3. PaddleOCR

### Họ thật sự có gì?

PaddleOCR 3.7.0 đã có PP-OCRv6; PaddleOCR-VL-1.6 là tuyến mạnh hơn cho trang có bố cục phức tạp. Tài liệu hiện liệt kê tiếng Việt trong phạm vi hỗ trợ của PP-OCRv6.

### Điểm cần thận trọng

Đã có báo cáo năm 2026 về từ điển PP-OCRv6 thiếu một số ký tự tiếng Việt có dấu. Vì vậy không được xem “có nhãn hỗ trợ tiếng Việt” là bằng chứng đủ về chất lượng tiếng Việt thực tế.

### Quyết định

- không nhận dạng chữ từ ảnh toàn bộ PDF;
- trang thường: thử PP-OCRv6;
- trang khó: thử PaddleOCR-VL-1.6 hoặc phương án mạnh tương đương;
- tiếng Việt: bắt buộc có bộ thử riêng về dấu, từ, thứ tự đọc và trích dẫn;
- câu trích quan trọng có độ tin cậy thấp phải kiểm lại ảnh trang.

---

## 6.4. RAGFlow

### Họ thật sự có gì?

RAGFlow hiện ở nhánh 1.0.0-rc1 tại ngày kiểm tra.

Khả năng **Biên dịch tri thức** đã được xác minh là tính năng thật, gồm các dạng như:

- Wiki;
- Graph;
- Tree;
- PageIndex;
- Mind Map;
- Timeline;
- Skills.

### Ta học và dùng gì?

- RAG tích hợp;
- truy hồi/xếp hạng;
- dẫn nguồn;
- thử các sản phẩm biên dịch tri thức;
- quản lý luồng tác tử nếu phù hợp.

### Quyết định

RAGFlow đứng sau bộ chuyển tiếp:

~~~text
Kho dữ liệu chuẩn
↓
bộ chuyển tiếp
↓
RAGFlow
↓
ứng viên / điểm / tham chiếu / sản phẩm biên dịch
~~~

Không dùng cơ sở dữ liệu của RAGFlow làm nguồn chân lý.

Wiki/Tree/Graph do RAGFlow sinh ra chỉ là **đầu ra máy**, không tự động trở thành Bộ não thứ hai chính thức.

---

## 6.5. Qdrant

### Họ thật sự có gì?

Qdrant hiện không còn chỉ nên được mô tả là “cơ sở dữ liệu véc-tơ”.

Nó hỗ trợ:

- tìm theo ý nghĩa bằng véc-tơ dày;
- tìm theo chữ/thưa, gồm BM25;
- tìm kiếm kết hợp;
- hợp nhất thứ hạng RRF;
- truy vấn nhiều tầng;
- nhiều véc-tơ;
- các luồng xếp hạng lại;
- lượng tử hóa để giảm bộ nhớ.

### Điều thay đổi trong phương án

Trước đây ta có thể cần một bộ máy tìm theo chữ riêng và Qdrant riêng. Hiện Qdrant có thể gom phần lớn chuỗi này vào một nơi.

### Quyết định

**Qdrant là ứng viên mặc định mạnh nhất cho chỉ mục kho nguồn ở bản đầu.**

Phương án thử đầu tiên:

~~~text
tìm theo ý nghĩa (véc-tơ dày)
+
tìm thưa/BM25 theo chữ
↓
RRF
↓
30–50 ứng viên
↓
bộ xếp hạng lại
↓
3–8 bằng chứng
~~~

Chỉ mục Qdrant vẫn phải xây lại được từ kho dữ liệu chuẩn.

---

## 6.6. QMD

### Họ thật sự có gì?

QMD hiện là công cụ tìm kiếm cục bộ cho Markdown với:

- BM25;
- tìm theo ý nghĩa;
- xếp hạng lại;
- MCP;
- SQLite/sqlite-vec;
- giao diện thư viện lập trình ổn định;
- công cụ đánh giá Precision/Recall/MRR/F1.

### Quyết định

QMD phù hợp rõ ràng với **Bộ não thứ hai Markdown**.

Không mặc định dùng QMD làm chỉ mục chính cho toàn bộ kho sách lớn, vì kho nguồn có nhu cầu khác về lọc thông tin kèm theo, truy nguồn và vòng đời chỉ mục.

---

## 6.7. PageIndex

### Họ thật sự có gì?

PageIndex hiện có chế độ chạy cục bộ để lập chỉ mục, truy hồi và trò chuyện trên máy bằng mô hình do người dùng chọn. Tuy nhiên, phạm vi cục bộ hiện **hẹp hơn chế độ đám mây**:

- chế độ cục bộ tập trung vào PDF có lớp chữ;
- không có nhận dạng chữ và hiểu ảnh tích hợp;
- không có thư mục, metadata quản lý và máy chủ MCP như phía đám mây;
- PageIndex File System — lớp tổ chức nhiều tài liệu thành cây — hiện là **tính năng đám mây**.

Vì vậy nhận định “PageIndex File System đã có thể dùng cục bộ” là không chính xác và đã được sửa trong vòng phản biện này.

### Quyết định

Ở bản đầu vẫn dùng:

~~~text
tìm toàn thư viện bằng hệ của Thư Viện Sống
↓
thu hẹp còn vài tài liệu
↓
PageIndex cục bộ
↓
đọc sâu chương / mục / trang
~~~

Cách đặt này còn hợp lý hơn sau khi kiểm chứng lại: PageIndex cục bộ làm tốt vai trò đọc sâu PDF có chữ, còn định tuyến toàn kho và quyền sở hữu metadata vẫn thuộc Thư Viện Sống.

Không dựa vào PageIndex File System cho kiến trúc cục bộ. Nếu sau này cân nhắc tính năng nhiều tài liệu của PageIndex Cloud, phải đánh giá riêng chi phí, quyền riêng tư, nơi lưu dữ liệu và khả năng rời dịch vụ.

---

## 6.8. claude-obsidian

### Họ thật sự có gì?

Dự án thể hiện rất rõ:

- nguồn do người dùng sở hữu;
- nguồn bất biến theo nội dung;
- sổ nguồn;
- sổ khẳng định;
- theo dõi mâu thuẫn và độ độc lập của nguồn;
- nhiều tác tử tạo bản nháp;
- một bộ điều phối áp dụng thay đổi theo giao dịch có thể phục hồi;
- wiki Markdown vẫn hữu ích khi không còn AI.

### Ta học gì?

Ba bài học rất quan trọng:

> **Nguồn sống lâu hơn bản tóm tắt.**

> **Khẳng định phải biết nó dựa vào đâu.**

> **Ghi tri thức phải kiểm toán và phục hồi được.**

### Quyết định

Học mạnh về kiến trúc Bộ não thứ hai và truy nguồn. Không dùng làm bộ nhập kho sách quy mô lớn.

---

## 6.9. obsidian-wiki

### Họ thật sự có gì?

Dự án có:

- vùng nguồn thô;
- nhiều giai đoạn nhập;
- QMD;
- đồng bộ GitHub;
- HTTP/MCP;
- Session Brain;
- đóng gói vault như dịch vụ.

Dự án vẫn tự mô tả là còn sớm.

### Quyết định

Học:

- luồng nguồn → nhập → biên dịch → wiki;
- cập nhật gia tăng;
- cách đưa wiki ra cho AI truy cập.

Không phụ thuộc vào repo này làm lõi.

---

## 6.10. Hermes Agent và LLM Wiki

### Họ thật sự có gì?

Hermes có kỹ năng đóng gói sẵn LLM Wiki, trong đó:

- người dùng chọn nguồn;
- tác tử tóm tắt, liên kết và tổ chức thành Markdown;
- mâu thuẫn được ghi lại;
- tri thức được “biên dịch” một lần để dùng lại;
- có cách nạp dần nội dung theo nhu cầu.

### Ta học gì?

Đây là một bằng chứng thực tế cho hai nguyên tắc:

> **biên dịch tri thức một lần, dùng lại nhiều lần;**

và:

> **chỉ nạp phần cần thiết khi cần.**

### Quyết định

Học mẫu thiết kế. Không dùng Hermes làm chủ kho nguồn.

---

## 6.11. Cognee

### Họ thật sự có gì?

Cognee hiện dùng bốn thao tác cấp cao:

- remember — ghi nhớ;
- recall — nhớ lại;
- improve — cải thiện;
- forget — quên.

Nó xây trí nhớ máy từ nhiều loại dữ liệu bằng đồ thị, véc-tơ và dữ liệu mã.

### Quyết định

Không đưa vào lõi bản đầu.

Có thể dùng sau này làm **trí nhớ máy của tác tử**, qua một giao diện riêng.

Bộ não thứ hai chính thức vẫn là dữ liệu do Thư Viện Sống kiểm soát.

---

## 6.12. LightRAG

### Họ thật sự có gì?

LightRAG kết hợp RAG với đồ thị và hiện có nhiều tùy chọn nhập liệu, chia đoạn, lưu trữ và triển khai cục bộ.

### Quyết định

Không tạo đồ thị toàn thư viện từ ngày đầu.

Chỉ thêm khi bộ câu hỏi thực tế chứng minh truy vấn quan hệ xuyên sách có giá trị đủ lớn.

---

## 6.13. Graphiti

### Họ thật sự có gì?

Graphiti là đồ thị ngữ cảnh có thời gian:

- giữ sự kiện nguồn;
- quan hệ có thời điểm hiệu lực;
- cập nhật gia tăng;
- bảo tồn lịch sử;
- tìm kiếm kết hợp chữ, nghĩa và đồ thị.

### Quyết định

Phù hợp với:

- lịch sử quyết định;
- trạng thái dự án;
- thông tin thay đổi;
- sự kiện;
- quan hệ có vòng đời.

Không phải ưu tiên cho phần lớn sách bất biến.

---

## 6.14. Mem0

### Họ thật sự có gì?

Mem0 là lớp trí nhớ cho tác tử/ứng dụng.

Một điểm cần thận trọng: dự án phân biệt một số kết quả đánh giá của nền tảng quản lý có tối ưu riêng với bản thư viện mã nguồn mở.

### Quyết định

Dùng bổ trợ cho:

- trí nhớ hội thoại;
- trí nhớ người dùng;
- tác tử/nhiệm vụ.

Không dùng làm kho bằng chứng sách có truy nguồn chính xác.

Không lấy kết quả đánh giá của dịch vụ quản lý để suy ra chất lượng của bản mã nguồn mở.

---

## 6.15. Khoj

### Họ thật sự có gì?

Khoj là sản phẩm “bộ não thứ hai” tự lưu trữ được, kết hợp tài liệu, web, tác tử và nghiên cứu.

Giấy phép hiện tại là AGPL-3.0.

### Quyết định

Học:

- trải nghiệm sản phẩm;
- giao diện;
- luồng tài liệu + web + tác tử.

Không sao chép hoặc tích hợp mã vào lõi khi chưa đánh giá nghĩa vụ giấy phép AGPL.

---

## 6.16. Qwen3-Embedding và Qwen3-Reranker

### Qwen3-Embedding-0.6B

Đã xác minh:

- 0,6 tỷ tham số;
- 100+ ngôn ngữ;
- ngữ cảnh 32K;
- tối đa 1024 chiều;
- có thể chọn chiều đầu ra từ 32 đến 1024;
- hỗ trợ Matryoshka;
- Apache-2.0.

**Điều chỉnh quan trọng:** 512 chiều không phải thông số gốc. Nếu dùng 512, đó là cấu hình thử nghiệm do Thư Viện Sống chọn.

### Qwen3-Reranker-0.6B

Đã xác minh:

- 0,6 tỷ tham số;
- 100+ ngôn ngữ;
- ngữ cảnh 32K;
- có chỉ dẫn theo nhiệm vụ.

### Quyết định

Hai mô hình này là cặp ứng viên đầu để đánh giá cục bộ, không phải lựa chọn bất biến.

---

## 6.17. BGE-M3

### Họ thật sự có gì?

BGE-M3 hỗ trợ:

- hơn 100 ngôn ngữ;
- 1024 chiều;
- ngữ cảnh 8192;
- tìm theo ý nghĩa;
- tín hiệu thưa;
- nhiều véc-tơ/ColBERT.

### Quyết định

BGE-M3 phải nằm trong bộ chuẩn so sánh với phương án Qwen3, đặc biệt nếu muốn một mô hình tạo nhiều tín hiệu tìm kiếm.

---

## 6.18. Kiến trúc được điều chỉnh sau vòng kiểm chứng

### Nhập tài liệu

~~~text
PDF / EPUB / MOBI
↓
Docling là ứng viên đọc mặc định
↓
trang có cần nhận dạng chữ?
├── không → dùng chữ gốc
└── có
    ↓
    PP-OCRv6
    ↓
    chưa đạt / bố cục khó
    ↓
    PaddleOCR-VL-1.6 hoặc tuyến dự phòng
↓
KHO DỮ LIỆU CHUẨN
~~~

### Tìm bằng chứng

~~~text
Qdrant
├── tìm theo ý nghĩa (véc-tơ dày)
└── tìm thưa/BM25 theo chữ
      ↓
      RRF
      ↓
30–50 ứng viên
      ↓
Qwen3-Reranker-0.6B
      ↓
3–8 bằng chứng
~~~

BGE-M3 là đường chuẩn so sánh.

### Bộ não thứ hai

~~~text
Markdown + Git
↓
QMD
↓
tìm theo chữ + ý nghĩa + xếp hạng
~~~

### Đọc sâu

~~~text
tìm toàn thư viện
↓
thu hẹp tài liệu
↓
PageIndex
↓
chương / mục / trang
~~~

### Đồ thị và trí nhớ tác tử

Tắt mặc định ở bản đầu:

- LightRAG;
- Graphiti;
- Cognee;
- Mem0.

---

## 6.19. Kết luận

### Nên dùng ngay trong thử nghiệm

- Docling;
- PaddleOCR;
- Qdrant;
- Qwen3-Embedding-0.6B;
- Qwen3-Reranker-0.6B;
- QMD;
- Markdown + Git.

### Nên tích hợp qua bộ chuyển tiếp và thử nghiệm

- RAGFlow;
- PageIndex.

### Nên giữ làm nguồn thiết kế

- claude-obsidian;
- obsidian-wiki;
- Hermes LLM Wiki.

### Nên để giai đoạn sau

- Cognee;
- LightRAG;
- Graphiti;
- Mem0.

### Chỉ tham khảo sản phẩm, chú ý giấy phép

- Khoj.

Kết luận lớn nhất của vòng kiểm chứng:

> **Kiến trúc “dữ liệu chuẩn của mình, công cụ bên ngoài chỉ là bộ máy” vẫn đúng. Những công cụ đã mạnh lên, nhưng điều đó càng làm cho kiến trúc bộ chuyển tiếp và khả năng thay thế trở nên có giá trị.**
