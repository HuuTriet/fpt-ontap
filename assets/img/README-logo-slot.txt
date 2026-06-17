SLOT LOGO THẬT — chưa có file (fallback-first)
==============================================

index.html mặc định hiển thị WORDMARK inline SVG "FPT Ôn Tập" (gradient 5 màu),
nên KHÔNG cần file logo thật để trang chạy. Khi nào có logo chính thức FPT
University, hãy thả vào đúng 2 tên dưới đây để web tự dùng bản thật:

  logo-fpt.svg         -> logo chính thức, dùng trên NỀN SÁNG (thanh nav)
  logo-fpt-white.svg   -> bản trắng, dùng trên NỀN TỐI (footer)

Cơ chế: <img id="lpLogoImg" src="assets/img/logo-fpt.svg"> chỉ hiện (và ẩn
wordmark) KHI onload thành công. Thiếu file -> không "broken image", vẫn dùng
wordmark.

QUY TẮC DÙNG LOGO THẬT (BẮT BUỘC):
  - Chừa whitespace tối thiểu 25% chiều cao logo.
  - KHÔNG méo / xoay / đổi tỉ lệ / đổi HEX / xoá ký hiệu trademark.
  - Nền tối (color-density >= 70%) -> dùng logo-fpt-white.svg.

Các file đã có sẵn trong thư mục này:
  favicon.svg  (on-brand, dùng được ngay)
  og.svg       (1200x630 on-brand, dùng được ngay; export PNG nếu cần share MXH)
