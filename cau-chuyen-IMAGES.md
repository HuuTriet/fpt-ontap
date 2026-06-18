# Manifest hình ảnh — cau-chuyen.html (Câu chuyện FPT)

Tất cả ảnh dùng cơ chế **image-slot fallback-first**: trang luôn có nền/ô dự phòng on-brand;
chỉ khi file ảnh tải `onload` thành công (`naturalWidth>0`) mới swap sang ảnh thật.
=> Thiếu file vẫn chạy đẹp trên `file://` và GitHub Pages, không vỡ layout.

Thư mục đặt ảnh: `assets/img/` (cùng chỗ với portal). Ảnh **lazy-load** (`loading="lazy"`).

> QUY TẮC: Logo kiểm định / xếp hạng phải là ẢNH CHÍNH THỨC do bạn cung cấp.
> KHÔNG tự vẽ, KHÔNG để AI tạo logo giả. Mọi số liệu/năm điền bằng thông tin đã xác minh.

---

## 1. Hero — ảnh campus toàn màn hình
- **File slot:** `assets/img/story-hero.jpg`
- **Vai trò:** Ảnh nền hero phủ toàn màn hình, có lớp phủ tối dần để chữ trắng đọc rõ; có hiệu ứng zoom/parallax nhẹ theo cuộn.
- **Nội dung gợi ý:** Khuôn viên Trường Đại học FPT trong nắng (toà nhà đặc trưng, sân trường, sinh viên đi lại) — khung cảnh rộng, truyền cảm hứng.
- **Hướng & tỉ lệ:** Ngang, 16:9 (hoặc rộng hơn 21:9 vì sẽ bị crop theo chiều cao màn hình). Chừa "đất trống" phía dưới/bên trái cho chữ.
- **Độ phân giải tối thiểu:** 1920×1080 (khuyến nghị 2400×1350 cho màn lớn).
- **Nguồn gợi ý:** Ảnh THẬT khuôn viên FPT (ảnh bạn tự chụp / kho ảnh chính thức của trường, nếu được phép). Có thể TÁI DÙNG ảnh campus sẵn có: đổi `data-img-slot="assets/img/story-hero.jpg"` thành `assets/img/hero.jpg` (ảnh đang có trong dự án) nếu phù hợp.
- **Alt:** "Khuôn viên Trường Đại học FPT trong nắng sớm"
  (đặt sẵn ở `data-alt`; lớp media `aria-hidden` vì là nền trang trí — chữ tiêu đề đã mang nội dung).

## 2. Khởi nguồn
- **Không có ảnh.** Section dùng chữ + một câu pull-quote viền cam. Giữ khoảng thở, không cần ảnh.

## 3. Hoài bão (tầm nhìn)
- **Không có ảnh.** Tuyên ngôn chữ lớn + 3 thẻ trụ cột (icon SVG inline, không phải file ảnh).

## 4. Hành trình (timeline)
- **Không có ảnh.** Timeline dọc thuần chữ + chấm mốc CSS. (Tuỳ chọn nâng cấp sau: có thể thêm 1 ảnh nhỏ minh hoạ cho mỗi mốc — hiện chưa cần.)

## 5. Thành tựu (số liệu)
- **Không có ảnh.** 4 ô số liệu dạng placeholder. Không dùng ảnh.

## 6. Chứng nhận & xếp hạng — "bức tường uy tín" (LOGO = SLOT)
6 ô logo, mỗi ô là 1 image-slot riêng. Mặc định hiện ô viền nét đứt + nhãn `[TÊN KIỂM ĐỊNH / XẾP HẠNG]`.
**Bắt buộc dùng LOGO CHÍNH THỨC** của tổ chức kiểm định/bảng xếp hạng — KHÔNG logo giả/AI.

| File slot | Vai trò | Nội dung |
|---|---|---|
| `assets/img/logo-trust-1.png` | Logo tổ chức kiểm định / xếp hạng #1 | Logo CHÍNH THỨC của tổ chức (thay nhãn `[TÊN…]` bằng tên thật) |
| `assets/img/logo-trust-2.png` | Logo #2 | nt |
| `assets/img/logo-trust-3.png` | Logo #3 | nt |
| `assets/img/logo-trust-4.png` | Logo #4 | nt |
| `assets/img/logo-trust-5.png` | Logo #5 | nt |
| `assets/img/logo-trust-6.png` | Logo #6 | nt |

- **Hướng & tỉ lệ:** Mỗi ô khung 3:2 ngang; logo hiển thị `object-fit:contain` (không méo). Logo có thể vuông hay ngang đều vừa.
- **Định dạng & nền:** PNG nền trong suốt (hoặc SVG) để hợp cả nền sáng/tối. Tránh logo có nền trắng đặc khi xem dark mode.
- **Độ phân giải tối thiểu:** cạnh dài ≥ 400px (PNG); SVG thì vô hạn.
- **Nguồn gợi ý:** TRANG CHÍNH THỨC của tổ chức kiểm định/xếp hạng (bộ nhận diện thương hiệu của họ). Xin phép/đúng điều kiện sử dụng trước khi đăng. KHÔNG dùng ảnh chụp lại mờ, KHÔNG AI tạo.
- **Alt:** đặt theo tên tổ chức thật, ví dụ "Logo [Tên tổ chức kiểm định]". (Hiện `data-alt="[TÊN KIỂM ĐỊNH / XẾP HẠNG]"` — sửa lại khi thay logo thật.)

## 7. Kết & CTA
- **Không có ảnh.** Nền gradient on-brand + chữ + 2 nút. Không dùng ảnh.

## Logo trong NAV/Footer (đã có cơ chế sẵn — tuỳ chọn)
- **File slot:** `assets/img/logo-fpt.svg` (dùng CHUNG với portal `index.html`).
- **Vai trò:** Logo thật ở thanh nav; mặc định hiện wordmark "FPT Ôn Tập" (SVG gradient inline). Nếu file logo thật tồn tại và load OK, wordmark tự ẩn.
- **Alt:** "FPT University" (đặt sẵn). Chỉ đặt logo bạn được phép dùng.

---

### Tóm tắt nhanh các file cần chuẩn bị
```
assets/img/story-hero.jpg        (hoặc tái dùng assets/img/hero.jpg)
assets/img/logo-trust-1.png  ... logo-trust-6.png   (LOGO CHÍNH THỨC)
assets/img/logo-fpt.svg          (tuỳ chọn — dùng chung portal)
```
Thiếu bất kỳ file nào: trang vẫn chạy, hiện fallback on-brand / ô nhãn placeholder.
