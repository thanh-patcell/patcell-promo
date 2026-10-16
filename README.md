# patcell-promo

Nguồn nội dung quảng bá chéo giữa các game/app của Patcell (Patcell Ads SDK). Được phát tại
**https://promo.patcell.com/** qua Cloudflare Pages (thư mục `public/`, nhánh `main`).

Thiết kế: `docs/monetization/PATCELL-ADS-SDK.md` trong repo `thanh-patcell/riveriq` (Sen Journey 1.5.0).

## Cấu trúc (dự kiến)

```
registry/apps.yaml        người sửa: allowlist game Patcell + thông tin không tự lấy được
registry/overrides.yaml   người sửa: chiến dịch nổi bật, trang store riêng, creative riêng
public/v1/catalog.json    máy sinh (GitHub Action hằng ngày)
public/v1/campaigns.json  máy sinh + ký Ed25519 (campaigns.json.sig)
public/v1/assets/         icon, ảnh quảng cáo
```

## Quy tắc

- Repo public: không bao giờ commit khóa, token hay dữ liệu người dùng. Khóa ký và service account chỉ nằm trong GitHub Secrets.
- Mọi thay đổi đi qua Pull Request và có người duyệt nội dung (game dành cho mọi lứa tuổi).
- Chỉ link tới `apps.apple.com` / `play.google.com`; chỉ quảng bá app có độ tuổi ≤ app nguồn.
- Chỉ dữ liệu (JSON, ảnh); không có code chạy trong app.
