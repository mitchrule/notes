# Well-foundedness and Termination

## Partial Functions

We have assumed that the domain of the function is known, so $f:X \rightarrow Y$ means $f(x)$ is defined for each $x \in X$

In computer science, it is often more appropriate to deal with functions that are partial.

$f(x)$ may be defined for only some $x \in X$.

## The Termination Question

Termination of algorithms is a tricky problem. (The general problem is undecidable)

_A function will always terminate if its lexicographical representation is always decreasing._

## Well Founded Orderings

The binary relation $\prec$ over some set $X$ is well founded iff there is no infinite sequence of X-elements $x_1, x_2, x_3,...$ such that $x_1 \succ x_2 \succ x_3...$

We say that $(X, \prec)$ is a well founded structure.

For example, $( \N, <)$ is a well founded structure.

### Lexicographic Ordering of Tuples

Example:

$(2,2,2) \succ (2,1,42) \succ (1,3,1000) \succ (1,3,999) \succ (0,0,15)$

Index 0 has the highest value in the tuple, then 1, then 2. This is the same as the lexicographic ordering of strings.
