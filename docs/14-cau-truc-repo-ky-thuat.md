# 14. Cấu trúc repo kỹ thuật

Tài liệu này phục hồi phần từng bị thiếu nhiều nhất: **hệ thống thật sẽ được chia thành các mô-đun nào và ranh giới trách nhiệm của chúng ra sao**.

Mục tiêu là xây một repo điều phối, không phải chép mã nguồn của mọi dự án bên ngoài vào cùng một nơi.

## 14.1. Cấu trúc đề xuất

```text
thu-vien-song-ai/
│
├── apps/
│   ├── web/
│   ├── cli/
│   └── mcp-server/
│
├── core/
│   ├── models/
│   ├── provenance/
│   ├── permissions/
│   ├── events/
│   └── config/
│
├── ingest/
│   ├── router/
│   ├── dedup/
│   ├── parsers/
│   │   ├── docling/
│   │   ├── epub/
│   │   └── calibre/
│   ├── ocr/
│   │   ├── paddleocr/
│   │   └── fallback/
│   └── cleaner/
│
├── corpus/
│   ├── works/
│   ├── editions/
│   ├── sections/
│   ├── pages/
│   ├── blocks/
│   └── chunks/
│
├── retrieval/
│   ├── lexical/
│   ├── semantic/
│   ├── reranker/
│   ├── hybrid/
│   └── adapters/
│       ├── ragflow/
│       └── pageindex/
│
├── brain/
│   ├── compiler/
│   ├── claims/
│   ├── linker/
│   ├── contradictions/
│   ├── dedup/
│   ├── lint/
│   └── markdown/
│
├── workspace/
│   ├── research/
│   └── evidence-packs/
│
├── agents/
│   ├── librarian/
│   ├── researcher/
│   ├── brain-maintainer/
│   └── verifier/
│
├── graph/
│   ├── interface/
│   ├── lightrag/
│   └── graphiti/
│
├── eval/
│   ├── ocr/
│   ├── retrieval/
│   ├── reranking/
│   ├── page-routing/
│   ├── citations/
│   ├── synthesis/
│   ├── brain/
│   └── regression/
│
├── vault/
│   ├── inbox/
│   ├── sources/
│   ├── brain/
│   └── _meta/
│
└── docker/
```

## 14.2. `apps/` — điểm vào của con người và AI

### `web/`

Giao diện web dành cho người dùng.

### `cli/`

Công cụ dòng lệnh cho xử lý hàng loạt, kiểm tra và quản trị.

### `mcp-server/`

Máy chủ MCP — giao diện chuẩn để AI gọi các khả năng của Thư Viện Sống.

Không đặt logic nghiệp vụ quan trọng trực tiếp trong các ứng dụng này. Chúng chỉ gọi các lớp bên dưới.

## 14.3. `core/` — luật của hệ thống

### `models/`

Các mô hình dữ liệu cốt lõi:

- tác phẩm;
- ấn bản;
- trang;
- bằng chứng;
- khẳng định;
- trang tri thức;
- hồ sơ nghiên cứu.

### `provenance/`

Truy nguồn:

- nguồn nào;
- phiên bản nào;
- xử lý bằng công cụ gì;
- khẳng định dựa trên bằng chứng nào.

### `permissions/`

Quyền đọc, quyền đề xuất và quyền ghi.

### `events/`

Các sự kiện như:

- tài liệu mới;
- xử lý xong;
- trang tri thức có thể bị ảnh hưởng;
- đề xuất đã được duyệt.

### `config/`

Cấu hình hệ thống, không gắn cứng các lựa chọn có thể thay đổi vào mã lõi.

## 14.4. `ingest/` — nhập tài liệu

### `router/`

Quyết định luồng xử lý:

```text
PDF chữ?
PDF scan?
EPUB?
MOBI?
định dạng khác?
```

### `dedup/`

Phát hiện:

- file trùng tuyệt đối;
- tài liệu gần trùng;
- ấn bản đã biết.

### `parsers/`

Các bộ chuyển tiếp tới Docling, bộ đọc EPUB, Calibre và công cụ khác.

### `ocr/`

Nhận dạng chữ cho những trang cần thiết.

### `cleaner/`

Chuẩn hóa văn bản nhưng không phá văn bản thô.

## 14.5. `corpus/` — kho dữ liệu chuẩn

Đây là trái tim của repo.

```text
works/
editions/
sections/
pages/
blocks/
chunks/
```

Các công cụ tìm kiếm bên ngoài có thể bị xóa và xây lại từ lớp này.

## 14.6. `retrieval/` — hệ tìm bằng chứng

### `lexical/`

Tìm theo chữ, cụm từ, mã tài liệu.

### `semantic/`

Tìm theo ý nghĩa.

### `reranker/`

Xếp hạng lại các ứng viên.

### `hybrid/`

Hợp nhất nhiều cách tìm.

### `adapters/`

Bộ chuyển tiếp cho các bộ máy ngoài như RAGFlow hoặc PageIndex.

Quy tắc:

> các bộ chuyển tiếp không được làm rò rỉ cấu trúc riêng của công cụ ngoài vào mô hình dữ liệu lõi.

## 14.7. `brain/` — Bộ não thứ hai

### `compiler/`

Biến kết quả nghiên cứu đã được duyệt thành trang tri thức.

### `claims/`

Quản lý sổ khẳng định.

### `linker/`

Tạo và kiểm tra liên kết giữa các trang.

### `contradictions/`

Phát hiện các khẳng định có thể mâu thuẫn.

### `dedup/`

Phát hiện trang hoặc ý trùng.

### `lint/`

Kiểm tra chất lượng wiki:

- link hỏng;
- trang mồ côi;
- thiếu nguồn;
- cấu trúc sai.

### `markdown/`

Lớp đọc/ghi định dạng Markdown bền lâu.

## 14.8. `workspace/` — bộ nhớ làm việc

### `research/`

Không gian nghiên cứu cho từng câu hỏi sâu.

### `evidence-packs/`

Các gói bằng chứng đã được chuẩn bị cho AI suy luận.

Dữ liệu ở đây không tự động trở thành tri thức lâu dài.

## 14.9. `agents/` — vai trò AI

### `librarian/` — thủ thư

Tìm tài liệu, chương, trang.

### `researcher/` — nhà nghiên cứu

So sánh và tổng hợp bằng chứng.

### `brain-maintainer/` — bộ bảo trì trí nhớ

Đề xuất cập nhật Bộ não thứ hai.

### `verifier/` — bộ kiểm chứng

Kiểm tra câu trích, khẳng định, truy nguồn và mâu thuẫn.

Các vai trò có thể chạy cùng một mô hình hoặc các mô hình khác nhau. Điều quan trọng là quyền hạn và trách nhiệm, không phải số lượng tiến trình.

## 14.10. `graph/` — quan hệ phức tạp, tắt mặc định

`graph/` là giao diện tùy chọn.

Bản đầu không cần xây đồ thị toàn kho.

Chỉ bật khi một bài toán thật sự hưởng lợi từ quan hệ:

- tác giả;
- khái niệm;
- ảnh hưởng;
- chuỗi trích dẫn;
- lịch sử thay đổi.

## 14.11. `eval/` — bộ đo chất lượng

Phải là phần chính thức của repo chứ không phải vài script thử nghiệm bên ngoài.

Các nhóm:

- nhận dạng chữ;
- tìm kiếm;
- xếp hạng lại;
- định tuyến theo trang;
- trích dẫn;
- tổng hợp;
- Bộ não thứ hai;
- kiểm thử hồi quy.

## 14.12. `vault/` — dữ liệu con người có thể đọc

### `inbox/`

Nơi nhận tài liệu mới hoặc ghi chú cần xử lý.

### `sources/`

Nguồn bất biến hoặc tham chiếu tới nguồn.

Ở bản thử nghiệm chạy trên file cục bộ, nên ưu tiên cách lưu theo dấu vân tay SHA-256, thí dụ:

```text
vault/
└── sources/
    └── sha256/
        └── ab/
            └── abcdef...pdf
```

Trong đó `ab` là hai ký tự đầu của SHA-256 để tránh một thư mục chứa quá nhiều file.

Nếu dùng NAS/S3/MinIO, có thể áp dụng cùng tư tưởng cho khóa đối tượng:

```text
sources/sha256/ab/abcdef...
```

Mục tiêu không phải bắt buộc đúng tên thư mục này, mà là:

- cùng một nội dung có địa chỉ ổn định;
- không ghi đè nguồn;
- có thể kiểm tra file bằng SHA-256;
- cơ sở dữ liệu chỉ tham chiếu tới nguồn, không biến công cụ tìm kiếm thành nơi duy nhất giữ file.

### `brain/`

Markdown của Bộ não thứ hai.

### `_meta/`

Bảng kê, trạng thái và dữ liệu quản trị dễ đọc.

## 14.13. `docker/`

Chỉ chứa cấu hình đóng gói và chạy các dịch vụ cần thiết.

Không để cấu trúc Docker quyết định kiến trúc hệ thống.

## 14.14. Ranh giới bất biến

Dù cấu trúc thư mục sau này thay đổi, bốn ranh giới sau phải giữ:

```text
NGUỒN
≠
DỮ LIỆU CHUẨN
≠
CHỈ MỤC TÌM KIẾM
≠
BỘ NÃO THỨ HAI
```

và:

```text
NGHIÊN CỨU TẠM
≠
TRI THỨC CHÍNH THỨC
```

Đây quan trọng hơn tên thư mục cụ thể.
