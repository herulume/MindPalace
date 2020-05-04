# My notes on Quantum Computing For Computer Scientists

This will be a slow read.

## Introduction

### From Real Numbers to Complex Numbers

- Quantum mechanics uses complex numbers in a fundamental way
- `i = √−1` was the "imaginary" solution to the polynomial equation `x² = −1`

### From Single States to Superpositions of States

- Every object exists in a unique place and in a well-defined state
- Even when we are not looking at it
- This is only true for large objects

- A microscopic object can "be in more than one place at a time"
- We say that an object is in a "superposition"
- In some sense, it is simultaneously in more than one location at the same time
- Other familiar physical properties are also hazy

- We do not see superposition of states
- Every time we look, measure, a superposition of states, it "collapses" to a single well-defined state

### From Locality to Non-locality

- Objects are directly affected only by nearby objects or forces
- To determine why a phenomenon occurs at a certain place, one must examine all the phenomena and forces near that place
- This is called "locality"
- Quantum mechanics laws predict certain effects that work in a nonlocal manner
- Two particles can be connected, "entangled", such that an action performed on one of them can have an immediate effect on the other particle light-years away

### From Deterministic Laws to Probabilistic Laws

- To which specific state will a superposition of states collapse when it is measured?
- The laws of quantum mechanics state that we can only know the probability of the outcome

### From Certainty to Uncertainty

- There are inherent limitations to the amount of knowledge that one can ascertain about a physical system

### The Implications Of The Quantum World On Computer Science

### Architecture

- A bit can be in either one of two states (0 or 1)
- Superposition will allow a qubit to be in both states simultaneously
- Many qubits together gives us quantum registers
- A quantum computer can be in many states simultaneously
- Quantum gates manipulate qubits
- Quantum gates will have to follow the dynamics of quantum operations
- Certain quantum operations are reversible hence certain quantum gates will have to be reversible

### Algorithms

- One places a quantum computer in many states simultaneously
- This needs special care: we cannot measure the computer while it is in this superposition because measuring it would collapse it to a single position
- Algorithms start with the quantum computer in a single position
- We shall then delicately place it in a superposition of many states.
- From there, we manipulate the qubits in a specified way.
- Finally, some of the qubits are measured.
- The measurement will collapse the qubits to the desired bits, which will be our output

- Entanglement will also play a role in quantum computing
- The qubits can be entangled
- By measuring some of them, others automatically reach the desired position

## Chapter 1

### Complex Numbers

- For `x² + 1 = 0`, any possible `x²` would be positive or zero (no solution)

#### Exercise 1.1.1

Verify that the equation `x⁴ + 2x² + 1 = 0` has no solution among the real numbers.

```
x⁴ + 2x² + 1 = 0

{ u = x² }

u² + 2u + 1 = 0

{ quadratic formula }

    -2 +- √(2² - 4*1*1)
u = ----------------------
           2 * 1
     -2
u = ----  = - 1
      2

{ u = x² and u = -1 }

x² = -1
```

No solution.

#### Chapter 1 continuation

- Let us assume `x² = −1`
- `i² = −1` or `i = √−1`
- Because it is imaginary, it is denoted `i`
- Aside from its weird behavior when squared, `i` will behave just like an ordinary number
- `i³` = `i * i * i` = `i² * i` = `−1 * i` = `−i`

#### Exercise 1.1.2

Find the value of `i¹⁵`.

```
i⁰ = 1
i¹ = i
i² = -1
i³ = i² * i = -1 * i = -i
i⁴ = i² * i² = -1 * -1 = 1
i⁵ = i⁴ * i = 1 * i = i

We see a pattern...

15 `mod` 4 = 3

i¹⁵ = i³ = -i
```

#### Chapter 1 continuation

- Numbers like `2*i` (`2i`) are known as imaginary numbers
- Numbers like `3 + 5 * i` are called **complex numbers**
- A complex number is an expression: `c = a + b * i = a + bi` where `a`, `b` are real numbers
- `a` is called the real part of `c`, whereas `b` is its imaginary part
- The set of all complex numbers will be denoted as `C`

- `c1 = 3 − i` and `c2 = 1 + 4i`
- `c1 + c2` = `3 − i + 1 + 4i` = `(3 + 1) + (−1 + 4)i` = `4 + 3i`
- `c1 * c2` = `(3 − i) * (1 + 4i)` = `(3 * 1) + (3 * 4i) + (−i * 1) + (−i * 4i)` = `(3 + 4) + (−1 + 12)i` = `7 + 11i`

#### Chapter 1.1.3

Let `c1 = −3 + i` and `c2 = 2 − 4i`.
Calculate `c1 + c2` and `c1 * c2`.

```
c1 = −3 + i
c2 = 2 − 4i

c1 + c2
-3 + i + 2 - 4i
-1 - 3i
```

```
c1 = −3 + i
c2 = 2 − 4i

c1 * c2
(-3 + i) * (2 - 4i)
(-3 * 2) + (-3 * -4i) + (i * 2) + (i * -4i)
-6 + 12i + 2i + -4i²
-6 + 14i + 4
-2 + 14i
```

#### Chapter 1 continuation

- **Fundamental Theorem of Algebra**: Every polynomial equation of one variable with complex coefficients has a complex solution

#### Exercise 1.1.4

Verify that the complex number `−1 + i` is a solution for the polynomial equation `x² + 2x + 2 = 0`.

```
x² + 2x + 2 = 0

{ x = -1 + i }

(-1 + i)² + 2(-1 + i) + 2 = 0
1 - 2i + i² -2 + 2i + 2 = 0
1 + i² = 0
1 - 1 = 0
0 = 0
```

#### Programming Drill 1.1.1

Write a program that accepts two complex numbers and outputs their sum and their product.

```haskell
data Complex = C Float Float -- C Real Imaginary

sumC :: Complex -> Complex -> Complex
sumC (C r0 i0) (C r1 i1) = C (r0 + r1) (i0 + i1)

mulC :: Complex -> Complex -> Complex
mulC (C r0 i0) (C r1 i1) = C (r0*r1 - i0*i1) (r0*i1 + i0*r1)

toStr :: Complex -> String
toStr (C r i) = show r ++ " + " ++ show i ++ "*i"

main :: IO ()
main = do
    putStrLn "Input expect: C float float"
    c0 <- getC "First complex number"
    c1 <- getC "Second complex number"
    putStrLn $ "(" ++ toStr c0 ++ ") + (" ++ toStr c1 ++ ") = " ++ toStr (sumC c0 c1)
    putStrLn $ "(" ++ toStr c0 ++ ") * (" ++ toStr c1 ++ ") = " ++ toStr (mulC c0 c1)


-- lazy about errors
getC :: String -> IO Complex
getC s = do
    putStrLn s
    l <- getLine
    case words l of
      ["C", r, i] -> return $ C (read r) (read i)
      _ -> error "Wrong format: C float float"
```

### The algebra of complex numbers

- What does it mean that `i` squared is equal to `-1`

- **Two** real numbers correspond to each complex number: its real and imaginary parts
- `c |-> (a, b)`
- Real numbers are of the form `(a, 0)` (`a |-> (a, 0)`)
- Imaginary numbers are of the form `(0, b)` (`i |-> (0, i)`)

- Addition `(a1, b1) + (a2, b2)` = `(a1 + a2, b1 + b2)`
- Multiplication `(a1, b1) * (a2, b2)` = `(a1, b1)(a2, b2)` = `(a1a2 − b1b2, a1b2 + a2b1)`

```
c
(a, b)
(a, 0) + (0, b)
(a, 0) + (b, 0) * (0, 1)
a + bi
```

- `i` is just `(0, 1)`
- A complex number is nothing more than an ordered pair of real numbers
- The strange multiplication rule makes sense when approaching it by another model

#### Exercise 1.2.1

Let `c1 = (−3, −1)` and `c2 = (1, −2)`. Calculate their product.

```
c1 * c2
(-3, -1)(1, -2)
(-3 - 2, 6 - 1)
(-5, 5)
-5 + 5i
```
#### Chapter 1 Continuation

- Addition and multiplication are **commutative** and **associative**

#### Exercise 1.2.2

Verify that multiplication of complex numbers is associative.

```
(c1 * c2) * c3
((a1, b1)(a2, b2))(a3, b3)
(a1a2 − b1b2, a1b2 + a2b1)(a3, b3)
((a1a2 - b1b2)a3 - (a1b2 + a2b1)b3, (a1a2 - b1b2)b3 + a3(a1b2 + a2b1))
(a1a2a3 - b1b2a3 - a1b2b3 - a2b1b3, a1a2b3 - b1b2b3 + a3a1b2 + a3a2b1)
(a1a2a3 - a1b2b3 - b1a2b3 - b1a3b2, a1a2b3 + a1a3b2 + a2a3b1 - b2b3b1)
(a1(a2a3 - b2b3) - b1(a2b3 + a3b2), a1(a2b3 + a3b2) + (a2a3 - b2b3)b1)
(a1, b1)(a2a3 - b2b3, a2b3 + a3b2)
(a1, b1)((a2, b2)(a3, b3))
c1 * (c2 * c3)
```

Bonus: commutative

```
c1 * c2
(a1, b1)(a2, b2)
(a1a2 − b1b2, a1b2 + a2b1)
(a2a1 - b2b1, a2b1 + a1b2
(a2, b2)(a1, b1)
c2 * c1
```

#### Chapter 1 continuation

- Multiplication **distributes** over addition (`c1 * (c2 + c3)` = `(c1 * c2) + (c1 * c3)`)
- Subtraction is defined component wise: `c1 − c2` = `(a1, b1) − (a2, b2)` = `(a1 − a2, b1 − b2)`
- Division is not straightforward. We look at it as the inverse of multiplication.

```
         (a1, b1)
(x, y) = --------
         (a2, b2)

(a1, b1) = (x, y)(a2, b2)
(a1, b1) = (a2x - b2y, a2y + b2x)

(1) a1 = a2x - b2y
(2) a2 = a2y + b2x

We need to solve this pair of equations for x and y

Multiply both sides of (1) by a2 and both sides of (2) by b2

(1') a1a2 = a2²x - b2a2y
(2') b1b2 = a2b2y + b2²x

Adding them we get

a1a2 + b1b2 = (a2² + b2²)x

Solving for x

    a1a2 + b1b2
x = -----------
     a2² + b2²

Multiplying (1) and (2) by b2 and -a2 respectively, and then adding them, solving for y

    a2b1 - a1b2
y = -----------
     a2² + b2²
```

- Division: `(a1 + b1i) / (a2 + b2i)` = `(a1a2 + b1b2)/(a2² + b2²)` + `(a2b1 - a1b2)/(a2² + b2²)` * `i`
- Both `x` and `y` are calculated with the same denominator
- This quantity has a meaning (seen later on)
