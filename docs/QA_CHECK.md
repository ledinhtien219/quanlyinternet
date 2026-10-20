# Parent Hub Pro V4 — QA checklist

## Đã kiểm tra trước khi đóng gói

- Tên sketch/folder Arduino khớp `ParentHub/ParentHub.ino`.
- Web UI được tách riêng trong `web_ui.h`.
- JavaScript của Web UI đã được kiểm tra cú pháp bằng Node.js.
- Có API kiểm tra bản mới: `/api/update/check`.
- Manifest phiên bản nằm tại `update.json` trên GitHub.
- Không hard-code Wi‑Fi nhà trong firmware; Wi‑Fi chính có thể đổi từ trang Cài đặt.
- Có fallback `ParentHub-Setup` khi không vào được Wi‑Fi đã lưu.

## Cần xác nhận trên phần cứng thật

- Compile/upload với ESP32 Arduino Core đang dùng trên máy thật.
- Quét Wi‑Fi/LAN trong điều kiện router ZTE F670Y thực tế.
- Enforcement cắt/mở Internet qua ZTE F670Y.
- Android Box Agent trên ViettelTV 4K Box Android 10.
- Thời gian chạy dài, mất điện/khởi động lại, thay đổi IP DHCP.
- Luồng cập nhật firmware thực tế sau khi có GitHub Release.
