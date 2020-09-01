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

# Unification

## Most General Unifiers

A unifier of two tersm $s$ and $t$ is a substitution $\theta$ such that $\theta (s) = \theta (t)$.

The terms $s$ and $t$ are unifiable iff there exists a unifier for $s$ and $t$.

A most general unified (mgu) for $s$ and $t$ is a substitution $\theta$ such that

- $\theta$ is a unifier for $s$ and $t$
- every other unifier $\tau$ of $s$ and $t$ can be expressed as $\tau \circ \theta$ for some substitution.

### Unifier Examples

- $P(x,a)$ and $P(b,c)$ are not unifiable.
- $P(x,c)$ and $P(a,y)$ are unifiable using $\{x \mapsto a, y \mapsto c\}$

## Unification Algorithm

1. $F(s_1,...,s_n) = F(t_1,...,t_n)$
   1. Replace the equation by the $n$ equations $s_1 = t_1,...,s_n=t_n$
2. $F(s_1,...,s_n)=G(t_1,...,t_m)$ where $F \ne G$ or $n\ne m$
   1. Halt, returning failure.
3. $x=x$
   1. Delete the equation.
4. $t=x$ where $t$ is not a variable
   1. Replace the equation by $x=t$.
5. $x=t$ where $t$ is not $x$ but $x$ occurs in $t$
   1. Halt, returning failure.
6. $x=t$ where $t$ contains no $x$ but $x$ occurs in other equations
   1. Replace $x$ by $t$ in those other equations.

### Unification Example

Starting from $f(h(y),g(y,a),z) = f(x,g(v,v),b)$

We can use the substitution $\theta = \{x\mapsto h(a), y \mapsto a, v \mapsto a, z \mapsto b \}$
