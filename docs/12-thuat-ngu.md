# 12. Từ điển thuật ngữ

Tài liệu này ưu tiên cách nói tiếng Việt. Thuật ngữ tiếng Anh chỉ giữ khi cần tra cứu kỹ thuật.

## RAG

Viết tắt của *Retrieval-Augmented Generation*.

Trong dự án này hiểu là:

> **tìm các phần tài liệu liên quan trước rồi mới cho AI đọc và trả lời.**

## Bộ não thứ hai

Kho tri thức đã được tổng hợp, liên kết và tích lũy qua nhiều lần nghiên cứu.

## OCR

*Optical Character Recognition* — nhận dạng chữ từ ảnh hoặc trang quét.

## Embedding — biểu diễn số của ý nghĩa

Cách biến văn bản thành một dãy số đại diện tương đối cho ý nghĩa, giúp máy tìm các đoạn gần nhau về nội dung.

## Cơ sở dữ liệu véc-tơ

Hệ thống chuyên lưu các biểu diễn số và tìm những mục gần nhau.

## Tìm kiếm kết hợp

Kết hợp tìm theo chữ và tìm theo ý nghĩa.

## Xếp hạng lại

Dùng một mô hình riêng để sắp lại các kết quả tìm được sau bước tìm kiếm ban đầu.

## Chunk — đoạn tìm kiếm

Phần văn bản được chuẩn bị làm đơn vị tìm kiếm.

## MCP

Tên một chuẩn giao tiếp giúp AI gọi công cụ và dữ liệu bên ngoài theo một giao diện thống nhất.

## Khẳng định

Một phát biểu tri thức cần được theo dõi về nguồn gốc và mức độ được bằng chứng hỗ trợ.

## Bằng chứng

Đoạn nguồn cụ thể hỗ trợ hoặc phản bác một khẳng định.

## Ứng viên bằng chứng

Một kết quả tìm được đáng xem nhưng chưa qua kiểm tra đầy đủ để trở thành bằng chứng.

## Truy nguồn

Khả năng lần ngược từ kết luận về tài liệu, ấn bản, trang và đoạn gốc.

## Gói bằng chứng

Tập nhỏ gồm những bằng chứng tốt nhất, tri thức liên quan, điểm chưa chắc chắn và thông tin nguồn được đưa cho AI để suy luận.

## Không gian nghiên cứu

Bàn làm việc tạm thời cho một vấn đề cụ thể.

## Bộ ghi duy nhất

Mô hình trong đó nhiều tác tử có thể đề xuất thay đổi nhưng chỉ một bộ phận được áp dụng thay đổi chính thức.

## Bảng kê xử lý

Thường gọi là *manifest* trong tài liệu kỹ thuật.

Ghi file nào đã xử lý, dấu vân tay số, phiên bản xử lý và kết quả đã sinh ra.

## PageIndex

Tên một cách/công cụ tổ chức tài liệu theo cây để đi từ sách tới chương, mục và đoạn cần đọc.

## Đồ thị tri thức

Mạng các thực thể và quan hệ giữa chúng.

## Kiểm thử hồi quy

Chạy lại cùng một bộ câu hỏi chuẩn sau mỗi thay đổi để xem chất lượng có giảm không.

## Tác tử AI

Một tiến trình AI được giao một vai trò hoặc nhiệm vụ cụ thể, thí dụ tìm tài liệu, kiểm chứng hoặc bảo trì Bộ não thứ hai.


## BM25

Một cách tìm theo chữ, ưu tiên những từ/cụm từ có tính phân biệt cao trong tập tài liệu. Hữu ích với tên riêng, câu nguyên văn và thuật ngữ.

## RRF — hợp nhất thứ hạng đối ứng

Cách gộp nhiều danh sách kết quả tìm kiếm dựa trên thứ hạng của mỗi kết quả. Nó giúp kết hợp tìm theo chữ và tìm theo ý nghĩa mà không cần các điểm số của hai hệ phải cùng thang đo.

## Precision — độ chính xác của tập kết quả

Trong các kết quả hệ thống trả về, tỷ lệ bao nhiêu là đúng hoặc thật sự liên quan.

## Recall — tỷ lệ tìm thấy

Trong các nguồn đúng đáng lẽ phải tìm được, hệ thống tìm thấy được bao nhiêu.

**Recall@5** và **Recall@10** xem nguồn đúng có xuất hiện trong 5 hoặc 10 kết quả đầu hay không.

## MRR — thứ hạng đối ứng trung bình

Đo việc nguồn đúng xuất hiện sớm đến mức nào. Nguồn đúng đứng càng gần đầu danh sách thì điểm càng cao.

## nDCG — chất lượng thứ hạng có trọng số

Đánh giá thứ tự kết quả khi các kết quả có nhiều mức độ liên quan khác nhau, không chỉ đúng/sai tuyệt đối.

## F1 — điểm cân bằng

Một chỉ số kết hợp Precision và Recall để tránh tối ưu một phía mà làm phía còn lại quá kém.
