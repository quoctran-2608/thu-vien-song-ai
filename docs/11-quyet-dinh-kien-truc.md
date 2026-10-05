# 11. Các quyết định kiến trúc quan trọng

Tài liệu này không chỉ ghi “chọn gì” mà còn ghi **vì sao** để các phiên bản sau không vô tình quay lại phương án đã loại bỏ.

## QĐ-001 — Nguồn gốc bất biến

**Chọn:** không sửa file nguồn và văn bản thô của một phiên bản xử lý.

**Vì sao:** mọi kết quả phải kiểm toán và tái tạo được.

## QĐ-002 — Dữ liệu chuẩn thuộc về Thư Viện Sống

**Chọn:** RAGFlow, Qdrant, QMD, PageIndex và mô hình AI chỉ là bộ máy.

**Vì sao:** tránh khóa công nghệ và bảo vệ khả năng sống lâu dài.

**Tiêu chuẩn kiểm tra:** xóa một bộ máy và dựng lại không làm mất tri thức cốt lõi.

## QĐ-003 — Hai loại trí nhớ tách biệt

**Chọn:** kho bằng chứng và Bộ não thứ hai dùng hai lớp dữ liệu/chỉ mục khác nhau.

**Vì sao:** “ta biết gì” và “ta biết từ đâu” là hai câu hỏi khác nhau.

## QĐ-004 — Không nhận dạng chữ toàn bộ PDF

**Chọn:** quyết định theo từng trang.

**Vì sao:** giảm chi phí, giảm lỗi và giữ chất lượng chữ gốc khi PDF đã có lớp chữ tốt.

## QĐ-005 — Tìm kiếm kết hợp

**Chọn:** tìm theo chữ + theo ý nghĩa + xếp hạng lại.

**Vì sao:** tên riêng, câu nguyên văn và khái niệm diễn đạt khác nhau cần các cách tìm khác nhau.

## QĐ-006 — Chia đoạn theo cấu trúc

**Chọn:** ưu tiên chương/mục/đoạn tự nhiên.

**Không chọn:** cắt mù theo số ký tự.

**Vì sao:** giữ ngữ cảnh và giúp truy nguồn tốt hơn.

## QĐ-007 — Đọc theo độ sâu thích ứng

**Chọn:** chỉ đọc sâu đến mức câu hỏi cần.

**Vì sao:** giảm lượng chữ và tránh nhiễu.

## QĐ-008 — Gói bằng chứng nhỏ

**Chọn:** mô hình AI cuối chỉ đọc số ít bằng chứng tốt nhất cùng một ít tri thức liên quan.

**Vì sao:** tiết kiệm chi phí và tăng khả năng kiểm chứng.

## QĐ-009 — Kết quả tìm được chưa phải bằng chứng

**Chọn:** có cửa kiểm tra giữa tìm kiếm và bằng chứng.

**Vì sao:** đoạn gần nghĩa chưa chắc hỗ trợ kết luận.

## QĐ-010 — Sổ khẳng định

**Chọn:** tách cách tạo khẳng định với tình trạng bằng chứng.

**Vì sao:** tránh biến suy luận thành sự kiện.

## QĐ-011 — Nghiên cứu tạm không ghi thẳng vào Bộ não thứ hai

**Chọn:** nghiên cứu → kiểm chứng → đề xuất → ghi chính thức.

**Vì sao:** bảo vệ trí nhớ lâu dài khỏi kết luận chưa chắc chắn.

## QĐ-012 — Một bộ ghi duy nhất

**Chọn:** nhiều tác tử có thể đề xuất, chỉ một bộ phận áp dụng thay đổi.

**Vì sao:** tránh xung đột và giúp kiểm toán.

## QĐ-013 — Cập nhật có tính toàn vẹn

**Chọn:** ghi toàn bộ hoặc không ghi.

**Vì sao:** không để wiki ở trạng thái nửa cũ nửa mới.

## QĐ-014 — Không xây đồ thị toàn kho ở bản đầu

**Chọn:** đồ thị là khả năng bật theo bài toán.

**Vì sao:** chi phí và độ phức tạp cao trong khi nhiều câu hỏi không cần.

## QĐ-015 — Second Brain phát triển theo nhu cầu

**Chọn:** lập chỉ mục rộng, tiêu hóa sâu có chọn lọc.

**Vì sao:** không lãng phí chi phí đọc hàng chục nghìn sách chưa bao giờ được dùng.

## QĐ-016 — Không tìm thấy không đồng nghĩa không tồn tại

**Chọn:** kết quả âm phải ghi phạm vi đã tìm.

**Vì sao:** không thể biến giới hạn của corpus thành khẳng định tuyệt đối.

## QĐ-017 — Công cụ mới phải được kiểm thử

**Chọn:** thay đổi dựa trên bộ kiểm thử của dữ liệu thật.

**Vì sao:** “mới hơn” hoặc “mạnh hơn trên bảng xếp hạng chung” chưa chắc tốt hơn cho thư viện này.

## QĐ-018 — Không dùng huấn luyện lại mô hình để thay RAG

**Chọn:** kiến thức sách nằm trong kho có truy nguồn.

**Vì sao:** huấn luyện lại không giải quyết tốt yêu cầu trang, ấn bản và bằng chứng cụ thể.
