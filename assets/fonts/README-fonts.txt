THƯ MỤC FONT — Be Vietnam Pro (self-host WOFF2)
===============================================

Trang web KHÔNG tải font từ CDN/Google Fonts. Bạn cần TỰ tải 5 file WOFF2
của Be Vietnam Pro về đây và đặt ĐÚNG TÊN dưới đây:

  be-vietnam-pro-400.woff2   (Regular)
  be-vietnam-pro-500.woff2   (Medium)
  be-vietnam-pro-600.woff2   (SemiBold)
  be-vietnam-pro-700.woff2   (Bold)
  be-vietnam-pro-800.woff2   (ExtraBold)

Nguồn tải hợp lệ (chỉ là nơi tải lúc chuẩn bị, KHÔNG nhúng vào web):
  - google-webfonts-helper:  https://gwfh.mranftl.com/fonts/be-vietnam-pro
      -> chọn charset "vietnamese" + "latin", weights 400/500/600/700/800,
         định dạng WOFF2; đổi tên file theo đúng mẫu ở trên.
  - Fontsource:              https://fontsource.org/fonts/be-vietnam-pro
  - GitHub gốc:              https://github.com/bettergui/BeVietnamPro

LƯU Ý unicode-range:
  - @font-face trong index.html KHÔNG khai báo unicode-range, nên hãy host
    file FULL charset (latin + vietnamese trong cùng 1 file/weight) để chắc
    chắn đủ dấu tiếng Việt. Nếu bạn dùng file subset riêng "vietnamese", hãy
    bổ sung khai báo unicode-range tương ứng trong index.html.

LICENSE:
  - Be Vietnam Pro phát hành theo SIL Open Font License 1.1 (OFL).
  - Khi tải font về, hãy kèm luôn file OFL.txt (license gốc của font) vào
    thư mục này. Xem OFL.txt cạnh file này để biết yêu cầu.

Khi chưa có file: trang vẫn hiển thị đẹp bằng fallback stack
('Be Vietnam Pro', Inter, system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif)
nhờ font-display:swap. Dấu tiếng Việt vẫn đúng vì system-ui hỗ trợ sẵn.
