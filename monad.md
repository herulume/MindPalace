# Monad

- A monad over a [[category]] $C$ is a triple $(T,\eta ,\mu)$
- $T$ is an [[endofunctor]] on $C$
- $\eta : Id_C \Rightarrow T$
- $\mu : T^2 \Rightarrow T$

Such that the following diagrams commute:

![[./imgs/monaddefcommute.png]]

- $\eta$ is the *unit*
- $\mu$ is the *multiplication*
- Both are natural transformations ([[natural-transformation]])

## Monad from adjunctions

- Let $F$ and $G$ be functors ([[functor]])
- For each $A \in Ob(C)$ and $B \in Ob(D)$ there's a bijection $\theta_{A,B} : C(A, GB) \cong D(FA,B)$ natural in $A,B$

- A monad can be built from the adjunction $F \dashv G$
- $T = G \circ F$
- $\eta_A : A \to GFA = \theta^{-1}_{A,FA}(id_{FA})$
- $\mu : GFGFA \to GFA = G(\theta_{GFA,FA}(id_{GFA}))$
