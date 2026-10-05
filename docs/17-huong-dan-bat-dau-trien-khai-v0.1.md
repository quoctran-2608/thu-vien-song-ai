# 17. Hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1

Tài liệu này trả lời câu hỏi:

> **Nếu một kỹ sư mới vào dự án hôm nay thì phải bắt đầu từ đâu?**

Đây không phải hướng dẫn cài đặt một sản phẩm đã hoàn thiện. Repo hiện là **bộ đặc tả kiến trúc**; mã triển khai sản xuất chưa được xây đầy đủ.

Trước khi triển khai dữ liệu thật hoặc mở quyền cho nhiều người dùng, phải đọc thêm [Kế hoạch khắc phục rủi ro](19-ke-hoach-khac-phuc-rui-ro.md), đặc biệt các mục P0 về quyền dữ liệu, phân quyền truy hồi, chèn lệnh gián tiếp và nhất quán chỉ mục.

Mục tiêu của bản kỹ thuật 0.1 là chứng minh một vòng nhỏ nhưng hoàn chỉnh:

```text
nguồn gốc
↓
đọc / nhận dạng chữ khi cần
↓
kho dữ liệu chuẩn
↓
tìm kết hợp
↓
xếp hạng lại
↓
bằng chứng
↓
trả lời có trang và nguồn
↓
đánh giá bằng bộ câu hỏi chuẩn
```

---

## 17.1. Điều phải đọc trước khi viết mã

Một kỹ sư mới nên đọc theo thứ tự:

1. [Tài liệu tổng thể](00-TAI-LIEU-TONG-THE-V1.0.md)
2. [Số hóa và kho dữ liệu chuẩn](02-so-hoa-va-chuan-hoa-nguon.md)
3. [Hệ tìm bằng chứng, RAG và đọc phân tầng](03-kien-truc-rag.md)
4. [Mô hình dữ liệu và truy nguồn](07-mo-hinh-du-lieu.md)
5. [Đánh giá chất lượng](09-danh-gia-chat-luong.md)
6. [Các quyết định kiến trúc](11-quyet-dinh-kien-truc.md)
7. [Cấu trúc repo kỹ thuật](14-cau-truc-repo-ky-thuat.md)
8. [Kiểm chứng công cụ hiện hành](16-kiem-chung-cong-cu-2026-10-05.md)

Không nên bắt đầu bằng RAGFlow, PageIndex hay đồ thị trước khi hiểu mô hình dữ liệu chuẩn.

---

## 17.2. Phạm vi thử nghiệm đầu tiên

Không nhập cả thư viện.

Chọn một tập nhỏ nhưng khó và đại diện:

- tổng cộng khoảng 200–500 trang;
- PDF có chữ tốt;
- PDF có mã hóa lỗi;
- PDF scan;
- trang mờ/lệch;
- tài liệu hai cột;
- chú thích;
- bảng;
- EPUB;
- MOBI nếu có;
- tài liệu tiếng Việt có nhiều dấu;
- một vài ấn bản hoặc bản dịch khác nhau của cùng tác phẩm.

Mục tiêu của tập này là **làm lộ lỗi kiến trúc sớm**, không phải chứng minh quy mô.

---

## 17.3. Việc đầu tiên: tạo kho nguồn bất biến

Tạo nơi lưu nguồn theo nguyên tắc:

```text
nguồn đã nhận
↓
tính SHA-256
↓
gán mã file nguồn
↓
không sửa file
```

Với bản thử nghiệm lưu file cục bộ, có thể dùng cấu trúc:

```text
vault/
└── sources/
    └── sha256/
        └── ab/
            └── abcdef...pdf
```

Nếu dùng kho file/NAS/S3/MinIO thì giữ cùng tư tưởng bằng khóa đối tượng theo SHA-256.

Mỗi file tối thiểu cần biết:

- mã file;
- SHA-256;
- tên gốc;
- loại file;
- thời điểm nhập;
- tác phẩm/ấn bản nếu xác định được;
- trạng thái xử lý.

Không đặt logic tìm kiếm hay véc-tơ vào bước này.

---

## 17.4. Tạo mô hình dữ liệu tối thiểu

Bản 0.1 phải có được đường truy nguồn:

```text
Tác phẩm
→ Ấn bản
→ File nguồn
→ Mục
→ Trang
→ Khối
→ Đoạn tìm kiếm
```

Mỗi đoạn tìm kiếm phải lần ngược được tới:

- file;
- ấn bản;
- trang;
- chương/mục nếu có.

Nếu chưa làm được điều này thì **chưa được xây lớp hỏi đáp cuối**.

---

## 17.5. Xây tuyến nhập tài liệu

Tuyến thử đầu tiên:

```text
file
↓
phân loại định dạng
↓
Docling hoặc bộ đọc phù hợp
↓
kiểm tra từng trang PDF
↓
cần nhận dạng chữ?
├── không → giữ chữ trực tiếp
└── có → PP-OCRv6
           ↓
         chưa đạt / bố cục khó
           ↓
         tuyến dự phòng / PaddleOCR-VL
↓
text_raw + text_clean
↓
cấu trúc chương/mục/trang
```

Với EPUB:

> đọc cấu trúc XHTML/mục lục trực tiếp.

Với MOBI:

> chuẩn hóa sang EPUB/HTML bằng tuyến phù hợp trước khi nhập.

---

## 17.6. Xây bộ kiểm tra chất lượng số hóa trước RAG

Trước khi tìm kiếm, phải đo ít nhất:

- chữ có đúng không;
- dấu tiếng Việt có đúng không;
- thứ tự đọc có đúng không;
- trang có đúng không;
- chương/mục có được giữ không;
- bảng/chú thích có gây đảo thứ tự không.

Những trang sai phải được giữ lại làm **tập kiểm thử hồi quy**.

---

## 17.7. Chia đoạn phục vụ tìm kiếm

Không cắt mù theo số ký tự.

Quy trình:

```text
chương / mục
↓
đoạn văn tự nhiên
↓
điều chỉnh độ dài
↓
thêm ngữ cảnh cấu trúc
```

Mỗi đoạn nên có tiêu đề ngữ cảnh kiểu:

```text
Tên sách
> Phần
> Chương
> Mục
```

và luôn mang mã truy nguồn.

---

## 17.8. Xây hệ tìm kiếm đầu tiên

Sau vòng kiểm chứng công cụ ngày 05/10/2026, cấu hình đầu tiên đáng thử là:

```text
Qdrant
├── tìm theo ý nghĩa
└── tìm theo chữ/thưa (BM25)
      ↓
hợp nhất thứ hạng
      ↓
30–50 ứng viên
      ↓
Qwen3-Reranker-0.6B
      ↓
3–8 đoạn tốt nhất
```

Qwen3-Embedding-0.6B là ứng viên đầu cho biểu diễn ý nghĩa.

BGE-M3 là đường chuẩn so sánh.

Đây là **cấu hình để đo**, không phải cam kết lâu dài.

---

## 17.9. Xây bộ câu hỏi chuẩn trước khi tối ưu

Mục tiêu cuối của giai đoạn thử nghiệm là khoảng 100–300 câu hỏi có đáp án nguồn.

Một bản ghi nên biết:

```text
câu hỏi
nguồn đúng
ấn bản đúng
chương/mục đúng
trang đúng
loại câu hỏi
```

Các nhóm câu hỏi cần có:

- câu nguyên văn;
- tên riêng;
- khái niệm diễn đạt khác nguồn;
- câu cần nhiều đoạn;
- câu có nguồn gần giống nhưng sai;
- câu không có đáp án trong kho.

---

## 17.10. Giao diện tối thiểu của bản 0.1

Không cần xây toàn bộ MCP ngay ngày đầu.

Tối thiểu cần chứng minh được các thao tác:

```text
search_library()
get_book_outline()
search_book()
read_pages()
get_page_image()
```

Sau khi các thao tác này ổn mới mở rộng sang Bộ não thứ hai và nghiên cứu sâu.

---

## 17.11. Tiêu chí hoàn thành bản 0.1

Bản 0.1 chỉ được coi là đạt khi:

- file nguồn được giữ bất biến;
- tài liệu được phân biệt theo tác phẩm và ấn bản;
- mỗi đoạn tìm kiếm truy ngược được về trang;
- PDF có chữ tốt không bị OCR lại vô ích;
- tiếng Việt được kiểm thử thực tế;
- tìm theo chữ và theo ý nghĩa đều hoạt động;
- có bước xếp hạng lại;
- câu trả lời thử nghiệm dẫn đúng nguồn/trang;
- có bộ câu hỏi chuẩn và kết quả đo;
- thay/xóa chỉ mục tìm kiếm không làm mất dữ liệu chuẩn;
- có thể xây lại chỉ mục từ kho dữ liệu chuẩn.

Nếu chưa đạt các điều này thì chưa nên chuyển trọng tâm sang Bộ não thứ hai, PageIndex, đồ thị hay tác tử phức tạp.

---

## 17.12. Những việc cố ý để sau

Bản 0.1 chưa cần:

- Bộ não thứ hai tự cập nhật đầy đủ;
- nhiều tác tử;
- LightRAG;
- Graphiti;
- Cognee;
- Mem0;
- đồ thị toàn thư viện;
- PageIndex làm bộ định tuyến toàn kho;
- giao diện web hoàn chỉnh.

Những thứ này chỉ được thêm sau khi vòng **nguồn → tìm → bằng chứng → trích dẫn → đánh giá** đã chắc.

---

## 17.13. Cấu trúc công việc đề xuất cho tuần đầu

### Ngày 1–2

- dựng khung thư mục tối thiểu theo tài liệu 14;
- chọn tập dữ liệu thử;
- tạo bảng kê file và SHA-256;
- chốt mô hình dữ liệu tối thiểu.

### Ngày 3–4

- nhập PDF/EPUB;
- kiểm tra trang cần OCR;
- lưu văn bản thô/sạch;
- kiểm tra truy trang.

### Ngày 5

- chia đoạn theo cấu trúc;
- dựng chỉ mục tìm kiếm đầu tiên.

### Sau đó

- tạo bộ câu hỏi chuẩn;
- chạy các phương án tìm;
- thêm xếp hạng lại;
- đo trích dẫn;
- sửa lỗi;
- chỉ khi kết quả ổn mới mở rộng phạm vi.

Thời gian ở trên chỉ là **thứ tự công việc gợi ý**, không phải cam kết tiến độ.

---

## 17.14. Nguyên tắc dừng

Nếu một bước không chứng minh được chất lượng bằng dữ liệu thật:

> **không xây thêm lớp phức tạp để che lỗi của lớp bên dưới.**

Ví dụ:

- OCR sai → sửa OCR trước;
- trang sai → sửa truy nguồn trước;
- tìm sai → sửa tìm kiếm trước;
- trích dẫn sai → sửa cửa bằng chứng trước.

Đây là cách giữ dự án đơn giản và kiểm toán được.


---

## 17.15. Các làn đối chứng tuyến đầu

Sau vòng đối chiếu với nghiên cứu thế giới năm 2026, bản 0.1 vẫn giữ **một đường chính đơn giản** để làm mốc, nhưng bổ sung các làn thử nghiệm. Không được đưa tất cả vào sản xuất cùng lúc.

### Làn A — mốc đơn giản mạnh

~~~text
chia đoạn theo cấu trúc
+ BM25
+ Qwen3-Embedding-0.6B
+ hợp nhất thứ hạng
+ Qwen3-Reranker-0.6B
~~~

Đây là mốc chi phí thấp và phải chạy đầu tiên.

### Làn B — trần chất lượng bằng mô hình lớn hơn

So:

- Qwen3-Embedding-0.6B với 4B/8B;
- Qwen3-Reranker-0.6B với 4B/8B.

Mục đích không phải chọn mô hình lớn nhất mà đo **mỗi phần chất lượng tăng thêm tốn bao nhiêu tài nguyên**.

### Làn C — tìm thưa học được

So:

- BM25;
- tín hiệu thưa của BGE-M3;
- SPLADE hoặc mô hình thưa đa ngôn ngữ phù hợp;
- tìm kết hợp chữ + nghĩa;
- nếu đáng giá, hợp nhất ba đường: BM25 + tìm thưa học được + tìm theo ý nghĩa.

### Làn D — đoạn có ngữ cảnh

So:

1. đoạn thông thường;
2. đoạn + tiêu đề sách/chương/mục;
3. đoạn + ngữ cảnh ngắn sinh riêng cho đoạn;
4. chia muộn — cho mô hình nhìn vùng ngữ cảnh rộng trước khi tạo biểu diễn cho từng đoạn.

### Làn E — nhiều véc-tơ / tương tác muộn

Thử một bộ tìm kiểu ColBERT hoặc BGE-M3 nhiều véc-tơ để kiểm tra xem câu hỏi chi tiết có được cải thiện đủ để bù dung lượng và độ phức tạp chỉ mục hay không.

### Làn F — tìm trực tiếp từ ảnh trang

Trên các trang có:

- bảng;
- biểu đồ;
- bố cục nhiều cột;
- chữ nhỏ;
- chú thích;
- nội dung mà OCR làm mất cấu trúc,

thử một bộ tìm thị giác như ColModernVBERT hoặc phương án tương đương.

Tuyến thị giác **đứng song song**, không thay tuyến văn bản.

### Làn G — RAG so với đọc ngữ cảnh dài

Khi đã thu hẹp còn một số sách/chương, so dưới cùng ngân sách:

- RAG theo đoạn;
- DOS-RAG/đọc theo thứ tự tài liệu;
- đưa ngữ cảnh dài trực tiếp;
- PageIndex.

Không mặc định RAG luôn thắng.

### Làn H — nghiên cứu sâu nhiều vòng

Chỉ sau khi các làn tìm kiếm cơ bản ổn:

~~~text
phân rã câu hỏi
↓
tìm bằng chứng
↓
đánh giá đã đủ chưa
├── đủ → tổng hợp
└── chưa
    ↓
    ghi rõ khoảng trống
    ↓
    tạo truy vấn tiếp
    ↓
    tìm lại
~~~

Mỗi vòng phải lưu truy vấn, ứng viên, bằng chứng được chọn và lý do dừng.

---

## 17.16. Đánh giá riêng cho tiếng Việt

Không chốt mô hình chỉ từ bảng xếp hạng tiếng Anh hoặc đa ngôn ngữ chung.

Ít nhất phải đối chiếu:

- **VN-MTEB** — tập đánh giá biểu diễn tiếng Việt;
- **ViRE** — nghiên cứu truy hồi tiếng Việt nhiều miền;
- bộ câu hỏi riêng từ chính kho sách của dự án.

Mục tiêu là tìm mô hình **ổn định trên tiếng Việt và sách thật**, không tìm mô hình có tên lớn nhất.

---

## 17.17. Thứ tự để tránh nổ phạm vi

Các làn trên là **bộ thí nghiệm**, không phải danh sách công nghệ phải xây.

Thứ tự:

1. làm Làn A chạy đúng;
2. khóa bộ dữ liệu và bộ câu hỏi;
3. chạy B/C/D/F/G như đối chứng;
4. chỉ giữ phương án tạo cải thiện có ý nghĩa;
5. sau đó mới thử adaptive-k — chọn số đoạn động;
6. sau đó mới thử Làn H — tìm nhiều vòng theo khoảng trống bằng chứng.

Nếu một phương pháp mới không thắng về chất lượng hoặc không đáng với chi phí/độ phức tạp:

> **loại khỏi đường chính dù nó là công nghệ mới hơn.**

Xem toàn bộ lập luận tại [Đối chiếu Thư Viện Sống với tuyến đầu thế giới năm 2026](20-doi-chieu-voi-tuyen-dau-the-gioi-2026.md).
