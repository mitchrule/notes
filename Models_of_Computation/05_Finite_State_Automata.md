# Finite State Automata

## Regular Languages

A language is regular iff there is a finite automaton that recognises it.

## Regular Operations

Let $A$ and $B$ be languages

- Union: $A \cup B$
- Concatenation: $A \circ B = \{xy | x \in A, y \in B\}$
- Kleene Star: $A^* = \{x_1 x_2 ... x_k | k \ge 0,$ each $x_i \in A \}$
  - The empty string, $\epsilon$, is always in $A^*$

## Nondeterminism

In an NFA, it is possible to have transitions to multiple states with the same input.

### Epsilon Transitions

In an NFA, we are allowed to make a transition without consuming any input.

This is called an $\epsilon$ transition.

This is useful for constructing a machine to recognise the union of two languages.
