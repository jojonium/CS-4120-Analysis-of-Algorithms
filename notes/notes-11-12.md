% Analysis of Algorithms Notes
% Joseph Petitti
% November 12, 2019

Greedy

: Build up a solution incrementally, myopically optimizing some local criterion

Divide-and-conquer

: Break up a problem into several steps

Dynamic

: E

## Dynamic Programming

First example: Fibonacci numbers:

$f(0) = 0$, $f(1)=1$, $f(i) = f(i - 1) + f(i - 2)$

First solution: use recursion directly. Running time is exponential

Second soultion: $M(0) = 0$, $M(1) = 2$, for $i=2$ to $n$ $M[i] = M[i - 1] +
M[i - 2]$

Running time is linear.

Unweighted interval scheduling problem:

Greedy algorithm

: works if all weights are 1, but can fail spectacularly if arbitrary weights
are allowed

Dynamic programming: recursive solution

: Notation: OPT(j) = value of optimal solution to the problem consisting of job
requests $1, 2, \dots, j$.

  - Case 1: OPT selects job $j$
    - Collect profit $v_j$
    - Can't use incompatible jobs $\{ p(j) + 1, p(j) + 2, \dots, j - 1 \}$
    - Must include optimal solution to problem consisting of remaining
      compatible jobs $1, 2, \dots, p(j)$

  - Case 2: OPT does not select job $j$
    - must include optimal solution to problem consisting of remaining
      compatible jobs $1, 2, \dots, j - 1$

$$
OPT(j) = 
\begin{cases}
    0 & \textrm{if } j = 0 \\
    \max \{ v_j + OPT(p(j)), OPT(j - 1) \} &  \textrm{otherwise}
\end{cases}
$$

### Weighted Interval Scheduling: Running time

Claim: Memoized version of algorithm takes $O(n \log n)$ time.

  - Sort by finish time: $O(n \log n)$
  - Computing $p( \cdot )$: $O(n \log n)$
    - $p(j)$: job with largest finishing time prior to $j$ not intersecting
  - `M-Compute-Opt(j)`: each invocation takes $O(1)$ time and either 
    1. returns an existing value `M[j]`
    2. fills in one new entry `M[j]` and makes two recursive calls
  - Progress measure $\Phi =$ number of nonempty entries in `M[]`.
    - Initially $\Phi = 0$, throughout $\Phi \le n$

Dynamic programming algorithms computes optimal value. What if we want the
solution itself?

