# Truth Tables — Digital Circuits & Computer Engineering

## Course context

A **truth table** is a systematic table used to show the output of a Boolean expression or digital logic circuit for **every possible combination of input values**.

Truth tables are one of the most important tools in digital logic because they connect:

```text
Boolean Algebra
      ↓
Logic Gates
      ↓
Truth Tables
      ↓
Digital Circuits
```

They are used to:

- Understand logic gates
- Evaluate Boolean expressions
- Design combinational circuits
- Verify Boolean identities
- Derive Boolean expressions
- Analyze adders, subtractors, MUX, DEMUX, encoders, decoders and comparators
- Check whether two circuits are equivalent

---

# 1. What is a truth table?

A **truth table** lists every possible combination of input values and shows the corresponding output.

Digital systems normally use two values:

```text
0 = FALSE / LOW
1 = TRUE / HIGH
```

For example, for an AND gate:

```text
Y = A·B
```

Truth table:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

The table tells us exactly what output occurs for every possible input combination.

---

# 2. Why are truth tables important?

Truth tables allow us to understand a circuit without physically building it.

They can be used to:

- Describe a logic function
- Analyze a circuit
- Verify a circuit
- Compare two Boolean expressions
- Design a circuit
- Find errors in logic
- Derive SOP and POS expressions

For university exams, you should be comfortable creating and reading truth tables.

---

# 3. Boolean values

Truth tables use Boolean values:

```text
0
1
```

Depending on the context, they can represent:

| Boolean | Possible meaning |
|---|---|
| 0 | False |
| 1 | True |
| 0 | LOW |
| 1 | HIGH |
| 0 | OFF |
| 1 | ON |

In real hardware, HIGH and LOW correspond to voltage ranges rather than simply mathematical numbers.

---

# 4. Inputs and outputs

A truth table contains:

```text
Input columns
      ↓
Output column(s)
```

Example:

```text
A ──┐
    ├── Logic → Y
B ──┘
```

The truth table has:

```text
A
B
Y
```

For two inputs, there are four possible combinations.

---

# 5. Number of rows in a truth table

This is one of the most important formulas.

For:

```text
n = number of inputs
```

the number of possible input combinations is:

```text
2ⁿ
```

Therefore:

| Number of inputs | Number of rows |
|---:|---:|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |
| 5 | 32 |
| 6 | 64 |
| 7 | 128 |
| 8 | 256 |
| 10 | 1024 |

### Example

For 4 inputs:

```text
2⁴ = 16
```

So a complete truth table has:

```text
16 rows
```

Do not count the header row.

---

# 6. How to generate input combinations

For two inputs:

```text
A B
```

write:

```text
00
01
10
11
```

For three inputs:

```text
A B C
```

write:

```text
000
001
010
011
100
101
110
111
```

For four inputs:

```text
A B C D
```

write:

```text
0000
0001
0010
0011
0100
0101
0110
0111
1000
1001
1010
1011
1100
1101
1110
1111
```

This is simply binary counting.

---

# 7. A useful pattern for making truth tables

For `n` variables, the rightmost variable changes fastest.

For three variables:

```text
A: 0 0 0 0 1 1 1 1
B: 0 0 1 1 0 0 1 1
C: 0 1 0 1 0 1 0 1
```

So:

```text
A changes every 4 rows
B changes every 2 rows
C changes every 1 row
```

For four variables:

```text
A: 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1
B: 0 0 0 0 1 1 1 1 0 0 0 0 1 1 1 1
C: 0 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1
D: 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1
```

This pattern is extremely useful in exams.

---

# 8. Truth table for NOT

The NOT operation has one input.

```text
Y = A'
```

Truth table:

| A | Y=A' |
|---|---:|
| 0 | 1 |
| 1 | 0 |

NOT reverses the input.

```text
0 → 1
1 → 0
```

---

# 9. Truth table for AND

Boolean expression:

```text
Y = AB
```

Truth table:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

AND outputs 1 only when **all inputs are 1**.

Memory rule:

> AND = all must be 1.

---

# 10. Truth table for OR

Boolean expression:

```text
Y = A+B
```

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

OR outputs 1 when **at least one input is 1**.

Memory rule:

> OR = one or more can be 1.

---

# 11. Truth table for NAND

NAND means:

```text
NOT AND
```

Boolean expression:

```text
Y=(AB)'
```

| A | B | AB | Y=(AB)' |
|---|---|---:|---:|
| 0 | 0 | 0 | 1 |
| 0 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 0 |

NAND is the opposite of AND.

---

# 12. Truth table for NOR

NOR means:

```text
NOT OR
```

Boolean expression:

```text
Y=(A+B)'
```

| A | B | A+B | Y |
|---|---|---:|---:|
| 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 |

NOR is the opposite of OR.

---

# 13. Truth table for XOR

XOR means **Exclusive OR**.

Boolean expression:

```text
Y=A⊕B
```

Equivalent Boolean expression:

```text
A⊕B=A'B+AB'
```

Truth table:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

XOR outputs 1 when the inputs are **different**.

Memory rule:

> XOR = different → 1.

---

# 14. Truth table for XNOR

XNOR is the opposite of XOR.

Boolean expression:

```text
Y=(A⊕B)'
```

Equivalent expression:

```text
Y=A'B'+AB
```

Truth table:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

XNOR outputs 1 when the inputs are **equal**.

Memory rule:

> XNOR = same → 1.

---

# 15. Complete basic gate truth table

| A | B | AND | OR | NAND | NOR | XOR | XNOR |
|---|---|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 |

This table is worth memorizing.

---

# 16. Reading a Boolean expression

Suppose:

```text
Y=A+BC
```

Operator precedence:

```text
1. Parentheses
2. NOT
3. AND
4. OR
```

Therefore:

```text
Y=A+(BC)
```

To construct the truth table, calculate:

```text
BC
```

first, then:

```text
A+BC
```

---

# 17. Example: truth table for Y = A + BC

First create the input combinations.

| A | B | C |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |
| 1 | 1 | 1 |

Now calculate `BC` and then `Y`.

| A | B | C | BC | Y=A+BC |
|---|---|---|---:|---:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

---

# 18. Intermediate columns

For complicated expressions, use intermediate columns.

Example:

```text
Y=(A+B)C'
```

Create:

```text
A+B
C'
(A+B)C'
```

Truth table:

| A | B | C | A+B | C' | Y |
|---|---|---|---:|---:|---:|
| 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 | 1 |
| 0 | 1 | 1 | 1 | 0 | 0 |
| 1 | 0 | 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 1 | 0 | 0 |
| 1 | 1 | 0 | 1 | 1 | 1 |
| 1 | 1 | 1 | 1 | 0 | 0 |

This method makes complicated truth tables much easier.

---

# 19. Truth tables for multiple outputs

A circuit can have more than one output.

For example, a half adder has:

```text
S = Sum
C = Carry
```

Truth table:

| A | B | S | C |
|---|---|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

Each output has its own Boolean function.

```text
S=A⊕B
C=AB
```

---

# 20. Truth table for a Half Adder

A half adder adds:

```text
A+B
```

Outputs:

```text
Sum
Carry
```

| A | B | Sum | Carry |
|---|---|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

Important:

```text
Sum = XOR
Carry = AND
```

---

# 21. Truth table for a Full Adder

Inputs:

```text
A
B
Cin
```

Outputs:

```text
S
Cout
```

| A | B | Cin | S | Cout |
|---|---|---|---:|---:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

Equations:

```text
S=A⊕B⊕Cin
```

```text
Cout=AB+ACin+BCin
```

---

# 22. Truth table for Half Subtractor

Inputs:

```text
A
B
```

Outputs:

```text
Difference
Borrow
```

| A | B | Difference | Borrow |
|---|---|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |

Equations:

```text
D=A⊕B
Borrow=A'B
```

---

# 23. Truth table for Full Subtractor

Inputs:

```text
A
B
Bin
```

Outputs:

```text
D
Bout
```

| A | B | Bin | D | Bout |
|---|---|---|---:|---:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 0 | 0 |
| 1 | 1 | 1 | 1 | 1 |

---

# 24. Truth table for a 2-to-1 MUX

Inputs:

```text
D0
D1
S
```

Output:

```text
Y
```

| S | Y |
|---|---|
| 0 | D0 |
| 1 | D1 |

Boolean expression:

```text
Y=S'D0+SD1
```

The select input determines which data input reaches the output.

---

# 25. Truth table for a 4-to-1 MUX

Inputs:

```text
D0 D1 D2 D3
```

Select lines:

```text
S1 S0
```

Output:

```text
Y
```

| S1 | S0 | Y |
|---|---|---|
| 0 | 0 | D0 |
| 0 | 1 | D1 |
| 1 | 0 | D2 |
| 1 | 1 | D3 |

---

# 26. Truth table for a 1-to-2 DEMUX

Input:

```text
D
```

Select:

```text
S
```

Outputs:

```text
Y0
Y1
```

| S | Y0 | Y1 |
|---|---|---|
| 0 | D | 0 |
| 1 | 0 | D |

Equations:

```text
Y0=DS'
Y1=DS
```

---

# 27. Truth table for a 2-to-4 Decoder

Inputs:

```text
A
B
```

Outputs:

```text
Y0
Y1
Y2
Y3
```

| A | B | Y0 | Y1 | Y2 | Y3 |
|---|---|---:|---:|---:|---:|
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 | 0 | 1 |

Assuming active-high outputs.

---

# 28. Truth table for a 4-to-2 Encoder

A simple encoder assumes only one input is active at a time.

| D3 | D2 | D1 | D0 | Y1 | Y0 |
|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 1 |
| 0 | 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 0 | 0 | 1 | 1 |

The output is the binary code corresponding to the active input.

---

# 29. Truth table for a 1-bit comparator

Inputs:

```text
A
B
```

Outputs:

```text
A>B
A=B
A<B
```

| A | B | A>B | A=B | A<B |
|---|---|---:|---:|---:|
| 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 1 | 0 |

Equations:

```text
A>B=AB'
```

```text
A=B=A'B'+AB
```

```text
A<B=A'B
```

---

# 30. Truth table for Boolean identities

Truth tables can prove Boolean identities.

Example:

```text
A+AB=A
```

| A | B | AB | A+AB | A |
|---|---|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 1 |
| 1 | 1 | 1 | 1 | 1 |

Since the last two columns are identical:

```text
A+AB=A
```

is proven.

---

# 31. Truth-table proof of De Morgan's law

Consider:

```text
(A+B)'=A'B'
```

| A | B | A+B | (A+B)' | A' | B' | A'B' |
|---|---|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 1 | 1 | 1 | 1 |
| 0 | 1 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 0 | 0 | 0 | 0 |

The two result columns are identical.

Therefore:

```text
(A+B)'=A'B'
```

---

# 32. How to prove two Boolean expressions are equivalent

Suppose we want to prove:

```text
F1=F2
```

Procedure:

```text
1. List all input combinations.
2. Calculate F1.
3. Calculate F2.
4. Compare the output columns.
```

If they are identical for every input combination:

```text
F1=F2
```

This is called **truth-table verification**.

---

# 33. Truth tables and SOP

Truth tables can be used to derive a **Sum of Products (SOP)** expression.

Procedure:

```text
1. Find rows where output = 1.
2. Write one minterm for each row.
3. OR the minterms together.
```

Example:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Rows with Y = 1:

```text
01
10
```

Minterms:

```text
A'B
AB'
```

Therefore:

```text
Y=A'B+AB'
```

This is XOR.

---

# 34. How to create a minterm from a truth-table row

For a row:

```text
A=0
B=1
C=0
```

the minterm is:

```text
A'BC'
```

Rule:

```text
Input = 1 → write variable normally
Input = 0 → write complemented variable
```

Examples:

```text
000 → A'B'C'
001 → A'B'C
010 → A'BC'
011 → A'BC
100 → AB'C'
101 → AB'C
110 → ABC'
111 → ABC
```

---

# 35. Minterm numbering

For three variables:

| A | B | C | Binary | Minterm |
|---|---|---|---|---|
| 0 | 0 | 0 | 000 | m0 |
| 0 | 0 | 1 | 001 | m1 |
| 0 | 1 | 0 | 010 | m2 |
| 0 | 1 | 1 | 011 | m3 |
| 1 | 0 | 0 | 100 | m4 |
| 1 | 0 | 1 | 101 | m5 |
| 1 | 1 | 0 | 110 | m6 |
| 1 | 1 | 1 | 111 | m7 |

Therefore, if:

```text
Y=1
```

for rows 1, 3, 5 and 7:

```text
Y=Σm(1,3,5,7)
```

---

# 36. Truth tables and POS

Truth tables can also produce **Product of Sums (POS)** expressions.

Procedure:

```text
1. Find rows where output = 0.
2. Write one maxterm for each row.
3. AND the maxterms together.
```

For XOR:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Rows where Y = 0:

```text
00
11
```

Canonical POS:

```text
Y=(A+B)(A'+B')
```

This is equivalent to XOR.

---

# 37. Maxterm rule

For a maxterm:

```text
Input = 0 → variable normally
Input = 1 → variable complemented
```

Example row:

```text
A=0
B=1
```

Maxterm:

```text
A+B'
```

Why?

The maxterm must evaluate to 0 for that row:

```text
A+B'
=0+0
=0
```

---

# 38. SOP vs POS

| Feature | SOP | POS |
|---|---|---|
| Full name | Sum of Products | Product of Sums |
| Basic structure | OR of AND terms | AND of OR terms |
| Usually derived from | Rows with output 1 | Rows with output 0 |
| Uses | Minterms | Maxterms |
| Symbol | `Σm` | `ΠM` |

Memory:

```text
SOP → look at 1s
POS → look at 0s
```

---

# 39. Don't-care conditions

Sometimes a digital system does not care about the output for certain input combinations.

These are called **don't-care conditions**.

They are commonly represented as:

```text
X
```

or:

```text
d
```

Example:

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | X |
| 1 | 1 | 1 |

A don't-care condition may be treated as either 0 or 1 when simplifying a Boolean function, if doing so helps produce a simpler circuit.

Don't-care conditions become especially important when studying Karnaugh maps.

---

# 40. Truth tables and Karnaugh maps

A truth table can be converted into a Karnaugh map.

General flow:

```text
Truth Table
     ↓
Minterms
     ↓
Karnaugh Map
     ↓
Grouping
     ↓
Simplified Boolean Expression
```

Truth tables are therefore an important foundation for K-maps.

---

# 41. Truth table for a 3-input majority function

A useful example is a majority circuit.

Output is 1 when **at least two of the three inputs are 1**.

Inputs:

```text
A B C
```

Output:

```text
Y
```

| A | B | C | Y |
|---|---|---|---:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 1 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

Boolean expression:

```text
Y=AB+AC+BC
```

This is also the carry equation of a full adder.

---

# 42. Truth table for a parity function

Parity circuits are important in digital communication and error detection.

For three inputs, odd parity can be represented by:

```text
Y=A⊕B⊕C
```

Truth table:

| A | B | C | Y |
|---|---|---|---:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

The output is 1 when an odd number of inputs are 1.

---

# 43. Truth tables and logic circuit analysis

Suppose a circuit contains:

```text
A ──┐
    AND ── X ──┐
B ──┘         OR ── Y
C ────────────┘
```

Then:

```text
X=AB
```

and:

```text
Y=X+C
```

Therefore:

```text
Y=AB+C
```

To construct the truth table, calculate the intermediate signal X first.

---

# 44. A systematic method for complex circuits

For a circuit with many gates:

### Step 1

Identify all input variables.

### Step 2

Identify every intermediate signal.

### Step 3

Write the Boolean expression for each gate.

### Step 4

Create the input combinations.

### Step 5

Calculate intermediate columns from left to right.

### Step 6

Calculate the final output.

Example:

```text
X=AB
Z=C'
Y=X+Z
```

Truth table columns:

```text
A
B
C
X=AB
Z=C'
Y=X+Z
```

This approach prevents mistakes.

---

# 45. Truth tables and circuit equivalence

Two circuits can look completely different but perform the same function.

Example:

```text
Circuit 1 → F1
Circuit 2 → F2
```

To check whether they are equivalent:

```text
Create one truth table
       ↓
Calculate F1
       ↓
Calculate F2
       ↓
Compare
```

If:

```text
F1 = F2
```

for every row, the circuits are functionally equivalent.

---

# 46. Common truth-table mistakes

## Mistake 1 — Missing input combinations

For 3 inputs you need:

```text
2³=8 rows
```

not 6 or 7.

## Mistake 2 — Repeating a combination

Every combination from:

```text
000 → 111
```

must appear exactly once.

## Mistake 3 — Wrong binary counting

For three inputs:

```text
000
001
010
011
100
101
110
111
```

## Mistake 4 — Calculating operations in the wrong order

Remember:

```text
NOT → AND → OR
```

after parentheses.

## Mistake 5 — Confusing XOR and OR

OR:

```text
1 OR 1 = 1
```

XOR:

```text
1 XOR 1 = 0
```

## Mistake 6 — Forgetting intermediate columns

For complicated expressions, calculate smaller parts first.

---

# 47. Fast method for evaluating a Boolean expression

Example:

```text
Y=A'B+C
```

Given:

```text
A=1
B=1
C=0
```

Step 1:

```text
A'=0
```

Step 2:

```text
A'B=0·1=0
```

Step 3:

```text
Y=0+0=0
```

Therefore:

```text
Y=0
```

---

# 48. Fast method for constructing a truth table

For:

```text
Y=A'B+C
```

use:

| A | B | C | A' | A'B | Y |
|---|---|---|---:|---:|---:|
| 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 | 1 |
| 0 | 1 | 1 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 1 |
| 1 | 1 | 0 | 0 | 0 | 0 |
| 1 | 1 | 1 | 0 | 0 | 1 |

This is much safer than trying to calculate the entire expression mentally.

---

# 49. Truth tables and digital design workflow

A common digital-design workflow is:

```text
Problem statement
      ↓
Identify inputs/outputs
      ↓
Truth table
      ↓
Boolean expression
      ↓
Boolean simplification
      ↓
Logic circuit
      ↓
Verification
```

You should be able to move in both directions:

```text
Circuit → Truth Table
```

and:

```text
Truth Table → Boolean Expression → Circuit
```

---

# 50. Important truth tables to memorize

You should know these without hesitation:

```text
NOT
AND
OR
NAND
NOR
XOR
XNOR
```

Also understand:

```text
Half Adder
Full Adder
Half Subtractor
Full Subtractor
MUX
DEMUX
Decoder
Encoder
Comparator
```

These are heavily connected to the combinational-network topic.

---

# 51. Exam practice — Level 1

1. What is a truth table?
2. What does 0 represent in digital logic?
3. What does 1 represent?
4. How many rows are required for 2 inputs?
5. How many rows are required for 5 inputs?
6. How many rows are required for 8 inputs?
7. Write the truth table of NOT.
8. Write the truth table of AND.
9. Write the truth table of OR.
10. Write the truth table of NAND.
11. Write the truth table of NOR.
12. Write the truth table of XOR.
13. Write the truth table of XNOR.
14. What is the difference between OR and XOR?
15. What is the formula for the number of truth-table rows?

---

# 52. Exam practice — Level 2

16. Construct the truth table for:

```text
Y=A+B
```

17. Construct the truth table for:

```text
Y=AB
```

18. Construct the truth table for:

```text
Y=A'B
```

19. Construct the truth table for:

```text
Y=A+BC
```

20. Construct the truth table for:

```text
Y=(A+B)C'
```

21. Construct the truth table for:

```text
Y=A'B+C
```

22. Prove using a truth table:

```text
A+AB=A
```

23. Prove using a truth table:

```text
A+A'=1
```

24. Verify:

```text
(A+B)'=A'B'
```

25. Verify:

```text
(AB)'=A'+B'
```

---

# 53. Exam practice — Level 3

26. Derive the Boolean expression from a given truth table.

27. Convert a truth table into canonical SOP.

28. Convert a truth table into canonical POS.

29. Express a Boolean function using sigma notation.

30. Express a Boolean function using pi notation.

31. Explain minterms and maxterms.

32. Design a half adder from a truth table.

33. Design a full adder from a truth table.

34. Derive the Boolean equation of a 2-to-1 MUX from its truth table.

35. Explain how a truth table can be used to prove circuit equivalence.

36. Explain how truth tables are connected to Karnaugh maps.

37. Design a majority circuit using a truth table.

---

# 54. Practice answers

### 4

```text
2²=4
```

### 5

```text
2⁵=32
```

### 6

```text
2⁸=256
```

### 14

```text
OR  → 1 when one or more inputs are 1
XOR → 1 when inputs are different
```

### 15

```text
2ⁿ
```

where `n` is the number of inputs.

---

# 55. Mini exam

Try these without looking at the answers.

### Question 1

How many rows are required for a truth table with 4 inputs?

### Question 2

What is the output of AND when:

```text
A=1
B=1
```

### Question 3

What is the output of XOR when:

```text
A=1
B=1
```

### Question 4

What is the output of XNOR when:

```text
A=1
B=1
```

### Question 5

Construct the truth table for:

```text
Y=A+B
```

### Question 6

Construct the truth table for:

```text
Y=AB
```

### Question 7

How do you derive SOP from a truth table?

### Question 8

How do you derive POS from a truth table?

### Question 9

What is a minterm?

### Question 10

What is a maxterm?

### Question 11

How can a truth table prove two circuits are equivalent?

### Question 12

What is a don't-care condition?

---

# 56. Mini exam answers

```text
1. 16 rows.
2. 1.
3. 0.
4. 1.
5. OR truth table.
6. AND truth table.
7. Take rows where output = 1, create minterms, OR them.
8. Take rows where output = 0, create maxterms, AND them.
9. An AND term containing every variable exactly once.
10. An OR term containing every variable exactly once.
11. Compare the output columns for every input combination.
12. An input combination for which the output may be treated as either 0 or 1 during simplification.
```

---

# 57. Final exam cheat sheet

## Number of rows

```text
n inputs → 2ⁿ rows
```

## Basic gates

```text
NOT:
A → A'

AND:
AB

OR:
A+B

NAND:
(AB)'

NOR:
(A+B)'

XOR:
A'B+AB'

XNOR:
A'B'+AB
```

## Gate behavior

```text
AND  → all 1 → output 1
OR   → at least one 1 → output 1
XOR  → different → output 1
XNOR → same → output 1
```

## SOP

```text
Output = 1 rows
      ↓
Minterms
      ↓
OR
```

```text
Σm(...)
```

## POS

```text
Output = 0 rows
      ↓
Maxterms
      ↓
AND
```

```text
ΠM(...)
```

## Minterm rule

```text
0 → complemented
1 → normal
```

Example:

```text
101 → AB'C
```

## Maxterm rule

```text
0 → normal
1 → complemented
```

Example:

```text
101 → (A'+B+C')
```

## Truth-table verification

```text
Expression 1
     ↓
Truth table
     ↓
Expression 2
     ↓
Compare outputs
```

If all rows match:

```text
Expressions are equivalent.
```

---

# 58. Key formulas to remember

```text
Number of rows = 2ⁿ
```

```text
Half Adder:
S=A⊕B
C=AB
```

```text
Full Adder:
S=A⊕B⊕Cin
Cout=AB+ACin+BCin
```

```text
Half Subtractor:
D=A⊕B
Borrow=A'B
```

```text
2-to-1 MUX:
Y=S'D0+SD1
```

```text
1-bit Comparator:
A>B=AB'
A=B=A'B'+AB
A<B=A'B
```

---

# 59. What you should be able to do before moving on

- [ ] Define a truth table.
- [ ] Explain Boolean 0 and 1.
- [ ] Calculate the number of rows using `2ⁿ`.
- [ ] Generate binary input combinations.
- [ ] Construct truth tables for NOT, AND, OR.
- [ ] Construct truth tables for NAND and NOR.
- [ ] Construct truth tables for XOR and XNOR.
- [ ] Evaluate Boolean expressions using truth tables.
- [ ] Use intermediate columns for complex expressions.
- [ ] Create multiple-output truth tables.
- [ ] Construct the truth table for a half adder.
- [ ] Construct the truth table for a full adder.
- [ ] Construct the truth table for a half subtractor.
- [ ] Construct the truth table for a full subtractor.
- [ ] Construct MUX and DEMUX truth tables.
- [ ] Construct decoder and encoder truth tables.
- [ ] Construct a comparator truth table.
- [ ] Prove Boolean identities using truth tables.
- [ ] Check whether two circuits are equivalent.
- [ ] Derive SOP from a truth table.
- [ ] Derive POS from a truth table.
- [ ] Understand minterms and maxterms.
- [ ] Understand don't-care conditions.
- [ ] Understand the connection between truth tables and Karnaugh maps.

---

# 60. Connection to the HKR course

The topics fit together like this:

```text
NUMBER SYSTEMS
      ↓
Binary 0 and 1
      ↓
BOOLEAN ALGEBRA
      ↓
Boolean expressions and laws
      ↓
TRUTH TABLES
      ↓
Describe and verify logic functions
      ↓
COMBINATIONAL NETWORKS
      ↓
Adders / Subtractors
MUX / DEMUX
Encoders / Decoders
Comparators
      ↓
SEQUENTIAL NETWORKS
      ↓
Flip-Flops
Registers
Counters
      ↓
PROCESSOR PRINCIPLES
      ↓
MEMORIES AND I/O
```

## Final key idea

> **A truth table is a complete description of how a digital logic function behaves for every possible combination of its inputs.**

If you understand truth tables well, you have a strong foundation for **Boolean Algebra, combinational networks, sequential networks, processors, and memory systems**.
