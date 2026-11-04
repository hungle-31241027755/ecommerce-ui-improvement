# Báo cáo bài tập Buổi 2

Ngày cập nhật: 04/11/2026.

## 1. Khu vực tiếp tục từ Buổi 1

Em tiếp tục dùng trang minh họa kết quả tìm kiếm “bí đao” trên Cocoon, gồm ô từ khóa cố định và bốn kết quả có ảnh, tên, dung tích, giá tham khảo và liên kết xem chi tiết. Trang nằm trong repository đã tạo ở Buổi 1; không tạo website mới.

Khu vực được rà soát là liên kết “Xem chi tiết” của từng kết quả. Mã hiện có đã dùng HTML5 có ngữ nghĩa, CSS riêng, Box Model, Flexbox, CSS Grid, hover và focus. Phạm vi Buổi 2 tập trung giải thích và kiểm tra các kỹ thuật này, đồng thời chỉnh cách thể hiện focus bàn phím để nhất quán hơn với hover.

## 2. Rà soát mã hiện tại

| Quan sát | Phân loại | Hướng xử lý |
| --- | --- | --- |
| Trang có bốn sản phẩm cố định cho từ khóa “bí đao”; ô tìm kiếm ở trạng thái chỉ đọc. | Giới hạn được chủ ý của bản HTML/CSS, không phải lỗi. | Giữ ghi chú “4 kết quả cố định”; chức năng tìm kiếm động thuộc phạm vi JavaScript ở Buổi 3. |
| Mỗi sản phẩm có ảnh, tên, dung tích, giá và liên kết. Ảnh có `alt`; liên kết có tên truy cập rõ ràng. | Đã có và phù hợp với nội dung. | Giữ cấu trúc hiện tại. |
| Hover làm nút đổi sang nền xanh đậm; focus bàn phím trước khi cập nhật chỉ dùng viền chung của trang. | Cơ hội đồng bộ hai trạng thái của cùng một hành động. | Dùng chung màu hover cho `:hover` và `:focus-visible`, giữ viền focus để nhận biết bàn phím. |

## 3. Thay đổi đã thực hiện

Trong `css/style.css`, quy tắc `.product-action:hover` được mở rộng để áp dụng cùng màu nền xanh đậm, viền xanh và chữ trắng cho `.product-action:focus-visible`. Trạng thái focus đặt `outline-offset: 3px` để viền nằm sát hơn quanh liên kết mà vẫn tách khỏi nút.

Đây là cải tiến phản hồi trực quan, không phải sửa lỗi hỏng chức năng. Khi dùng chuột, nút đổi nền; khi dùng Tab, nút có cùng nền và thêm viền focus; khi dùng Enter, liên kết mở trang chi tiết trong thẻ mới.

Mã có element selector như `img` và `h3`, class selector như `.product-action`, và descendant selector như `.search-field svg`. Quy tắc `* { box-sizing: border-box; }` giúp kích thước phần tử tính cả viền và padding trong chiều rộng/chiều cao đã khai báo.

## 4. Kiểm tra giao diện

| Nội dung kiểm tra | Kết quả | Ghi chú |
| --- | --- | --- |
| Trang HTML mở được | Đạt | Mở trang từ máy chủ cục bộ trong trình duyệt. |
| CSS được áp dụng | Đạt | Kiểu chữ, màu, bố cục và nút hiển thị theo `css/style.css`. |
| Hình ảnh sản phẩm | Đạt | Bốn ảnh hiển thị trong trang đã mở. |
| Liên kết sản phẩm đầu tiên | Đạt | Tab đến liên kết đầu tiên, nhấn Enter; trang đích có tiêu đề “Nước tẩy trang bí đao 500ml” và giá 299.000 đ. |
| Trạng thái bàn phím | Đạt | Viền focus hiển thị quanh liên kết sản phẩm đầu tiên. |
| Tràn ngang ở khung đã mở | Không ghi nhận | Quan sát trang ở khung trình duyệt hiện có; chưa chạy lại toàn bộ kích thước 1366 px, 768 px và 390 px trong lần cập nhật này. |
| Tìm kiếm động | Không áp dụng | Trang ghi rõ đây là bốn kết quả cố định; không giả lập chức năng chưa có. |

Buổi 1 đã ghi nhận kiểm tra responsive ở 1280 × 900, 768 × 1024, 375 × 812 và 320 × 740. Lần cập nhật Buổi 2 chỉ đổi trạng thái hover/focus của liên kết; các quy tắc breakpoint không thay đổi. Cần chụp một cặp ảnh trước/sau khi người học mở trang ở trình duyệt để bổ sung minh chứng trực quan theo yêu cầu nộp bài.

## 5. Giải thích kỹ thuật trong mã

### Câu 1. Các phần tử HTML5 được dùng và lý do

Trang dùng `header` cho đầu trang, `main` cho nội dung chính, `section` để nhóm ô tìm kiếm và kết quả, `article` cho từng sản phẩm, `footer` cho ghi chú cuối trang. Danh sách dùng `ul` và `li`; mỗi ảnh dùng `img` với `alt`; `label` gắn tên với `input`; `a` mở trang chi tiết; `mark` nhấn phần khớp từ khóa; `data` đặt giá trị số cho giá hiển thị. Trang không có menu điều hướng nhiều mục nên không cần thêm `nav` chỉ để đủ danh sách phần tử.

### Câu 2. Khác nhau giữa margin và padding

`margin` tạo khoảng cách bên ngoài phần tử. Ví dụ `.search-panel { margin-bottom: 16px; }` tạo khoảng cách giữa khung tìm kiếm và phần kết quả. `padding` tạo khoảng trống bên trong đường viền. Ví dụ `.search-result { padding: 15px 22px; }` tạo khoảng cách giữa nội dung từng hàng và viền danh sách; phần đệm giúp ảnh và chữ không sát mép.

### Câu 3. Flexbox được sử dụng ở đâu

`.header-inner` dùng `display: flex` để xếp logo, ghi chú và liên kết nguồn theo hàng; `justify-content: space-between` đẩy các nhóm ra hai phía, còn `align-items: center` căn chúng giữa theo trục dọc. `.search-field` dùng Flexbox để đặt biểu tượng, ô từ khóa và nhãn cùng hàng. `.product-price` và `.site-footer` cũng dùng Flexbox cho các nhóm thành phần nhỏ.

### Câu 4. CSS Grid khác Flexbox như thế nào

Flexbox phù hợp căn chỉnh theo một trục chính, thường là một hàng hoặc một cột. Grid kiểm soát đồng thời hàng và cột. Trong `.search-result`, Grid chia mỗi kết quả thành vùng ảnh, thông tin, giá và thao tác bằng `grid-template-columns` cùng `grid-template-areas`; media query đổi vị trí các vùng khi màn hình hẹp. Cách này phù hợp vì nội dung của một sản phẩm cần nằm ở các cột có vai trò rõ ràng.

### Câu 5. Nếu xóa `display: grid` khỏi danh sách kết quả

Các `grid-template-columns`, `grid-template-areas` và khai báo `grid-area` sẽ không còn điều khiển vị trí. Các phần tử con trở lại luồng khối thông thường, thường xếp nối tiếp theo chiều dọc; ảnh, thông tin, giá và liên kết không còn nằm theo hàng như thiết kế. Quy tắc bên trong media query cũng không thể tạo lại lưới nếu phần tử cha không còn `display: grid`.

### Câu 6. Vì sao ảnh cần thuộc tính alt

`alt` cung cấp mô tả thay thế cho trình đọc màn hình và nội dung dự phòng nếu ảnh không tải được. Ví dụ ảnh đầu có mô tả “Chai nước tẩy trang bí đao Cocoon 500 ml”, giúp nhận biết nội dung ảnh mà không chỉ dựa vào hình ảnh.

### Câu 7. Một đề xuất AI đã kiểm tra hoặc điều chỉnh

Đề xuất là đồng bộ trạng thái hover và focus bàn phím trên liên kết sản phẩm. Mã được cập nhật trong `css/style.css`; sau đó dùng Tab để đến liên kết đầu tiên, quan sát nền và viền focus, rồi nhấn Enter để kiểm tra trang đích. Cách này kiểm tra cả phản hồi trực quan lẫn thao tác bàn phím.

## 6. Cách chạy và tự kiểm tra

Mở `index.html` bằng trình duyệt. Dùng chuột di chuyển lên nút “Xem chi tiết”, sau đó nhấn Tab đến liên kết để so sánh hai trạng thái. Nhấn Enter để mở trang sản phẩm. Thay đổi chiều rộng cửa sổ để quan sát các quy tắc `@media` ở 899 px và 559 px.

Ảnh trước/sau cần được chụp từ cùng trình duyệt và cùng kích thước hiển thị để đối chiếu công bằng. Khi nộp, lưu ảnh vào repository và cập nhật đường dẫn ảnh trong README nếu cần.
