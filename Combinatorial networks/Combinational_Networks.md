# Combinational Networks — Digital Circuits & Computer Engineering

## Course context

A **combinational network** (also called a combinational circuit) is a digital circuit whose output depends only on the **current input values**.

```text
Current inputs
      ↓
Combinational logic
      ↓
Current outputs
```

There is **no memory** of previous inputs.

This topic connects Boolean Algebra and Truth Tables to practical digital circuits such as:

- Adders
- Subtractors
- Multiplexers (MUX)
- Demultiplexers (DEMUX)
- Encoders
- Decoders
- Comparators
- Arithmetic circuits

---

# 1. What is a combinational network?

A **combinational network** is a digital circuit in which the output is determined entirely by the present inputs.

Mathematically:

```text
Output = f(current inputs)
```

For example:

```text
Y = A + B
```

If:

```text
A = 1
B = 0
```

then:

```text
Y = 1
```

The circuit does not need to know what A and B were previously.

---

# 2. Combinational vs sequential circuits

This distinction is extremely important.

## Combinational circuit

```text
Output = function(current inputs)
```

Examples:

- Adders
- Subtractors
- Multiplexers
- Decoders
- Encoders
- Comparators

## Sequential circuit

```text
Output = function(current inputs, previous state)
```

Examples:

- Flip-flops
- Registers
- Counters
- Memory elements

### Key difference

| Feature | Combinational | Sequential |
|---|---|---|
| Depends on current inputs | Yes | Yes |
| Depends on previous state | No | Yes |
| Memory | No | Yes |
| Feedback normally required | No | Often |
| Examples | Adder, MUX | Counter, register |

Remember:

> **Combinational = no memory. Sequential = has state/memory.**

---

# 3. Basic structure

A combinational network can be represented as:

```text
A ─────┐
B ─────┤
C ─────┤
       ↓
[ Logic Circuit ]
       ↓
Y ─────
```

The circuit can contain:

```text
AND
OR
NOT
NAND
NOR
XOR
XNOR
```

The output changes according to the current input combination.

---

# 4. Number of possible input combinations

If a combinational circuit has `n` binary inputs:

```text
Number of possible input combinations = 2ⁿ
```

Examples:

```text
1 input  → 2 combinations
2 inputs → 4 combinations
3 inputs → 8 combinations
4 inputs → 16 combinations
8 inputs → 256 combinations
```

This is the same principle used when constructing truth tables.

---

# 5. Designing a combinational circuit

A common design procedure is:

```text
1. Understand the problem
        ↓
2. Identify inputs and outputs
        ↓
3. Create the truth table
        ↓
4. Derive Boolean expressions
        ↓
5. Simplify the expressions
        ↓
6. Draw the logic circuit
        ↓
7. Verify the circuit
```

This sequence is very important for exams.

---

# 6. Example of combinational design

Suppose an output should be 1 when both A and B are 1.

Inputs:

```text
A
B
```

Output:

```text
Y
```

Truth table:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

Boolean expression:

```text
Y = AB
```

Therefore, an AND gate implements the circuit.

---

# 7. Propagation delay

Real gates do not respond instantaneously.

When an input changes, there is a small delay before the output changes.

This is called **propagation delay**.

```text
Input changes
     ↓
small delay
     ↓
Output changes
```

This is important in real digital circuits because larger circuits can have greater delays.

---

# 8. Main combinational networks

The important circuits for this topic are:

```text
1. Half Adder
2. Full Adder
3. Half Subtractor
4. Full Subtractor
5. Multiplexer
6. Demultiplexer
7. Decoder
8. Encoder
9. Comparator
```

These are important building blocks in computer hardware.

---

# 9. Binary addition

Before studying adders, understand binary addition.

Basic rules:

```text
0 + 0 = 0
0 + 1 = 1
1 + 0 = 1
1 + 1 = 10
```

The last result means:

```text
Sum = 0
Carry = 1
```

This carry is the reason digital adders need more than one output.

---

# 10. Half Adder

A **half adder** adds two one-bit binary numbers.

Inputs:

```text
A
B
```

Outputs:

```text
S = Sum
C = Carry
```

Block representation:

```text
A ─────┐
       │
    [ HALF ]
    [ ADDER ]── S
       │
B ─────┘
       │
       └────── C
```

---

# 11. Half Adder truth table

| A | B | Sum S | Carry C |
|---|---|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

Notice:

```text
Sum = XOR
Carry = AND
```

Therefore:

```text
S = A ⊕ B
C = AB
```

---

# 12. Half Adder using gates

A half adder requires:

```text
1 XOR gate
1 AND gate
```

Circuit concept:

```text
A ─────┬──── XOR ─── S
       │
B ─────┘

A ─────┬──── AND ─── C
       │
B ─────┘
```

The XOR produces the sum.

The AND produces the carry.

---

# 13. Why is it called a half adder?

A half adder adds two bits but does **not accept an input carry** from a previous stage.

This is its main limitation.

That is why a full adder is needed for multi-bit addition.

---

# 14. Full Adder

A **full adder** adds three one-bit inputs:

```text
A
B
Cin
```

where:

```text
Cin = Carry in
```

Outputs:

```text
S = Sum
Cout = Carry out
```

So:

```text
A + B + Cin
```

produces:

```text
Sum + Carry
```

---

# 15. Full Adder truth table

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

---

# 16. Full Adder Boolean expressions

The Sum output is:

```text
S = A ⊕ B ⊕ Cin
```

The carry output is:

```text
Cout = AB + ACin + BCin
```

Another useful form is:

```text
Cout = AB + Cin(A ⊕ B)
```

Both describe the same carry function.

---

# 17. Full Adder using two Half Adders

A full adder can be built using:

```text
2 Half Adders
1 OR gate
```

Structure:

```text
        ┌─────────────┐
A ─────→│ Half Adder  │── S1 ──┐
B ─────→│             │        │
        └─────────────┘        ↓
                              ┌─────────────┐
Cin ─────────────────────────→│ Half Adder  │── S
                              └─────────────┘
                                      │
                         Carry ───────┘
```

The two carry outputs are ORed:

```text
Cout = C1 + C2
```

---

# 18. Multi-bit binary addition

A computer usually adds numbers containing many bits.

For example:

```text
1011
0110
----
10001
```

Several full adders can be connected together.

```text
FA → FA → FA → FA
```

The carry from one stage becomes the carry input of the next stage.

---

# 19. Ripple Carry Adder

A simple multi-bit adder is the **Ripple Carry Adder**.

Example for 4 bits:

```text
A0 B0 ─→ FA0 ─→ C1
A1 B1 ─→ FA1 ─→ C2
A2 B2 ─→ FA2 ─→ C3
A3 B3 ─→ FA3 ─→ C4
```

The carry ripples from the least significant bit toward the most significant bit.

### Advantage

Simple design.

### Disadvantage

The carry must travel through multiple adders, creating propagation delay.

---

# 20. Half Subtractor

A **half subtractor** subtracts one bit from another.

Inputs:

```text
A = Minuend
B = Subtrahend
```

Outputs:

```text
D = Difference
Borrow = Borrow
```

It performs:

```text
A - B
```

---

# 21. Half Subtractor truth table

| A | B | Difference D | Borrow |
|---|---|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |

Therefore:

```text
D = A ⊕ B
```

and:

```text
Borrow = A'B
```

---

# 22. Why is borrow needed?

Consider:

```text
0 - 1
```

A single binary digit cannot represent `-1` directly in the unsigned subtraction process.

So we borrow from a higher bit.

Therefore:

```text
0 - 1
```

produces:

```text
Difference = 1
Borrow = 1
```

---

# 23. Full Subtractor

A full subtractor subtracts three inputs:

```text
A
B
Bin
```

where:

```text
Bin = Borrow in
```

Outputs:

```text
D = Difference
Bout = Borrow out
```

It performs:

```text
A - B - Bin
```

---

# 24. Full Subtractor truth table

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

# 25. Full Subtractor equations

Difference:

```text
D = A ⊕ B ⊕ Bin
```

Borrow out:

```text
Bout = A'B + A'Bin + BBin
```

Another useful form is:

```text
Bout = A'B + Bin(A ⊕ B)'
```

The first form is often easier to derive directly from the truth table.

---

# 26. Multiplexer — MUX

A **multiplexer (MUX)** is a digital selector.

It selects one of several inputs and sends the selected input to one output.

Think:

> **MUX = many inputs → one output**

For example, a 4-to-1 MUX has:

```text
4 data inputs
2 select inputs
1 output
```

Because:

```text
2² = 4
```

---

# 27. 2-to-1 Multiplexer

A 2-to-1 MUX has:

```text
D0
D1
S
```

and output:

```text
Y
```

Truth table:

| S | Y |
|---|---|
| 0 | D0 |
| 1 | D1 |

Boolean expression:

```text
Y = S'D0 + SD1
```

Explanation:

If:

```text
S=0
```

then:

```text
Y=D0
```

If:

```text
S=1
```

then:

```text
Y=D1
```

---

# 28. 2-to-1 MUX using gates

Expression:

```text
Y=S'D0+SD1
```

requires:

```text
1 NOT gate
2 AND gates
1 OR gate
```

Conceptually:

```text
       ┌─ NOT ── S'
S ─────┤
       │
D0 ─── AND ──┐
              │
D1 ─── AND ─── OR ── Y
              │
S ────────────┘
```

---

# 29. 4-to-1 Multiplexer

A 4-to-1 MUX has:

```text
D0
D1
D2
D3
```

two select inputs:

```text
S1
S0
```

and one output:

```text
Y
```

Truth table:

| S1 | S0 | Selected input |
|---|---|---|
| 0 | 0 | D0 |
| 0 | 1 | D1 |
| 1 | 0 | D2 |
| 1 | 1 | D3 |

Boolean expression:

```text
Y = S1'S0'D0
  + S1'S0D1
  + S1S0'D2
  + S1S0D3
```

---

# 30. MUX size relationship

For a MUX with `n` select lines:

```text
Number of inputs = 2ⁿ
```

Examples:

```text
1 select → 2 inputs
2 selects → 4 inputs
3 selects → 8 inputs
4 selects → 16 inputs
```

A MUX has:

```text
2ⁿ data inputs
n select lines
1 output
```

---

# 31. Applications of multiplexers

MUXes are used for:

- Data selection
- Data routing
- Communication paths
- Processor datapaths
- Selecting ALU inputs
- Selecting registers
- Bus selection
- Digital control systems

A MUX can be thought of as a digitally controlled switch.

---

# 32. Demultiplexer — DEMUX

A **demultiplexer** performs the opposite basic routing operation.

Think:

> **DEMUX = one input → many possible outputs**

A DEMUX receives one data input and routes it to one selected output.

---

# 33. 1-to-2 DEMUX

Inputs:

```text
D
S
```

Outputs:

```text
Y0
Y1
```

Truth table:

| S | Y0 | Y1 |
|---|---:|---:|
| 0 | D | 0 |
| 1 | 0 | D |

Equations:

```text
Y0 = DS'
Y1 = DS
```

---

# 34. 1-to-4 DEMUX

A 1-to-4 DEMUX has:

```text
1 data input
2 select lines
4 outputs
```

The select lines choose where the input goes.

```text
S1 S0 = 00 → Y0
S1 S0 = 01 → Y1
S1 S0 = 10 → Y2
S1 S0 = 11 → Y3
```

Equations:

```text
Y0 = DS1'S0'
Y1 = DS1'S0
Y2 = DS1S0'
Y3 = DS1S0
```

---

# 35. MUX vs DEMUX

| Feature | MUX | DEMUX |
|---|---|---|
| Main function | Select | Route |
| Data flow | Many → One | One → Many |
| Data inputs | Many | One |
| Outputs | One | Many |
| Select lines | Control selection | Control destination |

Memory trick:

```text
MUX  = many into one
DEMUX = one into many
```

---

# 36. Decoder

A **decoder** converts an `n`-bit binary input into one of up to `2ⁿ` outputs.

For an `n-to-2ⁿ` decoder:

```text
n inputs
2ⁿ outputs
```

Usually only one output is active for each input combination.

---

# 37. 2-to-4 Decoder

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

Truth table:

| A | B | Y0 | Y1 | Y2 | Y3 |
|---|---|---:|---:|---:|---:|
| 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 |
| 1 | 0 | 0 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 | 0 | 1 |

Assuming active-high outputs.

Equations:

```text
Y0 = A'B'
Y1 = A'B
Y2 = AB'
Y3 = AB
```

---

# 38. Decoder applications

Decoders are used in:

- Memory address decoding
- Instruction decoding
- Display control
- Device selection
- Register selection
- Control circuits

A processor can use a decoder to determine which device or memory location should respond to an address.

---

# 39. Encoder

An **encoder** performs the reverse conceptual operation of a decoder.

Think:

> **Encoder = many inputs → binary code**

A simple `4-to-2` encoder has:

```text
4 inputs
2 outputs
```

Assuming only one input is active at a time:

| Active input | Output |
|---|---|
| D0 | 00 |
| D1 | 01 |
| D2 | 10 |
| D3 | 11 |

The encoder converts the active input position into a binary code.

---

# 40. 4-to-2 Encoder equations

For a simple one-hot 4-to-2 encoder:

```text
Y1 = D2 + D3
```

```text
Y0 = D1 + D3
```

This assumes only one input is active at a time.

---

# 41. Priority encoder

A normal encoder may have a problem if more than one input is active.

A **priority encoder** solves this by assigning priority to inputs.

For example:

```text
D3 > D2 > D1 > D0
```

If D3 and D1 are both 1, D3 is selected.

Priority encoders are useful when multiple requests may occur simultaneously.

---

# 42. Encoder vs Decoder

| Feature | Encoder | Decoder |
|---|---|---|
| Main conversion | Input position → binary code | Binary code → output position |
| Typical structure | Many → fewer | Fewer → many |
| Example | 4-to-2 | 2-to-4 |
| Outputs | Fewer | More |

Memory trick:

```text
ENCODER:
Many inputs → code

DECODER:
Code → one selected output
```

---

# 43. Comparator

A **digital comparator** compares two binary numbers.

For two numbers:

```text
A
B
```

a comparator can produce outputs indicating:

```text
A > B
A = B
A < B
```

These are often called:

```text
G = A greater than B
E = A equal to B
L = A less than B
```

---

# 44. One-bit comparator

For one-bit inputs:

```text
A
B
```

Truth table:

| A | B | A>B | A=B | A<B |
|---|---|---:|---:|---:|
| 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 0 | 1 | 0 |

Equations:

```text
A>B = AB'
```

```text
A<B = A'B
```

```text
A=B = A'B' + AB
```

Notice:

```text
A=B
```

is the XNOR function.

---

# 45. Multi-bit comparison

When comparing multi-bit numbers, the **most significant bit (MSB)** is very important.

Example:

```text
A = 1010
B = 1001
```

Compare from the left:

```text
1 = 1
0 = 0
1 > 0
```

Therefore:

```text
A > B
```

Once a higher-order bit differs, lower bits do not affect the comparison.

---

# 46. Building larger comparators

Multi-bit comparators can be constructed from smaller comparator blocks.

For example:

```text
1-bit comparator
       ↓
2-bit comparator
       ↓
4-bit comparator
       ↓
8-bit comparator
```

This modular approach is common in digital design.

---

# 47. Adders, MUXes, decoders and encoders — overview

| Circuit | Main purpose |
|---|---|
| Half Adder | Adds two bits |
| Full Adder | Adds two bits + carry in |
| Half Subtractor | Subtracts two bits |
| Full Subtractor | Subtracts two bits + borrow in |
| MUX | Selects one of many inputs |
| DEMUX | Routes one input to one of many outputs |
| Decoder | Binary code → selected output |
| Encoder | Active input → binary code |
| Comparator | Compares binary numbers |

---

# 48. Important formulas

## Half Adder

```text
S = A⊕B
C = AB
```

## Full Adder

```text
S = A⊕B⊕Cin
Cout = AB+ACin+BCin
```

## Half Subtractor

```text
D = A⊕B
Borrow = A'B
```

## Full Subtractor

```text
D = A⊕B⊕Bin
Bout = A'B+A'Bin+BBin
```

## 2-to-1 MUX

```text
Y = S'D0+SD1
```

## 1-to-2 DEMUX

```text
Y0=DS'
Y1=DS
```

## 2-to-4 Decoder

```text
Y0=A'B'
Y1=A'B
Y2=AB'
Y3=AB
```

## 4-to-2 Encoder

```text
Y1=D2+D3
Y0=D1+D3
```

## 1-bit Comparator

```text
A>B = AB'
A=B = A'B'+AB
A<B = A'B
```

---

# 49. Important relationships to memorize

```text
Half Adder:
2 inputs → 2 outputs

Full Adder:
3 inputs → 2 outputs

Half Subtractor:
2 inputs → 2 outputs

Full Subtractor:
3 inputs → 2 outputs

2-to-1 MUX:
2 data inputs → 1 output

4-to-1 MUX:
4 data inputs → 1 output

1-to-2 DEMUX:
1 input → 2 outputs

1-to-4 DEMUX:
1 input → 4 outputs

2-to-4 Decoder:
2 inputs → 4 outputs

4-to-2 Encoder:
4 inputs → 2 outputs
```

---

# 50. Common exam question: design from a truth table

A common question gives:

```text
Inputs
↓
Truth table
↓
Boolean function
↓
Logic circuit
```

Example:

| A | B | Y |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Rows where Y = 1:

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

Recognize this as:

```text
Y=A⊕B
```

So an XOR gate can implement the circuit.

---

# 51. Common exam question: identify a circuit

If given:

```text
S = A⊕B
C = AB
```

This is a:

```text
Half Adder
```

If given:

```text
S = A⊕B⊕Cin
```

and:

```text
Cout = AB+ACin+BCin
```

this is a:

```text
Full Adder
```

If a circuit has:

```text
many inputs
one selected output
select lines
```

think:

```text
MUX
```

If it has:

```text
one input
many possible outputs
select lines
```

think:

```text
DEMUX
```

---

# 52. Common exam mistakes

## Mistake 1 — Confusing MUX and DEMUX

Remember:

```text
MUX  = many → one
DEMUX = one → many
```

## Mistake 2 — Confusing encoder and decoder

Remember:

```text
Encoder = input → code
Decoder = code → output
```

## Mistake 3 — Forgetting carry in a full adder

Half adder:

```text
A+B
```

Full adder:

```text
A+B+Cin
```

## Mistake 4 — Confusing carry and borrow

Addition uses:

```text
Carry
```

Subtraction uses:

```text
Borrow
```

## Mistake 5 — Forgetting XOR in adders

Half adder:

```text
Sum = XOR
Carry = AND
```

This is one of the most useful facts to memorize.

---

# 53. Propagation delay in ripple carry adders

A ripple carry adder has a disadvantage.

The carry must travel through each full adder:

```text
FA0 → FA1 → FA2 → FA3
```

If each stage takes time to produce its carry, the total delay increases with the number of bits.

This is why faster adder architectures exist.

One important example is the:

```text
Carry Look-Ahead Adder
```

A carry look-ahead adder calculates carries more quickly using additional logic.

For introductory study, remember:

```text
Ripple Carry → simple but slower
Carry Look-Ahead → more hardware but faster
```

---

# 54. Combinational circuits in a processor

Combinational networks are essential inside processors.

Examples include:

```text
ALU
Multiplexers
Decoders
Comparators
Adders
Arithmetic logic
Address-selection logic
Control logic
```

For example, an ALU uses combinational logic to perform operations such as:

```text
Addition
Subtraction
AND
OR
XOR
Comparison
```

---

# 55. Real-world applications

## Adders

Used in:

- CPU arithmetic
- Address calculations
- Counters
- ALUs

## MUX

Used in:

- Data selection
- CPU datapaths
- Communication systems
- Bus routing

## DEMUX

Used in:

- Data distribution
- Communication routing
- Device selection

## Decoder

Used in:

- Memory addressing
- Instruction decoding
- Display systems
- Device selection

## Encoder

Used in:

- Keyboards
- Interrupt systems
- Priority selection
- Input coding

## Comparator

Used in:

- CPU comparison operations
- Sorting hardware
- Control systems
- Digital measurement systems

---

# 56. Combinational network design checklist

When designing a circuit:

- [ ] Identify all inputs.
- [ ] Identify all outputs.
- [ ] Determine the required behavior.
- [ ] Construct the truth table.
- [ ] Identify rows where output = 1.
- [ ] Write the Boolean expression.
- [ ] Simplify using Boolean Algebra.
- [ ] Choose suitable gates.
- [ ] Draw the circuit.
- [ ] Verify using the truth table.
- [ ] Check propagation-delay requirements if relevant.

---

# 57. Exam practice — Level 1

1. What is a combinational network?
2. Does a combinational circuit have memory?
3. What is the difference between combinational and sequential circuits?
4. How many combinations are possible with 4 binary inputs?
5. What is a half adder?
6. What are the outputs of a half adder?
7. What is a full adder?
8. What is `Cin`?
9. What is the difference between carry and borrow?
10. What is a MUX?
11. What is a DEMUX?
12. What is a decoder?
13. What is an encoder?
14. What is a comparator?
15. What is propagation delay?

---

# 58. Exam practice — Level 2

16. Write the truth table of a half adder.

17. Write the Boolean equations for a half adder.

18. Write the truth table of a full adder.

19. Write the Boolean equations for a full adder.

20. Write the truth table of a half subtractor.

21. Write the equations for a half subtractor.

22. Write the truth table of a 2-to-1 MUX.

23. Derive the Boolean expression for a 2-to-1 MUX.

24. Write the truth table of a 2-to-4 decoder.

25. Write the Boolean equations for a 2-to-4 decoder.

26. Write the Boolean equations for a 4-to-2 encoder.

27. Write the equations for a 1-bit comparator.

---

# 59. Exam practice — Level 3

28. Explain how two half adders can be used to construct a full adder.

29. Explain why a ripple carry adder becomes slower as the number of bits increases.

30. Design a combinational circuit from a given truth table.

31. Explain how a MUX can be used as a data selector.

32. Explain the difference between a decoder and a DEMUX.

33. Explain the difference between an encoder and a MUX.

34. Explain why NAND and NOR can be used to construct combinational circuits.

35. Design a 4-to-1 MUX and write its Boolean expression.

36. Design a full subtractor and derive its Boolean expressions.

37. Explain how a multi-bit comparator determines whether A > B.

---

# 60. Practice answers

### 4

For 4 inputs:

```text
2⁴=16
```

So there are 16 possible combinations.

### 17

Half Adder:

```text
S=A⊕B
C=AB
```

### 19

Full Adder:

```text
S=A⊕B⊕Cin
Cout=AB+ACin+BCin
```

### 21

Half Subtractor:

```text
D=A⊕B
Borrow=A'B
```

### 23

2-to-1 MUX:

```text
Y=S'D0+SD1
```

### 25

2-to-4 Decoder:

```text
Y0=A'B'
Y1=A'B
Y2=AB'
Y3=AB
```

### 27

1-bit Comparator:

```text
A>B=AB'
A=B=A'B'+AB
A<B=A'B
```

---

# 61. Mini exam

Try these without looking at the answers.

### Question 1

What is the main characteristic of a combinational circuit?

### Question 2

How many rows are in a truth table with 5 inputs?

### Question 3

What are the two outputs of a half adder?

### Question 4

What is the difference between a half adder and a full adder?

### Question 5

Write the full-adder Sum equation.

### Question 6

Write the half-subtractor Borrow equation.

### Question 7

What does a MUX do?

### Question 8

What does a DEMUX do?

### Question 9

How many select lines does a 16-to-1 MUX require?

### Question 10

How many outputs does a 3-to-8 decoder have?

### Question 11

What does an encoder do?

### Question 12

What three results can a comparator produce?

### Question 13

What is the main disadvantage of a ripple carry adder?

### Question 14

What is the difference between carry and borrow?

### Question 15

Why are combinational networks important in processors?

## Answers

```text
1. Output depends only on current inputs.
2. 2⁵ = 32.
3. Sum and Carry.
4. A full adder also accepts Carry-in.
5. S=A⊕B⊕Cin.
6. Borrow=A'B.
7. Selects one of many inputs and sends it to one output.
8. Routes one input to one selected output.
9. 4 select lines.
10. 8 outputs.
11. Converts an active input into a binary code.
12. A>B, A=B, A<B.
13. Carry propagation delay.
14. Addition produces carry; subtraction can require borrow.
15. They implement arithmetic, selection, comparison and control functions.
```

---

# 62. Final exam cheat sheet

## Combinational circuit

```text
Output = f(current inputs)
```

No memory.

## Number of input combinations

```text
n inputs → 2ⁿ combinations
```

## Half Adder

```text
S=A⊕B
C=AB
```

## Full Adder

```text
S=A⊕B⊕Cin
Cout=AB+ACin+BCin
```

## Half Subtractor

```text
D=A⊕B
Borrow=A'B
```

## Full Subtractor

```text
D=A⊕B⊕Bin
Bout=A'B+A'Bin+BBin
```

## MUX

```text
Many → One
```

For `n` select lines:

```text
2ⁿ inputs → 1 output
```

## DEMUX

```text
One → Many
```

For `n` select lines:

```text
1 input → 2ⁿ outputs
```

## Decoder

```text
n inputs → 2ⁿ outputs
```

## Encoder

```text
2ⁿ inputs → n outputs
```

## Comparator

```text
A>B
A=B
A<B
```

## Important XOR fact

```text
XOR = 1 when inputs are different
XNOR = 1 when inputs are equal
```

## Ripple Carry Adder

```text
Simple
but carry propagation causes delay
```

---

# 63. What you should be able to do before moving on

- [ ] Define a combinational network.
- [ ] Explain why it has no memory.
- [ ] Distinguish combinational and sequential circuits.
- [ ] Calculate the number of input combinations.
- [ ] Design a circuit from a truth table.
- [ ] Derive Boolean expressions from truth tables.
- [ ] Simplify Boolean expressions.
- [ ] Explain a half adder.
- [ ] Construct a half adder using gates.
- [ ] Explain a full adder.
- [ ] Derive full-adder equations.
- [ ] Build a full adder from half adders.
- [ ] Explain ripple carry addition.
- [ ] Explain propagation delay.
- [ ] Explain a half subtractor.
- [ ] Explain a full subtractor.
- [ ] Derive subtractor equations.
- [ ] Explain a 2-to-1 MUX.
- [ ] Explain a 4-to-1 MUX.
- [ ] Derive MUX Boolean expressions.
- [ ] Explain a DEMUX.
- [ ] Explain a decoder.
- [ ] Explain an encoder.
- [ ] Explain a priority encoder.
- [ ] Explain a comparator.
- [ ] Compare MUX and DEMUX.
- [ ] Compare encoder and decoder.
- [ ] Recognize combinational circuits from their equations or truth tables.

---

# 64. Connection to the next HKR topics

The overall learning path is:

```text
NUMBER SYSTEMS
      ↓
Binary representation
      ↓
BOOLEAN ALGEBRA
      ↓
Boolean laws and simplification
      ↓
TRUTH TABLES
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

The key idea is:

> **A combinational network takes the current binary inputs, processes them using logic, and produces outputs without storing a previous state.**

