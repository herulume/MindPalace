# My notes on Thinking with Types

## Chapter 1 - The Algebra Behind Types

### Isomorphisms and cardinalities

We can associate each type with its cardinality.

In this context, the cardinality is the number of inhabitants a type has minus bottoms (`_|_`).
We will use the following notation: `|Type| = #{inhabitants}`

```haskell
-- |Void| = 0
-- Inhabitants = { }
data Void

-- |Unit| = 1
-- Inhabitants = { () }
data Unit = ()

-- |Bool| = 2
-- Inhabitants = { True, False }
data Bool = True | False
```

If two types have the same cardinality, they are isomorphic.

A pair of functions, `from` and `to`, witness an isomorphism in the following way:

```haskell
to :: s -> t
from :: t -> s

-- to . from = id
-- from . to = id
```

Intuitively, if two types have the same cardinality, it is possible to define a one-to-one map between their inhabitants.

An isomorphism between `t` and `s` is proof that for all intents and purposes, `t` and `s` are the same thing.

```haskell
data Spin = Up | Down
data Bool = True | False

-- Isomorphism 1
toSpin1 :: Bool -> Spin
toSpin1 True  = Up
toSpin1 False = Down

fromSpin1 :: Spin -> Bool
fromSpin1 Up   = True
fromSpin1 Down = False

-- Isomorphism 2
toSpin2 :: Bool -> Spin
toSpin2 True  = Down
toSpin2 False = Up

fromSpin2 :: Spin -> Bool
fromSpin2 Up   = False
fromSpin2 Down = True
```

For any two types with cardinality `n` there are `n!` unique isomorphisms.
