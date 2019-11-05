% Analysis of Algorithms Notes
% Joseph Petitti
% November 5, 2019

## Reverse Delete Algorithm

  - Sort all edges in $G$ in decreasing order
  - While there exist an edge $e$ whose removal does not disconnect the graph
    delete it
  - Return the set of remaining $F$ edges

__Correctness__:

  - The returned set of edges forms a tree (if there was a cycle we would have
    deleted an edge from it)
  - $F$: Necessarily a MST

__Question__: What is the running time of this algorithm?

## Clustering

Given a set $U$ of $n$ objects labeled $p_1, \dots, p_n$, classify into coherent
groups

Distance function

  ~ Numeric value specifying "closeness" of two objects

$k$-clustering

: Divide objects into $k$ non-empty groups

Distance function

: Assume it satisfies several natural properties

Spacing

: Minimum distance between any pair of points in different clusters

Clustering of maximum spacing

: Given an integer $k$, find a $k$-clustering of maximum spacing

Max $\min_{1 \le i < j \le k} d(C(i), C(j))$

__Single-link k-clustering algorithm__

  - Form a graph on the vertex set $U$, corresponding to $n$ clusters
  - Find the closest pair of objects such that each object is in a different
    cluster, and add an edge between them
  - Merge the two different clusters into a single cluster
  - Repeat $n-k$ times until there are exactly $k$ clusters

Key observation: this procedure is precisely Kruskal's algorithm (except we stop
when there are $k$ connected components)

Same as to finding an MST $T$ and deleting the $k-1$ most expensive edges in
$T$

By Kruskal, spacing of clustering is the length $d$ of the $(k-1)$st most
expensive edge in $T$

## Greedy Clustering Algorithm

Theorem: Let $C^*$ denote the clustering $C^*_1, \dots, C^*_k$ formed by
deleting the $k-1$ most expensive edges of the MST. $C^*$ is a $k$-clustering of
max spacing.

Proof:

  - Assume $C$ has some other clustering $C_1, \dots, C_k$
  - The spacing of $C^*$ is the length $d^*$ of the $(k-1)$th most expensive
    edge
  - Let $p_i, p_j$ be in the same cluster in $c^*$, say $C^*_r$, but different
    clusters in $C$, say $C_s$ and $C_t$
  - Some edge $(p, q)$ on $p_i - p_j$ path in $C^*_r$ connects two different
    clusters in $C$
  - All edges on $p_i - p_j$ path have length $\le d^*$ since Kruskal chose them
  - Spacing of $C$ is $\le d^*$ since $p$ and $q$ are in different clusters.
