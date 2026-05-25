# 📖 Hướng dẫn cài đặt GitHub Profile đẹp

## Bước 1: Tạo repository profile

1. Đăng nhập GitHub → **New repository**
2. **Repository name** = `TÊN_GITHUB_CỦA_BẠN` (phải trùng khớp chính xác)
   - Ví dụ: nếu username là `john123` thì repo name là `john123`
3. Chọn **Public**
4. Tick ✅ **Add a README file**
5. Nhấn **Create repository**

---

## Bước 2: Thay thế nội dung README

Mở file `README.md` trong repo vừa tạo, dán nội dung từ file `README.md` trong thư mục này.

**⚠️ Nhớ thay tất cả `YOUR_USERNAME` bằng username GitHub thực của bạn!**

---

## Bước 3: Thay thông tin cá nhân

Tìm và thay các chỗ sau:

| Cần thay | Giá trị thực |
|---|---|
| `YOUR_USERNAME` | Username GitHub của bạn |
| `your@email.com` | Email liên hệ |
| `YOUR_ZALO` | Số Zalo của bạn |
| Link project GitHub | URL repo thực tế của bạn |

---

## Bước 4: Thêm Snake Animation (tùy chọn - cực đẹp!)

Thêm GitHub Action để tự động tạo snake animation từ contribution graph:

Tạo file `.github/workflows/snake.yml` trong repo profile:

```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 */12 * * *"
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Sau đó chạy workflow thủ công lần đầu: **Actions → Generate Snake Animation → Run workflow**

---

## Bước 5: Cập nhật link Snake trong README

Sau khi chạy action thành công, thay link snake bằng:

```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" 
    srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" 
    srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake.svg" />
  <img alt="github-snake" 
    src="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake-dark.svg" />
</picture>
```

---

## Các widget GitHub Stats đang dùng

| Widget | Mô tả |
|---|---|
| `github-readme-stats` | Thống kê tổng quan, ngôn ngữ |
| `readme-typing-svg` | Hiệu ứng chữ gõ đầu trang |
| `streak-stats` | Chuỗi ngày commit liên tiếp |
| `komarev.com/ghpvc` | Đếm lượt xem profile |
| `shields.io` | Badge công nghệ |

---

## Lưu ý quan trọng

- File `README.md` duy nhất này sẽ **tự động hiển thị** trên trang profile GitHub của bạn
- File `README_VI.md` = phiên bản thuần tiếng Việt
- File `README_EN.md` = phiên bản thuần tiếng Anh
- Bạn có thể chọn 1 trong 3 file hoặc dùng file `README.md` song ngữ

---

*Được tạo bởi AI — chỉnh sửa theo nhu cầu của bạn!* 🚀
