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

## 3b. Ảnh thật (image slot — tái sử dụng, fallback-first)

Trang dùng **cơ chế image slot**: mỗi vị trí ảnh hiển thị **placeholder SVG on-brand đẹp** mặc định. Khi bạn thả file ảnh thật **đúng tên** vào `img/`, trang sẽ thử nạp qua `<img>` và **chỉ swap sang ảnh thật khi tải THÀNH CÔNG** (`onload`). Nếu thiếu file, placeholder vẫn giữ nguyên — **không bao giờ hiện "broken image"**, chạy được cả `file://`. (Không dùng `onerror`.)

Thả ảnh vào đúng các tên sau (tất cả **không bắt buộc** — thiếu thì dùng placeholder):

| File | Vị trí trên trang | Kích thước khuyến nghị | Ghi chú |
|---|---|---|---|
| `img/hero.jpg` | Visual lớn ở **hero** (thay mockup SVG) | **1200×900** (4:3) | Ảnh chụp app / minh hoạ; sẽ phủ kín khối hero |
| `img/feature-1.jpg` | Hàng marketing "Flashcard" | **960×640** (3:2) | Màn hình flashcard / lật thẻ |
| `img/feature-2.jpg` | Hàng marketing "Trắc nghiệm" | **960×640** (3:2) | Màn hình quiz chấm điểm |
| `img/feature-3.jpg` | Hàng marketing "Tiến độ & Offline" | **960×640** (3:2) | Biểu đồ tiến độ / màn hình kết quả |

- **Định dạng:** ưu tiên `.jpg`/`.webp` nén tốt (≤ ~200KB mỗi ảnh). Nếu muốn dùng `.webp`/`.png`, đổi đuôi trong `index.html` tại thuộc tính `data-img-slot="assets/img/<tên>"`.
- **A11y:** mỗi slot đã có `data-alt` mô tả — sửa text trong `index.html` cho khớp ảnh thật của bạn.
- (Tuỳ chọn) Nếu sau này cần avatar/sao chứng thực: thêm slot mới dạng `<span class="lp-media" data-img-slot="assets/img/avatar-1.jpg" data-alt="...">` kèm placeholder SVG, kích thước vuông **160×160**.

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
| `hero.jpg` | **1200×900** (4:3) |
| `feature-1.jpg` / `feature-2.jpg` / `feature-3.jpg` | **960×640** (3:2) |
| font WOFF2 | full charset/weight, tránh subset thiếu dấu |

## 6. Legal / Trademark FPT (BẮT BUỘC)

> Đây là dự án của sinh viên (phi thương mại, phục vụ học tập). FPT, FPT University, FPT Education là thương hiệu của FPT Corporation. Sản phẩm **KHÔNG được FPT chính thức bảo trợ** (*not officially endorsed*). © FPT Corporation cho các thương hiệu FPT.

- **Khuyến nghị xin phép:** trước khi công bố rộng rãi, nên xin phép bằng văn bản từ bộ phận Truyền thông/Thương hiệu FPT University (trademark không có miễn trừ giáo dục tự động).
- **Điều khoản sử dụng FPT:** https://fpt.com/en/terms-of-use
- Không tuyên bố "endorsed", không dùng cho mục đích thương mại.
