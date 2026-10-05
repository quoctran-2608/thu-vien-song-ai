# THƯ VIỆN SỐNG AI

## Kiến trúc tổng thể: thư viện số + hệ tìm bằng chứng + Bộ não thứ hai + không gian nghiên cứu

**Phiên bản tài liệu: 1.0**

> Nếu chỉ đọc một tài liệu để hiểu toàn bộ dự án, hãy đọc tài liệu này.

---

# 1. Mục tiêu thật sự của dự án

Mục tiêu của dự án không phải chỉ là xây một phần mềm hỏi đáp trên PDF.

Nó cũng không phải chỉ là tạo một kho ghi chú Markdown, một wiki tự động, một cơ sở dữ liệu véc-tơ hay một chatbot đọc sách.

Mục tiêu lớn hơn là xây:

> **một nền tảng tri thức lâu dài, trong đó tài liệu gốc được bảo tồn, AI có thể tìm đúng bằng chứng, đọc sâu khi cần, tổng hợp nhiều nguồn, tích lũy hiểu biết qua thời gian và luôn quay lại được nguồn để kiểm chứng.**

Nói ngắn gọn hơn:

> **Thư Viện Sống AI phải vừa là thư viện, vừa là hệ thống nghiên cứu, vừa là trí nhớ lâu dài cho AI.**

Dữ liệu thật phải thuộc về hệ thống của mình. Các phần mềm như RAGFlow, QMD, PageIndex, Qdrant hay bất kỳ mô hình AI nào chỉ là các bộ máy có thể thay thế.

---

# 2. Bài toán cần giải quyết

Một kho sách lớn có thể chứa đồng thời:

- PDF có lớp chữ tốt;
- PDF có chữ nhưng mã hóa lỗi;
- PDF chỉ là ảnh quét;
- PDF vừa có chữ vừa có ảnh;
- EPUB;
- MOBI;
- nhiều ấn bản của cùng một tác phẩm;
- nhiều bản dịch;
- tài liệu nhiều ngôn ngữ;
- trang cũ, mờ, cong, lệch;
- văn bản hai cột;
- sách có nhiều chú thích;
- bảng biểu và hình ảnh;
- bài nghiên cứu;
- ghi chú;
- kết quả nghiên cứu cũ.

Nếu làm theo cách đơn giản:

```text
lấy chữ
→ cắt thành các đoạn bằng nhau
→ biến thành véc-tơ
→ tìm vài đoạn gần nhất
→ đưa hết cho AI
```

thì hệ thống sớm gặp các vấn đề:

- mất cấu trúc sách;
- không phân biệt tác phẩm và ấn bản;
- khó truy đúng trang;
- dễ lấy một đoạn “na ná” nhưng không thật sự chứng minh điều cần nói;
- đưa quá nhiều chữ cho AI;
- AI phải đọc lại những thứ đã nghiên cứu;
- bản tóm tắt ngày càng tách khỏi nguồn;
- thay một phần mềm có thể kéo theo việc xây lại toàn bộ kho.

Vì vậy dự án phải được thiết kế theo hướng: **nguồn bền vững, dữ liệu chuẩn, tìm kiếm có kiểm chứng, trí nhớ tích lũy và công cụ thay thế được**.

---

# 3. Kiến trúc bốn lớp

```text
1. KHO NGUỒN GỐC
PDF / EPUB / MOBI / ảnh / tài liệu

        ↓

2. KHO DỮ LIỆU CHUẨN
+
HỆ TÌM BẰNG CHỨNG

        ↓

3. BỘ NÃO THỨ HAI
tri thức đã được đọc, tổng hợp và liên kết

        ↓

4. KHÔNG GIAN NGHIÊN CỨU
bộ nhớ nhỏ cho vấn đề đang xử lý

        ↓

AI
```

Có thể nhớ bằng bốn câu:

> **Nguồn gốc giữ sự thật.**

> **Hệ tìm kiếm tìm đúng thứ cần đọc.**

> **Bộ não thứ hai giữ những gì đã hiểu.**

> **Không gian nghiên cứu chỉ giữ những gì cần cho câu hỏi hiện tại.**

---

# 4. Hiến pháp của hệ thống

## 4.1. AI không phải là nguồn

AI có thể:

- tìm;
- đọc;
- dịch;
- so sánh;
- tóm tắt;
- suy luận;
- phát hiện mâu thuẫn;
- đặt giả thuyết.

Nhưng AI không được tự biến kiến thức có sẵn trong mô hình thành bằng chứng.

Căn cứ của một kết luận phải đến từ tài liệu hoặc nguồn được xác định.

---

## 4.2. Nguồn gốc phải được bảo tồn

AI không sửa trực tiếp:

- PDF;
- EPUB;
- MOBI;
- ảnh trang;
- văn bản thô lấy từ tài liệu.

Nếu cần làm sạch văn bản, phải giữ cả:

```text
văn bản thô
+
văn bản đã làm sạch
```

Không ghi đè dữ liệu thô.

---

## 4.3. Kho dữ liệu chuẩn phải sống lâu hơn mọi công cụ

RAGFlow có thể thay.

Qdrant có thể thay.

QMD có thể thay.

PageIndex có thể thay.

Mô hình AI có thể thay.

Nhưng:

> **tác phẩm, ấn bản, chương, mục, trang, đoạn nguồn, lịch sử truy nguồn và Bộ não thứ hai phải còn nguyên.**

Đây là tiêu chuẩn kiến trúc quan trọng nhất.

---

## 4.4. Mọi khẳng định quan trọng phải truy ngược được về nguồn

Một kết luận quan trọng không nên kết thúc ở:

> “AI nói”.

Nó phải có thể lần ngược:

```text
khẳng định
↓
bằng chứng
↓
đoạn văn
↓
trang
↓
chương / mục
↓
ấn bản
↓
file nguồn
```

---

## 4.5. Một kết quả tìm được chưa phải là bằng chứng

Hệ tìm kiếm trả về một đoạn chỉ có nghĩa:

> “đoạn này đáng xem”.

Nó chưa có nghĩa:

> “đoạn này chứng minh được kết luận”.

Do đó phải phân biệt:

```text
kết quả tìm được
↓
ứng viên bằng chứng
↓
kiểm tra
↓
bằng chứng đã xác minh
```

---

## 4.6. Một trích dẫn có thật chưa chắc chứng minh được khẳng định

Một lỗi nguy hiểm là:

- tài liệu có thật;
- số trang có thật;
- đoạn trích có thật;

nhưng đoạn đó không thực sự hỗ trợ điều AI đang nói.

Vì vậy hệ thống nghiên cứu sâu phải kiểm tra:

> **“đoạn này có thực sự hỗ trợ khẳng định không?”**

---

## 4.7. “Chưa đủ bằng chứng” là một câu trả lời hợp lệ

AI không được ép tất cả câu hỏi thành kết luận chắc chắn.

Các câu trả lời hợp lệ có thể là:

- chưa đủ bằng chứng trong phạm vi tài liệu đã tìm;
- các nguồn hiện có mâu thuẫn nhau;
- chưa thể kết luận;
- không tìm thấy trong kho nguồn đã khảo sát.

---

## 4.8. Không để phần mềm bên ngoài sở hữu dữ liệu

Tiêu chuẩn dễ kiểm tra:

> Nếu xóa hoàn toàn RAGFlow rồi cài lại, kho dữ liệu chuẩn vẫn còn.

> Nếu bỏ QMD, toàn bộ Markdown của Bộ não thứ hai vẫn còn.

> Nếu không dùng PageIndex nữa, cấu trúc chương/mục/trang vẫn còn.

---

## 4.9. Nhiều AI có thể nghiên cứu, nhưng chỉ một nơi được ghi chính thức

Nhiều tác tử AI có thể cùng:

- tìm;
- đọc;
- phân tích;
- đề xuất.

Nhưng không được cùng sửa trực tiếp một trang tri thức.

Quy trình:

```text
nhiều AI
↓
đề xuất thay đổi
↓
kiểm tra
↓
một bộ ghi duy nhất
↓
ghi chính thức
```

---

## 4.10. Mọi thay đổi lớn phải phục hồi được

Nếu một lần cập nhật cần sửa ba file, không được để trạng thái mới sửa xong một file rồi gặp lỗi.

Phải:

> **ghi thành công toàn bộ hoặc không ghi gì cả.**

Sau đó lưu lịch sử bằng Git.

---

## 4.11. Công cụ mới phải qua kiểm thử

Không thay công cụ chỉ vì:

- phiên bản mới hơn;
- số sao nhiều hơn;
- quảng cáo tốt hơn;
- bảng xếp hạng chung tốt hơn.

Phải kiểm thử trên chính dữ liệu của thư viện.

---

## 4.12. Mục tiêu không phải “AI không bao giờ sai”

Không có kiến trúc nào loại bỏ hoàn toàn sai sót.

Mục tiêu đúng là:

> **làm cho sai sót khó lọt qua kiểm tra hơn, dễ phát hiện hơn, truy ra được và sửa được.**

---

# 5. Lớp 1 — Kho nguồn gốc

Đây là nơi chứa:

- PDF;
- EPUB;
- MOBI;
- ảnh trang;
- bài báo;
- tài liệu nghiên cứu;
- bản dịch;
- tài liệu tham khảo;
- dữ liệu khác.

Kho nguồn gốc trả lời:

> **Tài liệu thật sự là gì?**

Nó không trả lời:

> “AI hiểu gì về tài liệu?”

Mỗi file cần có dấu vân tay số, thí dụ SHA-256, để nhận biết chính xác phiên bản file.

---

# 6. Lớp 2 — Kho dữ liệu chuẩn và hệ tìm bằng chứng

Đây là lớp biến tài liệu thành dạng máy có thể xử lý ổn định.

```text
Tác phẩm
↓
Ấn bản
↓
Nguồn file
↓
Chương / mục
↓
Trang
↓
Khối nội dung
↓
Đoạn phục vụ tìm kiếm
```

Lớp này trả lời:

- thông tin nằm ở đâu;
- trang nào;
- ấn bản nào;
- đoạn nào có liên quan;
- nguồn nào đã được xử lý bằng cách nào.

---

# 7. Lớp 3 — Bộ não thứ hai

Đây là tri thức đã được tiêu hóa.

Ví dụ:

```text
Khái niệm/
Nhân vật/
Tác phẩm/
Truyền thống/
So sánh/
Tranh luận/
Mốc thời gian/
Tổng hợp/
Câu hỏi mở/
```

Bộ não thứ hai trả lời:

> “Ta đã hiểu gì về vấn đề này?”

Nó không thay thế nguồn gốc.

---

# 8. Lớp 4 — Không gian nghiên cứu

Đây là bàn làm việc tạm thời cho một vấn đề.

Ví dụ:

```text
research/
└── giac-ngo/
    ├── cau-hoi.md
    ├── pham-vi.md
    ├── tai-lieu-ung-vien.json
    ├── bang-chung/
    ├── ghi-chu/
    ├── mau-thuan.md
    ├── tong-hop.md
    └── truy-nguon.json
```

Khi nghiên cứu xong:

- phần tạm có thể lưu lại;
- kết quả tốt được đề xuất đưa vào Bộ não thứ hai;
- kết luận chưa chắc chắn không tự động trở thành tri thức chính thức.

---

# 9. Số hóa PDF đúng cách

## 9.1. Không nhận dạng chữ từ ảnh toàn bộ PDF

Đối với từng trang:

```text
kiểm tra trang
↓
có lớp chữ tốt?
├── có → lấy chữ trực tiếp
└── không → nhận dạng chữ từ ảnh
```

Có thể kiểm tra:

- có lớp chữ hay không;
- lượng ký tự;
- Unicode có hợp lệ không;
- chữ có bị rác không;
- thứ tự đọc có hợp lý không.

Một cuốn 500 trang có thể chỉ cần nhận dạng chữ từ ảnh ở một phần nhỏ.

---

## 9.2. Trang dễ và trang khó không nên xử lý giống nhau

Có thể dùng nhiều tầng:

```text
trang cần nhận dạng chữ
↓
công cụ nhận dạng thông thường
↓
đủ tốt?
├── có → dùng kết quả
└── không
     ↓
công cụ hiểu bố cục mạnh hơn
```

Tên công cụ cụ thể có thể thay đổi; nguyên tắc nhiều tầng mới là phần cần giữ lâu dài.

---

# 10. EPUB và MOBI

## EPUB

EPUB thường đã có:

- XHTML;
- mục lục;
- tiêu đề;
- chương;
- thông tin sách.

Không nên biến EPUB thành ảnh rồi nhận dạng chữ.

## MOBI

Có thể chuẩn hóa bằng Calibre:

```text
MOBI
↓
EPUB hoặc HTML
↓
đọc cấu trúc
```

---

# 11. Bảo tồn văn bản thô và văn bản sạch

Mỗi đoạn quan trọng nên giữ:

```text
text_raw
= chữ lấy trực tiếp từ nguồn hoặc nhận dạng chữ

text_clean
= chữ đã chuẩn hóa
```

Kèm theo:

- phương pháp lấy chữ;
- công cụ đã dùng;
- mức tin cậy;
- trang;
- vị trí trên trang nếu có;
- ảnh trang nếu cần.

---

# 12. Chống trùng và bảo tồn ấn bản

## Trùng tuyệt đối

Dùng SHA-256.

## Gần trùng

Có thể dùng các dấu vân tay nội dung như MinHash hoặc SimHash.

## Không đánh mất ấn bản

Cùng một tác phẩm có thể có:

- nhiều lần xuất bản;
- nhiều bản dịch;
- nhiều bản scan;
- nhiều định dạng.

Không được vì phát hiện gần trùng mà gộp mất thông tin lịch sử.

---

# 13. Hai cách nhìn kho dữ liệu chuẩn

## 13.1. Cách nhìn theo thực thể

```text
Tác phẩm
↓
Ấn bản
↓
Nguồn file
↓
Chương / mục
↓
Trang
↓
Khối
↓
Đoạn tìm kiếm
```

## 13.2. Cách nhìn theo tầng dữ liệu

### Tầng 0 — Danh mục

Tên sách, tác giả, dịch giả, nhà xuất bản, năm, ngôn ngữ, chủ đề.

### Tầng 1 — Cấu trúc

Mục lục, phần, chương, mục, số trang.

### Tầng 2 — Tìm kiếm

Các đoạn văn đã được chuẩn bị để tìm.

### Tầng 3 — Nguồn

File gốc, văn bản thô, văn bản sạch, ảnh trang, vị trí chữ, độ tin cậy.

Hai cách nhìn bổ sung cho nhau.

---

# 14. Chia đoạn theo cấu trúc

Không nên:

```text
cứ 1.000 ký tự
→ cắt
```

Nên ưu tiên:

```text
tiêu đề
↓
mục
↓
đoạn
↓
ranh giới tự nhiên của nội dung
```

Một đoạn tìm kiếm nên luôn biết mình thuộc:

```text
Tên sách
> Phần
> Chương
> Mục
```

---

# 15. RAG — cơ chế tìm trước khi AI trả lời

RAG là viết tắt của *Retrieval-Augmented Generation*.

Trong dự án này có thể hiểu:

> **tìm phần tài liệu thích hợp trước, rồi mới cho AI đọc và trả lời.**

RAG không đồng nghĩa với “cơ sở dữ liệu véc-tơ”.

---

# 16. Tìm theo chữ + tìm theo ý nghĩa + xếp hạng lại

## Tìm theo chữ

Mạnh với:

- tên người;
- tên sách;
- câu nguyên văn;
- thuật ngữ;
- mã tài liệu;
- cụm từ hiếm.

## Tìm theo ý nghĩa

Giúp tìm các đoạn nói cùng ý nhưng dùng từ khác.

## Kết hợp

```text
TÌM THEO CHỮ
        │
        ├─────────┐
                  ↓
              TRỘN KẾT QUẢ
                  ↓
             XẾP HẠNG LẠI
                  ↓
              VÀI ĐOẠN TỐT
                  ↑
        ┌─────────┘
        │
TÌM THEO Ý NGHĨA
```

Bộ xếp hạng lại đọc câu hỏi và một danh sách nhỏ các kết quả ứng viên để sắp lại chính xác hơn.

---

# 17. Một kết quả tìm được phải qua cửa kiểm tra bằng chứng

Không nên:

```text
tìm được
↓
đưa thẳng cho AI
```

Nên:

```text
kết quả tìm được
↓
ứng viên
↓
kiểm tra:
- đúng nguồn?
- đúng vị trí?
- đủ ngữ cảnh?
- thật sự liên quan?
↓
bằng chứng
```

Ở chế độ hỏi đáp thường, bước kiểm tra có thể nhẹ.

Ở chế độ nghiên cứu nghiêm ngặt, bước này phải chặt.

---

# 18. Tóm tắt phân tầng

Mỗi tài liệu có thể có:

```text
SÁCH
↓
CHƯƠNG
↓
MỤC
↓
ĐOẠN GỐC
```

Câu hỏi tổng quát đi từ trên xuống.

Câu hỏi cần nguyên văn có thể đi thẳng tới tầng bằng chứng.

---

# 19. Đọc theo độ sâu thích ứng

Không phải câu hỏi nào cũng cần cùng lượng dữ liệu.

## Câu đơn giản

```text
câu hỏi
↓
2–3 trang Bộ não thứ hai
↓
trả lời
```

## Cần nguồn

```text
Bộ não thứ hai
+
2–5 đoạn bằng chứng
```

## Cần đọc một cuốn

```text
mục lục
↓
chọn chương
↓
chọn mục
↓
đọc đoạn
```

## Cần kiểm tra nguyên văn

```text
trang nguồn
↓
ảnh trang nếu cần
```

## Cần nghiên cứu lớn

```text
nhiều sách
↓
không gian nghiên cứu
```

Nguyên tắc:

> **AI chỉ đọc sâu đến mức nhiệm vụ thật sự cần.**

---

# 20. PageIndex nên đứng ở đâu?

PageIndex là một cách tổ chức tài liệu theo cây để đi từ:

```text
sách
↓
chương
↓
mục
↓
đoạn
```

Vị trí hợp lý:

```text
toàn thư viện
↓
hệ tìm kiếm chọn vài cuốn
↓
PageIndex
↓
đọc sâu bên trong các cuốn đó
```

Không nên mặc định dùng nó làm lớp tìm kiếm toàn thư viện.

---

# 21. Hai chỉ mục phải tách nhau

Không nên trộn:

```text
hàng triệu đoạn sách
+
các trang tri thức đã tổng hợp
```

vào một chỉ mục duy nhất.

Nên có:

```text
CHỈ MỤC KHO SÁCH
= bằng chứng

CHỈ MỤC BỘ NÃO THỨ HAI
= hiểu biết đã tiêu hóa
```

Khi hỏi:

> Ta đã hiểu gì về X?

ưu tiên Bộ não thứ hai.

Khi hỏi:

> Điều này lấy từ đâu?

ưu tiên kho sách.

---

# 22. Gói bằng chứng

Một trong những phần quan trọng nhất là **gói bằng chứng**.

Đây là gói nhỏ mà AI cuối cùng đọc.

Có thể gồm:

```text
Câu hỏi

Phạm vi nghiên cứu

Một ít thông tin từ Bộ não thứ hai

Bằng chứng 1
- đoạn
- sách
- chương
- trang

Bằng chứng 2
...

Bằng chứng phản bác nếu có

Điểm chưa chắc chắn
```

Gói bằng chứng không chỉ để tiết kiệm chi phí. Nó còn là **đơn vị trung gian giữa hệ tìm kiếm và AI suy luận**.

---

# 23. Vì sao gói bằng chứng tiết kiệm chi phí?

Cách ngây thơ có thể lấy:

```text
30 đoạn × 800 đơn vị chữ
```

rồi đưa tất cả cho AI.

Phương án tốt hơn có thể chỉ cần:

```text
4–8 đoạn tốt nhất
+
một ít tri thức tổng hợp
```

Con số chỉ mang tính minh họa, không phải tỷ lệ tiết kiệm cố định.

Điểm quan trọng:

> **chi phí lớn thường nằm ở việc để mô hình lớn đọc quá nhiều thứ không cần thiết ở mỗi câu hỏi.**

---

# 24. Bộ não thứ hai là gì?

Bộ não thứ hai không phải thư mục chứa bản tóm tắt từng cuốn.

Nó phải tổ chức theo tri thức:

```text
Khái niệm/
Nhân vật/
Tác phẩm/
Truyền thống/
So sánh/
Tranh luận/
Mốc thời gian/
Tổng hợp/
Câu hỏi mở/
```

Một trang như:

```text
Vô-ngã.md
```

có thể tổng hợp từ nhiều sách và nhiều cuộc nghiên cứu.

---

# 25. Bộ não thứ hai không thay thế sách gốc

Nếu hệ thống liên tục tóm tắt bản tóm tắt, sai lệch có thể tăng dần.

Do đó:

> **Bộ não thứ hai là điều AI đã hiểu.**

> **Kho nguồn là nơi kiểm tra điều đó có đúng hay không.**

---

# 26. RAG có độ phủ rộng, Bộ não thứ hai có độ sâu tích lũy

Giả sử thư viện có 100.000 sách.

Không nên cho AI đọc sâu cả 100.000 sách ngay khi nhập.

Thay vào đó:

```text
100.000 sách
↓
đều được số hóa và lập chỉ mục

nhưng

Bộ não thứ hai
↓
chỉ phát triển sâu ở những chủ đề thực sự được sử dụng
```

Chủ đề dùng nhiều ngày càng được tổng hợp sâu.

Chủ đề chưa dùng vẫn nằm trong thư viện để tìm khi cần.

---

# 27. Cấu trúc một trang tri thức

Một trang quan trọng nên phân biệt:

```text
THÔNG TIN TỪ NGUỒN

TỔNG HỢP CỦA AI

ĐIỂM MÂU THUẪN

ĐIỂM CHƯA CHẮC CHẮN

CÂU HỎI CẦN NGHIÊN CỨU THÊM

NGUỒN
```

---

# 28. Sổ khẳng định

Markdown dễ đọc cho con người là chưa đủ.

Những kết luận quan trọng nên có bản ghi có cấu trúc.

Ví dụ:

```text
Mã:
C1258

Nội dung:
"Tác giả A giải thích X theo nghĩa Y."

Nguồn:
book_183

Trang:
126–128
```

---

# 29. Khẳng định cần hai chiều trạng thái

## 29.1. Nó được tạo bằng cách nào?

### TRÍCH XUẤT

Nguồn nói trực tiếp.

### SUY LUẬN

AI rút ra từ bằng chứng.

### TỔNG HỢP

AI kết hợp nhiều nguồn.

## 29.2. Bằng chứng hỗ trợ đến đâu?

### ĐƯỢC HỖ TRỢ

Bằng chứng đủ mạnh.

### CÓ TRANH LUẬN

Có nguồn quan trọng bất đồng.

### HỖ TRỢ YẾU

Có liên quan nhưng chưa đủ chắc.

### CHƯA ĐỦ DỮ LIỆU

Không đủ để kết luận.

### CHƯA BIẾT

Hiện chưa xác định được.

### BỊ PHẢN BÁC

Có bằng chứng mạnh chống lại.

Hai chiều này không nên trộn thành một.

---

# 30. Phải tách nguyên văn, bản dịch và suy luận

Ít nhất nên phân biệt:

```text
1. Nguyên văn nguồn
2. Bản dịch xuất bản
3. Bản dịch làm việc do AI tạo
4. Diễn đạt lại
5. Diễn giải của tác giả/học giả
6. Tổng hợp của AI
```

Không được để người đọc hiểu nhầm bản dịch AI là bản dịch xuất bản.

---

# 31. Không gian nghiên cứu

Đối với câu hỏi khó, AI không nên vừa nghiên cứu vừa sửa Bộ não thứ hai.

Quy trình:

```text
nghiên cứu
↓
bằng chứng
↓
tổng hợp
↓
kiểm chứng
↓
đề xuất
↓
Bộ não thứ hai
```

---

# 32. Tìm bằng chứng phản bác

Trong nghiên cứu sâu, hệ thống không chỉ tìm thứ ủng hộ kết luận.

Sau khi có kết luận sơ bộ:

```text
kết luận sơ bộ
↓
tạo truy vấn tìm phản bác
↓
tìm bằng chứng trái chiều
```

Nếu tìm thấy:

- sửa khẳng định;
- thu hẹp phạm vi;
- giảm mức chắc chắn;
- hoặc ghi rõ mâu thuẫn.

Đặc biệt cần chú ý các kết luận dùng từ:

- tất cả;
- luôn luôn;
- duy nhất;
- không có;
- sớm nhất;
- chưa từng.

---

# 33. “Không tìm thấy” không đồng nghĩa “không tồn tại”

Nếu tìm trong một kho tài liệu mà không thấy X, không nên kết luận:

> “Không có bằng chứng nào cho X.”

Nên nói:

> **“Không tìm thấy bằng chứng cho X trong phạm vi tài liệu đã khảo sát.”**

Kết quả âm nên ghi:

```text
đã tìm kho nào
phiên bản nào
ngôn ngữ nào
dùng cách tìm nào
ngày nào
phạm vi có hạn chế gì
```

---

# 34. Nhiều nguồn đồng ý chưa chắc là nhiều bằng chứng độc lập

Ba cuốn sách có thể nói cùng một điều vì đều dựa trên một nguồn chung.

Trong nghiên cứu sâu có thể cần theo dõi:

- chuỗi trích dẫn;
- quan hệ bản dịch;
- họ bản thảo;
- nguồn chung;
- phụ thuộc văn bản.

Không cần xây toàn bộ ngay ở bản đầu, nhưng mô hình dữ liệu không nên chặn khả năng này.

---

# 35. Kiểm tra câu trích

Với nghiên cứu cần độ chính xác cao:

```text
câu trích có tồn tại?
↓
nằm đúng vị trí?
↓
đúng tài liệu?
↓
đúng phiên bản?
```

Nếu AI diễn đạt lại, phải ghi rõ đó là diễn đạt lại.

---

# 36. Kiểm tra khẳng định với bằng chứng

Một khẳng định có thể được đánh giá:

```text
TRỰC TIẾP
= nguồn nói gần như chính xác điều đó

MẠNH
= cách diễn đạt lại hợp lý

YẾU
= có liên quan nhưng cần thêm giả định

KHÔNG ĐỦ
= nguồn chưa chứng minh được

MÂU THUẪN
= có bằng chứng chống lại
```

Ở chế độ nghiêm ngặt:

- TRỰC TIẾP: được dùng;
- MẠNH: được dùng;
- YẾU: phải ghi giới hạn;
- KHÔNG ĐỦ: không được biến thành kết luận chắc chắn;
- MÂU THUẪN: phải trình bày như một điểm tranh luận.

---

# 37. Hồ sơ của mỗi lần nghiên cứu

Một nghiên cứu sâu nên có mã riêng.

Lưu:

```text
mã lần nghiên cứu
câu hỏi
ngày chạy

phiên bản kho dữ liệu
phiên bản phần mềm
phiên bản cấu hình

cách tìm
tham số tìm

bằng chứng đã dùng
khẳng định được chấp nhận
khẳng định bị loại

mô hình AI
phiên bản hướng dẫn

kết quả cuối
```

Nhờ đó có thể trả lời:

> “Tại sao hệ thống từng đưa ra kết luận này?”

---

# 38. Cập nhật Bộ não thứ hai theo phần thay đổi

Giả sử hôm qua có 10.000 sách, hôm nay thêm 3 sách.

Không được đọc lại 10.003 sách.

Cần một **bảng kê xử lý** — trong tài liệu kỹ thuật thường gọi là `manifest`.

Nó lưu:

- file nào đã biết;
- dấu vân tay số;
- phiên bản xử lý;
- kết quả đã sinh ra;
- phần nào có thể bị ảnh hưởng.

Luồng:

```text
file mới
↓
tính dấu vân tay
↓
đã xử lý?
├── có → bỏ qua
└── chưa
     ↓
    xử lý
     ↓
    tìm trang tri thức có thể bị ảnh hưởng
     ↓
    chỉ xem xét cập nhật các trang đó
```

---

# 39. Bộ não thứ hai có thể tự bảo trì nhưng không được tự bịa

Hệ thống có thể định kỳ tìm:

- liên kết chết;
- trang không có liên kết;
- hai trang trùng;
- khẳng định thiếu nguồn;
- mâu thuẫn;
- trang quá dài;
- trang quá nhỏ;
- chủ đề xuất hiện nhiều nhưng chưa có trang riêng.

Khi thấy nguồn A nói X và nguồn B nói ngược lại, không được tự động xóa một bên.

Phải giữ cả hai và đánh dấu tình trạng chưa giải quyết nếu chưa đủ căn cứ.

---

# 40. Vai trò của các công cụ bên ngoài

Thông tin tính năng hiện hành phải được kiểm chứng lại trước khi chốt triển khai. Về mặt kiến trúc, vai trò dự kiến như sau.

## Docling

Máy đọc và chuẩn hóa tài liệu có cấu trúc.

## PaddleOCR

Nhận dạng chữ cho trang ảnh.

## RAGFlow

Bộ máy RAG mạnh có thể kết nối qua giao diện riêng.

Không dùng làm nguồn dữ liệu duy nhất.

## Qdrant

Kho chuyên tìm các biểu diễn số của đoạn văn.

## QMD

Tìm trong các trang Markdown của Bộ não thứ hai.

## PageIndex

Đọc sâu tài liệu dài theo cây chương/mục.

## LightRAG

Quan hệ tri thức xuyên tài liệu khi thật sự cần đồ thị.

## Graphiti

Theo dõi thông tin và quan hệ thay đổi theo thời gian.

## Cognee

Nguồn tham khảo về trí nhớ lâu dài cho tác tử AI.

## Obsidian

Giao diện con người thuận tiện cho Markdown, không phải nơi sở hữu dữ liệu.

---

# 41. AI chỉ nên thấy một bộ công cụ nhỏ

Giao diện cấp cao có thể gồm:

```text
search_library()
= tìm trong thư viện

get_book_outline()
= lấy mục lục/cấu trúc sách

search_book()
= tìm trong một cuốn

read_section()
= đọc một mục

read_pages()
= đọc một số trang

get_page_image()
= xem ảnh trang gốc

search_brain()
= tìm trong Bộ não thứ hai

read_brain_page()
= đọc trang tri thức

research()
= mở nghiên cứu sâu
```

AI không cần biết phía sau là Qdrant, QMD, RAGFlow, PageIndex hay công cụ khác.

---

# 42. MCP là gì?

MCP là tên một chuẩn giao tiếp giúp AI gọi công cụ và dữ liệu bên ngoài theo cách thống nhất.

```text
AI
↓
MCP của Thư Viện Sống
↓
lệnh cấp cao
↓
bộ chuyển tiếp
↓
công cụ thật
```

Nhờ vậy thay công cụ phía sau không nhất thiết làm thay đổi cách AI sử dụng thư viện.

---

# 43. Luồng hỏi đáp tổng thể

```text
CÂU HỎI
   ↓
BỘ CHỌN CÁCH XỬ LÝ
   │
   ├───────────────┬────────────────┐
   ↓               ↓                ↓
tìm chính xác   hỏi tổng hợp     đọc sách dài
   ↓               ↓                ↓
RAG          Bộ não thứ hai      PageIndex
   │               │                │
   └───────────────┴────────────────┘
                   ↓
             GÓI BẰNG CHỨNG
                   ↓
                AI ĐỌC
                   ↓
              KIỂM CHỨNG
                   ↓
                TRẢ LỜI
                   ↓
       có tri thức đáng lưu?
             ┌─────┴─────┐
             ↓           ↓
           không        có
             ↓           ↓
            xong      đề xuất
                         ↓
                     kiểm tra
                         ↓
                Bộ não thứ hai
```

---

# 44. Vòng đời tri thức

```text
ĐỌC
↓
TÌM
↓
HIỂU
↓
NGHIÊN CỨU
↓
KIỂM CHỨNG
↓
GHI NHỚ
↓
LẦN SAU ĐỌC TỐT HƠN
```

Đây là điểm khiến dự án khác một ứng dụng RAG thông thường.

---

# 45. Chế độ nghiên cứu nghiêm ngặt

Không phải câu hỏi nào cũng cần quy trình nặng.

Chế độ này dùng khi:

- nghiên cứu học thuật;
- viết sách;
- nghiên cứu lịch sử;
- đối chiếu nhiều nguồn;
- cần trích dẫn chính xác;
- kết luận có rủi ro cao.

Luồng:

```text
xác định phạm vi nguồn
↓
tìm
↓
kiểm tra câu trích
↓
kiểm tra khẳng định
↓
tìm bằng chứng phản bác
↓
ghi hồ sơ nghiên cứu
↓
kết luận có giới hạn
```

---

# 46. Chế độ kho nguồn đóng

Có thể yêu cầu:

> chỉ dùng những tài liệu nằm trong kho đã chỉ định.

Khi đó:

- không dùng kiến thức có sẵn của AI làm bằng chứng;
- không âm thầm tìm web;
- không bổ sung nguồn ngoài;
- nếu thiếu thì trả:

> **Chưa đủ dữ liệu trong phạm vi kho nguồn được phép.**

---

# 47. Kiểm thử chất lượng

## 47.1. Kiểm thử số hóa

Đo:

- lỗi ký tự;
- lỗi dấu tiếng Việt;
- thứ tự đọc;
- tiêu đề;
- chú thích;
- số trang;
- bảng;
- trang nhiều cột.

Nên dùng vài trăm trang đại diện cho nhiều kiểu khó.

## 47.2. Kiểm thử tìm kiếm

Tạo bộ câu hỏi chuẩn.

Mỗi câu biết trước sách/chương/trang đúng.

So sánh:

- chỉ tìm theo chữ;
- chỉ tìm theo ý nghĩa;
- tìm kết hợp;
- thêm xếp hạng lại;
- thêm phân tầng.

## 47.3. Kiểm thử trích dẫn

Kiểm tra:

- đúng sách;
- đúng ấn bản;
- đúng trang;
- đúng đoạn;
- đoạn có thật sự hỗ trợ câu trả lời.

## 47.4. Kiểm thử Bộ não thứ hai

Tìm:

- khẳng định thiếu nguồn;
- suy luận bị trình bày như sự kiện;
- trang trùng;
- mâu thuẫn;
- liên kết hỏng;
- thông tin cũ.

---

# 48. Bộ kiểm thử cố định

Mỗi khi thay:

- cách đọc PDF;
- công cụ nhận dạng chữ;
- cách chia đoạn;
- mô hình biểu diễn ý nghĩa;
- bộ xếp hạng lại;
- RAGFlow;
- QMD;
- PageIndex;

phải chạy lại cùng một bộ câu hỏi chuẩn.

Nếu chất lượng giảm, không triển khai chỉ vì công cụ mới hơn.

---

# 49. Những gì không nên làm ở phiên bản đầu

Không nên:

- nhận dạng chữ toàn bộ PDF;
- xây đồ thị toàn kho;
- huấn luyện lại AI bằng cả thư viện;
- dựng kiến trúc quá nhiều máy khi chưa cần;
- cho AI tự chạy vòng nghiên cứu không giới hạn;
- dùng duy nhất tìm kiếm véc-tơ;
- đưa quá nhiều đoạn cho mô hình lớn;
- cho AI tự sửa trực tiếp Bộ não thứ hai;
- xây Bộ não thứ hai của toàn bộ thư viện trước khi biết chủ đề nào thực sự cần.

---

# 50. Phần nào nên dùng lại, phần nào phải tự kiểm soát?

## Không nên tự viết lại từ đầu

- máy đọc PDF;
- công cụ nhận dạng chữ;
- cơ sở dữ liệu véc-tơ;
- mô hình biểu diễn ý nghĩa;
- mô hình xếp hạng lại;
- PageIndex;
- QMD;
- công cụ đồ thị.

## Phải thuộc quyền kiểm soát của Thư Viện Sống

- mô hình dữ liệu chuẩn;
- truy nguồn;
- mã tài liệu và mã đoạn;
- bộ chọn cách xử lý câu hỏi;
- sổ khẳng định;
- gói bằng chứng;
- không gian nghiên cứu;
- quy trình cập nhật Bộ não thứ hai;
- kiểm tra chất lượng;
- giao diện công cụ cho AI.

---

# 51. Công nghệ dự kiến cho giai đoạn đầu

Đây là lựa chọn triển khai hiện tại, không phải hiến pháp bất biến.

| Nhiệm vụ | Lựa chọn dự kiến |
|---|---|
| Ngôn ngữ chính | Python |
| Giao diện dịch vụ | FastAPI |
| Cơ sở dữ liệu thông tin | PostgreSQL hoặc giải pháp nhẹ hơn ở giai đoạn thử nghiệm |
| File lớn | ổ đĩa/NAS hoặc MinIO/S3 |
| Đọc tài liệu | Docling kết hợp công cụ đọc PDF phù hợp |
| MOBI | Calibre |
| Nhận dạng chữ | PaddleOCR |
| Tìm theo ý nghĩa | Qdrant hoặc công cụ tương đương |
| RAG đầy đủ | RAGFlow qua bộ chuyển tiếp nếu phù hợp |
| Tìm trong Markdown | QMD |
| Bộ não thứ hai | Markdown + Git |
| Đọc sâu sách dài | PageIndex khi cần |
| Giao tiếp AI | MCP + HTTP |
| Đồ thị | chưa bật mặc định |

Các lựa chọn cụ thể phải được kiểm chứng trên dữ liệu thật.

---

# 52. Lộ trình xây dựng

## Giai đoạn thử nghiệm

Chọn 200–500 trang đại diện.

Đo:

- lấy chữ;
- nhận dạng chữ;
- thứ tự đọc;
- trang;
- tìm kiếm;
- trích dẫn.

## Bản kỹ thuật 0.1 — Nguồn và bằng chứng

```text
nguồn bất biến
↓
số hóa
↓
mô hình dữ liệu
↓
tìm kiếm
↓
trích dẫn
```

## Bản kỹ thuật 0.2 — Bộ não thứ hai

Thêm:

- Markdown;
- liên kết;
- sổ khẳng định;
- QMD;
- Git.

## Bản kỹ thuật 0.3 — Nghiên cứu sâu

Thêm:

- không gian nghiên cứu;
- gói bằng chứng;
- đề xuất;
- một bộ ghi duy nhất;
- kiểm tra mâu thuẫn;
- tự bảo trì.

## Bản kỹ thuật 0.4 — Đọc sâu và điều phối

Thêm:

- PageIndex;
- RAGFlow;
- bộ chọn cách xử lý;
- các bộ chuyển tiếp.

## Bản kỹ thuật 0.5 — Quan hệ phức tạp

Chỉ khi có nhu cầu thực:

- đồ thị tri thức;
- LightRAG;
- Graphiti;
- các hệ trí nhớ khác.

## Bản sản xuất 1.0

Hoàn thiện:

- giao diện;
- phân quyền;
- sao lưu;
- phục hồi;
- kiểm thử tự động;
- giám sát;
- tài liệu vận hành.

---

# 53. Thứ tự ưu tiên

Nếu buộc phải chọn:

```text
1. Đúng nguồn
2. Đúng cấu trúc
3. Đúng trang
4. Tìm đúng
5. Trích dẫn đúng
6. Giảm lượng chữ AI phải đọc
7. Tích lũy hiểu biết
8. Tự động hóa
9. Đồ thị và tính năng nâng cao
```

Không nên đảo ngược thứ tự này.

---

# 54. Điểm khác biệt thực sự

Thư Viện Sống AI không phải “RAGFlow + Obsidian”.

Kiến trúc thật sự là:

```text
NGUỒN BẤT BIẾN
        ↓
KHO DỮ LIỆU CHUẨN
        ↓
HAI LOẠI TRÍ NHỚ
    │
    ├── trí nhớ bằng chứng
    └── trí nhớ hiểu biết
        ↓
ĐỌC THEO ĐỘ SÂU THÍCH ỨNG
        ↓
GÓI BẰNG CHỨNG
        ↓
AI NGHIÊN CỨU
        ↓
KIỂM CHỨNG
        ↓
TRI THỨC TỐT
        ↓
BỘ NÃO THỨ HAI
```

---

# 55. Mô hình dễ nhớ nhất

Có thể coi hệ thống có hai nhân vật.

## Người thủ thư

Hệ tìm bằng chứng đóng vai người thủ thư cực giỏi.

Nó biết:

- sách nào;
- chương nào;
- trang nào;
- đoạn nào.

## Học giả

Bộ não thứ hai đóng vai học giả tích lũy hiểu biết qua nhiều lần nghiên cứu.

Nó biết:

- vấn đề này đã nghiên cứu chưa;
- khái niệm liên hệ với gì;
- các nguồn đồng thuận ở đâu;
- các nguồn mâu thuẫn ở đâu;
- còn câu hỏi gì chưa giải quyết.

## Khi kết hợp

> Học giả đưa ra hiểu biết.

> Thủ thư mang bằng chứng đến kiểm tra.

---

# 56. Câu kết luận quan trọng nhất

> **Hãy xây một thư viện số làm trí nhớ gốc; phía trên là hệ tìm bằng chứng để tìm đúng sách, đúng chương, đúng trang; phía trên nữa là Bộ não thứ hai để giữ những gì AI đã hiểu và đã kiểm chứng. Mỗi câu hỏi chỉ cho AI đọc lượng thông tin tối thiểu cần thiết, còn mọi tri thức mới chỉ được ghi nhớ sau khi có thể truy ngược về nguồn.**

Câu ngắn hơn:

> **RAG giúp tìm đúng bằng chứng. Bộ não thứ hai giúp không phải học lại từ đầu. Sách gốc luôn là trọng tài cuối cùng.**

Mục tiêu cuối cùng không phải tạo thêm một ứng dụng RAG.

Mục tiêu là:

> **xây một nền tảng tri thức có thể sống qua nhiều thế hệ AI.**
