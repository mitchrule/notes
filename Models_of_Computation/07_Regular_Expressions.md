# Regular Expressions

Regular expressions is a notation for languages.

## Regular Expressions vs Automata

$L$ is regular iff $L$ can be described by a regular expression.

## Regular Expressions from NFAs

In this process, arcs get labelled with regular expressions.

- Starts by making sure the NFA has a single accept state.
- Repeatedly eliminate states that are neither start nor accept states

## Limitations of DFAs and NFAs

Consider the language $\{ 0^n 1^n | n \ge 0\}$

We cannot build a DFA to recognise this language, because a DFA has no memory of its actions so far.
