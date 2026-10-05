# 11. Các quyết định kiến trúc

## QĐ-001 — Nguồn gốc bất biến

**Quyết định:** không sửa file nguồn và text thô của một phiên bản xử lý.

**Lý do:** mọi kết quả AI cần có thể kiểm toán và tái tạo.

## QĐ-002 — Không lấy RAGFlow làm lõi dữ liệu

**Quyết định:** RAGFlow là adapter/động cơ, không phải nguồn dữ liệu duy nhất.

**Lý do:** tránh khoá công nghệ và bảo vệ khả năng thay thế lâu dài.

## QĐ-003 — Hai trí nhớ tách biệt

**Quyết định:** corpus index và brain index là hai lớp riêng.

**Lý do:** bằng chứng và hiểu biết có vòng đời, độ tin cậy và cách truy hồi khác nhau.

## QĐ-004 — OCR theo tầng

**Quyết định:** chỉ OCR trang cần thiết, từ công cụ nhẹ đến mạnh.

**Lý do:** giảm chi phí và giảm lỗi do OCR không cần thiết.

## QĐ-005 — Hybrid retrieval + reranking

**Quyết định:** kết hợp từ khóa và ý nghĩa, sau đó xếp hạng lại.

**Lý do:** sách có cả câu hỏi nguyên văn và câu hỏi ngữ nghĩa; một phương pháp đơn lẻ không đủ.

## QĐ-006 — Gói bằng chứng nhỏ

**Quyết định:** AI lớn chỉ đọc số ít đoạn tốt nhất và tri thức liên quan.

**Lý do:** tiết kiệm token, giảm nhiễu và tăng khả năng kiểm chứng.

## QĐ-007 — Sổ khẳng định

**Quyết định:** mọi tri thức quan trọng phân loại TRICH_XUAT/SUY_LUAN/MO_HO.

**Lý do:** chống trôi nguồn và chống AI biến suy luận thành sự kiện.

## QĐ-008 — Single Writer

**Quyết định:** nhiều tác tử được đề xuất, chỉ một bộ ghi áp dụng thay đổi chính thức.

**Lý do:** tránh xung đột và bảo đảm giao dịch có thể phục hồi.

## QĐ-009 — Không graph toàn kho ở bản đầu

**Quyết định:** graph là tính năng bật theo use case.

**Lý do:** chi phí cao, độ phức tạp lớn, chưa chắc tăng chất lượng cho phần lớn câu hỏi.

## QĐ-010 — Mọi thay động cơ phải benchmark

**Quyết định:** không thay model chỉ vì mới hơn.

**Lý do:** dữ liệu thực của kho sách là tiêu chuẩn quyết định.
