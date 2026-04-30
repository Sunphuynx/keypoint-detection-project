<div align="center">

# Keypoint Detection Project

**Nghiên cứu, triển khai và so sánh các phương pháp phát hiện điểm đặc trưng ảnh**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.9%2B-green.svg)](https://opencv.org/)
[![scikit-image](https://img.shields.io/badge/scikit--image-Latest-yellow.svg)](https://scikit-image.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-Latest-orange.svg)](https://mediapipe.dev/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-red.svg)](https://streamlit.io/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-Plotting-blueviolet.svg)](https://matplotlib.org/)
[![Pandas](https://img.shields.io/badge/Pandas-Data--Analysis-lightgrey.svg)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-Scientific--Computing-ff69b4.svg)](https://numpy.org/)
[![Pillow](https://img.shields.io/badge/Pillow-Image--Processing-informational.svg)](https://python-pillow.org/)

| | |
|:---|:---|
|  **Trường** | Trường Đại học Kinh tế TP.HCM (UEH) |
|  **Môn học** | Xử lý và Phân tích Hình ảnh |

</div>

---

##  Giới thiệu | Introduction

**[VI]** Dự án nghiên cứu, triển khai và so sánh các phương pháp phát hiện điểm đặc trưng ảnh (Keypoint Detection), bao gồm **5 phương pháp truyền thống/toán học** (Harris, SIFT, ORB, FAST, LoG/DoH) và **1 phương pháp dựa trên học máy** (MediaPipe Pose). Kèm theo là ứng dụng web demo tương tác cho phép người dùng tải ảnh lên và quan sát kết quả của từng phương pháp theo thời gian thực.

**[EN]** This project studies, implements, and compares multiple keypoint detection methods — 5 classical/mathematical approaches (Harris, SIFT, ORB, FAST, LoG/DoH) and 1 machine learning-based approach (MediaPipe Pose) — along with an interactive Streamlit web app where users can upload images and observe each method's output side by side.

---

##  Tính năng | Features

| Tính năng | Mô tả |
|:---|:---|
|  **6 phương pháp** | Triển khai đầy đủ Harris, SIFT, ORB, FAST, LoG/DoH, MediaPipe trên cùng một nền tảng |
|  **So sánh định lượng** | Đo lường số keypoint, thời gian xử lý, phân bố không gian trên cùng bộ ảnh test |
|  **Web app 2 tab** | Tab phát hiện keypoint và tab so khớp đối tượng (SIFT Feature Matching) |
|  **Đa dạng input** | Hỗ trợ JPG, PNG (kể cả ảnh có alpha channel), ảnh người, ảnh vật thể |
|  **Workflow chuẩn** | Toàn bộ sprint, issue, phân công quản lý trên GitHub Project Board |

---

##  Các phương pháp | Methods

| # | Phương pháp | Loại | Thư viện | Tham số chính | Đặc điểm |
|:---:|:---|:---:|:---:|:---:|:---|
| 1 | **Harris Corner Detector** | Classical | `OpenCV` | `k=0.04` · `threshold=0.01` | Phát hiện góc cạnh, nền tảng lý thuyết cổ điển |
| 2 | **SIFT** | Classical | `OpenCV` | `nfeatures=500` | Bất biến tỉ lệ và góc xoay, descriptor mạnh |
| 3 | **ORB** | Classical | `OpenCV` | `nfeatures=500` | Nhanh, miễn phí bản quyền, thay thế SIFT/SURF |
| 4 | **FAST** | Classical | `OpenCV` | `threshold=10` · `nms=True` | Tốc độ cao, phù hợp real-time trên thiết bị yếu |
| 5 | **LoG / DoH** | Blob Detection | `scikit-image` | `max_sigma=30` | Phát hiện vùng đặc trưng (blob), dựa trên đạo hàm bậc 2 |
| 6 | **MediaPipe Pose** | ML-based | `MediaPipe` | — | 33 keypoints ngữ nghĩa trên cơ thể người |

> **Lưu ý:** Dự án sử dụng `opencv-python` thay vì `opencv-contrib-python`.  
> Bằng sáng chế SIFT đã hết hạn tháng 3/2020 — SIFT hiện có sẵn trong module chính của OpenCV từ phiên bản 4.4+.

---

##  Ứng dụng Web | Web Application

### Tab 1 — Keypoint Detection

| Bước | Thao tác |
|:---:|:---|
| 1 | Upload ảnh bất kỳ (JPG, PNG — kể cả PNG có alpha channel) |
| 2 | Tích chọn một hoặc nhiều phương pháp muốn chạy |
| 3 | Nhấn **"Phân tích ảnh"** — kết quả hiển thị song song theo từng cột |
| 4 | Xem bảng tổng hợp: số keypoint và thời gian xử lý (ms) của mỗi method |

### Tab 2 — SIFT Object Matching

| Bước | Thao tác |
|:---:|:---|
| 1 | Upload **Ảnh A** và **Ảnh B** (2 uploader riêng biệt) |
| 2 | Nhấn **"So khớp đối tượng"** |
| 3 | Xem ảnh kết quả với đường nối các keypoint tương đồng |
| 4 | Đọc nhận xét tự động: ✅ Cùng đối tượng / ⚠️ Khó xác định / ❌ Khác đối tượng |

---

##  Cấu trúc thư mục | Project Structure

```
keypoint-detection-project/
│
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md
│       └── feature_request.md
│
├── app/
│   ├── streamlit_app.py          # Web app chính (2 tab)
│   └── image_utils.py            # Tiền xử lý ảnh, xử lý edge cases
│
├── methods/
│   ├── base_detector.py          # Interface chuẩn cho toàn bộ methods
│   ├── harris.py                 # Harris Corner Detector
│   ├── sift.py                   # SIFT + match_sift() cho feature matching
│   ├── orb.py                    # ORB Detector
│   ├── fast.py                   # FAST Detector
│   ├── blob_detector.py          # LoG + DoH Blob Detection
│   └── mediapipe_kp.py           # MediaPipe Pose (33 keypoints)
│
├── evaluation/
│   ├── compare.py                # Script đo lường 5 methods × 4 metrics
│   ├── visualize.py              # Figures so sánh side-by-side
│   ├── results.csv               # Kết quả đo lường thực tế
│   ├── charts/                   # Biểu đồ so sánh (PNG)
│   │   ├── keypoint_count.png
│   │   ├── processing_time.png
│   │   └── distribution.png
│   └── figures/                  # Figures visualize từng ảnh test
│       ├── compare_<image>.png
│       ├── blob_vs_corner.png
│       └── speed_ranking.png
│
├── notebooks/
│   ├── harris_demo.ipynb
│   ├── sift_demo.ipynb
│   ├── orb_demo.ipynb
│   ├── fast_demo.ipynb
│   ├── blob_demo.ipynb
│   └── mediapipe_demo.ipynb
│
├── data/
│   ├── general/                  # Ảnh chung — test Harris, SIFT, ORB, FAST
│   ├── blob/                     # Ảnh blob — test LoG/DoH
│   ├── people/                   # Ảnh người — test MediaPipe
│   ├── matching_pairs/           # Cặp ảnh — test SIFT Matching
│   └── README.md                 # Nguồn gốc ảnh test
│
├── report/
│   ├── theory_draft.md           # Tóm tắt lý thuyết 5 methods
│   ├── T13a_classical.md         # Lý thuyết Harris / SIFT / ORB / FAST
│   ├── T13b_ml_evaluation.md     # MediaPipe + LoG/DoH + kết quả thực nghiệm
│   ├── T13c_webapp_conclusion.md # Mô tả web app + kết luận
│   └── final_report.pdf          # Báo cáo hoàn chỉnh
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

##  Cài đặt | Installation

> **Yêu cầu hệ thống:** Python 3.10+ · pip · Git

### Bước 1 — Clone repository

```bash
git clone https://github.com/Sunphuynx/keypoint-detection-project.git
cd keypoint-detection-project
```

### Bước 2 — Tạo môi trường ảo *(khuyến nghị)*

```bash
python -m venv venv
```

```bash
# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### Bước 3 — Cài đặt dependencies

```bash
pip install -r requirements.txt
```

### Bước 4 — Chạy web app

```bash
streamlit run app/streamlit_app.py
```

Mở trình duyệt và truy cập: `http://localhost:8501`

---

##  Dependencies

| Package | Phiên bản | Mục đích |
|:---|:---:|:---|
| `opencv-python` | 4.9.0.80 | Xử lý ảnh, Harris / SIFT / ORB / FAST |
| `scikit-image` | 0.22.0 | Blob detection — LoG và DoH |
| `mediapipe` | 0.10.9 | Pose estimation — 33 body keypoints |
| `streamlit` | 1.33.0 | Web application framework |
| `torch` | 2.2.0 | PyTorch backend (hỗ trợ ML pipeline) |
| `numpy` | 1.26.4 | Tính toán ma trận và xử lý dữ liệu |
| `matplotlib` | 3.8.0 | Vẽ biểu đồ và visualization |
| `Pillow` | 10.2.0 | Đọc/ghi và convert định dạng ảnh |
| `pandas` | 2.2.0 | Lưu và phân tích kết quả đo lường |

---

##  Hướng dẫn sử dụng | Usage

### Chạy từng phương pháp riêng lẻ

Tất cả các phương pháp tuân theo cùng một interface chuẩn định nghĩa tại `methods/base_detector.py`:

```python
from methods.harris import detect_harris
from methods.sift import detect_sift
from methods.orb import detect_orb
from methods.fast import detect_fast
from methods.blob_detector import detect_blobs
from methods.mediapipe_kp import detect_mediapipe

# Tất cả đều trả về cùng format:
# (keypoints_list, annotated_image_numpy, processing_time_ms)

keypoints, image, time_ms = detect_harris("data/general/general_01.jpg")
keypoints, image, time_ms = detect_sift("data/general/general_01.jpg")
keypoints, image, time_ms = detect_fast("data/general/general_01.jpg")
keypoints, image, time_ms = detect_blobs("data/blob/blob_01.jpg", method="log")
keypoints, image, time_ms = detect_mediapipe("data/people/people_01.jpg")
```

### Chạy SIFT Feature Matching

```python
from methods.sift import match_sift

num_matches, match_image, time_ms = match_sift(
    image_path1="data/matching_pairs/pair1_a.jpg",
    image_path2="data/matching_pairs/pair1_b.jpg",
    top_n=50
)
print(f"Tìm thấy {num_matches} điểm khớp ({time_ms:.1f}ms)")
```

### Chạy toàn bộ evaluation

```bash
# Đo lường 5 methods trên toàn bộ bộ ảnh test → lưu results.csv
python evaluation/compare.py

# Tạo figures và biểu đồ so sánh → lưu vào charts/ và figures/
python evaluation/visualize.py
```

Kết quả lưu tại:
- `evaluation/results.csv` — số liệu thô
- `evaluation/charts/` — 3 biểu đồ PNG
- `evaluation/figures/` — figures so sánh side-by-side

### Chạy notebook demo từng method

```bash
jupyter notebook notebooks/
```

Mỗi method có 1 notebook riêng: `harris_demo.ipynb`, `sift_demo.ipynb`, `orb_demo.ipynb`, `fast_demo.ipynb`, `blob_demo.ipynb`, `mediapipe_demo.ipynb`

---

##  Kết quả | Results

> Xem báo cáo đầy đủ với số liệu thực nghiệm tại `report/final_report.pdf`

### Hướng dẫn chọn phương pháp theo usecase

| Usecase | Phương pháp đề xuất | Lý do |
|:---|:---:|:---|
| Real-time, thiết bị yếu | **FAST** | Nhanh nhất trong nhóm classical |
| Feature matching, object retrieval | **SIFT** | Descriptor mạnh, bất biến tỉ lệ/góc xoay |
| Cần nhẹ, không GPU, royalty-free | **ORB** | Kết hợp FAST + BRIEF, rất nhẹ |
| Phát hiện vùng đặc trưng (blob, tế bào) | **LoG / DoH** | Phát hiện vùng chứ không phải góc |
| Phân tích tư thế, nhận diện hành động | **MediaPipe Pose** | 33 keypoints ngữ nghĩa, độ chính xác cao |
| Học thuật, nghiên cứu lý thuyết cơ bản | **Harris** | Nền tảng toán học, dễ hiểu, dễ phân tích |

---

##  Thành viên | Team

| Thành viên | Vai trò | Trách nhiệm chính |
|:---|:---:|:---|
| **Chí Tâm** | Tech Lead · Algorithm Engineer | Setup repo · `base_detector.py` · FAST · Tích hợp web app · Release |
| **Duy Quang** | Classical Methods Engineer | Harris · SIFT · ORB · Visualization · Báo cáo lý thuyết classical |
| **Lan Thanh** | ML Engineer · Evaluation Lead | LoG/DoH · MediaPipe · Evaluation metrics · Báo cáo ML + kết quả |
| **Trọng Nguyên** | Web App Developer · Report Lead | Dataset · Streamlit app · SIFT Matching · Tổng hợp báo cáo |

---

##  GitHub Project

Toàn bộ tiến độ, phân công và sprint được quản lý tại GitHub Project Board:

 **[Xem Project Board](https://github.com/Sunphuynx/keypoint-detection-project/projects)**

### Quy ước đặt tên branch

```
feature/harris-implementation      ← tính năng mới
fix/mediapipe-no-person-error      ← bug fix
docs/update-readme                 ← tài liệu
eval/comparison-metrics            ← evaluation
app/streamlit-ui                   ← web app
```

### Quy ước commit message

```
feat: add harris corner detector module
fix: resolve mediapipe no-person edge case
docs: update README with bilingual content
eval: add processing time chart to compare.py
app: integrate SIFT matching into tab 2
```

---

##  License

Dự án được phân phối theo giấy phép **MIT License** — xem file [LICENSE](LICENSE) để biết thêm chi tiết.

---

<div align="center">
  <b>Keypoint Detection Project</b><br>
  <sub>Thực hiện bởi nhóm sinh viên · Trường Đại học Kinh tế TP.HCM (UEH)<br>
  Môn học: Xử lý và Phân tích Hình ảnh · Năm học 2024 – 2025</sub>
</div>