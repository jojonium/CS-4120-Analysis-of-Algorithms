% Analysis of Algorithms Notes
% Joseph Petitti
% October 25, 2019

## Asymptotic Notation

__Exponential Time__ definition: $2^{n^{k}}$ for some $k > 0$

## Chapter 3: Graphs

Topics:

  - Basic definitions and applications
  - Graph connectivity and graph traversal
  - testing bipartiteness
  - connectivity in directed graphs
  - DAGs and topological ordering

### Undirected Graphs

Notation: $G = (V, E)$

  - $V$ = nodes (or vertices)
  - $E$ = edges (or arcs) between pairs of nodes

How many different graphs of size $n$ are there? $2^{\frac{n+1}{2}}$

### Graph representation

__Adjacency Matrix__

  - An adjacency matrix is an n-by-n matrix with $A_{uv} = 1$ if $(u, v)$ is an
    edge.
  - Two representations of each edge
  - Space proportional to $n^{2}$
  - Checking if $(u, v)$ is an edge takes $\Theta(1)$ time
  - Identifying all edges takes $\Theta(n^{2})$
  - Identifying all edges next to a vertex takes $\Theta(n)$ time_

__Adjacency Lists__

  - Node-indexed array of lists
  - Two representations of each edge.
  - Space is $\Theta(m + n)$
  - Checking if $(u, v)$ is an edge takes $O(\text{degree}(u))$ time[^1]

Takeaway: we use Adjacency Lists

  - Scan all neighbors of $v$ in time $O(\text{degree}(v))$
  - Handshake lemma:
    $\displaystyle\sum_{v \in V} \text{degree}(v) = 2 |E|$

[^1]: $\text{degree}(u)$ is the number of neighbors of $u$

### Connected components and independent sets

Definition: an undirected graph is _connected_ if for every pair of nodes $u$
and $v$, there is a path between $u$ and $v$

Definition: A _connected component_ is a connected subset of vertices that is not
strictly contained in any subset of vertices

Definition: An _independent set_ is a subset of vertices such that no two are
connected by an edge

### Cycles

Definition: a _cycle_ is a path $v_1, v_2, \dots, v_k$ of connected nodes where
the first and last nodes are connected

### Trees

Definition: An undirected graph is a _tree_ if it is connected and does not
contain a cycle

It's basically a minimum connected graph. Removing any edge breaks the
connectivity

Any two of these statements imply the third:

  1. $G$ is connected
  2. $G$ does not contain a cycle
  3. $G$ has $n-1$ edges

## Connectivity

$s-t$ connectivity problem: Given two nodes $s$ and $t$, is there a path
between $s$ and $t$?

$s-t$ shortest path problem: Given two nodes $s$ and $t$, what is the length of
a shortest path between $s$ and $t$?

Distance $d(s, t)$ = length of shortest path

### Breadth-First Search

BFS intuition: explore outward from $s$ in all possible directions, adding nodes
one layer at a time

High-level algorithm:

  - $L_{0} = { s }$
  - $L_{1}$ = all neighbors of $L_{1}$
  - $L_{2}$ = all nodes that do not belong to $L_{0}$ or $L_{1}$, and that have
    an edge to a node in $L_{1}$
  - $L_{i + 1}$ = all nodes that do not belong to an earlier layer, and that
    have an edge to a node in $L_{i}$

Theorem: For each $i$, $L_{i}$ consists of all nodes at distance exactly $i$
from $L_{0}$
