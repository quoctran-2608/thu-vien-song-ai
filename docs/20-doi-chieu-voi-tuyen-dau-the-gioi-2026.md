# 20. Đối chiếu Thư Viện Sống với tuyến đầu thế giới năm 2026

**Ngày nghiên cứu: 05/10/2026**

Tài liệu này trả lời câu hỏi:

> **Kiến trúc Thư Viện Sống hiện đã tiếp cận những phương pháp tiên tiến và hiệu quả nhất trên thế giới hay chưa?**

Kết luận ngắn:

> **Về kỷ luật kiến trúc, truy nguồn, quản trị bằng chứng và khả năng thay công cụ: rất gần tuyến đầu.**
>
> **Về các kỹ thuật truy hồi và hiểu tài liệu đa phương thức đang tiến rất nhanh trong 2025–2026: chưa bao phủ đủ.**

Điều cần làm không phải đập bỏ kiến trúc hiện tại. Ngược lại, kiến trúc “dữ liệu chuẩn của mình, bộ máy có thể thay” chính là điều cho phép bổ sung các kỹ thuật tuyến đầu mà không phải xây lại hệ thống.

---

# 20.1. “Tuyến đầu” không có nghĩa dùng nhiều công nghệ nhất

Một hệ tiên tiến không phải hệ có nhiều lớp nhất.

EMNLP 2025 cho thấy một tuyến RAG rất đơn giản nhưng giữ nguyên cấu trúc và thứ tự của tài liệu, gọi là DOS-RAG, có thể ngang hoặc hơn những tuyến nhiều tầng như RAPTOR và ReadAgent trên nhiều bài kiểm tra khi so dưới cùng ngân sách lượng chữ đưa vào mô hình.

Vì vậy tiêu chuẩn của Thư Viện Sống phải là:

> **phương pháp nào thắng trên dữ liệu thật, dưới cùng ngân sách chất lượng–độ trễ–chi phí, thì dùng phương pháp đó.**

Nguồn:
- https://aclanthology.org/2025.emnlp-main.1656/

---

# 20.2. Đánh giá tổng thể

| Lớp | Mức hiện tại | Đánh giá |
|---|---:|---|
| Quyền sở hữu dữ liệu chuẩn | 9.5/10 | Rất mạnh |
| Truy nguồn / Claim–Evidence | 9/10 | Gần tuyến đầu |
| Tìm kết hợp chữ + nghĩa | 8/10 | Mạnh nhưng chưa đủ đối chứng tuyến đầu |
| Xếp hạng lại | 7.5/10 | Đúng hướng, mô hình thử còn thiên về tiết kiệm |
| Đọc cấu trúc PDF/EPUB | 8/10 | Mạnh |
| OCR/VLM tài liệu | 8/10 | PaddleOCR-VL-1.6 thuộc nhóm rất mạnh hiện nay |
| Tìm trực tiếp từ ảnh trang | 4/10 | Khoảng trống lớn |
| Tương tác muộn nhiều véc-tơ | 4.5/10 | Chưa là tuyến thử chính |
| Biểu diễn đoạn có ngữ cảnh | 5/10 | Có tiêu đề cấu trúc nhưng chưa benchmark chia muộn/ngữ cảnh hóa |
| Tìm thưa học bằng mạng nơ-ron | 5/10 | Chưa là đường thử chuẩn |
| Ngữ cảnh dài so với RAG | 6/10 | Thiếu baseline long-context/DOS-RAG chính thức |
| RAG thích ứng theo câu hỏi | 6.5/10 | Có bộ định tuyến, chưa đủ adaptive-k/gap-aware |
| Nghiên cứu nhiều bước | 7/10 | Không gian nghiên cứu tốt, vòng “thiếu gì → tìm tiếp” chưa đủ hình thức |
| Tổng hợp dài theo bằng chứng | 8/10 | Gói bằng chứng rất đúng hướng |
| Graph RAG | 8.5/10 | Quyết định tắt mặc định là hợp lý |
| Bộ não thứ hai con người đọc được | 9/10 | Rất mạnh về kiểm toán |
| Trí nhớ tác tử học từ kinh nghiệm | 5/10 | Chưa phải mục tiêu hiện tại |
| Đánh giá tiếng Việt | 5.5/10 | Chưa tận dụng VN-MTEB/ViRE |
| Đánh giá đa phương thức | 4.5/10 | Chưa có benchmark kiểu ViDoRe/T²-RAGBench |
| An toàn/truy quyền | 8.5/10 | Sau vòng rủi ro đã rất tốt về thiết kế |

**Đánh giá chuyên môn tổng quát: khoảng 7,5/10 về độ sẵn sàng tiếp cận tuyến đầu.**

Đây không phải thước đo khoa học; nó chỉ dùng để chỉ ra khoảng trống tương đối.

---

# 20.3. Khoảng trống lớn nhất: tìm trực tiếp từ ảnh trang

Kiến trúc hiện tại chủ yếu đi theo:

~~~text
trang
→ đọc/OCR
→ văn bản
→ đoạn
→ biểu diễn ý nghĩa
→ tìm
~~~

Đây vẫn là tuyến rất quan trọng.

Nhưng tuyến đầu 2025–2026 có thêm một nhánh:

~~~text
ảnh trang
→ bộ biểu diễn thị giác
→ nhiều véc-tơ của các vùng/từ/miếng ảnh
→ tương tác muộn với câu hỏi
→ tìm trang liên quan
~~~

ColPali là một trong những công trình mở đường: coi trang tài liệu như ảnh và tạo nhiều véc-tơ, nhờ vậy giữ được bố cục, bảng, biểu đồ, chữ và quan hệ thị giác.

ViDoRe V3 năm 2026 gồm khoảng 26.000 trang và 3.099 câu hỏi do con người xác minh, bằng 6 ngôn ngữ. Kết quả cho thấy bộ tìm thị giác nhìn chung vượt bộ tìm chỉ dựa văn bản, mô hình tương tác muộn và bước xếp hạng lại tiếp tục cải thiện kết quả; tuy vậy toàn ngành vẫn khó với phần tử phi văn bản, truy vấn mở và định vị thị giác tinh.

Nguồn:
- https://arxiv.org/abs/2601.08620
- https://aclanthology.org/2026.acl-long.204/
- https://huggingface.co/docs/transformers/model_doc/colpali

## Kết luận cho Thư Viện Sống

**Không thay OCR/text bằng tìm thị giác.**

Thêm một chỉ mục song song:

~~~text
                 ┌→ chỉ mục văn bản
TRANG CHUẨN ─────┤
                 └→ chỉ mục thị giác
~~~

Sau đó hợp nhất hai đường.

Đây là thay đổi tuyến đầu quan trọng nhất nên benchmark ngay.

---

# 20.4. Ứng viên thực tế để thử tìm thị giác

## ColModernVBERT

ModernVBERT là bộ mã hóa thị giác–ngôn ngữ khoảng 250M tham số. Biến thể ColModernVBERT dùng tương tác muộn nhiều véc-tơ cho truy hồi tài liệu.

Ưu điểm:
- nhỏ hơn nhiều VLM sinh văn bản;
- giấy phép MIT;
- tích hợp với Sentence Transformers;
- có thể thử cục bộ;
- phù hợp vai trò đối chứng nghiên cứu.

Giới hạn:
- dữ liệu huấn luyện và đánh giá vẫn thiên các ngôn ngữ giàu tài nguyên;
- không được mặc định suy ra chất lượng tiếng Việt.

Nguồn:
- https://huggingface.co/ModernVBERT/colmodernvbert
- https://arxiv.org/abs/2510.01149

## ColPali / ColQwen

Rất có giá trị làm đường chuẩn nghiên cứu cho tương tác muộn trực quan.

Nhưng phải chú ý giấy phép mô hình nền:
- nhiều bản ColPali kế thừa điều khoản Gemma;
- ColQwen2.5 có bản dựa trên Qwen Research License.

Không được thấy mã nguồn mở rồi suy ra “tự do dùng thương mại”.

## Jina Embeddings v4

Có văn bản + ảnh, ngữ cảnh dài, véc-tơ đơn, nhiều véc-tơ và chia muộn.

Nhưng Jina xác nhận v4 kế thừa Qwen Research License, không phù hợp làm mặc định cho sản phẩm thương mại nếu điều kiện giấy phép không cho phép.

Do đó:

> **đáng benchmark để biết trần chất lượng, chưa nên chọn làm nền sản xuất mặc định.**

---

# 20.5. Tương tác muộn nhiều véc-tơ là khoảng trống đáng thử

Biểu diễn truyền thống:

~~~text
1 đoạn → 1 véc-tơ
~~~

Tương tác muộn kiểu ColBERT:

~~~text
1 đoạn/trang → nhiều véc-tơ
câu hỏi → nhiều véc-tơ
↓
so khớp chi tiết từng phần
↓
gộp điểm
~~~

Ưu điểm:
- giữ chi tiết tốt hơn;
- ít nén cả đoạn vào một điểm;
- tốt cho câu hỏi cần chi tiết chính xác;
- kết hợp tự nhiên với tài liệu thị giác.

Nhược điểm:
- chỉ mục lớn hơn;
- truy vấn phức tạp hơn;
- cần bộ máy lưu/truy hồi hỗ trợ tốt;
- vận hành khó hơn véc-tơ đơn.

## Quyết định

Không thay đường Qdrant véc-tơ đơn ngay.

Thêm **một đường thử nhiều véc-tơ** vào benchmark 0.1.

---

# 20.6. Tìm thưa học bằng mạng nơ-ron: BM25 chưa phải trần chất lượng

BM25 vẫn rất mạnh vì đơn giản, rẻ, dễ giải thích và tốt với tên riêng/câu nguyên văn.

Nhưng tìm thưa học được, ví dụ SPLADE, có thể mở rộng từ/cụm từ theo ngữ nghĩa nhưng vẫn dùng chỉ mục thưa.

SPLADE-v3 được báo cáo vượt BM25 trên nhiều benchmark tiếng Anh/BEIR. Các hệ SemEval 2026 mạnh đã dùng kết hợp:

~~~text
BM25
+
SPLADE-v3
+
dense embedding
→ hợp nhất thứ hạng
~~~

Nguồn:
- https://arxiv.org/abs/2403.06789
- https://aclanthology.org/2026.semeval-1.389/
- https://aclanthology.org/2026.semeval-1.198/

## Nhưng với tiếng Việt

Không được suy ra SPLADE-v3 tiếng Anh sẽ thắng.

EACL 2026 đã có nghiên cứu riêng cho tiếng Việt, so sánh lexical, dense, neural sparse, late interaction và hybrid.

Kết quả tổng thể cho thấy **kết hợp BM25 + embedding vẫn là nhóm ổn định nhất xuyên nhiều miền**, và “mô hình lớn hơn” không tự động tốt hơn trong truy hồi tiếng Việt.

Nguồn:
- https://aclanthology.org/2026.findings-eacl.110/

## Quyết định

Benchmark:
1. BM25;
2. BGE-M3 sparse;
3. SPLADE hoặc mô hình sparse đa ngôn ngữ phù hợp;
4. dense;
5. BM25 + dense;
6. BM25 + learned sparse + dense.

Không thay BM25 chỉ vì SPLADE tiên tiến hơn.

---

# 20.7. Biểu diễn đoạn có ngữ cảnh: chia đoạn có cấu trúc vẫn chưa phải trần

Hiện ta làm đúng một việc quan trọng: mỗi đoạn biết sách/chương/mục của nó.

Tuyến đầu đi xa hơn.

## Contextual Retrieval

Anthropic thử thêm một đoạn ngữ cảnh ngắn riêng cho từng chunk trước khi tạo embedding và BM25. Trong thí nghiệm của họ, lỗi không tìm được tài liệu trong top-20 giảm 49% khi kết hợp contextual embeddings + contextual BM25, và 67% khi thêm xếp hạng lại.

Đây là số liệu trên tập thử của Anthropic, không phải bảo đảm phổ quát.

Nguồn:
- https://www.anthropic.com/engineering/contextual-retrieval

## Late Chunking — chia muộn

Cách thường:

~~~text
chia đoạn
→ biểu diễn từng đoạn độc lập
~~~

Chia muộn:

~~~text
đưa một vùng văn bản dài qua mô hình
→ token đã nhìn thấy ngữ cảnh rộng
→ sau đó mới gom thành biểu diễn cho từng đoạn
~~~

Nghiên cứu ConTEB/EMNLP 2025 cho thấy embedding hiện đại vẫn yếu khi đoạn cần ngữ cảnh toàn tài liệu; InSeNT kết hợp chia muộn cải thiện biểu diễn có ngữ cảnh.

Nguồn:
- https://arxiv.org/abs/2409.04701
- https://aclanthology.org/2025.emnlp-main.1150/

## Quyết định

Benchmark bốn phương án:
A. đoạn thường;  
B. đoạn + tiêu đề cấu trúc hiện tại;  
C. đoạn + ngữ cảnh sinh bởi mô hình;  
D. chia muộn.

Không mặc định D thắng.

---

# 20.8. Qwen3-Embedding-0.6B là mốc tiết kiệm, không phải trần chất lượng

Ta chọn 0.6B để bắt đầu là hợp lý về chi phí.

Nhưng Qwen3 có 0.6B, 4B và 8B cho cả embedding và reranker.

Qwen công bố:
- Qwen3-Embedding-8B: 32K, tối đa 4096 chiều;
- Qwen3-Reranker-8B: 32K;
- 100+ ngôn ngữ;
- Apache-2.0.

Trong số liệu do Qwen công bố, các bản reranker 4B/8B nhìn chung cao hơn 0.6B trên nhiều tập đa ngôn ngữ.

Nguồn:
- https://qwenlm.github.io/blog/qwen3-embedding/
- https://huggingface.co/Qwen/Qwen3-Embedding-8B
- https://huggingface.co/Qwen/Qwen3-Reranker-8B

## Quyết định

0.6B là **mốc chi phí thấp**.

Thêm:
- Qwen3-Embedding-4B hoặc 8B làm trần chất lượng;
- Qwen3-Reranker-4B/8B làm trần xếp hạng.

Sau đó đo chênh lệch chất lượng có xứng đáng chi phí hay không.

---

# 20.9. Xếp hạng cả danh sách cùng lúc

Reranker truyền thống thường chấm từng cặp câu hỏi–tài liệu.

Một hướng mới là listwise reranking: mô hình nhìn nhiều ứng viên cùng lúc và sắp cả danh sách.

Jina reranker v3.5 là ví dụ:
- 0.6B;
- đa ngôn ngữ;
- ngữ cảnh rất dài;
- mạnh với dữ liệu có cấu trúc.

Nhưng giấy phép CC-BY-NC 4.0 giới hạn sử dụng thương mại nếu không có giấy phép thương mại.

Nguồn:
- https://jina.ai/models/jina-reranker-v3.5
- https://huggingface.co/jinaai/jina-reranker-v3.5

## Quyết định

Có thể benchmark để biết trần kỹ thuật.

Không chọn làm mặc định sản xuất nếu giấy phép không phù hợp.

---

# 20.10. RAG và ngữ cảnh dài phải cạnh tranh trực tiếp

Một sai lầm phổ biến là cho rằng RAG luôn tốt hơn vì “thông minh hơn”.

Nghiên cứu cho thấy:
- khi đủ ngân sách, đưa lượng tài liệu dài trực tiếp vào mô hình có lúc vượt RAG;
- RAG vẫn lợi thế lớn về chi phí và quy mô;
- DOS-RAG rất đơn giản có thể thắng pipeline nhiều tầng;
- cách tốt nhất phụ thuộc câu hỏi, mô hình, độ dài và ngân sách.

Nguồn:
- https://aclanthology.org/2024.emnlp-industry.66.pdf
- https://aclanthology.org/2025.emnlp-main.1656/

## Kiến trúc nên sửa thành

~~~text
CÂU HỎI
↓
BỘ ĐỊNH TUYẾN
├── tìm chính xác
├── RAG kết hợp
├── đọc ngữ cảnh dài
├── PageIndex
└── nghiên cứu sâu nhiều vòng
~~~

RAG là một chiến lược, không phải con đường duy nhất.

---

# 20.11. Số đoạn đưa vào mô hình nên thay đổi theo câu hỏi

Lấy cố định top-5 hay top-20 là một giả định yếu.

EMNLP 2025 đề xuất Adaptive-k: số đoạn được chọn tùy câu hỏi và phân bố điểm tương đồng; trong thử nghiệm của họ, phương pháp này có thể dùng ít lượng chữ hơn đáng kể so với đưa toàn bộ ngữ cảnh mà vẫn duy trì hoặc cải thiện kết quả.

Nguồn:
- https://aclanthology.org/2025.emnlp-main.1017/

## Quyết định

Thay tư duy lấy cố định bằng:

~~~text
tìm ứng viên
↓
loại câu hỏi + phân bố điểm + độ khó
↓
chọn số đoạn động
~~~

Đây là nâng cấp tương đối rẻ và đáng thử sớm.

---

# 20.12. RAG có tác tử chỉ dành cho câu khó

ACL 2026 tổng kết Agentic RAG — RAG có tác tử chủ động lập kế hoạch, tìm nhiều vòng và điều chỉnh truy vấn — là hướng nghiên cứu lớn.

Nhưng thực nghiệm cũng cảnh báo pipeline phức tạp không tự động thắng pipeline đơn giản.

Nguồn:
- https://aclanthology.org/2026.findings-acl.78/
- https://aclanthology.org/2026.acl-long.374/
- https://aclanthology.org/2026.acl-industry.5/

## Kết luận

Bộ định tuyến hiện tại của Thư Viện Sống là đúng.

Không chạy tác tử cho:
- tìm câu nguyên văn;
- mở trang;
- định nghĩa đơn giản.

Chỉ kích hoạt với:
- câu hỏi nhiều bước;
- nhiều nguồn;
- cần phản chứng;
- tổng hợp lớn;
- chưa đủ bằng chứng sau lượt đầu.

---

# 20.13. Gap-aware retrieval: biết mình còn thiếu gì

S2G-RAG tại ACL 2026 rất phù hợp với Thư Viện Sống.

Quy trình:

~~~text
tìm bằng chứng
↓
đủ chưa?
├── đủ → trả lời
└── chưa
    ↓
    tạo danh sách khoảng trống cụ thể
    ↓
    biến khoảng trống thành truy vấn mới
    ↓
    tìm tiếp
~~~

Nó đồng thời giữ một bộ bằng chứng cấp câu nhỏ để tránh tích lũy nhiễu.

Nguồn:
- https://aclanthology.org/2026.acl-long.1185/

## Nâng cấp Research Workspace

Nên thêm:
- evidence_sufficiency — mức đủ bằng chứng;
- missing_gaps — những điều còn thiếu;
- next_queries — truy vấn tiếp;
- stop_reason — lý do dừng.

---

# 20.14. Retriever cho tác tử đang trở thành một lĩnh vực riêng

Agentic-R 2026 chỉ ra đoạn giống câu hỏi chưa chắc là đoạn hữu ích nhất cho kết quả cuối của một quá trình tìm nhiều bước.

Họ huấn luyện retriever dựa không chỉ trên độ liên quan cục bộ mà cả độ đúng của câu trả lời cuối.

Nguồn:
- https://aclanthology.org/2026.findings-acl.785/

## Quyết định

Chưa cần huấn luyện kiểu này ở v0.1.

Nhưng nhật ký nghiên cứu nên lưu:
- truy vấn từng lượt;
- ứng viên;
- bằng chứng được dùng;
- kết quả cuối.

Đó là dữ liệu cần nếu sau này muốn học retriever từ hành vi thật.

---

# 20.15. Tổng hợp dài: Gói bằng chứng của ta đúng, nhưng còn một cấp nữa

EviReport ACL 2026 rất gần tư tưởng Thư Viện Sống:
- bằng chứng nhỏ, truy được nguồn;
- dàn ý có lý do;
- gom sự kiện kiểm chứng được trước;
- chỉ viết từ tập sự kiện đó;
- phát hiện phần còn thiếu;
- truy vấn bổ sung.

Nguồn:
- https://aclanthology.org/2026.findings-acl.1397/

## Research Workspace nên nâng thành

~~~text
câu hỏi
↓
chia thành khía cạnh / câu hỏi con
↓
mỗi câu hỏi con có ô bằng chứng riêng
↓
đánh giá độ phủ
↓
tìm thêm chỗ trống
↓
SỔ SỰ KIỆN / KHẲNG ĐỊNH
↓
dàn ý
↓
viết
↓
kiểm trích dẫn
~~~

Điểm cần thêm là **độ phủ**, không chỉ “có trích dẫn hay không”.

---

# 20.16. Đồ thị: quyết định tắt mặc định vẫn là tiên tiến

Có nhiều nghiên cứu mới về graph retrieval, multi-hop graph, temporal graph và multi-graph memory.

Nhưng chúng không chứng minh graph phải là mặc định cho mọi thư viện.

Đồ thị có giá trị nhất khi câu hỏi cần:
- chuỗi quan hệ;
- liên kết thực thể;
- nhiều bước;
- thời gian;
- sự kiện.

Do đó quyết định hiện tại **graph tắt mặc định** là thận trọng và đúng.

Tiên tiến không đồng nghĩa “graph mọi thứ”.

---

# 20.17. Trí nhớ: Bộ não thứ hai của ta mạnh nhưng thuộc một loại trí nhớ cụ thể

Năm 2026, trí nhớ tác tử đang tách thành nhiều loại.

Ví dụ:
- AgeMem: tác tử học khi nào lưu, lấy, cập nhật, tóm tắt, xóa;
- Memory-R1: học ADD/UPDATE/DELETE/NOOP;
- ReMe: lưu kinh nghiệm thành công/thất bại, tái dùng và cắt bỏ kinh nghiệm cũ;
- Cognitive Scaffold: tách ngữ cảnh làm việc khỏi trí nhớ cấu trúc dài hạn.

Nguồn:
- https://aclanthology.org/2026.acl-long.981/
- https://aclanthology.org/2026.acl-long.583/
- https://aclanthology.org/2026.findings-acl.829/
- https://aclanthology.org/2026.acl-long.1170/

## Thư Viện Sống nên phân bốn bộ nhớ

1. **Kho nguồn** — bằng chứng gốc.
2. **Bộ não tri thức** — Markdown + Claim/Evidence + lịch sử.
3. **Trí nhớ làm việc** — Research Workspace của một nhiệm vụ.
4. **Trí nhớ thủ tục** — tùy chọn tương lai, học chiến lược/trải nghiệm vận hành.

Không trộn trí nhớ thủ tục vào Bộ não tri thức.

---

# 20.18. OCR/document parsing: ta đang khá gần tuyến đầu

PaddleOCR-VL-1.6 hiện là lựa chọn rất mạnh. Paddle công bố 96.33% trên OmniDocBench v1.6, khoảng 0.9B tham số, mạnh ở text, formula, table và các tình huống scan/skew/warp.

Nguồn:
- https://github.com/PaddlePaddle/PaddleOCR/blob/main/docs/version3.x/algorithm/PaddleOCR-VL/PaddleOCR-VL-1.6.en.md

Nhưng không nên dừng ở một engine.

ICML 2026 MORE đánh giá 149 ngôn ngữ và cho thấy HunyuanOCR, PaddleOCR-VL, dots.ocr/dots.mocr có thế mạnh khác nhau; **table parsing vẫn là nút thắt lớn**.

Nguồn:
- https://proceedings.mlr.press/v306/xu26bs.html

## Quyết định

Trong pilot khó, nên thử ít nhất:
- Docling/PaddleOCR-VL-1.6;
- dots.mocr;
- một baseline khác nếu giấy phép và hạ tầng phù hợp.

Không cần dùng ba engine trong sản xuất. Mục tiêu là biết engine nào thắng từng lớp tài liệu.

---

# 20.19. Tiếng Việt: hiện ta chưa khai thác các benchmark mới nhất

## VN-MTEB

EACL 2026:
- 41 tập dữ liệu;
- 6 loại tác vụ;
- dành riêng cho embedding tiếng Việt.

Nguồn:
- https://aclanthology.org/2026.findings-eacl.86/

## ViRE

Nghiên cứu retrieval tiếng Việt trên giáo dục, pháp lý, y tế, chăm sóc khách hàng, đánh giá đời sống và tri thức mở.

Nó so:
- lexical;
- dense;
- neural sparse;
- late interaction;
- hybrid.

Một kết luận đáng chú ý:

> **kết hợp lexical + semantic là lựa chọn ổn định xuyên miền; kích thước model không dự đoán tốt chất lượng retrieval.**

Nguồn:
- https://aclanthology.org/2026.findings-eacl.110/

## Thay đổi cần thiết

Mọi lựa chọn embedding/reranker của Thư Viện Sống phải qua:
1. VN-MTEB hoặc phần phù hợp;
2. ViRE;
3. bộ câu hỏi sách tiếng Việt riêng của dự án.

Không chốt theo bảng tiếng Anh hay đa ngôn ngữ chung.

---

# 20.20. Đánh giá đa phương thức của ta còn thiếu

Tập 100–300 câu hiện tại là khởi đầu tốt nhưng chưa đủ để gọi là tuyến đầu.

Nên bổ sung lớp bài kiểm tra lấy cảm hứng từ:

## ViDoRe V3
- tìm trang giàu hình;
- bảng;
- biểu đồ;
- nhiều ngôn ngữ;
- định vị tới vùng trang.

## T²-RAGBench
- câu hỏi kết hợp text + table;
- phải tìm đúng bảng trước khi reasoning.

Nguồn:
- https://aclanthology.org/2026.eacl-long.8/

## MORE / olmOCR-Bench
- scan cũ;
- bảng;
- nhiều cột;
- chữ nhỏ;
- công thức;
- thứ tự đọc;
- đa ngôn ngữ.

## Agentic/multi-hop
- vòng tìm nhiều bước;
- chẩn đoán từng lượt truy hồi.

## Memory
- không chỉ nhớ fact;
- còn phải kiểm tra cập nhật, quên dữ liệu cũ và dùng trí nhớ đúng lúc.

---

# 20.21. Ma trận benchmark mới cho bản 0.1

Không đưa tất cả vào sản xuất.

Chạy các **làn thử nghiệm song song**.

## Làn A — mốc đơn giản mạnh

~~~text
chia đoạn theo cấu trúc
+ BM25
+ Qwen3-Embedding-0.6B
+ RRF
+ Qwen3-Reranker-0.6B
~~~

## Làn B — mô hình lớn hơn
- Qwen3-Embedding-4B/8B;
- Qwen3-Reranker-4B/8B.

Mục tiêu: biết trần chất lượng tăng bao nhiêu khi trả thêm tài nguyên.

## Làn C — tìm thưa học được
- BM25;
- BGE-M3 sparse;
- SPLADE/phương án sparse phù hợp tiếng Việt;
- hợp nhất ba đường nếu có lợi.

## Làn D — biểu diễn có ngữ cảnh
- tiêu đề cấu trúc;
- contextual prefix;
- late chunking.

## Làn E — tương tác muộn văn bản
- ColBERT/BGE-M3 multi-vector hoặc tương đương.

## Làn F — tìm thị giác
- ColModernVBERT;
- một visual retriever mạnh khác nếu giấy phép phù hợp;
- hợp nhất với tuyến text.

## Làn G — ngữ cảnh dài
Sau khi chọn 1–3 sách/chương:
- đọc ngữ cảnh dài trực tiếp;
- DOS-RAG;
- PageIndex;
- RAG đoạn bình thường.

Tất cả dùng ngân sách token tương đương.

## Làn H — nghiên cứu sâu

~~~text
phân rã câu hỏi
→ tìm
→ kiểm đủ bằng chứng
→ khoảng trống
→ tìm lại
→ sổ sự kiện/khẳng định
→ tổng hợp
~~~

---

# 20.22. Ưu tiên

## P0 — benchmark ngay

1. visual retrieval trên trang giàu bố cục;
2. VN-MTEB/ViRE + benchmark sách tiếng Việt riêng;
3. Qwen3 0.6B vs 4B/8B;
4. BM25+dense vs learned-sparse+dense;
5. tiêu đề cấu trúc vs contextual/late chunking;
6. DOS-RAG/long-context vs RAG/PageIndex.

## P1 — sau baseline

7. adaptive-k;
8. gap-aware iterative retrieval;
9. evidence coverage / facts-first synthesis.

## P2 — khi có nhu cầu chứng minh được

10. graph retrieval;
11. retriever học từ trajectory;
12. procedural memory;
13. RL-based memory management.

---

# 20.23. Những thứ rất mới nhưng chưa nên đưa vào lõi

## Học tăng cường cho memory
AgeMem/Memory-R1 thú vị nhưng cần dữ liệu hành vi và reward. Ta chưa có.

## Retriever học từ agent trajectories
Agentic-R hấp dẫn nhưng v0.1 chưa có trajectory thật.

## Multi-graph memory
Kết quả benchmark tốt không chứng minh cần cho thư viện sách bất biến.

## Model đứng đầu leaderboard tuần này
Leaderboard đổi nhanh, giấy phép và tài nguyên có thể không phù hợp.

Kiến trúc nên benchmark **phương pháp đại diện**, không chạy theo tên model mới nhất.

---

# 20.24. Kiến trúc nâng cấp đề xuất

Không thay kho dữ liệu chuẩn.

Thêm các lớp có thể bật/tắt:

~~~text
                     ┌────────────────────────────┐
                     │       KHO NGUỒN CHUẨN       │
                     └──────────────┬─────────────┘
                                    │
                ┌───────────────────┼──────────────────┐
                │                   │                  │
        CHỈ MỤC VĂN BẢN      CHỈ MỤC THỊ GIÁC     CHỈ MỤC CẤU TRÚC
       chữ + sparse + dense    ảnh trang +          cây/chương/mục
       + nhiều véc-tơ         tương tác muộn
                │                   │                  │
                └──────────────┬────┴──────────────────┘
                               ↓
                       BỘ ĐỊNH TUYẾN
          ┌────────────────────┼───────────────────────┐
          │                    │                       │
       tìm đơn giản       đọc ngữ cảnh dài       nghiên cứu sâu
          │                    │                       │
          │                    │              đủ/chưa đủ bằng chứng
          └────────────────────┴───────────────┬───────┘
                                               ↓
                                      SỔ BẰNG CHỨNG / SỰ KIỆN
                                               ↓
                                        TỔNG HỢP KIỂM CHỨNG
                                               ↓
                                         ĐỀ XUẤT CHO BRAIN
~~~

Điểm quan trọng:

> **chỉ mục thị giác không thay chỉ mục chữ; ngữ cảnh dài không thay RAG; tác tử không thay bộ định tuyến; graph không thay corpus.**

Tất cả là chiến lược cạnh tranh phía trên cùng dữ liệu chuẩn.

---

# 20.25. Nguồn lực bổ sung để benchmark tuyến đầu

## Tìm thị giác
- 3–5 ngày kỹ sư ML;
- GPU 16–24 GB tùy model;
- 50–100 câu hỏi dựa vào bảng/hình/bố cục.

## Biểu diễn có ngữ cảnh
- 3–5 ngày cho late chunking/contextual prefix.

## Sparse/multi-vector
- 3–7 ngày;
- phải đo dung lượng chỉ mục.

## Long-context / DOS-RAG
- 2–4 ngày;
- chi phí chủ yếu là inference benchmark.

## Deep-research loop
- 5–10 ngày sau khi retrieval baseline ổn.

Tổng:

> **thêm khoảng 2–4 tuần kỹ thuật cho một vòng benchmark tuyến đầu có ý nghĩa**, nếu làm sau khi nền 0.1 đã chạy được.

Không kéo tất cả vào đường sản xuất.

---

# 20.26. Phán quyết cuối

## Ta có đang lạc hậu không?

**Không.**

Các nguyên tắc:
- kho dữ liệu chuẩn;
- truy nguồn;
- gói bằng chứng;
- tìm kết hợp;
- xếp hạng lại;
- chia đoạn theo cấu trúc;
- đọc theo độ sâu thích ứng;
- không gian nghiên cứu;
- sổ khẳng định;
- bộ máy thay được;
- đánh giá trước;
- Brain con người đọc được;

đều phù hợp rất tốt với hướng phát triển hiện đại.

## Ta đã có đầy đủ phương pháp tốt nhất năm 2026 chưa?

**Chưa.**

Khoảng trống quan trọng nhất:

1. tìm tài liệu trực tiếp bằng thị giác;
2. tương tác muộn/nhiều véc-tơ;
3. tìm thưa học được;
4. biểu diễn đoạn có ngữ cảnh/chia muộn;
5. baseline ngữ cảnh dài/DOS-RAG;
6. chọn số bằng chứng thích ứng;
7. tìm lặp theo khoảng trống bằng chứng;
8. tổng hợp dài đo cả độ phủ bằng chứng;
9. đánh giá retrieval tiếng Việt hiện đại;
10. đánh giá đa phương thức và memory phong phú hơn.

## Có phải đưa hết vào hệ thống?

**Không.**

Đó sẽ tái tạo đúng rủi ro lớn nhất đã nhận ra: quá phức tạp.

Cách tuyến đầu phù hợp với Thư Viện Sống là:

> **biến các kỹ thuật tiên tiến thành các làn thử nghiệm, bắt chúng cạnh tranh trên cùng dữ liệu, cùng ngân sách, cùng bộ câu hỏi; chỉ phương pháp thắng mới được thăng lên đường chính.**

---

# 20.27. Khuyến nghị thay đổi ngay

## Giữ nguyên
- kho dữ liệu chuẩn;
- nguồn bất biến có ngoại lệ xóa có kiểm toán;
- Qdrant làm baseline tìm kết hợp;
- QMD cho Brain;
- PageIndex sau thu hẹp;
- graph tắt mặc định;
- một bộ ghi logic;
- mô hình Claim/Evidence.

## Thêm vào benchmark v0.1
- ColModernVBERT hoặc visual retriever tương đương;
- VN-MTEB + ViRE;
- Qwen3 4B/8B như trần chất lượng;
- BGE-M3 sparse/multi-vector;
- learned sparse lane;
- late chunking/contextual retrieval;
- DOS-RAG/long-context;
- adaptive-k.

## Thêm vào chế độ nghiên cứu v0.2
- sufficiency + missing-gap loop;
- facts-first synthesis;
- evidence coverage;
- procedural memory thử nghiệm.

## Chưa đưa vào lõi
- graph toàn thư viện;
- học tăng cường cho memory;
- huấn luyện Agentic-R;
- PageIndex Cloud File System;
- Jina v4/v3.5 cho sản xuất nếu giấy phép chưa phù hợp.

---

# 20.28. Nguồn nghiên cứu chính

## Đa phương thức và tìm thị giác
- ViDoRe V3: https://arxiv.org/abs/2601.08620
- Multimodal RAG Survey, ACL 2026: https://aclanthology.org/2026.acl-long.204/
- Unified Multimodal Interleaved Document Representation: https://aclanthology.org/2026.findings-eacl.83/
- ModernVBERT: https://arxiv.org/abs/2510.01149
- ColModernVBERT: https://huggingface.co/ModernVBERT/colmodernvbert
- ColPali: https://huggingface.co/docs/transformers/model_doc/colpali
- Jina Embeddings v4: https://jina.ai/models/jina-embeddings-v4/

## Truy hồi văn bản
- SPLADE-v3: https://arxiv.org/abs/2403.06789
- BGE-M3: https://huggingface.co/BAAI/bge-m3
- Qwen3 Embedding/Reranker: https://qwenlm.github.io/blog/qwen3-embedding/
- Vietnamese Retrieval Study: https://aclanthology.org/2026.findings-eacl.110/
- VN-MTEB: https://aclanthology.org/2026.findings-eacl.86/

## Biểu diễn có ngữ cảnh
- Contextual Retrieval: https://www.anthropic.com/engineering/contextual-retrieval
- Late Chunking: https://arxiv.org/abs/2409.04701
- ConTEB / InSeNT: https://aclanthology.org/2025.emnlp-main.1150/

## Ngữ cảnh dài / thích ứng
- DOS-RAG: https://aclanthology.org/2025.emnlp-main.1656/
- Adaptive-k: https://aclanthology.org/2025.emnlp-main.1017/
- RAG vs Long Context: https://aclanthology.org/2024.emnlp-industry.66.pdf

## Nghiên cứu sâu có tác tử
- Agentic RAG Survey: https://aclanthology.org/2026.findings-acl.78/
- Search Agents Survey: https://aclanthology.org/2026.acl-long.374/
- S2G-RAG: https://aclanthology.org/2026.acl-long.1185/
- Agentic-R: https://aclanthology.org/2026.findings-acl.785/
- EviReport: https://aclanthology.org/2026.findings-acl.1397/

## Trí nhớ
- AgeMem: https://aclanthology.org/2026.acl-long.981/
- Memory-R1: https://aclanthology.org/2026.acl-long.583/
- ReMe: https://aclanthology.org/2026.findings-acl.829/
- Cognitive Scaffold: https://aclanthology.org/2026.acl-long.1170/

## OCR và đọc tài liệu
- PaddleOCR-VL-1.6: https://github.com/PaddlePaddle/PaddleOCR/blob/main/docs/version3.x/algorithm/PaddleOCR-VL/PaddleOCR-VL-1.6.en.md
- MORE, ICML 2026: https://proceedings.mlr.press/v306/xu26bs.html
- T²-RAGBench: https://aclanthology.org/2026.eacl-long.8/
