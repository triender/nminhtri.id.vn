---
id: "wcag-va-cac-tieu-chuan-tiep-can-ky-thuat-so"
title: "WCAG và các tiêu chuẩn tiếp cận kỹ thuật số: Lịch sử phát triển, nguyên tắc POUR và hướng dẫn kiểm toán"
summary: "Tổng hợp lịch sử tiếp cận web từ 1990 đến WCAG 2.2, ma trận đối chiếu Section 508, EN 301 549, Thông tư 22/2023/TT-BTTTT, bảng tra cứu định lượng, khối trực quan và quy trình kiểm toán."
date: "2026-09-03"
category: "standards"
readTime: "12 phút đọc"
badge: "Tiêu chuẩn kỹ thuật"
tags: ["Accessibility", "WCAG", "a11y", "Section 508", "UI/UX", "Web Standards"]
---

## 1. Lịch sử phát triển và triết lý Tim Berners-Lee

Khả năng tiếp cận web (*web accessibility - a11y*) đảm bảo mọi người dùng, bao gồm người khuyết tật, đều có thể tiếp nhận, hiểu, điều hướng và tương tác với trang web.

> [!NOTE]
> *"The power of the Web is in its universality. Access by everyone regardless of disability is an essential aspect."*  
> *(Tạm dịch: "Sức mạnh của Web nằm ở tính phổ quát của nó. Mọi người đều có thể tiếp cận bất kể tình trạng khuyết tật là một khía cạnh thiết yếu.")*  
> — **Sir Tim Berners-Lee**, Nhà phát minh World Wide Web & Giám đốc W3C.

---

### 1.1. Dòng thời gian phát triển của các thế hệ WCAG

<div class="a11y-timeline">
  <div class="timeline-item">
    <div class="timeline-marker">1990s</div>
    <div class="timeline-content">
      <h4>Giai đoạn Web sơ khai</h4>
      <p>Sự xuất hiện của bảng layout, ảnh động, thẻ <code>&lt;marquee&gt;</code>, <code>&lt;blink&gt;</code> và Flash gây mất khả năng tiếp cận đối với người dùng bàn phím và trình đọc màn hình.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">1997</div>
    <div class="timeline-content">
      <h4>Thành lập Sáng kiến Tiếp cận Web (WAI)</h4>
      <p>W3C thành lập <em>Web Accessibility Initiative</em> nhằm xây dựng các hướng dẫn kỹ thuật tiếp cận thống nhất trên toàn cầu.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">1999</div>
    <div class="timeline-content">
      <h4>WCAG 1.0</h4>
      <p>Ban hành 14 hướng dẫn căn bản, tập trung vào khả năng tương thích với trình duyệt văn bản dòng lệnh (<em>Lynx</em>) và chuẩn HTML tĩnh.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">2008</div>
    <div class="timeline-content">
      <h4>WCAG 2.0: Định hình 4 nguyên tắc POUR</h4>
      <p>Chuyển từ kiểm tra thẻ HTML sang 4 nguyên tắc <strong>POUR</strong> (<em>perceivable, operable, understandable, robust</em>) và 3 cấp độ $A, AA, AAA$. Được công nhận là <strong>ISO/IEC 40500:2012</strong>.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">2018</div>
    <div class="timeline-content">
      <h4>WCAG 2.1: Mở rộng cho thiết bị di động</h4>
      <p>Bổ sung 17 tiêu chí thành công (success criteria). Các tiêu chí này được định khung rộng hơn nhằm tập trung cải thiện trải nghiệm tiếp cận cho 3 nhóm đối tượng mục tiêu lớn:</p>
      <ul>
        <li>Người dùng thiết bị di động (mobile accessibility).</li>
        <li>Người có thị lực kém (low vision).</li>
        <li>Người có khuyết tật về nhận thức và khả năng học tập (cognitive and learning disabilities).</li>
      </ul>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">2023</div>
    <div class="timeline-content">
      <h4>WCAG 2.2: Tối ưu tiêu điểm, xác thực và bãi bỏ tiêu chí parsing</h4>
      <p>Bổ sung 9 tiêu chí mới: Tiêu điểm không bị che khuất (<em>focus not obscured</em>), vùng chạm tối thiểu $24 \times 24\text{px}$ (<em>target size - minimum</em>), xác thực dễ tiếp cận (<em>accessible authentication</em>). Đồng thời <strong>chính thức bãi bỏ tiêu chí 4.1.1 (parsing)</strong> do trình duyệt hiện đại đã tự động xử lý lỗi phân tích cú pháp DOM đồng nhất.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-marker">Tương lai</div>
    <div class="timeline-content">
      <h4>WCAG 3.0 (project Silver)</h4>
      <p>Nghiên cứu chuyển đổi từ cơ chế Đạt/Không đạt sang mô hình thang điểm tích lũy.</p>
    </div>
  </div>
</div>

---

## 2. Bảng tra cứu nhanh và ma trận tiêu chuẩn tiếp cận tương đương

### 2.1. Ma trận đối chiếu các bộ tiêu chuẩn tiếp cận toàn cầu và khu vực

| Bộ tiêu chuẩn | Phạm vi áp dụng | Cơ sở pháp lý & Kỹ thuật | Trọng tâm cốt lõi |
| :--- | :--- | :--- | :--- |
| **W3C WCAG 2.2** | Toàn cầu (Tiêu chuẩn công nghệ Web) | Khuyến nghị chính thức của W3C (2023) | Chuẩn mực tham chiếu kỹ thuật tự nguyện (technical standard); đóng vai trò cơ sở nền tảng để các quốc gia và vùng lãnh thổ tích hợp vào luật định. |
| **US Section 508** | Hoa Kỳ (Chính phủ Liên bang & Nhà thầu cung ứng) | Rehabilitation Act of 1973 (29 U.S.C. 794d, cập nhật 2017) | Bắt buộc các cơ quan liên bang phải đảm bảo CNTT-TT (ICT) do họ phát triển, mua sắm, duy trì hoặc sử dụng có khả năng tiếp cận (tham chiếu WCAG 2.0 Level AA). Có các ngoại lệ luật định nghiêm ngặt: hệ thống an ninh quốc gia, hạ tầng phụ trợ (*back-office*), tài liệu nội bộ không công bố rộng rãi, di sản CNTT cũ (*legacy ICT*) và gánh nặng quá mức (*undue burden*). |
| **ADA Title II / III** | Hoa Kỳ (Cơ quan địa phương & Doanh nghiệp) | Americans with Disabilities Act (1990) & DOJ Final Rule (04/2024) | Quy tắc của Bộ Tư pháp Hoa Kỳ (DOJ, 04/2024) ấn định bắt buộc chính quyền tiểu bang/địa phương tuân thủ WCAG 2.1 Level AA (thời hạn 2026–2027). Án lệ tư pháp áp dụng Title III coi website thương mại là nơi công cộng (*public accommodation*). |
| **EN 301 549 & EAA** | Liên minh Châu Âu (EU) | Directive (EU) 2019/882 (EAA) & Harmonised Standard ETSI EN 301 549 | **ETSI EN 301 549** là tiêu chuẩn kỹ thuật hài hòa (tham chiếu WCAG 2.1 Level AA). **EAA (Chỉ thị 2019/882)** là văn bản luật áp đặt nghĩa vụ pháp lý bắt buộc từ ngày 28/06/2025 đối với một số sản phẩm và dịch vụ tư nhân/thương mại trọng yếu (máy ATM, ngân hàng, thương mại điện tử, vé số) và sử dụng EN 301 549 làm chuẩn mực chứng minh tuân thủ. |
| **Thông tư 22/2023/TT-BTTTT & Nghị định 224/2026/NĐ-CP** | Việt Nam (Cơ quan nhà nước) | Bắt buộc tối thiểu WCAG 2.0 | Căn cứ Điều 43 Luật Người khuyết tật 2010; Phụ lục II Thông tư 22/2023/TT-BTTTT bắt buộc áp dụng tiêu chuẩn WCAG tối thiểu phiên bản 2.0; chuyển đổi khung thể chế sang Nghị định 224/2026/NĐ-CP (Luật Chuyển đổi số) thay thế Nghị định 42/2022/NĐ-CP. |

> [!NOTE]
> **Khung pháp lý tiếp cận số tại Việt Nam:**
>
> - **Căn cứ luật định:** Điều 43 Luật Người khuyết tật số 51/2010/QH12 quy định bắt buộc trang thông tin điện tử của cơ quan nhà nước phải được xây dựng để người khuyết tật tiếp cận được.
> - **Tiêu chuẩn kỹ thuật thực thi:** Thông tư số 22/2023/TT-BTTTT của Bộ Thông tin và Truyền thông (hiệu lực từ 05/04/2024, bãi bỏ các điều khoản tiếp cận cũ tại Thông tư 32/2017/TT-BTTTT) ấn định tiêu chuẩn kỹ thuật bắt buộc áp dụng WCAG tối thiểu phiên bản 2.0 cho cổng và trang thông tin điện tử.
> - **Khung chuyển đổi số hiện hành:** Nghị định số 224/2026/NĐ-CP (hiệu lực từ 01/07/2026) hướng dẫn Luật Chuyển đổi số, chính thức thay thế Nghị định 42/2022/NĐ-CP; kết hợp cùng Văn bản hợp nhất số 6050/2026/VBHN-NĐ-BTP mở rộng chuẩn tiếp cận cho thiết bị ki-ốt thông minh tự phục vụ công cộng.

---

### 2.2. Bảng phân cấp 3 mức độ tuân thủ (A, AA, AAA)

- **Level A (Cơ bản - Bắt buộc tối thiểu):** Loại bỏ các rào cản gây cản trở nghiêm trọng cho người khuyết tật khi tiếp cận nội dung web (ví dụ: cung cấp văn bản thay thế `alt` cho ảnh, không bẫy phím).
- **Level AA (Chuẩn mực công nghiệp toàn cầu):** Là ngưỡng mục tiêu phổ biến nhất được các chính phủ và tổ chức lựa chọn khi xây dựng luật pháp tiếp cận kỹ thuật số. Tuy nhiên, bản thân WCAG là một tài liệu hướng dẫn kỹ thuật tự nguyện của W3C, hoàn toàn không tự ban hành nghĩa vụ pháp lý bắt buộc mọi website doanh nghiệp trên thế giới phải tuân thủ. Nghĩa vụ pháp lý thực tế có bắt buộc đạt Level AA hay không phụ thuộc hoàn toàn vào tài phán (*jurisdiction*) của từng quốc gia, loại hình tổ chức (nhà nước hay tư nhân), và các đạo luật cụ thể được áp dụng tại thị trường hoạt động.
- **Level AAA (Mức độ tiếp cận tối đa):** Dành cho các hệ thống chuyên biệt, không bắt buộc áp dụng toàn diện trên mọi trang.

---

### 2.3. Bảng chỉ số định lượng cốt lõi nên nhớ

| Tiêu chí kỹ thuật | Mức Level AA (Tiêu chuẩn) | Mức Level AAA (Nâng cao) | Ghi chú thực thi |
| :--- | :--- | :--- | :--- |
| **Độ tương phản chữ thường** | Tối thiểu $\ge 4.5:1$ (WCAG 1.4.3) | Tối thiểu $\ge 7.0:1$ (WCAG 1.4.6) | Dưới $18\text{pt}$ ($24\text{px}$) hoặc dưới $14\text{pt}$ bold ($18.66\text{px}$). |
| **Độ tương phản chữ lớn** | Tối thiểu $\ge 3.0:1$ (WCAG 1.4.3) | Tối thiểu $\ge 4.5:1$ (WCAG 1.4.6) | Từ $18\text{pt}$ ($24\text{px}$) hoặc $14\text{pt}$ bold ($18.66\text{px}$) trở lên. |
| **Độ tương phản phi văn bản** | Tối thiểu $\ge 3.0:1$ (WCAG 1.4.11) | Tương phản tăng cường (khuyến nghị) | Áp dụng cho thành phần giao diện (viền ô nhập, checkbox, radio, focus tùy biến) và đối tượng đồ họa mang thông tin (biểu đồ, icon cảnh báo). |
| **Vùng chạm ngón tay (target size)** | Tối thiểu $24 \times 24\text{px}$ CSS (WCAG 2.5.8) | Tối thiểu $44 \times 44\text{px}$ CSS (WCAG 2.5.5) | Mức AA (2.5.8) là chuẩn sàn WCAG 2.2 (kèm ngoại lệ liên kết trong dòng và vòng tròn khoảng đệm đường kính 24px không giao nhau). Tiêu chí 2.5.5 (Level AAA) quy định $44\text{px}$ CSS; độc lập với khuyến nghị $44 \times 44\text{pt}$ của Apple HIG. |
| **Đường viền tiêu điểm focus** | Nhìn thấy rõ ràng (WCAG 2.4.7) | Độ dày $\ge 2\text{px}$, tương phản $\ge 3:1$ (WCAG 2.4.13) | Mức AA (2.4.7) yêu cầu mắt thường nhìn thấy được. Tiêu chí 2.4.13 (Level AAA) quy định diện tích viền $\ge 2\text{px}$ và tương phản $\ge 3:1$ với trạng thái chưa focus. |
| **Tiêu điểm không bị che khuất** | Không bị che khuất hoàn toàn (WCAG 2.4.11) | Không bị che khuất bất kỳ phần nào (WCAG 2.4.12) | Tiêu chuẩn mới WCAG 2.2: Ngăn thanh header/footer cố định (*sticky*) hoặc popup che khuất thành phần đang nhận tiêu điểm phím Tab. |
| **Thu phóng không vỡ (reflow)** | Không cuộn 2 chiều tại $320\text{px}$ CSS (WCAG 1.4.10) | Hỗ trợ reflow toàn diện | Chuẩn mực gốc quy định tại chiều rộng $320\text{px}$ CSS (cuộn dọc) hoặc chiều cao $256\text{px}$ CSS (cuộn ngang). Zoom 400% tại màn hình $1280\text{px}$ là kịch bản quy đổi thực tế. |

---

## 3. Cơ chế tầng sâu: 4 nguyên tắc nền tảng POUR

Mọi tiêu chí trong WCAG đều phân bổ vào 4 nguyên tắc **POUR**:

```
[POUR Architecture]
 ├── 1. P - Perceivable   (Dễ cảm nhận: Trình bày thông tin qua các giác quan)
 ├── 2. O - Operable      (Có thể thao tác: Điều khiển qua bàn phím và con trỏ)
 ├── 3. U - Understandable(Dễ hiểu: Giao diện rõ ràng, nhất quán, dự đoán được)
 └── 4. R - Robust        (Tương thích tốt: Phân tích chính xác bởi công nghệ trợ năng)
```

---

### 3.1. Dễ cảm nhận (perceivable)

- **Văn bản thay thế (1.1.1 non-text content):** Mọi hình ảnh mang thông tin phải có thuộc tính `alt="Nội dung mô tả"`. Ảnh trang trí thuần túy bắt buộc đặt `alt=""` hoặc `aria-hidden="true"`.
- **Không dùng màu sắc làm tín hiệu duy nhất (1.4.1 use of color):** Không chỉ dùng màu đỏ để báo lỗi form; phải kết hợp icon cảnh báo hoặc thông báo văn bản.
- **Độ tương phản màu sắc chữ viết (1.4.3 contrast minimum):** Tỷ lệ tương phản tính toán dựa trên độ sáng tương đối $L_1$ và $L_2$:
  $$\text{Contrast Ratio} = \frac{L_1 + 0.05}{L_2 + 0.05}$$
  Trong đó $L_1$ là độ sáng tương đối (relative luminance) của màu sáng hơn, $L_2$ là độ sáng tương đối của màu tối hơn ($0 \le L_2 \le L_1 \le 1$). Ràng buộc $L_1 \ge L_2$ đảm bảo tỷ lệ tương phản luôn nằm trong dải giá trị chuẩn từ $1:1$ (hai màu hoàn toàn trùng nhau) đến $21:1$ (tương phản cực đại giữa đen tuyền `#000000` và trắng tinh `#ffffff`).
- **Độ tương phản phi văn bản (1.4.11 non-text contrast - Level AA):** Yêu cầu tỷ lệ tương phản tối thiểu $\ge 3:1$ với màu nền liền kề, áp dụng cụ thể cho hai nhóm đối tượng:
  1. *Thành phần giao diện người dùng (user interface components):* Trạng thái trực quan của các thành phần điều khiển như viền ô nhập liệu (`input border`), nút kiểm (`checkbox`), nút chọn (`radio button`), hoặc chỉ báo trạng thái tiêu điểm/di chuột tùy biến (`focus/hover states`).
  2. *Đối tượng đồ họa mang thông tin (graphical objects):* Các phần đồ họa cần thiết để hiểu nội dung (như các thanh/lát cắt trong biểu đồ, icon cảnh báo độc lập mang ngữ nghĩa); không áp dụng cho ảnh trang trí thuần túy.

---

### 3.2. Có thể thao tác (operable)

- **Tiếp cận toàn diện bằng bàn phím (2.1.1 keyboard):** Mọi thao tác mở menu, nhấn nút, chuyển tab, điền form đều phải thực hiện được qua phím `Tab`, `Shift+Tab`, `Enter`, `Space` và các phím mũi tên.
- **Nhận diện tiêu điểm trực quan (2.4.7 focus visible & 2.4.13 focus appearance):** Phần tử tương tác khi nhận tiêu điểm bàn phím phải có chỉ báo nhìn thấy được bằng mắt thường (Level AA - 2.4.7). Ở cấp độ nâng cao Level AAA (2.4.13 focus appearance), chỉ báo phải có diện tích tối thiểu tương đương đường viền dày $2\text{px}$ bao quanh và độ tương phản $\ge 3:1$ với nền liền kề cũng như trạng thái chưa focus (hoặc được đánh giá gián tiếp qua 1.4.11 non-text contrast Level AA khi tự tạo custom focus indicator).
- **Tiêu điểm không bị che khuất (2.4.11 focus not obscured - minimum & 2.4.12 focus not obscured - enhanced):** Tiêu chuẩn mới trong WCAG 2.2: Khi người dùng Tab vào một liên kết hoặc nút bấm, phần tử đó không được phép bị che khuất hoàn toàn (Level AA - 2.4.11) hoặc không bị che khuất bất kỳ phần nào (Level AAA - 2.4.12) bởi các thành phần cố định trên màn hình như thanh điều hướng cố định (sticky header), chân trang (footer) hoặc tiện ích trò chuyện (chatbot widget).

---

### 3.3. Dễ hiểu (understandable)

- **Khai báo ngôn ngữ trang (3.1.1 language of page):** Luôn khai báo `<html lang="vi">` hoặc `<html lang="en">` ở đầu trang để trình đọc màn hình nạp đúng bộ phát âm bản ngữ.
- **Dự đoán được hành vi (3.2.1 on focus & 3.2.2 on input):** Không tự động chuyển trang, bật popup hay submit form khi người dùng mới chỉ di chuyển con trỏ vào ô nhập.
- **Hỗ trợ xử lý lỗi (3.3.1 error identification & 3.3.2 labels or instructions):** Chỉ rõ vị trí ô lỗi và hướng dẫn cách khắc phục cụ thể.

---

### 3.4. Tương thích tốt (robust)

- **Sử dụng HTML5 chuẩn ngữ nghĩa (semantic HTML):** Sử dụng đúng thẻ `<button>`, `<nav>`, `<main>`, `<article>` thay vì dựng giao diện bằng các thẻ `<div>` lồng nhau.
- **Giao tiếp qua WAI-ARIA khi tạo thành phần tùy biến (custom component):** Khai báo đúng thuộc tính `role`, `aria-expanded`, `aria-controls`, `aria-live` khi tạo các component phức tạp như accordion, tablist hay toast.
- **Bãi bỏ tiêu chí 4.1.1 (parsing) trong WCAG 2.2:** Tiêu chí 4.1.1 parsing (vốn kiểm tra các lỗi cú pháp HTML như thẻ chưa đóng, trùng lặp thuộc tính) đã chính thức bị W3C bãi bỏ (*obsolete*) trong bản WCAG 2.2. Nguyên nhân là do đặc tả HTML5 và các công cụ kết xuất hiện đại đã chuẩn hóa thuật toán tự khắc phục lỗi cú pháp DOM (*error recovery*), loại bỏ nguy cơ gây mất tiếp cận cho phần mềm trợ năng.

---

## 4. Khối trực quan đối chiếu thực tế và bài học mã nguồn

Các khối trực quan dưới đây đối chiếu giữa cách hiện thực chưa đạt chuẩn và cách triển khai đạt chuẩn:

---

### 4.1. Đối chiếu trực quan: Độ tương phản màu sắc văn bản (color contrast)

<div class="a11y-compare-grid">
  <div class="a11y-card fail">
    <div class="a11y-card-header">Chưa đạt chuẩn: Độ tương phản thấp</div>
    <div class="a11y-preview-box" style="background-color: #ffffff;">
      <span style="color: #94a3b8; font-size: 0.95rem; font-weight: 500;">Chữ xám nhạt trên nền trắng</span>
      <span class="a11y-ratio-tag">Tỷ lệ tương phản: 2.1:1 &lt; 4.5:1</span>
    </div>
    <p class="a11y-explanation">Màu xám <code>#94a3b8</code> có tỷ lệ tương phản 2.1:1, không đạt ngưỡng tối thiểu (4.5:1), gây khó đọc cho người suy giảm thị lực.</p>
  </div>

  <div class="a11y-card pass">
    <div class="a11y-card-header">Đạt chuẩn: Tương phản cao (WCAG AAA)</div>
    <div class="a11y-preview-box" style="background-color: #ffffff;">
      <span style="color: #334155; font-size: 0.95rem; font-weight: 600;">Chữ xám đậm trên nền trắng</span>
      <span class="a11y-ratio-tag">Tỷ lệ tương phản: 7.4:1 &ge; 7.0:1</span>
    </div>
    <p class="a11y-explanation">Màu <code>#334155</code> đem lại độ tương phản 7.4:1, bảo đảm độ rõ nét trên mọi màn hình và điều kiện ánh sáng.</p>
  </div>
</div>

---

### 4.2. Đối chiếu trực quan: Chỉ báo tiêu điểm bàn phím (focus ring indicator)

<div class="a11y-compare-grid">
  <div class="a11y-card fail">
    <div class="a11y-card-header">Chưa đạt chuẩn: Xóa bỏ outline</div>
    <div class="a11y-preview-box">
      <button type="button" style="padding: 0.5rem 1rem; border-radius: 6px; border: 1px solid #cbd5e1; background: #f8fafc; color: #0f172a; outline: none; cursor: pointer;">Nút bấm bị ẩn viền focus</button>
    </div>
    <p class="a11y-explanation">Sử dụng <code>button:focus { outline: none; }</code> làm mất đường viền chỉ báo, khiến người dùng bàn phím không xác định được phần tử đang nhận tiêu điểm.</p>
  </div>

  <div class="a11y-card pass">
    <div class="a11y-card-header">Đạt chuẩn: Focus ring rõ ràng (WCAG 2.4.7)</div>
    <div class="a11y-preview-box">
      <button type="button" style="padding: 0.5rem 1rem; border-radius: 6px; border: 1px solid #2563eb; background: #eff6ff; color: #1d4ed8; outline: 2px solid #2563eb; outline-offset: 2px; cursor: pointer;">Nút bấm có viền focus rõ ràng</button>
    </div>
    <p class="a11y-explanation">Áp dụng <code>:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }</code> giúp người dùng nhận diện ngay phần tử đang chọn khi nhấn phím Tab.</p>
  </div>
</div>

---

### 4.3. Đối chiếu trực quan: Vùng chạm ngón tay (touch target size)

<div class="a11y-compare-grid">
  <div class="a11y-card fail">
    <div class="a11y-card-header">Chưa đạt chuẩn: Kích thước quá nhỏ</div>
    <div class="a11y-preview-box" style="flex-direction: row; gap: 0.25rem;">
      <button type="button" style="width: 18px; height: 18px; padding: 0; font-size: 10px; background: #fee2e2; border: 1px solid #ef4444; color: #b91c1c;">✕</button>
      <button type="button" style="width: 18px; height: 18px; padding: 0; font-size: 10px; background: #e0e7ff; border: 1px solid #6366f1; color: #4338ca;">✎</button>
    </div>
    <p class="a11y-explanation">Kích thước $18 \times 18\text{px}$ đặt sát nhau dễ gây thao tác bấm nhầm trên màn hình cảm ứng.</p>
  </div>

  <div class="a11y-card pass">
    <div class="a11y-card-header">Đạt chuẩn: Vùng chạm tối thiểu $24\text{px}$ (Level AA) và nâng cao $44\text{px}$ (Level AAA)</div>
    <div class="a11y-preview-box" style="flex-direction: row; gap: 0.75rem;">
      <button type="button" style="min-width: 44px; min-height: 44px; display: inline-flex; align-items: center; justify-content: center; border-radius: 8px; background: #fee2e2; border: 1px solid #ef4444; color: #b91c1c; cursor: pointer;">✕</button>
      <button type="button" style="min-width: 44px; min-height: 44px; display: inline-flex; align-items: center; justify-content: center; border-radius: 8px; background: #e0e7ff; border: 1px solid #6366f1; color: #4338ca; cursor: pointer;">✎</button>
    </div>
    <p class="a11y-explanation">Tiêu chí <strong>2.5.8 (Level AA)</strong> quy định diện tích tối thiểu là $24 \times 24\text{px}$ CSS. <em>Lưu ý về ngoại lệ kỹ thuật:</em> W3C quy định 2 trường hợp miễn trừ quan trọng: (1) <strong>Ngoại lệ liên kết trong dòng (inline):</strong> Các thẻ liên kết nằm trong dòng văn bản không bắt buộc đạt $24\text{px}$; (2) <strong>Ngoại lệ khoảng đệm (spacing):</strong> Các nút nhỏ hơn $24\text{px}$ (ví dụ $18 \times 18\text{px}$) vẫn đạt chuẩn nếu khoảng cách tâm tới phần tử lân cận đủ tạo một vòng tròn bảo vệ đường kính $24\text{px}$ không giao nhau. Để đạt chuẩn nâng cao <strong>Level AAA (tiêu chí 2.5.5 target size - enhanced)</strong>, diện tích vùng chạm tối thiểu là $44 \times 44\text{px}$ CSS. Độc lập với chuẩn W3C, tài liệu hướng dẫn thiết kế <strong>Apple Human Interface Guidelines (Accessibility)</strong> cũng đưa ra khuyến nghị vùng bấm công thái học tối thiểu $44 \times 44\text{pt}$ (points) cho các ứng dụng trên hệ điều hành iOS.</p>
  </div>
</div>

---

### 4.4. Đối chiếu mã nguồn: Nút bấm ngữ nghĩa (semantic button) so với thẻ div lồng

<div class="a11y-compare-grid">
  <div class="a11y-card fail">
    <div class="a11y-card-header">Chưa đạt chuẩn: Thẻ div gắn onclick</div>
    <div class="a11y-code-box">
      <pre><code>&lt;div class="btn" onclick="submit()"&gt;
  Gửi bình luận
&lt;/div&gt;</code></pre>
    </div>
    <p class="a11y-explanation">Không nhận phím Tab, không thể kích hoạt bằng phím Enter hoặc Space, và trình đọc màn hình không nhận diện là nút bấm.</p>
  </div>

  <div class="a11y-card pass">
    <div class="a11y-card-header">Đạt chuẩn: Thẻ button ngữ nghĩa</div>
    <div class="a11y-code-box">
      <pre><code>&lt;button type="submit" class="btn"&gt;
  Gửi bình luận
&lt;/button&gt;</code></pre>
    </div>
    <p class="a11y-explanation">Tự động hỗ trợ điều hướng bàn phím toàn diện và khai báo đúng vai trò <code>button</code> cho công nghệ trợ năng.</p>
  </div>
</div>

---

### 4.5. Đối chiếu mã nguồn: Biểu mẫu (form) và thông báo lỗi tiếp cận

<div class="a11y-compare-grid">
  <div class="a11y-card fail">
    <div class="a11y-card-header">Chưa đạt chuẩn: Placeholder thay thế Label</div>
    <div class="a11y-code-box">
      <pre><code>&lt;input type="email"
  placeholder="Nhập email..."
  class="input-error"&gt;</code></pre>
    </div>
    <p class="a11y-explanation">Placeholder biến mất khi nhập liệu, không liên kết ngữ nghĩa với thông báo lỗi khi biểu mẫu không hợp lệ.</p>
  </div>

  <div class="a11y-card pass">
    <div class="a11y-card-header">Đạt chuẩn: Ràng buộc nhãn (label) và cảnh báo ARIA</div>
    <div class="a11y-code-box">
      <pre><code>&lt;label for="email"&gt;Email&lt;/label&gt;
&lt;input id="email" type="email"
  aria-describedby="email-err"
  aria-invalid="true" required&gt;
&lt;p id="email-err" role="alert"&gt;
  Email không hợp lệ.
&lt;/p&gt;</code></pre>
    </div>
    <p class="a11y-explanation">Trình đọc màn hình đọc rõ tên nhãn và tự động phát âm thông báo lỗi khi dữ liệu sai định dạng. <em>Lưu ý kỹ thuật:</em> Không render tĩnh phần tử <code>role="alert"</code> rỗng ngay từ đầu trên HTML khi tải trang (SSR) để tránh trình đọc màn hình thông báo lỗi giả; hãy cập nhật nội dung động khi có lỗi. Ngoài ra, dù WCAG 2.1 đã chuẩn hóa thuộc tính <code>aria-errormessage</code>, các kỹ sư kiểm toán vẫn ưu tiên dùng hoặc kết hợp <code>aria-describedby</code> để duy trì khả năng tương thích ngược với các trình đọc màn hình cũ.</p>
  </div>
</div>

---

## 5. Quy trình kiểm toán tiếp cận và tài liệu tham khảo

### 5.1. Khung quy trình kiểm toán tiếp cận 4 tầng toàn diện (a11y audit framework)

Một quy trình kiểm toán tiếp cận toàn diện kết hợp giữa công cụ quét mã tự động với kiểm thử điều hướng và trải nghiệm thực tế trên công nghệ trợ năng:

#### Tầng 1: Kiểm thử quét tự động (automated scanning)

- Quét nhanh bằng các công cụ phân tích cấu trúc DOM chuẩn công nghiệp: **Axe DevTools**, **Google Lighthouse**, **WAVE Evaluation Tool**.

> [!WARNING]
> **Giới hạn kỹ thuật của công cụ tự động:** Các công cụ quét tự động chỉ có thể phát hiện tối đa **$30\% - 40\%$** tổng số lỗi tiếp cận. Những rào cản cốt lõi như ý nghĩa ngữ cảnh của văn bản thay thế `alt`, thứ tự đọc logic của nội dung, hay bẫy tiêu điểm bàn phím trong các luồng tương tác phức tạp bắt buộc phải được đánh giá qua kiểm thử thủ công (manual audit).

#### Tầng 2: Kiểm thử điều hướng bàn phím thuần (manual keyboard navigation)

- Ngắt kết nối chuột, chỉ sử dụng bàn phím thực hiện tuần tự mọi tác vụ của người dùng:
  - Phím `Tab` / `Shift+Tab`: Kiểm tra thứ tự chuyển tiêu điểm có logic tự nhiên (tuân thủ luồng DOM tree), không bị nhảy cóc hay mất dấu.
  - Phím `Enter` / `Space`: Kích hoạt nút bấm, chuyển tab, mở accordion, chọn checkbox và submit form.
  - Phím `Esc`: Đóng ngay lập tức các hộp thoại modal, menu thả xuống (dropdown menu) và tự động trả tiêu điểm về đúng nút kích hoạt ban đầu.
  - Phím mũi tên: Điều hướng bên trong các khối phức tạp (`radiogroup`, `tablist`, `combobox`).
  - Kiểm tra chỉ báo tiêu điểm (focus indicator): Luôn hiển thị rõ nét trên mọi thành phần tương tác.

#### Tầng 3: Ma trận kiểm thử thực tế trên trình đọc màn hình (screen reader testing matrix)

- Kiểm thử trang web trên các tổ hợp Trình đọc màn hình và Trình duyệt phổ biến nhất thế giới:
  - **Windows:** **NVDA** (nonvisual desktop access - chuẩn mã nguồn mở phổ biến nhất) và **JAWS** trên Google Chrome / Mozilla Firefox / Microsoft Edge.
  - **macOS & iOS:** **VoiceOver** tích hợp sẵn trên Apple Safari.
  - **Android:** **TalkBack** tích hợp sẵn trên Google Chrome.
- Nội dung rà soát bắt buộc: Danh mục điểm neo cấu trúc (landmarks), phân cấp tiêu đề (`h1` đến `h6`), bảng dữ liệu (`table`, `th`, `td` có thuộc tính `scope`), nhãn nút bấm hành động (`aria-label`) và các thông báo cập nhật động qua vùng phát tín hiệu `aria-live="polite"`.

#### Tầng 4: Kiểm thử thu phóng và tái sắp xếp bố cục (reflow & zoom testing)

- Thu phóng không vỡ bố cục (Reflow - Tiêu chí 1.4.10, Level AA): Nội dung phải được trình bày mượt mà, không bị mất thông tin hoặc chức năng và không bắt buộc người dùng phải cuộn theo hai chiều (2D scrolling) đối với:

  1. Nội dung cuộn theo chiều dọc ở chiều rộng tương đương 320 CSS pixels

  2. Nội dung cuộn theo chiều ngang ở chiều cao tương đương 256 CSS pixels

> [!WARNING]
> Mức thu phóng 400% trên màn hình máy tính để bàn tiêu chuẩn có độ phân giải 1280 CSS pixels chỉ là kịch bản kiểm thử quy đổi thực tế phổ biến để đạt được không gian hiển thị tương đương 320 CSS pixels ($1280 / 4 = 320$) chứ không phải là đơn vị chuẩn mực duy nhất của tiêu chuẩn
---

### 5.2. Các hệ thống thiết kế và trang web kiểu mẫu tham khảo

- **[GOV.UK Design System](https://design-system.service.gov.uk/) (Anh):** Tiêu chuẩn thiết kế giao diện dịch vụ công tối giản, tương thích cao và đạt chuẩn tiếp cận nghiêm ngặt.
- **[U.S. Web Design System (USWDS)](https://designsystem.digital.gov/) (Mỹ):** Bộ linh kiện UI đáp ứng chuẩn Section 508 cho các cơ quan chính phủ liên bang.
- **[W3C Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/):** Cẩm nang hướng dẫn và ví dụ mã nguồn chính thức từ tổ chức sáng lập WCAG.
- **[W3C Web Accessibility Initiative - Laws and Policies](https://www.w3.org/WAI/policies/):** Báo cáo tổng hợp danh mục chính sách và khung pháp lý tiếp cận kỹ thuật số tại các quốc gia trên thế giới.
- **[Apple Human Interface Guidelines - Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility):** Tài liệu hướng dẫn thiết kế công thái học độc lập của Apple, khuyến nghị vùng chạm tối thiểu $44 \times 44\text{pt}$ cho thiết bị di động.

---

### 5.3. Danh mục tiêu chuẩn kỹ thuật và khung pháp lý

- **W3C Recommendation:** *Web Content Accessibility Guidelines (WCAG) 2.2* (W3C Recommendation, 05/10/2023) — Đặc tả kỹ thuật chính thức cho các tiêu chí tiếp cận web.
- **W3C WAI Supporting Documents:** *Understanding WCAG 2.2* (Hướng dẫn giải thích kỹ thuật chuyên sâu cho các tiêu chí: 1.4.10 Reflow, 1.4.11 Non-text Contrast, 2.5.5 Target Size Enhanced, 2.5.8 Target Size Minimum) và *What's New in WCAG 2.1* (Định khung 17 Success Criteria mở rộng cho Mobile, Low Vision, Cognitive Disabilities).
- **W3C Web Accessibility Initiative (WAI):** *Web Accessibility Laws and Policies* (Tổng hợp các đạo luật và chính sách tiếp cận trên phạm vi toàn cầu).
- **United States Access Board:** *Revised Section 508 Standards and Transition Guide* (36 CFR Part 1194, 2017) — Quy định tiếp cận CNTT-TT cho cơ quan liên bang Mỹ và các ngoại lệ luật định.
- **European Parliament and Council:** *Directive (EU) 2019/882 on the accessibility requirements for products and services (European Accessibility Act - EAA)* (Áp đặt nghĩa vụ pháp lý từ 28/06/2025 cho khu vực thương mại).
- **European Standard:** *ETSI EN 301 549 V3.2.1: Accessibility requirements for ICT products and services* (Tiêu chuẩn kỹ thuật hài hòa Châu Âu, tham chiếu WCAG 2.1 Level AA).
- **Apple Developer:** *Human Interface Guidelines - Accessibility (Layout and Target Sizes)* (Khuyến nghị vùng chạm tối thiểu $44 \times 44\text{pt}$ cho nền tảng iOS).
- **Quốc hội Việt Nam:** *Điều 43 Luật Người khuyết tật số 51/2010/QH12* (Quy định bắt buộc trang thông tin điện tử của cơ quan nhà nước phải được xây dựng để người khuyết tật tiếp cận được).
- **Bộ Thông tin và Truyền thông Việt Nam:** *Thông tư số 22/2023/TT-BTTTT quy định cấu trúc, bố cục, yêu cầu kỹ thuật cho cổng thông tin điện tử và trang thông tin điện tử của cơ quan nhà nước* (Có hiệu lực từ 05/04/2024, bắt buộc áp dụng tiêu chuẩn WCAG tối thiểu phiên bản 2.0 tại Phụ lục II; bãi bỏ các điều khoản cũ tại Thông tư 32/2017/TT-BTTTT).
- **Chính phủ Việt Nam:** *Nghị định số 224/2026/NĐ-CP quy định chi tiết một số điều và biện pháp thi hành Luật Chuyển đổi số* (Có hiệu lực từ 01/07/2026, thay thế Nghị định 42/2022/NĐ-CP) và *Văn bản hợp nhất số 6050/2026/VBHN-NĐ-BTP* (Bộ Tư pháp xác thực ngày 06/08/2026 về thiết bị ki-ốt thông minh tự phục vụ công cộng).
