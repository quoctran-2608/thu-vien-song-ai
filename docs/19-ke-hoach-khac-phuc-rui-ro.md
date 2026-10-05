# 19. Kế hoạch khắc phục rủi ro: giải pháp, xác suất thành công và nguồn lực

**Ngày nghiên cứu: 05/10/2026**

Tài liệu này nối tiếp [18. Phản biện: rủi ro, giới hạn và điều kiện thất bại](18-rui-ro-gioi-han-va-phan-bien.md).

Mục tiêu là trả lời cho từng rủi ro:

1. Có thể khắc phục bằng cách nào?
2. Khả năng đưa rủi ro xuống mức chấp nhận được là bao nhiêu?
3. Cần người, thời gian, hạ tầng và chuyên môn gì?
4. Điều kiện nào chứng minh giải pháp đã thật sự hiệu quả?

---

# 19.1. Cách hiểu các tỷ lệ phần trăm

Các tỷ lệ dưới đây **không phải số liệu thống kê khách quan** và không có nghĩa “xóa được X% rủi ro”.

Đây là **ước lượng kỹ thuật của nhóm thiết kế**, dựa trên:

- mức trưởng thành của biện pháp kiểm soát;
- khả năng kiểm thử khách quan;
- mức phụ thuộc vào AI, dữ liệu hoặc bên thứ ba;
- các nghiên cứu và tài liệu kỹ thuật hiện hành;
- phạm vi dự án hiện tại.

“Khả năng khắc phục thành công” nghĩa là:

> **xác suất rằng, nếu bố trí đúng nguồn lực như đề xuất, dự án có thể đưa rủi ro xuống mức chấp nhận được cho bản kỹ thuật 0.1 và các bước tiếp theo.**

Sai số của các con số nên được hiểu khoảng **±10 điểm phần trăm**; với pháp lý, hành vi người dùng và “sự thật nguồn”, độ bất định còn lớn hơn.

Không rủi ro nào được coi là 100% biến mất.

---

# 19.2. Đơn vị nguồn lực

Các ký hiệu:

- **KT**: kiến trúc sư / kỹ sư backend.
- **ML**: kỹ sư dữ liệu, học máy, OCR, tìm kiếm.
- **QA**: kiểm thử, gắn nhãn dữ liệu, tạo bộ câu hỏi chuẩn.
- **AT**: an toàn thông tin / DevSecOps.
- **PL**: pháp lý / bảo vệ dữ liệu cá nhân.
- **SP**: sản phẩm / nghiên cứu người dùng.
- **NV**: người có chuyên môn nội dung, học thuật hoặc thủ thư.

Nguồn lực được tính theo **ngày công**, không phải số ngày lịch. Nhiều rủi ro dùng chung một biện pháp, vì vậy **không được cộng cơ học toàn bộ ngày công trong bảng**.

---

# 19.3. Bảng tổng hợp 42 rủi ro

| Mã | Rủi ro | Giải pháp chính | Khả năng khắc phục | Nguồn lực chính |
|---|---|---|---:|---|
| R01 | Xây quá nhiều lớp trước khi chứng minh giá trị | Khóa phạm vi 0.1, cổng quyết định, chỉ xây sau khi có số đo | 85% | KT 3–5 ngày, SP 3–5 ngày |
| R02 | Không thể bảo đảm “sự thật” chỉ bằng truy nguồn | Đánh giá loại/độ tin cậy/độc lập của nguồn, người chuyên môn duyệt | 60% | NV 10–20 ngày, KT 3–5 ngày |
| R03 | Cửa bằng chứng tạo cảm giác chắc chắn giả | Tách tạo–kiểm–phê duyệt, đo độ phủ trích dẫn, mô hình/luật kiểm độc lập | 78% | ML 7–10 ngày, QA 5–10 ngày |
| R04 | Truy hồi bỏ sót nguồn đúng | Hybrid search, mở rộng truy vấn, Recall@K riêng, tập khó kín | 85% | ML 10–15 ngày, QA 10 ngày |
| R05 | “Không tìm thấy” nhưng không biết đã tìm ở đâu | Ghi SearchScope và phiên bản chỉ mục vào mỗi ResearchRun | 95% | KT 3–5 ngày |
| R06 | Trang có lớp chữ nhưng lớp chữ sai | Bộ tiền kiểm tra nhiều tín hiệu + lấy mẫu đối chiếu ảnh | 90% | ML 5–8 ngày, QA 3–5 ngày |
| R07 | Docling sai bố cục/thứ tự đọc | Tập hồi quy bố cục + tuyến dự phòng + cấu hình theo loại tài liệu | 85% | ML 7–12 ngày, QA 5–8 ngày |
| R08 | OCR tiếng Việt sai dấu | Benchmark tiếng Việt riêng + PP-OCRv5/v6/VL đối chứng + kiểm ảnh trang | 82% | ML 10–15 ngày, QA/NV 8–12 ngày, GPU |
| R09 | Bảng/hình/công thức bị biến thành text nghèo nàn | Mô hình khối đa phương thức, giữ ảnh/bảng cấu trúc, tuyến VLM cho trang khó | 75% | ML 15–25 ngày, QA 8–15 ngày, GPU |
| R10 | EPUB không có trang ổn định | SourceLocator nhiều loại, dùng page-list/pagebreak khi thật sự tồn tại | 95% | KT 4–7 ngày |
| R11 | Chống trùng làm mất khác biệt ấn bản | SHA tự động cho trùng tuyệt đối; gần trùng chỉ gợi ý quan hệ | 90% | ML/KT 5–8 ngày, QA 3–5 ngày |
| R12 | Bộ não thứ hai tạo nợ tri thức | freshness, source generation, lịch xem lại, trạng thái tranh luận | 75% | KT 5–8 ngày, NV 5–10 ngày + vận hành |
| R13 | Tự bảo trì tạo vòng lặp nhiễu | ngân sách thay đổi, chống lặp, gom đề xuất, chế độ chỉ báo cáo | 90% | KT 5–8 ngày |
| R14 | Một bộ ghi trở thành nút nghẽn | một vai trò logic, hàng đợi, khóa theo phạm vi, idempotency | 92% | KT 5–10 ngày |
| R15 | Không thể giao dịch nguyên tử qua nhiều kho | PostgreSQL là nguồn chuẩn + transactional outbox + chỉ mục cập nhật bất đồng bộ | 90% | KT 10–15 ngày, AT/Ops 3–5 ngày |
| R16 | Các chỉ mục nhìn thấy các thế hệ dữ liệu khác nhau | generation_id và trạng thái build cho mọi chỉ mục | 95% | KT 4–7 ngày |
| R17 | Qdrant: nhất quán, lượng tử hóa, bảo mật | cấu hình consistency, benchmark quantization, TLS/API key/private network | 90% | ML 5–8 ngày, AT/Ops 5–8 ngày |
| R18 | Rò dữ liệu do phân quyền sau truy hồi | lọc quyền trước/trong truy hồi, collection/tenant partition, kiểm thử rò rỉ | 93% | KT 7–12 ngày, AT 5–8 ngày |
| R19 | Chèn lệnh gián tiếp qua PDF/EPUB | nguồn = dữ liệu không tin cậy, quyền tối thiểu, tác tử đọc chỉ đọc, red-team | 70% | AT 8–12 ngày, KT 7–10 ngày |
| R20 | Nguồn độc hại hoặc nguồn sai | source policy, nguồn gốc, chữ ký/hash, trust status, quarantine | 75% | KT 5–8 ngày, NV 5–10 ngày |
| R21 | Tác tử có quá nhiều quyền | công cụ hẹp, quyền theo vai trò, phê duyệt hành động nhạy cảm | 92% | AT 5–8 ngày, KT 5–8 ngày |
| R22 | Chuỗi cung ứng phần mềm/mô hình | khóa phiên bản, hash, SBOM/AI-BOM, quét CVE, nguồn tải được duyệt | 85% | AT/Ops 5–10 ngày + duy trì |
| R23 | RAGFlow rc thay đổi lớn | không làm lõi, khóa phiên bản, adapter contract test, chỉ nâng sau backup | 95% | KT 3–5 ngày, QA 2–4 ngày |
| R24 | Hiểu sai tính năng PageIndex local/cloud | kiểm chứng nguồn chính thức, capability matrix có ngày, contract test | 98% | KT 2–3 ngày |
| R25 | PageIndex local chỉ phù hợp PDF có chữ | chỉ dùng sau OCR/chuẩn hóa, không dùng làm tuyến ingest | 95% | KT/ML 2–5 ngày |
| R26 | QMD bị dùng quá phạm vi | chỉ dùng Brain Markdown, một writer, health check, rebuild dễ dàng | 90% | KT 3–5 ngày |
| R27 | Tối ưu quá mức theo bộ câu hỏi chuẩn | chia dev/hidden/adversarial/time-split | 90% | QA 5–8 ngày |
| R28 | Bộ thử thiếu câu không có đáp án | thêm unanswerable/conflict/weak-evidence/fake-quote | 92% | QA/NV 3–6 ngày |
| R29 | Điểm tự tin AI bị hiểu là xác suất đúng | không dùng % nếu chưa hiệu chỉnh; calibration riêng theo claim | 65% | ML 8–15 ngày, QA 5–8 ngày |
| R30 | Nguồn bất biến xung đột quyền xóa | immutable-by-default + audited deletion/tombstone/purge workflow | 90% | KT 7–10 ngày, PL 3–5 ngày |
| R31 | Bản quyền số hóa và chia sẻ | rights registry, phạm vi truy cập, quy tắc không-cloud, rà pháp lý theo bộ sưu tập | 70% | PL 5–15 ngày, NV 3–5 ngày |
| R32 | Dữ liệu cá nhân/nhạy cảm | data classification, DPIA, retention, ACL, deletion, cross-border register | 85% | PL 8–15 ngày, AT 8–12 ngày, KT 8–12 ngày |
| R33 | Cloud fallback làm dữ liệu rời hệ thống | policy engine LOCAL/CLOUD, allowlist theo độ nhạy cảm, log egress | 95% | KT 5–8 ngày, AT 3–5 ngày |
| R34 | Dữ liệu phát sinh phình rất lớn | đo hệ số phình ở 0.1, tiered storage, không giữ ảnh trung gian vô hạn | 92% | Ops 3–5 ngày, ML 2–3 ngày |
| R35 | Chi phí lập lại chỉ mục lớn | version gate, canary reindex, dual index, capacity model | 85% | ML/Ops 7–12 ngày |
| R36 | Có backup nhưng khôi phục không được | restore drill định kỳ, checksum, RTO/RPO, snapshot compatibility test | 95% | Ops 5–8 ngày + định kỳ |
| R37 | Thuế adapter tăng vô hạn | ngân sách adapter, chuẩn giao diện nội bộ, giới hạn số engine đang hoạt động | 80% | KT 5–10 ngày |
| R38 | Mô hình dữ liệu quá cứng cho nguồn ngoài sách | Locator/StructuralNode tổng quát, lớp Work/Edition là chuyên biệt sách | 85% | KT 7–12 ngày |
| R39 | Bộ não thứ hai cần quản trị biên tập | quy tắc đặt tên/gộp/tách, owner, review queue, linter | 75% | NV 8–15 ngày, KT 3–5 ngày + vận hành |
| R40 | Giao diện quá nặng | hai chế độ thường/kiểm chứng, progressive disclosure, test người dùng | 85% | SP/UX 5–10 ngày, KT 3–5 ngày |
| R41 | Người dùng chỉ cần tìm sách, không cần “hệ điều hành tri thức” | pilot người dùng, đo retention/use frequency, feature gates | 65% | SP 10–15 ngày, 10–20 người dùng thật |
| R42 | Hứa quá mức | công bố giới hạn sản phẩm, SLO theo loại nhiệm vụ, không quảng bá “không sai” | 95% | SP/KT 2–4 ngày |

---

# 19.4. R01 — Quá phức tạp trước khi chứng minh giá trị

## Giải pháp

Thiết lập **cổng quyết định kiến trúc**.

Bản 0.1 chỉ được phép xây:

- nguồn bất biến;
- mô hình dữ liệu tối thiểu;
- ingest;
- OCR khi cần;
- hybrid retrieval;
- reranker;
- citation;
- evaluation.

Các lớp sau bị khóa:

- graph;
- multi-agent;
- tự bảo trì Brain;
- RAGFlow sâu;
- Cognee/Mem0/Graphiti;
- PageIndex toàn kho.

Mỗi tính năng mới phải trả lời:

1. bài toán người dùng nào?
2. baseline hiện tại thất bại ra sao?
3. số đo nào chứng minh tính năng mới tốt hơn?
4. chi phí vận hành thêm bao nhiêu?

## Khả năng thành công: 85%

Phần khó không phải kỹ thuật mà là kỷ luật phạm vi.

## Nguồn lực

- KT: 3–5 ngày để chốt architecture gates.
- SP: 3–5 ngày để định nghĩa 5–10 use case thật.
- Sau đó 1 giờ/tuần review scope.

## Tiêu chí đạt

Không có engine mới nào được đưa vào main path nếu chưa có benchmark và use case.

---

# 19.5. R02 — Truy nguồn không thể bảo đảm sự thật

Nghiên cứu RA-RAG cho thấy RAG thông thường bỏ qua sự khác biệt về độ đáng tin giữa nguồn; việc ước lượng độ tin cậy nguồn có thể cải thiện kết quả khi corpus chứa nguồn chất lượng không đồng đều.

## Giải pháp

Bổ sung SourceAssessment, nhưng **không biến thành một điểm “truth score” duy nhất**.

Các trường:

- source_type;
- authority_scope;
- publication_status;
- peer_reviewed;
- primary_or_secondary;
- independence_group;
- known_retraction_or_dispute;
- conflict_of_interest;
- reviewed_by;
- reviewed_at.

Khi tổng hợp:

- relevance quyết định nguồn có liên quan;
- source assessment quyết định cách diễn giải sức nặng;
- contradiction không bị xóa chỉ vì một nguồn có điểm cao hơn.

## Khả năng thành công: 60%

Có thể giảm việc “nguồn yếu được đối xử như nguồn mạnh”, nhưng **không thể tự động hóa sự thật**.

## Nguồn lực

- NV: 10–20 ngày xây taxonomy nguồn và gắn nhãn tập pilot.
- KT: 3–5 ngày bổ sung schema.
- Nếu lĩnh vực học thuật chuyên sâu: cần reviewer theo miền.

---

# 19.6. R03 — Cửa bằng chứng tự xác nhận chính mình

Nghiên cứu TACL 2026 tách riêng **citation failure** và **response failure**, đồng thời cho thấy lỗi trích dẫn tăng khi quan hệ câu trả lời–bằng chứng phức tạp hơn.

## Giải pháp

Tách ba vai trò:

- Generator: tạo claim.
- Evidence checker: đánh giá claim–evidence.
- Publisher: chỉ xuất claim qua ngưỡng.

Không để một lời gọi mô hình duy nhất làm cả ba.

Với claim quan trọng:

- kiểm tra entailment bằng mô hình khác hoặc phương pháp khác;
- đo citation precision và citation completeness riêng;
- hiển thị đoạn chứng cứ cho người dùng;
- yêu cầu nhiều evidence khi claim là tổng quát.

## Khả năng thành công: 78%

Có thể giảm mạnh lỗi tự xác nhận, nhưng không loại bỏ được lỗi chung của nhiều mô hình cùng họ.

## Nguồn lực

- ML 7–10 ngày.
- QA/NV 5–10 ngày tạo tập claim–evidence có nhãn.

---

# 19.7. R04 — Retrieval bỏ sót nguồn đúng

ACL 2025 cho thấy dense retriever có thiên lệch ngắn, sớm và khớp chữ; tài liệu được retriever ưa thích còn có thể làm RAG tệ hơn so với không cung cấp tài liệu.

## Giải pháp

Đo pipeline theo tầng:

1. Recall@50 của retriever.
2. Recall@10 sau fusion.
3. NDCG/MRR sau rerank.
4. answer correctness khi cung cấp gold evidence.
5. citation correctness.

Bổ sung:

- BM25 + dense;
- query expansion;
- alias/entity normalization;
- multi-query cho câu khó;
- metadata filtering;
- candidate budget khác nhau theo loại câu hỏi.

## Khả năng thành công: 85%

Retrieval có thể cải thiện rất nhiều bằng đánh giá đúng. Tuy nhiên luôn tồn tại tail cases.

## Nguồn lực

- ML 10–15 ngày.
- QA/NV 10 ngày cho 100–300 câu hỏi gold.
- 1 GPU 16–24 GB dùng theo đợt cho benchmark embedding/rerank.

---

# 19.8. R05 — “Không tìm thấy” không có phạm vi tìm

## Giải pháp

Mỗi ResearchRun ghi:

- corpus_generation;
- collection_ids;
- user_acl_snapshot;
- query_variants;
- retriever_version;
- embedding_version;
- reranker_version;
- top_k;
- filters;
- excluded_sources;
- timestamp.

## Khả năng thành công: 95%

Đây là bài toán dữ liệu có tính xác định, dễ kiểm thử.

## Nguồn lực

KT 3–5 ngày.

---

# 19.9. R06 — Lớp chữ PDF có nhưng sai

## Giải pháp

Không dùng điều kiện nhị phân “có text layer = tốt”.

Tính page quality score từ:

- số ký tự;
- Unicode hợp lệ;
- tỷ lệ ký tự lạ;
- độ liên tục từ/ngôn ngữ;
- text bounding boxes;
- reading-order sanity;
- đối chiếu một số vùng với ảnh;
- rule đặc biệt cho tiếng Việt.

Ba trạng thái:

- TRUST_TEXT;
- OCR_REQUIRED;
- REVIEW_OR_SECOND_PASS.

## Khả năng thành công: 90%

## Nguồn lực

- ML 5–8 ngày.
- QA 3–5 ngày xây 200–500 trang thử.

---

# 19.10. R07 — Docling sai bố cục

Docling cung cấp nhiều tuỳ chọn reading order và table extraction; các issue 2026 vẫn cho thấy một số PDF key-value/bảng có thứ tự đọc sai.

## Giải pháp

- Docling là parser mặc định, không phải “sự thật”.
- Tạo regression corpus theo layout.
- Ghi parser_version + options.
- Nếu table/key-value confidence thấp: chuyển sang tuyến khác.
- So sánh FAST/ACCURATE/table cell matching trên tập khó.
- Giữ ảnh trang để người kiểm tra.

## Khả năng thành công: 85%

Không đạt 100% vì PDF layout là bài toán mở.

## Nguồn lực

ML 7–12 ngày, QA 5–8 ngày.

---

# 19.11. R08 — OCR tiếng Việt

PaddleOCR hiện liệt kê PP-OCRv6 hỗ trợ vi, nhưng issue #18254 chỉ ra từ điển PP-OCRv6 từng thiếu nhiều ký tự tiếng Việt có dấu. Vì vậy “hỗ trợ vi” không đủ để chốt chất lượng.

## Giải pháp

Benchmark ít nhất:

- PP-OCRv5 vi;
- PP-OCRv6 vi;
- PaddleOCR-VL;
- một tuyến dự phòng khác nếu cần.

Đo:

- CER;
- lỗi dấu;
- lỗi tên riêng;
- lỗi thuật ngữ;
- quote exactness.

Với câu trích quan trọng từ trang OCR:

- confidence thấp → đối chiếu ảnh;
- có thể chạy OCR thứ hai.

## Khả năng thành công: 82%

Với sách in rõ có thể cao hơn; sách cũ/mờ/đa ngôn ngữ thấp hơn.

## Nguồn lực

- ML 10–15 ngày.
- QA/NV 8–12 ngày.
- GPU 16–24 GB theo đợt.

---

# 19.12. R09 — Bảng/hình/công thức là vùng mù

## Giải pháp

Block model phải có type:

- text;
- table;
- picture;
- chart;
- formula;
- caption.

Giữ:

- original crop;
- page bbox;
- relation caption-of;
- table cells;
- alt/description nếu sinh bằng AI;
- model_version.

Chỉ chạy VLM trên trang/khối cần thiết.

## Khả năng thành công: 75%

Chi phí cao hơn text; chất lượng phụ thuộc loại tài liệu.

## Nguồn lực

ML 15–25 ngày, QA 8–15 ngày, GPU.

---

# 19.13. R10 — EPUB không có trang ổn định

W3C xác định EPUB reflowable có thể phân trang động. Trang tham chiếu tĩnh chỉ đáng tin khi có page-list/pagebreak gắn với nguồn phân trang.

## Giải pháp

Thay assumption Page bằng SourceLocator:

- pdf_page;
- epub_xhtml_path;
- element_id;
- page_break;
- page_list_target;
- paragraph_index;
- character_range.

Nếu EPUB không có pagination source thì **không tự sinh “trang sách” rồi trình bày như trang gốc**.

## Khả năng thành công: 95%

## Nguồn lực

KT 4–7 ngày.

---

# 19.14. R11 — Gần trùng làm mất ấn bản

## Giải pháp

- SHA-256: chỉ tự động hợp nhất file trùng tuyệt đối.
- MinHash/SimHash: chỉ tạo candidate relationship.
- Không auto-merge Edition.
- Diff theo chương/đoạn trước khi đánh dấu cùng văn bản.
- Quan hệ: revised_edition_of, translation_variant_of, derived_from.

## Khả năng thành công: 90%

## Nguồn lực

ML/KT 5–8 ngày, QA 3–5 ngày.

---

# 19.15. R12 — Nợ tri thức của Bộ não thứ hai

## Giải pháp

Mỗi BrainPage ghi:

- compiled_from_generation;
- last_reviewed_at;
- source_count;
- unresolved_claim_count;
- affected_by_new_sources;
- review_priority.

Không tự rebuild mọi trang.

Dùng impact graph nhẹ để xác định trang bị ảnh hưởng.

## Khả năng thành công: 75%

Phần kỹ thuật dễ hơn phần biên tập.

## Nguồn lực

KT 5–8 ngày, NV 5–10 ngày ban đầu; sau đó cần vận hành định kỳ.

---

# 19.16. R13 — Tự bảo trì gây vòng lặp

## Giải pháp

- dedupe proposal bằng fingerprint;
- cooldown window;
- max proposals/run;
- no-op detection;
- cause_id;
- dry-run/report-only mặc định;
- human approval cho thay đổi lớn.

## Khả năng thành công: 90%

## Nguồn lực

KT 5–8 ngày.

---

# 19.17. R14 — Single Writer thành nút nghẽn

## Giải pháp

Single Writer là **quyền ghi logic**, không phải một process.

Thiết kế:

- proposal queue;
- scope locks;
- idempotency key;
- retry;
- dead-letter queue;
- audit log.

## Khả năng thành công: 92%

## Nguồn lực

KT 5–10 ngày.

---

# 19.18. R15 — Giao dịch nhiều kho

AWS mô tả transactional outbox để giải quyết dual-write: dữ liệu nghiệp vụ và outbox event được ghi trong cùng transaction; downstream consumer phải idempotent.

## Giải pháp

PostgreSQL/canonical store là nguồn chân lý:

~~~text
canonical transaction
+ outbox_event
↓
commit
↓
index workers
├── Qdrant
├── QMD
└── các engine khác
~~~

Không cố tạo “distributed transaction” giữa Git/Qdrant/QMD.

## Khả năng thành công: 90%

## Nguồn lực

KT 10–15 ngày, Ops 3–5 ngày.

---

# 19.19. R16 — Thế hệ chỉ mục không đồng bộ

## Giải pháp

Mỗi index build có:

- generation_id;
- canonical_generation;
- status;
- started_at;
- completed_at;
- checksum/count;
- error.

Query response ghi generation đã dùng.

## Khả năng thành công: 95%

## Nguồn lực

KT 4–7 ngày.

---

# 19.20. R17 — Qdrant trade-off

Qdrant xác nhận:

- self-hosted không an toàn mặc định;
- concurrent update có thể tạm thời không nhất quán;
- quantization có trade-off recall–memory;
- snapshot restore bị ràng buộc tương thích phiên bản.

## Giải pháp

V0.1:

- single-node private/local;
- API key;
- bind private/localhost;
- TLS khi qua mạng;
- không bật quantization trước baseline.

Khi scale:

- 3 voting nodes nếu cần HA;
- replication >= 2;
- write consistency phù hợp;
- strong/medium ordering cho workload cần;
- benchmark recall trước/sau quantization.

## Khả năng thành công: 90%

## Nguồn lực

ML 5–8 ngày, AT/Ops 5–8 ngày.

---

# 19.21. R18 — Phân quyền sau retrieval

OWASP khuyến nghị permission-aware vector store và phân tách dữ liệu trong RAG.

## Giải pháp

ACL phải được push xuống retrieval:

~~~text
user identity
↓
policy
↓
allowed collections / tenant / source ids
↓
Qdrant/QMD query
↓
results
~~~

Không lọc sau khi model đã nhìn thấy.

Thêm adversarial tests:

- user A hỏi nội dung của B;
- semantic near-match xuyên tenant;
- cached result;
- logs.

## Khả năng thành công: 93%

## Nguồn lực

KT 7–12 ngày, AT 5–8 ngày.

---

# 19.22. R19 — Chèn lệnh gián tiếp

OWASP nói không có biện pháp “chống prompt injection tuyệt đối” ở tầng mô hình; chiến lược thực tế là giảm quyền và giảm hậu quả.

## Giải pháp

Bốn lớp:

1. **Tách dữ liệu và chỉ dẫn**: mọi chunk nguồn được đóng khung UNTRUSTED.
2. **Least privilege**: researcher chỉ đọc.
3. **Tool mediation**: backend kiểm quyền, không hỏi model “có được phép không?”.
4. **Red-team corpus**: PDF/EPUB chứa prompt injection, text ẩn, instructions trong footnote.

Hành động ghi/xóa/egress cần approval hoặc luật xác định.

## Khả năng thành công: 70%

Không thể bảo đảm model không bị ảnh hưởng; mục tiêu là ngăn ảnh hưởng biến thành hành động nguy hiểm.

## Nguồn lực

AT 8–12 ngày, KT 7–10 ngày; red-team định kỳ.

---

# 19.23. R20 — Nguồn độc hại hoặc sai

## Giải pháp

Source intake có quarantine.

Mỗi nguồn:

- provenance;
- uploader;
- hash;
- trust_status;
- rights_status;
- malware scan;
- hidden-text scan;
- source assessment.

Nguồn chưa duyệt có thể searchable nhưng bị gắn nhãn/giảm quyền sử dụng trong synthesis.

## Khả năng thành công: 75%

Khó nhất là nhận biết “sai nhưng có vẻ đáng tin”.

## Nguồn lực

KT 5–8 ngày, NV 5–10 ngày, AT 2–4 ngày.

---

# 19.24. R21 — Tác tử quá nhiều quyền

OWASP Excessive Agency xác định ba nguyên nhân: quá nhiều chức năng, quá nhiều quyền, quá nhiều tự chủ.

## Giải pháp

Ma trận quyền:

- librarian: read;
- researcher: read;
- verifier: read;
- brain-maintainer: propose;
- writer: apply approved proposal;
- admin: destructive actions.

Backend kiểm policy ở mọi tool call.

## Khả năng thành công: 92%

## Nguồn lực

KT 5–8 ngày, AT 5–8 ngày.

---

# 19.25. R22 — Chuỗi cung ứng

## Giải pháp

Tạo bảng kê thành phần:

- name;
- version;
- source;
- license;
- sha256;
- model revision;
- container digest;
- approved_at.

Áp dụng:

- lockfile;
- image digest;
- model revision pin;
- vulnerability scanning;
- dependency update bot nhưng không auto-deploy;
- offline mirror cho thành phần quan trọng.

## Khả năng thành công: 85%

## Nguồn lực

AT/Ops 5–10 ngày khởi tạo + 0.5 ngày/tuần bảo trì.

---

# 19.26. R23 — RAGFlow 1.0.0-rc1

Release notes hiện mô tả rc1 là preview, rewrite lớn sang Go, migration từ 0.27.2 không rollback trực tiếp và một số API cũ bị bỏ.

## Giải pháp

- Không dùng rc1 làm canonical store.
- Chỉ thử trong môi trường riêng.
- Pin version.
- Backup trước upgrade.
- Adapter contract tests.
- Chỉ productionize sau một chu kỳ ổn định + benchmark.

## Khả năng thành công: 95%

Vì cách giảm tốt nhất là **không phụ thuộc**.

## Nguồn lực

KT 3–5 ngày, QA 2–4 ngày.

---

# 19.27. R24 — Hiểu sai PageIndex local/cloud

## Giải pháp

Capability registry cho engine:

- verified_at;
- verified_version;
- local/cloud;
- data_egress;
- supported_formats;
- license;
- source_url.

Không ghi feature vào kiến trúc nếu chưa có nguồn chính thức.

## Khả năng thành công: 98%

## Nguồn lực

KT 2–3 ngày + rà định kỳ.

---

# 19.28. R25 — PageIndex local giới hạn

README hiện ghi local phù hợp text-based PDF; OCR, image understanding, metadata, folders, MCP và File System nhiều tài liệu ở Cloud.

## Giải pháp

PageIndex local chỉ nhận đầu vào đã chuẩn hóa phù hợp.

Không giao:

- ingest;
- OCR;
- corpus routing;
- canonical metadata.

## Khả năng thành công: 95%

## Nguồn lực

KT/ML 2–5 ngày.

---

# 19.29. R26 — QMD bị dùng quá phạm vi

QMD changelog đã phải xử lý SQLite locking và giới hạn phiên nhúng dài; điều này phù hợp với việc xem nó là local knowledge search chứ không phải primary large-corpus engine.

## Giải pháp

- QMD chỉ index Brain Markdown.
- một writer;
- read concurrency;
- scheduled embed;
- health check;
- index disposable/rebuildable.

## Khả năng thành công: 90%

## Nguồn lực

KT 3–5 ngày.

---

# 19.30. R27 — Overfit bộ đánh giá

## Giải pháp

Tách:

- dev set 50%;
- hidden test 25%;
- adversarial 15%;
- temporal holdout 10%.

Không cho engineer xem đáp án hidden trong lúc tuning.

Sau mỗi thay đổi lớn, chạy hidden một lần và lưu kết quả.

## Khả năng thành công: 90%

## Nguồn lực

QA 5–8 ngày thiết lập; sau đó tự động hóa.

---

# 19.31. R28 — Thiếu câu không có đáp án

Nghiên cứu về abstention cho thấy “biết không trả lời” là một năng lực riêng cần benchmark.

## Giải pháp

Ít nhất 20–30% bộ evaluation là:

- unanswerable;
- evidence insufficient;
- conflicting;
- fake quote;
- wrong edition;
- near-match distractor.

Metric:

- abstention precision;
- abstention recall;
- false answer rate.

## Khả năng thành công: 92%

## Nguồn lực

QA/NV 3–6 ngày.

---

# 19.32. R29 — Confidence không phải xác suất

Nghiên cứu 2025 cho thấy calibration ở claim nhỏ trong long-form kém hơn response-level; confidence đa ngôn ngữ cũng cần đánh giá riêng.

## Giải pháp

Giai đoạn đầu:

- bỏ “0.97 confidence” nếu chưa calibrate;
- dùng status: direct/strong/weak/insufficient/conflict;
- model_score không hiển thị như probability.

Nếu cần số:

- calibration set tiếng Việt riêng;
- reliability diagram;
- Brier score/ECE;
- calibrate theo claim type.

## Khả năng thành công: 65%

Có thể làm điểm hữu ích hơn, nhưng khó biến thành xác suất sự thật tuyệt đối.

## Nguồn lực

ML 8–15 ngày, QA 5–8 ngày.

---

# 19.33. R30 — Bất biến và quyền xóa

Luật bảo vệ dữ liệu cá nhân hiện hành của Việt Nam có quyền yêu cầu xóa; Nghị định 356/2025 quy định quy trình/thời hạn trong các trường hợp áp dụng.

## Giải pháp

Bất biến chỉ áp dụng cho lịch sử thông thường.

Deletion workflow:

1. legal/security request;
2. locate all derivatives;
3. tombstone canonical record;
4. purge source;
5. purge OCR/text/chunks;
6. remove Qdrant/QMD;
7. backup retention handling;
8. verification report.

Audit log chỉ lưu metadata cần thiết, không lưu lại nội dung đã phải xóa.

## Khả năng thành công: 90%

## Nguồn lực

KT 7–10 ngày, PL 3–5 ngày, Ops 2–4 ngày.

---

# 19.34. R31 — Bản quyền

## Giải pháp

Rights registry bắt buộc trước ingest lớn:

- public_domain;
- licensed;
- owned_internal;
- research_only;
- unknown;
- prohibited.

Policy quyết định:

- được scan không;
- được OCR không;
- được cloud không;
- ai được search;
- có được xuất đoạn dài không;
- retention.

Nguồn “unknown” không được mặc định coi là được phép.

## Khả năng thành công: 70%

Kỹ thuật kiểm soát tốt, nhưng quyền thực tế phụ thuộc từng bộ sưu tập và pháp luật áp dụng.

## Nguồn lực

PL 5–15 ngày cho policy + review theo collection; NV 3–5 ngày lập inventory.

---

# 19.35. R32 — Dữ liệu cá nhân

Từ 01/01/2026, Luật 91/2025/QH15 và Nghị định 356/2025/NĐ-CP là khung hiện hành. Nghị định yêu cầu các biện pháp về quyền chủ thể, dữ liệu nhạy cảm, AI, đánh giá tác động và chuyển dữ liệu xuyên biên giới trong các trường hợp áp dụng.

## Giải pháp

Data classification:

- PUBLIC;
- INTERNAL;
- PERSONAL;
- SENSITIVE_PERSONAL;
- SECRET.

Mỗi Source có:

- processing_purpose;
- legal_basis;
- retention;
- allowed_users;
- allowed_models;
- cross_border_allowed;
- deletion_policy.

Trước triển khai thật:

- xác định vai trò controller/processor;
- đánh giá tác động nếu thuộc trường hợp áp dụng;
- thủ tục quyền chủ thể dữ liệu;
- incident procedure.

## Khả năng thành công: 85%

## Nguồn lực

PL 8–15 ngày, AT 8–12 ngày, KT 8–12 ngày.

---

# 19.36. R33 — Cloud fallback

## Giải pháp

Tool registry:

- execution_location;
- sends_text;
- sends_images;
- provider;
- region;
- retention;
- allowed_data_classes.

Router bắt buộc policy check trước call.

Ví dụ:

- SENSITIVE_PERSONAL → LOCAL_ONLY;
- COPYRIGHT_RESEARCH_ONLY → theo policy;
- PUBLIC → cloud allowed nếu được cấu hình.

## Khả năng thành công: 95%

## Nguồn lực

KT 5–8 ngày, AT 3–5 ngày.

---

# 19.37. R34 — Phình lưu trữ

## Giải pháp

Pilot phải đo bytes per source byte cho:

- original;
- page render;
- OCR;
- parsed JSON;
- chunks;
- embeddings;
- index;
- backups.

Storage tiers:

- source: giữ lâu;
- derived canonical: giữ;
- rebuildable index: có thể xóa/xây lại;
- temporary page renders: TTL.

## Khả năng thành công: 92%

Không làm dữ liệu nhỏ đi hoàn toàn, nhưng biến chi phí thành thứ dự báo được.

## Nguồn lực

Ops 3–5 ngày, ML 2–3 ngày.

---

# 19.38. R35 — Reindex cost

## Giải pháp

- model/chunker versioning;
- canary 1–5%;
- benchmark trước full rebuild;
- dual index A/B;
- resumable jobs;
- content hash skip unchanged;
- capacity budget.

## Khả năng thành công: 85%

## Nguồn lực

ML/Ops 7–12 ngày.

---

# 19.39. R36 — Backup nhưng không restore

Qdrant snapshot có ràng buộc tương thích minor version; vì vậy backup plan phải đi cùng restore plan.

## Giải pháp

Mỗi tháng/quarter:

- restore source store;
- restore PostgreSQL;
- restore Qdrant hoặc rebuild;
- restore Brain Git;
- verify checksum;
- chạy 20 smoke queries.

Định nghĩa:

- RPO;
- RTO;
- restore owner.

## Khả năng thành công: 95%

## Nguồn lực

Ops 5–8 ngày setup, 0.5–1 ngày mỗi drill.

---

# 19.40. R37 — Thuế adapter

## Giải pháp

Một internal contract ổn định:

- SearchRequest;
- Candidate;
- SourceLocator;
- ScoreBreakdown;
- Health;
- Rebuild.

Mỗi engine phải qua conformance test.

Quy tắc:

> tối đa 1 primary + 1 experimental engine cho mỗi capability.

## Khả năng thành công: 80%

## Nguồn lực

KT 5–10 ngày; tiết kiệm lớn về sau.

---

# 19.41. R38 — Data model cứng

## Giải pháp

Tách:

- ContentObject/SourceDocument: tổng quát.
- Work/Edition: profile dành cho sách.
- StructuralNode: chương/mục/scene/segment.
- SourceLocator: page/xpath/timecode/element.

Không phá mô hình sách hiện tại; chỉ thêm abstraction trên.

## Khả năng thành công: 85%

## Nguồn lực

KT 7–12 ngày.

---

# 19.42. R39 — Quản trị Brain

## Giải pháp

Editorial policy:

- canonical title;
- alias;
- merge/split rules;
- owner;
- page type;
- max scope;
- minimum evidence;
- review state.

Linter:

- orphan page;
- duplicate alias;
- unsupported claim;
- stale generation;
- broken link.

## Khả năng thành công: 75%

Không thể loại bỏ hoàn toàn công việc biên tập.

## Nguồn lực

NV 8–15 ngày policy, KT 3–5 ngày linter; sau đó ongoing review.

---

# 19.43. R40 — UX quá nặng

## Giải pháp

Hai tầng:

### Bình thường

- câu trả lời;
- 2–5 nguồn;
- cảnh báo thiếu/mâu thuẫn.

### Kiểm chứng

- claim ledger;
- evidence;
- search scope;
- provenance;
- versions;
- conflict details.

Không buộc người đọc bình thường hiểu toàn bộ kiến trúc.

## Khả năng thành công: 85%

## Nguồn lực

SP/UX 5–10 ngày, KT 3–5 ngày.

---

# 19.44. R41 — Người dùng chỉ cần tìm sách

## Giải pháp

Pilot 10–20 người dùng thật trong 4–6 tuần.

Theo dõi:

- số query/người/tuần;
- tỷ lệ mở source;
- tỷ lệ dùng Brain;
- tỷ lệ quay lại;
- thời gian tiết kiệm;
- use case nào lặp lại;
- feature nào không ai dùng.

Feature gates:

- Brain advanced chỉ bật cho nhóm cần;
- graph/multi-agent không build trước nhu cầu.

## Khả năng thành công: 65%

Đây là rủi ro thị trường/hành vi, không thể giải bằng code.

## Nguồn lực

SP 10–15 ngày + 10–20 người dùng pilot; KT 3–5 ngày telemetry.

---

# 19.45. R42 — Hứa quá mức

## Giải pháp

Công bố rõ:

- hệ thống có thể bỏ sót;
- OCR có thể sai;
- nguồn có thể không đáng tin;
- citation không phải proof of truth;
- AI có thể abstain;
- high-stakes claim cần human review.

Đặt SLO theo lớp, không có SLO “100% đúng”.

## Khả năng thành công: 95%

## Nguồn lực

SP/KT 2–4 ngày.

---

# 19.46. Chín chương trình khắc phục dùng chung

Thay vì triển khai 42 rủi ro như 42 dự án, nên gom thành chín chương trình.

## Chương trình A — Khóa phạm vi và chứng minh nhu cầu

Bao phủ: R01, R40, R41, R42.

**Thời gian:** 1–2 tuần.  
**Người:** 1 KT + 0.5 SP.

## Chương trình B — Chính sách nguồn và quyền

Bao phủ: R02, R20, R30, R31, R32, R33.

**Thời gian:** 2–4 tuần.  
**Người:** 0.5 KT + PL + AT + NV.

## Chương trình C — Chất lượng ingest/OCR/layout

Bao phủ: R06–R11.

**Thời gian:** 3–5 tuần.  
**Người:** 1 ML + 0.5–1 QA/NV + GPU theo đợt.

## Chương trình D — Retrieval/evidence/evaluation

Bao phủ: R03–R05, R27–R29.

**Thời gian:** 3–5 tuần.  
**Người:** 1 ML + 0.5–1 QA/NV.

## Chương trình E — An toàn AI và phân quyền

Bao phủ: R18–R22, R33.

**Thời gian:** 2–4 tuần.  
**Người:** 1 KT + 0.5 AT.

## Chương trình F — Nhất quán dữ liệu và vận hành

Bao phủ: R14–R17, R34–R36.

**Thời gian:** 2–4 tuần.  
**Người:** 1 KT + 0.5 Ops.

## Chương trình G — Quản trị Bộ não thứ hai

Bao phủ: R12, R13, R39.

**Thời gian:** 2–3 tuần để dựng khung; sau đó ongoing.  
**Người:** 0.5 KT + NV.

## Chương trình H — Kiểm soát công cụ bên ngoài

Bao phủ: R23–R26, R37.

**Thời gian:** 1–2 tuần.  
**Người:** 1 KT.

## Chương trình I — Mô hình dữ liệu mở rộng

Bao phủ: R10, R38.

**Thời gian:** 1–2 tuần.  
**Người:** 1 KT.

---

# 19.47. Nguồn lực tổng thể thực tế cho bản 0.1 “đã giảm rủi ro”

Không nên cộng toàn bộ bảng vì nhiều biện pháp trùng nhau.

Một đội tối thiểu hợp lý:

- **1 kiến trúc/backend**: toàn thời gian.
- **1 ML/data engineer**: toàn thời gian.
- **1 QA/data curator**: 0.5–1 người.
- **AT/DevSecOps**: 0.2–0.4 người.
- **PL/privacy**: 5–15 ngày tư vấn tập trung.
- **SP/UX**: 0.2–0.3 người.
- **NV/domain expert**: 5–15 ngày gán nhãn/review.

## Thời gian lịch

Với 2.5–3.5 người tương đương toàn thời gian:

> **6–10 tuần** để có bản 0.1 nhỏ nhưng có control P0/P1 tương đối nghiêm túc.

Một người làm một mình:

> thực tế nên tính **3–5 tháng**, nếu không cắt phạm vi.

## Hạ tầng

Cho pilot 200–500 trang và 100–300 câu hỏi:

- 1 máy CPU/RAM tốt;
- SSD/NVMe;
- 1 GPU khoảng 16–24 GB theo đợt là đủ để benchmark phần lớn lựa chọn nhỏ;
- không cần cluster Qdrant ở 0.1;
- môi trường test tách dữ liệu thật;
- backup riêng.

---

# 19.48. Thứ tự phải làm

## Trước dòng mã lớn tiếp theo — P0

1. R01: khóa scope.
2. R31/R32/R33: rights + personal data + cloud policy.
3. R18/R19/R21: retrieval ACL + prompt injection boundary + agent permissions.
4. R15/R16: outbox + generations.
5. R06–R08: ingest/OCR quality gates.

## Trong 0.1 — P1

6. R04: retrieval recall.
7. R03/R28/R29: evidence, abstention, confidence.
8. R27: hidden/adversarial evaluation.
9. R34–R36: storage/reindex/restore.

## Chỉ sau khi 0.1 chứng minh giá trị

10. R12/R13/R39: Brain automation.
11. R23–R26: deeper external-engine integrations.
12. graph/multi-agent nâng cao.

---

# 19.49. Ngưỡng “GO / NO-GO” đề xuất cho 0.1

Đây là **mục tiêu kỹ thuật khởi đầu**, phải điều chỉnh theo corpus thật.

## GO nếu

- provenance/locator đúng >= 99% trên pilot;
- không có rò dữ liệu trong test ACL;
- không có hành động nhạy cảm trái phép trong prompt-injection red-team;
- Recall@50 >= 95% trên hidden set cho nhóm câu hỏi quan trọng;
- Recall@10 >= 90% sau fusion/rerank;
- citation support precision >= 97% cho claim được xuất bản;
- false-answer rate trên unanswerable <= 5%;
- restore drill thành công;
- chi phí ingest/reindex đo được và chấp nhận được;
- ít nhất một use case có người dùng quay lại thường xuyên.

## NO-GO / sửa trước nếu

- page/source locator sai;
- OCR tiếng Việt làm sai câu trích thường xuyên;
- retrieval bỏ sót nguồn gold;
- ACL leak;
- prompt injection gây tool side effect;
- không xóa sạch được dữ liệu khi có yêu cầu;
- không thể rebuild index;
- chi phí vận hành vượt khả năng.

---

# 19.50. Những rủi ro không thể “khắc phục hoàn toàn”

Bốn nhóm nên được quản lý, không hứa loại bỏ:

1. **Sự thật của nguồn** — không thể tự động bảo đảm.
2. **Prompt injection** — không có biện pháp tuyệt đối; phải giới hạn hậu quả.
3. **Confidence của LLM** — không nên xem là xác suất sự thật nếu chưa hiệu chỉnh.
4. **Product–market fit** — chỉ người dùng thật mới trả lời được.

Với bốn nhóm này, thành công nghĩa là:

> **phát hiện tốt hơn, giới hạn hậu quả, minh bạch bất định và có đường kiểm tra bởi con người.**

---

# 19.51. Nguồn nghiên cứu chính

## An toàn và quản trị AI

- OWASP LLM01 Prompt Injection: https://genai.owasp.org/llmrisk/llm01-prompt-injection/
- OWASP LLM03 Supply Chain: https://genai.owasp.org/llmrisk/llm032025-supply-chain/
- OWASP LLM06 Excessive Agency: https://genai.owasp.org/llmrisk/llm062025-excessive-agency/
- OWASP LLM08 Vector and Embedding Weaknesses: https://genai.owasp.org/llmrisk/llm082025-vector-and-embedding-weaknesses/
- NIST Generative AI Profile: https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-generative-artificial-intelligence

## Retrieval, evidence, abstention và confidence

- Citation Failure, TACL 2026: https://aclanthology.org/2026.tacl-1.66/
- Collapse of Dense Retrievers, ACL 2025: https://aclanthology.org/2025.acl-long.447/
- Source Reliability RAG, EMNLP 2025: https://aclanthology.org/2025.emnlp-main.1738/
- Know Your Limits — Abstention, TACL 2025: https://aclanthology.org/2025.tacl-1.26/
- Atomic Calibration, 2025: https://aclanthology.org/2025.findings-ijcnlp.9/
- MlingConf, 2025: https://aclanthology.org/2025.findings-acl.129/

## Dữ liệu và tính nhất quán

- AWS Transactional Outbox: https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/transactional-outbox.html

## Công cụ

- Qdrant Security: https://qdrant.tech/documentation/security/
- Qdrant Consistency: https://qdrant.tech/documentation/scaling/consistency-guarantees/
- Qdrant Quantization: https://qdrant.tech/documentation/manage-data/quantization/
- Qdrant Snapshots: https://qdrant.tech/documentation/operations/snapshots/
- RAGFlow release notes: https://ragflow.io/docs/v1.0.0-rc1/release_notes
- PageIndex README: https://github.com/VectifyAI/PageIndex/blob/main/README.md
- QMD changelog: https://github.com/tobi/qmd/blob/main/CHANGELOG.md
- Docling advanced options: https://github.com/docling-project/docling/blob/main/docs/usage/advanced_options.md
- PaddleOCR OCR docs: https://github.com/PaddlePaddle/PaddleOCR/blob/main/docs/version3.x/pipeline_usage/OCR.en.md
- PaddleOCR Vietnamese issue: https://github.com/PaddlePaddle/PaddleOCR/issues/18254

## EPUB

- W3C EPUB 3.4: https://www.w3.org/TR/epub-34/
- W3C EPUB Accessibility: https://www.w3.org/TR/epub-a11y-12/

## Pháp lý Việt Nam

- Luật Bảo vệ dữ liệu cá nhân 91/2025/QH15: https://chinhphu.vn/?classid=1&docid=214590&pageid=27160&typegroupid=3
- Nghị định 356/2025/NĐ-CP: https://vbpl.vn/bocongan/Pages/vbpq-toanvan.aspx?ItemID=187276
- Luật sửa đổi Luật Sở hữu trí tuệ 07/2022/QH15 — WIPO Lex: https://www.wipo.int/wipolex/en/legislation/details/21740
