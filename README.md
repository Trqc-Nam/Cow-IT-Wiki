# BÁO CÁO DỰ ÁN THỰC HÀNH TIN HỌC 12
**Tên dự án:** Bách khoa toàn thư Công Nghệ - Cow IT

**Kính gửi:** Thầy/Cô giáo bộ môn Tin học
**Họ và tên học sinh:** [Tên của bạn]
**Lớp:** [Tên lớp]

---

## I. GIỚI THIỆU DỰ ÁN

Dự án **"Cow IT"** là một trang web Bách khoa toàn thư được xây dựng với mục tiêu mang đến một không gian tìm hiểu kiến thức về Công nghệ thông tin một cách trực quan, hiện đại và khoa học.

Thử thách lớn nhất của dự án là tuân thủ 100% yêu cầu của bài thực hành: **chỉ sử dụng HTML5 và CSS3**, hoàn toàn không có sự can thiệp của JavaScript. Toàn bộ các tính năng tương tác phức tạp, hiệu ứng động và logic giao diện đều được xử lý bằng các kỹ thuật CSS nâng cao.

## II. TRẢI NGHIỆM TRỰC TUYẾN

Sản phẩm đã được triển khai và đưa lên Internet. Kính mời Thầy/Cô trải nghiệm trực tiếp tại địa chỉ:

*   **Website:** **[https://it-cow.netlify.app/](https://it-cow.netlify.app/)**
*   **Tình trạng triển khai:** [![Netlify Status](https://api.netlify.com/api/v1/badges/a732fcf0-8618-442f-a2f4-2d432f1e6285/deploy-status)](https://app.netlify.com/projects/it-cow/deploys)

## III. HƯỚNG DẪN SỬ DỤNG VÀ CÁC ĐIỂM NỔI BẬT

Để có trải nghiệm tốt nhất các tính năng của website, em xin gợi ý một vài điểm Thầy/Cô có thể tương tác:

1.  **Chuyển đổi Giao diện Sáng/Tối (Dark/Light Mode):** Ở góc trên bên phải màn hình, Thầy/Cô có thể bấm vào nút icon Mặt trăng/Mặt trời để chuyển đổi giao diện website mà không cần tải lại trang.
2.  **Hệ thống Điều hướng Wiki:** Các bài viết được liên kết chéo với nhau. Khi đang đọc một bài, Thầy/Cô có thể click vào các thuật ngữ được bôi đậm để di chuyển đến bài viết liên quan.
3.  **Tương tác với Giao diện:** Xin hãy thử di chuột (hover) qua các thẻ bài viết ở trang chủ hoặc các nút bấm để trải nghiệm hiệu ứng nổi khối và phát sáng (Glow Effect).
4.  **Kiểm tra tính Tương thích (Responsive):** Giao diện website được thiết kế để tự động co giãn và hiển thị tốt trên các kích thước màn hình khác nhau, từ máy tính để bàn đến điện thoại di động.

## IV. KIẾN TRÚC & CÔNG NGHỆ ÁP DỤNG

### a. Công nghệ cốt lõi
*   **HTML5:** Xây dựng cấu trúc trang web với các thẻ ngữ nghĩa (`<header>`, `<main>`, `<article>`, `<aside>`), đảm bảo tính chuẩn hóa và tốt cho SEO.
*   **CSS3:** Chịu trách nhiệm 100% về giao diện, hiệu ứng và các logic tương tác.

### b. Phong cách thiết kế (UI/UX)
Dự án được thiết kế theo các xu hướng hiện đại nhất để tạo cảm giác chuyên nghiệp:
*   **Bento Grid:** Bố cục các khối hộp ở trang chủ được sắp xếp bằng `CSS Grid`, lấy cảm hứng từ giao diện của Apple.
*   **Glassmorphism:** Hiệu ứng "kính mờ" được áp dụng cho thanh Header và các thẻ bài viết bằng thuộc tính `backdrop-filter`.
*   **Futuristic / Neon Glow:** Sử dụng `box-shadow` và `transition` để tạo hiệu ứng phát sáng màu Tím Neon khi người dùng tương tác.

### c. Các kỹ thuật CSS nâng cao đã sử dụng
*   **CSS Variables & `:has()` Selector:** Nền tảng cho tính năng Dark/Light Mode không cần JavaScript.
*   **CSS Grid & Flexbox:** Chịu trách nhiệm chính trong việc dàn trang và sắp xếp bố cục một cách linh hoạt.
*   **CSS Animations & Transitions (`@keyframes`):** Tạo ra các hiệu ứng chuyển động mượt mà, từ Hero Banner trang chủ đến các hiệu ứng hover.
*   **CSS Pseudo-classes (`:valid`, `:invalid`):** Giả lập tính năng kiểm tra lỗi "sống" cho Form nhập email mà không cần code logic.

### d. Cấu trúc thư mục chuyên nghiệp
Dự án được tổ chức theo mô hình phân tách rõ ràng, giúp dễ dàng quản lý và bảo trì.
```text
Cow-IT-Wiki/
├── index.html
├── css/
│   ├── style.css
│   ├── layout.css
│   └── animation.css
├── topics/
│   ├── ai.html, webdev.html, algorithms.html
│   ├── ai_pages/
│   ├── webdev_pages/
│   └── algorithms_pages/
└── images/
```

## V. KẾT LUẬN

Dự án **Cow IT** là kết quả của quá trình vận dụng kiến thức đã học và nỗ lực tự nghiên cứu các kỹ thuật lập trình web hiện đại. Qua bài thực hành này, em không chỉ củng cố được kỹ năng về HTML/CSS mà còn học hỏi được tư duy thiết kế hệ thống, cách tổ chức mã nguồn khoa học và giải quyết các bài toán giao diện phức tạp bằng công cụ đơn giản nhất.

Em xin chân thành cảm ơn Thầy/Cô đã giảng dạy và hướng dẫn tận tình!

*Người viết báo cáo,*

*(Ký và ghi rõ họ tên)*

**[Tên của bạn]**
