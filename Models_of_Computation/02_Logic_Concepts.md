# Logic Concepts

## Language

A propositional formula is _valid_ if there is no truth assignment which makes it false. Otherwise it is _non-valid_.

It is _unsatisfiable_ if no truth assignment makes it true. Otherwise it is _satisfiable_.

A valid propositional formula is a _tautology_.

An unsatisfiable propositional formula is a _contradiction_.

A valid statement is not that laudable; in a sense it is void of information. For example: $A \implies A$ is valid.

## Contradiction Example

$P \land Q \land (\neg Q \iff (\neg P \lor Q))$ is unsatisfiable.

Again, we can just complete the truth table. However, it is often possible to apply faster reasoning.

In this case, $P$ and $Q$ are conjuncts of the formula, so if a truth assignment maps either to $f$, the formula evaluates to $f$.

Validity is preserced by _substitution_ of propositional letters by formulas.

_A formula is unsatisfiable iff its negation is valid!_

## Models, Logical Consequence, and Equivalence

Let $\theta$ be a truth assignment and $\Phi$ be a propositional formula. If $\theta$ makes $\Phi$ true then $\theta$ is a _model_ of $\Phi$.

$\Psi$ is a _logical consequence_ of $\Phi$ iff every model of $\Phi$ is a model of $\Psi$ as well. In that case we write $\Phi \models \Psi$.

If $\Phi \models \Psi$ and $\Psi \models \Phi$ both hold, that is, $\Phi$ and $\Psi$ have exactly the same models, then $\Phi$ and $\Psi$ are logically equivalent.

In that case we write $\Psi \equiv \Phi$.

Substitution preserves logical equivalence.

Replacing equals by equals yields equals. If

1. $F$ is a sub formula of $H$,
2. $F \equiv G$, and
3. $H'$ is the result of replacing $F$ in $H$ by $G$.

### Some Equivalences

Absorption

- $P \land P \equiv P$
- $P \lor P \equiv P$

Commutativity

- $P \land Q \equiv Q \land P$
- $P \lor Q \equiv Q \lor P$

Associativity

- $P \land (Q \land R) \equiv (P \land Q) \land R$
- $P \lor (Q \lor R) \equiv (P \lor Q) \lor R$

Distributivity

- $P \land (Q \lor R) \equiv (P \land Q) \lor (P \land R)$
- $P \lor (Q \land R) \equiv (P \lor Q) \land (P \lor R)$

De Morgan

- $\neg (P \land Q) \equiv \neg P \lor \neg Q$
- $\neg (P \lor Q) \equiv \neg P \land \neg Q$

Implication

- $P \implies Q \equiv \neg P \lor Q$

Contraposition

- $\neg P \implies \neg Q \equiv Q \implies P$
- $P \implies \neg Q \equiv Q \implies \neg P$
- $\neg P \implies Q \equiv \neg Q \implies P$

Biimplication

- $P \iff Q \equiv (P \land Q) \lor (\neg P \land \neg Q)$

Let $\perp$ be any unsatisfiable formula and let $\top$ be able valid formula.

Duality

- $\neg \top \equiv \perp$
- $\neg \perp \equiv \top$

Negation from absurdity

- $P \implies \perp \equiv \neg P$

Identity

- $P \lor \perp \equiv P$
- $P \land \top \equiv P$

Dominance

- $P \lor \perp \equiv P$
- $P \land \top \equiv P$

Contradiciton

- $P \land \neg P \equiv \perp$

Excluded middle

- $P \lor \neg P \equiv \top$
