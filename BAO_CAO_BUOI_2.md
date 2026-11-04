# Báo cáo bài tập Buổi 2

Ngày cập nhật: 04/11/2026.

## 1. Khu vực tiếp tục từ Buổi 1

Em tiếp tục dùng trang minh họa kết quả tìm kiếm “bí đao” trên Cocoon, gồm ô từ khóa cố định và bốn kết quả có ảnh, tên, dung tích, giá tham khảo và liên kết xem chi tiết. Trang nằm trong repository đã tạo ở Buổi 1; không tạo website mới.

Khu vực được rà soát là liên kết “Xem chi tiết” của từng kết quả. Mã hiện có đã dùng HTML5 có ngữ nghĩa, CSS riêng, Box Model, Flexbox, CSS Grid, hover và focus. Phạm vi Buổi 2 tập trung giải thích và kiểm tra các kỹ thuật này, đồng thời chỉnh cách thể hiện focus bàn phím để nhất quán hơn với hover.

## 2. Rà soát mã hiện tại

| Quan sát | Phân loại | Hướng xử lý |
| --- | --- | --- |
| Ô từ khóa chỉ đọc và bốn kết quả được cố định. | Giới hạn có chủ ý của bản HTML/CSS, không phải lỗi hiển thị; người dùng cần được biết đây là minh họa. | Giữ chú thích “4 kết quả cố định”; chức năng tìm kiếm động thuộc Buổi 3. |
| Trước khi sửa, hover đổi nền nút nhưng focus bằng bàn phím chỉ có viền chung của trang. | Hai trạng thái của cùng liên kết có phản hồi khác nhau; đây là cơ hội cải thiện, không làm hỏng thao tác. | Cho `:focus-visible` dùng màu nền như hover và giữ viền nhận biết focus. |
| Trước khi sửa, nền và màu chữ có chuyển đổi 150 ms nhưng màu viền đổi ngay. | Chi tiết chuyển động nhỏ chưa đồng bộ với hai thuộc tính còn lại. | Thêm `border-color` vào danh sách thuộc tính chuyển đổi. |

## 3. Thay đổi đã thực hiện

Trong `css/style.css`, `.product-action:hover` và `.product-action:focus-visible` dùng chung nền xanh đậm, viền xanh và chữ trắng. Viền focus vẫn hiện rõ với `outline-offset: 3px`. Quy tắc `transition` cũng thêm `border-color 150ms` để viền chuyển màu cùng nền và chữ.

Đây là cải tiến phản hồi trực quan, không phải sửa lỗi hỏng chức năng. Khi dùng chuột, nút đổi nền; khi dùng Tab, nút có cùng nền và thêm viền focus; khi dùng Enter, liên kết mở trang chi tiết trong thẻ mới. Codex đã sửa mã theo yêu cầu của người học; phần thay đổi và kiểm tra được ghi trong `AI_USAGE.md`.

Mã có element selector như `img` và `h3`, class selector như `.product-action`, và descendant selector như `.search-field svg`. Quy tắc `* { box-sizing: border-box; }` giúp kích thước phần tử tính cả viền và padding trong chiều rộng/chiều cao đã khai báo.

## 4. Kiểm tra giao diện

| Nội dung kiểm tra | Kết quả | Ghi chú |
| --- | --- | --- |
| Trang HTML mở được | Đạt | Mở từ máy chủ cục bộ trong Chrome. |
| CSS được áp dụng | Đạt | Kiểu chữ, màu, bố cục và trạng thái liên kết lấy từ `css/style.css`. |
| Hình ảnh sản phẩm | Đạt | 4/4 ảnh tải hoàn tất ở cả 1366 px, 768 px và 390 px. |
| Liên kết sản phẩm đầu tiên | Đạt | Dùng bàn phím mở trang “Nước tẩy trang bí đao 500ml”; trang đích đã được xác nhận ở lần kiểm tra trước. |
| Hover bằng chuột | Đạt | Di chuyển con trỏ lên liên kết làm nền và viền chuyển xanh, chữ chuyển trắng. |
| Focus bằng bàn phím | Đạt | Dùng Tab; liên kết có nền xanh cùng viền focus nhìn thấy rõ. |
| Bố cục và tràn ngang | Đạt | Viewport 1366, 768 và 390 px; `scrollWidth` lần lượt bằng đúng chiều rộng viewport, không có tràn ngang. |
| Tìm kiếm động | Chưa có, theo phạm vi | Trang ghi rõ đây là bốn kết quả cố định; không giả lập chức năng tìm kiếm của Buổi 3. |

Ảnh trước/sau ở `screenshots/before-1366.png` và `screenshots/after-1366.png` cùng kích thước 1366 × 1100 px, tập trung vào liên kết sản phẩm đầu tiên ở trạng thái focus. Hai ảnh responsive sau khi hoàn thiện ở `screenshots/responsive-768.png` và `screenshots/responsive-390.png`. Ảnh được kết xuất bằng Chrome; kiểm tra hover và Tab cũng được thực hiện trên trang đang mở.

## 5. Giải thích kỹ thuật trong mã

### Câu 1. Các phần tử HTML5 được dùng và lý do

Trang dùng `header` cho đầu trang, `main` cho nội dung chính, `section` để nhóm ô tìm kiếm và kết quả, `article` cho từng sản phẩm, `footer` cho ghi chú cuối trang. Danh sách dùng `ul` và `li`; mỗi ảnh dùng `img` với `alt`; `label` gắn tên với `input`; `a` mở trang chi tiết; `mark` nhấn phần khớp từ khóa; `data` đặt giá trị số cho giá hiển thị. Trang không có menu điều hướng nhiều mục nên không cần thêm `nav` chỉ để đủ danh sách phần tử.

### Câu 2. Khác nhau giữa margin và padding

`margin` tạo khoảng cách bên ngoài phần tử. Trong thẻ sản phẩm, `.product-category { margin-bottom: 5px; }` tạo khoảng cách giữa nhãn danh mục và tên sản phẩm. `padding` tạo khoảng trống bên trong đường viền; `.search-result { padding: 15px 22px; }` giúp ảnh và chữ không sát mép hàng sản phẩm.

### Câu 3. Flexbox được sử dụng ở đâu

`.header-inner` dùng `display: flex` để xếp logo, ghi chú và liên kết nguồn theo hàng; `justify-content: space-between` đẩy các nhóm ra hai phía, còn `align-items: center` căn chúng giữa theo trục dọc. `.search-field` dùng Flexbox để đặt biểu tượng, ô từ khóa và nhãn cùng hàng. `.product-price` và `.site-footer` cũng dùng Flexbox cho các nhóm thành phần nhỏ.

### Câu 4. CSS Grid khác Flexbox như thế nào

Flexbox phù hợp căn chỉnh theo một trục chính, thường là một hàng hoặc một cột. Grid kiểm soát đồng thời hàng và cột. Trong `.search-result`, Grid chia mỗi kết quả thành vùng ảnh, thông tin, giá và thao tác bằng `grid-template-columns` cùng `grid-template-areas`; media query đổi vị trí các vùng khi màn hình hẹp. Cách này phù hợp vì nội dung của một sản phẩm cần nằm ở các cột có vai trò rõ ràng.

### Câu 5. Nếu xóa `display: grid` khỏi danh sách kết quả

Các `grid-template-columns`, `grid-template-areas` và khai báo `grid-area` sẽ không còn điều khiển vị trí. Các phần tử con trở lại luồng khối thông thường, thường xếp nối tiếp theo chiều dọc; ảnh, thông tin, giá và liên kết không còn nằm theo hàng như thiết kế. Quy tắc bên trong media query cũng không thể tạo lại lưới nếu phần tử cha không còn `display: grid`.

### Câu 6. Vì sao ảnh cần thuộc tính alt

`alt` cung cấp mô tả thay thế cho trình đọc màn hình và nội dung dự phòng nếu ảnh không tải được. Ví dụ ảnh đầu có mô tả “Chai nước tẩy trang bí đao Cocoon 500 ml”, giúp nhận biết nội dung ảnh mà không chỉ dựa vào hình ảnh.

### Câu 7. Một đề xuất AI đã kiểm tra hoặc điều chỉnh

Đề xuất là đồng bộ trạng thái hover và focus bàn phím, đồng thời chuyển màu viền cùng lúc với nền và chữ. Mã được cập nhật trong `css/style.css`; sau đó dùng chuột và Tab để kiểm tra phản hồi trực quan, rồi nhấn Enter để kiểm tra trang đích.

### Câu hỏi tự kiểm tra bổ sung trong đề

- `nav` dùng để đánh dấu một nhóm liên kết điều hướng chính; trang này không có menu nhiều mục nên không cần thêm `nav` rỗng.
- `article` có ngữ nghĩa là một nội dung độc lập có thể đứng riêng; `div` chỉ là vùng nhóm trung tính. Mỗi kết quả sản phẩm phù hợp với `article`.
- Dùng `ul` và `li` khi các mục cùng loại tạo thành một danh sách; bốn kết quả tìm kiếm đang dùng cấu trúc này.
- `display: flex` đặt trên phần tử cha để sắp xếp các phần tử con. `justify-content: space-between` đẩy mục đầu/cuối ra hai đầu và chia khoảng trống còn lại giữa các mục.
- `gap` tạo khoảng cách giữa các phần tử con trong Flexbox; `margin` thuộc về từng phần tử và có thể tạo khoảng trống cả ở phía ngoài nhóm.
- `:hover` phản hồi khi con trỏ chuột ở trên phần tử; `:focus-visible` báo vị trí đang được chọn khi điều hướng bằng bàn phím.

## 6. Cách chạy và tự kiểm tra

Mở `index.html` bằng trình duyệt. Dùng chuột di chuyển lên nút “Xem chi tiết”, sau đó nhấn Tab đến liên kết để so sánh hover và focus. Nhấn Enter để mở trang sản phẩm. Có thể xem các ảnh 1366, 768 và 390 px trong thư mục `screenshots/` để đối chiếu breakpoint 899 px và 559 px.
