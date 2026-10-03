---
id: "computational-complexity-and-calculus"
title: "Computational complexity: Execution time cheat sheet and asymptotic limits in calculus"
summary: "Understanding Big-O notation through calculus limits as N approaches infinity, practical lookup tables for operations per second, and loop analysis."
date: "2026-09-03"
category: "algorithms"
readTime: "8 min read"
badge: "Algorithms"
tags: ["Algorithms", "Calculus", "Big-O", "Performance", "Mathematics"]
---

## 1. Quick reference and execution limits

### 1.1. Computational capability reference

In computer science and competitive programming, baseline execution constraints are:

- **Standard desktop CPU:** Approximately $10^8$ basic operations per **second** (100 million ops/sec).
- **Exascale supercomputers:** Up to $10^{18}$ floating-point operations per second ($1\text{ Exaflops} = 10^{18}\text{ FLOPS}$).

```bash
# Estimation based on input size N (target operations <= 10^8 per second):
# If input size N <= 10^8  -> O(N) linear algorithm runs in <= 1.0s
# If input size N <= 10^18 -> Requires O(log N) or O(1) algorithms so operations <= 60
```

---

### 1.2. Cheat sheet: Input size N and maximum allowed complexity

Matching input size $N$ with acceptable time complexity within a **1-second window**:

| Input size N | Maximum feasible complexity | Typical algorithms and data structures |
| :--- | :--- | :--- |
| $N \le 10 - 12$ | $O(N!)$ or $O(N^2 \cdot 2^N)$ | Permutation backtracking, brute-force search, traveling salesperson problem TSP |
| $N \le 20 - 25$ | $O(2^N)$ | Subset iteration, bitmask dynamic programming |
| $N \le 80 - 100$ | $O(N^4)$ | 4-nested loop brute force, combinatorial geometry |
| $N \le 300 - 500$ | $O(N^3)$ | Floyd-Warshall all-pairs shortest path, standard matrix multiplication |
| $N \le 2000 - 5000$ | $O(N^2)$ | Insertion sort, basic Dijkstra, nested loops |
| $N \le 10^5 - 10^6$ | $O(N \log N)$ | Merge sort, Quick sort, segment tree, binary heap |
| $N \le 10^7 - 10^8$ | $O(N)$ | Two pointers, sieve of Eratosthenes, linear scan |
| $N \le 10^{12} - 10^{14}$ | $O(\sqrt{N})$ | Primality test, prime factorization, Mo's algorithm |
| $N \le 10^9 - 10^{18}$ | $O(\log N)$ | Binary search, binary exponentiation, Euclidean GCD |
| $N$ very large ($N \ge 10^{18}$) | $O(\log N)$ or $O(1)$ depending on structure | Binary exponentiation, binary search over value range, closed-form formulas |

---

## 2. Asymptotic complexity through the lens of calculus

Big-O complexity investigates the **growth rate of $f(N)$ as $N$ approaches infinity ($N \to \infty$)**.

### 2.1. Infinitely large quantities and asymptotic orders

When input size $N$ increases without bound ($N \to \infty$), the operations count $f(N)$ becomes an **infinitely large quantity**.

In calculus, we evaluate the limit of the ratio:

$$L = \lim_{N \to \infty} \frac{f(N)}{g(N)}$$

| Limit value L | Meaning in calculus | Asymptotic notation |
| :--- | :--- | :--- |
| $L = 0$ | $f(N)$ grows strictly slower than $g(N)$ | $f(N) = o(g(N))$ |
| $0 < L < \infty$ | $f(N)$ and $g(N)$ have the same order of growth | $f(N) = \Theta(g(N))$ and $f(N) = O(g(N))$ |
| $L = \infty$ | $f(N)$ grows strictly faster than $g(N)$ | $f(N) = \omega(g(N))$ |

---

### 2.2. Relative infinitesimals and lower-order term elimination

Why does $f(N) = 3N^2 + 500N + 10000$ simplify to **$O(N^2)$**?

**Calculus proof:**

Divide the entire expression by the highest-order term $N^2$:

$$\frac{f(N)}{N^2} = \frac{3N^2 + 500N + 10000}{N^2} = 3 + \frac{500}{N} + \frac{10000}{N^2}$$

As $N \to \infty$:
- The term $\frac{500}{N} \to 0$, becomes **infinitesimal**.
- The term $\frac{10000}{N^2} \to 0$, becomes **infinitesimal**.
- Limit: $\lim_{N \to \infty} \frac{f(N)}{N^2} = 3$ (Finite non-zero constant $C = 3 > 0$).

> [!NOTE]
> **Mathematical conclusion:** As $N$ approaches infinity, all lower-order terms ($500N$) and constants ($10000$) become **negligible infinitesimals relative to $N^2$**. Multiplicative constants do not alter the asymptotic growth rate. Hence $f(N) = O(N^2)$.

---

### 2.3. Hierarchy of growth rates

From slowest (best) to fastest (worst) as $N \to \infty$:

$$O(1) \subsetneq O(\log \log N) \subsetneq O(\log N) \subsetneq O(\sqrt{N}) \subsetneq O(N) \subsetneq O(N \log N) \subsetneq O(N^2) \subsetneq O(N^3) \subsetneq O(2^N) \subsetneq O(N!) \subsetneq O(N^N)$$

![Biểu đồ so sánh tốc độ tăng trưởng của các hàm độ phức tạp Big-O](/assets/images/posts/algorithms/big-o-complexity-chart.svg)

---

## 3. Pseudocode and practical loop analysis

### 3.1. Linear loops O(N) and logarithmic loops O(log N)

```python
# 1. O(N) Complexity: Sequential traversal over N elements
def find_max(arr):
    max_val = arr[0]
    for x in arr: # Loops exactly N times
        if x > max_val:
            max_val = x
    return max_val

# 2. O(log N) Complexity: Halving the search space at each iteration
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right: # Search space halved: N -> N/2 -> N/4 -> ... -> 1
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

### 3.2. Divide and conquer O(N log N) and Master theorem

For divide-and-conquer recurrences, running time is expressed as:

$$T(N) = a \cdot T\left(\frac{N}{b}\right) + f(N)$$

Where $a$ is the number of subproblems, $\frac{N}{b}$ is the size of each subproblem, and $f(N)$ is the cost of dividing and merging.

**Application to Merge Sort:**
- Splitting into 2 halves ($a = 2, b = 2$) and two-sided linear merging ($f(N) = \Theta(N)$):
  $$T(N) = 2T\left(\frac{N}{2}\right) + \Theta(N)$$
- Critical exponent: $N^{\log_b a} = N^{\log_2 2} = N^1 = N$.
- Since $f(N) = \Theta(N)$, by Case 2 of the Master Theorem:
  $$T(N) = \Theta(N \log N)$$

```python
# Divide-and-conquer structure of Merge Sort: O(N log N)
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])   # T(N/2)
    right = merge_sort(arr[mid:])  # T(N/2)
    return merge(left, right)      # Linear merge cost Θ(N)
```

---

### 3.3. Binary exponentiation: Handling N = 10^18 in O(log N)

When $N = 10^{18}$, calculating $a^N \pmod M$ naively requires $10^{18}$ multiplications (exceeding practical computing limits). Binary exponentiation reduces this to approximately 60 steps ($< 0.0001\text{ ms}$):

```cpp
// Computes (a^b) % mod for b up to 10^18 in O(log b)
// Note: mod <= 3e9 to prevent long long multiplication overflow (for mod > 3e9, use __int128 or safe modular multiplication)
long long fast_pow(long long a, long long b, long long mod) {
    long long result = 1;
    a %= mod;
    while (b > 0) {
        if (b & 1) { // If lowest bit is 1
            result = (result * a) % mod;
        }
        a = (a * a) % mod;
        b >>= 1; // Bit shift right (halving b)
    }
    return result;
}
```

---

## 4. Quick reference checklist

1. **Multiplication or division loop step (`i *= 2` or `i /= 2`):** Asymptotically bounded by $O(\log N)$ (when loop body executes in $O(1)$).
2. **Linear step increment (`i += 1`):** Asymptotically bounded by $O(N)$ (when loop body executes in $O(1)$).
3. **Dependent nested loops (`i` from 1 to $N$, `j` from `i` to $N$; or half-open `0 <= i < N`, `i <= j < N`):** Total steps $N + (N-1) + \dots + 1 = \frac{N(N+1)}{2} = \frac{N^2}{2} + \frac{N}{2}$, asymptotically bounded by $O(N^2)$ (when loop body executes in $O(1)$).
4. **K-way branching recursion with depth $D$ ($K \ge 2$):** Asymptotically bounded by $\sum_{d=0}^D K^d = \frac{K^{D+1}-1}{K-1} = O(K^D)$ (when each node executes in $O(1)$). For $K = 1$ (linear recursion), total nodes is $O(D)$.

---

## 5. Academic references

- **CLRS (MIT Press):** Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein. *Introduction to Algorithms* (4th Edition, MIT Press, 2022) — Chapter 3: Asymptotic Notation, Chapter 4: Divide-and-Conquer & Master Theorem.
- **Donald E. Knuth (ACM):** Donald E. Knuth. *Big Omicron and big Omega and big Theta* (ACM SIGACT News, 1976).
- **Robert Sedgewick & Kevin Wayne (Princeton University):** *Algorithms* (4th Edition, Addison-Wesley, 2011) — Chapter 1.4: Analysis of Algorithms.
- **World Supercomputer Ranking:** [TOP500.org](https://www.top500.org/) — Frontier Exascale Supercomputer Benchmark ($1.194 \times 10^{18}\text{ FLOPS}$).
