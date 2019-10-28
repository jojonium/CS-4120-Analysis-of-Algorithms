% Analysis of Algorithms Notes
% Joseph Petitti
% October 28, 2019

### Proof of Handshake Lemma

Handshake Lemma: 

$\displaystyle\sum_{v \in V} \text{degree}(v) = 2 |E|$

Proof: scan all vertices

  - For every vertex mark all edges next to it
  - Every vertex contributes $\text{deg}(v)$ marks
  - Overall $\sum_{v \in V} \text{degree}(v)$ marks
  - Every edge marked twice
  - Overall $2|E|$ edges

Theorem: every tree with more than one vertex has a vertex of degree one (leaf)

Proof: every vertex has degree > 0

Number of edges: $|E| = n - 1$

## Breadth-First Search

The $i\text{th}$ layer is all nodes exactly $i$ distance from the starting node

## Bipartiteness

__Goal__: decide if a graph is bipartite or not

Many graph problems become easier if the graph is bipartite

Lemma: if a graph $G$ is bipartite, it cannot contain an odd-length cycle

Proof. Not possible to 2-color the odd-length cycle, let alone $G$.

It turns out this is the only problem to bipartiteness. A graph is bipartite if
and only if it does not contain an odd-length cycle.

### How do you color a bipartite graph?

Lemma: Let $G$ be a connected graph and let $L_0, \dots, L_k$ be the layers
produced by BFS starting at node $s$. Exactly one of the following holds:

  1. No edge of $G$ joins two nodes of the same layer, and $G$ is bipartite
  2. An edge of $G$ joins two nodes of the same layer, and $G$ contains an
	 odd-length cycle (and hence is not bipartite

Proof.

  - Suppose no edge joins two nodes in the same layer
  - By BFS property, each edge joins two nodes in adjacent levels
  - Bipartition: white = nodes on odd levels, blue = nodes on even levels

Basically to be bipartite you can't have edges connecting nodes on
non-consecutive layers or two nodes on the same layer

Another proof:

  - Suppose $(x, y)$ is an edge with $x, y$ in the same level $L_j$
  - Let $z = lca(x, y)$, the lowest common ancestor
  - Let $L_i$ be level containing $z$
  - Consider cycle that takes edge from $x$ to $y$, then path from $y$ to $z$,
    then path from $z$ to $x$
  - Its length is $1 + (j - i) + (j - i)$, which is odd

Corollary: A graph $G$ is bipartite iff it contains no odd-length cycle

Corollary: There is an efficient algorithm to determine if a graph has no odd
cycles

## Strong connectivity

Definition: A graph is strongly connected if every pair of nodes is mutually
reachable


