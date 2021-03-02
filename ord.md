# Ord

A [[category]].

- Objects: Preorders ([[preorder]])
- Morphisms: Monote functions ([[monote-function]])
- Composition: Function composition
- Identity morphism: $id$

## Proofs

### Associativity
   
   trivial
   
### Identity
   
   trivial
   
### Composition is monotone
   
   - $f : A \to B$ is monotone
   - $g : B \to C$ is monotone
   - $a \leq_A a' \implies f(a) \leq_B (a') \implies g(f(a) \leq_C g(f(a')) \implies g \circ f$ is monotone
