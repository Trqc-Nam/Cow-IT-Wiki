# Teachable Machine: Khi Máy Tính Cũng Có "Đôi Mắt"

---

## 1. Thị giác máy tính (Computer Vision) là gì?

Bạn mở điện thoại bằng FaceID, Facebook tự động gắn thẻ (tag) mặt bạn trong ảnh chụp tập thể, hay xe tự lái Tesla nhìn thấy đèn đỏ và dừng lại. Tất cả những "phép thuật" đó đều xuất phát từ một công nghệ lõi: **Thị giác máy tính (Computer Vision).**

Nói một cách đơn giản nhất, nếu Webcam hay Camera là "con mắt" thu nhận ánh sáng, thì Computer Vision chính là "bộ não" xử lý những gì mắt thấy.

Máy tính vốn dĩ chỉ hiểu các con số 0 và 1. Một bức ảnh đối với máy tính chỉ là một lưới khổng lồ chứa hàng triệu điểm ảnh (pixels) với các mã màu vô tri. Computer Vision là công nghệ giúp máy tính "nhìn" bức ảnh đó và hiểu được ý nghĩa: *"À, đây là con mèo, kia là cái cây, còn đây là chữ A"*, thay vì chỉ thấy một đống mã màu hỗn độn.

Trước đây, để làm được điều này cần hàng tá thuật toán toán học phức tạp. Nhưng hôm nay, Google đã mang nó đến tận tay học sinh cấp 3 thông qua **Teachable Machine**.

![Video 1 Placeholder](https://youtu.be/T2qQGqZxkD0)
> **Chú thích Video:** *Giới thiệu TM của Google*  
> **Mô tả ảnh cho thẻ `alt`:** Video giới thiệu Teachable Machine.

---

## 2. Teachable Machine: AI trong tầm tay

**Teachable Machine** là một công cụ dựa trên nền tảng web do Google phát triển, cho phép bất kỳ ai – kể cả người chưa từng viết một dòng code nào – cũng có thể tạo ra các mô hình máy học (Machine Learning) nhanh chóng, dễ dàng và miễn phí.

Sức mạnh của nó nằm ở tính trực quan. Bạn không cần cài đặt Python, không cần thư viện TensorFlow nặng nề. Mọi thứ diễn ra ngay trên trình duyệt Chrome của bạn.
LINK : https://teachablemachine.withgoogle.com/
---

## 3. Quy trình 3 bước để "dạy khôn" máy tính

Để một đứa trẻ phân biệt được quả táo và quả cam, bạn cần chỉ cho nó xem quả táo trông thế nào và quả cam trông thế nào. Máy tính cũng vậy. Quy trình làm việc với Teachable Machine gói gọn trong 3 bước:

### Bước 1: Thu thập dữ liệu (Gather Data)
Đây là bước bạn "nhồi" kiến thức cho AI. Bạn sẽ định nghĩa các Lớp (Class). Ví dụ, bạn muốn AI phân biệt việc bạn đang "Sách 1" hay "Sách 2".
*   **Class 1 (Sách 1):** Bạn bật Webcam, Cầm sách 1 vào và nhấn nút "Hold to Record". Máy sẽ chụp hàng trăm tấm ảnh bạn ở các góc độ khác nhau.
*   **Class 2 (Sách 2):** Lấy sách 2 ra và làm tương tự.

Dữ liệu càng phong phú, AI học càng giỏi.

### Bước 2: Huấn luyện (Train Model)
Sau khi đã có dữ liệu mẫu, bạn nhấn nút **"Train Model"**.
Lúc này, trình duyệt sẽ sử dụng sức mạnh phần cứng máy tính của bạn để chạy các thuật toán tìm ra sự khác biệt giữa hai nhóm ảnh trên. Nó sẽ tự học rằng: *"Cứ hễ có Sách 1 thì là Class 1, còn thấy Sách 2 thì là Class 2"*. Quá trình này thường chỉ mất vài chục giây.
Lưu ý trong phần advance:
- Phần Epochs: Số lần bạn cho máy học qua dữ liệu.
- Phần Batch size: Số mẫu trong mỗi set học.
- Phần Learning rate: để nguyên nếu bạn chưa học bài bản về Machine Learning.

### Bước 3: Xuất và Sử dụng (Export Model)
Khi huấn luyện xong, bạn có thể kiểm tra ngay lập tức ở khung Preview. Thử đeo khẩu trang vào và xem thanh dự đoán nhảy lên **100% Class 1** – cảm giác đó thực sự rất phấn khích!

Cuối cùng, bạn có thể xuất mô hình này dưới dạng file hoặc mã nhúng (TensorFlow.js) để đưa vào các dự án web, ứng dụng di động hoặc thậm chí là mạch Arduino/Micro:bit.


---

## 4. Video Demo trực quan

*(Phần này được thiết kế riêng để đáp ứng tiêu chí Đa phương tiện của dự án Cow IT. Hãy xem cách một mô hình AI được tạo ra trong chưa đầy 2 phút)*.

VIDEO : ![Image 2 Placeholder](https://youtu.be/ipWdLj2Xgns) 
> **Mô tả video cho thẻ `alt`:** Một người đang cầm cuốn sách 1 và 2 trước camera, sau đó thực hiện training, kết quả khi thực nghiệm rên màn hình máy tính hiển thị thể hiện AI nhận diện chính xác vật thể.

> *Gợi ý kỹ thuật: Sử dụng thẻ `<iframe>` với class `video-responsive` để video hiển thị đẹp trên mọi màn hình.*

---

## 5. Ứng dụng thực tiễn và Ý nghĩa

Teachable Machine không chỉ là một món đồ chơi công nghệ. Cơ chế hoạt động của nó là nền tảng cho những ứng dụng vĩ mô hơn:
*   **Y tế:** AI phân tích ảnh X-quang để phát hiện khối u (tương tự như phân biệt táo và cam, nhưng ở cấp độ tế bào).
*   **Nông nghiệp:** Drone bay trên cánh đồng, nhận diện cây bị sâu bệnh qua màu sắc lá.
*   **Hỗ trợ người khiếm thị:** Ứng dụng nhìn vào đồ vật và phát ra âm thanh tên gọi của đồ vật đó.

Với Teachable Machine, rào cản kỹ thuật đã bị xóa bỏ. Giờ đây, giới hạn duy nhất chính là trí tưởng tượng của bạn. Hãy thử bắt đầu dự án AI đầu tiên của mình ngay hôm nay!
