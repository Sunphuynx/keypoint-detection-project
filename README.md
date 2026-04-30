# Keypoint Detection & Feature Extraction

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.9%2B-green.svg)](https://opencv.org/)
[![scikit-image](https://img.shields.io/badge/scikit--image-Latest-yellow.svg)](https://scikit-image.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Latest-orange.svg)](https://mediapipe.dev/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-red.svg)](https://streamlit.io/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Plotting-blueviolet.svg)](https://matplotlib.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data--Analysis-lightgrey.svg)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Scientific--Computing-ff69b4.svg)](https://numpy.org/)
[![Pillow](https://img.shields.io/badge/Pillow-Image--Processing-informational.svg)](https://python-pillow.org/)

## 📖 Mô tả dự án (Project Description)
Dự án học thuật này tập trung vào bài toán **Keypoint Detection** (Phát hiện điểm đặc trưng) trong lĩnh vực **Computer Vision** (Thị giác máy tính). Mục tiêu chính là xây dựng một ứng dụng trực quan để trích xuất và so sánh hiệu năng của các thuật toán phát hiện điểm đặc trưng cổ điển cũng như các phương pháp dựa trên Deep Learning (Học sâu). 

Ứng dụng được xây dựng dưới dạng Web App tương tác thông qua thư viện Streamlit, cho phép người dùng tải ảnh lên, tùy chỉnh các tham số theo thời gian thực và quan sát kết quả trực tiếp.

## ✨ Tính năng chính (Features)
*   **Giao diện tương tác trực quan:** Xây dựng bằng Streamlit, thân thiện với người dùng.
*   **Hỗ trợ đa thuật toán:** Tích hợp cả phương pháp xử lý ảnh truyền thống và mô hình học máy hiện đại.
*   **Tùy chỉnh tham số:** Người dùng có thể điều chỉnh các threshold (ngưỡng) và tham số đặc thù của từng thuật toán để thấy sự thay đổi.
*   **So sánh trực quan (Visual Comparison):** Hiển thị kết quả phát hiện điểm đặc trưng song song để dễ dàng đánh giá.

## 🔬 Các phương pháp được so sánh (Methods Compared)
Dự án tiến hành cài đặt và so sánh 4 phương pháp tiếp cận khác nhau:

1.  **Harris Corner Detection** (Thuật toán phát hiện góc Harris): Phương pháp kinh điển dựa trên sự biến thiên cường độ sáng để tìm ra các góc/cạnh.
2.  **SIFT** (Scale-Invariant Feature Transform): Thuật toán trích xuất đặc trưng mạnh mẽ, bất biến với phép chia tỷ lệ (scale) và phép xoay (rotation).
3.  **ORB** (Oriented FAST and Rotated BRIEF): Thuật toán trích xuất đặc trưng nhanh, hiệu quả, thường được dùng làm giải pháp thay thế mã nguồn mở cho SIFT/SURF.
4.  **MediaPipe:** Bộ giải pháp mã nguồn mở của Google, ứng dụng mạng neural để nhận diện và theo dõi các điểm đặc trưng (landmarks) với tốc độ cao, độ trễ thấp (thường dùng cho khuôn mặt, bàn tay, tư thế).

## ⚙️ Hướng dẫn cài đặt (Installation Steps)

**Bước 1: Clone repository về máy**

```bash
git clone https://github.com/Sunphuynx/keypoint-detection-project.git
cd keypoint-detection-project
```

**Bước 2: Tạo môi trường ảo (Virtual Environment)**
Việc tạo môi trường ảo được khuyến khích để tránh xung đột thư viện.
```bash
python -m venv venv
# Đối với Windows
venv\Scripts\activate
# Đối với macOS/Linux
source venv/bin/activate
```

**Bước 3: Cài đặt các thư viện phụ thuộc (Dependencies)**
Đảm bảo bạn đã có file `requirements.txt` chứa `opencv-python`, `mediapipe`, `streamlit`.
```bash
pip install -r requirements.txt
```

## 🚀 Hướng dẫn sử dụng (Usage)

Khởi chạy ứng dụng Streamlit bằng lệnh sau trong terminal:
```bash
streamlit run app.py
```

*   Trình duyệt sẽ tự động mở tab mới tại địa chỉ `http://localhost:8501`.
*   Sử dụng thanh công cụ bên trái (sidebar) để upload hình ảnh và chọn thuật toán muốn kiểm thử.
*   Tinh chỉnh các thanh trượt (slider) để thay đổi tham số tương ứng với từng thuật toán.

## 👥 Nhóm phát triển (Team)
*Đồ án được thực hiện bởi sinh viên Khoa học Máy tính.*
*   **Phùng Chí Tâm** - [MSSV] - Phụ trách [Công việc cụ thể]

## 📄 Giấy phép (License)
Dự án này được phân phối dưới giấy phép MIT License. Vui lòng xem tệp `LICENSE` để biết thêm chi tiết.
```
