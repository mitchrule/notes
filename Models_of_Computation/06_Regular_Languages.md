# Regular Languages

## Closure Results for Regular Languages

- The class of regular languages is closed under union.
  - Epsilon transitions can be added from a single start state to the start state of each language
- The class of regular languages is closed under $\circ$.
  - Epsilon transitions can be added from the end state of language $A$ to the start state of language $B$.
- The class of regular languages is closed under Kleene Star.
  - End states of language $A$ can have epsilon transitions back to the start state of $A$.

Regular langauges are also closed under

- Intersection
- Complement ($A^C =$ All strings not in $A$)
- Difference
- Reversal

## Equivalence of DFAs

Since a DFA has a unique start state and the transition function is total and deterministic, we can test two DFAs for equivalence by minimizing them.

## Generating a Minimal DFA

This algorithm takes an NFA and produces an equivalent minimal DFA.

Input can also be a DFA

1. Reverse the NFA/DFA
2. Determinize the result
3. Reverse again
4. Determinise

To reverse an NFA $A$ with initial state $q_0$ and accept states $F \ne \empty$:

1. If $F= \{q\}$, let $q$ be the accept state
2. Otherwise add a new state $q$ which becomes the only accept state; then, for each state in $F$, add an $\epsilon$ transition to $q$.
3. Reverse every transition in the resulting NFA, making $q$ the initial state and $q_0$ the only accept state.
