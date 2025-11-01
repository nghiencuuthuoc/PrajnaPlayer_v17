# PrajnaPlayer v17

PrajnaPlayer v17 là một trình phát media viết bằng Python, dạng **một file duy nhất**, dành cho các bộ sưu tập tri thức cá nhân, transcript YouTube, thư viện audio–video Phật học/học thuật và các thư mục R&D kiểu PharmApp. Ứng dụng ưu tiên **lưu trạng thái**, **chạy offline** và **giao diện đồng nhất** trên Windows/macOS/Linux.

---

## 🌟 Tính năng chính

- **Chạy bằng một file**: chỉ cần chạy `PrajnaPlayer_v17.py` — dễ mang đi, dễ backup, dễ version.
- **Tự tải assets lần đầu**: khi chạy lần đầu, app có thể kiểm tra thư mục `assets/`, nếu chưa có sẽ tải gói assets dùng chung cho v17 từ GitHub:
  - https://github.com/nghiencuuthuoc/PrajnaPlayer-Assets/tree/main/Assets_v17
- **Giao diện kiểu PharmApp**: nền màu kem, footer thương hiệu, dễ tích hợp với các tiện ích khác.
- **Nhớ phiên làm việc**: nhớ thư mục lần cuối, bài hát/video cuối, âm lượng, vị trí phát (lưu JSON) → rất hữu ích khi nghe pháp thoại hoặc video R&D dài.
- **Ưu tiên nội bộ/offline**: phát trực tiếp từ thư mục máy tính, phù hợp kho dữ liệu lớn.
- **Có chỗ gắn thêm hàm phụ**: ví dụ lấy URL tab Chrome đang mở, reload assets, tích hợp watchdog, tích hợp PharmApp.
- **Phù hợp hệ sinh thái PharmApp**: đặt tên, thư mục, footer tương thích.

---

## 📁 Cấu trúc repo

```text
PrajnaPlayer_v17/
├── PrajnaPlayer_v17.py   # file chạy chính
```

Repo hiện tại giữ tối giản để dễ đóng gói.

---

## 📦 Yêu cầu

- Python **3.9+** (3.10/3.11/3.12 đều dùng được)
- `tkinter` (có sẵn trên Windows/macOS; Linux có thể cần cài `python3-tk`)
- Backend phát media (ví dụ `python-vlc`) — tùy bạn cấu hình trong mã
- Có Internet **chỉ lần chạy đầu** nếu cần tải assets

---

## 🛠 Cài đặt

1. **Tải repo** (clone hoặc tải ZIP).
2. Kiểm tra Python:
   ```bash
   python --version
   ```
3. (Khuyến nghị) tạo môi trường ảo:
   ```bash
   python -m venv venv
   source venv/bin/activate      # macOS/Linux
   venv\Scripts\activate       # Windows
   ```
4. Cài các gói cần thiết:
   ```bash
   pip install python-vlc pillow requests
   ```

---

## 🚀 Chạy

```bash
python PrajnaPlayer_v17.py
```

Lần chạy đầu, app có thể:
- kiểm tra `./assets/`,
- tải bộ assets v17 từ GitHub,
- lưu lại để các lần sau chạy nhanh.

---

## 🖼 Assets & Thương hiệu

- URL assets mặc định:
  - https://github.com/nghiencuuthuoc/PrajnaPlayer-Assets/tree/main/Assets_v17
- Nên để logo/icon trong `assets/`.
- Nếu đổi logo, nên giữ footer “PharmApp / Nghiên Cứu Thuốc” để đồng bộ với các module khác.

---

## 🗂 Gợi ý bố cục thư mục

```text
PrajnaPlayer_v17/
├── PrajnaPlayer_v17.py
├── assets/                     # tự tải nếu chưa có
│   ├── icons/
│   ├── logos/
│   └── samples/
├── database/                   # tùy chọn: metadata, playlist
└── state/                      # tùy chọn: trạng thái phiên
```

Bạn cũng có thể để JSON trạng thái cạnh file `.py` như các script PharmApp khác.

---

## 🔁 Lưu trạng thái (Khuyến nghị)

PrajnaPlayer v17 được thiết kế để **nhớ**:

- thư mục media lần cuối
- file phát lần cuối
- vị trí phát
- âm lượng
- cấu hình giao diện (nếu có)

Lưu vào các file kiểu:

```text
./state_recent.json
./state_<folder-hash>.json
./static.json
```

Cách này giống PrajnaPlayer trước đó và các tool quét/crawl của bạn.

---

## 🧪 Ghi chú phát triển

- Repo hiện mới 1 file → có thể tách thành:
  - `prajna_player/gui.py`
  - `prajna_player/player.py`
  - `prajna_player/assets.py`
  - `prajna_player/state.py`
- Có thể thêm tham số CLI:
  ```bash
  python PrajnaPlayer_v17.py --headless --scan "D:\PharmApp\audio"
  ```
- Có thể gắn watchdog để kiểm tra assets hoặc URL ngrok của PharmApp.

---

## 📜 Giấy phép

Thêm license bạn muốn (MIT/BSD/Apache-2.0).  
Nếu muốn đồng bộ với các module PharmApp public, dùng MIT và giữ footer.

---

## 🤝 Ghi công

- **PharmApp / Nghiên Cứu Thuốc / RnD Pharma Plus**
- Tác giả: **Bùi Huỳnh Quốc Đạt**
- Cộng đồng thử nghiệm trên Windows và chia sẻ bộ assets

---

## 🏁 Footer kiểu PharmApp

PharmApp // Nghiên Cứu Thuốc // RnD Pharma Plus  
www.pharmapp.vn • www.nghiencuuthuoc.com  
© 2025
