# E-commerce UI Improvement

## 1. Giới thiệu

Bài thực hành cải tiến khu vực tìm kiếm sản phẩm, tham khảo website Cocoon Vietnam. Giao diện bổ sung ảnh và giá vào từng kết quả, đồng thời giữ rõ tên, dung tích và liên kết xem chi tiết.

## 2. Website tham khảo

- Tên website: Cocoon Vietnam.
- URL: https://cocoonvietnam.com/
- Khu vực khảo sát: khung tìm kiếm sản phẩm với từ khóa “bí đao”.

## 3. Chức năng

- Hiển thị bốn kết quả mẫu cho từ khóa “bí đao”.
- Mỗi kết quả có ảnh, tên, dung tích, giá tham khảo và liên kết “Xem chi tiết”.
- Điều chỉnh bố cục theo màn hình máy tính, máy tính bảng và điện thoại.
- Hỗ trợ thao tác liên kết bằng bàn phím và mô tả thay thế cho ảnh.

Đây là giao diện minh họa với từ khóa cố định; ô tìm kiếm ở trạng thái chỉ đọc. Liên kết “Xem chi tiết” mở trang sản phẩm chính thức của Cocoon.

## 4. Công nghệ

- HTML5.
- CSS3, CSS Grid và media queries.
- Tài nguyên ảnh lưu trong thư mục dự án.

## 5. Cách chạy

Tải dự án về, giải nén nếu cần và mở `index.html` bằng trình duyệt. Không cần cài thư viện. Các liên kết đến Cocoon cần kết nối Internet.

```text
.
├── index.html
├── README.md
├── AI_USAGE.md
├── HUONG_DAN.md
├── NGUON_ANH.md
├── css/
│   └── style.css
└── images/
    ├── tay-trang-bi-dao.jpg
    ├── gel-rua-mat-bi-dao.jpg
    ├── mat-na-bi-dao.jpg
    └── nuoc-can-bang-bi-dao.jpg
```

## 6. Cải tiến đã thực hiện

Khung tìm kiếm được khảo sát hiển thị danh sách tên sản phẩm có liên kết; nhiều tên đã kèm dung tích nhưng chưa có ảnh và giá ngay trong kết quả. Bản thực hành bổ sung hai thông tin này để hỗ trợ nhận diện sản phẩm và đối chiếu giá trước khi mở chi tiết.

Máy tính từ 900 px xếp ảnh, thông tin, giá và liên kết trên cùng hàng. Từ 560 đến 899 px đưa giá xuống dưới tên. Dưới 560 px đưa liên kết xuống dưới nội dung, rộng theo hàng.

Ảnh và giá được đối chiếu ngày 21/10/2026. Giá có thể thay đổi; xem [nguồn ảnh và dữ liệu](NGUON_ANH.md). Lợi ích sử dụng là mục tiêu thiết kế, chưa được đo bằng khảo sát khách hàng.

## 7. Hỗ trợ từ AI

Tôi lựa chọn website, đối chiếu nhận xét với giao diện thực tế, cung cấp ảnh menu và yêu cầu loại bỏ các kết luận chưa có cơ sở về banner hoặc việc cuộn trang. Tôi chọn hướng bổ sung ảnh và giá trong tìm kiếm, xem xét bản minh họa và quyết định phương án cuối.

AI hỗ trợ hệ thống hóa phân tích, đề xuất bố cục, tạo và sửa mã HTML/CSS, kiểm tra hiển thị và chuẩn bị tài liệu. Quá trình chọn lọc kết quả, phạm vi kiểm tra và các thành phần mã được ghi ngắn gọn tại [AI_USAGE.md](AI_USAGE.md).

## 8. Bài tập Buổi 2

Buổi 2 tiếp tục dùng trang kết quả tìm kiếm từ Buổi 1 để ôn HTML5 có ngữ nghĩa, CSS selector, Box Model, Flexbox, CSS Grid và trạng thái tương tác. Bản cập nhật đồng bộ trạng thái hover và focus bàn phím trên liên kết “Xem chi tiết”; phần giải thích, câu trả lời kiến thức và ghi nhận kiểm thử nằm trong [báo cáo Buổi 2](BAO_CAO_BUOI_2.md).
