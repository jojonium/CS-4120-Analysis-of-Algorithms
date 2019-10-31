% Analysis of Algorithms Notes
% Joseph Petitti
% October 31, 2019

## Interval Scheduling

Greedy algorithm in general: consider jobs in some natural order. Take each job
provided it's compatible with the ones already taken.

For interval scheduling: consider jobs in increasing order of finish time. Take
each job provided it's compatible with the ones already taken.

Implementation: $O(n \log{n})$

Theorem: greedy algorithm is optimal

Proof (by contradiction):

  - Assume greedy is not optimal, and let's see what happens
  - Let $i_1, i_2, \dots, i_k$ denote set of jobs selected by greedy
  - Let $j_1, j_2, \dots, j_m$ denote set of jobs in the optimal solution
  - Key observation: $f(i_r) \le f(j_r)$ for any $r \le k$
  - Suppose (towards contradiction) $k < m$
  - Key observation: $f(i_k) \le f(j_m)$ for any $r \le k$

## Interval Partitioning

Lecture $j$ starts at $s_j$ and finishes at $f_j$.

Goal: find minimum number of classrooms to schedule all lectures so that no two
occur at the same time in the same room.

Observation: Greedy algorithm never schedules two incompatible lectures in the
same classroom

Theorem: Greedy algorithm is optimal

Proof:

  - Let $d$ be the number of classrooms that the greedy algorithm allocates.
  - Classroom $d$ is opened because we needed to schedule a job, say $j$, that
    is incompatible with all $d-1$ other classrooms.
  - These $d-1$ lectures each end after $s_j$
  - Since we sorted by start time, all these $d-1$ lectures start no later than
    $s_j$
  - $d$ lectures overlapping at time $s_j$
  - Key observation: all schedules use $\ge d$ classrooms
  - Therefore the greedy algorithm is optimal

## Coloring Interpretation

Coloring: assignment colors to vertices such that no two neighboring vertices
have same color.

Question: connection between interval partitioning and coloring

## Shortest Path

Applications:

  - PERT/CPM
  - Map routing
  - Seam carving
  - Robot navigation
  - Texture mapping
  - Typesetting in LaTeX
  - Urban traffic planning
  - Telemarketer operator scheduling
  - Routing of telecommunications networks

### Dijkstra's Algorithm

  - Maintain a set of explored nodes $S$ for which we have determined the
    shortest path distance $d(u)$ from $s$ to  $u$
  - Initialize $S = \{s\}, d(s) = 0$
  - Repeatedly choose unexplored node $v$ which minimizes

    $\pi(v) = \min d(u) + l_e$

  - Add $v$ to $S$, and set $d(v) = \pi(v)$

Proof of correctness:

Invariant: For each node $u \in S$, $d(u)$ is the length of the shortest $s-u$
path.

Proof (by induction on $|S|$):

Base case: $|S| = 1$ is trivial

Inductive hypothesis: Assume true for $|S| = k \ge 1$

  - Let $v$ be next node added to $S$, and let $(u, v)$ be the chosen edge.
  - The shortest $s-u$ path plus $(u, v)$ is an $s-v$ path of length $\pi(v)$.
  - Consider any $s-v$ path P. We'll prove: no shorter than $\pi(v)$
  - $(x, y)$: first edge in $P$ leaving $S$, $P'$: the subpath to x

Runtime analysis:

For each unexplored node, maintain $\text{Key}(v) = \pi(v) = \min d(u) + l_e$

  - Next node to explore = node with minimum $\pi(v)$
  - When exploring $v$, for each incident edge $e = (v, w)$, update
    $\pi(w) = \min \{ \pi(w), \pi(v) + l_e \}$

Efficient implementation: maintain a priority queue of unexplored nodes,
prioritized by $\pi(v)$
