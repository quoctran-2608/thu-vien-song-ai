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

Đây cũng là tinh thần cốt lõi của phương án ban đầu: dữ liệu thuộc về hệ thống của mình, còn các phần mềm như RAGFlow, QMD hay PageIndex chỉ là các bộ máy có thể thay thế.

---

# 2. Bài toán mà hệ thống phải giải quyết

Một kho sách lớn thường chứa lẫn rất nhiều loại tài liệu:

- PDF có lớp chữ tốt;
- PDF có chữ nhưng mã hóa lỗi;
- PDF chỉ là ảnh quét;
- PDF vừa có chữ vừa có ảnh;
- EPUB;
- MOBI;
- nhiều ấn bản của cùng một tác phẩm;
- tài liệu nhiều ngôn ngữ;
- trang cũ, mờ, cong, lệch;
- văn bản hai cột;
- sách nhiều chú thích;
- bảng biểu;
- hình ảnh;
- tài liệu nghiên cứu;
- bài viết;
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

thì hệ thống sớm gặp nhiều vấn đề:

- mất cấu trúc sách;
- không phân biệt được tác phẩm và ấn bản;
- khó truy đúng trang;
- tìm được đoạn “na ná” nhưng không thật sự chứng minh điều cần nói;
- đưa quá nhiều chữ cho AI;
- AI phải đọc lại những thứ đã nghiên cứu trước đây;
- bản tóm tắt dần bị tách khỏi nguồn gốc;
- thay một phần mềm có thể kéo theo việc phải xây lại toàn bộ kho.

Vì vậy dự án này phải được thiết kế từ đầu theo hướng khác.

---

# 3. Kết luận kiến trúc ngay từ đầu

Phương án cuối cùng gồm bốn lớp:

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
một bộ nhớ nhỏ cho vấn đề đang xử lý

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

Có một số nguyên tắc không phải là lựa chọn kỹ thuật thông thường. Chúng là những nguyên tắc không nên bị phá khi hệ thống phát triển.

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

File nguồn phải được giữ nguyên.

AI không sửa trực tiếp:

- PDF;
- EPUB;
- MOBI;
- ảnh trang;
- văn bản thô lấy từ tài liệu.

Nếu cần làm sạch văn bản, phải lưu:

```text
văn bản thô
+
văn bản đã làm sạch
```

chứ không ghi đè văn bản thô.

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

Hệ tìm kiếm có thể trả về một đoạn vì đoạn đó có nhiều từ giống câu hỏi.

Điều đó chỉ có nghĩa:

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

Một lỗi rất nguy hiểm của AI là:

- tài liệu có thật;
- số trang có thật;
- đoạn trích có thật;

nhưng:

> đoạn đó không thực sự hỗ trợ điều AI đang nói.

Vì vậy hệ thống nghiên cứu sâu phải kiểm tra cả:

> **“đoạn này có thực sự hỗ trợ khẳng định không?”**

chứ không chỉ kiểm tra xem nguồn có tồn tại hay không.

---

## 4.7. “Chưa đủ bằng chứng” là một câu trả lời hợp lệ

AI không được ép tất cả câu hỏi thành kết luận chắc chắn.

Một kết quả hoàn toàn hợp lệ có thể là:

> Chưa đủ bằng chứng trong phạm vi tài liệu đã tìm.

Hoặc:

> Các nguồn hiện có mâu thuẫn nhau.

Hoặc:

> Chưa thể kết luận.

---

## 4.8. Không để phần mềm bên ngoài sở hữu dữ liệu

Tiêu chuẩn rất dễ kiểm tra là:

> Nếu xóa hoàn toàn RAGFlow rồi cài lại, kho dữ liệu chuẩn vẫn còn.

> Nếu bỏ QMD, toàn bộ Markdown của Bộ não thứ hai vẫn còn.

> Nếu không dùng PageIndex nữa, cấu trúc chương/mục/trang vẫn còn.

Bản phương án ban đầu cũng đặt rất rõ tiêu chuẩn này.

---

## 4.9. Nhiều AI có thể nghiên cứu, nhưng chỉ một nơi được ghi chính thức

Nhiều tác tử AI — tức các tiến trình AI đảm nhận những nhiệm vụ khác nhau — có thể cùng:

- tìm;
- đọc;
- phân tích;
- đề xuất.

Nhưng không được cùng sửa trực tiếp một trang tri thức.

Quy trình đúng:

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

Bản kiến trúc ban đầu coi đây là một cơ chế bắt buộc.

---

## 4.10. Mọi thay đổi lớn phải phục hồi được

Nếu một lần cập nhật cần sửa:

```text
Vô-ngã.md
Duyên-khởi.md
index.md
```

thì không được để tình trạng:

```text
sửa xong Vô-ngã.md
↓
gặp lỗi
↓
hai file còn lại chưa sửa
```

Phải:

> **ghi thành công toàn bộ hoặc không ghi gì cả.**

Sau đó lưu lịch sử bằng Git.

Ý tưởng giao dịch cập nhật này đã được mô tả rất rõ trong phương án ban đầu.

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

# 5. Bốn lớp của Thư Viện Sống

## 5.1. Lớp 1 — Kho nguồn gốc

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

> **Tài liệu thực sự là gì?**

Nó không trả lời:

> “AI hiểu gì về tài liệu?”

---

## 5.2. Lớp 2 — Kho dữ liệu chuẩn và hệ tìm bằng chứng

Đây là lớp biến tài liệu thành dạng máy có thể xử lý ổn định.

Ví dụ:

```text
Tác phẩm
↓
Ấn bản
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

> “Thông tin nằm ở đâu?”

> “Trang nào?”

> “Ấn bản nào?”

> “Đoạn nào có liên quan?”

---

## 5.3. Lớp 3 — Bộ não thứ hai

Đây là tri thức đã được tiêu hóa.

Ví dụ:

```text
Khái niệm/
    Vô ngã.md
    Duyên khởi.md
    Tánh không.md

Nhân vật/

Truyền thống/

So sánh/

Tranh luận/

Tổng hợp/

Câu hỏi mở/
```

Bộ não thứ hai trả lời:

> “Ta đã hiểu gì về vấn đề này?”

---

## 5.4. Lớp 4 — Không gian nghiên cứu

Đây là bàn làm việc tạm thời.

Ví dụ một câu hỏi:

> Quan niệm giác ngộ khác nhau thế nào giữa các nhóm tài liệu?

Hệ thống có thể tạo:

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
- kết luận chưa chắc chắn không được tự động trở thành tri thức chính thức.

---

# 6. Số hóa tài liệu đúng cách

## 6.1. Không nhận dạng chữ từ ảnh toàn bộ PDF

Đây là một trong những nguyên tắc tiết kiệm tài nguyên quan trọng nhất.

Đối với mỗi trang PDF:

```text
kiểm tra trang
↓
có lớp chữ tốt?
├── có
│   ↓
│ lấy chữ trực tiếp
│
└── không
    ↓
nhận dạng chữ từ ảnh
```

Có thể dùng các tín hiệu như:

- có lớp chữ hay không;
- số lượng ký tự;
- Unicode có hợp lệ không;
- chữ có bị rác hay không;
- thứ tự đọc có hợp lý không.

Một cuốn 500 trang có thể chỉ có vài chục trang thực sự cần nhận dạng chữ từ ảnh.

---

## 6.2. Trang dễ và trang khó không nên xử lý giống nhau

Có thể dùng nhiều tầng:

```text
trang cần nhận dạng chữ
↓
PP-OCRv6
↓
đủ tốt?
├── có → dùng kết quả
└── không
     ↓
PaddleOCR-VL hoặc công cụ mạnh hơn
```

PP-OCRv6 là một họ mô hình nhận dạng chữ.

PaddleOCR-VL là mô hình có khả năng hiểu bố cục trang phức tạp hơn.

Tên công cụ cụ thể có thể thay đổi sau này; nguyên tắc nhiều tầng mới là phần cần giữ lâu dài.

---

# 7. EPUB và MOBI phải được xử lý khác PDF

## EPUB

EPUB thường đã có:

- HTML/XHTML;
- mục lục;
- tiêu đề;
- chương;
- thông tin sách.

Không nên biến EPUB thành ảnh rồi nhận dạng chữ.

Cần lấy trực tiếp cấu trúc có sẵn.

---

## MOBI

MOBI có thể được chuẩn hóa qua Calibre:

```text
MOBI
↓
EPUB hoặc HTML
↓
đọc cấu trúc
```

---

# 8. Bảo tồn văn bản thô và văn bản sạch

Mỗi đoạn quan trọng nên giữ tối thiểu:

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

Như vậy khi phát hiện lỗi làm sạch hoặc lỗi nhận dạng chữ, ta vẫn quay lại được nguồn ban đầu.

---

# 9. Dấu vân tay số và chống trùng

Mỗi file nguồn cần có SHA-256.

Có thể hiểu SHA-256 là:

> **dấu vân tay số của file.**

Nếu hai file có cùng dấu vân tay thì chúng giống nhau tuyệt đối.

Ngoài ra còn cần phát hiện các bản gần giống:

- cùng sách nhưng khác định dạng;
- cùng ấn bản nhưng scan khác nhau;
- hai file chỉ khác vài trang;
- PDF và EPUB có cùng nội dung.

Có thể dùng các kỹ thuật tạo dấu vân tay nội dung như MinHash hoặc SimHash nếu cần.

Quan trọng:

> **không được vì phát hiện gần trùng mà làm mất thông tin về ấn bản.**

---

# 10. Kho dữ liệu chuẩn — trái tim của toàn hệ thống

Không phải RAGFlow.

Không phải Qdrant.

Không phải Obsidian.

Mà chính là:

> **mô hình dữ liệu chuẩn.**

Bản phương án ban đầu cũng đặt phần này ở vị trí trung tâm.

---

# 11. Hai cách nhìn kho dữ liệu chuẩn

## 11.1. Cách nhìn theo thực thể

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

### Tác phẩm

Ví dụ:

> một cuốn sách về mặt nội dung trí tuệ.

### Ấn bản

Ví dụ:

- bản năm 1995;
- bản dịch năm 2008;
- tái bản năm 2022.

### Nguồn file

PDF/EPUB/MOBI cụ thể.

### Chương / mục

Cấu trúc logic.

### Trang

Trang vật lý hoặc vị trí tương đương.

### Khối

Có thể là:

- tiêu đề;
- đoạn văn;
- bảng;
- chú thích;
- hình.

### Đoạn tìm kiếm

Phần văn bản được chuẩn bị để hệ tìm kiếm sử dụng.

---

## 11.2. Cách nhìn theo tầng dữ liệu

### Tầng 0 — Danh mục

- tên sách;
- tác giả;
- dịch giả;
- nhà xuất bản;
- năm;
- ngôn ngữ;
- chủ đề.

### Tầng 1 — Cấu trúc

- mục lục;
- phần;
- chương;
- mục;
- số trang.

### Tầng 2 — Tìm kiếm

Các đoạn văn đã được chuẩn bị để tìm.

### Tầng 3 — Nguồn

- file gốc;
- văn bản thô;
- văn bản sạch;
- ảnh trang;
- vị trí chữ;
- độ tin cậy.

Hai cách nhìn này không thay thế nhau.

Một cách giải thích **các đối tượng**.

Cách kia giải thích **vai trò của dữ liệu**.

---

# 12. Chia đoạn theo cấu trúc, không chia máy móc

Không nên:

```text
cứ 1.000 ký tự
→ cắt
```

mà nên ưu tiên:

```text
tiêu đề
↓
mục
↓
đoạn
↓
ranh giới tự nhiên của nội dung
```

Sau đó mới cân đối độ dài.

Một đoạn tìm kiếm nên luôn biết mình thuộc:

```text
Tên sách
> Phần
> Chương
> Mục
```

Nhờ đó AI không đọc một đoạn bị tách khỏi ngữ cảnh.

---

# 13. RAG là gì?

RAG là viết tắt của *Retrieval-Augmented Generation*.

Trong dự án này có thể hiểu đơn giản là:

> **tìm phần tài liệu thích hợp trước, rồi mới cho AI đọc và trả lời.**

Không nên hiểu RAG đơn giản là:

> “cơ sở dữ liệu véc-tơ”.

RAG là cả một chuỗi xử lý.

---

# 14. Không được chỉ tìm theo ý nghĩa

Có hai nhóm tìm kiếm khác nhau.

## 14.1. Tìm theo chữ

Rất mạnh với:

- tên người;
- tên tác phẩm;
- câu nguyên văn;
- thuật ngữ;
- mã tài liệu;
- cụm từ hiếm.

---

## 14.2. Tìm theo ý nghĩa

Hệ thống biến đoạn văn thành một dãy số đại diện tương đối cho ý nghĩa.

Nhờ vậy câu:

> “buông bỏ sự đồng nhất với cái tôi”

có thể tìm được đoạn dùng từ khác nhưng nói cùng ý.

---

## 14.3. Phương án tốt nhất: kết hợp cả hai

```text
TÌM THEO CHỮ
        │
        ├─────────┐
                  ↓
              TRỘN KẾT QUẢ
                  ↓
             XẾP HẠNG LẠI
                  ↓
               3–8 ĐOẠN
                  ↑
        ┌─────────┘
        │
TÌM THEO Ý NGHĨA
```

Bộ xếp hạng lại là một mô hình nhỏ đọc câu hỏi và các kết quả ứng viên để sắp lại thứ tự chính xác hơn.

---

# 15. Một kết quả tìm được phải đi qua “cửa bằng chứng”

Không nên có luồng:

```text
tìm được
↓
đưa thẳng cho AI
```

Nên có:

```text
kết quả tìm được
↓
ứng viên
↓
kiểm tra:
- đúng nguồn?
- đúng trang?
- có đủ ngữ cảnh?
- có thật sự liên quan?
↓
bằng chứng
```

Ở chế độ hỏi đáp đơn giản, bước kiểm tra có thể nhẹ.

Ở chế độ nghiên cứu nghiêm ngặt, bước này phải mạnh hơn.

---

# 16. Tóm tắt nhiều tầng

Mỗi tài liệu có thể có các lớp tóm tắt:

```text
SÁCH
↓
CHƯƠNG
↓
MỤC
↓
ĐOẠN GỐC
```

Ví dụ:

- tóm tắt sách: vài trăm đơn vị chữ;
- tóm tắt chương: ngắn hơn;
- mô tả mục: rất ngắn;
- văn bản gốc: chỉ đọc khi cần.

Nhờ đó câu hỏi tổng quát không cần tìm thẳng vào hàng triệu đoạn.

---

# 17. Đọc theo độ sâu thích ứng

Đây là một nguyên tắc trung tâm.

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

## Cần đọc một cuốn sâu hơn

```text
mục lục
↓
chọn chương
↓
chọn mục
↓
đọc đoạn
```

## Cần kiểm tra câu nguyên văn

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

Nguyên tắc có thể diễn đạt bằng một câu:

> **AI chỉ đọc sâu đến mức nhiệm vụ thật sự cần.**

---

# 18. PageIndex được đặt ở đâu?

PageIndex là một phương pháp tổ chức tài liệu thành dạng cây để AI đi theo:

```text
sách
↓
chương
↓
mục
↓
đoạn
```

Nó đặc biệt hữu ích với sách dài.

Nhưng không nên dùng làm lớp tìm kiếm mặc định cho toàn thư viện.

Luồng hợp lý:

```text
toàn thư viện
↓
hệ tìm kiếm chọn vài cuốn
↓
PageIndex
↓
đi sâu bên trong những cuốn đó
```

Đây cũng là vị trí được đề xuất trong phương án ban đầu.

---
# 19. Hai chỉ mục phải tách nhau

Không nên trộn:

```text
10 triệu đoạn sách
+
5.000 trang tri thức
```

vào một nơi rồi coi chúng giống nhau.

Nên có:

```text
CHỈ MỤC KHO SÁCH
= bằng chứng

CHỈ MỤC BỘ NÃO THỨ HAI
= tri thức đã tiêu hóa
```

Khi hỏi:

> Ta đã hiểu gì về X?

ưu tiên Bộ não thứ hai.

Khi hỏi:

> Điều này lấy từ đâu?

ưu tiên kho sách.

Bản kiến trúc ban đầu gọi đây là hai loại trí nhớ: **trí nhớ hiểu biết** và **trí nhớ bằng chứng**.

---

# 20. Gói bằng chứng

Một trong những phần quan trọng nhất của kiến trúc là **gói bằng chứng**.

Đây là gói nhỏ mà AI cuối cùng đọc để suy luận.

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

---

# 21. Vì sao gói bằng chứng tiết kiệm rất nhiều chi phí?

Cách ngây thơ có thể lấy:

```text
30 đoạn
×
800 đơn vị chữ
```

rồi đưa tất cả cho AI.

Trong khi phương án tốt hơn có thể chỉ cần:

```text
4–8 đoạn tốt nhất
+
một ít tri thức tổng hợp
```

Bản thiết kế ban đầu minh họa khoảng vài nghìn đơn vị chữ thay vì hàng chục nghìn. Con số cụ thể chỉ là ví dụ, không phải mức tiết kiệm bảo đảm cho mọi trường hợp.

Điểm quan trọng là:

> **chi phí lớn không chỉ nằm ở việc tạo chỉ mục. Nó còn nằm ở việc cho mô hình lớn đọc quá nhiều thứ không cần thiết ở mỗi câu hỏi.**

---

# 22. Bộ não thứ hai là gì?

Bộ não thứ hai không phải:

> một thư mục chứa bản tóm tắt từng cuốn sách.

Một Bộ não thứ hai tốt phải tổ chức theo tri thức.

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

Một trang:

```text
Vô-ngã.md
```

có thể tham chiếu đến:

- sách A;
- sách B;
- sách C;
- tác giả D;
- một nghiên cứu trước đó.

Nó phải liên kết với:

```text
[[Ngũ uẩn]]
[[Duyên khởi]]
[[Tánh không]]
[[Chấp thủ]]
```

---

# 23. Bộ não thứ hai không thay thế sách gốc

Nếu hệ thống cứ tóm tắt rồi lại tóm tắt bản tóm tắt:

```text
nguồn X
↓
tóm tắt X'
↓
tổng hợp X''
↓
tổng hợp lại X'''
```

sai lệch có thể tăng dần.

Do đó:

> **Bộ não thứ hai là điều AI đã hiểu.**

> **Kho nguồn là nơi kiểm tra điều đó có đúng hay không.**

Hai lớp phải tồn tại song song.

---

# 24. RAG có độ phủ rộng, Bộ não thứ hai có độ sâu tích lũy

Giả sử thư viện có:

```text
100.000 sách
```

Không nên cho AI đọc 100.000 sách ngay khi nhập để tạo một siêu wiki.

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

Chủ đề dùng nhiều:

> ngày càng được tổng hợp sâu hơn.

Chủ đề chưa dùng:

> vẫn nằm trong thư viện và có thể tìm khi cần.

Đây là cách giảm rất lớn chi phí tạo Bộ não thứ hai.

---

# 25. Sổ khẳng định

Một trang Markdown dễ đọc cho con người là chưa đủ.

Những kết luận quan trọng nên có một bản ghi có cấu trúc.

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

Bản thiết kế ban đầu đã đưa “sổ khẳng định” thành một phần chính thức của kiến trúc.

---

# 26. Khẳng định cần có hai chiều trạng thái

## 26.1. Nó được tạo ra bằng cách nào?

### TRÍCH XUẤT

Nguồn nói trực tiếp.

### SUY LUẬN

AI rút ra từ bằng chứng.

### TỔNG HỢP

AI kết hợp nhiều nguồn.

---

## 26.2. Bằng chứng hỗ trợ nó đến đâu?

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

Hai chiều này không nên trộn làm một.

---

# 27. Phải tách nguyên văn, bản dịch và suy luận

Ít nhất nên phân biệt:

```text
1. Nguyên văn nguồn

2. Bản dịch xuất bản

3. Bản dịch làm việc do AI tạo

4. Diễn đạt lại

5. Diễn giải của tác giả/học giả

6. Tổng hợp của AI
```

Điều đặc biệt quan trọng:

> **không được để người đọc hiểu nhầm bản dịch AI là bản dịch xuất bản.**

---

# 28. Không gian nghiên cứu

Đối với câu hỏi khó, AI không nên vừa nghiên cứu vừa sửa Bộ não thứ hai.

Phải tạo một không gian tạm.

Ví dụ:

```text
research/
└── 2026-10-giac-ngo/
    ├── cau-hoi.md
    ├── pham-vi.md
    ├── tai-lieu-ung-vien.json
    ├── bang-chung/
    ├── ghi-chu/
    ├── mau-thuan.md
    ├── tong-hop.md
    └── truy-nguon.json
```

Bản thiết kế ban đầu cũng đặt rõ chuỗi:

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

# 29. Tìm bằng chứng phản bác

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

Đây là cơ chế đặc biệt hữu ích khi kết luận chứa các từ như:

- tất cả;
- luôn luôn;
- duy nhất;
- không có;
- sớm nhất;
- chưa từng.

---

# 30. “Không tìm thấy” không đồng nghĩa “không tồn tại”

Nếu tìm trong một kho tài liệu mà không thấy bằng chứng cho X, kết luận đúng không nên là:

> “Không có bằng chứng nào cho X.”

Nên là:

> **“Không tìm thấy bằng chứng cho X trong phạm vi tài liệu đã khảo sát.”**

Kết quả tìm kiếm âm nên ghi được:

```text
đã tìm kho nào
phiên bản nào
ngôn ngữ nào
dùng cách tìm nào
ngày nào
phạm vi có hạn chế gì
```

Điều này đặc biệt quan trọng với nghiên cứu lịch sử và học thuật.

---

# 31. Nhiều nguồn đồng ý chưa chắc là nhiều bằng chứng độc lập

Ba cuốn sách có thể cùng nói một điều vì cả ba đều chép từ một nguồn chung.

Do đó trong nghiên cứu rất sâu, có thể cần theo dõi:

- chuỗi trích dẫn;
- quan hệ bản dịch;
- họ bản thảo;
- nguồn chung;
- phụ thuộc văn bản.

Đây không phải tính năng cần xây ngay ở bản đầu.

Nhưng mô hình dữ liệu không nên chặn khả năng bổ sung sau này.

---

# 32. Kiểm tra câu trích

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

Nếu câu không giống nguồn:

> không được trình bày như trích dẫn nguyên văn.

Nếu AI diễn đạt lại:

> phải ghi rõ đó là diễn đạt lại.

---

# 33. Kiểm tra khẳng định với bằng chứng

Một khẳng định có thể được đánh giá:

```text
TRỰC TIẾP
= nguồn nói gần như chính xác điều đó

MẠNH
= là cách diễn đạt lại hợp lý

YẾU
= có liên quan nhưng cần thêm giả định

KHÔNG ĐỦ
= nguồn chưa chứng minh được

MÂU THUẪN
= có bằng chứng chống lại
```

Trong nghiên cứu nghiêm ngặt:

- `TRỰC TIẾP` được dùng;
- `MẠNH` được dùng;
- `YẾU` phải ghi giới hạn;
- `KHÔNG ĐỦ` không được biến thành kết luận chắc chắn;
- `MÂU THUẪN` phải được trình bày như một điểm tranh luận.

---

# 34. Hồ sơ của mỗi lần nghiên cứu

Một nghiên cứu sâu nên có mã riêng.

Ví dụ:

```text
run_id
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

Nhờ đó về sau có thể hỏi:

> Tại sao hệ thống từng đưa ra kết luận này?

và tái dựng quá trình.

---

# 35. Bộ não thứ hai phải cập nhật theo phần thay đổi

Giả sử:

```text
hôm qua: 10.000 sách

hôm nay: thêm 3 sách
```

Không được đọc lại 10.003 sách.

Ta cần một **bảng kê xử lý**, trong tài liệu kỹ thuật thường gọi là `manifest`.

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
    tìm những trang tri thức có thể bị ảnh hưởng
     ↓
    chỉ xem xét cập nhật những trang đó
```

Cách cập nhật gia tăng này đã được nhấn mạnh trong phương án ban đầu.

---

# 36. Bộ não thứ hai có thể tự bảo trì nhưng không được tự bịa

Hệ thống có thể định kỳ tìm:

- liên kết chết;
- trang không có liên kết;
- hai trang trùng nhau;
- khẳng định thiếu nguồn;
- mâu thuẫn;
- trang quá dài;
- trang quá nhỏ;
- chủ đề xuất hiện nhiều nhưng chưa có trang riêng.

Nhưng khi thấy:

```text
Nguồn A nói X
Nguồn B nói ngược lại
```

hệ thống không được tự động xóa một bên.

Nó phải ghi:

```text
A:
...

B:
...

Tình trạng:
chưa thể giải quyết
```

Đây là cách “tự chữa” đáng tin hơn là để AI tự quyết định lịch sử.

---

# 37. Vai trò của RAGFlow

RAGFlow là một hệ thống RAG khá đầy đủ.

Trong kiến trúc này, nó có thể giúp:

- quản lý tài liệu;
- tìm kiếm;
- chia đoạn;
- xếp hạng;
- dẫn nguồn;
- chạy các tác tử;
- biên dịch tri thức.

Nhưng:

> **RAGFlow là động cơ, không phải lõi dữ liệu.**

Có thể hình dung:

```text
Thư Viện Sống
↓
bộ chuyển tiếp
↓
RAGFlow
```

Ta đưa cho nó:

```text
tài liệu
đoạn
thông tin kèm theo
```

và nhận:

```text
ứng viên
điểm xếp hạng
tham chiếu
```

Nếu sau này thay RAGFlow:

> giao diện cấp cao của Thư Viện Sống không đổi.

---

# 38. Vai trò của QMD

QMD là một công cụ tìm trong Markdown.

Nó phù hợp với:

```text
brain/
```

hơn là trở thành nơi duy nhất lập chỉ mục toàn bộ hàng triệu trang sách.

Nó có thể giúp Bộ não thứ hai kết hợp:

- tìm theo chữ;
- tìm theo ý nghĩa;
- xếp hạng kết quả.

---

# 39. Vai trò của PageIndex

PageIndex hỗ trợ:

> đọc sâu tài liệu dài theo cấu trúc cây.

Vai trò:

```text
RAG
↓
chọn vài sách
↓
PageIndex
↓
chọn chương
↓
chọn mục
↓
đọc sâu
```

---

# 40. Vai trò của LightRAG và đồ thị tri thức

LightRAG và các hệ đồ thị có thể hữu ích khi câu hỏi là:

> tác giả nào liên hệ với khái niệm nào?

> trường phái nào ảnh hưởng đến trường phái nào?

> những ý tưởng nào nối nhiều tài liệu lại với nhau?

Nhưng không nên xây đồ thị toàn bộ thư viện ngay từ ngày đầu.

Nguyên tắc:

> **chỉ xây đồ thị khi bài toán thật sự cần quan hệ.**

---

# 41. Vai trò của Graphiti

Graphiti hữu ích hơn với thông tin thay đổi theo thời gian.

Ví dụ:

```text
2024
hệ thống dùng A

2025
chuyển sang B

2026
chuyển sang C
```

Nó có thể hữu ích với:

- lịch sử quyết định;
- nghiên cứu đang thay đổi;
- thông tin thời sự;
- trạng thái dự án.

Đối với sách cổ hoặc tài liệu bất biến, nó không phải ưu tiên ban đầu.

---

# 42. Vai trò của Cognee

Cognee có những ý tưởng đáng tham khảo về trí nhớ của tác tử AI:

```text
ghi nhớ
nhớ lại
cải thiện
quên
```

Nhưng không cần đưa Cognee vào lõi ngay.

Thư Viện Sống nên có giao diện của riêng mình.

Sau này mới quyết định dùng bộ máy nào ở phía sau.

---

# 43. Obsidian chỉ là giao diện

Markdown mới là dữ liệu.

Obsidian có thể giúp:

- đọc;
- viết;
- xem mạng liên kết;
- duyệt wiki.

Nhưng nếu ngày mai không dùng Obsidian:

> toàn bộ Bộ não thứ hai vẫn phải đọc được bằng trình soạn thảo khác, trình duyệt, AI hoặc công cụ dòng lệnh.

---

# 44. AI chỉ nên thấy một bộ công cụ rất nhỏ

Không nên đưa hàng trăm lệnh cấp thấp cho AI.

Giao diện cấp cao có thể chỉ gồm:

```text
search_library()
= tìm trong thư viện

get_book_outline()
= lấy cấu trúc một cuốn

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
= mở một nghiên cứu sâu
```

Ý tưởng này đã có rất rõ trong phương án ban đầu.

AI không cần biết phía sau là:

- Qdrant;
- QMD;
- RAGFlow;
- PageIndex;
- hay một công cụ khác.

---

# 45. MCP là gì?

MCP là tên một chuẩn giao tiếp giúp AI gọi công cụ và dữ liệu bên ngoài theo cách thống nhất.

Trong Thư Viện Sống:

```text
AI
↓
MCP của Thư Viện Sống
↓
các lệnh cấp cao
↓
các bộ máy phía sau
```

Nhờ vậy:

> thay công cụ phía sau không nhất thiết làm thay đổi cách AI sử dụng thư viện.

---

# 46. Luồng hỏi đáp tổng thể

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

Đây là vòng khép kín quan trọng nhất của toàn hệ thống.

---

# 47. Vòng đời tri thức

Có thể tóm tắt toàn bộ dự án bằng:

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

# 48. Chế độ nghiên cứu nghiêm ngặt

Không phải câu hỏi nào cũng cần quy trình rất nặng.

Vì vậy nên có một chế độ riêng cho:

- nghiên cứu học thuật;
- viết sách;
- nghiên cứu lịch sử;
- đối chiếu nhiều nguồn;
- câu hỏi có yêu cầu trích dẫn chính xác;
- kết luận có rủi ro cao.

Khi bật chế độ này:

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

# 49. Chế độ kho nguồn đóng

Đôi khi người dùng muốn:

> chỉ được dùng những tài liệu nằm trong kho đã chỉ định.

Khi đó:

- không dùng kiến thức có sẵn của AI làm bằng chứng;
- không âm thầm tìm web;
- không bổ sung nguồn ngoài;
- nếu thiếu thì trả:

> **Chưa đủ dữ liệu trong phạm vi kho nguồn được phép.**

---

# 50. Kiểm thử chất lượng

Hệ thống cần kiểm thử ở nhiều tầng.

## 50.1. Kiểm thử số hóa

Đo:

- lỗi ký tự;
- lỗi dấu tiếng Việt;
- thứ tự đọc;
- tiêu đề;
- chú thích;
- số trang;
- bảng;
- trang nhiều cột.

Nên dùng vài trăm trang đại diện cho những loại tài liệu khó khác nhau.

---

## 50.2. Kiểm thử tìm kiếm

Tạo một bộ câu hỏi chuẩn.

Ví dụ:

```text
Câu hỏi:
Tác giả A nói gì về X?

Đáp án mong đợi:
book_328
trang 71–74
```

Sau đó so sánh:

- chỉ tìm theo chữ;
- chỉ tìm theo ý nghĩa;
- tìm kết hợp;
- thêm xếp hạng lại;
- thêm tìm phân tầng.

---

## 50.3. Kiểm thử trích dẫn
Kiểm tra:

- đúng sách;
- đúng ấn bản;
- đúng trang;
- đúng đoạn;
- đoạn có thật sự hỗ trợ câu trả lời.

---

## 50.4. Kiểm thử Bộ não thứ hai

Tìm:

- khẳng định thiếu nguồn;
- suy luận bị trình bày như sự kiện;
- trang trùng;
- mâu thuẫn;
- liên kết hỏng;
- thông tin cũ.

---

# 51. Bộ kiểm thử cố định

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

Nếu chất lượng giảm:

> không triển khai chỉ vì công cụ mới hơn.

Bản kiến trúc ban đầu cũng đặt rõ nguyên tắc này.

---

# 52. Những gì không nên làm ở phiên bản đầu

Không nên:

- nhận dạng chữ toàn bộ PDF;
- xây đồ thị toàn kho;
- huấn luyện lại AI bằng cả thư viện;
- dựng kiến trúc quá nhiều máy khi chưa cần;
- cho AI tự chạy vòng nghiên cứu không giới hạn;
- dùng duy nhất tìm kiếm véc-tơ;
- đưa quá nhiều đoạn cho mô hình lớn;
- cho AI tự sửa trực tiếp Bộ não thứ hai;
- xây Second Brain của toàn bộ thư viện trước khi biết chủ đề nào thực sự cần.

---

# 53. Phần nào nên dùng lại, phần nào phải tự kiểm soát?

## Không nên tự viết lại từ đầu

- máy đọc PDF;
- công cụ nhận dạng chữ;
- cơ sở dữ liệu véc-tơ;
- mô hình biểu diễn ý nghĩa;
- mô hình xếp hạng lại;
- PageIndex;
- QMD;
- công cụ đồ thị.

---

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

Đây cũng là ranh giới được chốt rất rõ trong phương án kiến trúc trước đó.

---

# 54. Công nghệ dự kiến cho giai đoạn đầu

Các lựa chọn dưới đây đã được **kiểm chứng lại bằng nguồn hiện hành ngày 05/10/2026**. Chi tiết xem [Báo cáo kiểm chứng công cụ ngày 05/10/2026](16-kiem-chung-cong-cu-2026-10-05.md).

Đây vẫn là lựa chọn triển khai để thử nghiệm, không phải “hiến pháp” bất biến.

| Nhiệm vụ | Lựa chọn dự kiến sau kiểm chứng |
|---|---|
| Ngôn ngữ chính | Python |
| Giao diện dịch vụ | FastAPI |
| Cơ sở dữ liệu thông tin | PostgreSQL hoặc giải pháp nhẹ hơn ở giai đoạn thử nghiệm |
| File lớn | ổ đĩa/NAS hoặc MinIO/S3 |
| Đọc và chuẩn hóa tài liệu | Docling là ứng viên mặc định để thử |
| MOBI | Calibre hoặc tuyến chuyển đổi phù hợp trước khi nhập |
| Nhận dạng chữ trang thường | PP-OCRv6, nhưng phải kiểm thử tiếng Việt riêng |
| Trang bố cục khó | PaddleOCR-VL-1.6 hoặc tuyến dự phòng tương đương |
| Chỉ mục kho nguồn | Qdrant với tìm theo ý nghĩa + tìm thưa/BM25 + hợp nhất thứ hạng |
| Mô hình biểu diễn ý nghĩa đầu tiên để thử | Qwen3-Embedding-0.6B |
| Mô hình xếp hạng lại đầu tiên để thử | Qwen3-Reranker-0.6B |
| Đường chuẩn so sánh | BGE-M3 |
| RAG đầy đủ / biên dịch tri thức | RAGFlow qua bộ chuyển tiếp |
| Tìm trong Bộ não thứ hai | QMD |
| Bộ não thứ hai | Markdown + Git |
| Đọc sâu sách dài | PageIndex sau khi đã thu hẹp phạm vi |
| Giao tiếp AI | MCP + HTTP |
| Đồ thị / trí nhớ tác tử nâng cao | chưa bật mặc định; LightRAG, Graphiti, Cognee, Mem0 chỉ thử khi có bài toán |

## Điều chỉnh quan trọng sau vòng kiểm chứng

### Qdrant không còn chỉ là “kho véc-tơ”

Qdrant hiện có thể đảm nhiệm cả tìm theo ý nghĩa, tìm thưa/BM25, hợp nhất thứ hạng và truy vấn nhiều tầng. Vì vậy bản đầu có thể đơn giản hơn:

~~~text
Qdrant
├── tìm theo ý nghĩa
└── tìm theo chữ/thưa
      ↓
hợp nhất thứ hạng
      ↓
30–50 ứng viên
      ↓
xếp hạng lại
      ↓
3–8 bằng chứng
~~~

### Qwen3-Embedding-0.6B không cố định ở 512 chiều

Thông số hiện hành cho phép tối đa 1024 chiều và có thể chọn chiều đầu ra nhỏ hơn. Nếu dùng 512 chiều thì đó là **cấu hình thử nghiệm của Thư Viện Sống**, không phải thông số gốc của mô hình.

### PageIndex có chế độ cục bộ, nhưng lớp nhiều tài liệu hiện thuộc đám mây

Kiểm chứng lại cho thấy PageIndex cục bộ có thể lập chỉ mục, truy hồi và trò chuyện trên PDF có chữ, nhưng PageIndex File System nhiều tài liệu hiện được mô tả là **tính năng đám mây**. Nhận định trước đây rằng hai khả năng này cùng có ở chế độ cục bộ là không chính xác.

Vì vậy ở bản đầu càng nên giữ nguyên chiến lược:

> **tìm rẻ trên toàn thư viện bằng hệ của Thư Viện Sống → thu hẹp → dùng PageIndex cục bộ để đọc sâu một số PDF có chữ.**

Nếu muốn dùng PageIndex Cloud cho nhiều tài liệu, phải đánh giá riêng quyền riêng tư, chi phí và phụ thuộc nhà cung cấp.

### RAGFlow Biên dịch tri thức là tính năng thật

RAGFlow hiện có Wiki, Graph, Tree, PageIndex, Mind Map, Timeline và Skills trong lớp Biên dịch tri thức. Các đầu ra này vẫn phải được xem là **sản phẩm của bộ máy bên ngoài**, không tự động trở thành Bộ não thứ hai chính thức.

### Tiếng Việt là tiêu chí kiểm thử bắt buộc của nhận dạng chữ

PP-OCRv6 có liệt kê hỗ trợ tiếng Việt, nhưng đã có báo cáo năm 2026 về thiếu ký tự tiếng Việt có dấu trong từ điển ở một thời điểm. Vì vậy phải đo trên dữ liệu thật trước khi chọn tuyến OCR sản xuất.

Nguyên tắc cuối cùng vẫn không đổi:

> **Công cụ có thể mạnh lên hoặc thay đổi, nhưng dữ liệu chuẩn và khả năng truy nguồn phải thuộc về Thư Viện Sống.**

---

# 55. Lộ trình xây dựng

> Nếu bắt đầu triển khai ngay, xem [Hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1](17-huong-dan-bat-dau-trien-khai-v0.1.md). Tài liệu đó chuyển các nguyên tắc dưới đây thành thứ tự công việc, dữ liệu thử và tiêu chí hoàn thành cụ thể.


## Giai đoạn thử nghiệm

Chọn 200–500 trang đại diện.

Đo:

- lấy chữ;
- nhận dạng chữ;
- thứ tự đọc;
- trang;
- tìm kiếm;
- trích dẫn.

---

## Bản kỹ thuật 0.1 — Nguồn và bằng chứng

Xây chắc:

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

---

## Bản kỹ thuật 0.2 — Bộ não thứ hai

Thêm:

- Markdown;
- liên kết;
- sổ khẳng định;
- QMD;
- Git.

---

## Bản kỹ thuật 0.3 — Nghiên cứu sâu

Thêm:

- không gian nghiên cứu;
- gói bằng chứng;
- đề xuất;
- một bộ ghi duy nhất;
- kiểm tra mâu thuẫn;
- tự bảo trì.

---

## Bản kỹ thuật 0.4 — Đọc sâu và điều phối

Thêm:

- PageIndex;
- RAGFlow;
- bộ chọn cách xử lý;
- các bộ chuyển tiếp.

---

## Bản kỹ thuật 0.5 — Quan hệ phức tạp

Chỉ khi có nhu cầu thực:

- đồ thị tri thức;
- LightRAG;
- Graphiti;
- các hệ trí nhớ khác.

---

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

# 56. Thứ tự ưu tiên phải giữ

Nếu buộc phải chọn thứ tự:

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

# 57. Điểm khác biệt thực sự của dự án

Nếu làm đúng, Thư Viện Sống AI không phải:

> RAGFlow + Obsidian.

Cũng không phải:

> một công cụ tìm kiếm sách.

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

# 58. Mô hình dễ nhớ nhất

Có thể coi hệ thống có hai nhân vật.

## Người thủ thư

RAG đóng vai:

> **thủ thư cực giỏi.**

Nó biết:

- sách nào;
- chương nào;
- trang nào;
- đoạn nào.

---

## Học giả

Bộ não thứ hai đóng vai:

> **học giả tích lũy hiểu biết qua nhiều lần nghiên cứu.**

Nó biết:

- vấn đề này đã nghiên cứu chưa;
- khái niệm liên hệ với gì;
- các nguồn đồng thuận ở đâu;
- các nguồn mâu thuẫn ở đâu;
- còn câu hỏi gì chưa giải quyết.

---

## Khi kết hợp

> Học giả đưa ra hiểu biết.

> Thủ thư mang bằng chứng đến kiểm tra.

Đó là mô hình tối ưu hơn nhiều so với chỉ có một trong hai.

---

# 59. Câu kết luận quan trọng nhất

Toàn bộ kiến trúc có thể rút lại thành:

> **Hãy xây một thư viện số làm trí nhớ gốc; phía trên là hệ tìm bằng chứng để tìm đúng sách, đúng chương, đúng trang; phía trên nữa là Bộ não thứ hai để giữ những gì AI đã hiểu và đã kiểm chứng. Mỗi câu hỏi chỉ cho AI đọc lượng thông tin tối thiểu cần thiết, còn mọi tri thức mới chỉ được ghi nhớ sau khi có thể truy ngược về nguồn.**

Và nếu phải nói bằng một câu ngắn hơn nữa:

> **RAG giúp tìm đúng bằng chứng. Bộ não thứ hai giúp không phải học lại từ đầu. Sách gốc luôn là trọng tài cuối cùng.**

Mục tiêu cuối cùng không phải tạo thêm một ứng dụng RAG.

Mục tiêu là:

> **xây một nền tảng tri thức có thể sống qua nhiều thế hệ AI.**