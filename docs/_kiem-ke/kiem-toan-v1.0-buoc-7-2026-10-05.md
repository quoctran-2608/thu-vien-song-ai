# Kiểm toán tài liệu phiên bản 1.0 — Bước 7

**Ngày kiểm toán: 05/10/2026**

Mục tiêu của vòng này là đọc repo như một người hoàn toàn mới, không dựa vào lịch sử trò chuyện.

## Phạm vi

Đã rà toàn bộ cấu trúc repo, 24 file Markdown có trước khi bổ sung Bước 7, tài liệu tổng thể, README, tài liệu phiên bản, quy tắc tác tử, lộ trình, mô hình dữ liệu, tài liệu công cụ và bảng kiểm bảo toàn ý tưởng.

Trước khi sửa đã kiểm tra cơ học 28 liên kết Markdown nội bộ và không thấy liên kết hỏng.

Sau khi bổ sung/sửa tài liệu ở Bước 7, đã kiểm tra lại **43 liên kết nội bộ**.

**Kết quả cuối: 0 liên kết nội bộ bị hỏng.**

## Điểm mạnh đã đạt

- Có một tài liệu tổng thể đủ dài để đọc liền mạch.
- README chỉ đóng vai trò cửa vào, không cố nhồi toàn bộ kiến trúc.
- Các nguyên tắc cốt lõi nhất quán giữa README, tài liệu tổng thể và AGENTS.md.
- Mô hình nguồn → dữ liệu chuẩn → tìm bằng chứng → Bộ não thứ hai → nghiên cứu được diễn đạt nhất quán.
- Công cụ bên ngoài đã được kiểm chứng riêng và tách khỏi quyết định kiến trúc.
- Có bảng kiểm để ngăn mất ý tưởng khi sửa tài liệu.
- Có lộ trình kỹ thuật theo các bản 0.x.

## Vấn đề phát hiện và cách xử lý

### 1. “v1.0” có thể bị hiểu nhầm

Repo dùng v1.0 cho **phiên bản tài liệu/đặc tả**, trong khi lộ trình cũng có **phần mềm sản xuất 1.0**.

Đã quyết định làm rõ:

- “tài liệu/đặc tả v1.0” = mốc nghiên cứu hiện tại;
- “phần mềm sản xuất 1.0” = mốc tương lai;
- nhánh v1.0 hiện dùng làm mốc tài liệu, không phải bằng chứng rằng phần mềm đã đạt bản sản xuất.

### 2. Trạng thái công khai của repo chưa được ghi rõ

Repo hiện đang ở chế độ **public**, nhưng THONG_TIN_REPO.md trước đó chỉ ghi khuyến nghị “nếu nội bộ thì nên riêng tư”.

Đã sửa tài liệu để nói rõ trạng thái hiện tại và ranh giới:

- repo công khai chỉ nên chứa kiến trúc, tài liệu, mã có thể công khai;
- sách, tài liệu có bản quyền hoặc dữ liệu nội bộ không được đưa vào repo công khai này.

### 3. Kỹ sư mới chưa có “điểm bắt đầu ngày đầu tiên”

Lộ trình cho biết phải xây gì ở từng phiên bản nhưng chưa đủ chi tiết để bắt đầu thực thi.

Đã bổ sung:

> [Hướng dẫn bắt đầu triển khai bản kỹ thuật 0.1](../17-huong-dan-bat-dau-trien-khai-v0.1.md)

Tài liệu này quy định:

- tập dữ liệu thử;
- kho nguồn;
- mô hình dữ liệu tối thiểu;
- tuyến nhập;
- tìm kiếm;
- bộ câu hỏi chuẩn;
- giao diện tối thiểu;
- tiêu chí hoàn thành.

### 4. Một số đoạn sau Bước 6 dùng tiếng Anh quá dày

Các từ như dense, sparse, benchmark, SDK, model card, File System xuất hiện trong phần kiểm chứng công cụ.

Đã sửa:

- giữ tên riêng và ký hiệu thật sự cần thiết;
- đổi phần diễn giải về tiếng Việt;
- thuật ngữ bắt buộc phải có chú thích tiếng Việt.

### 5. Các chỉ số đánh giá chưa được giải thích đủ dễ hiểu

Các tên Recall@5, MRR, nDCG, Precision, F1 cần được diễn giải bằng tiếng Việt thay vì chỉ liệt kê.

Đã bổ sung giải thích trong tài liệu đánh giá và từ điển thuật ngữ.

### 6. Giấy phép của chính repo — đã xử lý ở Bước 8

Tại thời điểm Bước 7, repo chưa có file LICENSE.

Ở Bước 8, repo đã được chốt dùng **Apache License 2.0** cho nội dung gốc do dự án tạo, kèm `NOTICE` để làm rõ nội dung bên thứ ba vẫn giữ giấy phép và bản quyền riêng.

### 7. Infographic thu nhỏ — đã xử lý ở Bước 8

Tại thời điểm Bước 7, ảnh `assets/infographic-rag-second-brain.png` chỉ có kích thước **200 × 283 pixel**, khoảng **6,8 KB**.

Ở Bước 8, ảnh đã được thay bằng bản **280 × 396 pixel**, khoảng **8,7 KB**. Bản này rõ hơn đáng kể nhưng vẫn đủ nhẹ cho README.

## Những điểm không thay đổi

Vòng kiểm toán không tìm thấy lý do để thay đổi các quyết định nền tảng sau:

- nguồn bất biến;
- kho dữ liệu chuẩn thuộc về mình;
- RAG/bộ tìm kiếm giữ bằng chứng;
- Bộ não thứ hai giữ hiểu biết;
- kết quả tìm được chưa phải bằng chứng;
- cập nhật Bộ não thứ hai phải qua đề xuất và một bộ ghi;
- đọc theo độ sâu thích ứng;
- đồ thị là tùy chọn;
- công cụ bên ngoài phải thay được.

## Kết luận

Sau Bước 7, repo đã chuyển từ trạng thái:

> **“đầy đủ về nghiên cứu nhưng người mới vẫn cần suy ra cách bắt đầu”**

sang mục tiêu:

> **“người mới đọc được, hiểu trạng thái hiện tại, biết tài liệu nào cần đọc và biết cách bắt đầu bản kỹ thuật 0.1 mà không phá kiến trúc.”**

Điểm lớn còn chưa tự động giải quyết là **giấy phép của chính repo**, vì cần quyết định của chủ sở hữu.
