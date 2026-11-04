# AI Usage Log

## 1. Công cụ AI

Codex của OpenAI, sử dụng trong quá trình thực hiện bài tập ngày 21/10/2026.

## 2. Mục đích sử dụng

Hỗ trợ tổ chức kết quả khảo sát, gợi ý phương án giao diện, tạo và chỉnh mã HTML/CSS, giải thích mã và kiểm tra hiển thị.

## 3. Prompt chính

Các yêu cầu chính được tóm lược từ quá trình trao đổi:

1. Phân tích năm khu vực của Cocoon; phân biệt quan sát thực tế với đề xuất và không khẳng định tính năng chưa kiểm chứng.
2. Rà soát lại nhận xét về banner, menu và thao tác cuộn; loại bỏ kết luận chưa có bằng chứng.
3. Đề xuất cách bổ sung ảnh nhỏ, dung tích và giá trong kết quả tìm kiếm “bí đao”, giải thích phương án trước khi tạo mã.
4. Tạo một trang HTML5/CSS3 với bốn sản phẩm mẫu, CSS riêng và bố cục phù hợp máy tính, điện thoại; ghi rõ trạng thái tìm kiếm cố định.

## 4. Kết quả AI đề xuất

AI hỗ trợ tạo bản phân tích và giao diện danh sách kết quả có ảnh, tên, dung tích, giá và liên kết xem chi tiết; tạo, chỉnh mã nguồn và kiểm tra hiển thị bằng công cụ.

## 5. Kiểm tra và điều chỉnh

### Phần tôi thực hiện

- Chọn Cocoon làm website khảo sát và nhận xét trực tiếp về banner, hiệu ứng và menu sản phẩm.
- Cung cấp ảnh đối chiếu menu; chỉ ra rằng việc cuộn trang chưa đủ để kết luận giao diện khó xem.
- Yêu cầu rà soát Nhiệm vụ 1 và 2, làm rõ khu vực cải tiến và thay phương án chưa phù hợp.
- Chọn hướng bổ sung ảnh và giá trong kết quả tìm kiếm; xem xét và duyệt bản giao diện cuối.

### Phần có AI hỗ trợ

AI tạo và sửa mã theo phương án được chọn, đối chiếu dữ liệu sản phẩm và kiểm tra ở 1280 × 900, 768 × 1024, 375 × 812, 320 × 740. Bốn ảnh tải được, không ghi nhận tràn ngang; liên kết đầu tiên mở đúng trang bằng bàn phím. Các phép thử này được thực hiện bằng công cụ hỗ trợ.

### Kết quả không sử dụng

Loại bỏ nhận xét “banner lớn nên bất tiện” và “phải cuộn nên khó xem” khi chưa có bằng chứng. Phương án cuối tập trung vào bổ sung thông tin trong tìm kiếm.

## 6. Thành phần mã nguồn và cách giải thích

| Thành phần | Vai trò |
| --- | --- |
| `header`, `main`, `section`, `footer` | Chia các phần có ý nghĩa trong trang. |
| `label`, `input`, `readonly` | Gắn nhãn ô từ khóa và giữ trạng thái minh họa cố định. |
| `ul`, `li`, `article` | Tổ chức danh sách và từng kết quả sản phẩm. |
| `img`, `alt` | Hiển thị ảnh và mô tả thay thế. |
| `a.product-action` | Mở đúng trang sản phẩm trên Cocoon. |
| CSS Grid và `grid-template-areas` | Sắp vị trí ảnh, thông tin, giá và liên kết. |
| `@media` | Đổi bố cục tại màn hình hẹp. |
| `object-fit: contain` | Giữ tỷ lệ và hiển thị trọn ảnh. |
| `:focus-visible` | Nhận biết vị trí liên kết khi dùng bàn phím. |

## 7. Hỗ trợ Buổi 2

### Prompt rà soát

> Hãy rà soát mã HTML/CSS hiện có của trang tìm kiếm Cocoon theo yêu cầu Buổi 2. Chỉ ra cấu trúc HTML5, selector, Box Model, Flexbox, Grid và trạng thái hover/focus đã có. Đề xuất một điều chỉnh nhỏ có thể kiểm tra trực tiếp trên giao diện, không tạo lại website và không bịa lỗi. Giải thích rõ cách kiểm tra bằng chuột và bàn phím.

### Kết quả và điều chỉnh

Mã Buổi 1 đã có phần tử ngữ nghĩa, CSS riêng, Grid, Flexbox và viền `:focus-visible`. Điều chỉnh Buổi 2 dùng chung màu nền đậm và màu chữ sáng cho trạng thái hover bằng chuột và focus bằng bàn phím trên `.product-action`; riêng focus giữ viền nhận biết và rút `outline-offset` còn 3 px. Thay đổi này tạo phản hồi nhất quán cho cùng một hành động.

Đã kiểm tra bằng Tab đến liên kết sản phẩm đầu tiên; viền focus hiển thị rõ. Nhấn Enter mở đúng trang nước tẩy trang bí đao 500 ml trên Cocoon. Mã vẫn dùng trạng thái tìm kiếm cố định, không thêm JavaScript hoặc giả lập chức năng tìm kiếm.

### Phạm vi ghi nhận

Phần mã và nội dung Buổi 2 trong phiên này được cập nhật với sự hỗ trợ của Codex. Người học cần mở lại trang trong trình duyệt, tự xem trạng thái focus và có thể thay đổi một giá trị CSS để luyện thao tác trực tiếp trước khi nộp.
