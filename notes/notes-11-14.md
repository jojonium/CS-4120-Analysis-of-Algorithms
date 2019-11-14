% Analysis of Algorithms Notes
% Joseph Petitti
% November 14, 2019

## Exam Tips:

  - Keep it simple!
  - Make sure you understand the basic definitions
  - Make sure you remember the algorithms from the course (BFS, Prim/Kruskal,
    activity selection...)
  - Stick with the course's book
  - Solution: try to isolate the key idea

# Homework 1 Questions

Most people got question 1 right, so we didn't go over it

## Question 2

Tree: connected graph with no cycles

Theorem: a graph $G$ is a tree if and only if it is connected and has exactly $n
- 1$ edges.

Solution: $G$ has at least $n - 1$ edges.

Run the explore connected component algorithm (pg. 82 of textbook)

Start with $S = \{s\}$. While $S \ne V$ find edge between $S$ and $V \backslash
S$. Such an edge must exist: graph is connected! Call all added edges special.

Total number of special edges: $n - 1$. Graph on special edges is connected
(induction).

More than $n - 1$ edges: there is an edge $e = (u, v)$ not special!

$u, v$ connected in $T$ means there is a cycle!

## Question 4

Prove that every connected graph $G$ has a vertex $v$ whose removal does not
disconnect the graph

Solution:

$G$ has a spanning tree $T$. Suffices to prove for $T$.

$T$ has a leaf $v$.

Removing $v$ does not make $T$ disconnected.

Proof: consider a path $P$ connecting $x$ to $y$ (both different from $v$).

If it contains $v$, delete it.

Efficient algorithm: compute a BFS tree and search for a leaf. Runtime is $O(n +
m)$

Running BFS from $s$: every vertex on the last layer $L(t)$ is a leaf

Analog for strong connectivity: not true!

## Question 5

Prove that a graph is connected if and only if every cut $(S, T)$ has an edge
crossing the cut

