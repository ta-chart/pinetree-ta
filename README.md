# Pinetree TA — bản độc lập

Một file duy nhất: `dist/PinetreeTA.html` (~250 KB). Không cần cài đặt, không cần server, không cần tài khoản Claude hay tài khoản công ty chứng khoán.

## Dùng

1. Mở `PinetreeTA.html` bằng Chrome hoặc Edge (nhấp đúp file, hoặc kéo vào trình duyệt).
2. Chọn mã ở thanh **Mã** hoặc gõ mã vào ô **Khác**.
3. **Nến**: 1p, 5p, 15p, 30p, 1G (trong phiên) và Ngày, Tuần, Tháng, Quý, Năm.
4. **Chỉ báo**: bấm để thêm từ danh sách 31 chỉ báo. Bấm tên chỉ báo để bật/tắt, bánh răng để đổi tham số và màu, × để xóa. **Mặc định** đưa về bộ chuẩn Pinetree.
5. **Xuất PNG**: tải ảnh chart (kèm tên mã, khung nến, danh sách chỉ báo, nguồn) về máy để chèn vào báo cáo.

Danh sách chỉ báo và khung nến được nhớ riêng trên trình duyệt của từng người.

## Chia sẻ cho team

- **Máy tính:** gửi file qua email/Teams/Zalo hoặc đặt trên ổ chung; mở bằng Chrome/Edge là dùng được.
- **Điện thoại:** KHÔNG mở file tải về (Tệp, Zalo, Teams, Mail đều mở trong trình xem chặn internet, page sẽ báo "Trình xem file đang chặn kết nối mạng"). Phải mở qua một **đường link https**, xem bên dưới.

### Tạo đường link https (miễn phí, khoảng 5 phút, làm được từ trình duyệt)

Dùng file `dist/index.html` (giống hệt `PinetreeTA.html`, chỉ đổi tên để làm trang chủ).

**GitHub Pages**
1. Đăng nhập github.com (tạo tài khoản nếu chưa có) → **New repository**, đặt tên ví dụ `pinetree-ta`, chọn **Public**, bấm **Create repository**.
2. Bấm **uploading an existing file**, kéo `index.html` vào, bấm **Commit changes**.
3. Vào **Settings → Pages**, mục **Branch** chọn `main` và `/ (root)`, bấm **Save**.
4. Sau 1–2 phút, link là `https://<tên-tài-khoản>.github.io/pinetree-ta/`. Mở link này trên điện thoại, có thể **Thêm vào màn hình chính** để dùng như app.

**Hoặc** đặt `index.html` lên web nội bộ của công ty (chỉ cần chỗ chứa file tĩnh, có https).

Khi cập nhật phiên bản mới, chỉ cần tải `index.html` mới đè lên file cũ; link giữ nguyên. File không chứa mật khẩu hay khóa API nào, nên để công khai không lộ thông tin gì.

Máy cần truy cập được `dchart-api.vndirect.com.vn` (dữ liệu giá). Nếu mạng công ty chặn trang này, page báo lỗi và vẫn cho **Nạp CSV** (cột Date, Open, High, Low, Close, Volume).

## Nguồn dữ liệu và giới hạn

- Giá lấy từ dữ liệu biểu đồ **công khai** của VNDirect (định dạng TradingView UDF). Đây không phải API chính thức có hợp đồng: có thể thay đổi hoặc bị chặn mà không báo trước. Dùng cho phân tích nội bộ; trước khi đưa chart vào báo cáo phát hành ra ngoài, nên kiểm tra điều khoản sử dụng dữ liệu.
- Nến ngày là giá đã điều chỉnh: VNINDEX từ 08/2017, đa số cổ phiếu từ 2013.
- Nến phút/giờ là giá **chưa điều chỉnh** và chỉ đầy đủ cho các phiên gần đây; kéo chart sang trái để tải thêm phiên cũ hơn.
- Mã chỉ số: VNINDEX, VN30, VN100, VNMID, HNX (HNXINDEX), HNX30, UPCOM (UPCOMINDEX).

## Sửa và build lại

- Mã nguồn: `pinetree-ta.src.html` (dùng thư viện chart từ CDN khi phát triển).
- Build file độc lập: `powershell -ExecutionPolicy Bypass -File build.ps1` → `dist/PinetreeTA.html` (thư viện được nhúng thẳng vào file, bản sao lưu ở `vendor/`).
- Thư viện chart: TradingView Lightweight Charts 5.0.8, giấy phép Apache 2.0.

## Hướng mở rộng

Dùng dữ liệu chính thức với tài khoản riêng của từng người (SSI FastConnect Data): SSI chặn trình duyệt gọi trực tiếp, nên cần thêm một proxy nhỏ (ví dụ Cloudflare Worker) và ô nhập ConsumerID/ConsumerSecret lưu trên máy người dùng.
