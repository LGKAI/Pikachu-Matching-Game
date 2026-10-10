# Pikachu Matching Game

Đồ án Cơ sở lập trình cho AI

🎥 **Video Demo:** [Xem trên YouTube](https://youtu.be/Ip8vcNSGLIY?si=lXj9NSeqTwNcnTkN)

Pikachu là một tựa game giải đố kinh điển được phát triển bằng ngôn ngữ lập trình Python kết hợp với thư viện Pygame. Game mang đến cho người chơi trải nghiệm giải trí thú vị với giao diện bắt mắt, hình ảnh sắc nét và âm thanh sống động. Không chỉ dừng lại ở gameplay cơ bản, trò chơi còn được tích hợp các tính năng nâng cao như hệ thống quản lý tài khoản người dùng, bảng xếp hạng thành tích và tùy chỉnh cài đặt chế độ chơi.

---

## 🛠 Công nghệ và Kiến thức sử dụng

Dự án này được xây dựng dựa trên sự kết hợp giữa nhiều thư viện Python và các kiến thức nền tảng về lập trình, thuật toán:

### 1. Công nghệ & Thư viện (Tech Stack)
- **Python (>= 3.8)**: Ngôn ngữ lập trình cốt lõi để phát triển toàn bộ logic game.
- **Pygame**: Thư viện chính được sử dụng để xây dựng giao diện đồ họa (GUI), quản lý vòng lặp game (game loop), xử lý sự kiện (chuột, bàn phím), kết xuất hình ảnh và phát âm thanh.
- **NumPy & SciPy**: Sử dụng để xử lý ma trận và hình ảnh. Cụ thể, `scipy.ndimage.gaussian_filter` được áp dụng lên mảng điểm ảnh (thông qua NumPy) để tạo hiệu ứng làm mờ (Gaussian blur) cho ảnh nền một cách mượt mà.
- **JSON**: Định dạng lưu trữ dữ liệu cục bộ, được dùng để ghi/đọc thông tin tài khoản người chơi (đăng nhập/đăng ký) và điểm số cho Bảng xếp hạng.

### 2. Kiến thức & Kỹ thuật lập trình
- **Thuật toán tìm đường (Pathfinding)**: Áp dụng thuật toán tìm kiếm trên đồ thị/ma trận 2D để kiểm tra đường đi hợp lệ giữa hai ô Pikachu. Đường nối phải đảm bảo không có vật cản và gấp khúc tối đa 2 lần (tương đương 3 đoạn thẳng) theo luật chơi chuẩn.
- **Thao tác trên Ma trận (2D Arrays/Matrices)**: Quản lý trạng thái bàn cờ (bảng game), tọa độ các ô, và xử lý việc thêm, xóa, xáo trộn các phần tử trên bảng.
- **Quản lý Trạng thái (State Management)**: Phân luồng các trạng thái khác nhau của chương trình như: Màn hình đăng nhập, Menu chính, Màn hình chơi game, Màn hình thắng/thua cuộc.
- **Xử lý Sự kiện & Va chạm (Event Handling & Collision Detection)**: Theo dõi tương tác người dùng, phát hiện tọa độ click chuột và kiểm tra xem vị trí đó có trùng khớp với một nút bấm (button) hoặc một ô Pikachu cụ thể hay không (`collidepoint`).

---

## 🌟 Tính năng nổi bật

- **Hệ thống Tài khoản:** Hỗ trợ người dùng đăng ký và đăng nhập.
- **Bảng xếp hạng (Leaderboard):** Lưu lại và vinh danh những người chơi có điểm số cao nhất.
- **Gameplay Cổ điển:** Lối chơi nối thú quen thuộc với nhiều cấp độ (Level) có độ khó tăng dần.
- **Giao diện & Hiệu ứng:** Hiệu ứng hình ảnh đẹp mắt (như làm mờ nền), âm thanh tương tác sinh động khi thao tác, ghép đúng/sai hoặc khi qua màn.

---

## 📁 Cấu trúc thư mục

```text
Project_Pikachu-Matching-Game/
├── report.pdf               # Báo cáo đồ án
├── video.mp4                # Video demo đồ án
└── source/                  # Thư mục chứa mã nguồn trò chơi
    ├── pikachu.py           # File mã nguồn chính, chạy để khởi động game
    ├── requirements.txt     # Danh sách các thư viện cần thiết (pygame, numpy, scipy)
    ├── README.md            # Tài liệu hướng dẫn đồ án
    ├── Resources/           # Thư mục chứa tài nguyên đa phương tiện
    │   ├── Background/      # Hình ảnh nền trò chơi
    │   ├── BGmusic/         # Nhạc nền các cấp độ chơi
    │   ├── Buttons/         # Hình ảnh các nút giao diện (New Game, Settings, Exit...)
    │   ├── Fonts/           # Phông chữ sử dụng trong game (Jersey15, Jersey20)
    │   ├── Others/          # Hình ảnh bổ trợ, bảng thông báo, cúp thành tích, logo
    │   ├── Pokemon_icons/   # Bộ icon các thẻ Pokémon trên bàn cờ
    │   └── Sound_effect/    # Hiệu ứng âm thanh (click chuột, ghép đúng/sai, chiến thắng...)
    └── User_data/           # Thư mục chứa dữ liệu cục bộ của người chơi
        ├── accounts.json    # File lưu trữ thông tin tài khoản
        └── scoreboard.json  # File lưu trữ điểm số bảng xếp hạng (Leaderboard)
```

---

## 🚀 Hướng dẫn triển khai

### 1. Cài đặt môi trường
Đầu tiên, bạn cần đảm bảo máy tính đã được cài đặt Python (phiên bản `>= 3.8`).
Sau đó, mở Terminal / Command Prompt, di chuyển vào thư mục chứa mã nguồn và cài đặt các thư viện cần thiết thông qua tệp `requirements.txt`:

```bash
pip install -r requirements.txt
```

### 2. Khởi chạy Game
Sau khi quá trình cài đặt hoàn tất, thực thi lệnh sau để khởi chạy trò chơi:

```bash
python pikachu.py
```

> **Lưu ý:** Nếu bạn đang ở thư mục gốc `Project_Pikachu-Matching-Game`, hãy chuyển vào thư mục `source` trước khi chạy:
> ```bash
> cd source
> python pikachu.py
> ```

Chúc bạn có những giờ phút giải trí vui vẻ với Pikachu Matching Game! 🎮