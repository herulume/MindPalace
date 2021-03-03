# Kleisli category

A [[category]].

Given a [[monad]] $T$ on some category $C$:

- Objects: $Ob(C)$
- Morphisms: $X \to Y$ for every $X \to T(Y)$ in $C$ ($Hom_C(X,TY)$)
- Composition: $g \circ_T f = \mu \circ Tg \circ f$
- Identity morphism: $\eta$
