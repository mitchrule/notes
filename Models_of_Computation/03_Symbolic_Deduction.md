# Symbolic Deduction

## Conjunctive Normal Form

A literal is $P$ or $\neg P$ where $P$ is a propositional letter.

A formula is in conjunctive normal form (CNF) if it is a conjunction of disjunctions of literals. (A conjunction of clauses).

It is in disjunctive normal form (DNF) if it is a disjunction of conjunctions of literals.

## Converting a Formula to CNF or to DNF

1. Eliminate all occurrences of $\oplus$ using $A \oplus B \equiv (A \lor B) \land (\neg A \lor \neg B)$.
2. Eliminate all occurrences of $\iff$ using $A \iff B \equiv (A \implies B) \land (B \implies A)$
3. Eliminate all occurrences of $\implies$ using $A \implies B \equiv \neg A \lor B$.
4. Use De Morgan's Laws to push $\neg$ inward over $\land$ and $\lor$.
5. Eliminate double negations using $\neg \neg A \equiv A$.
6. Using the distributinve laws to get the required form.

## Reduced Conjunctive Normal Form

A formula is in reduced CNF if, for each of its clauses, no propositional letter occurs twice.

## Canonical Forms: Xor Normal Form

If a normal forms leads to a unique representation for every Boolean function, we call it canonical.

Xor normal form presents the function in a sum-of-products form, using xor and conjunction.

$$ABC \oplus AC \oplus B \oplus C$$

This form is unique, up to reordering of conjuncts and summands.

## CNF and Clausal Form

We can think of a formula in CNF as given in clausal form, we may write $(P \lor \neg Q \lor S) \land (P \lor \neg R \lor S) \land (\neg S \lor \neg P)$ as $\{\{P,S,\neg Q\},\{P, \neg R, S\}, \{\neg S, \neg P\}\}$

## Empty Clauses and Formulas

- The set $\empty$ of clauses is valid.
- Any set $\{\empty, ...\}$ of clauses is unsatisfiable.

## Resolution-Based Inference

Consider the two clauses $\neg p \lor A$ and $P \lor B$.

- If $P$ is true, they reduce to $A$ and $t$.
- If $P$ is false, they reduce to $t$ and $B$.

If both clauses are true, then either $A$ is true or $B$ (or both). That is, the clause $A \lor B$ is a logical consequence of the two original clauses.

We call this their resolvent.

## Refuting a Set of Clauses

Resolution suggests a way of verifying that a CNF formula is unsatisfiable.

If, through a number of resolution steps, we can derive the empty clause $\perp$, then the original set of clauses were unsatisfiable.

We talk about a refutation proof.

## How to Use Refutations

To show that $F$ is valid, first put $\neg F$ in RCNF, yielding a set $S$ of clauses.

Then refute $S$, that is, deduce $\perp$ from $S$.

Suppose we express a circuit design as a formula $F$ in RCNF.

Suppose we wish to show that the design satisfies some property $G$, that is, show $F \models G$.

We can expliot the fact that, $F \models G$ iff $F \land \neg G$ is unsatisfiable.

Hence a strategy is:

1. Negate $G$ and bring it into RCNF.
2. Add those clauses to the set $F$.
3. Find a refutation of the resulting set of clauses.

# Predicate Logic

Unlike propositional logic, predicate logic allows us to

- Finitely express statements that deal with infinite collections of objects, e.g. integers.
- Express relations, capturing transitive verbs and relative pronouns.

To enable this, predicate logic uses variables that are assumed to range over collections of individuals, such as integers, graphs, people, as well as quantifiers.

Proposotional letters before generalised to predicates, that is, functions that map tuples of indiividuals to $f$ or $t$.

## Examples

No emus fly: $\forall x (Emu(x) \implies \neg Flies(x))$

There are black swans: $\exists x (Black(x) \land Swan(x))$

Tom found Rover and returned him to Anne: $Found(tom, rover) \land Gave(tom, rover, anne)$

Tom found a dog and gave it to Anne: $\exists x (Dog(x) \land Found(tom, x) \land Gave(tom, x, anne))$

## Existential and Universal Quantification

Existential quantification, $\exists$, is generalised $\lor$.
Universal quantification, $\forall$, is generalised $\land$.

## Vocabulary

- variables $(x,y,x,u,v,w,...)$
- function symbols $(f,g,h,...)$
- constants $(a,b,c,0,1,...)$
- predicate symbols $(P,Q,R,A,B,...)$
- connectives
- quantifiers
- parentheses
- (sometimes $(f,t)$)

## Terminology

A term is a variable or a constant or a construction
$$ f(t_1,...,t_n) $$
where $n>0$, $f$ is a function symbol of arity $n$, and each $t_i$ is a term.

An atomic formula is a construction $P(T_1,...,t_n)$ where $n \ge 0$ and $P$ is a predicate symbol of aroty $n$, and each $t_i$ is a term.

- Term $\leftrightarrow$ Individual, object
- Atom $\leftrightarrow$ Assertion (true or false)

A literal is an atomic formula or its negation

## Bound and Free Variables

A variable which is in the scope of a quantifier (binding that variable) is bound. If it is not bound then it is free.

A variable may occur both free and bound in a formula.

## English to Predicate Logic

- Introduce symbols for predicates
  - He is a man
  - Predicate: Is a man
  - Symbol: $M()$

"$x$ is a man", $M(x)$, cannot be assigned a truth value.

Kim is a man, $M(kim)$, can be assigned a truth value.

_It is very common to use $\implies$ with $\forall$ and $\land$ with $\exists$._

- Every human is mortal
  - $\forall x (Human(x) \implies Mortal(x))$
- Some cat is mortal
  - $\exists x (Cat(x) \land Mortal(x))$
