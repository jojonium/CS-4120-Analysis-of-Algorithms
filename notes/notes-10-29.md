% Analysis of Algorithms
% Joseph Petitti
% October 29, 2019

## Directed Acyclic Graphs

Lemma: if $G$ is a DAG, then $G$ has a node with no entering edges

Proof (by contradiction):

  - Suppose that $G$ is a DAG and every node has at least one entering edge
  - Pick any node $v$, and begin following edges backward from $v$. Since $v$
    has at least one entering edge $(u, v)$ we can walk backward to $u$
  - Then, since $u$ has at least one entering edge $(x, u)$, we can walk
    backward to $x$
  - Repeat until we visit a node, say $w$, twice
  - Let $C$ denote the sequence of nodes encountered between successive visits
    to $w$. $C$ is a cycle.
