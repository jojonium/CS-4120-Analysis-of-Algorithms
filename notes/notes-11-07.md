% Analysis of Algorithms Notes
% Joseph Petitti
% November 7, 2019

## Huffman Encoding

Prefix

: $x$ is a prefix of $y$ if there exists $i \le |y|$ such that $x = y_i$

S

: Finite set of symbols

Encoding

: $c:S \rightarrow \{ 0, 1 \}$. For every a in $S c(a)$ sequence of bits

Prefix free encoding

: For every $a, b$ in $S$, $c(a)$ is not a prefix of $c(b)$

Text

: A sequence of symbols from $S$ (length $n$)

Frequency of $b$

: $f_b$ is the number of occurrences of $b$ n the text $f_bn$

Observation: if we replace every symbol $x$ in $S$ by $c(x)$ we get a text of
length:

$\sum_{x \in S} f_x n |c(x)|$

__Average bits per letter__ of a prefix code $c$ is the sum over all symbols of
its frequency times the number of bitrs of its encoding:

$ABL(c) = \sum_{x \in S} f_x |c(x)|$

Goal: find a prefix code that has the lowest possible average bits per letter

Step 1: model a code as a binary tree

A binary tree is __full__ if every node that is not a leaf has two children

Claim: the binary tree corresponding to the optimal prefix code is full.

Proof by contradiction

  - Suppose $T$ is binary tree of optimal prefix code and is not full
  - This means there is a node $u$ with only one child $v$
  - Case 1: $u$ is the root; delete $u$ and use $v$ as the root
  - Case 2: $u$ is not the root:
    - Let $w$ be the parent of $u$
    - Delete $u$ and make $v$ be a child of $w$ in place of $u$
  - In both cases the number of bits needed to encode any leaf in the subtree of
    $v$ is decreased. The rest of the tree is not affected
  - Clearly this new tree $T'$ has a smaller ABL than $T$. Contradiction

Question: Where in the tree of an optimal prefix code should letters with a high
frequency be placed?
