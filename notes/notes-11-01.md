% Analysis of Algorithms Notes
% Joseph Petitti
% November 1, 2019

## Minimum Spanning Trees

Spanning tree definition: Let $H = (V, T)$ be a subgraph of an undirected graph
$G = (V, E)$. $H$ is a spanning tree of $G$ if $H$ is both acyclic and
connected.

Every connected graph has a spanning tree

Minimum spanning trees have many applications

  - Network design
  - Approximating algorithms for combinatorial problems

### Solution Space Approach:

Examine all spanning trees:

  - Cayley's Theorem. There are $n^{n-2}$ spanning trees of the graph with all
    edges $K_n$ (at least $(n-1)!$ spanning trees)
  - Number of spanning trees in graphs of max degree $d$ may be exponential of
    $d$

Simplifying assumption: all edge costs $c_e$ are distinct

__Cut property__: Let $S$ be any subset of nodes, and let $e$ be the min cost
edge with exactly one endpoint in $S$. Then the MST must contain $e$.

__Cycle property__: Let $C$ be any cycle, and let $f$ be the max edge cost
belonging to $C$. Then the MST does not contain $f$.

Proof (exchange argument)

  - Suppose $e = (x, y)$ does not belong to $T*$, and let's see what happens.
  - Since $(x, y)$ are connected in $T*$ there is a path $P$ connecting them in
    $T*$

### Prim's Algorithm

  - Initialize $S$ = any node, $T = \emptyset$
  - Repeat $n - 1$ times:
    - Add to $T$ a min-cost edge with one endpoint in $S$
    - Add new node to $S$

Theorem: Prim's Algorithm produces a MST

Proof of correctness

Every edge $e$ added has minimum weight in the cut $(S, V \backslash S)$

  - $e$ belongs to every MST (cut property)
  - $T$ at the end: connected and has $n-1$ edges, therefore $T$ is a spanning
    tree
  - Let $T''$ be an MST. Every edge in $T$ is also in $T''$. Hence they are
    equal
  - $T$ is a minimum spanning tree

Prim's algorithm can be made to run in $O(m \log n)$ time.

### Kruskal's Algorithm

Consider edges in ascending order of cost. Add to tree unless it would create a
cycle

$e = (v, w)$ added by Kruskal

$S$: all nodes having a path, vrom $v$ before $e$ added

$w$ does not belong to $S$

$e$: first in $(S, V \backslash S)$

$e$ has minimum weight in the cut $(S, V \backslash S)$

  - $e$ belongs to every MST (cut property)
  - $T$ at the end: connected and no cycles, therefore $T$ is a spanning tree
  - Let $T''$ be an MST. Every edge in $T$ is also in $T''$. Hence they are
    equal
  - $T$ is a minimum spanning tree
