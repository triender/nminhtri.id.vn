---
id: "algorithm-definition-and-representation-methods"
title: "Algorithm definition: 5 core characteristics, representation methods, and structural theorem"
summary: "Comprehensive analysis of algorithms through Donald Knuth's 5 criteria, distinguishing from programs and heuristics, 4 representation methods, loop invariants, and space-time tradeoffs."
date: "2026-09-03"
category: "algorithms"
readTime: "10 min read"
badge: "Algorithms"
tags: ["Algorithms", "Computation Theory", "Pseudocode", "Flowchart", "Loop Invariants", "Donald Knuth"]
---

## 1. Quick reference and algorithm identification criteria

### 1.1. 5 core characteristics of an algorithm (Donald Knuth)

In foundational computer science, Donald E. Knuth (*The Art of Computer Programming*) systematized 5 characteristic features of an algorithm:

| Characteristic | English term | Technical specification | Violation scenario |
| :--- | :--- | :--- | :--- |
| **1. Finiteness** | *finiteness* | Must always terminate after a finite number of steps for any valid input. | Infinite loops, permanently hanging processes without exit conditions. |
| **2. Definiteness** | *definiteness* | Each step must be clear and unambiguous; machines execute without guessing. | Vague directives ("pick an arbitrary number", "increment slightly"). |
| **3. Input** | *input* | Accepts 0 or more defined values belonging to specified valid domains. | Undefined data types or unconstrained variable domains. |
| **4. Output** | *output* | Must produce at least one result with a determined relationship to inputs. | Statements executing without modifying state or returning a result. |
| **5. Effectiveness** | *effectiveness* | Every operation must be sufficiently basic to execute exactly in finite time. | Demanding infinite precision of real numbers or division by zero. |

---

### 1.2. Comparison: Algorithm vs program vs heuristic

Clarifying the distinction between mathematical concepts and runtime code:

| Metric | Algorithm | Program | Heuristic |
| :--- | :--- | :--- | :--- |
| **Termination guarantee** | Terminates after a finite number of steps for decision problems. | May never terminate (web servers, OS kernels, daemons). | Terminates based on defined iteration/convergence criteria. |
| **Solution guarantee** | Produces verified output adhering to specification (for exact algorithms). | Depends on implementation code and logic. | Yields a "good enough" approximation, no optimality guarantee. |
| **Scientific essence** | Abstract mathematical concept, hardware-independent. | Concrete implementation on specific languages and OS. | Empirical search strategy ($A^*$, genetic algorithms). |

---

### 1.3. Comparison of 4 algorithm representation methods

| Method | Essence | Strengths | Suitable context |
| :--- | :--- | :--- | :--- |
| **1. Natural language** | Step-by-step description in native prose. | Intuitive and accessible for beginners. | Brainstorming, business domain logic specifications. |
| **2. Flowchart** | Visual geometric diagrams. | Explicit control flow branching and loops. | Process analysis, education, architecture design documents. |
| **3. Pseudocode** | Blends programming syntax with structured prose. | Concise, language-agnostic, focuses purely on logic. | Standard in academic textbooks and research papers. |
| **4. Programming language** | Concrete source code (C++, Python, Java, Rust). | Directly compilable and executable by computers. | Production software development and deployment. |

---

### 1.4. Classification: Deterministic vs randomized algorithms

- **Deterministic algorithm:** The same input always passes through the exact same sequence of states and produces identical results (e.g., *merge sort*, *binary search*).
- **Randomized algorithm:** Employs pseudorandom numbers during execution to make branching choices and avoid worst-case scenarios on adversarial inputs or pathological data distributions (e.g., *randomized quick sort*, *Miller-Rabin*).

---

## 2. Fundamental components and Böhm–Jacopini structural theorem

The Böhm–Jacopini theorem (1966) establishes the structural foundation of computation.

### 2.1. Böhm–Jacopini structural theorem (1966)
The Böhm–Jacopini theorem (1966) proves that: **Any computable algorithm can be expressed using only 3 basic control structures (sequence, selection, and iteration), provided auxiliary boolean state variables are permitted when transforming arbitrary flow graphs**:

- **Sequence:** Statements execute consecutively from top to bottom in order of appearance.
- **Selection / Branching:** Evaluates a logical condition (`if-else`, `switch-case`) to choose the next execution path.
- **Iteration / Loop:** Repeats a block of statements (`while`, `for`) as long as the continuation condition holds true.

---

### 2.2. Illustrated case study: Primality test across 4 representation methods

Given an integer $N > 0$, determine whether $N$ is a prime number.

#### Method 1: Natural language description
1. Accept a positive integer $N$.
2. If $N \le 1$, conclude $N$ is not prime and terminate.
3. Initialize loop variable $i = 2$.
4. Loop while $i \cdot i \le N$:
   - If $N$ is divisible by $i$, conclude $N$ is not prime and terminate.
   - Increment $i$ by $1$ ($i = i + 1$).
5. If the loop completes without finding divisors, conclude $N$ is prime and terminate.

---

#### Method 2: Flowchart representation

![Prime check flowchart](/assets/images/posts/algorithms/prime-check-flowchart.svg)

---

#### Method 3: Standard pseudocode

```text
Algorithm IsPrime(N):
    Input: Positive integer N
    Output: True if N is prime, False if N is not prime

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

#### Method 4: Concrete programming implementation

```python
# Python implementation: Prime test in O(sqrt(N))
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
// C++ implementation: Prime test in O(sqrt(N))
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

## 3. Correctness proofs and engineering tradeoffs

### 3.1. Proving correctness with loop invariants

In algorithm analysis, proving correctness verifies that the algorithm functions as intended across all valid inputs. The standard technique is the **loop invariant**, evaluated in 3 phases analogous to mathematical induction:

1. **Initialization:** The invariant holds true prior to the first loop iteration.
2. **Maintenance:** If true before iteration $k$, it remains true before iteration $k+1$.
3. **Termination:** Upon loop termination, the invariant provides conclusive evidence that the algorithm produced the exact intended result.

> [!NOTE]
> **Application to `is_prime`:**  
> - **Invariant:** *"At the start of each iteration $i$, $N$ has no divisors in the range $[2, i-1]$."*  
> - **Initialization:** At $i = 2$, the range $[2, 1]$ is empty $\implies$ Invariant holds.  
> - **Maintenance:** If $N$ is not divisible by $i$, advancing to $i+1$ keeps $[2, i]$ free of divisors $\implies$ Invariant preserved.  
> - **Termination:** The loop terminates when $i > \lfloor\sqrt{N}\rfloor$ (i.e., $i > N / i$). By the arithmetic lemma, every composite number $N > 1$ must have at least one prime factor $\le \sqrt{N}$. Because $N$ has no divisors in $[2, \lfloor\sqrt{N}\rfloor]$, $N$ cannot be composite $\implies$ $N$ is prime.

---

### 3.2. Space-time tradeoff

In algorithm and system design, balancing memory usage against execution time is a fundamental engineering tradeoff:

| Strategy | Mechanism | Pros & Cons | Applied examples |
| :--- | :--- | :--- | :--- |
| **Trading memory for speed** | Uses auxiliary arrays or hash tables to store intermediate states. | Extremely fast ($O(1)$ or $O(N)$), but consumes higher RAM. | • Hash tables<br/>• Sieve of Eratosthenes<br/>• Dynamic programming memoization |
| **Trading time for memory** | Recomputes values on the fly without extra storage arrays. | Minimal memory footprint ($O(1)$ RAM), but higher execution time. | • Trial division primality test<br/>• Linear search |

---

## 4. Classic design paradigms and theoretical limits

### 4.1. 5 classic algorithm design paradigms

| Design paradigm | Core mechanism | Classic examples |
| :--- | :--- | :--- |
| **Brute-force** | Exhaustively searches the entire solution space. | Permutation search, linear scan |
| **Divide and conquer** | Recursively divides the problem into independent subproblems. | Merge sort, binary search |
| **Greedy** | Makes locally optimal choices at each step. | Dijkstra algorithm, Kruskal MST |
| **Dynamic programming** | Caches overlapping subproblem solutions (memoization). | Fibonacci numbers, knapsack problem, shortest path |
| **Backtracking** | Explores candidate solutions, undoing dead ends. | N-queens problem, maze solving, Sudoku |

---

### 4.2. Theoretical limits of computation

Not all mathematical problems are solvable by algorithms:

1. **Alan Turing's Halting Problem (1936):**
   - Turing proved mathematically that no general algorithm can decide whether an arbitrary program will halt or loop indefinitely.
2. **P and NP complexity classes:**
   - **Class P:** Decision problems solvable in polynomial time ($O(N^k)$) by a deterministic Turing machine — e.g., sorting, shortest paths.
   - **Class NP:** The set of decision problems whose candidate solutions can be verified in polynomial time via a polynomial-length certificate by a deterministic Turing machine (or solved in polynomial time by a non-deterministic Turing machine). Class NP contains Class P ($P \subseteq NP$).

---

## 5. Historical origins and academic references

### 5.1. Etymology of "algorithm"
- The word **"Algorithm"** derives from the Latinization of the 9th-century Persian mathematician and astronomer **Muhammad ibn Musa al-Khwarizmi**, whose pioneering treatise introduced systematic step-by-step arithmetic procedures.
- The word **"Algebra"** similarly originates from the Arabic word *al-jabr* in the title of his landmark book.

---

### 5.2. Academic references

- **Donald E. Knuth:** *The Art of Computer Programming, Volume 1: Fundamental Algorithms* (3rd Edition, Addison-Wesley, 1997) — Section 1.1: Algorithms.
- **Corrado Böhm & Giuseppe Jacopini:** *Flow Diagrams, Turing Machines and Languages with Only Two Formation Rules* (Communications of the ACM, Vol. 9, No. 5, 1966, pp. 366–371).
- **CLRS (MIT Press):** Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein. *Introduction to Algorithms* (4th Edition, MIT Press, 2022) — Chapter 1: The Role of Algorithms in Computing, Chapter 2: Getting Started (Loop Invariants).
