# Parent Hub – Quản lý Internet & thời gian thiết bị cho trẻ

Parent Hub là dự án ESP32 DevKit V1 dùng để giám sát và quản lý thời gian sử dụng thiết bị trong gia đình, tập trung vào **ViettelTV 4K Box / Android TV** và **iPad của trẻ**.

## Tính năng hiện tại

- ESP32 kết nối Wi‑Fi chính và có captive portal cấu hình lại khi cần.
- Dashboard Web responsive theo giao diện Parent Hub Pro.
- Đăng ký thiết bị, nhóm Bé/Bố mẹ/Khách/IoT.
- Giới hạn thời gian theo ngày, khung giờ, khóa/mở, +15/+30 phút.
- Quét LAN, lưu IP/MAC và tên thiết bị khi thiết bị công bố hostname.
- Android Box Agent protocol để nhận heartbeat, app foreground và usage.
- Báo cáo 7 ngày.
- **Kiểm tra phiên bản mới từ GitHub** tại **Cài đặt → Cập nhật Parent Hub**.

> Với iPad, khi chưa tích hợp sâu router/Apple Screen Time, thời gian hiển thị là ước tính hoạt động mạng, không phải Screen Time của Apple.

## Source hiện tại

Gói source V4 đang được lưu tại:

`source/ParentHub_Pro_V4.zip`

Bên trong có:

- `ParentHub.ino`
- `web_ui.h`
- `AGENT_PROTOCOL.md`
- `QA_CHECK.md`
- `VERSION.txt`

Để phát triển local, giải nén gói trên vào một thư mục tên `ParentHub`, sau đó mở `ParentHub.ino` bằng Arduino IDE.

## Cài firmware bằng Arduino IDE

1. Cài ESP32 core:
   `https://espressif.github.io/arduino-esp32/package_esp32_index.json`
2. Library Manager → cài **ArduinoJson by Benoit Blanchon**.
3. Giải nén `source/ParentHub_Pro_V4.zip`.
4. Mở `ParentHub.ino`.
5. Board: `DOIT ESP32 DEVKIT V1` (hoặc `ESP32 Dev Module`).
6. Chọn cổng COM và Upload.

## Cập nhật phiên bản

Firmware đọc manifest:

`update.json`

Khi bấm **Kiểm tra cập nhật**, ESP32 so sánh `FW_VERSION` hiện tại với `version` trên GitHub và hiển thị ghi chú bản mới cùng link Release.

Hiện tại đây là **kiểm tra phiên bản + dẫn tới file phát hành**. OTA tự động trực tiếp từ ESP32 sẽ được bổ sung sau khi luồng Release/firmware ổn định trên phần cứng thật.

## GitHub Actions

Workflow `.github/workflows/build-release.yml`:

- tự giải nén source V4;
- cài ESP32 Arduino Core + ArduinoJson;
- compile firmware;
- tạo artifact `ParentHub.bin`;
- khi push tag `vX.Y.Z`, đính kèm `ParentHub.bin` vào GitHub Release.

## Tài liệu

- `docs/AGENT_PROTOCOL.md` – giao thức Android Box Agent.
- `docs/QA_CHECK.md` – checklist kiểm thử.

## Quy trình phát hành

1. Tăng `FW_VERSION`.
2. Cập nhật `VERSION.txt` và `update.json`.
3. Commit/push lên `main`.
4. Xác nhận GitHub Actions build thành công.
5. Tạo tag, ví dụ `v4.1.0`, và push tag.
6. GitHub Actions tạo Release asset `ParentHub.bin`.
