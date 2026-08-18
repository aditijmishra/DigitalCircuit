# Sequential Networks — Digital Circuits & Computer Engineering

## Course context

A **sequential network** is a digital circuit whose output depends on:

1. The current inputs, and
2. The previous state of the circuit.

This means sequential circuits have **memory**.

The fundamental difference is:

```text
Combinational circuit:
Output = Current inputs

Sequential circuit:
Output = Current inputs + Previous state
```

Sequential networks are the foundation of:

- Flip-flops
- Registers
- Counters
- Shift registers
- Finite-state machines
- Control units
- Processor sequencing
- Memory elements

---

# 1. Combinational vs Sequential Networks

## Combinational network

A combinational circuit has no internal memory.

```text
Inputs ──→ Combinational Logic ──→ Outputs
```

Examples:

- Adders
- Subtractors
- Multiplexers
- Demultiplexers
- Encoders
- Decoders
- Comparators

The output depends only on the current input.

---

## Sequential network

A sequential circuit has memory.

```text
             ┌───────────────┐
Inputs ─────→│ Combinational │────→ Outputs
             │    Logic      │
             └───────┬───────┘
                     ↓
                 State/Memory
                     │
                     └────────→ feedback
```

The output depends on:

```text
Current inputs
+
Previous state
```

Examples:

- Latches
- Flip-flops
- Registers
- Counters
- Finite-state machines

---

# 2. What is state?

The **state** represents information stored by a sequential circuit.

For a single bit of memory:

```text
State = 0
```

or:

```text
State = 1
```

A circuit can therefore remember one of two possible states.

For `n` bits of state:

```text
Number of possible states = 2ⁿ
```

Examples:

| Storage bits | Possible states |
|---:|---:|
| 1 | 2 |
| 2 | 4 |
| 3 | 8 |
| 4 | 16 |
| 8 | 256 |

---

# 3. Why do sequential circuits need memory?

Consider a traffic-light controller.

It may need to remember:

```text
RED
↓
GREEN
↓
YELLOW
↓
RED
```

The next output depends on the current state.

Similarly, a digital clock must remember its current count.

A processor must remember information such as:

- Program state
- Registers
- Instruction-related state
- Control state

This requires sequential logic.

---

# 4. Clock signal

Most sequential digital systems use a **clock**.

A clock is a periodic digital signal:

```text
0 ──┐    ┌────┐    ┌────┐
    │    │    │    │    │
1   └────┘    └────┘    └──
```

The clock alternates between:

```text
0 and 1
```

The transitions are called edges.

---

# 5. Rising and falling edges

## Rising edge

A transition:

```text
0 → 1
```

is called a:

**rising edge** or **positive edge**.

Symbolically:

```text
↑
```

---

## Falling edge

A transition:

```text
1 → 0
```

is called a:

**falling edge** or **negative edge**.

Symbolically:

```text
↓
```

---

# 6. Clock period and frequency

A clock has:

- Period `T`
- Frequency `f`

Relationship:

```text
f = 1/T
```

and:

```text
T = 1/f
```

Example:

If:

```text
T = 10 ns
```

then:

```text
f = 1/(10 × 10⁻⁹)
```

```text
f = 100 MHz
```

---

# 7. Why clocks are important

The clock provides synchronization.

Instead of every part of a system changing at random times, state changes occur according to clock events.

Conceptually:

```text
Clock
  ↓
Storage element
  ↓
State update
  ↓
Next operation
```

This makes large digital systems predictable and manageable.

---

# 8. Latches vs Flip-Flops

Two important categories of storage elements are:

```text
Latches
Flip-flops
```

## Latch

A latch is generally **level-sensitive**.

It can respond while an enable/control signal is at a particular level.

## Flip-flop

A flip-flop is generally **edge-triggered**.

It changes state on a clock edge.

Memory rule:

```text
Latch     → level sensitive
Flip-flop → edge sensitive
```

---

# 9. SR Latch

The SR latch is one of the simplest memory circuits.

SR means:

```text
S = Set
R = Reset
```

A basic NOR-based SR latch has two inputs:

```text
S
R
```

and two outputs:

```text
Q
Q'
```

The outputs are normally complementary:

```text
Q' = NOT Q
```

---

# 10. SR latch truth table

For a NOR-based active-high SR latch:

| S | R | Q(next) | Meaning |
|---|---|---:|---|
| 0 | 0 | Q | Hold |
| 0 | 1 | 0 | Reset |
| 1 | 0 | 1 | Set |
| 1 | 1 | Invalid | Forbidden |

Important:

```text
S=1, R=0 → Set
S=0, R=1 → Reset
S=0, R=0 → Hold
S=1, R=1 → Invalid
```

Be careful: other SR latch implementations, such as NAND-based active-low versions, have a different input convention.

---

# 11. Set operation

When:

```text
S=1
R=0
```

the latch is set.

Therefore:

```text
Q=1
Q'=0
```

---

# 12. Reset operation

When:

```text
S=0
R=1
```

the latch is reset.

Therefore:

```text
Q=0
Q'=1
```

---

# 13. Hold operation

When:

```text
S=0
R=0
```

the circuit maintains its previous state.

Therefore:

```text
Q(next)=Q(previous)
```

This is the memory property.

---

# 14. Why the invalid state is a problem

For a NOR SR latch:

```text
S=1
R=1
```

forces both outputs toward the same value, violating the normal complementary relationship.

When both inputs return to the inactive state, the resulting state may become uncertain.

Therefore:

```text
S=R=1
```

is avoided in this implementation.

---

# 15. D Latch

The D latch is designed to avoid the invalid SR combination.

D means:

```text
Data
```

Typical inputs:

```text
D
Enable
```

When Enable is active:

```text
Q follows D
```

When Enable is inactive:

```text
Q holds its previous value
```

Truth table:

| Enable | D | Q(next) |
|---|---|---:|
| 0 | X | Q |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

`X` means "don't care" for that row.

---

# 16. D Flip-Flop

The D flip-flop is one of the most important sequential elements.

Inputs:

```text
D
Clock
```

Output:

```text
Q
```

For a rising-edge-triggered D flip-flop:

| Clock event | D | Q(next) |
|---|---|---:|
| Rising edge | 0 | 0 |
| Rising edge | 1 | 1 |
| No active edge | X | Q |

The key relationship is:

```text
Q(next)=D
```

at the active clock edge.

---

# 17. Why D flip-flops are important

D flip-flops are widely used for:

- Registers
- Data storage
- Pipeline stages
- State machines
- Synchronization
- Temporary storage

A D flip-flop stores exactly one bit.

Therefore:

```text
1 D flip-flop = 1 bit of storage
```

---

# 18. JK Flip-Flop

The JK flip-flop is related to the SR flip-flop but removes the forbidden input combination.

Inputs:

```text
J
K
```

Truth table:

| J | K | Q(next) | Operation |
|---|---|---:|---|
| 0 | 0 | Q | Hold |
| 0 | 1 | 0 | Reset |
| 1 | 0 | 1 | Set |
| 1 | 1 | Q' | Toggle |

The important case is:

```text
J=1, K=1
```

which causes toggling.

---

# 19. T Flip-Flop

T means:

```text
Toggle
```

Truth table:

| T | Q(next) | Operation |
|---|---:|---|
| 0 | Q | Hold |
| 1 | Q' | Toggle |

Therefore:

```text
T=0 → no change
T=1 → toggle
```

T flip-flops are especially useful in counters.

---

# 20. Flip-flop comparison

| Type | Inputs | Main operation |
|---|---|---|
| SR | S, R | Set/Reset |
| D | D | Store data |
| JK | J, K | Set/Reset/Toggle |
| T | T | Toggle |

Memory shortcuts:

```text
D → Data
T → Toggle
S → Set
R → Reset
J/K → General-purpose set/reset/toggle behavior
```

---

# 21. Characteristic tables

A characteristic table describes the next state of a flip-flop.

## D flip-flop

```text
Q(next)=D
```

| D | Q(next) |
|---|---:|
| 0 | 0 |
| 1 | 1 |

## T flip-flop

| T | Q(next) |
|---|---:|
| 0 | Q |
| 1 | Q' |

## JK flip-flop

| J | K | Q(next) |
|---|---|---:|
| 0 | 0 | Q |
| 0 | 1 | 0 |
| 1 | 0 | 1 |
| 1 | 1 | Q' |

---

# 22. Excitation tables

An **excitation table** answers the opposite question:

> What input is required to move from the current state to the desired next state?

## D flip-flop

| Q | Q(next) | D |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

Therefore:

```text
D=Q(next)
```

---

## T flip-flop

| Q | Q(next) | T |
|---|---|---:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

Therefore:

```text
T=Q⊕Q(next)
```

---

## JK flip-flop

| Q | Q(next) | J | K |
|---|---|---|---|
| 0 | 0 | 0 | X |
| 0 | 1 | 1 | X |
| 1 | 0 | X | 1 |
| 1 | 1 | X | 0 |

`X` means don't care.

---

# 23. Characteristic equation

Characteristic equations describe next-state behavior.

## D flip-flop

```text
Q(next)=D
```

## T flip-flop

```text
Q(next)=T⊕Q
```

## JK flip-flop

```text
Q(next)=JQ'+K'Q
```

These equations are useful when analyzing sequential circuits.

---

# 24. Setup time

A flip-flop cannot accept data instantaneously.

**Setup time** is the minimum time the input must be stable **before** the active clock edge.

Conceptually:

```text
        setup time
<------------------->

D ───────────── stable ───────
                         ↑
                    clock edge
```

If data changes too close to the clock edge, the flip-flop may not capture it reliably.

---

# 25. Hold time

**Hold time** is the minimum time the input must remain stable **after** the active clock edge.

```text
                    hold time
                    <-------->

D ────────────────┬──────────
                  ↑
             clock edge
```

Therefore:

```text
Setup time → before clock edge
Hold time  → after clock edge
```

---

# 26. Propagation delay

A flip-flop does not change its output exactly at the same instant as the clock edge.

The delay between the triggering event and the output transition is called **clock-to-Q propagation delay**.

```text
Clock edge
    ↓
small delay
    ↓
Q changes
```

This matters when determining the maximum operating frequency of a digital system.

---

# 27. Metastability

If an input changes very close to the sampling clock edge, a flip-flop can temporarily enter an uncertain state.

This is called **metastability**.

It is especially important when transferring signals between different clock domains.

A common solution is a **synchronizer**, often using multiple flip-flops.

Conceptually:

```text
Asynchronous input
        ↓
   Flip-flop 1
        ↓
   Flip-flop 2
        ↓
 Synchronized signal
```

---

# 28. Registers

A register is a group of flip-flops used to store multiple bits.

For example:

```text
8-bit register
=
8 flip-flops
```

Conceptually:

```text
D7 → FF → Q7
D6 → FF → Q6
D5 → FF → Q5
D4 → FF → Q4
D3 → FF → Q3
D2 → FF → Q2
D1 → FF → Q1
D0 → FF → Q0
```

All flip-flops can share the same clock.

---

# 29. Parallel register

In a parallel register, several bits are loaded at the same time.

For a 4-bit register:

```text
D3 D2 D1 D0
 ↓  ↓  ↓  ↓
FF FF FF FF
 ↓  ↓  ↓  ↓
Q3 Q2 Q1 Q0
```

All bits are stored together.

---

# 30. Shift registers

A shift register moves stored bits from one flip-flop to another.

Example:

```text
Q3 ← Q2 ← Q1 ← Q0
```

On every clock edge, the data shifts.

Applications include:

- Serial-to-parallel conversion
- Parallel-to-serial conversion
- Data delay
- Temporary storage
- Digital communication

---

# 31. Types of shift registers

Common types:

```text
SISO
SIPO
PISO
PIPO
```

## SISO

Serial In, Serial Out.

```text
Serial input → FF → FF → FF → Serial output
```

## SIPO

Serial In, Parallel Out.

```text
Serial input
     ↓
 FF → FF → FF → FF
 ↓    ↓    ↓    ↓
 Q0   Q1   Q2   Q3
```

## PISO

Parallel In, Serial Out.

Multiple bits are loaded together and shifted out one by one.

## PIPO

Parallel In, Parallel Out.

Multiple bits are loaded and read in parallel.

---

# 32. Counters

A counter is a sequential circuit that moves through a sequence of states.

Example 3-bit binary counter:

```text
000
001
010
011
100
101
110
111
000
...
```

There are:

```text
2³ = 8 states
```

for a 3-bit binary counter.

---

# 33. Up counter

An up counter counts upward:

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

Then it returns to:

```text
000
```

---

# 34. Down counter

A down counter counts downward:

```text
111
110
101
100
011
010
001
000
```

Then it returns to:

```text
111
```

---

# 35. Synchronous vs Asynchronous Counters

## Asynchronous counter

Also called a **ripple counter**.

The clock is applied to the first flip-flop, and subsequent flip-flops are triggered by preceding stages.

```text
Clock → FF1 → FF2 → FF3
```

Changes ripple through the circuit.

Advantage:

- Simple design

Disadvantage:

- Accumulated propagation delay

---

## Synchronous counter

All flip-flops receive the same clock.

```text
             ┌→ FF1
Clock ───────┼→ FF2
             └→ FF3
```

Advantages:

- Faster
- More predictable timing

---

# 36. Frequency division with flip-flops

A T flip-flop configured to toggle every active clock edge can divide the clock frequency by 2.

If:

```text
f = 100 MHz
```

the output can be:

```text
50 MHz
```

Cascading stages can produce:

```text
100 MHz
 ↓
50 MHz
 ↓
25 MHz
 ↓
12.5 MHz
```

This principle is used in frequency-divider circuits and counters.

---

# 37. Modulus of a counter

The **modulus**, or MOD number, is the number of distinct states in the counting sequence.

A 3-bit binary counter has:

```text
MOD-8
```

because:

```text
2³=8
```

A 4-bit binary counter has:

```text
MOD-16
```

because:

```text
2⁴=16
```

In general:

```text
Maximum states = 2ⁿ
```

for `n` flip-flops.

---

# 38. State diagrams

A state diagram represents states and transitions graphically.

Example:

```text
       0
   ┌───────┐
   ↓       │
  [0] → [1]
       1
```

A more complete binary sequence might be:

```text
[00] → [01] → [10] → [11]
 ↑                       │
 └───────────────────────┘
```

Each box represents a state.

Arrows represent transitions.

---

# 39. State table

A state table is similar to a truth table but includes present and next states.

Example:

| Present State | Input | Next State |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

For a D flip-flop:

```text
Q(next)=D
```

So the next state directly follows the input.

---

# 40. Finite-State Machines

A **Finite-State Machine (FSM)** is a sequential system with a finite number of states.

Basic structure:

```text
Inputs
  ↓
Combinational logic
  ↓
Next-state logic
  ↓
Flip-flops
  ↓
Present state
  ↓
Combinational logic
```

FSMs are used for:

- Traffic-light controllers
- Vending machines
- Elevator controllers
- Communication protocols
- Processor control
- Digital locks
- Industrial controllers

---

# 41. Moore machine

In a Moore machine:

```text
Output depends only on present state.
```

```text
State → Output
```

Inputs affect the next state, but not the output directly.

Advantages:

- Outputs are often easier to stabilize
- Output changes are tied to state changes

---

# 42. Mealy machine

In a Mealy machine:

```text
Output depends on:
Present state + Current input
```

```text
State + Input → Output
```

Mealy machines can respond quickly to input changes.

---

# 43. Moore vs Mealy

| Feature | Moore | Mealy |
|---|---|---|
| Output depends on | State | State + Input |
| Output changes | Usually with state changes | Can change when input changes |
| Design | Often simpler | Can be more compact |
| Typical output timing | More predictable | Potentially faster response |

Memory rule:

```text
Moore → Output = State
Mealy → Output = State + Input
```

---

# 44. Sequential circuit design procedure

A common design process is:

```text
1. Understand the problem
2. Identify inputs and outputs
3. Identify states
4. Create the state diagram
5. Create the state table
6. Choose flip-flop type
7. Create excitation table
8. Derive Boolean equations
9. Simplify equations
10. Draw the circuit
11. Verify the circuit
```

This is an important exam procedure.

---

# 45. Example: 2-bit counter

Suppose the circuit should count:

```text
00 → 01 → 10 → 11 → 00
```

State table:

| Present State | Next State |
|---|---|
| 00 | 01 |
| 01 | 10 |
| 10 | 11 |
| 11 | 00 |

There are:

```text
4 states
```

so two flip-flops are sufficient because:

```text
2²=4
```

---

# 46. Number of flip-flops required

To represent `N` states:

```text
Number of flip-flops = ceil(log₂N)
```

Examples:

### 4 states

```text
log₂4=2
```

Need:

```text
2 flip-flops
```

### 8 states

```text
log₂8=3
```

Need:

```text
3 flip-flops
```

### 10 states

```text
log₂10≈3.32
```

Need:

```text
4 flip-flops
```

because 3 flip-flops provide only 8 states.

---

# 47. Unused states

If a circuit uses fewer than all possible states, some states are unused.

Example:

A MOD-10 counter needs:

```text
10 states
```

but 4 flip-flops provide:

```text
2⁴=16 states
```

Therefore:

```text
16 - 10 = 6
```

states are unused.

A good design should consider what happens if the circuit enters an unused state.

---

# 48. Timing diagram

A timing diagram shows how signals change over time.

Example:

```text
Clock:  __|‾‾|__|‾‾|__|‾‾|__

D:      ____|‾‾‾‾‾|________

Q:      ______|‾‾‾‾‾|______
```

The exact behavior depends on the flip-flop and triggering edge.

Timing diagrams are useful for understanding:

- Clock edges
- Data sampling
- Delays
- Flip-flop behavior
- Counters
- Registers
- Shift registers

---

# 49. Race-around condition

In certain level-triggered JK flip-flop configurations, when:

```text
J=1
K=1
```

and the clock pulse remains active for too long, the output can toggle repeatedly during one clock pulse.

This is called the **race-around condition**.

It can be avoided using:

- Edge-triggered flip-flops
- Master-slave arrangements
- Proper clock pulse widths

---

# 50. Master-slave flip-flop

A master-slave arrangement uses two stages.

Conceptually:

```text
Input
  ↓
Master
  ↓
Slave
  ↓
Output
```

The two stages respond during opposite clock phases.

This helps prevent unwanted repeated changes during a clock pulse.

---

# 51. Preset and Clear

Many flip-flops have asynchronous control inputs such as:

```text
PRESET
CLEAR
```

These can force the output to a known state independently of the clock.

Typical behavior:

```text
Preset → Q=1
Clear  → Q=0
```

These inputs are often used when initializing a circuit.

Always check whether a particular device uses active-high or active-low controls.

---

# 52. Synchronous vs Asynchronous inputs

## Synchronous

The operation occurs in relation to the clock.

```text
Input → sampled at clock edge
```

## Asynchronous

The operation can affect the state independently of the clock.

Examples:

```text
Asynchronous clear
Asynchronous preset
```

This distinction is important in timing analysis.

---

# 53. Sequential networks in processors

Sequential circuits are essential inside processors.

Examples:

```text
Program Counter
Instruction Register
General-purpose Registers
Status Registers
Control Unit
Pipeline Registers
Counters
```

A processor repeatedly performs operations synchronized by a clock.

Simplified:

```text
Fetch
  ↓
Decode
  ↓
Execute
  ↓
Memory access
  ↓
Write back
  ↓
Next instruction
```

State and registers allow the processor to remember where it is in this process.

---

# 54. Sequential networks and memory

Memory systems rely on storage elements.

At a basic level:

```text
Flip-flop → stores a bit
Register  → stores multiple bits
Memory array → stores many words
```

This creates a hierarchy:

```text
Bit
 ↓
Register
 ↓
Cache
 ↓
Main memory
 ↓
Storage
```

The exact technologies differ, but sequential/state concepts are fundamental.

---

# 55. Important formulas

## Number of states

```text
2ⁿ
```

where `n` is the number of state bits.

## Required flip-flops

```text
n = ceil(log₂N)
```

where `N` is the required number of states.

## Clock frequency

```text
f=1/T
```

## Clock period

```text
T=1/f
```

## D flip-flop

```text
Q(next)=D
```

## T flip-flop

```text
Q(next)=T⊕Q
```

## JK flip-flop

```text
Q(next)=JQ'+K'Q
```

---

# 56. Common exam mistakes

## Mistake 1 — Confusing combinational and sequential circuits

Remember:

```text
Combinational → no memory
Sequential    → memory/state
```

## Mistake 2 — Confusing latch and flip-flop

```text
Latch → level-sensitive
Flip-flop → edge-triggered
```

## Mistake 3 — Forgetting the clock

Most synchronous sequential circuits operate based on clock events.

## Mistake 4 — Confusing characteristic and excitation tables

```text
Characteristic:
Inputs → Next state

Excitation:
Current state + Next state → Required inputs
```

## Mistake 5 — Confusing XOR with XNOR

```text
XOR  → different → 1
XNOR → same → 1
```

## Mistake 6 — Forgetting unused states

A 4-bit circuit has 16 possible states even if the design uses only 10.

## Mistake 7 — Ignoring setup and hold time

Data must satisfy timing requirements around the active clock edge.

---

# 57. Exam practice — Level 1

1. What is a sequential network?
2. How is a sequential circuit different from a combinational circuit?
3. What is state?
4. What is a clock?
5. What is a rising edge?
6. What is a falling edge?
7. What is a latch?
8. What is a flip-flop?
9. What is the difference between a latch and a flip-flop?
10. What does SR stand for?
11. What does D stand for?
12. What does T stand for?
13. What is the main purpose of a D flip-flop?
14. What is the main purpose of a T flip-flop?
15. What is a register?

---

# 58. Exam practice — Level 2

16. Write the truth table of an SR latch.

17. Write the characteristic table of a D flip-flop.

18. Write the characteristic table of a JK flip-flop.

19. Write the characteristic table of a T flip-flop.

20. Explain setup time.

21. Explain hold time.

22. Explain propagation delay.

23. What is metastability?

24. What is a shift register?

25. Explain SISO, SIPO, PISO and PIPO.

26. What is a counter?

27. What is the difference between synchronous and asynchronous counters?

28. What is a MOD-8 counter?

29. How many flip-flops are needed for 16 states?

30. How many flip-flops are needed for 10 states?

---

# 59. Exam practice — Level 3

31. Design a 2-bit synchronous counter.

32. Design a sequence detector using an FSM.

33. Explain the difference between Moore and Mealy machines.

34. Convert a state diagram into a state table.

35. Convert a state table into a sequential circuit.

36. Explain characteristic and excitation tables.

37. Design a counter using T flip-flops.

38. Explain race-around condition in a JK flip-flop.

39. Explain how master-slave flip-flops solve race-around.

40. Explain how sequential networks are used in a processor.

41. Explain how registers are constructed from flip-flops.

42. Explain the role of setup and hold time in synchronous digital design.

---

# 60. Mini exam

Try these without looking at the answers.

### Question 1

What is the main difference between combinational and sequential logic?

### Question 2

How many possible states can 4 state bits represent?

### Question 3

What does a D flip-flop do?

### Question 4

What happens when T=1 in a T flip-flop?

### Question 5

What happens when J=K=1 in a JK flip-flop?

### Question 6

What is setup time?

### Question 7

What is hold time?

### Question 8

How many flip-flops are needed for 10 states?

### Question 9

What is the difference between synchronous and asynchronous counters?

### Question 10

What is the difference between Moore and Mealy machines?

---

# 61. Mini exam answers

```text
1. Combinational logic depends only on current inputs; sequential logic also depends on stored state.

2. 2⁴ = 16 states.

3. At its active clock edge, a D flip-flop stores the value of D.

4. It toggles.

5. It toggles.

6. Minimum time the data input must be stable before the active clock edge.

7. Minimum time the data input must remain stable after the active clock edge.

8. 4 flip-flops.

9. Synchronous counters clock all stages together; asynchronous counters allow changes to ripple between stages.

10. Moore output depends only on state; Mealy output depends on state and input.
```

---

# 62. Quick comparison table

| Topic | Key idea |
|---|---|
| Combinational | No memory |
| Sequential | Has state/memory |
| Latch | Level-sensitive |
| Flip-flop | Edge-triggered |
| SR | Set/reset |
| D | Store data |
| JK | Set/reset/toggle |
| T | Toggle |
| Register | Stores multiple bits |
| Shift register | Moves bits |
| Counter | Moves through states |
| FSM | State-based controller |
| Moore | Output depends on state |
| Mealy | Output depends on state + input |

---

# 63. Final cheat sheet

## Sequential logic

```text
Output = Current input + Previous state
```

## Clock

```text
Rising edge: 0 → 1
Falling edge: 1 → 0
```

## Storage

```text
1 flip-flop = 1 bit
n flip-flops = n bits
```

## States

```text
n bits → 2ⁿ states
```

## SR

```text
S=1 → Set
R=1 → Reset
```

For a NOR-based active-high SR latch:

```text
S=R=0 → Hold
S=R=1 → Invalid
```

## D

```text
Q(next)=D
```

## JK

```text
00 → Hold
01 → Reset
10 → Set
11 → Toggle
```

## T

```text
0 → Hold
1 → Toggle
```

## Timing

```text
Setup → before clock edge
Hold  → after clock edge
```

## Counters

```text
n flip-flops → up to 2ⁿ states
```

## FSM

```text
Present state
      ↓
Next-state logic
      ↓
Next state
```

## Moore

```text
Output = State
```

## Mealy

```text
Output = State + Input
```

---

# 64. What you should be able to do before moving on

- [ ] Define a sequential network.
- [ ] Explain the difference between combinational and sequential circuits.
- [ ] Explain state and memory.
- [ ] Explain clock signals.
- [ ] Identify rising and falling edges.
- [ ] Explain latches.
- [ ] Explain flip-flops.
- [ ] Understand SR, D, JK and T flip-flops.
- [ ] Construct flip-flop characteristic tables.
- [ ] Construct flip-flop excitation tables.
- [ ] Explain setup time.
- [ ] Explain hold time.
- [ ] Explain propagation delay.
- [ ] Understand metastability.
- [ ] Explain registers.
- [ ] Explain shift registers.
- [ ] Explain SISO, SIPO, PISO and PIPO.
- [ ] Explain counters.
- [ ] Distinguish synchronous and asynchronous counters.
- [ ] Calculate the modulus of a counter.
- [ ] Calculate the number of flip-flops needed for a given number of states.
- [ ] Draw and interpret state diagrams.
- [ ] Create state tables.
- [ ] Explain finite-state machines.
- [ ] Distinguish Moore and Mealy machines.
- [ ] Understand race-around condition.
- [ ] Understand preset and clear.
- [ ] Explain how sequential logic is used in processors.

---

# 65. Connection to the HKR course

The major topics connect together like this:

```text
NUMBER SYSTEMS
      ↓
Binary representation
      ↓
BOOLEAN ALGEBRA
      ↓
Boolean expressions
      ↓
TRUTH TABLES
      ↓
COMBINATIONAL NETWORKS
      ↓
Logic without memory
      ↓
SEQUENTIAL NETWORKS
      ↓
Memory + State + Clock
      ↓
Flip-flops
      ↓
Registers + Counters
      ↓
Finite-State Machines
      ↓
PROCESSOR PRINCIPLES
      ↓
CPU control + Registers + Sequencing
      ↓
MEMORIES AND I/O
```

## Final key idea

> **A sequential network is a digital circuit whose behavior depends not only on the current inputs but also on its stored state.**

The most important concepts to master are:

```text
State
Clock
Latch
Flip-flop
D / JK / T / SR
Setup time
Hold time
Registers
Shift registers
Counters
State diagrams
State tables
FSMs
Moore / Mealy
```

Once these are clear, you have the foundation needed for understanding **processor principles, memory systems, and I/O**.
