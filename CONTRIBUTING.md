# Quy định làm việc nhóm (Contributing Guidelines)

Dự án: **Nghiên cứu, triển khai và so sánh các phương pháp Nhận diện điểm đặc trưng**

## 1. Môi trường phát triển (Setup)
Để đảm bảo cả nhóm chạy được code mà không gặp lỗi môi trường:
1. Clone dự án về máy: `git clone <repo_url>`
2. (Khuyến nghị) Tạo môi trường ảo: `python -m venv venv`
3. Kích hoạt môi trường:
   - Windows: `venv\Scripts\activate`
   - Linux/Mac: `source venv/bin/activate`
4. Cài đặt thư viện: `pip install -r requirements.txt`

**Tiêu chuẩn Hoàn thành (Definition of Done) cơ bản:**
- `pip install` không báo lỗi.
- Thư mục chuẩn phải nằm đúng vị trí.
- Code mới không phá vỡ tính năng hiện tại.

## 2. Chiến lược nhánh (Branching Strategy)
Dự án sử dụng mô hình **Git Flow đơn giản hóa**:
- **`main`**: Nhánh chứa code ổn định (stable), dùng để demo. Sẽ được khóa (protected) và chỉ nhận code thông qua Pull Request.
- **`develop`**: Nhánh tích hợp (integration) dành cho quá trình phát triển chính.
- **`feature/`**, **`fix/`**, **`docs/`**, **`eval/`**, **`app/`**: Các nhánh chức năng. Bắt nhánh từ `develop`, sau khi xong sẽ tạo Pull Request gộp lại vào `develop`.

## 3. Quy ước đặt tên nhánh (Branch Naming Convention)
Sử dụng các tiền tố sau:
- `feature/tên-chức-năng`: Tính năng mới (VD: `feature/harris-implementation`)
- `fix/tên-lỗi-cần-sửa`: Sửa lỗi (bug fix) (VD: `fix/sift-opencv-version-error`)
- `docs/tên-tài-liệu`: Cập nhật tài liệu (VD: `docs/update-readme`)
- `eval/tên-đánh-giá`: Các phần liên quan đến đánh giá thuật toán (VD: `eval/comparison-metrics`)
- `app/tên-thành-phần-web`: Các chức năng của web app (VD: `app/streamlit-ui`)

## 4. Định dạng Issue (Issue Format)
Khi tạo Issue trên GitHub, vui lòng tuân thủ định dạng sau và gán vào **GitHub Project board**:

```markdown
Title: [TASK-XX] Tên task ngắn gọn

## Mục tiêu
(Mô tả ngắn gọn mục đích của task này là gì)

## Các bước thực hiện
- [ ] Bước 1...
- [ ] Bước 2...

## Definition of Done
- [ ] Code chạy không lỗi.
- [ ] (Các tiêu chí cụ thể của task)
```
- **Labels**: Gắn nhãn phù hợp (`enhancement`, `bug`, `documentation`, `evaluation`)
- **Assignee**: Gán tên thành viên chịu trách nhiệm.

## 5. Quy ước Commit (Commit Convention)
Các commit message cần ngắn gọn, rõ ràng theo chuẩn:
- `feat: ...` : Thêm chức năng mới (VD: `feat: add harris corner detector module`)
- `fix: ...` : Sửa lỗi (VD: `fix: resolve SIFT import error with opencv-contrib`)
- `docs: ...` : Thay đổi tài liệu (VD: `docs: update README with installation steps`)
- `eval: ...` : Cập nhật các đánh giá, test (VD: `eval: add processing time measurement to compare.py`)
- `app: ...` : Cập nhật giao diện/chức năng web app (VD: `app: integrate ORB into streamlit sidebar`)
