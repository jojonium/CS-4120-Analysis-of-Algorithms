% Analysis of Algorithms Notes
% Joseph Petitti
% October 24, 2019

## Chapter 2: Basics of Algorithm Analysis

Problem: imagine a network of nodes connected by edges. Assign a color to every
node such that any two adjacent nodes are different colors. What is the minimum
number of colors?

Brute force

  - Try all possible solutions. Usually takes $2^{n}$ steps or worse
  - Usually unacceptable in practice

Efficient algorithm should be significantly better than brute force

An algorithm has polynomial running time if:

> There exist constants $c > 0$ and $d > 0$ such that, for every input of size
> $n$, the running time of the algorithm is bounded above by $c n^{d}$ primitive
> computational steps

An algorithm is efficient if its running time is polynomial

  - In practice, poly-time algorithms usually have low constants and low
    exponents
  - Breaking through the exponential barrier of brute force typically exposes
    some crucial structure of the problem
  - Robust

Exceptions:

  - Some poly-time algorithms do have high constants and/or exponents and are
    useless in practice
  - Some exponential-time (or worse) algorithms are widely used because the
    worst-case instances seem to be rare

Measuring running time

  - Finding exact running time is very difficult
  - Running time: sensitive to model and other details
  - Convention: we care about asymptotics

Asymptotic order of growth

  - $O(f(n)$ is upper bounds
  - $\Omega (f(n))$ is lower bound
  - $\Theta (f(n))$ is tight bounds

Follow properties of transitivity and additivity

### A Survey of Common Running Times

__Constant Time__ is $O(1)$. Examples:

  - Conditional branch
  - Arithmetic/logic operation
  - Declare/initialize a variable
  - Follow a link in a linked list
  - Access element $i$ in an array
  - Compare/exchange two elements in an array

__Linear Time__ is $O(n)$

  - Merge two sorted lists (combine two sorted lists into a sorted whole)

__Quadratic Time__ is $O(n^{2})$

  - Closest pair of points: given a list of $n$ points in a plane find the pair
    that is closest to each other. The quadratic time algorithm is just to
    examine each pair of points

__Cubic Time__ is $O(n^{3})$

  - 3-sum: given an array of $n$ distinct integers, find three that sum to 0. The
  cubic time algorithm is to enumerate all triples (with $i < j < k$)

__Exponential Time__ is $O(2^{kn})$ for some constant $k > 0$

  - Given a graph, find independent set of max cardinality
