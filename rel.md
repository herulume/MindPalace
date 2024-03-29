# Rel

A [[category]].

- Objects: Sets
- Morphisms: [[binary-relation]]s ($f : A → B$ means $f \subseteq A× B$)
- Composition: $R : A \to B$ and $S : B \to C$ then $(a, c) \in S \circ R \Leftrightarrow \exists b\ (a, b) \in R \land (b, c) \in S$
- Identity morphism: $1_A = \{ (a, a) \in A \times A | a \in A\} \subseteq A \times A$

## Proofs
### Left id
   - $f : A \to B$
   - $b\ (id_B \circ f)\ a = \langle \exists b \::\:: b\ id_B\  b \land b\ (f)\ a \rangle$
   - $b\ id_B\ b$ is always true so  $b\ (id_B \circ f)\ a = \langle \exists b \::\:: b\ (f)\ a \rangle = f$
### Right id
   - $f : A \to B$
   - $b\ (f \circ id_A)\ a = \langle \exists a \::\:: b\ (f)\  a \land a\ id_A\ a \rangle$
   - $a\ id_A\ a$ is always true so  $b\ (f \circ id_A)\ a = \langle \exists a \::\:: b\ (f)\ a \rangle = f$
### Associativy
   - $f : A \to B$
   - $g : B \to C$
   - $h : C \to D$

$$
\begin{equation}
\begin{matrix}
d\ ((h \circ g)\ \circ f)\ a = d\ (h \circ (g \circ f))\ a \\
\Leftrightarrow \\
\langle \exists b \::\:: d\ (h \circ g)\ b \land b\ (f)\ a \rangle = \langle \exists c \::\:: d\ (h)\ c \land c\ (g \circ f)\ a \rangle \\
\Leftrightarrow \\
\langle \exists b \::\:: \langle \exists c \::\:: d\ (h)\ c \land c\ (g)\ b \rangle \land b\ (f)\ a \rangle = \langle \exists c \::\:: d\ (h)\ c \land \langle \exists b \::\:: c\ (g)\ b \land b\ (f)\ a \rangle \rangle \\
\Leftrightarrow \\
\langle \exists b,c \::\::  d\ (h)\ c \land c\ (g)\ b \land b\ (f)\ a \rangle = \langle \exists c,b \::\:: d\ (h)\ c \land c\ (g)\ b \land b\ (f)\ a \rangle \\
\Leftrightarrow \\
Trivial
\end{matrix}
\end{equation}
$$