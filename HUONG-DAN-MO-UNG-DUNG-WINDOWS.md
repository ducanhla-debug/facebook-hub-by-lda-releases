# Hướng dẫn cài và mở Facebook Hub by LDA trên Windows

Phiên bản: 1.0.0-beta.2 · File cài: `Facebook-Hub-by-LDA-Setup-x64.exe` (Windows 10/11, 64-bit)

Máy **không cần** cài Node.js, npm, Chrome riêng, MuMu, ADB hay công cụ lập trình.

## 1. Kiểm tra file tải về (khuyến nghị)

Mở PowerShell tại thư mục chứa file và chạy:

```powershell
Get-FileHash .\Facebook-Hub-by-LDA-Setup-x64.exe -Algorithm SHA256
```

So sánh kết quả với dòng tương ứng trong `SHA256SUMS.txt`. Nếu khác nhau, **không** chạy file và tải lại từ trang phát hành chính thức.

## 2. Vì sao Windows cảnh báo

Bản beta này **không được ký số** (chưa có chứng thư ký mã). Vì vậy Microsoft Defender SmartScreen có thể hiện màn hình "Windows protected your PC / Windows đã bảo vệ máy tính của bạn".

Nếu bạn đã kiểm tra SHA-256 và tin tưởng nguồn tải:

1. Bấm **More info / Thông tin thêm**.
2. Nếu có nút **Run anyway / Vẫn chạy**, bấm nút đó.

Lưu ý quan trọng:

- Nút **Run anyway không phải lúc nào cũng xuất hiện**. Tùy cấu hình máy, chính sách của công ty/trường học hoặc phần mềm diệt virus, Windows có thể chặn hoàn toàn.
- **Smart App Control** (Windows 11): theo Microsoft, hiện không có cách cho phép riêng từng ứng dụng bị Smart App Control chặn. Nếu máy bật Smart App Control, bản không ký có thể không cài được. Hãy liên hệ người cung cấp ứng dụng hoặc bộ phận IT; chúng tôi **không** hướng dẫn tắt các cơ chế bảo mật của Windows.
- Máy do công ty quản lý có thể chặn ứng dụng không ký theo chính sách.

## 3. Cài đặt

1. Chạy `Facebook-Hub-by-LDA-Setup-x64.exe`.
2. Chọn **thư mục gốc** để cài (mặc định: `%USERPROFILE%\Facebook-Hub-by-LDA`). Không cài vào `Program Files`. Có thể dùng đường dẫn có dấu cách hoặc tiếng Việt.
3. Trình cài tạo bên trong thư mục gốc:

```text
<thư mục gốc>\
├── App\        chương trình
├── Data\       lịch, CRM, cài đặt
├── Sessions\   phiên đăng nhập Facebook của từng tài khoản
├── Media\      ảnh/video dùng cho bài đăng
├── Logs\       nhật ký đã khử dữ liệu nhạy cảm
└── Backups\    bản sao lưu
```

4. Trình cài hỏi có **tự khởi động cùng Windows** hay không (mặc định: Không). Có thể đổi lại trong *Cài đặt → Chạy nền*.
5. Shortcut được tạo trên Desktop và Start Menu.

## 4. Lần mở đầu tiên

Ứng dụng mở ra trống: 0 tài khoản, 0 chiến dịch, 0 khách hàng, Google chưa kết nối.

- Vào **Tài khoản → Thêm tài khoản**, rồi tự đăng nhập Facebook trong cửa sổ ứng dụng. Ứng dụng không lưu mật khẩu hay OTP. Nếu Facebook yêu cầu OTP, CAPTCHA hoặc xác minh, hãy tự xử lý.
- Đóng cửa sổ chỉ thu nhỏ xuống khay hệ thống (góc phải thanh tác vụ); lịch vẫn chạy. Muốn dừng hẳn: chuột phải biểu tượng khay → **Thoát hoàn toàn**.
- Khi còn lịch đã duyệt, ứng dụng ngăn máy **tự** ngủ nhưng vẫn cho màn hình tắt. Ứng dụng không chống được việc bạn chủ động Sleep/Shut down, gập nắp hoặc hết pin — khi đó bài sẽ chuyển sang "Đã lỡ lịch" và **không tự đăng bù**.

## 5. Cập nhật

Không có cập nhật tự động. Khi có bản mới, tải bộ cài mới và cài vào **cùng thư mục gốc**: chỉ thư mục `App` được thay, dữ liệu được giữ nguyên.

> **Quan trọng:** không dùng bộ cài **1.0.0-beta.1** để cài lại hoặc cài đè — bộ cài đó có lỗi có thể xóa cả thư mục dữ liệu. Hãy dùng bộ cài 1.0.0-beta.2 trở lên. Nên sao lưu (Cài đặt → Sao lưu) trước khi cập nhật.

## 6. Gỡ cài đặt

*Settings → Apps → Facebook Hub by LDA → Uninstall*. Mặc định trình gỡ **giữ lại** dữ liệu (Data, Sessions, Media, Logs, Backups). Trình gỡ sẽ hỏi riêng (hai lần xác nhận, mặc định "No") nếu bạn muốn xóa luôn dữ liệu.
