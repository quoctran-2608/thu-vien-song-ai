# Tóm tắt một trang

> Đây là bản đọc nhanh. Nếu muốn hiểu đầy đủ, đọc [Tài liệu tổng thể phiên bản 1.0](00-TAI-LIEU-TONG-THE-V1.0.md).

## Mục tiêu

Xây một nền tảng giúp AI:

- tìm đúng tài liệu, chương, mục, trang và đoạn;
- tổng hợp nhiều nguồn;
- phân biệt nguồn với suy luận;
- ghi nhớ kết quả nghiên cứu tốt;
- luôn quay lại được bằng chứng;
- giảm lượng chữ phải đưa cho mô hình AI ở mỗi câu hỏi.

## Bốn lớp chính

```text
KHO NGUỒN GỐC
↓
KHO DỮ LIỆU CHUẨN + HỆ TÌM BẰNG CHỨNG
↓
BỘ NÃO THỨ HAI
↓
KHÔNG GIAN NGHIÊN CỨU
```

## Hai loại trí nhớ

**Trí nhớ bằng chứng** trả lời:

> Điều này lấy từ sách nào, trang nào, đoạn nào?

**Trí nhớ hiểu biết** trả lời:

> Sau nhiều lần đọc và nghiên cứu, hệ thống đã hiểu được gì?

## Nguyên tắc cốt lõi

- AI không phải là nguồn.
- Nguồn gốc phải được giữ nguyên.
- Một kết quả tìm được chưa tự động là bằng chứng.
- Một trích dẫn có thật chưa chắc chứng minh được khẳng định.
- Không đủ bằng chứng là một kết quả hợp lệ.
- Dữ liệu chuẩn phải độc lập với RAGFlow, QMD, PageIndex, Qdrant và mọi mô hình AI.
- Nhiều AI có thể nghiên cứu nhưng chỉ một bộ phận được ghi chính thức vào Bộ não thứ hai.
- Công cụ mới phải được kiểm thử trên dữ liệu thật trước khi thay công cụ cũ.

## Cách AI đọc

AI không đọc toàn bộ thư viện.

Nó đọc theo độ sâu thích ứng:

```text
câu đơn giản
→ vài trang tri thức

cần kiểm chứng
→ vài đoạn nguồn

cần đọc sâu
→ chương / mục

cần nghiên cứu lớn
→ không gian nghiên cứu riêng
```

## Một câu để nhớ

> **RAG giúp tìm đúng bằng chứng. Bộ não thứ hai giúp không phải học lại từ đầu. Nguồn gốc luôn là trọng tài cuối cùng.**
