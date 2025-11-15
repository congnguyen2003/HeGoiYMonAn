# 🍳 Hệ Thống Gợi Ý Công Thức Nấu Ăn Dựa Trên Cơ Sở Tri Thức

Một ứng dụng web hiện đại sử dụng **cơ sở tri thức (Knowledge Base)** để giúp người dùng tìm kiếm công thức nấu ăn phù hợp dựa trên nguyên liệu mà họ có.

## ✨ Tính Năng Chính

- **⬇️ Suy Diễn Tiến (Forward Chaining)**
  - Nhập danh sách nguyên liệu có sẵn
  - Hệ thống gợi ý các món có thể nấu được
  - Hiển thị công thức chi tiết và video hướng dẫn

- **⬆️ Suy Diễn Lùi (Backward Chaining)**
  - Nhập tên một món ăn
  - Hệ thống hiển thị nguyên liệu cần thiết

- **💡 Gợi Ý Gần Đúng (Partial Matching)**
  - Tìm các món ăn gần phù hợp nhất
  - Hiển thị độ khớp (%) và nguyên liệu còn thiếu

- **⚙️ Quản Lý Cơ Sở Tri Thức**
  - Giao diện Admin để thêm, sửa, xóa các luật
  - Bảo vệ bằng mật khẩu

- **🇻🇳 Hỗ Trợ Tiếng Việt**
  - Hiển thị tên nguyên liệu với dấu
  - Giao diện 100% tiếng Việt

## 🛠️ Tech Stack

### Backend
- **Python 3.7+**
- **Flask** - Web framework
- **flask-cors** - CORS support
- **JSON** - Cơ sở tri thức

### Frontend
- **React 18**
- **CSS3** - Responsive design
- **Gradient & Modern UI**

## 🚀 Cài Đặt Nhanh

### Yêu Cầu
- Python 3.7+
- Node.js 12+
- npm

### 1. Backend

```bash
cd backend
pip install flask flask-cors
python app.py
```

Kết quả: `Running on http://127.0.0.1:5000`

### 2. Frontend

```bash
cd frontend
npm install
npm start
```

Kết quả: `http://localhost:3000` (tự động mở)

## 📖 Hướng Dẫn Sử Dụng

### 👤 Người Dùng

#### Tab 1: Suy Diễn Tiến
1. Nhập nguyên liệu: `thịt gà, sả, ớt, gừng`
2. Nhấp "🔍 Gợi ý món ăn"
3. Xem kết quả:
   - ✅ Món có thể nấu được
   - 💡 Gợi ý gần đúng

#### Tab 2: Suy Diễn Lùi
1. Nhập tên món: `Gà kho gừng`
2. Nhấp "🔍 Tìm kiếm"
3. Xem nguyên liệu + công thức + video

### ⚙️ Quản Trị Viên

1. Nhấp "⚙️ Quản trị viên"
2. Đăng nhập (mật khẩu: `admin123`)
3. Thêm/Sửa/Xóa các luật:
   - ID: `R101`
   - Tên món: `Gà kho gừng`
   - Nguyên liệu: `co_thit_ga, co_gung`
   - Công thức: (mô tả)
   - Video: (link YouTube)
4. Nhấp "💾 Lưu tất cả thay đổi"

⚠️ **Quan Trọng**: Luôn nhấp "Lưu" trước khi tắt ứng dụng!

## 📁 Cấu Trúc Dự Án

```
web/
├── backend/
│   ├── app.py              # Flask app chính
│   ├── inference.py        # Thuật toán suy diễn
│   ├── rules.json          # Cơ sở tri thức
│   ├── synonyms.json       # Từ đồng nghĩa
│   └── ingredient_names.json # Tên Việt
├── frontend/
│   ├── src/
│   │   ├── App.jsx         # Component chính
│   │   ├── App.css
│   │   ├── pages/
│   │   │   ├── UserPage.jsx
│   │   │   ├── AdminPage.jsx
│   │   │   └── ...
│   │   └── styles/
│   │       ├── UserPage.css
│   │       └── AdminPage.css
│   └── public/
├── HUONG_DAN_CHI_TIET.md  # Hướng dẫn chi tiết
└── huongdan.txt           # Hướng dẫn nhanh
```

## 🔌 API Endpoints

### POST `/api/suggest` - Suy Diễn Tiến
```json
Request: { "ingredients": ["co_thit_ga", "co_gung"] }
Response: { "forward": [...], "partial": [...] }
```

### POST `/api/backward` - Suy Diễn Lùi
```json
Request: { "goal": "Gà kho gừng" }
Response: [{ "dish": "...", "ingredients": [...], ... }]
```

### GET `/api/rules` - Lấy Toàn Bộ Luật
```json
Response: { "rules": [...] }
```

### POST `/api/rules` - Cập Nhật Luật
```json
Request: { "rules": [...] }
Response: { "message": "Cập nhật thành công!" }
```

## 🆘 Khắc Phục Sự Cố

### ❌ Cannot Connect to Server
**Giải pháp**: Kiểm tra backend có chạy không
```bash
cd backend
python app.py
```

### ❌ Module Not Found: flask
**Giải pháp**: Cài đặt dependencies
```bash
pip install flask flask-cors
```

### ❌ Dữ Liệu Admin Không Lưu
**Giải pháp**: Nhấp "💾 Lưu tất cả thay đổi" trước khi tắt

Xem **HUONG_DAN_CHI_TIET.md** để khắc phục các lỗi khác.

## 📝 Ví Dụ Dữ Liệu

### rules.json
```json
{
  "rules": [
    {
      "id": "R01",
      "if": ["co_thit_ga", "co_gung"],
      "then": "Gà kho gừng",
      "recipe": "Ướp thịt gà với gừng, tỏi, nước mắm...",
      "video": "https://www.youtube.com/watch?v=xFzQdCIrgko"
    }
  ]
}
```

### ingredient_names.json
```json
{
  "co_thit_ga": "thịt gà",
  "co_gung": "gừng",
  "co_toi": "tỏi",
  "co_sa": "sả"
}
```

## 🎓 Hướng Dẫn Thêm Công Thức Mới

1. **Qua Giao Diện Admin** (Dễ nhất)
   - Đăng nhập Admin
   - Nhấp "➕ Thêm luật mới"
   - Nhập ID, tên món, nguyên liệu
   - Nhấp "➕ Thêm"
   - Nhấp "💾 Lưu"

2. **Qua File rules.json** (Nâng cao)
   - Mở `backend/rules.json`
   - Thêm object mới vào mảng "rules"
   - Lưu file
   - Khởi động lại backend

## 🔐 Bảo Mật

- **Admin Password**: `admin123` (thay đổi trong App.jsx dòng 26)
- **CORS**: Cho phép localhost:3000 kết nối đến localhost:5000
- **Frontend**: Chỉ Admin có quyền truy cập quản lý

## 📱 Responsive Design

- ✅ Desktop (1200px+)
- ✅ Tablet (768px - 1199px)
- ✅ Mobile (< 768px)

## 🌍 Hỗ Trợ Ngôn Ngữ

- 🇻🇳 Tiếng Việt (100%)

## 📚 Giáo Dục

Dự án này được tạo ra như một bài tập về:
- **Cơ Sở Tri Thức (Knowledge Base)**
- **Forward Chaining** - Từ dữ kiện → kết luận
- **Backward Chaining** - Từ mục tiêu → dữ kiện
- **Partial Matching** - Tìm kiếm gần đúng
- **Web Development** - Full Stack (React + Flask)

## 📄 License

Dự án dành cho mục đích giáo dục.

## 👨‍💻 Tác Giả

Phát triển bởi nhóm học tập - Năm 5, HK1
Trường Đại học (Hệ cơ sở tri thức)

## 📞 Liên Hệ

Để biết thêm thông tin chi tiết, xem file:
📖 **HUONG_DAN_CHI_TIET.md**

---

**Phiên Bản**: 1.0  
**Cập Nhật**: 15/11/2024  
**Trạng Thái**: ✅ Hoạt Động

Chúc bạn nấu ăn thành công! 🍽️😋
