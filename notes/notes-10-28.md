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
