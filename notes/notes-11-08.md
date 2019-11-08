% Analysis of Algorithms
% Joseph Petitti
% November 8, 2019

## Integer Multiplication

### Addition

Given two $n$-bit integers $a$ and $b$, compute $a + b$.

Grade-school: $\Theta (n)$ bit operations

Remark: grade-school addition algorithm is optimal

### Multiplication
Given two $n$-bit integers, compute $a \times b$.

Grade school algorithm (long multiplication): $\Theta (n^2)$ bit operations

Divide and conquer multiplication:

To multiply two $n$-bit integers $a$ and $b$:

  - Multiply four $\frac{1}{2} n$-bit integers, recursively
  - Multiply three $\frac{1}{3} n$-bit integers, recursively
  - Add, subtract, and shift to obtain result
