vi# Boolean Algebra — Digital Circuits & Computer Engineering

## Course context

Boolean Algebra is a core foundation of digital circuits. It provides the mathematical language used to describe, analyze, and simplify logic circuits.

The main connection is:

```text
Truth Tables → Boolean Expressions → Boolean Algebra → Logic Gates → Digital Circuits
```

---

# 1. What is Boolean Algebra?

**Boolean Algebra** is a mathematical system in which variables have only two possible values:

```text
0 or 1
```

In digital electronics:

```text
0 = LOW / FALSE
1 = HIGH / TRUE
```

Boolean Algebra was developed by **George Boole**.

Unlike ordinary algebra, Boolean operations follow special rules.

For example:

```text
Ordinary algebra: 1 + 1 = 2
Boolean algebra:  1 + 1 = 1
```

Here `+` means **OR**, not normal arithmetic addition.

---

# 2. Boolean variables

A Boolean variable can contain only `0` or `1`.

Examples:

```text
A = 0
B = 1
C = 0
```

Variables may represent:

- Digital inputs
- Digital outputs
- Switch states
- Sensor states
- Control signals
- Processor signals

---

# 3. Boolean constants

There are two constants:

```text
0
1
```

They can represent:

```text
0 → FALSE / LOW / OFF
1 → TRUE / HIGH / ON
```

The actual physical voltage represented by HIGH or LOW depends on the digital technology.

---

# 4. Basic Boolean operators

| Operation | Common notation | Logic gate |
|---|---|---|
| AND | `·` or `AB` | AND |
| OR | `+` | OR |
| NOT | `'` or overbar | NOT |

Examples:

```text
AND: AB
OR:  A+B
NOT: A'
```

---

# 5. AND operation

AND gives `1` only when **all inputs are 1**.

```text
Y = AB
```

Truth table:

| A | B | Y=AB |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

Think:

> AND means both conditions must be true.

---

# 6. OR operation

OR gives `1` when **at least one input is 1**.

```text
Y = A+B
```

| A | B | Y=A+B |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

Think:

> OR means one or more conditions are true.

---

# 7. NOT operation

NOT reverses a Boolean value.

```text
Y = A'
```

| A | A' |
|---|---:|
| 0 | 1 |
| 1 | 0 |

Other notation includes:

```text
A'
Ā
¬A
```

---

# 8. Operator precedence

Use this order when evaluating Boolean expressions:

```text
1. Parentheses
2. NOT
3. AND
4. OR
```

For example:

```text
Y = A + BC
```

means:

```text
Y = A + (BC)
```

Example:

```text
A=0, B=1, C=1

BC = 1
Y = 0+1
Y = 1
```

---

# 9. Boolean expressions

A Boolean expression combines variables, constants, and operators.

Examples:

```text
A+B
AB
A'B
A+BC
(A+B)(C+D)
A'B+CD
```

Example:

```text
Y=A'B+C
```

contains NOT, AND, and OR operations.

---

# 10. Fundamental Boolean laws

These laws are essential for exams and circuit simplification.

## Identity laws

```text
A+0=A
A·1=A
```

OR with 0 changes nothing.

AND with 1 changes nothing.

---

## Dominance / Null laws

```text
A+1=1
A·0=0
```

OR with 1 is always 1.

AND with 0 is always 0.

---

## Idempotent laws

```text
A+A=A
AA=A
```

Repeating the same Boolean variable does not change the result.

---

## Complement laws

```text
A+A'=1
AA'=0
```

A variable OR its complement is always 1.

A variable AND its complement is always 0.

Truth table:

| A | A' | A+A' | AA' |
|---|---|---:|---:|
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |

---

## Involution law

```text
(A')'=A
```

NOT applied twice returns the original variable.

---

## Commutative laws

```text
A+B=B+A
AB=BA
```

The order can be changed.

---

## Associative laws

```text
(A+B)+C=A+(B+C)
(AB)C=A(BC)
```

Grouping can be changed.

---

# 11. Distributive laws

Boolean Algebra has two important distributive laws.

### AND over OR

```text
A(B+C)=AB+AC
```

### OR over AND

```text
A+BC=(A+B)(A+C)
```

The second identity is especially important because it differs from the usual form remembered from ordinary algebra.

---

# 12. Absorption laws

```text
A+AB=A
```

and:

```text
A(A+B)=A
```

Example:

```text
A+AB
=A(1+B)
=A·1
=A
```

Absorption laws are extremely useful when simplifying circuits.

---

# 13. De Morgan's laws

De Morgan's laws are among the most important Boolean identities.

### First law

```text
(A+B)'=A'B'
```

Meaning:

> NOT of OR becomes AND of the NOTs.

### Second law

```text
(AB)'=A'+B'
```

Meaning:

> NOT of AND becomes OR of the NOTs.

Memorize:

```text
(A+B)' = A'B'
(AB)'  = A'+B'
```

---

# 14. De Morgan's laws with three variables

They also work with more variables:

```text
(A+B+C)'=A'B'C'
```

and:

```text
(ABC)'=A'+B'+C'
```

General rule:

> When a NOT moves across a group, change AND ↔ OR and complement every variable.

---

# 15. De Morgan truth-table proof

For:

```text
(A+B)' = A'B'
```

| A | B | A+B | (A+B)' | A' | B' | A'B' |
|---|---|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 | 0 | 0 | 0 |

The two columns are identical, so the expressions are equivalent.

---

# 16. Boolean duality

The **principle of duality** says that a valid Boolean identity has a corresponding dual.

To form the dual:

```text
+ ↔ ·
0 ↔ 1
```

Variables remain unchanged.

Example:

```text
A+0=A
```

Dual:

```text
A·1=A
```

Another:

```text
A+1=1
```

Dual:

```text
A·0=0
```

---

# 17. Simplifying Boolean expressions

Boolean simplification means reducing an expression to an equivalent but simpler expression.

Example:

```text
Y=A+AB
```

Using absorption:

```text
Y=A
```

The simplified circuit requires less logic.

---

# 18. Simplification examples

## Example 1

```text
Y=A+AB
```

Absorption:

```text
Y=A
```

---

## Example 2

```text
Y=A+A'
```

Complement law:

```text
Y=1
```

---

## Example 3

```text
Y=AA'
```

Complement law:

```text
Y=0
```

---

## Example 4

```text
Y=AB+AB'
```

Factor A:

```text
Y=A(B+B')
```

Complement:

```text
B+B'=1
```

Therefore:

```text
Y=A
```

---

## Example 5

```text
Y=A+A'B
```

Use the identity:

```text
A+A'B=A+B
```

Therefore:

```text
Y=A+B
```

---

## Example 6

```text
Y=(A+B)(A+B')
```

Using:

```text
(X+Y)(X+Z)=X+YZ
```

we get:

```text
Y=A+BB'
```

Since:

```text
BB'=0
```

then:

```text
Y=A
```

---

# 19. Consensus theorem

A useful Boolean identity is:

```text
AB+A'C+BC=AB+A'C
```

The term:

```text
BC
```

is redundant.

The theorem can remove unnecessary logic from a circuit.

---

# 20. Boolean Algebra and logic gates

Every basic Boolean operation corresponds to a logic gate.

```text
AB  → AND gate
A+B → OR gate
A'  → NOT gate
```

Therefore, a Boolean expression can describe a digital circuit.

For example:

```text
Y=AB+C
```

means:

1. AND A and B.
2. OR that result with C.

---

# 21. NAND and NOR

NAND:

```text
Y=(AB)'
```

NOR:

```text
Y=(A+B)'
```

Using De Morgan:

```text
(AB)'=A'+B'
```

and:

```text
(A+B)'=A'B'
```

NAND and NOR are called **universal gates** because complete logic circuits can be built using only NAND gates or only NOR gates.

---

# 22. XOR

XOR means **exclusive OR**.

It outputs 1 when the inputs are different.

| A | B | A⊕B |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Boolean expression:

```text
A⊕B=A'B+AB'
```

XOR is very important in adders and digital arithmetic.

---

# 23. XNOR

XNOR is the complement of XOR.

It outputs 1 when inputs are equal.

```text
A XNOR B = A'B'+AB
```

| A | B | XNOR |
|---|---|---:|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

---

# 24. Literals

A **literal** is a variable or its complement.

Examples:

```text
A
B
C'
```

In:

```text
AB'C
```

there are three literals:

```text
A, B', C
```

---

# 25. Sum of Products (SOP)

SOP means:

> **Sum of Products**

In Boolean terminology:

```text
Sum → OR
Product → AND
```

Example:

```text
Y=AB+A'C+BC
```

The AND terms are:

```text
AB
A'C
BC
```

and they are ORed together.

General structure:

```text
AND terms → OR
```

---

# 26. Product of Sums (POS)

POS means:

> **Product of Sums**

Example:

```text
Y=(A+B)(A'+C)(B+C)
```

Each parenthesized expression is an OR term.

The terms are ANDed together.

General structure:

```text
OR terms → AND
```

---

# 27. Minterms

A **minterm** is an AND term containing every variable exactly once.

For two variables:

```text
A'B'
A'B
AB'
AB
```

Truth table:

| A | B | Minterm |
|---|---|---|
| 0 | 0 | A'B' |
| 0 | 1 | A'B |
| 1 | 0 | AB' |
| 1 | 1 | AB |

Minterms are useful for deriving Boolean expressions from truth tables.

---

# 28. Minterm numbering

For variables A and B:

| A | B | Binary | Minterm |
|---|---|---|---|
| 0 | 0 | 00 | m₀ |
| 0 | 1 | 01 | m₁ |
| 1 | 0 | 10 | m₂ |
| 1 | 1 | 11 | m₃ |

Therefore:

```text
A'B' = m₀
A'B  = m₁
AB'  = m₂
AB   = m₃
```

---

# 29. Maxterms

A **maxterm** is an OR term containing every variable exactly once.

For two variables, examples are:

```text
A+B
A+B'
A'+B
A'+B'
```

Maxterms are mainly used in canonical POS expressions.

---

# 30. From a truth table to Boolean expression

Suppose:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Find the rows where Y = 1:

```text
01
10
```

Convert each to a minterm:

```text
01 → A'B
10 → AB'
```

OR them:

```text
Y=A'B+AB'
```

This is XOR.

---

# 31. Canonical SOP

Canonical SOP is formed by ORing all minterms where the output is 1.

For the XOR example:

```text
Y=A'B+AB'
```

can be written as:

```text
Y=Σm(1,2)
```

This means:

> Sum of minterms 1 and 2.

---

# 32. Canonical POS

Canonical POS is formed by ANDing all maxterms where the output is 0.

For XOR, output is 0 for:

```text
00
11
```

Therefore:

```text
Y=ΠM(0,3)
```

This means:

> Product of maxterms 0 and 3.

---

# 33. Number of truth-table rows

For `n` Boolean variables:

```text
Number of rows = 2ⁿ
```

Examples:

```text
1 variable → 2 rows
2 variables → 4 rows
3 variables → 8 rows
4 variables → 16 rows
5 variables → 32 rows
```

This is an important exam formula.

---

# 34. Boolean equivalence

Two Boolean expressions are equivalent if they give the same output for every possible input combination.

For example:

```text
A+AB=A
```

Algebraic proof:

```text
A+AB
=A(1+B)
=A·1
=A
```

Therefore the expressions are equivalent.

You can also verify equivalence using a truth table.

---

# 35. Truth-table verification

Check:

```text
A+AB=A
```

| A | B | AB | A+AB | A |
|---|---|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |

The final two columns are identical.

Therefore:

```text
A+AB=A
```

---

# 36. Boolean Algebra and circuit simplification

Suppose a circuit implements:

```text
Y=AB+AB'
```

Simplify:

```text
Y=A(B+B')
```

```text
Y=A·1
```

```text
Y=A
```

The original circuit can therefore be replaced by a much simpler connection.

This demonstrates why Boolean Algebra is important in digital design.

---

# 37. Why simplify circuits?

Boolean simplification can reduce:

- Number of gates
- Number of gate inputs
- Propagation delay
- Hardware complexity
- Power consumption
- Physical circuit area
- Cost

Therefore Boolean Algebra is both a mathematical and practical digital-design tool.

---

# 38. Karnaugh maps

A **Karnaugh map (K-map)** is a graphical method for simplifying Boolean functions.

Typical process:

```text
Truth table
    ↓
Boolean function
    ↓
Karnaugh map
    ↓
Simplified Boolean expression
    ↓
Simplified circuit
```

Before studying K-maps, make sure you understand:

- Boolean laws
- Truth tables
- Minterms
- Maxterms
- SOP
- POS

---

# 39. Common exam mistakes

## Mistake 1 — Treating + as ordinary addition

Wrong:

```text
1+1=2
```

Correct:

```text
1+1=1
```

because Boolean `+` means OR.

## Mistake 2 — Forgetting implicit AND

```text
ABC
```

means:

```text
A·B·C
```

## Mistake 3 — Incorrect De Morgan's law

Wrong:

```text
(A+B)'=A'+B'
```

Correct:

```text
(A+B)'=A'B'
```

Remember:

```text
NOT(OR) → AND of NOTs
NOT(AND) → OR of NOTs
```

## Mistake 4 — Confusing complements

Remember:

```text
A+A'=1
AA'=0
```

## Mistake 5 — Ignoring precedence

```text
A+BC
```

means:

```text
A+(BC)
```

not:

```text
(A+B)C
```

---

# 40. Simplification strategy for exams

When simplifying:

### Step 1 — Apply parentheses and De Morgan where needed

Look for expressions such as:

```text
(A+B)'
(AB)'
```

### Step 2 — Look for complements

```text
A+A'=1
AA'=0
```

### Step 3 — Use identity and dominance

```text
A+0=A
A·1=A
A+1=1
A·0=0
```

### Step 4 — Remove repetition

```text
A+A=A
AA=A
```

### Step 5 — Try absorption

```text
A+AB=A
A(A+B)=A
```

### Step 6 — Factor common terms

```text
AB+AC=A(B+C)
```

### Step 7 — Verify

Use a truth table if necessary.

---

# 41. Essential Boolean laws — master table

| Law | Identity |
|---|---|
| Identity | `A+0=A` |
| Identity | `A·1=A` |
| Dominance | `A+1=1` |
| Dominance | `A·0=0` |
| Idempotent | `A+A=A` |
| Idempotent | `AA=A` |
| Complement | `A+A'=1` |
| Complement | `AA'=0` |
| Involution | `(A')'=A` |
| Commutative | `A+B=B+A` |
| Commutative | `AB=BA` |
| Associative | `(A+B)+C=A+(B+C)` |
| Associative | `(AB)C=A(BC)` |
| Distributive | `A(B+C)=AB+AC` |
| Distributive | `A+BC=(A+B)(A+C)` |
| Absorption | `A+AB=A` |
| Absorption | `A(A+B)=A` |
| De Morgan | `(A+B)'=A'B'` |
| De Morgan | `(AB)'=A'+B'` |

---

# 42. Exam practice — Level 1

1. What is Boolean Algebra?
2. What values can a Boolean variable have?
3. What does `+` represent?
4. What does `·` represent?
5. What does `A'` represent?
6. Write the truth table for AND.
7. Write the truth table for OR.
8. Write the truth table for NOT.
9. What is `A+0`?
10. What is `A·1`?
11. What is `A+1`?
12. What is `A·0`?
13. What is `A+A`?
14. What is `AA`?
15. What is `A+A'`?
16. What is `AA'`?

---

# 43. Exam practice — Level 2

Simplify:

17. `A+AB`

18. `A(A+B)`

19. `AB+AB'`

20. `A+A'B`

21. `A+A'`

22. `AA'`

23. `(A+B)'`

24. `(AB)'`

25. `A+AB+AC`

26. `A(B+C)`

27. `(A+B)(A+B')`

28. `AB+A'C+BC`

---

# 44. Exam practice — Level 3

29. Prove:

```text
A+AB=A
```

30. Prove:

```text
A+A'B=A+B
```

31. Simplify:

```text
Y=AB+A'C+BC
```

32. Simplify:

```text
Y=(A+B)(A'+C)
```

33. Write the Boolean expression for XOR.

34. Write the Boolean expression for XNOR.

35. How many rows are required for a truth table with 4 variables?

36. Derive the Boolean expression for XOR from its truth table.

37. Explain the difference between SOP and POS.

38. Explain why NAND and NOR are called universal gates.

---

# 45. Answers

### 9

```text
A+0=A
```

### 10

```text
A·1=A
```

### 11

```text
A+1=1
```

### 12

```text
A·0=0
```

### 13

```text
A+A=A
```

### 14

```text
AA=A
```

### 15

```text
A+A'=1
```

### 16

```text
AA'=0
```

### 17

```text
A+AB=A
```

### 18

```text
A(A+B)=A
```

### 19

```text
AB+AB'
=A(B+B')
=A
```

### 20

```text
A+A'B=A+B
```

### 21

```text
A+A'=1
```

### 22

```text
AA'=0
```

### 23

```text
(A+B)'=A'B'
```

### 24

```text
(AB)'=A'+B'
```

### 25

```text
A+AB+AC
=A(1+B+C)
=A
```

### 26

```text
A(B+C)=AB+AC
```

### 27

```text
(A+B)(A+B')
=A+BB'
=A
```

### 28

```text
AB+A'C+BC=AB+A'C
```

### 33

```text
A⊕B=A'B+AB'
```

### 34

```text
XNOR=A'B'+AB
```

### 35

```text
2⁴=16 rows
```

---

# 46. Mini exam

Try these without looking at the answers.

### Question 1

Simplify:

```text
Y=A+AB
```

### Question 2

Simplify:

```text
Y=AB+AB'
```

### Question 3

Apply De Morgan:

```text
Y=(A+B+C)'
```

### Question 4

Apply De Morgan:

```text
Y=(ABC)'
```

### Question 5

Simplify:

```text
Y=A+A'B
```

### Question 6

How many rows does a truth table with 5 variables have?

### Question 7

Write XOR in Boolean form.

### Question 8

What is the difference between SOP and POS?

### Question 9

Name the two universal gates.

### Question 10

Why is Boolean simplification useful?

## Mini exam answers

```text
1. A
2. A
3. A'B'C'
4. A'+B'+C'
5. A+B
6. 2⁵ = 32
7. A'B+AB'
8. SOP = OR of AND terms; POS = AND of OR terms
9. NAND and NOR
10. It can reduce gates, delay, power, area, complexity and cost.
```

---

# 47. Final exam cheat sheet

## Basic operations

```text
AND → AB
OR  → A+B
NOT → A'
```

## Core laws

```text
A+0=A
A·1=A

A+1=1
A·0=0

A+A=A
AA=A

A+A'=1
AA'=0

(A')'=A
```

## Distributive

```text
A(B+C)=AB+AC
A+BC=(A+B)(A+C)
```

## Absorption

```text
A+AB=A
A(A+B)=A
```

## De Morgan

```text
(A+B)'=A'B'
(AB)'=A'+B'
```

## XOR

```text
A⊕B=A'B+AB'
```

## XNOR

```text
XNOR=A'B'+AB
```

## Truth-table rows

```text
n variables → 2ⁿ rows
```

## SOP

```text
OR of AND terms
```

## POS

```text
AND of OR terms
```

## Universal gates

```text
NAND
NOR
```

---

# 48. What you should be able to do before moving on

- [ ] Define Boolean Algebra.
- [ ] Explain Boolean variables and constants.
- [ ] Explain AND, OR and NOT.
- [ ] Construct truth tables.
- [ ] Evaluate Boolean expressions.
- [ ] Apply operator precedence.
- [ ] Use identity laws.
- [ ] Use dominance laws.
- [ ] Use idempotent laws.
- [ ] Use complement laws.
- [ ] Use involution.
- [ ] Use commutative laws.
- [ ] Use associative laws.
- [ ] Use distributive laws.
- [ ] Use absorption laws.
- [ ] Apply De Morgan's laws.
- [ ] Explain Boolean duality.
- [ ] Simplify Boolean expressions.
- [ ] Explain NAND and NOR.
- [ ] Write XOR and XNOR expressions.
- [ ] Understand SOP and POS.
- [ ] Understand minterms and maxterms.
- [ ] Derive a Boolean expression from a truth table.
- [ ] Verify Boolean equivalence using a truth table.
- [ ] Explain why circuit simplification is useful.

---

# 49. Connection to the next HKR topics

The concepts connect as:

```text
NUMBER SYSTEMS
      ↓
Binary 0 and 1
      ↓
BOOLEAN ALGEBRA
      ↓
Boolean variables and expressions
      ↓
TRUTH TABLES
      ↓
Logic functions
      ↓
LOGIC GATES
      ↓
COMBINATIONAL NETWORKS
      ↓
Adders, subtractors, MUX, DEMUX, encoders, decoders
      ↓
SEQUENTIAL NETWORKS
      ↓
Flip-flops, registers, counters
      ↓
PROCESSORS + MEMORY + I/O
```

## Key idea

> **Boolean Algebra lets us mathematically describe and simplify the logic performed by digital circuits.**

