# 3. Hệ tìm bằng chứng, RAG và đọc phân tầng

## 3.1. RAG là gì?

RAG là viết tắt của *Retrieval-Augmented Generation*.

Trong dự án này có thể hiểu đơn giản:

> **tìm phần tài liệu thích hợp trước, rồi mới cho AI đọc và trả lời.**

RAG không đồng nghĩa với cơ sở dữ liệu véc-tơ.

## 3.2. Tìm theo chữ

Mạnh với:

- tên người;
- tên sách;
- thuật ngữ;
- câu nguyên văn;
- mã tài liệu;
- cụm từ hiếm.

## 3.3. Tìm theo ý nghĩa

Hệ thống biến văn bản thành một dãy số đại diện tương đối cho ý nghĩa, thường gọi là *embedding*.

Nhờ vậy hai câu dùng từ khác nhau nhưng nói cùng một ý vẫn có thể tìm thấy nhau.

## 3.4. Tìm kiếm kết hợp

```text
tìm theo chữ ─┐
              ├→ hợp nhất kết quả
tìm theo ý ───┘
              ↓
         xếp hạng lại
              ↓
         vài đoạn tốt nhất
```

Không nên dùng duy nhất một phương pháp.

## 3.5. Xếp hạng lại

Bộ xếp hạng lại đọc câu hỏi và một danh sách nhỏ các đoạn ứng viên để sắp lại chính xác hơn.

Mục tiêu là để mô hình AI lớn cuối cùng chỉ đọc một số rất ít đoạn tốt.

## 3.6. Kết quả tìm được chưa phải bằng chứng

Luồng đúng:

```text
kết quả tìm được
↓
ứng viên bằng chứng
↓
kiểm tra nguồn, vị trí, ngữ cảnh
↓
bằng chứng đã xác minh
```

Ở chế độ hỏi đáp thường, bước kiểm tra có thể nhẹ. Ở chế độ nghiên cứu nghiêm ngặt, bước này phải chặt.

## 3.7. Chia đoạn theo cấu trúc

Không cắt máy móc theo số ký tự.

Ưu tiên:

- tiêu đề;
- mục;
- đoạn;
- ranh giới tự nhiên của nội dung.

Mỗi đoạn nên mang theo đường dẫn:

```text
Tên sách
> Phần
> Chương
> Mục
```

## 3.8. Tóm tắt phân tầng

Có thể xây:

```text
tóm tắt sách
↓
tóm tắt chương
↓
mô tả mục
↓
đoạn nguồn
```

Câu hỏi tổng quát đi từ trên xuống. Câu hỏi nguyên văn có thể đi thẳng tới bằng chứng.

## 3.9. Đọc theo độ sâu thích ứng

### Câu đơn giản

Ưu tiên Bộ não thứ hai.

### Cần kiểm chứng

Đọc vài đoạn nguồn.

### Cần đọc một cuốn

Đi qua mục lục và chương.

### Cần đọc sâu

Dùng cấu trúc cây hoặc PageIndex.

### Cần nghiên cứu lớn

Tạo không gian nghiên cứu riêng.

Nguyên tắc:

> **AI chỉ đọc sâu đến mức nhiệm vụ thật sự cần.**

## 3.10. PageIndex đặt ở đâu?

```text
toàn thư viện
↓
hệ tìm kiếm chọn vài cuốn
↓
PageIndex
↓
đi theo cây chương/mục
↓
đọc sâu
```

Không nên mặc định dùng PageIndex để duyệt toàn bộ thư viện.

## 3.11. Hai chỉ mục riêng

### Chỉ mục kho sách

Giữ bằng chứng.

### Chỉ mục Bộ não thứ hai

Giữ tri thức đã tiêu hóa.

Câu “ta biết gì?” và câu “ta biết điều đó từ đâu?” đi theo hai đường khác nhau.

## 3.12. Gói bằng chứng

Gói bằng chứng là tập nhỏ mà AI cuối cùng đọc, có thể gồm:

- câu hỏi;
- phạm vi;
- một ít tri thức liên quan;
- 4–8 bằng chứng tốt nhất;
- nguồn và vị trí;
- bằng chứng phản bác nếu có;
- điểm chưa chắc chắn.

Gói bằng chứng vừa giảm lượng chữ phải đọc, vừa tạo ranh giới rõ giữa hệ tìm kiếm và hệ suy luận.

## 3.13. Kinh tế lượng chữ đưa cho AI

Cách ngây thơ có thể đưa hàng chục đoạn, tức hàng chục nghìn đơn vị chữ.

Phương án tốt hơn chỉ đưa vài bằng chứng tốt nhất và một lượng nhỏ tri thức liên quan.

Không có tỷ lệ tiết kiệm cố định cho mọi trường hợp, nhưng nguyên tắc là:

> **đừng bắt mô hình lớn đọc những gì có thể loại bỏ từ trước.**
