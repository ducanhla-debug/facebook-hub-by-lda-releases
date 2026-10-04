# Hướng dẫn cài và mở Facebook Hub by LDA trên macOS

Phiên bản: 1.0.0-beta.3 · File: `Facebook-Hub-by-LDA-1.0.0-beta.3-arm64.dmg`

Dành cho **Mac chip Apple (M1/M2/M3/M4…)**, macOS 12 trở lên. Bản này **không** dành cho Mac chip Intel (chưa phát hành bản Intel vì chưa kiểm thử phù hợp).

Máy **không cần** cài Node.js, npm hay công cụ lập trình.

## 1. Kiểm tra file tải về (khuyến nghị)

Mở Terminal tại thư mục Downloads:

```bash
shasum -a 256 Facebook-Hub-by-LDA-1.0.0-beta.3-arm64.dmg
```

So sánh với dòng tương ứng trong `SHA256SUMS.txt`. Khác nhau thì không mở và tải lại.

## 2. Cài đặt

1. Mở file `.dmg`.
2. Kéo biểu tượng **Facebook Hub by LDA** vào thư mục **Applications**.
3. Đẩy (Eject) ổ DMG.

## 3. Mở lần đầu (Open Anyway)

Bản beta **không được ký bằng Apple Developer ID và chưa được Apple notarize**, nên lần đầu macOS sẽ chặn với thông báo không thể kiểm tra ứng dụng. Theo hướng dẫn chính thức của Apple:

1. Mở ứng dụng một lần từ Applications (macOS sẽ chặn) → bấm **Done/Xong**.
2. Mở **System Settings → Privacy & Security**, kéo xuống phần Security.
3. Bấm **Open Anyway** cho "Facebook Hub by LDA", xác nhận bằng mật khẩu/Touch ID nếu được hỏi.
4. Khi cảnh báo hiện lại, bấm **Open**.

Sau đó ứng dụng được ghi nhận là ngoại lệ và mở bình thường bằng cách bấm đúp.

Lưu ý: nếu Mac do công ty/trường học quản lý, nút **Open Anyway có thể không khả dụng**. Hãy liên hệ bộ phận IT. Chúng tôi **không** hướng dẫn tắt Gatekeeper hay các cơ chế bảo mật của macOS.

## 4. Dữ liệu

Dữ liệu tự động nằm tại (ứng dụng không hỏi chọn thư mục):

```text
~/Library/Application Support/Facebook Hub by LDA/
├── Data/  Sessions/  Media/  Logs/  Backups/
```

Lần mở đầu tiên ứng dụng trống: 0 tài khoản, 0 chiến dịch, 0 khách hàng, Google chưa kết nối.

## 5. Chạy nền

Đóng cửa sổ chỉ ẩn ứng dụng; biểu tượng vẫn nằm trên thanh menu (menu bar) và lịch vẫn chạy. Chọn **Thoát hoàn toàn** trên menu bar để dừng. Khi còn lịch đã duyệt, ứng dụng ngăn máy tự ngủ nhưng vẫn cho màn hình tắt; ứng dụng không chống được việc gập nắp, Sleep thủ công hay hết pin — bài khi đó chuyển "Đã lỡ lịch" và không tự đăng bù.

## 6. Kết nối Google Sheets (tùy chọn, làm một lần)

Dùng khi bạn muốn soạn lịch đăng trên Google Sheet rồi nhập vào ứng dụng. Cần một file "OAuth Client" của riêng bạn:

1. Mở https://console.cloud.google.com, đăng nhập Gmail của bạn. Chọn **Select a project → New project**, đặt tên (vd. `Facebook Hub`) → **Create**.
2. Vào **APIs & Services → Library**, tìm **Google Sheets API** → **Enable**. Làm tương tự với **Google Drive API**.
3. Vào **Google Auth Platform → Branding** (lần đầu có nút **Get started**): App name `Facebook Hub`, chọn email hỗ trợ → **Next**; Audience chọn **External** → **Next**; nhập email liên hệ → **Next**; tích đồng ý → **Create**.
4. Vào **Audience → Test users → Add users**, thêm đúng Gmail bạn sẽ dùng để kết nối → **Save**. (Để ứng dụng ở chế độ **Testing**; không cần gửi Google xét duyệt.)
5. Vào **Clients → Create client**: Application type chọn **Desktop app**, đặt tên → **Create** → **Download JSON**.
6. Trong Facebook Hub: **Cài đặt → Google Sheets → Nhập file OAuth Client (JSON)**, chọn file vừa tải → bấm **Kết nối Google** và đăng nhập trong trình duyệt. Nếu Google báo "Google hasn't verified this app", bấm **Continue** (đây là app của chính bạn).
7. Bấm **Tạo Google Sheet mẫu**, điền Sheet, rồi bấm **Nhập từ Google Sheets** → **Xem & duyệt hàng loạt**.

Lưu ý: ứng dụng chỉ có quyền `drive.file` — chỉ mở được Sheet do chính ứng dụng tạo, không đọc được các file khác trong Drive. Ở chế độ Testing, Google có thể yêu cầu đăng nhập lại sau khoảng 7 ngày. Không chia sẻ file JSON cho người khác.

## 7. Cập nhật và gỡ

Không có cập nhật tự động. Bản mới: tải DMG mới và kéo đè vào Applications (dữ liệu giữ nguyên). Gỡ: kéo ứng dụng từ Applications vào Thùng rác; dữ liệu vẫn nằm ở thư mục trên cho đến khi bạn tự xóa.
