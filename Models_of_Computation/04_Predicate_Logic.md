# Predicate Logic Semantics

## Interpretations (Structures)

An interpretation (or structure) consists of

- A non-empty set $D$. (the domain or universe)
- An assignment, to each n-ary predicate symbol $P$, of an n-place function $p : D^n \rightarrow \{f,t\}$
- An assignment, to each n-ary function symbol $g$, of an n-place function $g:D^n \rightarrow D$
- An assignment to each constant $a$ of some fixed element of $D$.

## Models and Validity of Formulas

A wff is true in interpretation $I$ iff every valuation makes $F$ true (for $I$). If not then it is false in interpretation $I$.

A model for $F$ is an interpretation $I$ such that $F$ is true in $I$. We write $I \models F$

A closed, well formed formula $F$ is

- satisfiable iff $I \models F$ for some interpretation $I$.
- valid iff $I \models F$ for every interpretation $I$.

## Rules for Quantifiers

$\exists x (\neg F_1) \equiv \neg \forall x F_1$

$\forall x (\neg F_1) \equiv \neg \exists x F_1$

$\exists x (F_1 \lor F_2) \equiv (\exists x F_1) \lor (\exists x F_2)$

$\forall x (F_1 \land F_2) \equiv (\forall x F_1) \land (\forall x F_2)$

# Resolution for Predicate Logic

## Skolemisation

### Predicate Logic Formulas to Clausal Form

1. Replace occurences of $\oplus$, $\iff$, and $\implies$.
2. Drive negation in.
3. Standardise bound variables apart.
4. Eliminate existential quantifiers (Skolemize).
5. Eliminiate universal quantifiers (just remove them).
6. Bring to CNF (using distributive laws).
