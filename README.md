# [Bài tập] Tái cấu trúc mã CSS của các bài tập đã làm (Landing Page với SASS)

## 🎯 Mục tiêu bài tập
- Luyện tập và củng cố toàn diện kỹ năng sử dụng **SASS / SCSS** trong dự án thực tế.
- Tái cấu trúc và hợp nhất toàn bộ mã CSS của 4 bài tập Landing Page đã thực hiện:
  1. **[Bài tập] Dựng navigation và header của landing page thiết kế sẵn.**
  2. **[Bài tập] Dựng phần sản phẩm nổi bật của landing page thiết kế sẵn.**
  3. **[Bài tập] Dựng phần số liệu thống kê của landing page thiết kế sẵn.**
  4. **[Bài tập] Dựng phần footer của landing page thiết kế sẵn.**
- Tối ưu hóa mã CSS thông qua việc áp dụng các tính năng cốt lõi của SASS: **Variables, Nesting, Mixins, Partials và Modules (@use)**.

---

## 🚀 Các tính năng SASS đã áp dụng

### 1. Variables (Biến trong SASS) - `abstracts/_variables.scss`
- **Màu sắc (Colors):** Quản lý tập trung màu chủ đạo (`$color-primary: #4f46e5;`), màu điểm nhấn (`$color-secondary: #06b6d4;`), màu nền (`$color-bg-page: #f8fafc;`, `$color-dark: #0f172a;`) và hệ thống gradient hiện đại.
- **Typography:** Khai báo kiểu chữ (`$font-family-base`), tỷ lệ kích thước font (`$font-size-base`, `$font-size-hero`,...), font-weight.
- **Hệ thống khoảng cách & bo góc:** `$spacing-xs` đến `$spacing-4xl`, `$radius-sm` đến `$radius-full`.
- **Hệ thống đổ bóng:** `$shadow-sm`, `$shadow-md`, `$shadow-lg`, `$shadow-xl`.
- **Breakpoints:** `$breakpoint-sm`, `$breakpoint-md`, `$breakpoint-lg`, `$breakpoint-xl`.

### 2. Nesting (Lồng bộ chọn)
- Cấu trúc các khối CSS lồng nhau tự nhiên, trực quan theo chuẩn **BEM (Block Element Modifier)**:
  ```scss
  .header {
    &__container { ... }
    &__nav {
      &-list { ... }
      &-link {
        &:hover, &--active { ... }
      }
    }
  }
  ```

### 3. Mixins (Tái sử dụng mã) - `abstracts/_mixins.scss`
- **Responsive Media Query Mixin:** `@mixin respond-to($breakpoint)` giúp xử lý giao diện thích ứng đa màn hình ngắn gọn:
  ```scss
  @include respond-to("md") { font-size: $font-size-2xl; }
  ```
- **Flexbox Helpers:** `@mixin flex(...)`, `@mixin flex-center`, `@mixin flex-between`.
- **Hiệu ứng Glassmorphism:** `@mixin glassmorphism` tạo thanh Navbar mờ kính cao cấp.
- **Chữ chuyển màu Gradient:** `@mixin text-gradient($gradient)`.
- **Base Components Mixins:** `@mixin button-base`, `@mixin card-base`, `@mixin text-truncate`.

### 4. Kiến trúc mô-đun hóa SASS (7-1 Pattern)
- Chia nhỏ mã nguồn thành các thư mục chuyên biệt: `abstracts`, `base`, `components`, `layout`.
- Tổng hợp qua file trung tâm [main.scss](file:///d:/BaiTapGithub/main.scss) sử dụng cú pháp chuẩn mới `@use`.

---

## 📁 Cấu trúc thư mục dự án

```
d:\BaiTapGithub\
├── abstracts/
│   ├── _variables.scss       # Khai báo Design tokens (màu sắc, typography, spacing, shadows)
│   └── _mixins.scss          # Mixins (responsive, flexbox, glassmorphism, buttons, cards)
├── base/
│   ├── _reset.scss           # Reset CSS, container, base section
│   └── _typography.scss      # Kiểu chữ tiêu đề h1-h4, text helpers
├── components/
│   ├── _buttons.scss         # Nút bấm (.btn, .btn--primary, .btn--gradient, .btn--outline)
│   └── _cards.scss           # Thẻ hiển thị (.card--product, .card--stat)
├── layout/
│   ├── _header.scss          # [Bài tập] Dựng Navigation và Header (Sticky Navbar)
│   ├── _hero.scss            # Hero Banner (Tiêu đề, CTA, Visual mockup)
│   ├── _products.scss        # [Bài tập] Dựng phần Sản phẩm nổi bật
│   ├── _statistics.scss      # [Bài tập] Dựng phần Số liệu thống kê
│   └── _footer.scss          # [Bài tập] Dựng phần Footer
├── main.scss                 # File SASS trung tâm (@use các partials)
├── styles.css                # File CSS biên dịch từ SCSS
├── styles.css.map            # Source map hỗ trợ debug
├── index.html                # Landing Page hoàn chỉnh kết nối 4 phần bài tập
├── package.json              # Khai báo npm scripts
├── .gitignore
└── README.md                 # Tài liệu hướng dẫn & báo cáo bài tập
```

---

## 🛠 Hướng dẫn cài đặt & biên dịch

1. **Cài đặt thư viện (nếu cần):**
   ```bash
   npm install
   ```

2. **Biên dịch SCSS sang CSS:**
   ```bash
   npm run build:sass
   # Hoặc chạy trực tiếp qua npx:
   npx sass main.scss styles.css
   ```

3. **Chế độ theo dõi tự động (Watch mode):**
   ```bash
   npm run watch:sass
   ```

4. **Kiểm tra giao diện:**
   Mở trực tiếp file `index.html` bằng trình duyệt web.

---

## 🎯 Kết quả đạt được
✔ Tái cấu trúc và hợp nhất thành công 4 phần bài tập Landing Page thành một hệ thống giao diện hoàn chỉnh, đồng bộ.  
✔ Tận dụng triệt để sức mạnh của SASS (Variables, Mixins, Nesting, Modules), loại bỏ hoàn toàn lặp mã.  
✔ Thiết kế giao diện hiện đại, chuyên nghiệp, responsive 100% trên cả Desktop, Tablet và Mobile.  
✔ Biên dịch CSS chuẩn xác, sạch sẽ, không có bất kỳ warning hay lỗi nào.
