# Natural Transformation

- Let $F,G : C \to D$ be two functors [[functor]].
- A natural transformation $\eta : F \Rightarrow G$  is a family of morphisms ([[morphism]]) in $D$ indexed by objects $A$ of $C$

$\forall A \in Ob(C)\ \{\ \eta_A : FA \to GA\ \}$

such that $\forall f : A \to B$

$Gf \circ \eta_A = \eta_B \circ Ff$

or as a diagram

![[./imgs/nattrans.png]]


This condition is called *naturality*.
