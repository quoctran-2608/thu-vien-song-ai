# 21. Đối chiếu ba repo phục vụ dự án sách BĂNG HÀ đến GIÁC NGỘ (11/10/2026)

> **Loại tài liệu:** Báo cáo khảo sát hiện trạng và đề xuất kết nối, không phải nghiệm thu liên thông hay quyết định chuyển chức năng đã phê duyệt. 
>
> **Mốc GitHub đã đọc trực tiếp:** `BuddhismDocuments-for-AI` main `17292dedf86ba9f732be3e99b40d57f37be03739`; `Bang-ha-giac-ngo` main `4345737ae16638b19226ea1b11007e6ffa4faf62`; `thu-vien-song-ai` main `d120c7f92666df38caa7be535e1c81ac868f0a48`.
>
> **Phân biệt:** có mã/dữ liệu; có chạy trong từng repo; có kiểm thử báo cáo; có chạy liên thông; đã nghiệm thu học thuật; chỉ có đặc tả. Chúng không đồng nghĩa nhau.

## 1. Phán quyết

- **BuddhismDocuments-for-AI/BCR 2.0** đã triển khai lớp nghiên cứu Phật học có kiểm chứng nguồn/câu trích (A), cấu trúc đánh giá luận điểm (B), kiểm phạm vi phản chứng và sự phụ thuộc nguồn (C), hồ sơ nghiên cứu có phiên bản (D) và adapter/CLI (E). Chưa nghiệm thu công bố Research, chưa có semantic approval đáng tin cậy chạy sản xuất, chưa đo chất lượng học thuật tổng thể, full Connector/Work chưa được xác nhận. Không được hạ nó thành “chỉ có search”.
- **Bang-ha-giac-ngo** có kho Nikāya/A-hàm/Vinaya Pāḷi–Hán–Việt, bản đọc EPUB/DOCX, giao diện tra cứu offline và các chương trình truy hồi nhiều ngữ liệu di sản, dữ liệu Parquet, bộ sổ claim/evidence/contradiction mẫu. Không được hạ nó thành “chỉ là dữ liệu”; đồng thời không biến mô tả tiến độ/hệ thống cục bộ ngoài repo thành bằng chứng toàn bộ dịch vụ đang chạy trên máy mới.
- **thu-vien-song-ai** hiện là bộ đặc tả về nhập PDF/EPUB/OCR, kho dữ liệu chuẩn, tìm kết hợp/đa phương thức, router đọc sâu, Bộ não thứ hai Markdown và không gian nghiên cứu. **Chưa có phần mềm sản xuất trong repo.**
- **Khoảng trống lớn nhất cho sách:** không phải xây lại A/B/C/D, mà là hợp đồng liên thông ba hệ, kiểm nghiệm dữ liệu thực, nguồn khoa học/lịch sử hiện đại từ Băng Hà đến Ấn Độ cổ, trí nhớ biên tập qua nhiều nhiệm vụ và quy trình từ luận điểm tới chương sách.

## 2. Trách nhiệm đề xuất (mỗi chức năng có một chủ sở hữu chính)

| Lĩnh vực | Chủ sở hữu chính | Thành phần còn lại dùng như thế nào |
|---|---|---|
| Văn bản Pāḷi/Hán/Việt, tủ sách đọc, UI sẵn có và bộ sổ minh họa của dự án | `Bang-ha-giac-ngo` | Xuất dữ liệu và công cụ qua bộ chuyển tiếp; không viết lại corpus |
| Nguồn Phật học quốc tế ghim phiên bản, witness, lemma, variants, parallels | `BuddhismDocuments-for-AI` | Dùng truy hồi 1.0 và luật provenance; không sao chép nguồn lên một kho “gốc” mới |
| Kiểm nguồn, câu trích, claim và phản chứng cho nguồn BCR | `BuddhismDocuments-for-AI` BCR 2.0 | Kế thừa lõi A/B/C/D/E; chuẩn hóa bộ chuyển tiếp để dùng cho nguồn ngoài Phật học; không giả định 13 resolver đã đủ |
| Ingest tài liệu tổng quát PDF/EPUB/MOBI, trang/ảnh/OCR | `thu-vien-song-ai` — **cần triển khai** | Không thay parser có cấu trúc và mã nguồn chuyên biệt của hai hệ hiện tại |
| Chỉ mục tìm theo ý nghĩa, xếp hạng lại, tìm thị giác, chọn chiến lược đọc | `thu-vien-song-ai` — **cần benchmark và triển khai** | Đứng bổ sung đường tìm chữ có sẵn; trả con trỏ về bản gốc |
| Giao diện tìm xuyên tất cả nguồn | `thu-vien-song-ai` — **cần triển khai** | Chỉ điều phối, không tự tạo kết luận hay cố đồng bộ tất cả record vật lý |
| Bộ não thứ hai dạng Markdown và quy tắc biên tập | `thu-vien-song-ai` — **cần triển khai** | Chỉ nhận claim đã đủ điều kiện và có provenance; không biến tài liệu nguồn thành wiki |
| Đề cương, chương, lập luận, bản thảo và vòng biên tập sách | Workspace chuyên cho `BĂNG HÀ đến GIÁC NGỘ` — **chưa có hệ chạy** | Dùng mọi kho và bộ máy; không được đồng nhất bản thảo với nguồn học thuật |
| Kiểm quyền, giấy phép, nguồn dùng được, xử lý nhạy cảm | Tầng policy chung — **cần thiết kế hợp đồng** | Policy áp trước truy hồi và trước xuất bản; không lấy “có trên GitHub/HF” làm giấy phép tái sử dụng |

Đây là phân quyền đề xuất để tránh trùng mã, không phải phê duyệt chuyển quyền sở hữu dữ liệu.

## 3. Ma trận những gì thật sự đã có

| Năng lực | BCR 2.0 | Bang-ha-giac-ngo | Thư Viện Sống |
|---|---|---|---|
| Kho văn bản có cấu trúc, định vị và nguồn | Đã có | Đã có | Đặc tả tổng quát |
| Nguồn Phật học quốc tế ghim commit | 13 nguồn | Có nguồn giao thoa, không cùng cơ chế quản lý | Dùng qua bộ chuyển tiếp |
| Bộ dữ liệu Pāḷi/Hán/Việt của dự án | Có bản nguồn quốc tế/bản dịch một phần | Mạnh | Kết nối |
| Tra cứu từ khóa/FTS và metadata | Đã có | Đã có | Mục tiêu |
| Dị bản/lemma/nhân chứng/quan hệ song hành | Mạnh về dữ liệu/luật | Có nhiều công cụ và quan hệ | Kế thừa |
| UI ngoại tuyến / trực quan | CLI/Python; không có web UI trong repo BCR hiện tại | Có web/đồ thị/giỏ trích dẫn | Chưa triển khai |
| Kiểm câu trích tại nguồn thật | Quick A với ba resolver có thử nguồn thật | Có định vị và một số kiểm tra nguồn | Tái dùng BCR A có adapter |
| Luận điểm và phản chứng | B/C lõi, có tests; assessment cần host đáng tin | Tri-ledger mẫu, graph 30 nút/28 cạnh | Đặc tả |
| Hồ sơ nghiên cứu có lịch sử | D/E lưu nháp, phiên bản, review package | Có artifact/sổ thực nghiệm | Đặc tả liên thông |
| Nghiệm thu kết luận học thuật và quyền công bố | **Chưa**, Research publication đóng | Chưa chứng minh có workflow độc lập toàn diện | Chưa triển khai |
| Semantic search, hybrid, reranker hiện đại | Không phải đường chính | Không phải đường chính | Thiết kế/benchmark |
| OCR/PDF/EPUB ingest tổng quát | Không | Có biên tập/dữ liệu nhiều định dạng nhưng không phải ingest engine tổng quát đã nghiệm thu | Thiết kế |
| Bộ não thứ hai Markdown biên tập | Không | Không | Thiết kế |
| Quản trị chương sách có liên kết tới claim nguồn | Không | Chưa có workflow | Cần xây |

## 4. Ba loại trùng lặp cần kiểm tra trước khi viết mã

**Dữ liệu giao thoa:** SuttaCentral, CBETA và bản văn Hán/Pāḷi có thể xuất hiện trong cả hai corpus chuyên ngành. Không dùng “cùng tên kinh” để tự nhận cùng bản dịch, phiên bản, nhân chứng hoặc đoạn. Tạo `SourceIdentityMap` gồm upstream, revision, work, edition, language, translator, witness, locator, text_role, hash khi có. Dùng quan hệ `same_witness`, `parallel`, `translation_of`, `derived_from` và `possibly_equivalent` chỉ khi có căn cứ. Một tác phẩm có thể có nhiều bản ghi nhưng không được tính là nhiều nguồn độc lập.

**Hai bộ sổ luận điểm:** BCR B/C/D đã có kiểm tra/hồ sơ, Bang có tri-ledger mẫu. Không tạo bộ ba thứ ba một cách độc lập ở `thu-vien-song-ai`. Nên coi BCR A/B/C/D là ứng viên cho lõi kiểm chứng chung; nhập dữ liệu Bang qua schema/hợp đồng, thử trạng thái và ý nghĩa luận điểm tương thích trước. BCR Research hiện không cho phép công bố; adapter không được tự bỏ khóa.

**Hai đường tìm và hai giao diện:** BCR có FTS/corpus đa nguồn; Bang có FTS và UI/web, cộng hồ dữ liệu Parquet; Thư Viện Sống định xây hybrid. Chỉ mục semantic/visual phải là chỉ mục bổ sung hoặc chỉ mục hợp nhất có thể xây lại, **không tạo kho văn bản “gốc thứ ba”** và không làm cho pointer thành bằng chứng.

## 5. Hợp đồng tích hợp tối thiểu

Đề xuất các đối tượng máy đọc cấp cao:

- `SourceIdentity`: provider, repository/source URI, immutable_revision, file_hash (nếu có), work_id, edition_id, language, translator, witness, text_role, rights_policy.
- `SourceLocator`: `type` = source_record/pdf_page/epub_xpath/text_range/tei_xpath/json_pointer; giá trị và phạm vi; không bịa số trang EPUB.
- `Candidate`: query, search_strategy, score/rank, provider, source_identity, locator, generation. Chỉ có giá trị đề xuất nguồn cần mở.
- `VerifiedEvidence`: candidate, actual immutable-source read, exact quotation/context, verification status/method/version, limitations.
- `AtomicClaim`: claim_id, text, type, evidence links, semantic assessment, counterevidence scope, reviewer/approval, lifecycle state.
- `ResearchRun`: question, subquestions, queries, versions, source scopes, evidence/claims, gaps, reviews, audit history.
- `BrainPageProposal`: destination/topic, claims/evidence, source generations, review status, human-readable Markdown diff.
- `BookClaim` / `ChapterSection`: lập luận sách liên kết tới claim đã duyệt và nguồn thật, vấn đề còn mở, chỉnh sửa văn phong **không làm thay nghĩa bằng chứng**.

Với adapter, nguyên tắc cứng:

~~~text
BCR source ──→ BCR retrieval / A verification ─┐
Bang source ─→ Bang retrieval ─→ adapter ──────┼→ cùng hợp đồng Candidate/Evidence
PDF source ──→ ingest + retrieval + verifier ─┘
                    ↓
         BCR B/C/D có thể tái dùng sau khi kiểm contract
                    ↓
              nghiên cứu có kiểm toán
                    ↓
               Brain đề xuất
                    ↓
             dàn ý / chương sách
~~~

BCR A hiện kiểm với Bilara JSON, CBETA TEI, 84000 TEI. Nguồn Bang/PDF cần verifier/resolver tương ứng; không gắn nhãn VERIFIED chỉ vì adapter trả một JSON có `verified:true`.

## 6. Những gì còn thiếu, theo mục tiêu sách

**P0 — để bắt đầu làm nghiên cứu có căn cứ:**
1. Kiểm toán các bản trùng/giao thoa giữa BCR và Bang trên 20–50 nguồn mẫu.
2. Chốt hợp đồng `SourceIdentity`, `Candidate`, `Evidence`, `Claim` và `ResearchRun`; tạo adapter hai bên.
3. Thực hiện thử nghiệm end-to-end trên **một chủ đề Phật học**, không cần AI ghi Brain: hỏi → tìm hai repo → mở nguồn → kiểm trích dẫn → ghi claim/counterevidence → xuất hồ sơ.
4. Phân định rõ ai được đánh giá nghĩa, ai được phê duyệt, ai được ghi và ai được công bố; không mở khóa Research publication trước nghiệm thu.

**P1 — để mở rộng cuốn sách vượt Phật giáo:**
5. Lập danh mục nguồn cho Băng Hà/Pleistocene, di truyền học cổ, khảo cổ, tiến hóa con người, nông nghiệp, văn minh sông Ấn, Veda/Upaniṣad/śramaṇa, lịch sử Phật giáo; đánh dấu gaps và độ tin cậy/niên đại từng khẳng định.
6. Ingest PDF/EPUB và nghiên cứu học thuật hiện đại có trang/ấn bản/DOI, OCR kiểm chất lượng khi cần, policy bản quyền và quyền dữ liệu.
7. Benchmark hybrid BM25+dense+reranker, tìm thị giác và long-context so với lexical baseline; không thay search hiện hữu trước khi có bằng chứng tăng chất lượng.

**P2 — để thật sự viết sách:**
8. Bộ não thứ hai Markdown theo chủ đề, chỉ nhận bản đã thẩm định và có lịch sử chỉnh sửa.
9. `BookProject`: luận đề tổng thể, ma trận chương–câu hỏi–claim–bằng chứng, timeline niên đại, unresolved gaps, bản thảo và sửa đổi.
10. `Chapter Audit`: từng khẳng định thực chứng/học thuật trong chương trỏ tới evidence, nguồn/ấn bản/trang, biết ghi tranh luận và không trích nguồn kinh như chứng minh sự kiện khoa học.

## 7. Một thử nghiệm nhỏ có thể bác bỏ giả thuyết tích hợp

**Chủ đề:** “Vô thường và vô ngã trong Nikāya/A-hàm”, có Pāḷi/Hán/Việt và bản dịch cụ thể.

**Đầu vào:** 15–30 câu hỏi, 20–50 vị trí nguồn đã xác minh, các bản văn giao thoa giữa hai repo.

**Đầu ra kỳ vọng:**
- tìm được bằng chứng qua cả hai provider;
- cho biết nguồn nào thật sự độc lập và nguồn nào chỉ lặp lại cùng một bản;
- không trộn lời kinh, dịch giả và chú giải;
- A kiểm đoạn/câu trích qua resolver phù hợp;
- tạo claim và ghi phản chứng/phạm vi chưa tìm;
- xuất một hồ sơ nghiên cứu, **chưa công bố học thuật**;
- đo thời gian, số truy vấn, tỷ lệ định vị đúng, số trùng bị loại và tỷ lệ chưa đủ bằng chứng.

**Dừng/sửa thiết kế** nếu phải copy lại toàn corpus, phá API sẵn có, bỏ cửa A/B/C/D, mất locator/ấn bản/nhân chứng, hoặc không truy ngược được trích dẫn về nguồn nguyên bản.

## 8. Không nên làm

- Không hợp nhất vật lý 13 upstream, hàng nghìn file Băng Hà và thư viện PDF vào một repo Git khổng lồ.
- Không “port” lại toàn bộ hai hệ đã có vào Thư Viện Sống.
- Không chép BCR Claim Gate thành hệ thứ ba khác ngữ nghĩa.
- Không chọn Qdrant/RAGFlow/graph/multi-agent vì mới hơn mà chưa chứng minh giá trị.
- Không coi `docs/20` hay README là bằng chứng phần mềm Thư Viện Sống đã chạy.
- Không coi số record/FTS là số hiểu biết đã kiểm chứng; Băng Hà graph được đọc tại mốc này có 30 nodes và 28 links.
- Không xem các số tiến độ cũ của Băng Hà như runtime hiện tại: `docs/TIEN_DO_DU_AN.md` ghi rõ chúng là ảnh chụp lịch sử và một số tuyên bố QA cũ đã được đính chính.
- Không dùng repo BCR làm bằng chứng các kết luận về cổ khí hậu/khảo cổ hiện đại khi nguồn ngoài lĩnh vực chưa nhập.

## 9. Cửa đọc nguồn

- [BCR main / README](https://github.com/quoctran-2608/BuddhismDocuments-for-AI/blob/main/README.md)
- [BCR 2.0 README](https://github.com/quoctran-2608/BuddhismDocuments-for-AI/blob/main/docs/v2/README.md)
- [BCR 2.0 acceptance](https://github.com/quoctran-2608/BuddhismDocuments-for-AI/blob/main/docs/v2/ACCEPTANCE.md)
- [BCR E report](https://github.com/quoctran-2608/BuddhismDocuments-for-AI/blob/main/docs/v2/E_REPORT.md)
- [BCR onboarding, mã và adapter](https://github.com/quoctran-2608/BuddhismDocuments-for-AI/blob/main/docs/AI_ONBOARDING.md)
- [Băng Hà README](https://github.com/quoctran-2608/Bang-ha-giac-ngo/blob/main/README.md)
- [Băng Hà tra cứu cục bộ](https://github.com/quoctran-2608/Bang-ha-giac-ngo/blob/main/tools/local_corpus_framework/README.md)
- [Băng Hà trạng thái có kiểm toán](https://github.com/quoctran-2608/Bang-ha-giac-ngo/blob/main/docs/TIEN_DO_DU_AN.md)
- [Thư Viện Sống README](../README.md)
- [Thư Viện Sống bản thử nghiệm 0.1](17-huong-dan-bat-dau-trien-khai-v0.1.md)
