# 4. Bộ não thứ hai — trí nhớ hiểu biết

## 4.1. Vì sao RAG chưa đủ?

RAG rất giỏi tìm nguồn, nhưng mỗi lần hỏi có thể phải tìm và tiêu hóa lại tài liệu.

Bộ não thứ hai giải quyết câu hỏi:

> **Sau nhiều lần đọc và nghiên cứu, hệ thống đã hiểu được gì?**

## 4.2. Bộ não thứ hai không phải bản tóm tắt từng sách

Nếu chỉ có:

```text
Sách A → tóm tắt A
Sách B → tóm tắt B
```

thì chưa phải một Bộ não thứ hai mạnh.

Nó cần các trang xuyên nguồn:

- khái niệm;
- tác giả;
- truyền thống;
- so sánh;
- tranh luận;
- tổng hợp;
- câu hỏi mở.

## 4.3. Cấu trúc gợi ý

```text
brain/
├── khai-niem/
├── nhan-vat/
├── tac-pham/
├── truyen-thong/
├── so-sanh/
├── tranh-luan/
├── tong-hop/
└── cau-hoi-mo/
```

## 4.4. Cấu trúc một trang tri thức

Một trang quan trọng nên phân biệt:

```text
THÔNG TIN TỪ NGUỒN

TỔNG HỢP CỦA AI

ĐIỂM MÂU THUẪN

ĐIỂM CHƯA CHẮC CHẮN

CÂU HỎI CẦN NGHIÊN CỨU THÊM

NGUỒN
```

## 4.5. Liên kết có chủ ý giữa các trang tri thức

Bộ não thứ hai không chỉ là một tập hợp các file đứng riêng lẻ. Các trang cần liên kết với nhau để biểu diễn những quan hệ mà hệ thống đã thật sự xác định.

Ví dụ:

```text
[[Vô ngã]]
[[Ngũ uẩn]]
[[Duyên khởi]]
```

Một trang `Vô-ngã.md` có thể liên kết tới `[[Ngũ uẩn]]`, `[[Duyên khởi]]`, `[[Chấp thủ]]` hoặc các trang tác giả, truyền thống và tranh luận liên quan.

Nguyên tắc:

- chỉ tạo liên kết khi có quan hệ có ý nghĩa;
- không tạo hàng loạt liên kết chỉ vì hai từ cùng xuất hiện;
- liên kết phải giúp người đọc hoặc AI lần theo mạch tri thức;
- liên kết bị hỏng phải được phát hiện trong bước tự bảo trì;
- Markdown là dữ liệu gốc, còn Obsidian hay công cụ xem đồ thị chỉ là giao diện.

Các liên kết này có thể dùng dạng `[[tên-trang]]` khi phù hợp với kho Markdown, nhưng ý nghĩa quan trọng hơn cú pháp cụ thể.

## 4.6. RAG có độ phủ rộng, Bộ não thứ hai có độ sâu

Nếu có hàng chục nghìn sách:

- tất cả có thể được số hóa và lập chỉ mục;
- Bộ não thứ hai chỉ phát triển sâu ở những chủ đề thực sự được dùng.

Không nên cho AI tiêu hóa toàn bộ thư viện ngay ngày đầu.

## 4.7. Sổ khẳng định

Một khẳng định quan trọng cần bản ghi có cấu trúc:

```text
mã
nội dung
nguồn
vị trí
cách tạo
tình trạng bằng chứng
```

### Cách tạo khẳng định

- TRÍCH_XUẤT: nguồn nói trực tiếp;
- SUY_LUẬN: AI rút ra từ bằng chứng;
- TỔNG_HỢP: AI kết hợp nhiều nguồn.

### Tình trạng bằng chứng

- ĐƯỢC_HỖ_TRỢ;
- CÓ_TRANH_LUẬN;
- HỖ_TRỢ_YẾU;
- CHƯA_ĐỦ_DỮ_LIỆU;
- CHƯA_BIẾT;
- BỊ_PHẢN_BÁC.

Hai chiều này không nên trộn thành một.

## 4.8. Phân biệt nguyên văn, bản dịch và suy luận

Tối thiểu nên tách:

1. nguyên văn nguồn;
2. bản dịch xuất bản;
3. bản dịch làm việc do AI tạo;
4. diễn đạt lại;
5. diễn giải của tác giả/học giả;
6. tổng hợp của AI.

Không được để người đọc hiểu nhầm bản dịch AI là bản dịch xuất bản.

## 4.9. Cập nhật gia tăng

Khi thêm vài tài liệu mới vào thư viện lớn:

- xử lý tài liệu mới;
- xác định các trang tri thức có thể bị ảnh hưởng;
- chỉ xem xét cập nhật các trang đó.

Không đọc lại toàn bộ thư viện.

## 4.10. Bảng kê xử lý

Một bảng kê xử lý, thường gọi là `manifest`, nên biết:

- file nào đã xử lý;
- dấu vân tay số;
- phiên bản xử lý;
- kết quả gì đã sinh ra;
- phần nào có thể bị ảnh hưởng.

## 4.11. Nhiều AI nhưng một bộ ghi

```text
AI 1 ─┐
AI 2 ─┼→ đề xuất → kiểm tra → một bộ ghi → Git
AI 3 ─┘
```

Nhiều AI được đọc và đề xuất. Chỉ một bộ phận được ghi chính thức.

## 4.12. Mỗi cập nhật phải có tính toàn vẹn

Nếu cần sửa nhiều trang, phải:

> **ghi tất cả hoặc không ghi gì.**

Không để wiki ở trạng thái nửa cũ nửa mới.

## 4.13. Tự bảo trì nhưng không tự bịa

Có thể tự kiểm tra:

- liên kết hỏng;
- trang mồ côi;
- trang trùng;
- khẳng định thiếu nguồn;
- mâu thuẫn;
- trang quá dài hoặc quá nhỏ.

Nhưng khi hai nguồn bất đồng, không được tự động xóa một bên hoặc chọn người thắng nếu chưa đủ căn cứ.

## 4.14. QMD trong kiến trúc

QMD phù hợp làm công cụ tìm trong kho Markdown của Bộ não thứ hai.

Nó không phải nơi sở hữu dữ liệu. Markdown và Git mới là phần bền lâu.
