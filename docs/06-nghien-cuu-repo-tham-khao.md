# 6. Vai trò các công cụ và dự án tham khảo

> Tài liệu này chỉ ghi **vai trò kiến trúc dự kiến** và những gì đáng học. Các thông tin dễ thay đổi như phiên bản mới nhất, số sao, tính năng hiện hành và giấy phép phải được kiểm chứng lại ở vòng rà nguồn bên ngoài trước khi chốt.

## 6.1. Nguyên tắc sử dụng dự án bên ngoài

Không bê nguyên một dự án lớn về làm “chủ” hệ thống.

Thay vào đó:

- học điểm mạnh;
- dùng qua giao diện riêng;
- giữ dữ liệu chuẩn ở Thư Viện Sống;
- có khả năng thay thế công cụ về sau.

## 6.2. Docling

Vai trò dự kiến:

> máy đọc và chuẩn hóa tài liệu có cấu trúc.

Điểm đáng học:

- bảo tồn bố cục;
- thứ tự đọc;
- biểu diễn tài liệu có cấu trúc;
- xử lý nhiều định dạng.

Quyết định:

- có thể dùng làm máy đọc mặc định;
- không để Docling sở hữu dữ liệu chuẩn.

## 6.3. PaddleOCR

Vai trò:

> nhận dạng chữ cho trang ảnh.

Điểm đáng học:

- dùng mô hình nhẹ cho trang dễ;
- dùng mô hình hiểu bố cục mạnh hơn cho trang khó;
- xử lý theo tầng thay vì dùng công cụ nặng cho mọi trang.

Quyết định:

- chỉ dùng khi trang thật sự cần nhận dạng chữ.

## 6.4. RAGFlow

Vai trò dự kiến:

- quản lý và tìm tài liệu;
- truy hồi;
- xếp hạng;
- dẫn nguồn;
- tác tử tìm kiếm;
- các khả năng biên dịch tri thức nếu phù hợp.

Kiến trúc sử dụng:

```text
Thư Viện Sống
↓
bộ chuyển tiếp
↓
RAGFlow
```

Thư Viện Sống đưa vào dữ liệu chuẩn hoặc các đoạn đã chuẩn hóa, nhận lại các ứng viên, điểm xếp hạng và tham chiếu.

Quyết định quan trọng:

> **RAGFlow không phải nguồn dữ liệu chính.**

Nếu xóa RAGFlow và dựng lại, hệ thống vẫn phải sống.

## 6.5. Qdrant

Vai trò dự kiến:

> kho chuyên lưu và tìm các biểu diễn số của đoạn văn.

Quyết định:

- là bộ máy tìm theo ý nghĩa;
- có thể thay thế;
- dữ liệu véc-tơ không phải nguồn chân lý.

## 6.6. QMD

Vai trò dự kiến:

> tìm trong kho Markdown của Bộ não thứ hai.

Phù hợp với:

- tìm theo chữ;
- tìm theo ý nghĩa;
- xếp hạng lại;
- giao tiếp với AI.

Quyết định:

- dùng cho Bộ não thứ hai;
- không mặc định dùng làm chỉ mục cho hàng triệu đoạn sách.

## 6.7. PageIndex

Vai trò:

> đọc sâu tài liệu dài theo cấu trúc cây.

Vị trí:

```text
toàn thư viện
↓
RAG chọn vài tài liệu
↓
PageIndex
↓
chương / mục liên quan
↓
đọc sâu
```

Không phụ thuộc vào PageIndex cho bước chọn tài liệu toàn thư viện.

## 6.8. claude-obsidian

Những tư tưởng đáng học:

- nguồn sống lâu hơn bản tóm tắt;
- dữ liệu người dùng sở hữu;
- mỗi khẳng định phải biết dựa vào đâu;
- thay đổi phải kiểm toán được;
- nhiều tác tử có thể tạo đề xuất nhưng áp dụng thay đổi cần được kiểm soát;
- wiki vẫn hữu ích ngay cả khi không còn tác tử AI.

Quyết định:

- học mạnh về kiến trúc Bộ não thứ hai;
- không coi đây là bộ máy nhập liệu công nghiệp cho kho sách cực lớn.

## 6.9. obsidian-wiki và các mô hình wiki do AI duy trì

Điểm đáng học:

- nhập nguồn rồi biên dịch thành tri thức;
- liên kết Markdown;
- cập nhật theo phần thay đổi;
- phát hiện trùng;
- phát hiện mâu thuẫn;
- phát hiện nội dung trôi khỏi nguồn.

Quyết định:

- dùng làm hình mẫu cho trình duy trì Bộ não thứ hai.

## 6.10. Hermes Agent và kiểu “wiki do AI biên dịch”

Điểm đáng học:

> thông tin đã được tiêu hóa có thể được biên dịch một lần thành wiki thay vì mỗi câu hỏi đều tiêu hóa lại toàn bộ nguồn.

Quyết định:

- học cách đóng gói quy trình này thành năng lực tác tử;
- vẫn giữ nguồn gốc làm trọng tài.

## 6.11. Cognee

Điểm đáng học:

- trí nhớ lâu dài của tác tử;
- tư tưởng ghi nhớ, nhớ lại, cải thiện, quên;
- biến phiên làm việc thành trí nhớ lâu dài.

Quyết định:

- chưa đưa vào lõi phiên bản đầu;
- tránh tạo quá nhiều kho dữ liệu trùng chức năng;
- có thể xây giao diện của mình để sau này cắm Cognee hoặc công cụ tương đương.

## 6.12. LightRAG

Điểm đáng học:

> kết hợp tìm kiếm với đồ thị quan hệ.

Quyết định:

- không xây đồ thị toàn thư viện ở bản đầu;
- chỉ bật cho những miền thật sự cần truy vấn quan hệ.

## 6.13. Graphiti

Điểm đáng học:

> mô hình hóa sự thật và quan hệ thay đổi theo thời gian.

Phù hợp hơn với:

- lịch sử quyết định;
- trạng thái dự án;
- ghi chú nghiên cứu thay đổi;
- dữ liệu thời sự.

Không phải ưu tiên cho phần lớn sách bất biến.

## 6.14. Mem0

Vai trò tham khảo:

> trí nhớ lâu dài cho tác tử và người dùng.

Không phải lõi kho bằng chứng sách.

## 6.15. Khoj

Vai trò tham khảo:

- trải nghiệm “bộ não thứ hai” có thể dùng ngay;
- hỏi đáp nhiều loại tài liệu;
- tác tử và nghiên cứu.

Quyết định:

- tham khảo trải nghiệm sản phẩm;
- không thay thế mô hình dữ liệu chuẩn riêng.

## 6.16. Kết luận

Không repo nào nên được lấy nguyên làm toàn bộ Thư Viện Sống.

Cách hợp lý hơn:

```text
công cụ đọc / nhận dạng chữ
↓
KHO DỮ LIỆU CHUẨN CỦA MÌNH
↓
hệ tìm bằng chứng + Bộ não thứ hai + đọc sâu
↓
gói bằng chứng
↓
AI
```

Các dự án bên ngoài là các bộ máy chuyên môn có thể thay thế.
