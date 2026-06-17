# FPT Ôn Tập — Cổng ôn tập đa môn

Cổng ôn tập tổng hợp (flashcard + trắc nghiệm) cho các môn ở FPT University, theo nhận diện thương hiệu FPT.
Đây là **single-file app** `index.html`: landing (chọn môn) + engine quiz nằm chung một trang, chuyển qua router hash. Bấm môn **đã có** sẽ vào ngay flashcard/quiz tại chỗ (không nhảy trang); môn **chưa có** hiển thị "Sắp có".

- **Live:** https://huutriet.github.io/fpt-ontap/
- **Công nghệ:** HTML + CSS + JavaScript thuần — không build step, không framework, không dependency runtime, không CDN. Deploy tĩnh trên GitHub Pages.
- **Dữ liệu môn:** nạp động (lazy-load) từ `data/<code>.js` → `window.__SUBJECT_DATA[CODE]` khi mở môn. Tiến độ lưu ở `localStorage` key `fpt-ontap:progress:<CODE>`.
- **Font:** Be Vietnam Pro **self-host** (xem `assets/fonts/`). Logo/ảnh OG/favicon: xem `assets/`.

## Cấu trúc

```
fpt-ontap/
├─ index.html            # single-file app (CSS + JS inline)
├─ .nojekyll
├─ README.md
├─ data/  └─ mln111.js   # dữ liệu MLN111 (window.__SUBJECT_DATA['MLN111'])
└─ assets/               # logo slot, font woff2 (self-host), favicon, og — xem assets/README.md
```

## Thêm một môn mới

Mở `index.html`, thêm **một object** vào mảng `SUBJECTS` (không cần sửa code render). Khi môn có dữ liệu thật thì tạo `data/<code>.js` và đổi `status` sang `'available'`.

```js
{
  code: 'PRN232',                       // mã môn (in hoa), duy nhất
  name: 'Lập trình Back-End .NET',      // tên ngắn
  fullName: '... (PRN232)',             // tên đầy đủ (aria/tiêu đề) — tùy chọn
  semester: 'Kỳ 7',                     // tùy chọn
  description: 'Mô tả ngắn 1–2 dòng.',
  status: 'available',                  // 'available' | 'coming-soon'
  accent: '#53B848',                    // màu nhấn — nên dùng palette FPT
  emoji: '🌐',                          // fallback nếu không có icon SVG
  iconKey: 'net',                       // tùy chọn: 'law'|'net'|'stats'|'project'|'db' (→ <symbol id="ic-..">)
  questionCount: 320                    // tùy chọn: số câu hiển thị (KHÔNG đọc DATA.length)
}
```

`iconKey` lạ/thiếu sẽ tự fallback về emoji rồi 📚 — an toàn, không vỡ. Tổng số môn ở hero + bộ lọc/tìm kiếm tự cập nhật.

## Palette accent on-brand (FPT)

| Môn | accent |
|---|---|
| MLN111 | `#0651A0` (Dark Peacock Blue) |
| PRN232 | `#53B848` (Leafy Green) |
| MAS291 | `#008DDE` (Cerulean) |
| SWP391 | `#F37124` (Dusty Orange) |
| DBI202 | `#E11B22` (đỏ logo) |

## Danh sách môn hiện có

| Mã | Trạng thái |
|----|-----------|
| MLN111 | ✅ Đã có (585 câu) |
| PRN232 | ⏳ Sắp có |
| MAS291 | ⏳ Sắp có |
| SWP391 | ⏳ Sắp có |
| DBI202 | ⏳ Sắp có |

> Tên/mã các môn "Sắp có" là tạm — xác nhận theo chương trình trước khi mở public.

## Pháp lý / Thương hiệu (BẮT BUỘC)

> Đây là dự án của sinh viên (phi thương mại, phục vụ học tập). FPT, FPT University, FPT Education là thương hiệu của FPT Corporation. Sản phẩm **KHÔNG được FPT chính thức bảo trợ** (*not officially endorsed*). © FPT Corporation cho các thương hiệu FPT.

- **Khuyến nghị xin phép:** trước khi công bố rộng rãi, nên xin phép bằng văn bản từ bộ phận Truyền thông/Thương hiệu FPT University (trademark không có miễn trừ giáo dục tự động).
- **Điều khoản sử dụng FPT:** https://fpt.com/en/terms-of-use
- Logo FPT thật: chừa whitespace ≥25% chiều cao, không méo/xoay/đổi màu/xoá trademark (xem `assets/README.md`).

Thực hiện bởi **HuuTriet**.
