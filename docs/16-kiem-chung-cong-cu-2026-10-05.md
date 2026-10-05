# 16. Kiểm chứng công cụ và dự án tham khảo — 05/10/2026

Tài liệu này ghi lại vòng kiểm chứng bên ngoài của **Bước 6**, thực hiện ngày **05/10/2026**.

Mục tiêu không phải chạy theo công nghệ mới nhất, mà là trả lời bốn câu:

1. Công cụ hoặc dự án hiện thật sự có gì?
2. Điều gì trong tài liệu cũ đã lỗi thời hoặc chưa chính xác?
3. Thư Viện Sống nên học hoặc dùng phần nào?
4. Phần nào tuyệt đối không được giao cho công cụ bên ngoài sở hữu?

Thông tin phiên bản và tính năng dưới đây là ảnh chụp tại ngày kiểm tra. Khi triển khai thật phải kiểm tra lại lần nữa và chạy bộ đánh giá của chính dự án.

---

## 1. Kết luận nhanh

| Thành phần | Tình trạng đã kiểm chứng | Vai trò khuyến nghị |
|---|---|---|
| Docling | Gói 2.131.0; MIT; hỗ trợ nhiều định dạng | Ứng viên trình đọc/chuẩn hóa mặc định |
| PaddleOCR | 3.7.0; PP-OCRv6; PaddleOCR-VL-1.6; Apache-2.0 | Nhận dạng chữ theo từng trang, có tuyến dự phòng |
| RAGFlow | 1.0.0-rc1; Apache-2.0; có Biên dịch tri thức | Bộ máy RAG qua bộ chuyển tiếp, không làm chủ dữ liệu |
| Qdrant | 1.19.1; Apache-2.0 | Ứng viên mạnh cho hệ tìm bằng chứng mặc định |
| QMD | Gói @tobilu/qmd 2.8.3; MIT | Tìm kiếm cục bộ cho Bộ não thứ hai Markdown |
| PageIndex | 0.2.20; MIT; có chế độ cục bộ | Đọc sâu tài liệu dài; chưa làm nền móng toàn kho ở bản đầu |
| claude-obsidian | MIT | Nguồn ý tưởng về nguồn bất biến, sổ nguồn, sổ khẳng định và ghi an toàn |
| obsidian-wiki | MIT; bản phát hành gần nhất v2026.07.10 | Nguồn ý tưởng về wiki do AI duy trì và cập nhật gia tăng |
| Hermes Agent / LLM Wiki | MIT; Hermes v0.21.3; kỹ năng LLM Wiki 2.1.0 | Mẫu “biên dịch tri thức một lần, dùng lại nhiều lần” |
| Cognee | 1.6.2; Apache-2.0 | Trí nhớ máy cho tác tử, tùy chọn về sau |
| LightRAG | 1.5.7; MIT | Đồ thị + RAG khi bài toán quan hệ chứng minh được giá trị |
| Graphiti | 0.30.2; Apache-2.0 | Đồ thị có thời gian cho dữ liệu thay đổi |
| Mem0 | Python SDK 2.2.1; Apache-2.0 | Trí nhớ tác tử/người dùng, không làm kho bằng chứng sách |
| Khoj | 2.0.0-beta.28; AGPL-3.0 | Tham khảo trải nghiệm sản phẩm, thận trọng khi dùng lại mã |
| Qwen3-Embedding-0.6B | Apache-2.0; 100+ ngôn ngữ; 32K; tối đa 1024 chiều | Ứng viên đầu cho biểu diễn ý nghĩa |
| Qwen3-Reranker-0.6B | Apache-2.0; 100+ ngôn ngữ; 32K | Ứng viên đầu cho xếp hạng lại |
| BGE-M3 | MIT; 100+ ngôn ngữ; 1024 chiều; 8192 đơn vị ngữ cảnh | Đường chuẩn so sánh, nhất là khi muốn nhiều tín hiệu tìm kiếm |

---

# 2. Docling

## 2.1. Điều đã xác minh

Ngày 05/10/2026, mã nguồn chính của Docling khai báo phiên bản 2.131.0, giấy phép MIT và trạng thái sản xuất ổn định.

Docling hiện hỗ trợ nhiều định dạng, trong đó có:

- PDF;
- DOCX/XLSX/PPTX;
- EPUB;
- Markdown;
- AsciiDoc;
- HTML/XHTML;
- ảnh;
- nhiều định dạng văn phòng cũ qua LibreOffice;
- một số định dạng âm thanh/video khi dùng phần mở rộng phù hợp.

Nó có thể xuất Markdown, HTML, JSON, văn bản và dữ liệu đoạn phục vụ RAG.

Nguồn chính thức:

- https://github.com/docling-project/docling
- https://github.com/docling-project/docling/blob/main/docs/usage/supported_formats.md
- https://github.com/docling-project/docling/blob/main/packages/docling/pyproject.toml

## 2.2. Điều chỉnh so với tài liệu cũ

Tài liệu cũ coi Docling chủ yếu là trình đọc PDF/EPUB có cấu trúc. Điều đó đúng nhưng đã hẹp.

Docling hiện đủ rộng để thử làm **trình đọc mặc định** cho nhiều định dạng, giảm số bộ đọc tự viết.

## 2.3. Quyết định cho Thư Viện Sống

Nên thử Docling làm trình đọc mặc định, nhưng:

- kết quả Docling phải được chuyển sang mô hình dữ liệu chuẩn của Thư Viện Sống;
- không lưu dữ liệu duy nhất ở định dạng riêng của Docling;
- EPUB vẫn phải bảo tồn cấu trúc chương/mục và thông tin gốc;
- phải đo chính xác trang, thứ tự đọc, chú thích và bảng trên tập dữ liệu thật.

---

# 3. PaddleOCR

## 3.1. Điều đã xác minh

PaddleOCR 3.7.0 được phát hành ngày 11/06/2026 với PP-OCRv6.

PP-OCRv6 có nhiều cỡ mô hình và tài liệu chính thức liệt kê hỗ trợ tiếng Việt bằng mã vi.

PaddleOCR-VL-1.6 được phát hành ngày 28/05/2026. Tài liệu PaddleOCR mô tả dòng VL là mô hình khoảng 0,9 tỷ tham số, hỗ trợ 109 ngôn ngữ và các thành phần phức tạp như chữ, bảng, công thức và biểu đồ.

PaddleOCR dùng giấy phép Apache-2.0.

Nguồn:

- https://github.com/PaddlePaddle/PaddleOCR/releases
- https://github.com/PaddlePaddle/PaddleOCR/blob/main/docs/version3.x/pipeline_usage/OCR.en.md
- https://github.com/PaddlePaddle/PaddleOCR/blob/main/docs/index.en.md

## 3.2. Lưu ý đặc biệt với tiếng Việt

Tài liệu hiện hành liệt kê PP-OCRv6 hỗ trợ tiếng Việt.

Tuy nhiên, issue #18254 ngày 10/07/2026 báo cáo rằng các từ điển nhận dạng PP-OCRv6 trên nhánh chính khi đó thiếu nhiều ký tự tiếng Việt có dấu. Issue đã đóng, nhưng trang issue không cung cấp đủ bằng chứng để kết luận chắc chắn vấn đề đã được giải quyết trong mọi gói/mô hình hiện hành.

Nguồn:

- https://github.com/PaddlePaddle/PaddleOCR/issues/18254

Vì vậy:

> **Không được mặc định xem PP-OCRv6 là đã đạt chuẩn tiếng Việt chỉ vì tài liệu ghi hỗ trợ vi.**

## 3.3. Quyết định

Giữ kiến trúc nhiều tầng:

1. trang có chữ tốt → lấy chữ trực tiếp;
2. trang cần nhận dạng chữ thông thường → thử PP-OCRv6;
3. trang bố cục khó → PaddleOCR-VL-1.6 hoặc phương án mạnh tương đương;
4. tiếng Việt → bắt buộc chạy bộ thử dấu tiếng Việt trước khi chốt;
5. nếu PP-OCRv6 chưa đạt → dùng tuyến dự phòng dựa trên kết quả kiểm thử.

---

# 4. RAGFlow

## 4.1. Điều đã xác minh

RAGFlow hiện khai báo phiên bản 1.0.0-rc1, phát hành ngày 29/09/2026.

RAGFlow dùng Apache-2.0 và hỗ trợ triển khai cục bộ.

Từ v0.27.0 ngày 19/08/2026, RAGFlow đưa vào **Knowledge Compilation — Biên dịch tri thức**, hỗ trợ ở mức tài liệu và tập dữ liệu:

- Wiki;
- Graph;
- Tree;
- PageIndex;
- Mind Map;
- Timeline;
- Skills.

GraphRAG và RAPTOR cũ đã được thay bằng Graph và Tree trong giao diện Biên dịch tri thức.

Nguồn:

- https://github.com/infiniflow/ragflow
- https://github.com/infiniflow/ragflow/blob/main/docs/release_notes.md
- https://github.com/infiniflow/ragflow/blob/main/docs/guides/knowledge_compilation/overview.md
- https://github.com/infiniflow/ragflow/blob/main/pyproject.toml

## 4.2. Điều chỉnh so với tài liệu cũ

Khẳng định “RAGFlow có Wiki/Tree/PageIndex/Graph...” hiện đã được xác minh là **tính năng thật**, không phải suy đoán.

Tuy nhiên đây là sản phẩm do RAGFlow tạo ra từ dữ liệu của nó. Điều này không làm thay đổi nguyên tắc của Thư Viện Sống.

## 4.3. Quyết định

Dùng RAGFlow qua bộ chuyển tiếp:

~~~text
Kho dữ liệu chuẩn
↓
bộ chuyển tiếp RAGFlow
↓
RAGFlow
↓
ứng viên / điểm / tham chiếu / sản phẩm biên dịch tri thức
~~~

Không để:

- cơ sở dữ liệu riêng của RAGFlow là nguồn chân lý;
- Wiki do RAGFlow sinh ra tự động thay thế Bộ não thứ hai chính thức;
- phiên bản 1.0.0-rc1 đi thẳng vào sản xuất mà chưa qua bộ kiểm thử.

Biên dịch tri thức rất đáng thử như **bộ máy đề xuất** cho Wiki/Tree/PageIndex, nhưng đầu ra quan trọng phải qua quy trình kiểm chứng và đề xuất của Thư Viện Sống.

---

# 5. Qdrant

## 5.1. Điều đã xác minh

Qdrant hiện khai báo phiên bản 1.19.1, giấy phép Apache-2.0.

Điểm quan trọng: **Qdrant hiện không còn nên được mô tả đơn giản là “cơ sở dữ liệu véc-tơ”.**

Qdrant hỗ trợ:

- véc-tơ dày cho tìm theo ý nghĩa;
- véc-tơ thưa/BM25 cho tìm theo chữ;
- tìm kiếm kết hợp;
- hợp nhất thứ hạng RRF;
- RRF có trọng số;
- DBSF;
- truy vấn nhiều tầng;
- nhiều véc-tơ;
- luồng xếp hạng lại kiểu late-interaction/ColBERT;
- nhiều dạng lượng tử hóa để giảm bộ nhớ.

Tài liệu lượng tử hóa hiện nêu scalar có thể giảm bộ nhớ khoảng 4 lần trong cấu hình thông dụng; các kỹ thuật khác có thể giảm mạnh hơn nhưng đổi lại tốc độ/chất lượng.

Nguồn:

- https://github.com/qdrant/qdrant
- https://qdrant.tech/documentation/search/hybrid-queries/
- https://qdrant.tech/documentation/tutorials-basics/reranking-hybrid-search/
- https://qdrant.tech/documentation/manage-data/quantization/

## 5.2. Điều chỉnh kiến trúc

Trước đây ta hình dung:

~~~text
BM25 riêng
+
Qdrant véc-tơ
+
bộ hợp nhất riêng
~~~

Hiện nay Qdrant có khả năng thực hiện phần lớn chuỗi này trong cùng một bộ máy.

Điều này giúp bản đầu đơn giản hơn.

## 5.3. Quyết định

**Qdrant trở thành ứng viên mặc định mạnh nhất cho chỉ mục kho sách ở bản đầu**, với phương án thử:

~~~text
dense
+
BM25/sparse
↓
RRF
↓
30–50 ứng viên
↓
Qwen3-Reranker hoặc bộ xếp hạng khác
↓
3–8 bằng chứng
~~~

Dữ liệu chuẩn vẫn ở ngoài Qdrant và chỉ mục phải có thể xây lại.

---

# 6. QMD

## 6.1. Điều đã xác minh

File package.json trên nhánh chính hiện khai báo @tobilu/qmd phiên bản 2.8.3, giấy phép MIT, yêu cầu Node >=22.

QMD mô tả chính nó là hệ tìm kiếm cục bộ cho tài liệu Markdown với:

- BM25;
- tìm theo véc-tơ;
- xếp hạng lại bằng mô hình;
- MCP;
- SQLite/sqlite-vec.

Từ QMD 2.0, dự án công bố giao diện thư viện ổn định QMDStore, không còn chỉ là công cụ dòng lệnh.

QMD cũng có lệnh benchmark đo Precision/Recall/MRR/F1 cho các tuyến tìm kiếm.

Nguồn:

- https://github.com/tobi/qmd
- https://github.com/tobi/qmd/blob/main/package.json
- https://github.com/tobi/qmd/blob/main/CHANGELOG.md

## 6.2. Quyết định

QMD phù hợp hơn trước đây cho **Bộ não thứ hai Markdown**:

- chạy cục bộ;
- vừa tìm theo chữ vừa theo ý nghĩa;
- có xếp hạng lại;
- có MCP;
- có giao diện lập trình;
- có công cụ đánh giá.

Không mặc định dùng QMD làm chỉ mục chính cho hàng triệu đoạn sách. Lý do không phải QMD “không làm được”, mà vì kho nguồn cần vòng đời chỉ mục, lọc thông tin kèm theo, truy nguồn và khả năng mở rộng riêng.

---

# 7. PageIndex

## 7.1. Điều đã xác minh

PageIndex mới nhất trên GitHub tại thời điểm kiểm tra là v0.2.20, phát hành 28/09/2026, giấy phép MIT.

Dự án tự mô tả là hệ truy hồi dựa trên suy luận, không cần cơ sở dữ liệu véc-tơ và không chia đoạn theo kiểu RAG truyền thống.

Từ tháng 08/2026:

- bộ công cụ phát triển hỗ trợ chế độ cục bộ;
- có thể lập chỉ mục, truy hồi và trò chuyện trên máy;
- PageIndex Flash là cách dựng cây nhanh mặc định cho PDF có chữ;
- có PageIndex File System để tạo lớp cây ở mức nhiều tài liệu.

Nguồn:

- https://github.com/VectifyAI/PageIndex
- https://github.com/VectifyAI/PageIndex/releases

## 7.2. Điều chỉnh so với nghiên cứu cũ

Nhận định cũ rằng phần File System nhiều tài liệu chủ yếu là phía dịch vụ đã lỗi thời một phần: repo hiện công bố bộ công cụ cục bộ và lớp nhiều tài liệu.

## 7.3. Quyết định

Dù khả năng đã mạnh hơn, bản 0.x của PageIndex vẫn còn trẻ.

Ở phiên bản đầu:

> **vẫn ưu tiên dùng PageIndex sau khi hệ tìm kiếm rẻ đã thu hẹp còn một số tài liệu.**

Sau này có thể đo PageIndex File System như một bộ định tuyến toàn kho. Chỉ thay kiến trúc khi bộ thử thực tế chứng minh tốt hơn.

---

# 8. claude-obsidian

## Điều đã xác minh

Dự án dùng MIT.

README và tài liệu hiện có các cơ chế rất gần triết lý Thư Viện Sống:

- nguồn cục bộ do người dùng sở hữu;
- bản nguồn bất biến theo nội dung;
- sổ nguồn;
- sổ khẳng định;
- theo dõi độ mới, độ độc lập và mâu thuẫn;
- nhiều tác tử tạo bản nháp;
- một bộ điều phối áp dụng một giao dịch có thể phục hồi;
- Markdown vẫn hữu ích khi không có tác tử.

Nguồn:

- https://github.com/AgriciDaniel/claude-obsidian
- https://github.com/AgriciDaniel/claude-obsidian/blob/main/WIKI.md
- https://github.com/AgriciDaniel/claude-obsidian/blob/main/agents/wiki-ingest.md

## Quyết định

Đây là **nguồn ý tưởng kiến trúc rất mạnh**, đặc biệt cho:

- nguồn bất biến;
- sổ nguồn/sổ khẳng định;
- nguồn độc lập;
- ghi theo giao dịch;
- Bộ não thứ hai con người đọc được.

Không dùng nó làm bộ nhập kho sách lớn.

---

# 9. obsidian-wiki

## Điều đã xác minh

Repo dùng MIT; bản phát hành gần nhất được GitHub liệt kê là v2026.07.10.

Tài liệu hiện nêu:

- bốn giai đoạn nhập;
- thư mục _raw làm vùng nguồn thô;
- QMD cho tìm kiếm;
- GitHub sync;
- HTTP/MCP;
- Session Brain;
- triển khai vault như dịch vụ trí nhớ bằng Docker.

README cũng tự ghi rằng dự án còn sớm.

Nguồn:

- https://github.com/Ar9av/obsidian-wiki
- https://github.com/Ar9av/obsidian-wiki/releases

## Quyết định

Học:

- cập nhật gia tăng;
- vùng nguồn thô;
- cách kết nối wiki với AI;
- cách đóng gói vault như dịch vụ.

Không phụ thuộc vào repo này làm lõi.

---

# 10. Hermes Agent và LLM Wiki

## Điều đã xác minh

Hermes Agent dùng MIT. Bản phát hành mới nhất được kiểm tra là v0.21.3, ngày 14/09/2026.

Hermes có kỹ năng đóng gói sẵn **LLM Wiki 2.1.0**, mô tả trực tiếp mô hình:

- wiki là thư mục Markdown;
- người dùng chọn nguồn;
- tác tử tóm tắt, liên kết, sắp xếp;
- tri thức được “biên dịch” một lần thay vì tìm lại từ đầu mỗi câu hỏi;
- mâu thuẫn được ghi nhận;
- wiki có thể kiểm tra sức khỏe.

Hermes cũng có kiểu “cơ sở tri thức” dùng cách tiết lộ dần: phần cốt lõi nhỏ, các chương/chủ đề nằm trong references và chỉ nạp khi cần.

Nguồn:

- https://github.com/NousResearch/hermes-agent
- https://github.com/NousResearch/hermes-agent/blob/main/website/docs/user-guide/skills/bundled/research/research-llm-wiki.md
- https://github.com/NousResearch/hermes-agent/blob/main/website/docs/user-guide/features/skills.md

## Quyết định

Đây là bằng chứng mạnh rằng ý tưởng:

> **biên dịch tri thức một lần + đọc theo nhu cầu**

đã trở thành một mẫu thiết kế thực tế.

Học mô hình, không biến Hermes thành nền tảng lưu nguồn của thư viện.

---

# 11. Cognee

## Điều đã xác minh

Cognee v1.6.2 phát hành 29/09/2026, Apache-2.0.

Cognee hiện mô tả bốn thao tác cấp cao:

- remember — ghi nhớ;
- recall — nhớ lại;
- improve — cải thiện;
- forget — quên.

Nó xây trí nhớ kết nối từ văn bản, mã nguồn và hội thoại; dùng đồ thị, véc-tơ và dữ liệu mã; có thể chạy cục bộ trong nhiều luồng.

Nguồn:

- https://github.com/topoteretes/cognee
- https://github.com/topoteretes/cognee/releases

## Quyết định

Không đưa vào lõi v0.1–0.3.

Có thể dùng về sau cho **trí nhớ máy của tác tử**, qua giao diện riêng.

Bộ não thứ hai chính thức vẫn là dữ liệu Markdown + sổ khẳng định + truy nguồn của Thư Viện Sống.

---

# 12. LightRAG

## Điều đã xác minh

LightRAG v1.5.7, phát hành 02/09/2026, MIT.

Dự án hiện có:

- RAG kết hợp đồ thị;
- nhập đa phương thức thông qua RagAnything/Docling/MinerU;
- nhiều chiến lược chia đoạn;
- triển khai cục bộ embedding, xếp hạng và kho lưu bằng Docker;
- WebUI và nhiều bộ lưu trữ.

Nguồn:

- https://github.com/HKUDS/LightRAG
- https://github.com/HKUDS/LightRAG/releases

## Quyết định

Không tạo đồ thị toàn thư viện từ ngày đầu.

Chỉ thêm LightRAG khi bộ câu hỏi thực tế chứng minh những truy vấn quan hệ xuyên sách không được giải quyết tốt bằng RAG + Bộ não thứ hai.

---

# 13. Graphiti

## Điều đã xác minh

Graphiti v0.30.2, Apache-2.0.

Nó là thư viện xây **đồ thị ngữ cảnh có thời gian**:

- sự kiện làm nguồn gốc;
- quan hệ có thời điểm hiệu lực;
- dữ liệu mới được nhập gia tăng;
- giữ lịch sử thay vì ghi đè sự thật cũ;
- tìm kiếm kết hợp nghĩa + BM25 + duyệt đồ thị;
- hỗ trợ nhiều bộ máy đồ thị;
- có MCP thử nghiệm.

Nguồn:

- https://github.com/getzep/graphiti
- https://github.com/getzep/graphiti/releases
- https://github.com/getzep/graphiti/blob/main/mcp_server/README.md

## Quyết định

Rất phù hợp với:

- lịch sử quyết định;
- thông tin thay đổi;
- trạng thái dự án;
- sự kiện;
- quan hệ có vòng đời.

Không cần cho đa số sách bất biến trong bản đầu.

---

# 14. Mem0

## Điều đã xác minh

Repo dùng Apache-2.0. GitHub hiện liệt kê Python SDK v2.2.1.

Mem0 là lớp trí nhớ cho tác tử/ứng dụng.

Một lưu ý quan trọng: README của Mem0 nói rõ một số kết quả benchmark mới dùng **nền tảng quản lý của Mem0 có tối ưu độc quyền không nằm trong SDK mã nguồn mở**.

Nguồn:

- https://github.com/mem0ai/mem0
- https://github.com/mem0ai/mem0/releases

## Quyết định

Mem0 là lựa chọn bổ trợ cho:

- trí nhớ người dùng;
- trí nhớ hội thoại;
- nhiệm vụ/tác tử.

Không dùng làm kho nguồn sách có trích dẫn chính xác.

Không lấy benchmark của dịch vụ quản lý để suy ra chất lượng của bản mã nguồn mở.

---

# 15. Khoj

## Điều đã xác minh

Khoj là “AI second brain” tự lưu trữ được, hỗ trợ tài liệu, web, tác tử và nghiên cứu sâu.

Bản phát hành mới nhất được GitHub liệt kê là 2.0.0-beta.28 ngày 26/03/2026.

Giấy phép repo là **AGPL-3.0**.

Nguồn:

- https://github.com/khoj-ai/khoj
- https://github.com/khoj-ai/khoj/releases
- https://github.com/khoj-ai/khoj/blob/master/LICENSE

## Quyết định

Dùng Khoj để học:

- trải nghiệm sản phẩm;
- giao diện người dùng;
- luồng tự lưu trữ;
- cách gắn tài liệu + web + tác tử.

Không sao chép hoặc tích hợp mã trực tiếp vào lõi mà chưa đánh giá nghĩa vụ AGPL.

---

# 16. Qwen3-Embedding và Qwen3-Reranker

## 16.1. Qwen3-Embedding-0.6B

Model card chính thức hiện ghi:

- 0,6 tỷ tham số;
- 100+ ngôn ngữ;
- ngữ cảnh 32K;
- chiều véc-tơ tối đa 1024;
- hỗ trợ chọn chiều đầu ra từ 32 đến 1024;
- hỗ trợ Matryoshka;
- Apache-2.0.

Nguồn:

- https://huggingface.co/Qwen/Qwen3-Embedding-0.6B

### Sửa một nhầm lẫn quan trọng

Nếu tài liệu từng nói “Qwen3-Embedding-0.6B là mô hình 512 chiều” thì câu đó **không chính xác**.

Thông số gốc là tối đa **1024 chiều**.

Ta có thể chọn **512 chiều** như một cấu hình thử nghiệm để giảm bộ nhớ nhờ khả năng Matryoshka, nhưng 512 là **quyết định của Thư Viện Sống**, không phải kích thước gốc của mô hình.

## 16.2. Qwen3-Reranker-0.6B

Model card ghi:

- 0,6 tỷ tham số;
- 100+ ngôn ngữ;
- ngữ cảnh 32K;
- hỗ trợ chỉ dẫn theo nhiệm vụ;
- Apache-2.0.

Nguồn:

- https://huggingface.co/Qwen/Qwen3-Reranker-0.6B

## Quyết định

Hai mô hình 0.6B vẫn là **điểm khởi đầu hợp lý để đánh giá cục bộ**.

Không chốt vì bảng xếp hạng. Phải đo trên câu hỏi tiếng Việt và kho sách thật.

---

# 17. BGE-M3

## Điều đã xác minh

BGE-M3:

- MIT;
- 100+ ngôn ngữ;
- 1024 chiều;
- ngữ cảnh 8192;
- hỗ trợ đồng thời:
  - dense — tìm theo ý nghĩa;
  - sparse — tìm theo chữ/thưa;
  - multi-vector/ColBERT — nhiều véc-tơ để so khớp chi tiết.

Nhóm phát triển khuyến nghị tìm kiếm kết hợp + xếp hạng lại.

Nguồn:

- https://huggingface.co/BAAI/bge-m3
- https://github.com/FlagOpen/FlagEmbedding

## Quyết định

BGE-M3 phải nằm trong bộ chuẩn so sánh.

Nó đặc biệt đáng thử nếu muốn một mô hình duy nhất tạo nhiều tín hiệu tìm kiếm.

---

# 18. Kiến trúc kỹ thuật được chốt lại sau vòng kiểm chứng

## 18.1. Nhập tài liệu

~~~text
PDF / EPUB / MOBI
↓
Docling là ứng viên đọc mặc định
↓
trang nào cần OCR?
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

Tiếng Việt phải có bộ thử riêng.

## 18.2. Tìm bằng chứng

Phương án thử đầu tiên:

~~~text
Qdrant
├── dense
└── sparse/BM25
      ↓
      RRF
      ↓
30–50 ứng viên
      ↓
Qwen3-Reranker-0.6B
      ↓
3–8 bằng chứng
~~~

BGE-M3 là đối chứng mạnh.

RAGFlow là tuyến tích hợp thay thế/đầy đủ hơn, không phải nguồn chân lý.

## 18.3. Bộ não thứ hai

~~~text
Markdown + Git
↓
QMD
↓
tìm theo chữ + ý nghĩa + xếp hạng
~~~

claude-obsidian, obsidian-wiki và Hermes LLM Wiki là nguồn thiết kế, không phải nơi sở hữu dữ liệu.

## 18.4. Đọc sâu

~~~text
tìm toàn thư viện
↓
thu hẹp tài liệu
↓
PageIndex
↓
chương/mục/trang
~~~

Có thể đánh giá PageIndex File System ở giai đoạn sau.

## 18.5. Đồ thị và trí nhớ tác tử

Tắt mặc định:

~~~text
LightRAG
Graphiti
Cognee
Mem0
~~~

Chỉ bật khi bài toán và bộ đánh giá chứng minh giá trị.

---

# 19. Quyết định cuối của Bước 6

## Nên dùng ngay trong thử nghiệm

- Docling;
- PaddleOCR;
- Qdrant;
- Qwen3-Embedding-0.6B;
- Qwen3-Reranker-0.6B;
- QMD;
- Markdown + Git.

## Nên tích hợp qua bộ chuyển tiếp và thử nghiệm

- RAGFlow;
- PageIndex.

## Nên giữ làm nguồn thiết kế

- claude-obsidian;
- obsidian-wiki;
- Hermes LLM Wiki.

## Nên để giai đoạn sau

- Cognee;
- LightRAG;
- Graphiti;
- Mem0.

## Chỉ tham khảo sản phẩm, chú ý giấy phép

- Khoj.

---

# 20. Những điều Bước 6 đã sửa trong nhận thức

1. **Qdrant không còn chỉ là kho véc-tơ**; nó có thể đảm nhiệm phần lớn tìm kiếm kết hợp ở bản đầu.
2. **PageIndex nay có chế độ cục bộ và lớp nhiều tài liệu**, nhưng vẫn chưa đủ lý do để bỏ kiến trúc tìm rẻ trước, đọc sâu sau.
3. **RAGFlow Biên dịch tri thức là tính năng thật**, không còn là suy đoán.
4. **QMD đã có giao diện thư viện ổn định và công cụ đánh giá**, nên phù hợp hơn nữa với Bộ não thứ hai.
5. **Docling hỗ trợ trực tiếp EPUB và nhiều định dạng**, có thể làm trình đọc mặc định rộng hơn dự kiến.
6. **PP-OCRv6 liệt kê tiếng Việt nhưng đã có báo cáo vấn đề với ký tự có dấu**, nên đánh giá tiếng Việt là bắt buộc.
7. **Qwen3-Embedding-0.6B có tối đa 1024 chiều, không phải cố định 512**; 512 chỉ nên là một cấu hình thử nghiệm.
8. **Các kết quả benchmark của dịch vụ quản lý Mem0 không thể coi là benchmark của bản mã nguồn mở.**
9. **Khoj là AGPL-3.0**, vì vậy phù hợp để học sản phẩm hơn là sao chép mã vào lõi.
10. Kiến trúc “dữ liệu chuẩn của mình, công cụ ngoài là bộ máy” vẫn đúng và càng được củng cố sau vòng kiểm chứng.
