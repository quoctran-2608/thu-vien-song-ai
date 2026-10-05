# 4. Bộ não thứ hai — trí nhớ hiểu biết

## 4.1. Vì sao RAG chưa đủ?

RAG rất giỏi tìm bằng chứng nhưng mỗi lần hỏi có xu hướng phải tìm và tiêu hoá lại tài liệu.

Bộ não thứ hai giải quyết câu hỏi khác:

> “Sau nhiều lần đọc và nghiên cứu, hệ thống đã hiểu được gì và những hiểu biết đó liên hệ với nhau ra sao?”

## 4.2. Mô hình LLM Wiki

Cảm hứng quan trọng đến từ mô hình:

```text
raw/    = nguyên liệu gốc
wiki/   = tri thức AI đã biên dịch
quy tắc = hiến pháp cho AI duy trì wiki
```

Trong dự án này, tư tưởng đó được mở rộng thành một lớp có truy nguồn và kiểm toán chặt hơn.

## 4.3. Wiki không phải bản tóm tắt từng cuốn

Nếu chỉ có:

```text
Sách A → tóm tắt A
Sách B → tóm tắt B
```

thì chưa phải Bộ não thứ hai mạnh.

Bộ não thứ hai cần có các trang xuyên nguồn:

- khái niệm;
- tác giả;
- trường phái;
- so sánh;
- tranh luận;
- tổng hợp;
- câu hỏi mở;
- kết quả nghiên cứu.

Ví dụ một trang `Vô ngã.md` có thể tổng hợp từ nhiều sách và liên kết sang `Duyên khởi`, `Ngũ uẩn`, `Tánh không`.

## 4.4. Sổ khẳng định

Mỗi ý quan trọng được lưu như một khẳng định có cấu trúc:

```yaml
id: C1258
noi_dung: "..."
loai: TRICH_XUAT | SUY_LUAN | MO_HO
nguon:
  - tai_lieu: book_183
    trang: 126-128
muc_tin_cay: 0.97
```

Điều này ngăn AI trộn “điều sách nói” với “điều AI suy ra”.

## 4.5. Tự duy trì nhưng không tự bịa

Bộ não thứ hai có thể tự kiểm tra:

- liên kết hỏng;
- trang mồ côi;
- khái niệm trùng;
- khẳng định thiếu nguồn;
- mâu thuẫn giữa các trang;
- chủ đề xuất hiện nhiều nhưng chưa có trang riêng.

Nhưng khi thấy mâu thuẫn, hệ thống không được âm thầm chọn một bên và xoá bên còn lại.

## 4.6. Cập nhật gia tăng

Khi thêm ba cuốn mới vào thư viện 10.000 cuốn:

- chỉ xử lý ba cuốn mới;
- xác định các trang wiki có thể bị ảnh hưởng;
- chỉ cập nhật các trang đó;
- không đọc lại toàn bộ kho.

## 4.7. Một bộ ghi duy nhất

Nhiều tác tử có thể nghiên cứu song song, nhưng chỉ một bộ phận có quyền ghi chính thức.

```text
Tác tử A ─┐
Tác tử B ─┼→ đề xuất → kiểm tra → bộ ghi duy nhất → Git commit
Tác tử C ─┘
```

Điều này tránh xung đột và giúp mọi thay đổi phục hồi được.

## 4.8. Bộ não làm việc tạm thời

Ngoài Bộ não thứ hai lâu dài, mỗi nghiên cứu sâu nên có một không gian tạm:

```text
research/chu-de-X/
  question.md
  evidence/
  notes/
  contradictions.md
  synthesis.md
```

Chỉ kết quả đã kiểm chứng mới được đề xuất đưa vào Bộ não thứ hai.

## 4.9. QMD trong kiến trúc

QMD rất phù hợp để tìm trong wiki Markdown vì có thể kết hợp:

- tìm theo chữ;
- tìm theo ý nghĩa;
- xếp hạng lại;
- giao diện MCP.

Không nhất thiết dùng cùng chỉ mục với hàng triệu đoạn sách.
