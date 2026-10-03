# nminhtri.id.vn — Sổ tay kỹ thuật tra cứu thực chiến

> **Trang web chính thức:** [https://nminhtri.id.vn](https://nminhtri.id.vn)  
> Kho lưu trữ bài viết kỹ thuật, ghi chú kiến trúc hệ thống, giải tích thuật toán và mô hình tư duy của Nguyễn Minh Trí.

---

## 1. Triết lý và định vị bài viết

- **Sổ tay tra cứu thực chiến:** Nơi lưu trữ tri thức ứng dụng, cấu hình chuẩn và mã giả tối ưu phục vụ tra cứu nhanh và nghiên cứu chuyên sâu.
- **Tiêu chuẩn học thuật và hình thức:** Mọi bài viết được cấu trúc 3 tầng chuẩn mực (bảng tra cứu nhanh, cơ chế tầng sâu, triển khai kỹ thuật kèm checklist), trực quan hóa bằng sơ đồ vector SVG và công thức toán học KaTeX.
- **Tính khách quan:** Văn phong kỹ thuật khiêm tốn, đi thẳng vào nguyên lý và chứng minh, không dùng từ ngữ quảng bá hay giật tít.

---

## 2. Mục lục bài viết (Table of contents)

### Bài viết tiếng Việt (`content/vn/posts/`)

1. [Mô hình câu hỏi đảo phủ và hệ quả phản thực](content/vn/posts/mo-hinh-cau-hoi-dao-phu-va-he-qua-phan-thuc.md)
   - *Chuyên mục:* Tư duy phản biện
   - *Nội dung:* Khung phân tích logic phản nghiệm, kiểm chứng giả thuyết và triệt tiêu ngụy biện trong tranh biện kỹ thuật.
2. [Tư duy phản biện — Bóc tách bẫy tiền giả định](content/vn/posts/tu-duy-phan-bien-boc-tach-bay-tien-gia-dinh.md)
   - *Chuyên mục:* Tư duy phản biện
   - *Nội dung:* Phân tích ngôn ngữ học và logic mệnh đề để nhận diện các tiền giả định ngầm định trong giao tiếp kỹ thuật.
3. [Cơ chế ảo hóa và các công nghệ container](content/vn/posts/co-che-ao-hoa-va-cac-cong-nghe-container.md)
   - *Chuyên mục:* Hạ tầng & Công nghệ
   - *Nội dung:* Phân tích tầng sâu kiến trúc KVM, QEMU, Namespaces, Cgroups, OverlayFS và so sánh hiệu năng thực tế.
4. [Định nghĩa thuật toán và phương pháp biểu diễn](content/vn/posts/dinh-nghia-thuat-toan-va-phuong-phap-bieu-dien.md)
   - *Chuyên mục:* Thuật toán & Cấu trúc dữ liệu
   - *Nội dung:* Cơ sở lý thuyết tính toán, mô hình máy Turing và các phương thức biểu diễn hình thức.
5. [Độ phức tạp thuật toán và giải tích](content/vn/posts/do-phuc-tap-thuat-toan-va-giai-tich.md)
   - *Chuyên mục:* Thuật toán & Cấu trúc dữ liệu
   - *Nội dung:* Tiệm cận Big-O, Big-$\Omega$, Big-$\Theta$, định lý thợ (Master theorem) và bài toán $P$ vs $NP$.
6. [WCAG và các tiêu chuẩn tiếp cận kỹ thuật số](content/vn/posts/wcag-va-cac-tieu-chuan-tiep-can-ky-thuat-so.md)
   - *Chuyên mục:* Tiêu chuẩn web & Khả năng tiếp cận
   - *Nội dung:* 4 nguyên tắc POUR, kỹ thuật ARIA, độ tương phản màu sắc và danh mục kiểm tra WCAG 2.2 AA.

### English articles (`content/en/posts/`)

1. [Algorithm definition and representation methods](content/en/posts/algorithm-definition-and-representation-methods.md)
2. [Computational complexity and calculus](content/en/posts/computational-complexity-and-calculus.md)
3. [WCAG and digital accessibility standards](content/en/posts/wcag-and-digital-accessibility-standards.md)

---

## 3. Cấu trúc thư mục kho lưu trữ

```
.
├── content/
│   ├── vn/                      # Bài viết và siêu dữ liệu tiếng Việt
│   │   ├── categories.json      # Danh mục các chuyên đề
│   │   ├── posts.json           # Chỉ mục bài viết và chuỗi liên hoàn
│   │   ├── projects.json        # Danh sách dự án
│   │   ├── site.json            # Thông tin tác giả và website
│   │   └── posts/               # Tệp nguồn Markdown các bài viết
│   └── en/                      # Bài viết và siêu dữ liệu tiếng Anh
│       ├── categories.json
│       ├── posts.json
│       ├── projects.json
│       ├── site.json
│       └── posts/
├── assets/images/posts/         # Sơ đồ vector SVG và đồ thị minh họa
├── LICENSE                      # Giấy phép bản quyền nội dung CC BY 4.0
└── README.md                    # Mục lục và giới thiệu kho lưu trữ
```

---

## 4. Bản quyền và giấy phép (License)

Toàn bộ bài viết, đồ thị và hình ảnh minh họa trong kho lưu trữ này được bảo hộ và phát hành theo giấy phép [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).
