# Isomorphism

Given a category $C$, a [[morphism]] $f : A \to B$ is an isomorphism if there's an arrow $g : B \to A$ such that:
1. $g \circ f = 1_A$
2. $f \circ g = 1_B$

- Inverse are unique, thus $g = f^{-1}$ is common notation

- $A$ is isomorphic to $B$, $A \cong B$, if there exists an isomorphism between them

* Uniqueness proof
- $f : A \to B$
- $f' : A \to B$
- $g : B \to A$

$$
\begin{equation}
\begin{matrix}
f = f \\
\Leftrightarrow \{\ 1_A\ \} \\
f = f \circ 1_A \\
\Leftrightarrow \{\ 1_A = g \circ f'\ by\ assumption\ \} \\
f = f \circ (g \circ f') \\
\Leftrightarrow \{\ (f \circ g) \circ f' = f \circ (g \circ f') \} \\
f = (f \circ g) \circ f' \\
\Leftrightarrow \{\ 1_B = f \circ g\ by\ assumption\ \} \\
f = 1_B \circ f' \\
\Leftrightarrow \{\ 1_B\ \} \\
f = f' \\
\end{matrix}
\end{equation}
$$