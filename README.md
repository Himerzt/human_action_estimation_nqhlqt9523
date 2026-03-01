# Hệ Thống Giám Sát và Cảnh Báo Hành Động Nguy Hiểm (Human Action Detection)

![Python](https://img.shields.io/badge/Ngôn_ngữ-Python_3.8%2B-blue)
![YOLOv8](https://img.shields.io/badge/Detection-YOLOv8m-red)
![OpenPose](https://img.shields.io/badge/Pose-OpenPose_BODY__25-orange)
![LSTM](https://img.shields.io/badge/Sequence-LSTM-yellow)

## 📌 1. Tổng quan dự án
Dự án tập trung xây dựng hệ thống giám sát thông minh, tự động nhận diện các hành động nguy hiểm (ngã, leo trèo) trong môi trường trong nhà nhằm hỗ trợ chăm sóc người cao tuổi và trẻ nhỏ. Hệ thống kết hợp các mô hình học sâu hiện đại để phân tích tư thế người và chuỗi chuyển động theo thời gian thực.

**Các hành động mục tiêu:** `Đứng (STAND)`, `Ngồi (SIT)`, `Nằm (LIEDOWN)`, `Leo (CLIMB)`, và `Té ngã (FALL)`.

## 🎥 2. Demo & Hình ảnh thực tế

| Nhận diện CLIMB & FALL (Leo/Ngã)


https://github.com/user-attachments/assets/cc4384bd-3ddb-43fe-8a49-cb9928bddb43


| Nhận diện SITTING (Ngồi) |


https://github.com/user-attachments/assets/106fa783-d03d-4ac8-82da-3029d2a515b7


| Nhận diện hành vi FALL (Té ngã) 


https://github.com/user-attachments/assets/63c4c6c1-9023-4449-ae6f-29ce8ec32ca7


https://github.com/user-attachments/assets/d1971ffd-adfc-40a0-b44d-c9d358d13653



| Cảnh báo qua Telegram |
<img width="1124" height="550" alt="detection_via_telegram" src="https://github.com/user-attachments/assets/ace6cf57-4305-49b1-b022-610a4884e9a3" />


## 🚀 3. Thành tựu nổi bật (Key Achievements)

* **Kết quả nghiên cứu ấn tượng:** Đạt độ chính xác thử nghiệm (Test Accuracy) lên đến **98.11%** khi thử nghiệm với kiến trúc **Fusion Model** (kết hợp đặc trưng hình ảnh và khung xương).
* **Tư duy triển khai thực tế:** Quyết định lựa chọn mô hình **Keypoint-based (86.60%)** để vận hành chính thức nhằm ưu tiên tính **ổn định (Robustness)**. Mô hình này giúp hệ thống hoạt động bền vững, ít bị ảnh hưởng bởi sự thay đổi ánh sáng, màu sắc trang phục hay hậu cảnh phức tạp so với các mô hình thuần hình ảnh.
* **Hiệu năng thời gian thực:** Duy trì tốc độ xử lý ổn định từ **5-10 FPS** trên các thiết bị cấu hình phổ thông, đáp ứng tốt yêu cầu giám sát và phản hồi tức thì.
* **Hệ thống cảnh báo thông minh:** Xây dựng thành công luồng thông báo tự động qua **Telegram Bot**, tự động gửi hình ảnh hiện trường ngay khi phát hiện hành vi nguy hiểm (té ngã, leo trèo) kéo dài $\ge$ 3 giây.

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

* **Báo cáo khóa luận:** [Xem tại đây](https://drive.google.com/drive/folders/1ey-TjmuKZNOPbtzXVW4Stl34Pzc8NXFJ).

## 🤝 8. Thông tin tác giả
* **Nguyễn Quốc Huy** - Đại học Công nghiệp TP. Hồ Chí Minh (IUH).
* **Lê Quang Tuấn** - Cộng sự.
* **Giảng viên hướng dẫn:** ThS. Võ Quang Hoàng Khang.

---
*Dự án thực hiện vào tháng 12/2025*.








