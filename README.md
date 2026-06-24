<h1 align="center">🛠️ Task Bug Management System</h1>

<p align="center">
  <strong>Hệ thống Quản lý Task và Theo dõi Lỗi Phần mềm</strong><br/>
  Đồ án Tốt nghiệp — Trường Đại học Thủy Lợi
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Laravel-10.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white"/>
  <img src="https://img.shields.io/badge/PHP-8.1-777BB4?style=for-the-badge&logo=php&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge"/>
</p>

---

## 👩‍🎓 Thông tin sinh viên

| | |
|---|---|
| **Sinh viên thực hiện** | Hoàng Yên Nhi |
| **Lớp** | 64HTTT3 |
| **Trường** | Đại học Thủy Lợi |
| **Ngành** | Hệ thống Thông tin |
| **Loại đồ án** | Tốt nghiệp |

---

## 📋 Giới thiệu

**Task Bug Management System** là hệ thống quản lý dự án phần mềm nội bộ, hỗ trợ toàn bộ vòng đời phát triển từ khi khởi tạo task đến khi nghiệm thu. Hệ thống tích hợp quy trình kiểm thử chất lượng, theo dõi lỗi, và đánh giá hiệu suất thành viên thông qua hệ thống KPI tự động.

### Vấn đề giải quyết

Trong quá trình phát triển phần mềm nhóm, các nhóm thường gặp khó khăn trong việc:
- Theo dõi tiến độ công việc của từng thành viên một cách minh bạch
- Quản lý vòng đời lỗi (bug) từ khi phát hiện đến khi xác nhận đóng
- Đánh giá khách quan hiệu suất làm việc của lập trình viên và kiểm thử viên
- Truy xuất nguồn gốc lỗi production về task/người phụ trách cụ thể

Hệ thống này giải quyết toàn bộ các vấn đề trên trong một nền tảng thống nhất.

---

## ✨ Tính năng chính

### 🔐 Xác thực & Phân quyền
- Đăng nhập bằng **username** (không dùng email)
- Tự động khóa tài khoản sau **3 lần sai mật khẩu** (30 phút)
- Bắt buộc đổi mật khẩu lần đầu đăng nhập
- Phân quyền 4 vai trò: **Admin / PM / Developer / Tester**

### 📁 Quản lý Dự án
- Tạo dự án, phân công thành viên với vai trò rõ ràng
- Thanh tiến độ dự án theo tỷ lệ task hoàn thành
- Quản lý thành viên linh hoạt (thêm, xóa, đổi vai trò)

### ✅ Quản lý Task
- Phân cấp task cha–con (root task → child task)
- 6 loại công việc: Task, Subtask, Bug, Research, Fix, Test
- Luồng trạng thái: `Todo → In Progress → Ready to Test → Review Approved → Done`
- **Auto-cascade**: con hoàn thành → cha tự động cập nhật trạng thái
- Lịch sử đầy đủ mọi lần chuyển trạng thái

### 🐛 Theo dõi Bug
- **Bug QA**: Tester nhấn **Fail** → modal tạo bug, tự gán cho developer gốc, task cha hoàn nguyên
- **Bug Production**: Ghi nhận lỗi từ môi trường sản xuất, liên kết với story gây ra lỗi
- Phân biệt rõ Bug QA và Bug Production trong bộ lọc danh sách

### 📊 KPI Tự động
| Sự kiện | Điểm trừ | Đối tượng |
|---------|----------|----------|
| Task hoàn thành trễ hạn | −2đ/ngày | Developer |
| Bug con được tạo | −0.25đ/bug | Developer |
| Giữ task ở RTT > 48 giờ | −0.5đ/ngày | Tester |
| Bug Production | −5đ | Developer + Tester gốc |

> Công thức: **Điểm = max(0, 100 + Σ điểm trừ)** theo từng tháng

### 📈 Báo cáo Chất lượng
- DRE % (Defect Removal Efficiency)
- Retest rate theo developer
- Thời gian sửa lỗi trung bình
- Completion rate theo thành viên

### 💬 Cộng tác
- Bình luận rich text trên mọi task/bug
- Upload ảnh inline vào nội dung comment
- Đính kèm tệp (ảnh, PDF, Office, zip — tối đa 20 MB)
- Thông báo nội bộ theo sự kiện (giao task, bug sẵn sàng test, review approved)

---

### Công nghệ sử dụng

| Thành phần | Công nghệ |
|-----------|----------|
| Backend | Laravel 10, PHP 8.1 |
| Database | MySQL 8.0 (Eloquent ORM) |
| Frontend | Blade Templates, CSS thuần (CSS Variables) |
| Authentication | Session-based, Username login |
| File Storage | Laravel Storage (local disk) |

---

## 🚀 Hướng dẫn cài đặt

### Yêu cầu môi trường
- PHP >= 8.1
- Composer
- MySQL >= 8.0

### Các bước cài đặt

```bash
# 1. Clone repository
git clone https://github.com/<your-username>/task_bug.git
cd task_bug

# 2. Cài đặt dependencies
composer install

# 3. Cấu hình môi trường
cp .env.example .env
php artisan key:generate

# 4. Cấu hình database trong .env
# DB_DATABASE=task_bug
# DB_USERNAME=root
# DB_PASSWORD=

# 5. Chạy migration và seed dữ liệu mẫu
php artisan migrate
php artisan db:seed --class=DemoSeeder

# 6. Khởi động server
php artisan serve
```

Truy cập: `http://localhost:8000`

<p align="center">
  Được xây dựng với ❤️ bởi <strong>Hoàng Yên Nhi</strong> — Lớp 64HTTT3, Đại học Thủy Lợi
</p>
