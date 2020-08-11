# Propositional Logic

_Propositional = Boolean Logic_

## Syntax

We assume that $\neg$ binds tighter than $\lor$ and $\land$.

These bind tighter than $\oplus$, which binds tighter than $\implies$ and $\iff$.

## Semantics

A proposition is false or true.

A _truth assignment_ maps each propositional letter to _t_ or _f_. We can give the semantics of the connectives via truth tables.

This gives meaning to all propositional formulas, as we let $A$ and $B$ stand for the values of arbitrary (compound) propositions.

### Conjunction and Disjunction

$P \land Q$ is the conjunction of $P$ and $Q$.

$P \lor Q$ is their disjunction.

An "or" in English sometimes translates to disjunction, sometimes it translates to exclusive or.

### The Conditional

$P \implies Q$ is best read "if $P$ then $Q$".

1. If the volume is increased, the pressure falls.
2. If Melbourne is in Queensland then Brisbane is in Victoria.
3. Melbourne and Brisbane are in different states _and_ if Melbourne is in Queensland then so is Brisbane.

$A \implies B$ has the same truth table as $\neg A \lor B$

### Other Binary Connectives

We can also define $\downarrow$ as "nor" and $\uparrow$ as "nand".

## Boolean Short-Circuit Definitions

Most programming languages offer the Boolean connectives 'and' and 'or', but usually these are not commutative. In Haskell, `0 == 1 && 1/0 == 42` has a different behaviour to `1/0 == 42 && 0 == 1`. If the first argument is false, the second argument is not evaluated.
