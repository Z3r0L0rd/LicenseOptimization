# License Optimization Documentation

Đây là tài liệu hướng dẫn về License Optimization được xây dựng bằng Hugo với theme hugo-theme-learn.

## Deploy lên GitHub Pages

### Bước 1: Chuẩn bị Repository
1. Tạo repository mới trên GitHub
2. Upload toàn bộ code lên repository

### Bước 2: Cấu hình GitHub Pages
1. Vào Settings của repository
2. Chọn Pages từ menu bên trái
3. Trong Source, chọn "GitHub Actions"

### Bước 3: Cập nhật baseURL
Trong file `config.toml`, thay đổi:
```toml
baseURL = "https://[YOUR-USERNAME].github.io/[YOUR-REPO-NAME]/"
```

Thay `[YOUR-USERNAME]` bằng username GitHub của bạn và `[YOUR-REPO-NAME]` bằng tên repository.

### Bước 4: Deploy
1. Push code lên branch `main`
2. GitHub Actions sẽ tự động build và deploy
3. Site sẽ có sẵn tại `https://[YOUR-USERNAME].github.io/[YOUR-REPO-NAME]/`

## Local Development

Để chạy local:
```bash
hugo server -D
```

## Build Production

Để build cho production:
```bash
hugo --minify
```

Files sẽ được tạo trong thư mục `public/`.