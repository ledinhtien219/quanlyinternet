# Parent Hub – Quản lý Internet & thời gian thiết bị cho trẻ

Parent Hub là dự án ESP32 DevKit V1 dùng để giám sát và quản lý thời gian sử dụng thiết bị trong gia đình, tập trung vào **ViettelTV 4K Box / Android TV** và **iPad của trẻ**.

## Tính năng hiện tại

- ESP32 kết nối Wi‑Fi chính và có captive portal cấu hình lại khi cần.
- Dashboard Web responsive, giao diện desktop/mobile.
- Đăng ký thiết bị, nhóm Bé/Bố mẹ/Khách/IoT.
- Giới hạn thời gian theo ngày, khung giờ, khóa/mở, +15/+30 phút.
- Quét LAN, lưu IP/MAC và tên thiết bị khi thiết bị công bố hostname.
- Android Box Agent protocol để nhận heartbeat, app foreground và usage.
- Báo cáo 7 ngày.
- **Kiểm tra cập nhật phiên bản từ GitHub** tại Cài đặt → Cập nhật Parent Hub.

> Lưu ý: với iPad, khi chưa tích hợp sâu router/Apple Screen Time, thời gian hiển thị là ước tính hoạt động mạng, không phải Screen Time của Apple.

## Cài firmware bằng Arduino IDE

1. Cài ESP32 core: `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
2. Library Manager → cài **ArduinoJson by Benoit Blanchon**.
3. Mở `firmware/ParentHub/ParentHub.ino`.
4. Board: `DOIT ESP32 DEVKIT V1` (hoặc `ESP32 Dev Module`).
5. Chọn cổng COM và Upload.

## Cấu trúc

- `firmware/ParentHub/` – firmware ESP32 + Web UI nhúng trong flash.
- `docs/` – protocol Android Box Agent và checklist test.
- `update.json` – manifest được firmware kiểm tra để phát hiện phiên bản mới.
- `.github/workflows/build-release.yml` – build firmware tự động; tag `vX.Y.Z` tạo GitHub Release và file `ParentHub.bin`.

## Quy trình phát hành

1. Tăng `FW_VERSION` trong `ParentHub.ino`.
2. Cập nhật `update.json` và `VERSION.txt`.
3. Commit/push.
4. Tạo tag, ví dụ `v4.1.0`, và push tag.
5. GitHub Actions sẽ build và đính kèm `ParentHub.bin` vào Release.

Repository: https://github.com/ledinhtien219/quanlyinternet
