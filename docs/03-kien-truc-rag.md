# 3. Kiến trúc RAG — trí nhớ bằng chứng

## 3.1. RAG là gì trong dự án này?

RAG là cơ chế **tìm những phần tài liệu liên quan trước, rồi mới đưa phần nhỏ đó cho AI đọc**.

Trong dự án này, RAG không chỉ là vector search. Nó gồm nhiều bước.

## 3.2. Tìm theo chữ + tìm theo ý nghĩa

### Tìm theo chữ

Mạnh với:

- tên người;
- thuật ngữ;
- câu nguyên văn;
- tên sách;
- số hiệu;
- cụm từ hiếm.

### Tìm theo ý nghĩa

Mạnh khi câu hỏi và tài liệu dùng từ khác nhau nhưng nói cùng một ý.

Ví dụ “buông chấp cái tôi” có thể liên quan đến đoạn dùng từ “không đồng hoá với ngã”.

## 3.3. Tìm kiếm kết hợp

Luồng chuẩn:

```text
Câu hỏi
  ↓
Tìm theo chữ ─┐
              ├→ hợp nhất thứ hạng → ứng viên
Tìm ý nghĩa ──┘
                         ↓
                   xếp hạng lại
                         ↓
                   3–6 đoạn tốt
```

Không đưa toàn bộ 30–50 ứng viên cho mô hình lớn.

## 3.4. Xếp hạng lại

Bộ xếp hạng lại đọc câu hỏi và một danh sách nhỏ các đoạn ứng viên để đánh giá mức liên quan chính xác hơn.

Đề xuất: Qwen3-Reranker-0.6B hoặc mô hình tương đương chạy tại máy.

Đây là khoản tính toán nhỏ nhưng tiết kiệm rất nhiều context về sau.

## 3.5. Chunking — chia đoạn theo cấu trúc

Không cắt máy móc cứ 1.000 ký tự.

Ưu tiên:

- ranh giới đoạn;
- tiêu đề;
- mục;
- tiểu mục;
- ranh giới trang khi cần trích dẫn.

Một chunk nên mang theo đường dẫn ngữ cảnh:

```text
Tên sách > Phần > Chương > Mục
```

Thông thường có thể thử khoảng 300–700 token, nhưng con số phải được kiểm chứng bằng bộ đánh giá thực tế.

## 3.6. Tóm tắt nhiều tầng

Mỗi tài liệu có thể có:

- tóm tắt sách;
- tóm tắt chương;
- mô tả mục;
- đoạn gốc.

Câu hỏi tổng quát đi từ trên xuống; câu hỏi nguyên văn đi thẳng vào tầng bằng chứng.

## 3.7. Gói bằng chứng

Sau truy hồi, hệ thống tạo một gói nhỏ gồm:

- câu hỏi;
- 3–8 đoạn tốt nhất;
- tên sách/chương/trang;
- vài ghi chú từ Bộ não thứ hai nếu cần;
- cờ độ tin cậy.

Mục tiêu là để mô hình lớn đọc khoảng vài nghìn token thay vì hàng chục nghìn token.

## 3.8. PageIndex đặt ở đâu?

PageIndex phù hợp sau khi đã chọn được một vài cuốn sách:

```text
Toàn thư viện
→ RAG chọn 3 cuốn
→ PageIndex đi theo mục lục/cây của từng cuốn
→ tìm chương/mục
→ đọc sâu
```

Không dùng PageIndex làm lớp tìm kiếm toàn kho mặc định vì có thể tăng chi phí suy luận.

## 3.9. RAGFlow đặt ở đâu?

RAGFlow là một động cơ rất mạnh để:

- nhập tài liệu;
- truy hồi;
- xếp hạng;
- dẫn nguồn;
- tác tử tìm kiếm;
- biên dịch tri thức.

Nhưng trong kiến trúc này, RAGFlow là một **bộ chuyển tiếp cắm thêm**, không phải nơi giữ dữ liệu chuẩn duy nhất.
