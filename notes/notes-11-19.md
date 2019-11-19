% Analysis of Algorithms Notes
% Joseph Petitti
% November 19, 2019

## Knapsack Problem

Goal: pack knapsack so as to maximize total value.

There are $n$ items: item $i$ provides value $v_i > 0$ and weighs $w_i > 0$. The
knapsack has weight capacity $W$. Assume all input values are integral.

Motivation: consumer behavior (e.g. choosing products in a store under budget
constraint)

### Dynamic Programming False Start

Def: OPT(i) = max profit subset of items $1, \dots, i$

Case 1: OPT does not select item $i$

  - OPT selects best of $\{ 1, 2, \dots, i - 1\}$

Case 2: OPT selects item $i$

  - Accepting item $i$ does not immediately imply that we will have to reject
    other items

Still missing something...

Add an index: consider a 2D table.

Define $OPT(i, w) =$ max profit subset of items $1, \dots, i$ with weight limit
$w$.

Case 1: OPT does not select item $i$

  - OPT selects best of $\{ 1, 2, \dots, i - 1\}$ using weight limit $w$

Case 2: OPT selects item i

  - new weight limit = $w - w_i$
  - OPT selects best of $\{ 1, 2, \dots, i - 1\}$ using new weight limit

Running time: $\Theta(n W)$
