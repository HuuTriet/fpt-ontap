# FPT Ôn Tập — Cổng ôn tập đa môn

Trang cổng (portal/hub) tổng hợp các site ôn tập (quiz/flashcard) cho các môn ở FPT University.
Mỗi môn là một thẻ; bấm vào môn **đã có** sẽ mở site quiz riêng của môn đó trong tab mới. Môn **chưa có** hiển thị trạng thái "Sắp có".

- **Live:** https://huutriet.github.io/fpt-ontap/
- **Công nghệ:** HTML + CSS + JavaScript thuần — không build step, không framework, không dependency. Deploy tĩnh trên GitHub Pages.

## Thêm một môn mới

Mở `index.html`, thêm **một object** vào mảng `SUBJECTS` (không sửa gì khác). Khi môn đã có site quiz thì đổi `status` sang `'available'` và điền `url`.

```js
{
  code: 'PRN232',                                   // mã môn (in hoa), duy nhất
  name: 'Lập trình Back-End .NET',                  // tên ngắn
  fullName: '... (PRN232)',                         // tên đầy đủ (tooltip/aria) — bỏ trống cũng được
  semester: 'Kỳ 7',                                 // kỳ học (tùy chọn)
  description: 'Mô tả ngắn 1–2 dòng.',
  status: 'available',                              // 'available' | 'coming-soon'
  url: 'https://huutriet.github.io/prn232-quiz/',   // link site quiz (bắt buộc nếu available)
  accent: '#1E6E45',                                // màu nhấn badge mã môn (tùy chọn)
  emoji: '🌐'                                        // emoji đại diện (tùy chọn)
}
```

Sau khi thêm: tổng số môn ở header và bộ lọc/tìm kiếm tự cập nhật — không cần đụng code render.

## Danh sách môn hiện có

| Mã | Trạng thái | Link |
|----|-----------|------|
| MLN111 | ✅ Đã có | https://huutriet.github.io/mln111-585-cau/ |
| PRN232 | ⏳ Sắp có | — |
| MAS291 | ⏳ Sắp có | — |
| SWP391 | ⏳ Sắp có | — |
| DBI202 | ⏳ Sắp có | — |

> Lưu ý: tên/mã các môn "Sắp có" là tạm — xác nhận lại theo chương trình trước khi mở public.
