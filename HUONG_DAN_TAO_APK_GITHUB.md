# Hướng dẫn tạo APK không cần cài Godot trên máy tính

1. Đăng nhập GitHub và tạo một repository riêng tư (Private).
2. Giải nén gói mã nguồn này, tải toàn bộ **nội dung bên trong thư mục SkyDashOffline**, kể cả thư mục ẩn `.github`, lên thư mục gốc repository. GitHub web Upload files có thể không giữ thư mục rỗng, điều đó không ảnh hưởng.
3. Vào tab **Actions** → **Build Android test APK** → **Run workflow**.
4. Chọn lần chạy, kiểm tra log. Khi thành công, mục **Artifacts** có tên `SkyDashHeroes-Test-APK` để tải file ZIP chứa `SkyDashHeroes-Test.apk`.
5. Trên điện thoại Android, giải nén ZIP, mở APK và cho phép cài từ nguồn này khi được yêu cầu.

Lưu ý: Pipeline này chưa được chạy kiểm thử trong môi trường hiện tại. Nếu GitHub Actions báo lỗi, gửi log để xác định lỗi dự án hoặc cấu hình. Workflow dùng image cộng đồng barichello/godot-ci:4.3 có SDK, export templates và debug keystore. Không dùng APK debug để phát hành Play Store. APK sẽ được ký bằng debug keystore (khác release signing).

Nếu muốn build hoàn toàn trên máy Windows, dùng Godot 4.3 (Standard), cài Android Export Templates và SDK rồi vào Project → Export → Android → Export Project, đánh dấu Export With Debug.
