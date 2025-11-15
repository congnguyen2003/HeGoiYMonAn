═══════════════════════════════════════════════════════════════════════════════
                 🍳 HỆ THỐNG GỢI Ý CÔNG THỨC NẤU ĂN DỰA TRÊN CƠ SỞ TRI THỨC
═══════════════════════════════════════════════════════════════════════════════

📋 MỤC LỤC
──────────
1. Giới thiệu hệ thống
2. Cấu trúc thư mục
3. Cài đặt và chạy ứng dụng
4. Hướng dẫn sử dụng giao diện Người Dùng
5. Hướng dẫn sử dụng giao diện Quản Trị Viên
6. Mô tả các API
7. Cấu trúc dữ liệu
8. Ghi chú kỹ thuật
9. Khắc phục sự cố


═══════════════════════════════════════════════════════════════════════════════
1️⃣  GIỚI THIỆU HỆ THỐNG
═══════════════════════════════════════════════════════════════════════════════

Hệ thống gợi ý công thức nấu ăn là một ứng dụng web hiện đại sử dụng cơ sở tri
thức (Knowledge Base) để giúp người dùng tìm kiếm công thức nấu ăn phù hợp dựa
trên nguyên liệu mà họ có.

🎯 CÁC TÍNH NĂNG CHÍNH:
───────────────────────
✅ Suy diễn tiến (Forward Chaining):
   - Nhập danh sách nguyên liệu có sẵn
   - Hệ thống tự động gợi ý các món có thể nấu được
   - Hiển thị công thức chi tiết và video hướng dẫn

✅ Suy diễn lùi (Backward Chaining):
   - Nhập tên món ăn mong muốn
   - Hệ thống tự động hiển thị nguyên liệu cần thiết

✅ Gợi ý gần đúng (Partial Matching):
   - Tìm các món ăn gần phù hợp nhất
   - Hiển thị độ khớp (%) và nguyên liệu còn thiếu

✅ Quản lý cơ sở tri thức:
   - Giao diện Admin để thêm, sửa, xóa các luật
   - Bảo vệ bằng mật khẩu

✅ Hỗ trợ tiếng Việt:
   - Hiển thị tên nguyên liệu đầy đủ với dấu
   - Giao diện hoàn toàn tiếng Việt


═══════════════════════════════════════════════════════════════════════════════
2️⃣  CẤU TRÚC THƯ MỤC
═══════════════════════════════════════════════════════════════════════════════

web/
├── backend/                          # Backend Python Flask
│   ├── app.py                       # Ứng dụng Flask chính
│   ├── inference.py                 # Thuật toán suy diễn
│   ├── rules.json                   # Cơ sở tri thức (các luật)
│   ├── synonyms.json                # Từ đồng nghĩa cho nguyên liệu
│   ├── ingredient_names.json        # Tên tiếng Việt của nguyên liệu
│   └── __pycache__/                 # Cache Python
│
├── frontend/                         # Frontend React
│   ├── package.json                 # Phụ thuộc npm
│   ├── public/
│   │   ├── index.html               # HTML chính
│   │   ├── ingredient_names.json    # (Copy từ backend)
│   │   └── synonyms.json            # (Copy từ backend)
│   ├── src/
│   │   ├── App.jsx                  # Thành phần ứng dụng chính
│   │   ├── App.css                  # Kiểu dáng ứng dụng
│   │   ├── index.js                 # Entry point
│   │   ├── pages/
│   │   │   ├── UserPage.jsx         # Giao diện người dùng
│   │   │   └── AdminPage.jsx        # Giao diện quản trị viên
│   │   └── styles/
│   │       ├── UserPage.css         # Kiểu dáng trang người dùng
│   │       └── AdminPage.css        # Kiểu dáng trang quản trị viên
│   └── node_modules/                # Các gói npm
│
└── huongdan.txt                      # File hướng dẫn ban đầu


═══════════════════════════════════════════════════════════════════════════════
3️⃣  CÀI ĐẶT VÀ CHẠY ỨNG DỤNG
═══════════════════════════════════════════════════════════════════════════════

YÊƯCẦU TRƯỚC CÀI ĐẶT:
───────────────────────
✓ Python 3.7 hoặc cao hơn
✓ Node.js 12.0 hoặc cao hơn
✓ npm hoặc yarn
✓ Git (tùy chọn)

BƯỚC 1️⃣ : CÀI ĐẶT BACKEND
──────────────────────────
1. Mở terminal và điều hướng đến thư mục dự án
2. Di chuyển vào thư mục backend:
   
   cd backend

3. Cài đặt các thư viện Python cần thiết:
   
   pip install flask flask-cors

4. Chạy ứng dụng Flask:
   
   python app.py

   Bạn sẽ thấy:
   ✓ * Running on http://127.0.0.1:5000
   ✓ * Press CTRL+C to quit

💡 Lưu ý: Giữ terminal này mở và chạy, vì nó là server backend

BƯỚC 2️⃣ : CÀI ĐẶT FRONTEND
────────────────────────────
1. Mở terminal mới (giữ terminal backend đang chạy)
2. Di chuyển vào thư mục frontend:
   
   cd frontend

3. Cài đặt các gói npm:
   
   npm install

4. Chạy ứng dụng React:
   
   npm start

   Trình duyệt sẽ tự động mở trang:
   ✓ http://localhost:3000

BƯỚC 3️⃣ : KIỂM TRA KẾT NỐI
────────────────────────────
- Nếu thấy giao diện, ứng dụng đã khởi động thành công!
- Nếu có lỗi "Cannot connect to server", kiểm tra:
  ✓ Terminal backend vẫn đang chạy tại http://127.0.0.1:5000
  ✓ Không có lỗi trong console browser


═══════════════════════════════════════════════════════════════════════════════
4️⃣  HƯỚNG DẪN SỬ DỤNG GIAO DIỆN NGƯỜI DÙNG
═══════════════════════════════════════════════════════════════════════════════

Giao diện người dùng có 2 tab chính:

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📌 TAB 1: SỰ DIỄN TIẾN (⬇️ Forward Chaining)
──────────────────────────────────────────────

Mục đích: Tìm các món ăn có thể nấu được từ nguyên liệu bạn có

CÁCH SỬ DỤNG:
1. Nhập danh sách nguyên liệu bạn có vào ô "Tìm món ăn từ nguyên liệu"
   
   Ví dụ có thể nhập:
   • Thịt gà, sả, ớt, gừng (tiếng Việt có dấu)
   • co_thit_ga; co_sa; co_ot (code nguyên liệu)
   • Các cách kết hợp của cả hai

   💡 Mẹo: Dùng dấu phẩy (,), dấu chấm phẩy (;) hoặc xuống dòng để phân tách

2. Nhấp nút "🔍 Gợi ý món ăn"

3. KẾT QUẢ SẼ HIỂN THỊ:

   ✅ PHẦN 1: "Món có thể nấu được"
   ─────────────────────────────────
   Bảng hiển thị:
   • #: Số thứ tự
   • Tên món ăn: Tên món được gợi ý
   • Nguyên liệu: Các tag hiển thị nguyên liệu cần thiết
   • Công thức: Click "Xem công thức" để xem hướng dẫn nấu
   • Video: Iframe hiển thị video YouTube hướng dẫn

   💡 Cách sử dụng:
   - Click vào "Xem công thức" để mở chi tiết công thức
   - Video sẽ hiển thị trực tiếp (nếu có link)

   💡 Gợi ý gần đúng"
   ─────────────────
   Bảng hiển thị các món ăn mà bạn không đủ nguyên liệu:
   • #: Số thứ tự
   • Món gợi ý: Tên món ăn gần phù hợp
   • Độ khớp: Phần trăm khớp (%):
     - 100% = Có đủ tất cả nguyên liệu
     - 75% = Thiếu 1/4 nguyên liệu
     - Thanh tiến độ hiển thị trực quan
   • Thiếu nguyên liệu: Hiển thị nguyên liệu còn thiếu (tag đỏ)

   💡 Ý NGHĨA:
   - Nếu bạn thiếu 1-2 nguyên liệu nhỏ, có thể thử nấu
   - Độ khớp càng cao, khả năng thành công càng lớn

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

📌 TAB 2: SỰ DIỄN LÙI (⬆️ Backward Chaining)
──────────────────────────────────────────────

Mục đích: Tìm các nguyên liệu cần thiết cho một món ăn bất kỳ

CÁCH SỬ DỤNG:
1. Nhập tên một món ăn vào ô "Tìm nguyên liệu từ tên món"
   
   Ví dụ:
   • Gà kho gừng
   • Bò xào hành tây
   • Tôm nướng bơ tỏi
   • Nem rán

2. Nhấp nút "🔍 Tìm kiếm" (hoặc nhấn Enter)

3. KẾT QUẢ SẼ HIỂN THỊ:

   ✨ Bảng kết quả tìm kiếm
   ─────────────────────
   • Tên món ăn: Tên chính xác của món
   • Nguyên liệu cần thiết: Danh sách các tag nguyên liệu
   • Công thức: Bước nấu chi tiết (click để xem)
   • Video hướng dẫn: Video YouTube (nếu có)

   💡 CÁCH SỬ DỤNG:
   - Xem danh sách nguyên liệu và kiểm tra xem bạn có đủ không
   - Click "Xem công thức" để đọc hướng dẫn nấu chi tiết
   - Click video để xem hướng dẫn nấu trực quan

   ⚠️ LƯU Ý:
   - Nếu không tìm thấy món, hãy kiểm tra lại tên
   - Tên phải khớp với cơ sở tri thức của hệ thống


═══════════════════════════════════════════════════════════════════════════════
5️⃣  HƯỚNG DẪN SỬ DỤNG GIAO DIỆN QUẢN TRỊ VIÊN
═══════════════════════════════════════════════════════════════════════════════

Giao diện Admin cho phép quản lý cơ sở tri thức (các luật).

🔐 ĐĂNG NHẬP QUẢN TRỊ VIÊN
───────────────────────────
1. Nhấp vào nút "⚙️ Quản trị viên" ở thanh navbar
2. Nhập mật khẩu (mặc định: admin123)
3. Nhấp "🔓 Đăng nhập"

💡 Lưu ý: Đó là mật khẩu ban đầu. Bạn có thể thay đổi nó trong file App.jsx

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚙️  QUẢN LÝ CÁC LUẬT
────────────────────

PHẦN 1: THÊM LUẬT MỚI
────────────────────
Bấm vào mục "➕ Thêm luật mới"

Các trường cần nhập:
1. ID (ví dụ: R101)
   - Mã định danh duy nhất cho luật
   - Công thức: R + số (ví dụ: R01, R02, R100)

2. Tên món ăn
   - Tên công thức cuối cùng (ví dụ: "Gà kho gừng")

3. Nguyên liệu
   - Danh sách các code nguyên liệu phân tách bằng dấu phẩy
   - Ví dụ: co_thit_ga, co_gung, co_toi
   - Các code bắt đầu bằng "co_" (từ tiếng Anh)

4. Nhấp nút "➕ Thêm"
   - Luật mới sẽ được thêm vào danh sách
   - Trạng thái sẽ chuyển thành "⚠️ Có thay đổi chưa lưu"

⚠️  LƯU Ý QUAN TRỌNG:
- Phải bấm "💾 Lưu tất cả thay đổi" để lưu vào database
- Nếu không lưu, dữ liệu sẽ mất khi reload trang

PHẦN 2: CHỈNH SỬA LUẬT CÓ SẴN
──────────────────────────────
1. Scroll xuống mục "📋 Danh sách các luật"
2. Tìm luật cần sửa
3. Nhấp vào các ô input để chỉnh sửa:
   - 📝 Điều kiện (if): Danh sách nguyên liệu
   - 🍽️ Kết luận (then): Tên món ăn
   - 📖 Công thức (recipe): Hướng dẫn nấu
   - 🎥 Link Video: URL video hướng dẫn

   Ví dụ video URL:
   - https://www.youtube.com/watch?v=xFzQdCIrgko
   - https://www.youtube.com/embed/xFzQdCIrgko

4. Thay đổi sẽ được lưu tự động trong ứng dụng
5. Trạng thái thay đổi thành "⚠️ Có thay đổi chưa lưu"

PHẦN 3: XÓA LUẬT
────────────────
1. Tìm luật cần xóa
2. Nhấp nút "🗑️ Xóa" ở góc phải của card luật
3. Xác nhận xóa trong hộp thoại
4. Luật sẽ bị loại bỏ khỏi danh sách
5. Nhấp "💾 Lưu tất cả thay đổi" để lưu vào database

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

💾 LƯU CÁC THAY ĐỔI
────────────────────
1. Tất cả các thay đổi được hiển thị trạng thái:
   ✅ "✅ Đã lưu" = Tất cả thay đổi đã được lưu
   ⚠️  "⚠️ Có thay đổi chưa lưu" = Cần lưu

2. Để lưu:
   - Nhấp nút "💾 Lưu tất cả thay đổi" ở đầu hoặc cuối trang
   - Chờ thông báo "✅ Đã lưu thành công!"

3. File rules.json sẽ được cập nhật tự động trên server

⚠️  CẢNH BÁO:
- Nếu tắt ứng dụng mà không lưu, tất cả thay đổi sẽ mất
- Luôn nhấp "Lưu" trước khi đóng tab hoặc refresh trang


═══════════════════════════════════════════════════════════════════════════════
6️⃣  MÔ TẢ CÁC API
═══════════════════════════════════════════════════════════════════════════════

Backend cung cấp các API REST để frontend gọi:

┌─ POST /api/suggest
├─ Mục đích: Suy diễn tiến (tìm món từ nguyên liệu)
├─ Request:
│  {
│    "ingredients": ["co_thit_ga", "co_gung", "co_toi"]
│  }
├─ Response:
│  {
│    "forward": [
│      {
│        "dish": "Gà kho gừng",
│        "ingredients": ["co_thit_ga", "co_gung"],
│        "recipe": "Ướp thịt gà...",
│        "video": "https://youtube.com/watch?v=..."
│      }
│    ],
│    "partial": [
│      {
│        "dish": "Gà kho sả",
│        "score": 0.75,
│        "missing": ["co_sa"]
│      }
│    ]
│  }
└─

┌─ POST /api/backward
├─ Mục đích: Suy diễn lùi (tìm nguyên liệu từ tên món)
├─ Request:
│  {
│    "goal": "Gà kho gừng"
│  }
├─ Response:
│  [
│    {
│      "dish": "Gà kho gừng",
│      "ingredients": ["co_thit_ga", "co_gung", "co_toi", "co_nuoc_mam"],
│      "recipe": "Ướp thịt gà với gừng...",
│      "video": "https://youtube.com/watch?v=..."
│    }
│  ]
└─

┌─ GET /api/rules
├─ Mục đích: Lấy toàn bộ danh sách luật
├─ Request: (không cần body)
├─ Response:
│  {
│    "rules": [
│      {
│        "id": "R01",
│        "if": ["co_thit_ga", "co_gung"],
│        "then": "Gà kho gừng",
│        "recipe": "...",
│        "video": "..."
│      }
│    ]
│  }
└─

┌─ POST /api/rules
├─ Mục đích: Cập nhật toàn bộ danh sách luật
├─ Request:
│  {
│    "rules": [
│      {
│        "id": "R01",
│        "if": ["co_thit_ga", "co_gung"],
│        "then": "Gà kho gừng",
│        "recipe": "...",
│        "video": "..."
│      }
│    ]
│  }
├─ Response:
│  {
│    "message": "Cập nhật thành công!"
│  }
└─


═══════════════════════════════════════════════════════════════════════════════
7️⃣  CẤU TRÚC DỮ LIỆU
═══════════════════════════════════════════════════════════════════════════════

📁 RULES.JSON - Cơ sở tri thức
──────────────────────────────

Cấu trúc:
{
  "rules": [
    {
      "id": "R01",                    // ID duy nhất của luật
      "if": [                         // Điều kiện (danh sách nguyên liệu)
        "co_thit_ga",
        "co_gung"
      ],
      "then": "Gà kho gừng",          // Kết luận (tên món ăn)
      "recipe": "Ướp thịt gà...",    // Công thức nấu chi tiết
      "video": "https://youtube.com/watch?v=xFzQdCIrgko"  // Link video
    }
  ]
}

📁 SYNONYMS.JSON - Từ đồng nghĩa
─────────────────────────────────

Mục đích: Ánh xạ giữa các code nguyên liệu và các từ gọi khác

Ví dụ:
{
  "gừng": ["co_gung", "gung", "gừng"],
  "thịt gà": ["co_thit_ga", "thit_ga", "thịt gà"],
  "sả": ["co_sa", "sa"]
}

💡 Ứng dụng:
- Người dùng nhập "gừng" hoặc "gung" → hệ thống hiểu là "co_gung"
- Hỗ trợ tìm kiếm linh hoạt

📁 INGREDIENT_NAMES.JSON - Tên tiếng Việt
──────────────────────────────────────────

Mục đích: Ánh xạ code → tên tiếng Việt đầy đủ với dấu

Ví dụ:
{
  "co_gung": "gừng",
  "co_thit_ga": "thịt gà",
  "co_sa": "sả",
  "co_toi": "tỏi",
  "co_ot": "ớt",
  "co_nuoc_mam": "nước mắm"
}

💡 Ứng dụng:
- Hiển thị "gừng" thay vì "co_gung" trên giao diện
- Cải thiện trải nghiệm người dùng


═══════════════════════════════════════════════════════════════════════════════
8️⃣  GHI CHÚ KỸ THUẬT
═══════════════════════════════════════════════════════════════════════════════

BACKEND (Python Flask):
───────────────────────
✓ Framework: Flask
✓ CORS: flask-cors (cho phép frontend gọi từ domain khác)
✓ Port: 5000
✓ Encoding: UTF-8

FRONTEND (React):
─────────────────
✓ Framework: React 18
✓ CSS: CSS thuần + Gradient + Flexbox
✓ Port: 3000
✓ Proxy: localhost:5000 (trong package.json)

LƯU Ý KỈ THUẬT:
───────────────
1. CORS: Backend cho phép requests từ frontend
2. JSON Encoding: Tất cả file JSON dùng UTF-8
3. Code Nguyên Liệu: Bắt đầu bằng "co_" (code pattern)
4. Caching: Python .pycache/ có thể xóa an toàn


═══════════════════════════════════════════════════════════════════════════════
9️⃣  KHẮC PHỤC SỰ CỐ
═══════════════════════════════════════════════════════════════════════════════

❌ VẤNĐỀ: "Cannot GET /" hoặc trang trắng
───────────────────────────────────────────
Nguyên nhân: Frontend không tìm thấy server hoặc lỗi React
Giải pháp:
1. Kiểm tra console browser (F12 → Console)
2. Kiểm tra xem backend có chạy không (http://127.0.0.1:5000)
3. Chạy lại npm start
4. Xóa node_modules và cài lại: rm -rf node_modules && npm install

❌ VẤNĐỀ: "Cannot connect to server" hoặc timeout
───────────────────────────────────────────────────
Nguyên nhân: Backend không chạy
Giải pháp:
1. Mở terminal mới
2. cd backend
3. python app.py
4. Kiểm tra "* Running on http://127.0.0.1:5000"

❌ VẤNĐỀ: Lỗi "ModuleNotFoundError: No module named 'flask'"
──────────────────────────────────────────────────────────────
Nguyên nhân: Flask chưa cài đặt
Giải pháp:
1. cd backend
2. pip install flask flask-cors

❌ VẤNĐỀ: Dữ liệu Admin không lưu
─────────────────────────────────
Nguyên nhân: Quên nhấp "Lưu thay đổi"
Giải pháp:
1. Kiểm tra trạng thái (✅ Đã lưu vs ⚠️ Có thay đổi)
2. Nhấp "💾 Lưu tất cả thay đổi"
3. Chờ thông báo "✅ Đã lưu thành công!"

❌ VẤNĐỀ: Hiệu suất chậm khi gợi ý
──────────────────────────────────
Nguyên nhân: Quá nhiều luật hoặc backend chậm
Giải pháp:
1. Kiểm tra xem backend có báo lỗi không
2. Refresh trang
3. Kiểm tra hiệu suất mạng (F12 → Network)

❌ VẤNĐỀ: Video không hiển thị
──────────────────────────────
Nguyên nhân: URL video sai
Giải pháp:
1. Kiểm tra URL video trong Admin
2. Phải là URL YouTube hợp lệ
3. Format: https://www.youtube.com/watch?v=VIDEO_ID
   hoặc: https://www.youtube.com/embed/VIDEO_ID

❌ VẤNĐỀ: Tên nguyên liệu không hiển thị đúng
──────────────────────────────────────────────
Nguyên nhân: File ingredient_names.json thiếu entry
Giải pháp:
1. Kiểm tra backend/ingredient_names.json
2. Thêm entry mới:
   "co_ten_nguyen_lieu": "Tên tiếng Việt với dấu"
3. Copy sang public/ingredient_names.json
4. Refresh frontend

❌ VẤNĐỀ: Mất kết nối sau khi restart
──────────────────────────────────────
Nguyên nhân: Một trong hai server không khởi động lại
Giải pháp:
1. Dừng cả hai server (Ctrl+C)
2. Bắt đầu lại backend: python app.py
3. Bắt đầu lại frontend: npm start
4. Chờ khoảng 5-10 giây cho React compile


═══════════════════════════════════════════════════════════════════════════════
🎓 VÍ DỤ THỰC HÀNH
═══════════════════════════════════════════════════════════════════════════════

VÍ DỤ 1: Tìm món ăn từ nguyên liệu
──────────────────────────────────
1. Nhấp tab "⬇️ Suy diễn tiến"
2. Nhập: thịt gà, gừng, tỏi, nước mắm
3. Nhấp "🔍 Gợi ý món ăn"
4. Kết quả: Gà kho gừng, Gà rang nghệ, v.v.

VÍ DỤ 2: Tìm nguyên liệu cho một món
──────────────────────────────────────
1. Nhấp tab "⬆️ Suy diễn lùi"
2. Nhập: Bò xào hành tây
3. Nhấp "🔍 Tìm kiếm"
4. Kết quả: Danh sách nguyên liệu cần thiết + công thức + video

VÍ DỤ 3: Thêm món mới vào hệ thống
──────────────────────────────────
1. Nhấp "⚙️ Quản trị viên"
2. Đăng nhập (mật khẩu: admin123)
3. Nhập:
   - ID: R50
   - Tên món: Mực xào không tỏi
   - Nguyên liệu: co_muc, co_ot, co_ca_rot
4. Nhấp "➕ Thêm"
5. Cuộn xuống và điền:
   - Công thức: "Xào mực với ớt..."
   - Video: "https://youtube.com/watch?v=..."
6. Nhấp "💾 Lưu tất cả thay đổi"


═══════════════════════════════════════════════════════════════════════════════
📞 LIÊN HỆ HỖ TRỢ
═══════════════════════════════════════════════════════════════════════════════

Nếu gặp vấn đề:
1. Kiểm tra mục "9️⃣ KHẮC PHỤC SỰ CỐ"
2. Kiểm tra console browser (F12)
3. Kiểm tra terminal backend
4. Đảm bảo cả hai server đang chạy
5. Thử refresh trang (Ctrl+R hoặc Cmd+R)
6. Restart cả hai server nếu vấn đề vẫn tồn tại

═══════════════════════════════════════════════════════════════════════════════
🎉 HOÀN TẤT - ỨNG DỤNG SẴN SÀNG SỬ DỤNG!
═══════════════════════════════════════════════════════════════════════════════

Cảm ơn bạn đã sử dụng hệ thống gợi ý công thức nấu ăn!
Chúc bạn nấu ăn thành công! 🍽️😋

Phiên bản: 1.0
Cập nhật lần cuối: 15/11/2024
