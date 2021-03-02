# Preorder

Set $A$ with a [[binary-relation]] $\leq_A$ such that $\forall a,b,c \in A$:
  - Reflexivity: $a \leq_A a$
  - Transitivity: if $a \leq_A b$ and $b \leq_A c$ then $a \leq_A c$

## Preorder as a [[category]]

Given a preorder $(A, \leq_A)$:

- Objects: $\forall a \in A$
- Morphisms: $\forall a,b \in A$ then $a \to b$ **iff** $a \leq_A b$

The transitive and reflexive conditions ensure the morphism laws hold and that there are identity arrows.

## More generally 

Any category with at most one arrow between any two objects determines a preorder.

- A [[functor]] between two preorder categories is a [[monote-function]]
- Thus, monote functions are [[homomorphism]]s between preorders
