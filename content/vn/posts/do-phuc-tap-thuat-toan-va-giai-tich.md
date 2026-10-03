---
id: "do-phuc-tap-thuat-toan-va-giai-tich"
title: "Độ phức tạp thuật toán: Bảng tra cứu thời gian và tính chất tiệm cận trong giải tích"
summary: "Phân tích tính chất của Big-O qua giới hạn giải tích, bảng ước lượng kích thước dữ liệu N trong lập trình thi đấu, định lý Master và các quy tắc phân tích nhanh."
date: "2026-09-03"
category: "algorithms"
readTime: "8 phút đọc"
badge: "Thuật toán"
tags: ["Thuật toán", "Giải tích", "Big-O", "Hiệu năng", "Toán học"]
---

## 1. Bảng tra cứu nhanh và giới hạn kích thước dữ liệu

### 1.1. Ước lượng năng lực tính toán trong thực tế

Trong lập trình thi đấu và kỹ thuật phần mềm, việc ước lượng thời gian chạy dựa trên độ phức tạp thuật toán là một kỹ năng thực tế rất cần thiết.

Quy tắc ước lượng thô (*rule of thumb*) phổ biến cho rằng một máy tính hiện đại có thể xử lý an toàn khoảng $10^8$ phép toán đơn giản trong thời gian **1 giây** (đối với ngôn ngữ biên dịch như C/C++).

> [!WARNING]
> **Lưu ý về môi trường thực thi:**  
> Mốc $10^8$ phép toán/giây chỉ là một quy tắc kinh nghiệm sơ bộ. Thời gian thực thi thực tế phụ thuộc chặt chẽ vào độ phức tạp của từng phép toán (phép cộng bitwise nhanh hơn rất nhiều so với phép chia hoặc modulo số thực), cấu trúc phân cấp bộ nhớ đệm (cache hit/miss), cơ chế dự đoán rẽ nhánh (*branch prediction*), tối ưu hóa của trình biên dịch và phần cứng. Không thể quy đổi trực tiếp độ phức tạp thuật toán từ chỉ số FLOPS phần cứng.

---

### 1.2. Bảng ước lượng nhanh trong môi trường lập trình thi đấu

Bảng đối chiếu kích thước dữ liệu đầu vào $N$ với độ phức tạp mục tiêu để chương trình chạy an toàn trong giới hạn **1 giây**:

| Kích thước đầu vào N | Ước lượng độ phức tạp mục tiêu | Thuật toán và cấu trúc dữ liệu điển hình |
| :--- | :--- | :--- |
| $N \le 10 - 12$ | $O(N!)$ hoặc $O(N^2 \cdot 2^N)$ | Quay lui hoán vị, duyệt toàn bộ (brute-force), quy hoạch động trạng thái TSP |
| $N \le 20 - 25$ | $O(2^N)$ | Duyệt tập con, quy hoạch động mặt nạ bit (bitmask DP) |
| $N \le 80 - 100$ | $O(N^4)$ | Duyệt 4 vòng lặp lồng nhau, bài toán hình học tổ hợp cơ bản |
| $N \le 300 - 500$ | $O(N^3)$ | Floyd-Warshall (đường đi ngắn nhất mọi cặp đỉnh), nhân ma trận cơ bản |
| $N \le 2.000 - 5.000$ | $O(N^2)$ | Sắp xếp chèn (insertion sort), Dijkstra dạng mảng cơ bản, 2 vòng lặp lồng |
| $N \le 10^5 - 10^6$ | $O(N \log N)$ | Sắp xếp trộn (*merge sort*), sắp xếp nhanh (*quick sort*), cây phân đoạn (*segment tree*), hàng đợi ưu tiên (*heap*) |
| $N \le 10^7 - 10^8$ | $O(N)$ | Kỹ thuật hai con trỏ, sàng nguyên tố Eratosthenes, duyệt mảng tuyến tính |
| $N \le 10^{12} - 10^{14}$ | $O(\sqrt{N})$ | Kiểm tra số nguyên tố và phân tích thừa số bằng thuật toán chia thử (*trial division*) |
| $N \le 10^9 - 10^{18}$ | $O(\log N)$ | Tìm kiếm nhị phân (*binary search*), lũy thừa nhị phân, thuật toán Euclid (GCD) |
| $N$ rất lớn ($N \ge 10^{18}$) | $O(\log N)$ hoặc $O(1)$ tùy cấu trúc bài toán | Công thức toán học đóng, tìm kiếm nhị phân trên miền giá trị, lũy thừa nhị phân modulo |

> [!NOTE]
> **Lưu ý định hướng:** Các mốc trên chỉ mang tính dẫn đường; thời gian thực tế phụ thuộc vào hệ số hằng ẩn (*hidden constant factor*), chi phí cấp phát bộ nhớ, ngôn ngữ lập trình và giới hạn thời gian (*time limit*) của từng hệ thống đánh giá.

---

## 2. Tính chất độ phức tạp dưới lăng kính giải tích

Về mặt toán học hình thức, ký hiệu Big-O được định nghĩa bằng quan hệ bị chặn tiệm cận:  
$f(N) = O(g(N))$ khi và chỉ khi tồn tại hai hằng số dương $C > 0$ và $N_0 > 0$ sao cho:

$$0 \le f(N) \le C \cdot g(N), \quad \forall N \ge N_0$$

Trong giải tích, việc tính giới hạn của tỷ số $\lim_{N \to \infty} \frac{f(N)}{g(N)}$ là một công cụ để phân loại và chứng minh cấp tăng trưởng tiệm cận khi giới hạn này tồn tại.

---

### 2.1. Khái niệm vô cùng lớn và cấp vô cùng lớn

Khi kích thước dữ liệu $N$ tăng lên vô hạn ($N \to \infty$), hàm số $f(N)$ mô tả số lượng thao tác tính toán sẽ trở thành một **đại lượng vô cùng lớn**.

Giả sử $f(N) > 0$ và $g(N) > 0$ với mọi $N$ đủ lớn. Ta xét giới hạn tỷ số:

$$L = \lim_{N \to \infty} \frac{f(N)}{g(N)}$$

| Giá trị giới hạn L | Ý nghĩa trong giải tích | Ký hiệu tiệm cận (asymptotic notation) |
| :--- | :--- | :--- |
| $L = 0$ | $f(N)$ là vô cùng lớn bậc thấp hơn $g(N)$ | $f(N) = o(g(N))$ |
| $0 < L < \infty$ | $f(N)$ và $g(N)$ là hai vô cùng lớn cùng bậc | $f(N) = \Theta(g(N))$ (tiệm cận chặt), suy ra $f(N) = O(g(N))$ |
| $L = \infty$ | $f(N)$ là vô cùng lớn bậc cao hơn $g(N)$ | $f(N) = \omega(g(N))$ |

---

### 2.2. Vô cùng bé tương đối và sự chi phối của số hạng bậc cao nhất

Xét hàm thời gian $f(N) = 3N^2 + 500N + 10000$. Tại sao ta lại viết gọn độ phức tạp tiệm cận thành **$O(N^2)$**?

**Chứng minh bằng giải tích:**

Chia toàn bộ biểu thức cho số hạng có tốc độ tăng trưởng cao nhất là $N^2$:

$$\frac{f(N)}{N^2} = \frac{3N^2 + 500N + 10000}{N^2} = 3 + \frac{500}{N} + \frac{10000}{N^2}$$

Khi $N \to \infty$:

- Đại lượng $\frac{500}{N} \to 0$ (trở thành vô cùng bé).
- Đại lượng $\frac{10000}{N^2} \to 0$ (trở thành vô cùng bé).
- Giới hạn: $\lim_{N \to \infty} \frac{f(N)}{N^2} = 3$ (Hằng số hữu hạn $C = 3 > 0$).

> [!NOTE]
> **Tính chất toán học:** Khi $N$ tiến ra vô cùng, các số hạng bậc thấp ($500N$) và hằng số tự do ($10000$) đều trở thành **vô cùng bé tương đối** so với $N^2$, do đó **không còn ảnh hưởng đến cấp tăng trưởng tiệm cận**. Hệ số nhân hằng số $3$ chỉ làm dãn đồ thị chứ không làm biến đổi hình thái tiệm cận. Do đó $f(N) = \Theta(N^2)$ và $f(N) = O(N^2)$.

---

### 2.3. Thang xếp hạng cấp tăng trưởng tiệm cận

Thứ tự tăng trưởng từ chậm nhất (tối ưu nhất) đến nhanh nhất (kém hiệu quả nhất) khi $N \to \infty$:

$$1 \ll \log \log N \ll \log N \ll \sqrt{N} \ll N \ll N \log N \ll N^2 \ll N^3 \ll 2^N \ll N! \ll N^N$$

*(Ký hiệu $f(N) \ll g(N)$ biểu thị $\lim_{N \to \infty} \frac{f(N)}{g(N)} = 0$, nghĩa là $g(N)$ tăng trưởng vượt trội tiệm cận so với $f(N)$).*

![Biểu đồ so sánh tốc độ tăng trưởng của các hàm độ phức tạp Big-O](/assets/images/posts/algorithms/big-o-complexity-chart.svg)

---

## 3. Mã giả và phương pháp phân tích vòng lặp

### 3.1. Phân tích vòng lặp tuyến tính O(N) và vòng lặp logarit O(log N)

```python
# 1. Độ phức tạp O(N): Duyệt tuần tự mảng qua N phần tử
def find_max(arr):
    max_val = arr[0]
    for x in arr: # Vòng lặp chạy đúng N bước
        if x > max_val:
            max_val = x
    return max_val

# 2. Độ phức tạp O(log N): Chia đôi không gian tìm kiếm sau mỗi bước
def binary_search(arr, target):
    # Với mảng đã sắp xếp: không gian tìm kiếm giảm một nửa sau mỗi bước: N -> N/2 -> ... -> 1
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```

---

### 3.2. Thuật toán chia để trị O(N log N) và giải mã bằng định lý Master (Master theorem)

Đối với các thuật toán đệ quy chia để trị, độ phức tạp được biểu diễn qua hệ thức truy hồi:

$$T(N) = a \cdot T\left(\frac{N}{b}\right) + f(N)$$

Trong đó $a \ge 1$ là số lượng bài toán con, $b > 1$ là hệ số thu nhỏ kích thước dữ liệu, và $f(N)$ là chi phí chia và gộp kết quả.

**Áp dụng cho thuật toán sắp xếp trộn (merge sort):**

- Chia mảng làm 2 nửa ($a = 2, b = 2$) và gộp 2 mảng trong thời gian tuyến tính hai phía ($f(N) = \Theta(N)$):
  $$T(N) = 2T\left(\frac{N}{2}\right) + \Theta(N)$$
- Hàm chuẩn $N^{\log_b a} = N^{\log_2 2} = N^1 = N$.
- Vì $f(N) = \Theta(N)$ (cân bằng với $N^{\log_b a}$), theo trường hợp 2 của định lý Master:
  $$T(N) = \Theta(N \log N)$$

```python
# Minh họa cấu trúc chia để trị của Merge Sort: O(N log N)
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])   # T(N/2)
    right = merge_sort(arr[mid:])  # T(N/2)
    return merge(left, right)      # Chi phí gộp Θ(N)
```

---

### 3.3. Thuật toán lũy thừa nhị phân: Xử lý số mũ lớn trong O(log N)

Khi cần tính $a^b \pmod M$ với $b = 10^{18}$, nhân tuần tự bằng vòng lặp sẽ cần $10^{18}$ bước (không khả thi trong thực tế). Bằng thuật toán lũy thừa nhị phân (*binary exponentiation*), thuật toán chỉ cần $O(\log b)$ vòng lặp; với $b = 10^{18}$, số vòng lặp chỉ khoảng 60 chu kỳ:

```cpp
// Tính (a^b) % mod với b lên tới 10^18 trong O(log b)
// Lưu ý: Với mod đủ nhỏ để tích trung gian vừa vặn trong kiểu số nguyên 64-bit (long long).
// Với mod lớn hơn, cần dùng kiểu số nguyên 128-bit (__int128 trên GCC/Clang) hoặc phép nhân modulo an toàn.
long long fast_pow(long long a, long long b, long long mod) {
    long long result = 1;
    a %= mod;
    while (b > 0) {
        if (b & 1) { // Nếu bit cuối là 1
            result = (result * a) % mod;
        }
        a = (a * a) % mod;
        b >>= 1; // Dịch phải 1 bit (chia đôi số mũ b)
    }
    return result;
}
```

---

## 4. Tóm tắt quy tắc phân tích nhanh

1. **Vòng lặp bước nhảy nhân hoặc chia (`i *= 2` hoặc `i /= 2`):** Tương ứng với độ phức tạp tiệm cận $O(\log N)$ (khi thân vòng lặp là $O(1)$).
2. **Vòng lặp tăng hoặc giảm tuyến tính (`i += 1`):** Tương ứng với độ phức tạp tiệm cận $O(N)$ (khi thân vòng lặp là $O(1)$).
3. **2 vòng lặp lồng nhau phụ thuộc (`i` chạy từ 1 đến $N$, `j` chạy từ `i` đến $N$; hoặc dạng nửa mở `0 <= i < N`, `i <= j < N`):** Tổng số bước $N + (N-1) + \dots + 1 = \frac{N(N+1)}{2} = \frac{N^2}{2} + \frac{N}{2}$, tương ứng với độ phức tạp tiệm cận $O(N^2)$ (khi thân vòng lặp là $O(1)$).
4. **Cây đệ quy rẽ nhánh ($K \ge 2$):** Nếu mỗi nút sinh tối đa $K$ nhánh độc lập ($K \ge 2$) và độ sâu tối đa của cây đệ quy là $D$, số nút trong trường hợp xấu nhất là $\sum_{d=0}^D K^d = \frac{K^{D+1}-1}{K-1} = O(K^D)$ (khi chi phí xử lý tại mỗi nút là $O(1)$). Với $K = 1$ (đệ quy tuyến tính), số nút là $O(D)$.

---

## 5. Tài liệu tham khảo

- **CLRS (MIT Press):** Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein. *Introduction to Algorithms* (4th Edition, MIT Press, 2022) — Chapter 3: Characterizing Running Times, Chapter 4: Divide-and-Conquer & Master Theorem.
- **Donald E. Knuth (ACM):** Donald E. Knuth. *Big Omicron and Big Omega and Big Theta* (ACM SIGACT News, Vol. 8, No. 2, 1976, pp. 18–24).
- **Robert Sedgewick & Kevin Wayne (Princeton University):** *Algorithms* (4th Edition, Addison-Wesley, 2011) — Section 1.4: Analysis of Algorithms.
- **TOP500.org:** [Frontier Exascale Supercomputer Benchmark](https://www.top500.org/) — Mốc hiệu năng tính toán cực hạn exascale của siêu máy tính hiện đại ($1.194 \times 10^{18}\text{ FLOPS}$, tách biệt FLOPS phần cứng với độ phức tạp thuật toán).
