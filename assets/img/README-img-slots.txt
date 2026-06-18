IMAGE SLOTS — thả ảnh thật vào đây (đúng tên), trang tự swap khi tải OK.
Thiếu file = vẫn đẹp nhờ placeholder SVG on-brand (fallback-first, không broken image).

Tên file        | Vị trí                         | Kích thước
----------------|--------------------------------|------------------
hero.jpg        | Visual hero (thay mockup SVG)  | 1200x900 (4:3)
feature-1.jpg   | Marketing "Flashcard"          | 960x640  (3:2)
feature-2.jpg   | Marketing "Trắc nghiệm"        | 960x640  (3:2)
feature-3.jpg   | Marketing "Tiến độ & Offline"  | 960x640  (3:2)

- Định dạng: .jpg/.webp nén tốt (≤ ~200KB). Đổi đuôi -> sửa data-img-slot trong index.html.
- Cơ chế: index.html nạp <img> qua data-img-slot, CHỈ hiện khi onload thành công (không dùng onerror).
- Logo/og/favicon: xem assets/README.md mục 1-3.
