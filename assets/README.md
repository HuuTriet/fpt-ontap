# assets/ — hướng dẫn thay tài nguyên thật

Trang `index.html` là **single-file vanilla** và **không tải bất kỳ tài nguyên nào từ CDN/domain ngoài**.
Mọi tài nguyên (logo, font, ảnh) đều dùng **đường dẫn tương đối nội bộ** trong thư mục này.
Khi chưa có file thật, trang vẫn chạy nhờ **fallback inline SVG** (wordmark, hero, favicon, og) — chỉ cần thả file đúng tên là tự dùng bản thật.

## 1. Logo FPT (slot — bạn thả vào)

| File | Dùng khi | Ghi chú |
|---|---|---|
| `img/logo-fpt.svg` | nền sáng (nav) | logo chính thức FPT University |
| `img/logo-fpt-white.svg` | nền tối (footer) | bản trắng |

- **Cơ chế fallback-first:** mặc định web hiển thị **wordmark inline SVG "FPT Ôn Tập"** (gradient ngang đủ 5 màu). Chỉ khi `img/logo-fpt.svg` **load thành công** thì mới ẩn wordmark và hiện logo thật (xử lý qua `<img onload>` trong `index.html`). Nếu chưa có file, KHÔNG bị "broken image".
- **Quy tắc dùng logo thật (BẮT BUỘC):** chừa whitespace tối thiểu **25% chiều cao** logo; **không** méo/xoay/đổi tỉ lệ/đổi HEX/xoá ký hiệu trademark. Nền có color-density ≥70% → dùng `logo-fpt-white.svg`.
- **Wordmark fallback KHÔNG mang ký hiệu ™/®** (vì là bản tự dựng của dự án sinh viên, không phải logo chính hãng). Chỉ logo THẬT mới giữ trademark.

## 2. Favicon — `img/favicon.svg`

- Đã có sẵn **favicon on-brand** (chữ "FPT" gradient 5 màu). Thay nếu muốn; giữ kích thước vuông (viewBox `0 0 32 32`).
- `index.html` cũng có favicon `data:` inline làm fallback nếu thiếu file.

## 3. OpenGraph — `img/og.svg` (1200×630)

- Đã có sẵn **og.svg gốc on-brand** (`viewBox="0 0 1200 630"`). `index.html` đã khai báo:
  `<meta property="og:image" content="assets/img/og.svg">` + width 1200 + height 630.
- **Lưu ý mạng xã hội:** Facebook/Zalo **không render SVG** cho `og:image`. Nếu cần preview đẹp khi share:
  1. Export `og.svg` → `og.png` (đúng **1200×630**, dùng Inkscape/Figma/trình duyệt).
  2. Đặt `og.png` vào `img/`.
  3. Đổi trong `index.html`: `content="assets/img/og.svg"` → `content="assets/img/og.png"`.
- **Không** sinh file `.png` nhị phân thủ công ở đây — hãy tự export.

## 4. Font — `fonts/` (Be Vietnam Pro, self-host)

- Xem `fonts/README-fonts.txt`. Cần **5 file WOFF2**:
  `be-vietnam-pro-400/500/600/700/800.woff2` (full charset latin + vietnamese).
- Tải bằng google-webfonts-helper / Fontsource / repo gốc, đổi đúng tên, **kèm `OFL.txt` gốc**.
- `@font-face` trong `index.html` đã trỏ sẵn các đường dẫn này (`font-display:swap`). Trước khi có file, trang dùng fallback `system-ui` (dấu tiếng Việt vẫn đúng).

## 5. Kích thước khuyến nghị

| Tài nguyên | Kích thước |
|---|---|
| `logo-fpt.svg` / `logo-fpt-white.svg` | SVG vector; hiển thị cao ~32–40px ở nav |
| `favicon.svg` | vuông, viewBox 32×32 |
| `og.svg` / `og.png` | **1200×630** |
| font WOFF2 | full charset/weight, tránh subset thiếu dấu |

## 6. Legal / Trademark FPT (BẮT BUỘC)

> Đây là dự án của sinh viên (phi thương mại, phục vụ học tập). FPT, FPT University, FPT Education là thương hiệu của FPT Corporation. Sản phẩm **KHÔNG được FPT chính thức bảo trợ** (*not officially endorsed*). © FPT Corporation cho các thương hiệu FPT.

- **Khuyến nghị xin phép:** trước khi công bố rộng rãi, nên xin phép bằng văn bản từ bộ phận Truyền thông/Thương hiệu FPT University (trademark không có miễn trừ giáo dục tự động).
- **Điều khoản sử dụng FPT:** https://fpt.com/en/terms-of-use
- Không tuyên bố "endorsed", không dùng cho mục đích thương mại.
