# Hệ Thống Giám Sát và Cảnh Báo Hành Động Nguy Hiểm (Human Action Detection)

![Python](https://img.shields.io/badge/Ngôn_ngữ-Python_3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/Detection-YOLOv8m-red)
![OpenPose](https://img.shields.io/badge/Pose-OpenPose_BODY__25-orange)
![LSTM](https://img.shields.io/badge/Sequence-LSTM-yellow)

## 📌 1. Tổng quan dự án
Dự án tập trung xây dựng hệ thống giám sát thông minh, tự động nhận diện các hành động nguy hiểm (ngã, leo trèo) trong môi trường trong nhà nhằm hỗ trợ chăm sóc người cao tuổi và trẻ nhỏ. Hệ thống kết hợp các mô hình học sâu hiện đại để phân tích tư thế người và chuỗi chuyển động theo thời gian thực.

**Các hành động mục tiêu:** `Đứng (STAND)`, `Ngồi (SIT)`, `Nằm (LIEDOWN)`, `Leo (CLIMB)`, và `Té ngã (FALL)`.

## 🎥 2. Demo & Hình ảnh thực tế

Hệ thống hoạt động ổn định với các hành động có biên độ chuyển động khác nhau, từ các tư thế tĩnh đến các hành vi nguy hiểm diễn ra nhanh.

| Nhận diện CLIMB & FALL (Leo/Ngã) | Nhận diện SITTING (Ngồi) |
| :---: | :---: |
| ![Climb & Fall Demo](https://drive.google.com/uc?id=1uYxBiCPDnKDX3hPPJ5h0k5NBOpkLPvYR) | ![Sitting Demo](https://drive.google.com/uc?id=1ojb1A-EZ-YMEiIizn5xGjqh-vkodWdUy) |
| *Mô hình xử lý leo trèo và chuyển đổi trạng thái* | *Nhận diện tư thế ngồi hằng ngày* |

| Nhận diện hành vi FALL (Té ngã) | Cảnh báo qua Telegram |
| :---: | :---: |
| ![Fall Demo](https://drive.google.com/uc?id=1B4VJfd-5L4IOFMOcbjW04rnp-9cgpTw0) | ![Telegram Alert](https://drive.google.com/uc?id=1ioo9wUm1lMq914BGk8Xa8l4CIy_K8X2x) |
| *Bắt trọn khoảnh khắc té ngã thực tế* | *Thông báo tức thời kèm ảnh chụp hiện trường* |

## 🚀 3. Thành tựu nổi bật
* **Độ chính xác vượt trội:** Mô hình Fusion (kết hợp Ảnh + Keypoints) đạt mức **98.11%**, vượt xa mức baseline 86.6%.
* **Vận hành ổn định:** Mô hình dựa trên khung xương (Keypoints-based) hoạt động bền vững bất kể sự thay đổi của ánh sáng, màu sắc trang phục hay hậu cảnh phức tạp.
* **Tốc độ xử lý:** Đạt ngưỡng gần thời gian thực (~4-5 FPS) trên cấu hình phần cứng phổ thông.
* **Cảnh báo tức thời:** Tự động chụp ảnh và gửi thông báo qua **Telegram Bot** khi phát hiện hành vi nguy hiểm kéo dài ≥ 3 giây.

## 🏗️ 4. Kiến trúc kỹ thuật (Pipeline)
Hệ thống vận hành thông qua quy trình xử lý đa tầng:
1.  **Phát hiện & Theo dõi:** Sử dụng **YOLOv8m** kết hợp thuật toán tracking để định danh ID cố định cho từng người.
2.  **Trích xuất đặc trưng:** **OpenPose (BODY_25)** trích xuất bộ khung xương 2D gồm 25 điểm khớp (75 giá trị x, y, confidence) cho mỗi khung hình.
3.  **Xử lý thời gian:** Mô hình **LSTM 2 lớp (128 units)** phân tích chuỗi 12 frames liên tiếp để đưa ra nhãn hành động cuối cùng.

## 🛠️ 5. Công nghệ sử dụng
* **Mô hình AI:** YOLOv8, OpenPose, LSTM, MobileNetV2.
* **Thư viện chính:** PyTorch, Keras, OpenCV, NumPy, Pandas.
* **Hệ thống:** FastAPI (Backend), ReactJS (Frontend), WebSocket (Truyền tải realtime).

## 📊 6. Kết quả thực nghiệm
So sánh hiệu năng giữa các kiến trúc mô hình trên tập Test:

| Mô hình | Độ chính xác (Test) | Độ ổn định thực tế |
| :--- | :---: | :--- |
| **Keypoints-based (Deployed)** | **86.60%** | **Cao (Chống nhiễu nền)** |
| **Image-based** | 97.17% | Thấp (Nhạy cảm ánh sáng) |
| **Fusion Model** | 98.11% | Thấp (Dễ Overfitting) |

## 📂 7. Tài nguyên bổ sung
* **Mã nguồn đầy đủ & Trọng số:** [Link Google Drive](#)[cite: 540].
* **Báo cáo khóa luận (Full PDF):** [Xem tại đây](#)[cite: 50, 67].

## 🤝 8. Thông tin tác giả
* **Nguyễn Quốc Huy** - Đại học Công nghiệp TP. Hồ Chí Minh (IUH).
* **Lê Quang Tuấn** - Cộng sự.
* **Giảng viên hướng dẫn:** ThS. Võ Quang Hoàng Khang.

---
*Dự án thực hiện vào tháng 12/2025*.




