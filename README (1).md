# 🍌 Diệu Trang — Minion-Concept Portfolio

Portfolio một trang (single-page), theme lấy cảm hứng từ **Minions** (vàng chuối, denim xanh, kính goggle), hiệu ứng chuyển cảnh nặng đô bằng GSAP + ScrollTrigger:

- Màn hình loading kiểu banana loader
- Custom cursor hình kính goggle
- Hero với hiệu ứng tách chữ (split-letter bounce) + tilt ảnh theo chuột
- Marquee chạy ngôn ngữ Minion
- Đếm số liệu (stat counter) khi cuộn tới
- **Timeline kinh nghiệm cuộn ngang có pin (horizontal pinned scroll)** — điểm nhấn chính
- Thanh kỹ năng (skill bar) tự fill khi vào khung nhìn
- Gallery cuộn ngang, hiệu ứng "wipe" khi các section xuất hiện

## Cấu trúc thư mục

```
(tất cả nằm CHUNG 1 cấp, KHÔNG có thư mục con)
├── index.html
├── hero.jpg
├── ads-report.jpg
├── zoom-call-1.jpg
├── zoom-call-2.jpg
├── award-stage.jpg
├── award-certificate.jpg
├── ranking-chart.jpg
└── README.md
```

**Vì sao đổi cấu trúc này:** hai cách làm trước đều từng gặp lỗi khi đẩy lên GitHub — để ảnh trong thư mục `assets/images/` thì dễ bị quên không đẩy thư mục lên; nhúng ảnh base64 thẳng vào `index.html` thì file nặng ~3MB, dễ bị lỗi khi upload/copy qua giao diện web. Bản này **để toàn bộ ảnh và `index.html` ngay tại gốc**, không thư mục con, mỗi ảnh chỉ ~50–500KB, `index.html` chỉ ~50KB — chọn hết 8 file kéo thả 1 lần vào GitHub là đủ, không thể thiếu sót.

## Cách đưa lên GitHub Pages (miễn phí)

1. Tạo repo mới trên GitHub, ví dụ `dieutrang-portfolio`.
2. Vào repo → **Add file → Upload files**.
3. **Chọn/kéo thả CÙNG LÚC cả 8 file** (`index.html` + 7 ảnh `.jpg` + `README.md`) vào khung upload — không kéo file zip, không kéo thư mục, chỉ kéo đúng các file này.
4. Cuộn xuống, bấm **Commit changes**.
5. Vào **Settings → Pages** → mục **Build and deployment** chọn **Deploy from a branch**, Branch = `main`, folder = `/ (root)` → **Save**.
6. Đợi 1–2 phút, mở `https://<username>.github.io/<tên-repo>/` để xem kết quả.

⚠️ Nếu vẫn báo lỗi sau khi làm đúng các bước trên, khả năng cao là do:
- Tên repo/branch Pages đang trỏ sai (kiểm tra lại mục Settings → Pages)
- Tài khoản GitHub chưa xác minh email (một số tính năng Pages yêu cầu email đã verify)
- Trình duyệt bị chặn JavaScript/cache cũ — thử mở bằng tab ẩn danh hoặc trình duyệt khác

## Tuỳ chỉnh nhanh

- **Đổi màu chủ đạo**: sửa các biến trong `:root{...}` đầu file `index.html` (`--yellow`, `--denim`, `--zap`...).
- **Đổi/thêm ảnh**: bỏ ảnh mới vào `assets/images/`, cập nhật đường dẫn `src="assets/images/ten-anh.jpg"` tại card tương ứng.
- **Thêm kinh nghiệm mới**: copy nguyên khối `<article class="exp-card">...</article>` trong phần `#experience` rồi sửa nội dung — hiệu ứng cuộn ngang tự nhận thêm card.
- **Tắt hiệu ứng cuộn ngang trên mobile**: đã tự động chuyển sang cuộn dọc thường khi màn hình < 760px (xem hàm `setupExpScroll()`).

## Thư viện dùng (qua CDN, không cần cài đặt)

- [GSAP 3](https://gsap.com/) + ScrollTrigger — animation & scroll-driven effects
- Google Fonts: `Baloo 2` (display) + `Be Vietnam Pro` (nội dung, hỗ trợ tốt tiếng Việt có dấu)

Không cần build tool, không cần npm — mở thẳng `index.html` bằng trình duyệt là chạy được (một số hiệu ứng ảnh nền cần host qua GitHub Pages hoặc `Live Server` để load mượt nhất).
