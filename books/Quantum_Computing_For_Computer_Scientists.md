# My notes on Quantum Computing For Computer Scientists

This will be a slow read.

## Introduction

### From Real Numbers to Complex Numbers

- Quantum mechanics uses complex numbers in a fundamental way
- `i = √−1` was the "imaginary" solution to the polynomial equation `x² = −1`

### From Single States to Superpositions of States

- Every object exists in a unique place and in a well-defined state
- Even when we are not looking at it
- This is only true for large objects

- A microscopic object can "be in more than one place at a time"
- We say that an object is in a "superposition"
- In some sense, it is simultaneously in more than one location at the same time
- Other familiar physical properties are also hazy

- We do not see superposition of states
- Every time we look, measure, a superposition of states, it "collapses" to a single well-defined state

### From Locality to Non-locality

- Objects are directly affected only by nearby objects or forces
- To determine why a phenomenon occurs at a certain place, one must examine all the phenomena and forces near that place
- This is called "locality"
- Quantum mechanics laws predict certain effects that work in a nonlocal manner
- Two particles can be connected, "entangled", such that an action performed on one of them can have an immediate effect on the other particle light-years away

### From Deterministic Laws to Probabilistic Laws

- To which specific state will a superposition of states collapse when it is measured?
- The laws of quantum mechanics state that we can only know the probability of the outcome

### From Certainty to Uncertainty

- There are inherent limitations to the amount of knowledge that one can ascertain about a physical system

### The Implications Of The Quantum World On Computer Science

### Architecture

- A bit can be in either one of two states (0 or 1)
- Superposition will allow a qubit to be in both states simultaneously
- Many qubits together gives us quantum registers
- A quantum computer can be in many states simultaneously
- Quantum gates manipulate qubits
- Quantum gates will have to follow the dynamics of quantum operations
- Certain quantum operations are reversible hence certain quantum gates will have to be reversible

### Algorithms

- One places a quantum computer in many states simultaneously
- This needs special care: we cannot measure the computer while it is in this superposition because measuring it would collapse it to a single position
- Algorithms start with the quantum computer in a single position
- We shall then delicately place it in a superposition of many states.
- From there, we manipulate the qubits in a specified way.
- Finally, some of the qubits are measured.
- The measurement will collapse the qubits to the desired bits, which will be our output

- Entanglement will also play a role in quantum computing
- The qubits can be entangled
- By measuring some of them, others automatically reach the desired position

## Chapter 1 - Complex Numbers

