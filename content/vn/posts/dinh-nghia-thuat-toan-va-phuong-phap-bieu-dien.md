---
id: "dinh-nghia-thuat-toan-va-phuong-phap-bieu-dien"
title: "Thuật toán: Từ định nghĩa, cấu trúc đến giới hạn tính toán"
summary: "Phân tích cấu trúc thuật toán qua 5 đặc tính Donald Knuth, định lý Böhm–Jacopini, phương pháp kiểm chứng bất biến vòng lặp, chiến lược thiết kế và giới hạn lý thuyết tính toán."
date: "2026-09-03"
category: "algorithms"
readTime: "9 phút đọc"
badge: "Thuật toán"
tags: ["Thuật toán", "Lý thuyết tính toán", "Mã giả", "Lưu đồ", "Bất biến vòng lặp", "Donald Knuth"]
---

## 1. Tiêu chuẩn nhận diện thuật toán

Để phân biệt một quy trình tính toán nói chung (*computational method*) với một thuật toán hình thức trong khoa học máy tính, Donald E. Knuth trong tác phẩm kinh điển *The Art of Computer Programming* đã đúc kết 5 đặc trưng nền tảng:

### 1.1. 5 đặc tính thuật toán (Donald Knuth)

| Đặc tính | Tiếng Anh | Nội dung tiêu chuẩn | Biểu hiện vi phạm |
| :--- | :--- | :--- | :--- |
| **1. Tính hữu hạn** | *finiteness* | Phải kết thúc sau một số hữu hạn bước đối với mỗi trường hợp đầu vào thuộc miền xác định. | Vòng lặp vô hạn, tiến trình treo không có điều kiện thoát. |
| **2. Tính xác định** | *definiteness* | Mỗi bước phải rõ ràng, đơn nghĩa, máy tính thực thi không cần suy đoán. | Chỉ thị mơ hồ ("chọn một số bất kỳ", "tăng biến lên một ít"). |
| **3. Đầu vào** | *input* | Nhận từ $0$ hoặc nhiều giá trị xác định thuộc miền dữ liệu cho phép. | Không xác định kiểu dữ liệu hoặc phạm vi biến số. |
| **4. Đầu ra** | *output* | Tạo ra một hoặc nhiều giá trị đầu ra có quan hệ xác định với đầu vào. | Khối lệnh chạy xong nhưng không trả về giá trị hay thay đổi trạng thái. |
| **5. Tính khả thi** | *effectiveness* | Mỗi phép tính phải thực hiện được chính xác bằng một số hữu hạn thao tác cơ bản trong mô hình tính toán. | Đòi hỏi độ chính xác vô hạn trên số thực hoặc thao tác không khả thi về mặt vật lý. |

---

### 1.2. Phân biệt thuật toán, chương trình và giải thuật phỏng đoán

Trong khoa học tính toán và kỹ thuật phần mềm, ba khái niệm này thuộc các tầng trừu tượng khác nhau:

| Tiêu chí | Thuật toán (algorithm) | Chương trình (program) | Giải thuật phỏng đoán (heuristic) |
| :--- | :--- | :--- | :--- |
| **Đặc tính cốt lõi** | Phương pháp tính toán trừu tượng xác định quy trình giải quyết bài toán. | Bản hiện thực cụ thể của thuật toán hoặc hệ thống trên một ngôn ngữ máy tính. | Phương pháp tìm kiếm nghiệm dựa trên quy tắc kinh nghiệm hoặc ước lượng. |
| **Điều kiện dừng** | Về mặt lý thuyết, luôn kết thúc sau hữu hạn bước trên mỗi đầu vào. | Có thể được thiết kế để chạy liên tục (hệ điều hành, daemon, web server). | Điều kiện dừng phụ thuộc vào chiến lược và tiêu chí tìm kiếm được lựa chọn. |
| **Tính chất nghiệm** | Giải quyết bài toán theo đúng đặc tả (tính đúng đắn cần được chứng minh). | Phụ thuộc vào mã nguồn cài đặt và tính toàn vẹn của môi trường thực thi. | Sử dụng tiêu chí hoặc quy tắc tìm kiếm nhằm nhanh chóng tìm nghiệm; tùy bài toán, có thể không bảo đảm tính tối ưu hoặc tính đầy đủ. |

---

### 1.3. 4 phương pháp biểu diễn thuật toán

Thuật toán có thể được mô tả bằng nhiều mức biểu diễn khác nhau, từ ngôn ngữ tự nhiên đến mã nguồn thực thi

| Phương pháp | Hình thức mô tả | Ưu điểm | Ngữ cảnh phù hợp |
| :--- | :--- | :--- | :--- |
| **1. Ngôn ngữ tự nhiên** | Mô tả tuần tự bằng văn bản thông thường. | Trực quan, dễ tiếp cận cho người mới bắt đầu. | Trao đổi ý tưởng sơ khởi, tài liệu mô tả nghiệp vụ. |
| **2. Lưu đồ (flowchart)** | Trực quan hóa bằng các khối hình học chuẩn. | Thấy rõ luồng rẽ nhánh và các bước lặp. | Thiết kế hệ thống, phân tích quy trình luồng dữ liệu. |
| **3. Mã giả (pseudocode)** | Pha trộn cú pháp lập trình và ngôn ngữ tự nhiên. | Cô đọng, độc lập ngôn ngữ, tập trung vào logic. | Phổ biến trong giáo trình, tài liệu kỹ thuật và các công trình khoa học. |
| **4. Ngôn ngữ lập trình** | Mã nguồn cụ thể (C++, Python, Java, Rust). | Máy tính có thể biên dịch và thực thi trực tiếp. | Hiện thực hóa sản phẩm phần mềm thực tế. |

---

### 1.4. Cơ chế ra quyết định: Tất định và ngẫu nhiên hóa

- **Thuật toán tất định (deterministic algorithm):** Với cùng một trường hợp đầu vào, thuật toán luôn trải qua chuỗi biến đổi trạng thái nội bộ giống nhau và cho ra cùng một kết quả duy nhất (ví dụ: *merge sort*, *binary search*).
- **Thuật toán ngẫu nhiên hóa (randomized algorithm):** Sử dụng các giá trị ngẫu nhiên trong quá trình xử lý nhằm đạt được thời gian chạy kỳ vọng (*expected running time*) tốt hơn, đơn giản hóa cấu trúc dữ liệu, hoặc giảm thiểu rủi ro khi gặp dữ liệu đối kháng (ví dụ: *randomized quick sort*, hoặc kiểm tra tính nguyên tố dạng xác suất *Miller–Rabin*).

---

## 2. Định lý cấu trúc Böhm–Jacopini

Vào thập niên 1960, các chương trình máy tính thường phụ thuộc nặng nề vào lệnh nhảy tùy tiện `goto`, tạo nên cấu trúc rối rắm như mạng nhện (*spaghetti code*) khiến việc bảo trì và chứng minh tính đúng đắn gặp nhiều trở ngại.

Năm 1966, hai nhà toán học Corrado Böhm và Giuseppe Jacopini đã công bố một định lý nền tảng (định lý Böhm–Jacopini). Định lý chỉ ra rằng mọi sơ đồ luồng thuật toán hợp lệ đều có thể chuẩn hóa và biểu diễn hoàn chỉnh chỉ bằng sự kết hợp của **ba cấu trúc điều khiển cơ bản** (kèm theo các biến trạng thái phụ khi cần thiết):`

- **Cấu trúc tuần tự (sequence):** Thực thi các câu lệnh lần lượt từ trên xuống dưới theo thứ tự xuất hiện.
- **Cấu trúc rẽ nhánh (selection):** Đánh giá một điều kiện logic (`if-else`, `switch-case`) để quyết định luồng thực thi tiếp theo.
- **Cấu trúc lặp (iteration):** Thực hiện lặp lại một khối lệnh (`while`, `for`) chừng nào điều kiện dừng chưa thỏa mãn.

Định lý Böhm–Jacopini cung cấp cơ sở toán học cho trường phái lập trình có cấu trúc (*structured programming*), chứng minh rằng mọi luồng điều khiển thuật toán đều có thể chuẩn hóa mà không cần dựa vào lệnh nhảy `goto`.

---

### 2.1. Ví dụ kiểm tra số nguyên tố qua 4 cách biểu diễn

Khảo sát bài toán nhận vào số nguyên $N$ và xác định $N$ có phải số nguyên tố hay không (với quy ước số nguyên tố là số nguyên lớn hơn 1 chỉ chia hết cho 1 và chính nó):

#### Cách 1: Ngôn ngữ tự nhiên

1. Nhận số nguyên $N$.
2. Nếu $N \le 1$, kết luận $N$ không phải số nguyên tố và kết thúc.
3. Khởi tạo biến đếm $i = 2$.
4. Lặp lại chừng nào $i \cdot i \le N$:
   - Nếu $N$ chia hết cho $i$, kết luận $N$ không phải số nguyên tố và kết thúc.
   - Tăng $i$ thêm 1 đơn vị ($i = i + 1$).
5. Nếu vòng lặp kết thúc mà không tìm thấy ước số nào, kết luận $N$ là số nguyên tố và kết thúc.

---

#### Cách 2: Lưu đồ (flowchart)

![Lưu đồ thuật toán kiểm tra số nguyên tố](/assets/images/posts/algorithms/prime-check-flowchart.svg)

---

#### Cách 3: Mã giả (pseudocode)

```text
Algorithm IsPrime(N):
    Input: Số nguyên N
    Output: True nếu N là số nguyên tố, False nếu không phải

    if N <= 1 then
        return False
    
    i ← 2
    while i * i <= N do
        if N mod i = 0 then
            return False
        i ← i + 1
        
    return True
```

---

#### Cách 4: Mã nguồn thực thi (implementation)

```python
def is_prime(n: int) -> bool:
    if n <= 1:
        return False
    
    i = 2
    while i * i <= n:
        if n % i == 0:
            return False
        i += 1
        
    return True
```

```cpp
bool is_prime(long long n) {
    if (n <= 1) return false;
    
    for (long long i = 2; i <= n / i; ++i) {
        if (n % i == 0) {
            return false;
        }
    }
    return true;
}
```

---

## 3. Chứng minh tính đúng đắn và đánh đổi tài nguyên

### 3.1. Phương pháp bất biến vòng lặp (loop invariant)

Trong khoa học máy tính, việc kiểm thử phần mềm (*testing*) chỉ có thể xác nhận sự hiện diện của lỗi trên một số ca kiểm thử hữu hạn chứ không thể chứng minh thuật toán hoàn toàn không có lỗi (như nhà khoa học máy tính Edsger Dijkstra từng chỉ ra: *"Testing shows the presence, not the absence of bugs"*).

Để kiểm chứng tính đúng đắn hình thức (*formal correctness*), ta có thể sử dụng kỹ thuật bất biến vòng lặp (loop invariant). Tính đúng đắn của thuật toán được thiết lập từ sự kết hợp của: **Mệnh đề bất biến + Điều kiện kết thúc $\implies$ Hậu điều kiện của bài toán (postcondition)**, qua 3 bước tương tự phương pháp quy nạp toán học:

1. **Khởi tạo (initialization):** Mệnh đề bất biến phải đúng trước khi vòng lặp bắt đầu bước chạy đầu tiên.
2. **Duy trì (maintenance):** Nếu mệnh đề đúng trước lần lặp thứ $k$, nó phải tiếp tục đúng trước lần lặp thứ $k+1$.
3. **Kết thúc (termination):** Khi vòng lặp dừng lại, mệnh đề bất biến kết hợp với điều kiện kết thúc cung cấp chứng cứ logic bảo đảm hậu điều kiện thỏa mãn.

> [!NOTE]
> **Ứng dụng kiểm chứng hàm `is_prime`:**
>
> - **Mệnh đề bất biến:** *"Tại đầu mỗi vòng lặp $i$, số $N$ không có bất kỳ ước số nào trong đoạn $[2, i-1]$."*
> - **Khởi tạo:** Trước khi lặp ($i = 2$), đoạn $[2, 1]$ rỗng $\implies$ Mệnh đề đúng hiển nhiên.
> - **Duy trì:** Nếu $N$ không chia hết cho $i$, khi tăng $i$ lên $i+1$, đoạn $[2, i]$ vẫn không chứa ước của $N$ $\implies$ Mệnh đề được bảo toàn.
> - **Kết thúc:** Vòng lặp kết thúc khi $i > \lfloor\sqrt{N}\rfloor$ (tương đương $i > N / i$).  
>   - Chứng minh hoàn tất:* Nếu $N$ là hợp số thì tồn tại hai số nguyên $a, b > 1$ sao cho $N = a \cdot b$. Không mất tính tổng quát, giả sử $a \le b \implies a^2 \le ab = N \implies a \le \sqrt{N}$. Vì vậy, mọi hợp số bắt buộc phải có ít nhất một ước không tầm thường $\le \sqrt{N}$. Do đoạn $[2, \lfloor\sqrt{N}\rfloor]$ không chứa bất kỳ ước nào của $N$, suy ra $N$ không thể là hợp số. Vì $N > 1$, kết luận $N$ chắc chắn là số nguyên tố.

> [!CAUTION]
> **Sự đánh đổi về bộ nhớ và thời gian:**  
> Trong nhiều bài toán tính toán, ta có thể đánh đổi bộ nhớ để giảm thời gian thực thi (chẳng hạn lưu trữ trạng thái trung gian bằng bảng băm hoặc bảng quy hoạch động). Ngược lại, khi môi trường bị giới hạn dung lượng bộ nhớ, hệ thống thường chấp nhận tính toán lại trực tiếp trên luồng chạy, làm tăng tổng thời gian xử lý.

---

## 4. Chiến lược thiết kế thuật toán và giới hạn lý thuyết

### 4.1. Cơ chế của các chiến lược thiết kế thuật toán

Khi kích thước dữ liệu đầu vào $N$ tăng lên, không gian nghiệm của bài toán thường tăng theo hàm mũ ($O(2^N)$ hoặc $O(N!)$). Nếu chỉ tìm kiếm vô hướng, máy tính sẽ nhanh chóng quá tải.

**Chiến lược thiết kế thuật toán (algorithmic paradigm)** là các phương pháp tiếp cận tổng quát giúp kỹ sư khai thác cấu trúc toán học của bài toán: nhận diện tính độc lập của các bài toán con, sự gối nhau của các trạng thái trung gian, hay tính chất lựa chọn tham lam.

| Chiến lược | Cơ chế cốt lõi | Ngữ cảnh áp dụng | Ví dụ điển hình |
| :--- | :--- | :--- | :--- |
| **Vét cạn (brute-force)** | Duyệt qua toàn bộ không gian nghiệm khả thi. | Không gian tìm kiếm đủ nhỏ trong giới hạn thời gian cho phép, hoặc dùng làm đối chuẩn kiểm thử. | Duyệt hoán vị, tìm kiếm tuyến tính |
| **Chia để trị (divide & conquer)** | Chia bài toán lớn thành các bài toán con độc lập, giải đệ quy và gộp kết quả. | Bài toán phân rã được thành các phần tương tự không phụ thuộc lẫn nhau. | Sắp xếp trộn (*merge sort*), tìm kiếm nhị phân (*binary search*) |
| **Tham lam (greedy)** | Đưa ra lựa chọn tối ưu cục bộ tại từng bước với kỳ vọng đạt tối ưu toàn cục. | Bài toán thỏa mãn tính chất lựa chọn tham lam (*greedy-choice property*). | Thuật toán Dijkstra (với trọng số không âm), cây khung Kruskal |
| **Quy hoạch động (dynamic programming)** | Lưu trữ nghiệm của các bài toán con chồng lấn (*memoization*) để tái sử dụng. | Bài toán có cấu trúc con tối ưu (*optimal substructure*) và các bài toán con gối nhau. | Dãy Fibonacci, bài toán cái túi (*knapsack*), Floyd-Warshall |
| **Quay lui (backtracking)** | Thử từng khả năng theo cây quyết định; nếu gặp ngõ cụt thì lùi lại bước trước để rẽ nhánh khác. | Bài toán tìm kiếm lời giải thỏa mãn ràng buộc trong không gian tổ hợp lớn. | 8 quân hậu, giải mê cung, Sudoku |

---

### 4.2. Giới hạn lý thuyết tính toán

Dù năng lực phần cứng không ngừng phát triển, các mô hình tính toán hình thức — từ máy tính truyền thống đến máy tính lượng tử — vẫn chịu những giới hạn lý thuyết nhất định khi tồn tại những bài toán nằm ngoài khả năng xử lý của thuật toán.

1. **Lập luận lực lượng tập hợp (cardinality argument), dựa trên định lý Cantor:**  
   Máy tính hoạt động dựa trên các hệ thống hình thức rời rạc. Mọi thuật toán (từ chương trình trên máy Turing cổ điển đến chuỗi cổng trong mạch lượng tử phổ quát) đều có thể mã hóa thành một chuỗi ký tự hữu hạn trên một bảng chữ cái hữu hạn $\Sigma$. Do đó, tập hợp toàn bộ các thuật toán có thể xây dựng $\mathcal{A}$ là một tập con của tập mọi chuỗi hữu hạn $\Sigma^*$. Vì $\Sigma^*$ là hợp đếm được của các tập hữu hạn, lực lượng của tập thuật toán là vô hạn đếm được:
   $$|\mathcal{A}| \le |\Sigma^*| = \aleph_0$$

   Trong khi đó, xét không gian các bài toán quyết định (*decision problems*) trên chuỗi nhị phân $\{0, 1\}^*$: Mỗi bài toán thực chất là một hàm phán đoán nhận chuỗi $x$ và trả về Đúng hoặc Sai, tương đương với việc xác định một ngôn ngữ hình thức $L \subseteq \{0, 1\}^*$. Do đó, tập hợp toàn bộ các bài toán quyết định khả dĩ chính là tập lũy thừa của $\{0, 1\}^*$, ký hiệu là $\mathcal{P}(\{0, 1\}^*)$.

   Theo định lý Cantor, tập lũy thừa luôn có lực lượng lớn hơn nghiêm ngặt tập hợp ban đầu ($|S| < |\mathcal{P}(S)|$). Vì $|\{0, 1\}^*| = \aleph_0$, suy ra:
   $$|\mathcal{P}(\{0, 1\}^*)| = 2^{\aleph_0} = \mathfrak{c}$$

   Vì $\aleph_0 < 2^{\aleph_0}$, không thể tồn tại một toàn ánh từ tập thuật toán sang tập bài toán quyết định. Đây là một chứng minh phi kiến thiết (*non-constructive proof*): Số lượng bài toán là vô hạn không đếm được (lực lượng continuum $\mathfrak{c}$), hoàn toàn áp đảo số lượng thuật toán đếm được ($\aleph_0$). Hệ quả tất yếu là hầu hết mọi bài toán quyết định đều **không thể giải được bằng thuật toán (undecidable)**.

2. **Tính không quyết định được và vấn đề dừng — Alan Turing (1936):**  
   Alan Turing đã chứng minh định lý nền tảng: Không thể tồn tại một thuật toán tổng quát nào có khả năng kiểm tra một chương trình máy tính bất kỳ cùng dữ liệu đầu vào của nó sẽ dừng lại hay lặp vô hạn. Về sau, lý thuyết tính toán lượng tử cũng chỉ ra máy tính lượng tử vẫn tuân theo giới hạn khả tính này: không một thuật toán lượng tử nào có thể giải được bài toán dừng (như David Deutsch chứng minh năm 1985 và Michael Nielsen năm 1997). Sự vượt trội của máy tính lượng tử nằm ở việc rút ngắn thời gian xử lý một số lớp bài toán cụ thể (độ phức tạp), chứ không làm thay đổi ranh giới những bài toán có thể giải được (tính khả tính).

3. **Lớp bài toán P và NP (complexity classes):**  
   - **Lớp P (Polynomial time):** Tập hợp các bài toán quyết định có thể tìm được lời giải trong thời gian đa thức ($O(N^k)$) trên máy Turing tất định. Lớp P đại diện cho các bài toán có lời giải khả thi về mặt lý thuyết theo tiêu chuẩn thời gian đa thức.
   - **Lớp NP (Nondeterministic Polynomial time):** Tập hợp các bài toán quyết định mà nếu có sẵn một nghiệm ứng viên, tính đúng đắn của nghiệm đó có thể được **xác minh thông qua một chứng nhận (certificate) có độ dài đa thức** trong thời gian đa thức trên máy Turing tất định. Lớp NP bao gồm cả lớp P ($P \subseteq NP$).  
   - **Bài toán thiên niên kỷ $P \stackrel{?}{=} NP$:** Một trong những bài toán mở nổi tiếng nhất của khoa học máy tính lý thuyết là liệu $P = NP$ hay không: Liệu mọi bài toán có thể xác minh chứng nhận trong thời gian đa thức thì đều có thể tìm được lời giải trong thời gian đa thức hay không.

---

## 5. Nguồn gốc và tài liệu tham khảo

### 5.1. Nguồn gốc tên gọi

- Thuật ngữ **thuật toán (algorithm)** bắt nguồn từ tên phiên âm Latin của nhà toán học và thiên văn học Ba Tư thế kỷ thứ 9: **Muhammad ibn Musa al-Khwarizmi**, người đặt nền móng cho phương pháp tính toán số học thập phân từng bước.
- Thuật ngữ **"Algebra" (Đại số)** cũng bắt nguồn từ tựa đề cuốn sách *Al-Kitāb al-mukhtaṣar fī ḥisāb al-jabr wal-muqābala* của ông.

---

### 5.2. Tài liệu tham khảo

- **Donald E. Knuth:** *The Art of Computer Programming, Volume 1: Fundamental Algorithms* (3rd Edition, Addison-Wesley, 1997) — Section 1.1: Algorithms.
- **Corrado Böhm & Giuseppe Jacopini:** *Flow Diagrams, Turing Machines and Languages with Only Two Formation Rules* (Communications of the ACM, Vol. 9, No. 5, 1966, pp. 366–371).
- **CLRS:** Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein. *Introduction to Algorithms* (4th Edition, MIT Press, 2022) — Chapter 1: The Role of Algorithms in Computing, Chapter 2: Getting Started (loop invariants).
- **Alan M. Turing:** *On Computable Numbers, with an Application to the Entscheidungsproblem* (Proceedings of the London Mathematical Society, Series 2, Vol. 42, 1936, pp. 230–265).
- **David Deutsch:** *Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer* (Proceedings of the Royal Society of London. A. Mathematical and Physical Sciences, Vol. 400, No. 1818, 1985, pp. 97–117).
- **Edsger W. Dijkstra:** *Go To Statement Considered Harmful* (Communications of the ACM, Vol. 11, No. 3, 1968, pp. 147–148) & *Notes on Structured Programming* (Academic Press, 1972).
- **Michael O. Rabin:** *Probabilistic Algorithm for Testing Primality* (Journal of Number Theory, Vol. 12, No. 1, 1980, pp. 128–138).
- **Stephen A. Cook:** *The Complexity of Theorem-Proving Procedures* (Proceedings of the Third Annual ACM Symposium on Theory of Computing, 1971, pp. 151–158).
- **Roshdi Rashed:** *The Development of Arabic Mathematics: Between Arithmetic and Algebra* (Kluwer Academic Publishers, 1994).
