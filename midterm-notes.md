% Analysis of Algorithms Midterm Review
% Joseph Petitti
% November 16, 2019

## Increasing Orders

  - $O(1)$
  - $O(\log n)$
  - $O(n)$
  - $O(n \log n)$
  - $O(n^2)$
  - $O(n^k)$, $k$ is an integer greater than 2
  - $O(c^n)$, $c$ is a constant
  - $O(n!)$

## Data structures

  - Priority Queue
    - Get sorted list: $O(n \log n)$
    - Heapify: $O(\log n)$
    - Insert, delete: $O(\log n)$
    - Find min: $O(n)$
	- A sequence of $O(n)$ priority queue operations can be used to sort a set
	  of $n$ numbers
    - Change value of key: $O(\log n)$

  - List
    - Access element $i$: $O(n)$
    - Insert, delete: $O(1)$
    - Contains: $O(n)$

  - Array
    - Access element $i$: $O(1)$
    - Insert, delete: $O(n)$
    - Contains: $O(\log n)$

  - Union-Find
    - Union operation takes O(1) time
    - $O(n)$ time to make
    - Find takes $O(\log n)$
    - Useful for Kruskal's algorithm

## Algorithms

  - Greedy
    - Good when there's only one parameter to optimize
    - Proof of correctness: exchange argument. Assume to contradiction that
      there's a more optimal solution S. Greedy would have picked the better
      element from S, therefore contradiction
    - Usually $O(n \log n)$, involving $O(n \log n)$ to sort and then $O(n)$ to
      go through the sorted list

  - Dijkstra's
    - Greedy
    - Takes a graph $G$ and a starting point $s$ and finds the shortest path
      from $s$ to every other node in $G$
    - Using a heap-based priority queue, runs in $O(m \log n)$

  - Prim's
    - Greedy
    - Finds the minimum spanning tree of a graph
    - Runs Dijkstra's algorithm

  - Kruskal's (union find)
    - Greedy
    - Finds the minimum spanning tree
    - $O(m \log n)$ time using the right data structures
    - Uses the Union-Find data structure

  - Clustering
	- Run Kruskal's algorithm and stop it before it adds the last $(k - 1)$th
	  edges

  - Breadth-First Search
    - $O(n + m)$
    - Creates a tree in which no edge spans more than one layer and each layer
      $i$ is $i$ distance from the starting node.

## Proof by Contradiction

  - If $(A \and !B)$ is false or $(B \and !A)$ is false, then A implies B

## Proof by Induction

  - Prove base case that $n = c$ is true, where $c$ is a constant (usually 1)
  - Assume true for $n = k$. Prove that $n = k + 1$ is true.

## Forward Reasoning

  - Series of implications that are true until you get where you want

## Definitions

Connected graph

: For all node pairs $u,v$ in undirected graph $G$ there exists a path from $u$
to $v$

Strongly connected graph

: For all node pairs in directed graph $G$, there exists a path from $u$ to $v$
and from $v$ to $u$

Tree

: Connected graph with no cycles. This implies that it has $n - 1$ edges

Spanning Tree

: Tree that includes all nodes in $G$, with the minimum number of edges ($n -
1)$

Minimum Spanning Tree

: The spanning tree of $G$ with minimum total edge weight

Cycle

: A non-empty trail in which the only repeated vertices are the first and last
vertices

Bipartite Graph

: a graph whose vertices can be divided into two disjoint and independent sets
$U$ and $V$ such that every edge connects a vertex in $U$ to one in $V$

: A graph is bipartite if and only if it does not contain an odd cycle

: A graph is bipartite if and only if it is 2-colorable

## Practice

1. Create an algorithm that determines whether a graph $G$ of $(V, E)$ is
   bipartite. Prove its correctness and analyze its running time.
   
   __Algorithm__:
   
     - Pick a node $s \in V$ to start with.
     - Build a BFS tree from $G$ starting with $s$
     - If any two nodes in the same layer are connected return false
     - Otherwise return true
   
   __Proof of correctness__:
   
   A graph is bipartite if its vertices can be divided into two disjoint and
   independent sets $U$ and $V$ such that every edge connects a vertex in $U$ to
   one in $V$.
   
   BFS return a tree where no edge can span more than one layer. Our algorithm
   makes sure no two nodes on the same layer are connected. Therefore each layer is
   a set of disconnected nodes. Therefore color each odd-numbered layer $c_1$ and
   each even-numbered layer $c_2$. Because each layer is a disconnected set of
   nodes, no two neighboring nodes will be connected. By the definition of a BFS
   tree no two odd or two even layers will be connected to each other. Therefore
   this is a legal coloring of $G$ using only two colors. Therefore $G$ is
   bipartite.
   
   __Running Time__:
   
   If you keep track of the layer each node is on as you go through BFS you can do
   this algorithm in the same amount of time as BFS, which is $O(m + n)$.
   
2. Suppose graph $G$ is connected with distinct edge weights. Prove $G$ has a
   unique MST.

   Proof by contradiction:

   - Suppose that the minimum spanning tree $T$ is not unique. Therefore there
     must be another minimum spanning tree $T'$
   - There must be some edge $e$ in $T$ that is not in $T'$ and some edge $e'$
     in $T'$ that is not in $T$.
   - Swap $e$ with $e'$. $T$ and $T'$ should still have the same edge weight.
   - Therefore $e$ and $e'$ have the same weight. This is a contradiction
     because the edges in $G$ have distinct weights.
