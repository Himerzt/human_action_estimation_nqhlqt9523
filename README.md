# 🛡️ Hệ Thống Giám Sát và Cảnh Báo Hành Động Nguy Hiểm (Human Action Detection)

![Python](https://img.shields.io/badge/Ngôn_ngữ-Python_3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/Detection-YOLOv8m-red)
![OpenPose](https://img.shields.io/badge/Pose-OpenPose_BODY__25-orange)
![LSTM](https://img.shields.io/badge/Sequence-LSTM-yellow)
![Accuracy](https://img.shields.io/badge/Độ_chính_xác-98.11%25-green)
![English](https://img.shields.io/badge/Tiếng_Anh-770_TOEIC-blueviolet)

## 📌 1. Tổng quan dự án
[cite_start]Dự án tập trung xây dựng hệ thống giám sát thông minh, tự động nhận diện các hành động nguy hiểm (ngã, leo trèo) trong môi trường trong nhà nhằm hỗ trợ chăm sóc người cao tuổi và trẻ nhỏ[cite: 70, 71, 235, 236]. [cite_start]Hệ thống kết hợp các mô hình học sâu hiện đại để phân tích tư thế người và chuỗi chuyển động theo thời gian thực[cite: 72, 73, 237, 238].

[cite_start]**Các hành động mục tiêu:** `Đứng (STAND)`, `Ngồi (SIT)`, `Nằm (LIEDOWN)`, `Leo (CLIMB)`, và `Té ngã (FALL)`[cite: 73, 238, 302].

## 🎥 2. Demo & Hình ảnh thực tế
*(Gợi ý: Huy hãy thay các đường dẫn này bằng link ảnh/GIF thực tế từ repo của ông)*

| Phát hiện hành vi FALL | Cảnh báo qua Telegram | Giao diện Web kiểm thử |
| :---: | :---: | :---: |
| ![Fall Demo](https://via.placeholder.com/300x200) | ![Telegram Alert](https://via.placeholder.com/300x200) | ![Web UI](https://via.placeholder.com/300x200) |
| [cite_start]*Hình 3:2: Nhận diện ngã* [cite: 597, 598] | [cite_start]*Hình 3:3: Thông báo khẩn* [cite: 598, 599] | [cite_start]*Hình 3:6: Dashboard hệ thống*  |

## 🚀 3. Thành tựu nổi bật
* [cite_start]**Độ chính xác vượt trội:** Mô hình Fusion (kết hợp Ảnh + Keypoints) đạt mức **98.11%**, vượt xa mức baseline 86.6%[cite: 37, 171, 177, 230].
* [cite_start]**Vận hành ổn định:** Mô hình dựa trên khung xương (Keypoints-based) hoạt động bền vững bất kể sự thay đổi của ánh sáng, màu sắc trang phục hay hậu cảnh phức tạp[cite: 749, 796, 882, 884].
* [cite_start]**Tốc độ xử lý:** Đạt ngưỡng gần thời gian thực (~4-5 FPS) trên cấu hình phần cứng phổ thông[cite: 76, 241, 907, 912].
* [cite_start]**Cảnh báo tức thời:** Tự động chụp ảnh và gửi thông báo qua **Telegram Bot** khi phát hiện hành vi nguy hiểm kéo dài ≥ 3 giây[cite: 289, 533, 556, 631, 644].

## 🏗️ 4. Kiến trúc kỹ thuật (Pipeline)
[cite_start]Hệ thống vận hành thông qua quy trình xử lý đa tầng[cite: 306, 522, 540]:
1.  [cite_start]**Phát hiện & Theo dõi:** Sử dụng **YOLOv8m** kết hợp thuật toán tracking để định danh ID cố định cho từng người[cite: 372, 523, 638].
2.  [cite_start]**Trích xuất đặc trưng:** **OpenPose (BODY_25)** trích xuất bộ khung xương 2D gồm 25 điểm khớp (75 giá trị x, y, confidence) cho mỗi khung hình[cite: 358, 359, 360, 524].
3.  [cite_start]**Xử lý thời gian:** Mô hình **LSTM 2 lớp (128 units)** phân tích chuỗi 12 frames liên tiếp để đưa ra nhãn hành động cuối cùng[cite: 420, 428, 429, 432, 440, 526].

## 🛠️ 5. Công nghệ sử dụng
* [cite_start]**Mô hình AI:** YOLOv8, OpenPose, LSTM, MobileNetV2[cite: 39, 116, 117, 198, 238].
* **Thư viện chính:** PyTorch, Keras, OpenCV, NumPy, Pandas[cite: 26, 30, 400, 738].
* [cite_start]**Hệ thống:** FastAPI (Backend), ReactJS (Frontend), WebSocket (Truyền tải realtime)[cite: 529, 531, 612, 616].

## 📊 6. Kết quả thực nghiệm
[cite_start]So sánh hiệu năng giữa các kiến trúc mô hình trên tập Test[cite: 887, 888]:

| Mô hình | Độ chính xác (Test) | Độ ổn định thực tế |
| :--- | :---: | :--- |
| **Keypoints-based (Deployed)** | **86.60%** | **Cao (Chống nhiễu nền)** |
| **Image-based** | 97.17% | Thấp (Nhạy cảm ánh sáng) |
| **Fusion Model** | 98.11% | Thấp (Dễ Overfitting) |

## 📂 7. Tài nguyên bổ sung
* [cite_start]**Mã nguồn đầy đủ & Trọng số:** [Link Google Drive](#)[cite: 540].
* [cite_start]**Báo cáo khóa luận (Full PDF):** [Xem tại đây](#)[cite: 50, 67].

## 🤝 8. Thông tin tác giả
* **Nguyễn Quốc Huy** - Đại học Công nghiệp TP. Hồ Chí Minh (IUH)[cite: 18, 45, 62].
* [cite_start]**Lê Quang Tuấn** - Cộng sự[cite: 46, 63].
* **Giảng viên hướng dẫn:** ThS. [cite_start]Võ Quang Hoàng Khang[cite: 49, 58, 66].

---
[cite_start]*Dự án thực hiện vào tháng 12/2025*[cite: 50, 59, 67].
