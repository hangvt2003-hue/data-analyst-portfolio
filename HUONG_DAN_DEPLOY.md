# 🚀 Hướng dẫn Deploy Portfolio lên GitHub Pages (cho người chưa biết Git)

Tài liệu này hướng dẫn **từng bước cực kỳ chi tiết** để đưa portfolio lên mạng dưới dạng một website công khai, miễn phí, dùng GitHub Pages. Không cần biết dùng dòng lệnh — toàn bộ hướng dẫn dùng giao diện web (GitHub.com) và kéo-thả file.

**Kết quả cuối cùng:** Một URL dạng `https://hangvt2003-hue.github.io/` mà ai cũng vào được.

**Thời gian dự kiến:** ~20 phút lần đầu, sau đó update chỉ mất ~2 phút mỗi lần.

---

## 📋 Mục lục

1. [Chuẩn bị trước khi deploy](#1-chuẩn-bị-trước-khi-deploy)
2. [Tạo tài khoản GitHub](#2-tạo-tài-khoản-github)
3. [Tạo repository (kho chứa code)](#3-tạo-repository-kho-chứa-code)
4. [Upload toàn bộ folder portfolio lên GitHub](#4-upload-toàn-bộ-folder-portfolio-lên-github)
5. [Bật GitHub Pages](#5-bật-github-pages)
6. [Kiểm tra website đã chạy](#6-kiểm-tra-website-đã-chạy)
7. [Cách update website sau này](#7-cách-update-website-sau-này)
8. [Xử lý lỗi thường gặp](#8-xử-lý-lỗi-thường-gặp)

---

## 1. Chuẩn bị trước khi deploy

Trước khi bắt đầu, hãy hoàn tất **4 việc** này. Đây là những chỗ còn placeholder cần điền:

### ✅ Việc 1: Thêm ảnh chân dung

- Tìm 1 ảnh chân dung dạng dọc, độ phân giải >= 600×800px, dạng `.jpg`.
- Đặt tên file là `profile.jpg`.
- Copy file vào folder `assets/img/` (ghi đè file `profile.jpg` cũ nếu có).

### ✅ Việc 2: Thêm PDF báo cáo Customer Behavior Supermarket

- Lấy file PDF báo cáo dự án "Customer Behavior at Supermarket" của bạn.
- Đổi tên thành đúng `customer-behavior-supermarket.pdf`.
- Copy vào folder `assets/`.

### ✅ Việc 3: Điền link Google Colab cho dự án Suicide Rates

1. Mở notebook Colab, bấm **Share → Anyone with the link → Viewer**, copy URL.
2. Mở file `projects/suicide-rates-analysis.html`, tìm `REPLACE_WITH_COLAB_URL`, thay bằng URL Colab.

### ✅ Việc 4: Điền link nhúng Power BI cho dự án HR Dashboard

1. Trong Power BI Service, mở dashboard HR → **File → Embed report → Publish to web (public)**.
2. Copy URL trong thuộc tính `src` của iframe (URL này có dạng `https://app.powerbi.com/view?r=…`).
3. Mở `projects/hr-power-bi-dashboard.html`, tìm iframe có `src="about:blank"`, thay `about:blank` bằng URL vừa copy. Xoá luôn các thuộc tính `data-pbi-placeholder` và `onload`.

> 💡 **Tip:** Nếu chưa có sẵn 1 trong 4 thứ trên, bạn vẫn có thể deploy được — website sẽ chỉ thiếu phần đó. Hoàn thiện sau cũng được.

---

## 2. Tạo tài khoản GitHub

> 👉 **Bỏ qua bước này nếu bạn đã có tài khoản GitHub.**

1. Mở trình duyệt, vào **https://github.com/signup**.
2. Nhập email cá nhân, tạo password, chọn username.
3. **⚠️ QUAN TRỌNG VỀ USERNAME:**
   - Username sẽ trở thành 1 phần URL website của bạn.
   - Nên chọn username chuyên nghiệp, ví dụ: `hangvt2003-hue`, `hang-nguyen-da`, v.v.
   - Username này KHÔNG đổi được sau khi tạo (đổi được nhưng phức tạp), nên cân nhắc kỹ.
4. Verify email. Hoàn thành.

---

## 3. Tạo repository (kho chứa code)

**Repository** (gọi tắt là **repo**) là 1 folder online trên GitHub chứa code của bạn.

### Bước 3.1: Bắt đầu tạo repo

1. Sau khi đăng nhập, ở góc trên bên phải bấm dấu **`+`** → chọn **"New repository"**.
2. Hoặc vào trực tiếp: **https://github.com/new**

### Bước 3.2: Đặt tên repo CỰC KỲ QUAN TRỌNG

Để website chạy ở URL gốc dạng `https://USERNAME.github.io/` (đẹp nhất, không có đuôi), tên repo PHẢI giống hệt theo công thức:

```
USERNAME.github.io
```

**Ví dụ:** Nếu username là `hangvt2003-hue` thì tên repo là **`hangvt2003-hue.github.io`** (chữ "hue" không phải tiếng Việt — đây là username).

→ Trong ô **"Repository name"**, gõ chính xác `hangvt2003-hue.github.io` (thay bằng username thật của bạn).

### Bước 3.3: Cấu hình các option còn lại

| Tùy chọn | Chọn giá trị |
|---|---|
| Description (mô tả) | Có thể để trống hoặc gõ "Personal portfolio — Data Analyst" |
| Public / Private | **Public** (BẮT BUỘC để GitHub Pages hoạt động miễn phí) |
| Add a README file | **KHÔNG TÍCH** ô này (vì mình đã có README rồi) |
| Add .gitignore | **None** |
| Choose a license | **None** |

### Bước 3.4: Tạo

Bấm nút xanh **"Create repository"** ở dưới cùng.

→ Bạn sẽ thấy trang trống với hướng dẫn nhiều dòng lệnh. **Bỏ qua chúng** — mình sẽ làm theo cách dễ hơn ở Bước 4.

---

## 4. Upload toàn bộ folder portfolio lên GitHub

Có 2 cách: **(A) Kéo-thả qua trình duyệt** (dễ hơn) và **(B) Dùng GitHub Desktop** (dễ update sau này). Chọn cách (A) cho lần đầu.

### Cách A: Kéo thả qua trình duyệt (Recommended cho người mới)

1. Trên trang repo vừa tạo, tìm dòng chữ:
   > "**uploading an existing file**"

   (thường nằm gần cuối phần hướng dẫn, là 1 link xanh).
   Bấm vào link đó.

2. Bạn sẽ thấy 1 vùng có chữ "**Drag files here to add them to your repository**".

3. **Mở folder portfolio trên máy tính** (folder có chứa `index.html`, `assets/`, `projects/`...).

4. **Chọn TẤT CẢ các file và folder con** bên trong folder portfolio:
   - Trên Windows: vào folder, nhấn `Ctrl + A`.
   - Trên Mac: vào folder, nhấn `Cmd + A`.

   ⚠️ **Lưu ý cực kỳ quan trọng:** Phải chọn **NỘI DUNG BÊN TRONG** folder portfolio, KHÔNG kéo cả folder portfolio vào. Tức là `index.html` phải nằm ở gốc của repo.

5. Kéo thả tất cả vào vùng "Drag files here..." trên GitHub.

6. Đợi GitHub upload (có thể 1–2 phút tuỳ tốc độ mạng — sẽ thấy progress bar).

7. Khi upload xong, kéo xuống dưới sẽ thấy ô "**Commit changes**":
   - **Commit message** (dòng tiêu đề): gõ `Initial portfolio upload`
   - Để mặc định "**Commit directly to the `main` branch**".
   - Bấm nút xanh **"Commit changes"**.

8. Đợi vài giây — trang sẽ refresh, bạn sẽ thấy danh sách file đầy đủ trong repo.

### ✅ Kiểm tra cấu trúc

Sau khi upload xong, vào trang repo, bạn phải thấy NGAY ở cấp gốc:

```
index.html        ← Bắt buộc phải có ở đây
README.md
HUONG_DAN_DEPLOY.md
assets/
projects/
Game_Metrics_Brief.html
Engagement_Drop_Doc.html
Ad_Quality_Report.html
```

Nếu thấy 1 folder tên `portfolio/` hoặc `hang-nguyen-portfolio/` ở gốc thay vì các file trên, nghĩa là bạn đã upload nhầm cả folder. Cách khắc phục: xoá hết file, làm lại Bước 4 nhưng nhớ vào BÊN TRONG folder rồi mới chọn.

---

## 5. Bật GitHub Pages

Bây giờ "biến" repo thành website thực sự:

1. Trong trang repo, ở thanh tab phía trên (Code, Issues, Pull requests, ...), bấm vào **"Settings"** (ngoài cùng bên phải).

2. Ở menu bên trái, kéo xuống tìm và bấm vào **"Pages"** (nằm trong nhóm "Code and automation").

3. Phần **"Build and deployment"**, bạn sẽ thấy:
   - **Source**: chọn **"Deploy from a branch"** (thường mặc định đã đúng).
   - **Branch**: trong dropdown, chọn **`main`** (hoặc `master` nếu hiện chữ đó), folder để **`/ (root)`**.
   - Bấm nút **"Save"**.

4. Sau khi save, đợi ~1 phút, trang sẽ tự refresh và hiện 1 banner xanh dạng:
   > ✅ **Your site is live at https://hangvt2003-hue.github.io/**

   (URL sẽ khác, đúng theo username của bạn).

5. Bấm vào URL đó — bạn sẽ thấy website portfolio của mình!

> ⏳ **Lưu ý lần đầu:** Đôi khi website chưa hiện ra ngay sau bước này, mà phải đợi 2–5 phút (đôi khi đến 10 phút) để GitHub xử lý lần đầu. Nếu bấm vào URL mà thấy 404, đợi thêm 5 phút rồi thử refresh.

---

## 6. Kiểm tra website đã chạy

Mở URL `https://USERNAME.github.io/`, kiểm tra các điểm sau:

- [ ] Trang hero hiện ra với tên "Hang Nguyen" và ảnh chân dung.
- [ ] Section "Selected Work" hiện 9 project, năm hiển thị đúng (5 project năm 2026, 2 project 2025, 2 project 2024).
- [ ] Bấm vào 1 project bất kỳ → mở trang case study.
- [ ] Section "Skills & Stack" KHÔNG còn DBeaver.
- [ ] Section "From the Blog" có 3 blog, bấm vào → mở đúng URL bên ngoài (LinkedIn/Medium...).
- [ ] Bấm nút "Download CV" → tải về file PDF, mở ra không có DBeaver.

Nếu có chỗ nào sai, xem mục **8. Xử lý lỗi thường gặp** phía dưới.

---

## 7. Cách update website sau này

Khi cần sửa nội dung (thêm project, đổi text, sửa ảnh...), KHÔNG cần upload lại từ đầu. Có 2 cách:

### Cách 1: Sửa trực tiếp 1 file trên GitHub (đơn giản nhất, dùng cho sửa text)

1. Vào repo trên GitHub, bấm vào file cần sửa (ví dụ `index.html`).
2. Bấm icon **bút chì** ✏️ ở góc trên bên phải khung code.
3. Sửa nội dung.
4. Kéo xuống dưới, gõ commit message (ví dụ: `Update CV link`), bấm **"Commit changes"**.
5. Đợi 1–2 phút, website sẽ tự cập nhật.

### Cách 2: Upload thêm file mới hoặc thay file cũ

1. Vào repo, bấm nút **"Add file"** ở góc trên bên phải → **"Upload files"**.
2. Kéo thả file mới vào (nếu trùng tên file cũ, sẽ ghi đè).
3. Commit changes.

### Cách 3: Dùng GitHub Desktop (tiện cho nhiều sửa đổi cùng lúc)

Tải tại **https://desktop.github.com/**. Sau khi clone repo về máy, mỗi lần sửa file ở local rồi:
- Mở GitHub Desktop → ghi commit message → bấm "Commit to main" → bấm "Push origin".
- Website tự cập nhật sau ~1 phút.

---

## 8. Xử lý lỗi thường gặp

### ❌ Vào URL thấy 404 — "There isn't a GitHub Pages site here"

**Nguyên nhân:** GitHub chưa kịp build, hoặc cấu trúc file sai.

**Kiểm tra:**
1. File `index.html` có nằm ở **gốc repo** không? (không phải trong subfolder)
2. Đã đợi đủ 5 phút sau khi bật Pages chưa?
3. Vào **Settings → Pages**, banner có hiện URL màu xanh không?

→ Nếu file `index.html` đang trong subfolder, vào subfolder đó trên GitHub, bấm vào file → **"Edit"** → ở ô tên file, đổi đường dẫn xoá phần subfolder → commit. Hoặc xoá hết và upload lại đúng.

### ❌ Website chạy nhưng ảnh chân dung không hiện

**Nguyên nhân:** File `assets/img/profile.jpg` chưa có hoặc tên file viết hoa-thường khác.

**Khắc phục:** Trên GitHub, mở folder `assets/img/`, kiểm tra tên file CHÍNH XÁC là `profile.jpg` (chữ thường, đuôi `.jpg` không phải `.JPG` hay `.jpeg`).

### ❌ Bấm vào blog ra trang trắng / 404

**Nguyên nhân:** Compaclass blog tạm thời không truy cập được, hoặc URL bị thay đổi.

**Khắc phục:** Mở `index.html`, tìm 3 chuỗi `compaclass.com/blog/p/...` trong mảng `BLOG_POSTS`, kiểm tra URL còn hoạt động không. Nếu cần đổi, sửa lại URL trong dấu nháy đơn rồi commit.

### ❌ Section Skills vẫn còn DBeaver

**Nguyên nhân:** Cache trình duyệt.

**Khắc phục:** Nhấn `Ctrl + F5` (Windows) hoặc `Cmd + Shift + R` (Mac) để xoá cache và load lại.

### ❌ Bấm "Download CV" tải về file cũ

**Nguyên nhân:** Cache, hoặc file PDF chưa được upload.

**Khắc phục:** Vào folder `assets/cv/` trên GitHub, kiểm tra file `Hang_Nguyen_DA_CV.pdf` đã có. Nếu có, hard refresh trang (`Ctrl + F5`).

### ❌ Không nhớ username, không tìm được repo

Vào **https://github.com/** → bấm avatar góc trên bên phải → "**Your profile**" → tab "**Repositories**" để thấy danh sách.

### ❌ Website hiện nhưng chữ tiếng Việt bị lỗi font

**Khắc phục:** Đảm bảo đường truyền internet ổn định (font load từ Google Fonts). Hard refresh (`Ctrl + F5`).

---

## 🎉 Hoàn thành

Sau khi xong toàn bộ các bước, bạn đã có:

- ✅ Một website portfolio chuyên nghiệp ở URL `https://USERNAME.github.io/`
- ✅ Có thể chia sẻ link này trên CV, LinkedIn, email, namecard.
- ✅ Update không tốn phí, không giới hạn lượt truy cập.
- ✅ HTTPS tự động (URL có ổ khoá xanh, an toàn).

**Mẹo nhỏ cuối cùng:**
- Pin URL portfolio vào bookmark trình duyệt để mỗi lần cần share là copy nhanh.
- Sau khi deploy, mở website trên điện thoại để check responsive (cần đảm bảo hiển thị tốt vì nhà tuyển dụng hay xem trên điện thoại).
- Lần đầu chạy có thể mất 1–2 phút để load font — bình thường, các lần sau sẽ nhanh hơn vì cache.

Chúc may mắn với hành trình tìm việc! 🚀

---

*Tài liệu này được viết riêng cho portfolio của Nguyễn Ngọc Thanh Hằng. Có gì thắc mắc, cứ giữ lại và tham khảo lại bất cứ lúc nào.*
