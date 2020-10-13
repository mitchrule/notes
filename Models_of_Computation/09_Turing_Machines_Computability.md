# Turing Machines

A Turing machine has an unbounded tape through which it takes its unput and performs its computations.

It can:

- Both read from and write to the tape
- More either left or right over the tape

The machines has distinct accept and reject states, in which it accepts/rejects irrespective of where its tape head is.

A Turing machine is a 7-tuple which consists of:

- A finite set of states
- A finite tape alphabet, including the blank character
- The input alphabet
- The transition function
- Initial state
- Accept state
- Reject state

_A Turing machine does not have to consume all of its input to finish in the accept state._

## Transition Function

A transition $\delta (q_i,x)=(q_j,y,d)$ depends on two things

- Current state $q_i$
- Currect symbol $x$ under the tape head

It consists of three actions

- Change state to $q_j$
- Overwrite tape symbol $x$ by $y$
- Move the tape head in direction $d$
