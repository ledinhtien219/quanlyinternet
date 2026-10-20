# Android Box Agent API — Parent Hub V4

Heartbeat (khoảng 10–20 giây/lần):

```http
POST http://<IP_PARENT_HUB>/api/agent/heartbeat
Content-Type: application/json
```

```json
{
  "id": "b859ce7eedbe",
  "mac": "b8:59:ce:7e:ed:be",
  "ip": "192.168.1.14",
  "active": true,
  "appLabel": "YouTube",
  "appPackage": "com.google.android.youtube.tv"
}
```

Response:

```json
{
  "ok": true,
  "locked": false,
  "remainingMin": 84
}
```

Đọc policy:

```http
GET http://<IP_PARENT_HUB>/api/agent/policy?id=b859ce7eedbe
```

Agent nên:

- Gửi `active=true` khi người dùng đang thực sự sử dụng Box / màn hình hoạt động.
- Gửi `appLabel` + `appPackage` của foreground app khi có quyền Usage Access.
- Khi `locked=true`: đưa màn hình khóa lên foreground và chặn quay lại nội dung theo mức quyền Android TV cho phép.
- Không cần gửi `appLabel/appPackage` khi `active=false`.
