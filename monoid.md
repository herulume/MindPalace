# Monoid

- $(M, \bullet, u)$
- Set $M$ equipped with a binary operation $\bullet : M \times M \to M$ and a unit element $u$
- $\forall x,y,z \in M$ then $x \bullet (y \bullet z) = (x \bullet y) \bullet z$ and $u \bullet x = x = x \bullet u$

- Sometimes called a [[semi-group]] with a unit

## Monoid as a [[category]]

Given a monoid $(M, \bullet, u)$

- Objects: One single object (doesn't matter what this object is)
- Morphisms: $\forall m \in M$
- Composition: $\bullet$
- Identity morphism: $u$

- A [[functor]] between two monoids (as categories) is a monoid [[homomorphism]]
