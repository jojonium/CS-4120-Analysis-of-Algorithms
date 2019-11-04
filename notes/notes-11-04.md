% Analysis of Algorithms Notes
% Joseph Petitti
% November 4, 2019

## The Cut Property

Let $S$ be any subset of nodes, and let $e = (x, y)$ be a min cost edge crossing
the cut. Then there exists an MST $T^*$ containing $e$.

Proof (exchange argument):

  - Suppose $e = (x, y)$ does not belong to $T^*$, and let's see what happens
  - Since $(x, y)$ are connected in $T^*$ ther eis a path $P$ connecting them in
    $T^*$
  - $P$ must have an edge $f = (u, v)$ in $T^*$ crossing the cut!
  - $T' = T^* \cup \{e\} - \{f\}$: also a spanning tree
  - $T'$: minimum weight

Design of greedy algorithms for MST:

  - $T$ = empty
  - While there exists $(S, V \backslash S)$ without an edge in $T$
    - Choose min edge $e$ in $(S, V \backslash S)$
    - Add $e$ to $T$

Greedy produces a spanning tree of min cost

Proof:

We prove by induction on the number of iterations that all edges chosen are
contained in an MST $T^*$

  - First edge $e_1$ belongs to an MST by the cut property
  - Suppose true for $e_1, \dots, e_{i-1}$
  - By induction: there is an MST $T^\#$ containing $e_1, \dots, e_{i-1}$
  - Cut property: $T^\#$ has an edge $e'$ crossing the cut such that $(T^\#
    \backslash e') \cup e$ is a spanning tree
  - $e'$ and $e$ are not in $\{e_1, \dots, e_{i-1} \}$
  - Choose $e_i$ to equal $e$

