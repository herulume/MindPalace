# Adjunction

- A relationship between functors ([[functor]])
- Relates categories ([[category]]) in a "weak" way (equivalence)

## Notation

$F \dashv G$

- $F$ is the left adjoint of $G$
- $G$ is the right adjoint of $F$

## Definition via Hom-set adjunction

- Let $F : D \to C$ and $G:C \to D$ be functors

- $\forall X \in Ob(C)$ $\forall Y \in Ob(D)$ there's a bijection between the respective morphisms sets

$hom_C(FY, X) \cong hom_D(Y, GX)$

such that this bijections are natural in $X$ and $Y$.

See [[hom-functor]].

### Meaning of natural

Natural here means that there are natural-isomorphisms ([[isomorphism]]) between:

$C(F-,X) : D \to Set$
$D(-, GX) : D \to Set$
For a fixed $X \in C$

And between

$C(FY, -) : C \to Set$
$D(Y, G-) : C \to Set$
For a fixed $Y \in D$

## Definition via unit and counit

- Let $F : D \to C$ and $G:C \to D$ be functors
- Let $\epsilon : FG \to 1_C$ (counit) and $\eta : 1_D \to FG$ (unit) be natural-transformations ([[natural-transformation]])

such that

$1_F = \epsilon F \circ F\eta$
$1_G = G\epsilon \circ \eta G$

- For each $X \in G$ and $Y \in D$

$1_{FY} = \epsilon FY \circ F(\eta Y)$
$1_{GX} = G(\epsilon X) \circ \eta GX$
