# My notes on Thinking with Types

The best book about type level programming I have found.

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

### Sum, Product and Exponential Types

### Sum Types

The cardinality of a sum type is the sum of the cardinalities of its constructors.

The canonical sum type is `Either a b`.

```haskell
data Either a b = Left a | Right b
data Maybe a = Nothing | Just a

-- |Either| = |a| + |b|
-- |Either Bool Spin| = |Bool| + |Spin| = 2 + 2 = 4

-- |Maybe a| = |Nothing| + |a| = 1 + |a|
-- |Maybe Bool| = |Nothing| + |Bool| = 1 + 2 = 3
```

`Either Unit Bool` is isomorphic to `Maybe Bool`, existing 3 unique isomorphisms.

```haskell
-- |Either Unit Bool| = |Unit| + |Bool| = 1 + 2 = 3
-- |Maybe Bool| = |Nothing| + |Bool| = 1 + 2 = 3
```

We can think of the void type as being an identity for sum types (`a + Void = a`).

```haskell
sumUnitTo :: Either a Void -> a
sumUnitTo (Left a) = a
sumUnitTo (Right v) = absurd v -- bluff

sumUnitFrom :: a -> Either a Void
sumUnitFrom = Left
```

### Product Types

Product types are dual to sum types.

The cardinality of a product type is the product of the cardinalities of its constructors.

The canonical product type is `(a, b)`

```haskell
data MixedFraction a =
  Fraction
  { mixedBit    :: Word8
  , numerator   :: a
  , denominator :: a
  }

-- |(a, b)| = |a| * |b|
-- |(Bool, Unit)| = |Bool| * |Unit| = 2 * 1 = 2

-- |MixedFraction a| = |Word8| x |a| x |a| = 256 x |a| x |a|
-- |MixedFraction Bool| = |Word8| x |Bool| x |Bool| = 256 x 2 x 2 = 1024
```

We can prove `a x 1 = a` by showing an isomorphism between `(a, Unit)` and `a`.

```haskell
-- |(a, b)| = |a| x |b|
-- |()| = 1
-- |(a, Unit) = |a| x 1
-- |a| x 1 == |a|

prodUnitTo :: a -> (a, Unit)
prodUnitTo a = (a, ())

prodUnitFrom :: (a, Unit)) -> a
prodUnitFrom (a, _) = a
```

We can think of the unit type as being an identity for product types (`a x Unit = a`).

### Functions

The cardinality of a function is the result's cardinality to the input's cardinality power.

```haskell
-- |a -> b| =|b| x |b| x |b| x ... x |b| = |b|^|a|

-- |Bool -> Bool| = 2^2 = 4
-- id, not, const True, const False

-- Either Bool (Bool, Maybe Bool) -> Bool`
-- |Bool| ^ (|Bool| + (|Bool| x (|Nothing| + |Bool|)))
-- 2 ^ (2 + (2 x (1 + 2)))
-- 2 ^ 8
-- 256
```

### Example: Tic-Tac-Toe

Naive implementation:

```haskell
data TicTacToe a = TicTacToe
  { topLeft      :: a
  , topCenter    :: a
  , topRight     :: a
  , centerLeft   :: a
  , centerCenter :: a
  , centerRight  :: a
  , bottomLeft   :: a
  , bottomCenter :: a
  , bottomRight  :: a
  }

emptyBoard :: TicTacToe (Maybe a)
emptyBoard = TicTacToe
    Nothing Nothing Nothing
    Nothing Nothing Nothing
    Nothing Nothing Nothing
```

We can analyse TicTacToe's cardinality.

```haskell
-- |TicTacToe a| = |a|^9 == |a|^(3 x 3)
-- TicTacToe is isomorphic to (|3|, |3|) -> a
```

Due to the isomorphism, we can represent the board as:

```haskell
data Three = One | Two | Three

data TicTacToe a = TicTacToe
  { board :: Three -> Three -> a
  }

emptyBoard :: TicTacToe (Maybe a)
emptyBoard = TicTacToe $ const $ const Nothing
```

# The Curry-Howard Isomorphism

The Curry-Howard isomorphism loosely states that types correspond to theorems and its values correspond to proofs of that theorem.

Algebra | Logic | Types
------- | ----- | ------
a + b | a \\/ b | Either a b
a x b | a /\\ b | (a, b)
b^a | a => b | a -> b
a = b | a <=> b | isomorphism
0 | \_\|\_ | Void
1 | inverted \_\|\_ | Unit
----

Consider `a^1 = a`. It corresponds to an isomorphism between `() -> a` and `a`.
There is no distinction between having a value or a pure program that computes it.

A more complicated example:


```haskell
-- Prove: a^b x a^c = a^(b + c)

-- a^b x a^c = (b -> a, c -> a)
-- a^(b + c) = Either b c -> a

from :: (b -> a, c -> a) -> (Either b c -> a)
from (f, _) (Left x) = f x
from (_, g) (Right y) = g y

to :: (Either b c -> a) -> (b -> a, c -> a)
to f = (f . Left, f . Right)
```


Curry and uncurry:

```haskell
-- Prove: a^(a x c) = (a^b)^c

-- a^(b x c) = (b, c) -> a
-- (a ^ b)^c = b -> c -> a

uncurry :: (b -> c -> a) -> (b, c) -> a
uncurry f (y, z) = f y z

curry :: ((b, c) -> a) -> b -> c -> a
curry f y z = f (y, z)
```

### Canonical Representations

The canonical representation is known as the sum of products.

 * Sum types on the outside
 * Product types on the inside
 * Sum types are represented via `Either`
 * Product types are represented via `(,)`
 * Exception for numeric types

Examples:

```haskell
Unit

Either a b

Either (a, b) (c, d)

a -> b

(a, Int)
```

The canonical representation of `Maybe a` is `Either a ()`.

## Chapter 2 - Terms, Types and Kinds

Terms are values that we can manipulate.
Types are proofs, to the compiler, that our programs make some sense.

In type-level programming, types and kinds are analogous.
Now we manipulate types and the kinds are the proofs.

The kind system can be thought as the type system for types. So, we can think of kinds as the types of types.

Historically, `*` refers to the kind of types that have inhabitants. `TYPE` has been proposed as the new symbol.
`*` is the kind of `Int`, `Bool`, or `Maybe Char`.
What all of these types have in common is that they exist at runtime.
It's possible to have terms of type `Maybe Char` and their kind would be `*`. However, it's not possible to have terms of type `Maybe`. `Maybe` has the kind `* -> *`.
