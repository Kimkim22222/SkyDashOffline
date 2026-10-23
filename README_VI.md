# SKY DASH HEROES — dự án Godot 4 (Android/offline)

## Phạm vi đã có trong mã nguồn
- Game endless runner 3D góc nhìn sau lưng, 3 làn; điều khiển bằng vuốt/chạm hoặc bàn phím.
- 10 nhân vật nguyên bản (4 nam, 4 nữ, 1 robot, 1 người thú) (không sử dụng nhân vật thương mại có bản quyền).
- 10 biến thể trang phục / nhân vật: 100 tổ hợp, mua bằng xu chơi game, lưu offline.
- 15 kỹ năng có chọn kỹ năng, nâng cấp bằng xu và cooldown.
- 5 bối cảnh: đường phố, đường sắt, trời, tuyết, sân bay; các vật cản 3 dạng, xu.
- Level/XP, điểm kỷ lục, kho đồ, tùy chỉnh chất lượng, âm thanh, lưu trạng thái JSON trên điện thoại.
- Các mô hình 3D hiện dựng theo hình học procedural. Có động tác tay/chân đơn giản, chưa có rig/animation chuyên nghiệp.
- Âm thanh WAV tổng hợp đơn giản, theo từng bối cảnh; không phải thư viện hiệu ứng thu âm thực tế.

## Chạy / phát triển
1. Tải Godot 4.x bản ổn định (chọn Godot 4.6 hoặc mới hơn trong nhánh 4).
2. Open / Import dự án từ thư mục này: `project.godot`.
3. Nhấn F6/F5 để thử trên máy tính. Phím ← → để đổi làn, ↑ hoặc Space nhảy, ↓ trượt, E dùng skill, Esc tạm dừng. Điện thoại dùng swipe hoặc các nút cảm ứng.
4. Trước khi xuất bản phải chạy thử trên thiết bị Android thực tế và sửa lỗi phát hiện được.

## Xuất APK để kiểm thử trên Android (trước khi phát hành Google Play)
1. Cài Android SDK với platform Android API 36+, SDK Build-tools, Java/JDK theo hướng dẫn bản Godot đang sử dụng.
2. Trong Godot: **Editor > Manage Export Templates** cài export templates khớp bản engine; **Editor Settings > Export > Android** cấu hình Java SDK và Android SDK (hoặc dùng setup tự động nếu phiên bản hỗ trợ).
3. **Project > Install Android Build Template** rồi cập nhật template Gradle / targetSdk thành >= 36. Đảm bảo template Gradle tương thích Android 16.
4. Trong **Project > Export > Android** xác nhận package id độc nhất (đang đặt mẫu `com.studio.skydashheroes`), tên, icon, version code, Gradle Build, AAB, arm64.
5. Tạo release keystore và lưu ngoài repo: `keytool -genkeypair -v -keystore release.keystore -alias skydash -keyalg RSA -keysize 2048 -validity 10000`. Khai báo keystore/password trong export preset giao diện Godot, KHÔNG đưa khóa hoặc mật khẩu lên mạng hay vào ZIP này.
6. Export Project > **Release** > `.aab`, xác nhận target API 36 trở lên, kiểm tra Play Console policy (target SDK, 64-bit, data safety, store listing, age rating, icon, screenshots, privacy policy nếu áp dụng) trước khi đăng.

## Lưu ý chất lượng
Đây là **nguyên mẫu mã nguồn có thể mở trong Godot**, chưa phải game hoàn thiện với art nhân vật 3D chi tiết. Chưa tạo được AAB đã ký vì môi trường xây dựng không có Godot editor/export templates/Android SDK và không có khóa ký release riêng của chủ sở hữu. Bạn phải build và thử nghiệm trước khi nộp Play Console.

## Quyền sử dụng
Toàn bộ tên nhân vật trong dự án là nhân vật mới, không phải Spider-Man, Naruto, Goku, Iron Man, Sailor Moon,... Muốn dùng nhân vật nổi tiếng thật trong app phân phối công khai cần bảo đảm quyền/licensing hợp pháp đối với nhân vật, tạo hình, biểu tượng và âm thanh.

## Bản Android thử nghiệm (APK)
1. Mở dự án bằng Godot 4.x; cài **Export Templates** cùng phiên bản với Godot.
2. Cài **OpenJDK 17**, **Android SDK** và **Android Build Tools**. Thiết lập đường dẫn trong Editor Settings > Export > Android.
3. Project > Export > Add > Android nếu chưa có; chọn file `build/SkyDashHeroes-Test.apk` và **Debug / Export Project**. Godot sẽ ký bằng khóa debug để cài thử. Không cần keystore phát hành ở bước này.
4. Chép APK vào điện thoại, cho phép cài ứng dụng thử nghiệm và mở game.
5. Nếu export preset bật Gradle, cần cài Android Build Template trong Project và kiểm tra phiên bản API phù hợp. Nếu chỉ test APK, có thể tắt Gradle khi không cần plugin Android.

**Lưu ý:** Không có tệp APK được biên dịch trong gói nguồn này. Hệ thống tạo gói không có Godot, Android SDK, Android Export Templates nên không thể kiểm chứng bản chạy Android tại đây. Mô hình vẫn là nguyên mẫu hình khối, chưa phải 3D nhân vật hoàn thiện.
