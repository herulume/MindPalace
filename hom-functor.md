# Hom-Functor

A special [[functor]].

## Covariant hom-functor
- Let $C$ be a [[category]]
- $\forall A \in Ob(C)$ $C(A,-) : C \to Set$ is defined as
  - Objects: $C(A,-)(B) = C(A,B) = B^A$
  - Arrows: $C(A,-)(f : B \to C) = C(A,f) = g \mapsto f \circ g$
    - $C(A, f) : C(A, B) \to C(A, C) = (A \to B) \to (A \to C)$
    - C(A, f) g a = f (g a) (haskell like notation)

## Contravariant hom-functor
- Let $C$ be a [[category]]
- $\forall A \in Ob(C)$ $C(-,A) : C^{Op} \to Set$ is defined as
  - Objects: $C(-,A)(B) = C(B,A) = A^B$
  - Arrows: $C(-,A)(h : C \to B) = C(h,A) = g \mapsto g \circ h$
    - $C(h, A) : C(B, A) \to C(C, A) = (B \to A) \to (C \to A)$
    - C(A, h) g a = h (h a) (haskell like notation)

## Bivariant hom-functor
- Let $C$ be a [[category]]
- $C(-,-) : C^{Op} \times C \to Set$ is defined as
  - Objects: $C(-,-)(A \times B) = C(A, B) = B^A$
  - Arrows : $C(-,-)(A \times B \to A' \times B') = C(A \times B) \to (A' \times B') = g \mapsto h \circ g \circ f_{op}$
    + $f : A \to A'$ $h : B \to B'$
    + $C(f, h) : C(A \times B) \to (A' \times B') = (A \to B) \to (A' \to B')$
      - C(f, h) g a' = h (g (f_op a'))  (haskell like notation)

## Commutative diagram
- $f : B \to B'$
- $h : A \to A'$

![[./imgs/homfunctor.png]]
