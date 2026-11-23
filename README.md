# XamReader

Đọc diễn đàn XenForo 2.x, lọc ảnh/video từ chủ đề. Expo SDK 52 + React Native 0.76 + TypeScript.

## Build file .ipa (không cần Mac) — dùng GitHub Actions
1. Tạo repo GitHub (private cũng được), đẩy **toàn bộ** thư mục này lên nhánh `main` (nhớ cả thư mục `.github`).
2. Vào tab **Actions** > **Build Unsigned IPA** > **Run workflow**. Mất khoảng 15–25 phút.
3. Khi xong, mở lần chạy đó, kéo xuống **Artifacts**, tải `XamReader-unsigned-ipa`, giải nén ra `XamReader.ipa`.
4. File này **chưa ký**. Ký và cài bằng ESign / Sideloadly / AltStore bằng Apple ID của bạn.

## Chạy thử trên Mac (tuỳ chọn)
```
npm install
npx expo install --fix
npx expo prebuild --platform ios
npx expo run:ios
```
Không chạy được trong Expo Go vì có module native (cookies, webview).

## Tuỳ biến thành app của riêng bạn
- Tên app, mã gói (`bundleIdentifier`), icon: sửa trong `app.json` (icon là `assets/icon.png`, 1024x1024, không trong suốt).
- Domain diễn đàn mặc định và link file cấu hình từ xa: `src/services/domain.ts`
  (`DEFAULT_DOMAIN`, `REMOTE_CONFIG_URL`; mẫu file JSON: `domain.example.json`).
- Các file `index.html`, `sw.js`, `manifest.webmanifest`, `api/`, `vercel.json` là bản web/PWA, không dùng khi build iOS.
