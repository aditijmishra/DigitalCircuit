# Principles of Processors

## Digital & Computer Technology — Study Notes

> **Purpose:** Detailed study notes for understanding how a processor works from the digital-logic level upward.
>
> **Prerequisites:** Number systems, Boolean algebra, logic gates, combinational networks, sequential networks, and basic data storage.

---

# 1. What is a processor?

A **processor**, or **Central Processing Unit (CPU)**, is the part of a computer that executes instructions.

At a high level:

```text
Program
   ↓
Instructions
   ↓
CPU
   ↓
Operations on data
   ↓
Results
```

A processor repeatedly performs a cycle similar to:

```text
Fetch → Decode → Execute → Store
   ↑                         |
   └─────────────────────────┘
```

This is the fundamental idea behind instruction execution.

A processor contains several important components:

```text
+--------------------------------------+
|                CPU                   |
|                                      |
|  +------------+    +-------------+  |
|  | Registers  |    | Control Unit|  |
|  +------------+    +-------------+  |
|          |                 |          |
|          +--------+--------+          |
|                   |                   |
|              +---------+              |
|              |   ALU   |              |
|              +---------+              |
|                   |                   |
|             Status/Flags              |
+--------------------------------------+
          |
     Memory / I/O
```

The exact organization differs between processor architectures, but these concepts are fundamental.

---

# 2. The main responsibilities of a processor

A CPU generally needs to:

1. Fetch instructions.
2. Decode instructions.
3. Fetch required operands.
4. Perform arithmetic or logical operations.
5. Store results.
6. Update processor state.
7. Control communication with memory and I/O.

For example, suppose an instruction means:

```text
ADD R1, R2
```

Conceptually:

```text
R1 + R2
   ↓
  ALU
   ↓
result
   ↓
register
```

The processor must know:

- which registers are involved
- which operation is required
- where the result should go
- how the next instruction should be selected

---

# 3. Processor as a state machine

A useful way to understand a processor is as a **large sequential digital system**.

It has:

```text
Inputs
  ↓
Combinational logic
  ↓
State elements
  ↓
Next state
```

The processor's state can include:

- register values
- program counter
- status flags
- control state
- other architectural state

This connects directly to the topic of **sequential networks**.

A simplified model:

```text
                 +----------------+
Inputs -------->| Combinational  |
                 |    Logic       |
                 +-------+--------+
                         |
                         v
                 +---------------+
                 | State /       |
                 | Registers     |
                 +-------+-------+
                         |
                         +------> feedback
```

A processor is therefore not just "a calculator." It is a controlled sequential system.

---

# 4. CPU architecture vs implementation

Two terms are important.

## Instruction Set Architecture — ISA

The ISA describes what the processor exposes to software.

It includes things such as:

- instructions
- registers visible to programs
- data types
- addressing modes
- memory model
- instruction encoding
- behavior of instructions

Examples of ISAs include:

- x86-64
- ARM
- RISC-V

## Microarchitecture

Microarchitecture describes how the processor is internally implemented.

Two processors can implement the same ISA using very different internal designs.

For example:

```text
Same ISA
   ↓
Processor A → implementation A
Processor B → implementation B
```

Software can use the same instruction set even though the hardware organization differs.

---

# 5. Instructions

An **instruction** tells the processor what operation to perform.

An instruction can conceptually contain:

```text
+----------------+-------------------+
|    Operation   |     Operands      |
+----------------+-------------------+
```

For example:

```text
ADD R1, R2
```

The operation is:

```text
ADD
```

The operands are:

```text
R1
R2
```

At machine level, instructions are encoded as binary patterns.

---

# 6. Machine code

Processors ultimately execute binary-encoded instructions.

A simplified instruction might look like:

```text
11001010 0011 0101
```

The exact interpretation depends on the ISA.

For example, fields might represent:

```text
+--------+------+-------+
| opcode | src  | dest  |
+--------+------+-------+
```

Where:

```text
opcode → operation
src    → source register
dest   → destination register
```

Real instruction formats can be much more complicated.

---

# 7. Opcode

An **opcode**, or operation code, identifies the operation to perform.

Examples conceptually:

```text
0001 → ADD
0010 → SUB
0011 → AND
0100 → OR
0101 → LOAD
0110 → STORE
```

This is only an example.

Actual opcode values depend on the ISA.

The processor's control logic interprets the opcode and generates the signals needed to execute the instruction.

---

# 8. Registers

Registers are small, very fast storage elements inside the processor.

They hold information needed during execution.

Examples include:

- general-purpose registers
- program counter
- instruction register
- stack pointer
- status/flag register

Conceptually:

```text
+----------------+
|    Registers   |
+----------------+
 |   |   |   |
 R0  R1  R2  R3
```

Registers are much smaller in number than main memory.

---

# 9. General-purpose registers

General-purpose registers can hold values used by instructions.

For example:

```text
R1 = 25
R2 = 10
```

An addition instruction could produce:

```text
R3 = R1 + R2
```

Therefore:

```text
R3 = 35
```

At the hardware level:

```text
R1 ─────┐
        ├──> ALU ───> R3
R2 ─────┘
```

---

# 10. Program Counter

The **Program Counter (PC)** contains information identifying the location of the next instruction to fetch.

A simplified sequence:

```text
PC
 ↓
Memory
 ↓
Instruction
 ↓
CPU
```

After fetching an ordinary sequential instruction, the PC normally advances to the next instruction.

For example:

```text
PC = 1000

fetch instruction at 1000

PC → next instruction
```

The exact amount added depends on the architecture and instruction format.

---

# 11. Instruction Register

The **Instruction Register (IR)** can hold the currently fetched instruction while the processor decodes and executes it.

Conceptually:

```text
Memory
   |
   v
Instruction Register
   |
   v
Decoder
```

The processor can then determine:

```text
What operation?
Which operands?
Where is the result?
```

---

# 12. Stack Pointer

The **Stack Pointer (SP)** identifies the current location of the processor's stack.

The stack is commonly used for:

- function calls
- return addresses
- local data
- saved registers
- temporary values

A simplified stack:

```text
+-------------+
|   data      |
+-------------+
|   data      |
+-------------+
| return addr |
+-------------+
       ↑
      SP
```

The exact direction in which the stack grows depends on the architecture.

---

# 13. Status and flag registers

Processors often maintain status information about operations.

Common flags include:

- Zero flag
- Carry flag
- Negative/sign flag
- Overflow flag

For example, after an arithmetic operation:

```text
Result = 0
```

The processor may set:

```text
Zero = 1
```

A conditional branch can then test the flag.

---

# 14. Arithmetic Logic Unit

The **Arithmetic Logic Unit (ALU)** performs arithmetic and logical operations.

Typical operations include:

### Arithmetic

```text
ADD
SUB
INC
DEC
```

### Logical

```text
AND
OR
XOR
NOT
```

### Comparison

```text
equal
less than
greater than
```

A simplified ALU:

```text
          Operand A
              |
              v
        +-----------+
        |           |
Operand |    ALU    | → Result
B ----->|           |
        +-----------+
             |
           Flags
```

The ALU is one of the most important functional blocks in a processor.

---

# 15. ALU and Boolean logic

The ALU is built from digital logic.

For example, bitwise AND can be implemented using AND gates.

```text
A ───┐
     AND ─── Result
B ───┘
```

A multi-bit AND operation uses multiple gates:

```text
A0 ─┐
    AND → R0

A1 ─┐
    AND → R1

A2 ─┐
    AND → R2
```

This demonstrates the connection:

```text
Boolean algebra
      ↓
Logic gates
      ↓
Combinational circuits
      ↓
ALU
      ↓
Processor
```

---

# 16. Binary addition inside the ALU

Binary addition can be constructed using **full adders**.

A full adder has:

```text
A
B
Carry-in
```

and produces:

```text
Sum
Carry-out
```

Conceptually:

```text
A ------+
         |
B ------>| Full Adder |----> Sum
         |
Cin ---->|
         |
         +-------------> Cout
```

Multiple full adders can be connected to create a multi-bit adder.

For example, a 4-bit adder:

```text
       +-----+     +-----+     +-----+     +-----+
A0 --->| FA0 |---->| FA1 |---->| FA2 |---->| FA3 |
B0 --->|     |     |     |     |     |     |     |
       +-----+     +-----+     +-----+     +-----+
          |           |           |           |
          S0          S1          S2          S3
```

The carry propagates between stages.

---

# 17. Subtraction in the ALU

Binary subtraction can be implemented using two's complement.

To calculate:

```text
A - B
```

the hardware can calculate:

```text
A + (-B)
```

In two's complement:

```text
-B = NOT(B) + 1
```

Therefore:

```text
A - B
=
A + NOT(B) + 1
```

This allows addition hardware to also support subtraction.

---

# 18. ALU control

The ALU needs to know which operation to perform.

A simplified control input might be:

```text
ALU control

000 → ADD
001 → SUB
010 → AND
011 → OR
100 → XOR
```

The actual encoding is architecture-specific.

The important idea is:

```text
Instruction
    ↓
Control unit
    ↓
ALU control signals
    ↓
ALU operation
```

---

# 19. Control Unit

The **Control Unit** coordinates processor operations.

It determines which hardware components should:

- read data
- write data
- perform an ALU operation
- access memory
- update registers
- change the program counter

Conceptually:

```text
                 Instruction
                     |
                     v
              +-------------+
              |   Decoder   |
              +------+------+
                     |
             Control signals
          +----------+----------+
          |          |          |
          v          v          v
        ALU      Registers    Memory
```

---

# 20. Datapath

The **datapath** is the collection of hardware that carries and transforms data.

It can include:

- registers
- ALU
- multiplexers
- buses
- shifters
- connections to memory

A simplified datapath:

```text
Register A ──┐
             v
           +-----+
Register B → ALU | → Register
           +-----+
```

The control unit tells the datapath what to do.

A useful distinction:

```text
Datapath → moves/processes data

Control → tells datapath what to do
```

---

# 21. Multiplexers

A **multiplexer (MUX)** selects one of several inputs.

For example:

```text
A ----\
B -----\
C ------> MUX ----> Output
D -----/
```

A control signal determines which input is selected.

Multiplexers are extremely important inside processors because many operations require choosing between possible data sources.

For example:

```text
Register A ----\
                MUX → ALU input
Immediate -----/
Memory data ---/
```

---

# 22. Processor buses

A bus is a group of signals used to transfer information.

Three conceptual categories are:

### Data bus

Carries data.

### Address bus

Carries addresses.

### Control signals

Carry control information.

Simplified:

```text
             CPU
              |
     +--------+--------+
     |        |        |
   Data    Address   Control
    Bus      Bus      Signals
     |        |        |
     +--------+--------+
              |
           Memory/I/O
```

Modern systems can use more complex interconnects, but these concepts are fundamental.

---

# 23. Fetch–decode–execute cycle

This is one of the most important concepts.

A processor repeatedly executes instructions.

## Step 1 — Fetch

The CPU uses the PC to identify the next instruction.

```text
PC → Memory
```

The instruction is transferred into the processor.

```text
Memory → Instruction Register
```

## Step 2 — Decode

The control logic interprets the instruction.

```text
Instruction
     ↓
Opcode / operands
     ↓
Control signals
```

## Step 3 — Execute

The processor performs the operation.

Examples:

```text
ADD → ALU
LOAD → memory read
STORE → memory write
BRANCH → update PC
```

## Step 4 — Write back

If necessary, the result is stored in a register or memory.

Then the processor continues with another instruction.

---

# 24. Example: ADD instruction

Imagine:

```text
ADD R3, R1, R2
```

Meaning:

```text
R3 = R1 + R2
```

Suppose:

```text
R1 = 7
R2 = 5
```

### Fetch

The CPU obtains the instruction from memory.

### Decode

The processor determines:

```text
operation = ADD
source 1 = R1
source 2 = R2
destination = R3
```

### Execute

The ALU receives:

```text
7
5
```

and performs:

```text
7 + 5 = 12
```

### Write back

```text
R3 = 12
```

The complete conceptual path:

```text
R1 ─────┐
        ├──> ALU ───> R3
R2 ─────┘
```

---

# 25. Example: LOAD instruction

Suppose:

```text
LOAD R1, [1000]
```

Conceptually:

```text
Read memory location 1000
and put its value into R1.
```

Execution:

```text
Instruction
     ↓
Decode
     ↓
Address = 1000
     ↓
Memory read
     ↓
Data
     ↓
R1
```

This demonstrates that processor instructions can interact with memory.

---

# 26. Example: STORE instruction

Suppose:

```text
STORE R1, [1000]
```

The processor sends:

```text
Address = 1000
Data = contents of R1
Write = enabled
```

Conceptually:

```text
R1
 |
 v
Data bus ───────> Memory
                   ^
                   |
              Address 1000
```

---

# 27. Branch instructions

A branch changes the normal sequence of execution.

Normally:

```text
Instruction A
Instruction B
Instruction C
Instruction D
```

A branch might cause:

```text
Instruction A
      ↓
branch
      ↓
Instruction X
```

The processor accomplishes this by changing the PC.

---

# 28. Conditional branches

A conditional branch depends on a condition.

Example:

```text
if R1 == 0:
    branch to address X
```

The ALU or comparison logic determines whether the condition is true.

Conceptually:

```text
Comparison
    ↓
Zero / condition flag
    ↓
Control logic
    ↓
Update PC?
```

This is how processor hardware supports constructs such as:

```text
if
while
for
```

At machine level, these become comparisons and branches.

---

# 29. Function calls

A function call requires the processor to remember where execution should return.

Conceptually:

```text
main
 |
 | CALL function
 v
function
 |
 | RETURN
 v
main continues
```

The return address can be stored using a stack or another architectural mechanism.

This connects the processor to:

- stack pointer
- registers
- memory
- control-flow instructions

---

# 30. Clock

A synchronous processor uses a **clock signal** to coordinate state changes.

Conceptually:

```text
Clock:

__|‾|__|‾|__|‾|__|‾|__
```

Each clock cycle provides timing events for sequential logic.

Registers commonly capture new values at defined clock edges.

Simplified:

```text
Combinational logic
       ↓
     Register
       ↓
Combinational logic
       ↓
     Register
```

The clock coordinates the transfer between states.

---

# 31. Clock frequency

Clock frequency is measured in hertz.

Examples:

```text
1 MHz = 1,000,000 cycles/second
1 GHz = 1,000,000,000 cycles/second
```

A higher clock frequency does **not** automatically mean a faster processor.

Performance also depends on:

- instructions per cycle
- microarchitecture
- cache behavior
- memory latency
- instruction dependencies
- branch behavior
- number of cores
- workload

---

# 32. Clock cycle

A clock cycle is one period of the processor's clock.

If:

```text
frequency = 2 GHz
```

then the clock period is:

```text
T = 1 / f
```

Therefore:

```text
T = 1 / 2,000,000,000
  = 0.5 ns
```

So one cycle takes approximately:

```text
0.5 nanoseconds
```

---

# 33. CPI and IPC

Two useful performance concepts are:

## CPI — Cycles Per Instruction

Average number of clock cycles required per instruction.

Lower CPI can be better.

## IPC — Instructions Per Cycle

Average number of instructions completed per cycle.

Higher IPC can be better.

They are approximately related by:

```text
IPC ≈ 1 / CPI
```

for a simplified interpretation.

---

# 34. Processor performance

A simplified CPU execution-time relationship is:

```text
CPU time
=
Instruction count
×
CPI
×
Clock cycle time
```

Since:

```text
clock cycle time = 1 / clock frequency
```

we can write:

```text
CPU time
=
Instruction count × CPI
--------------------------------
       Clock frequency
```

This equation is extremely useful for understanding processor performance.

---

# 35. RISC and CISC

Two broad design philosophies are often discussed.

## RISC

**Reduced Instruction Set Computer**

Typical characteristics include:

- relatively simple instructions
- emphasis on register operations
- regular instruction formats in many designs
- load/store organization in many RISC ISAs

Examples include ARM and RISC-V.

## CISC

**Complex Instruction Set Computer**

Historically associated with:

- richer instruction sets
- more complex instruction encodings
- instructions capable of performing more varied operations

x86 is commonly classified as a CISC ISA.

Modern processors blur some of these distinctions internally.

---

# 36. Load/store architecture

In a load/store architecture:

```text
LOAD  → memory → register
STORE → register → memory
```

Arithmetic instructions generally operate on registers.

Example:

```text
LOAD R1, [A]
LOAD R2, [B]
ADD  R3, R1, R2
STORE R3, [C]
```

Conceptually:

```text
Memory A ──> R1 ──┐
                  ├──> ALU ──> R3 ──> Memory C
Memory B ──> R2 ──┘
```

This makes the datapath organization easier to reason about.

---

# 37. Instruction formats

An instruction can contain fields such as:

```text
+---------+---------+---------+---------+
| Opcode  | Source  | Source  | Dest.   |
+---------+---------+---------+---------+
```

Another instruction might contain:

```text
+---------+---------+-------------------+
| Opcode  | Reg     | Immediate value   |
+---------+---------+-------------------+
```

Common field types include:

- opcode
- register identifiers
- immediate values
- addressing information
- function/sub-operation fields

The exact layout depends on the ISA.

---

# 38. Immediate values

An **immediate** is a constant embedded directly in an instruction.

For example:

```text
ADD R1, R1, #5
```

Conceptually:

```text
R1 = R1 + 5
```

The value `5` is part of the instruction rather than being fetched from another memory location.

This can avoid an additional memory access.

---

# 39. Addressing modes

An addressing mode determines how an instruction obtains an operand or address.

Common conceptual forms include:

### Immediate

```text
ADD R1, #10
```

Value is directly in instruction.

### Register

```text
ADD R1, R2
```

Operand comes from a register.

### Direct/absolute

```text
LOAD R1, [1000]
```

Instruction contains a memory address.

### Register indirect

```text
LOAD R1, [R2]
```

R2 contains the address.

### Base + offset

```text
LOAD R1, [R2 + 8]
```

Useful for arrays, structures, and stack frames.

---

# 40. Memory-mapped I/O

In many systems, I/O devices are accessed through addresses.

Conceptually:

```text
Address range
+-------------------+
| RAM               |
+-------------------+
| Device registers  |
+-------------------+
```

The CPU performs reads/writes, and certain addresses correspond to hardware registers rather than ordinary RAM.

For example:

```text
WRITE [device_address], value
```

could configure a hardware device.

This is called **memory-mapped I/O**.

---

# 41. Interrupts

An **interrupt** allows hardware or software to request processor attention.

Without interrupts, a CPU might repeatedly check a device:

```text
Is data ready?
Is data ready?
Is data ready?
Is data ready?
```

This is polling.

With an interrupt:

```text
Device
  |
  | interrupt
  v
CPU
  |
  v
interrupt handler
```

The processor can perform other work until attention is needed.

---

# 42. Interrupt handling

A simplified sequence:

```text
1. CPU executes normal program.
2. Device raises an interrupt.
3. CPU recognizes the interrupt.
4. CPU saves necessary state.
5. CPU transfers control to an interrupt handler.
6. Handler services the event.
7. CPU restores state.
8. Original program continues.
```

The exact mechanism is architecture-dependent.

---

# 43. Processor state

Processor state can include:

```text
Program Counter
Registers
Status Flags
Control State
```

When an interrupt or function call occurs, preserving appropriate state is essential.

This is why registers and memory are closely connected to processor control flow.

---

# 44. Pipelining

A simple processor might complete one instruction before starting the next.

A **pipeline** overlaps stages of multiple instructions.

For example:

```text
Instruction stages:

Fetch
Decode
Execute
Memory
Writeback
```

Without pipelining:

```text
I1: F D E M W
I2:           F D E M W
```

With pipelining:

```text
I1: F D E M W
I2:   F D E M W
I3:     F D E M W
I4:       F D E M W
```

The goal is to increase instruction throughput.

---

# 45. Pipeline hazards

Pipelining introduces problems called **hazards**.

## Data hazard

An instruction depends on a previous instruction's result.

```text
ADD R1, R2, R3
SUB R4, R1, R5
```

The second instruction needs the result of the first.

## Control hazard

A branch changes which instruction should execute next.

```text
BEQ ...
```

The processor may have already fetched instructions from the wrong path.

## Structural hazard

Two operations require the same hardware resource at the same time.

Processors use techniques such as forwarding, stalls, scheduling, and branch prediction to handle these problems.

---

# 46. Superscalar processors

A superscalar processor can potentially start or execute multiple instructions in parallel during a clock cycle.

Conceptually:

```text
Instruction stream
       |
       v
+------+------+------+
| Unit | Unit | Unit |
+------+------+------+
   |      |      |
   v      v      v
 ALU    ALU    Load/Store
```

This requires sophisticated scheduling and dependency management.

---

# 47. Multiple cores

A processor can contain multiple CPU cores.

Conceptually:

```text
+--------------------------------+
|            CPU                 |
|                                |
| +------+  +------+  +------+  |
| |Core 0|  |Core 1|  |Core 2|  |
| +------+  +------+  +------+  |
|                                |
+--------------------------------+
```

Each core can execute instructions.

Multiple cores allow parallel execution when software and the operating system can take advantage of it.

---

# 48. Cache hierarchy

Modern processors often have multiple cache levels.

A simplified example:

```text
CPU core
   ↓
L1 cache
   ↓
L2 cache
   ↓
L3 cache
   ↓
RAM
```

Generally:

```text
L1 → smaller and faster
L2 → larger and slower
L3 → larger and often shared
RAM → much larger and slower
```

Actual designs differ substantially.

---

# 49. Why cache matters to processors

A processor can execute instructions extremely quickly compared with the latency of accessing main memory.

If every instruction or data access required waiting for RAM, performance could suffer.

Cache reduces this problem by keeping frequently/recently used data closer to the CPU.

```text
CPU
 ↓
L1
 ↓
L2
 ↓
L3
 ↓
RAM
```

This is an application of **locality**.

---

# 50. Branch prediction

Branches create uncertainty about which instruction comes next.

A processor may predict the likely path.

Example:

```text
if condition:
    A
else:
    B
```

The processor predicts:

```text
A
```

and begins preparing instructions from that path.

If the prediction is correct:

```text
less disruption
```

If incorrect:

```text
wrong-path work discarded
correct path fetched
```

Branch prediction is one of the techniques used by modern high-performance processors.

---

# 51. Out-of-order execution

Some modern processors can execute independent instructions in an order different from their original program order, while preserving the required architectural behavior.

Example:

```text
Instruction 1 → waiting for memory
Instruction 2 → independent
```

Instead of allowing the CPU to remain completely idle, hardware may execute Instruction 2 first.

Conceptually:

```text
Program order:
I1 → I2 → I3

Possible internal execution:
I2 → I3 → I1

Architectural result:
still behaves as required by the ISA
```

This requires sophisticated dependency tracking and retirement mechanisms.

---

# 52. The role of sequential logic

Processor registers are sequential storage elements.

For example:

```text
Register
   ↑
Clock
```

The processor combines:

```text
Combinational logic
+
Sequential storage
+
Control
```

This is why studying sequential networks is important before studying processor architecture.

---

# 53. Processor datapath example

Consider a simplified processor:

```text
                  +----------------+
                  | Control Unit   |
                  +-------+--------+
                          |
                     control signals
                          |
                          v
+---------+       +-------------+       +---------+
| Reg A   |------>|             |------>| Reg C   |
+---------+       |     ALU     |       +---------+
                  |             |
+---------+------>|             |
| Reg B   |       +-------------+
+---------+
```

The control unit decides:

```text
which registers are read
which ALU operation occurs
which register receives the result
```

This is the essence of a datapath/control design.

---

# 54. Processor and memory interaction

A CPU rarely operates completely independently.

Typical execution:

```text
CPU
 |
 +---- instruction fetch ----> Memory
 |
 +<--- instruction -----------+
 |
 +---- data read ------------> Memory
 |
 +<--- data ------------------+
 |
 +---- result write ---------> Register
```

The processor continuously interacts with memory during program execution.

---

# 55. Von Neumann architecture

A classic computer organization is the **Von Neumann architecture**.

Instructions and data share the same main memory system.

Conceptually:

```text
              +--------+
              |  CPU   |
              +---+----+
                  |
              +---+---+
              |Memory |
              |       |
              |Data   |
              |Code   |
              +-------+
```

This makes program instructions and data part of a common memory system.

---

# 56. Harvard architecture

In a Harvard-style organization, instruction and data memories/interfaces are separated.

```text
              +--------+
              |  CPU   |
              +---+----+
                  |
          +-------+-------+
          |               |
     Instruction        Data
       memory           memory
```

This can allow instruction and data accesses to occur independently.

Many real processors use architectures that combine ideas from both approaches.

---

# 57. Von Neumann bottleneck

When instructions and data share a communication path or memory system, bandwidth between CPU and memory can become a limiting factor.

This is commonly called the **Von Neumann bottleneck**.

Conceptually:

```text
              CPU
               |
               | limited transfer
               |
             Memory
```

Caches, wider interfaces, multiple memory channels, prefetching, and other techniques help reduce the practical impact.

---

# 58. Endianness

When multi-byte values are stored in memory, the byte order matters.

Two common conventions:

- little-endian
- big-endian

Suppose:

```text
32-bit value:

0x12345678
```

It consists of bytes:

```text
12 34 56 78
```

In little-endian memory, the least significant byte is stored first:

```text
78 56 34 12
```

In big-endian memory:

```text
12 34 56 78
```

Endianness is about **byte ordering**, not the ordering of individual bits within a byte.

---

# 59. Processor word size

A processor's word size describes an important aspect of the architecture.

Common examples:

```text
32-bit
64-bit
```

A 64-bit processor can operate with 64-bit registers and values as defined by its architecture.

However:

> "64-bit processor" does not simply mean every operation is always 64 bits.

The ISA may support many operand sizes.

---

# 60. Instruction execution — complete example

Consider:

```text
LOAD R1, [1000]
ADD  R2, R1, R3
STORE R2, [2000]
```

Conceptually:

### Instruction 1

```text
PC
 ↓
Fetch LOAD
 ↓
Decode
 ↓
Address = 1000
 ↓
Memory read
 ↓
R1
```

### Instruction 2

```text
Fetch ADD
 ↓
Decode
 ↓
Read R1 and R3
 ↓
ALU
 ↓
R2
```

### Instruction 3

```text
Fetch STORE
 ↓
Decode
 ↓
Read R2
 ↓
Address = 2000
 ↓
Memory write
```

The entire sequence:

```text
Memory[1000]
     ↓
    R1
     ↓
    ALU ← R3
     ↓
    R2
     ↓
Memory[2000]
```

This is a very useful mental model for understanding processors.

---

# 61. How high-level programming becomes processor operations

Consider:

```c
x = a + b;
```

At a high level, this looks like one simple operation.

At lower levels, it may involve:

```text
load a
load b
add
store x
```

Then those operations are represented by machine instructions.

Ultimately:

```text
C code
 ↓
Compiler
 ↓
Assembly / machine instructions
 ↓
CPU fetch
 ↓
Decode
 ↓
Datapath
 ↓
ALU / registers / memory
 ↓
Result
```

This is the connection between programming and computer hardware.

---

# 62. Assembly language

Assembly language provides a human-readable representation of machine instructions.

Example:

```asm
LOAD R1, [1000]
LOAD R2, [1004]
ADD  R3, R1, R2
STORE R3, [1008]
```

The exact syntax depends on the processor architecture.

Assembly is useful for learning:

- registers
- memory access
- instructions
- control flow
- stack behavior
- processor state

---

# 63. Processor reset

A processor needs a known initial state when it starts or resets.

A reset mechanism can initialize important state such as:

- program counter
- control logic
- registers
- execution mode

The processor then begins executing from an architecture-defined starting location.

This starts the process that eventually loads or begins the operating system or firmware.

---

# 64. Firmware and boot process

A simplified boot process is:

```text
Power on
   ↓
Processor reset
   ↓
Firmware starts
   ↓
Hardware initialization
   ↓
Bootloader / operating system loading
   ↓
Operating system
   ↓
Applications
```

The details vary by system.

The key idea is that a processor needs initial instructions to begin meaningful execution.

---

# 65. Performance: what actually matters?

Do not judge a processor only by clock frequency.

A simplified performance relationship is:

```text
Performance depends on:

Instruction count
CPI
Clock frequency
```

But modern processors also depend heavily on:

- cache hierarchy
- branch prediction
- pipeline depth
- instruction-level parallelism
- memory subsystem
- number of cores
- workload characteristics
- compiler quality

For example:

```text
CPU A = 4 GHz
CPU B = 3 GHz
```

CPU A is **not automatically faster**.

Architecture matters.

---

# 66. Common misconceptions

## Misconception 1

> "The CPU only performs arithmetic."

False.

It also:

- controls program flow
- loads/stores data
- compares values
- performs logical operations
- manages registers
- interacts with memory and I/O

---

## Misconception 2

> "RAM is the CPU."

False.

RAM is memory.

The CPU contains processing and control hardware plus registers.

---

## Misconception 3

> "A higher GHz always means a faster CPU."

False.

Clock frequency is only one performance factor.

---

## Misconception 4

> "An instruction is always completed in one clock cycle."

Not necessarily.

Some processors use multiple stages, pipelines, caches, variable latency, and complex execution mechanisms.

---

## Misconception 5

> "64-bit means the CPU can only process 64-bit numbers."

False.

A 64-bit architecture can support operations on different operand sizes.

---

# 67. Connecting the course topics

The topics you listed form a logical progression:

```text
1. Number systems
       ↓
2. Data storage
       ↓
3. Truth tables
       ↓
4. Boolean algebra
       ↓
5. Combinational networks
       ↓
6. Sequential networks
       ↓
7. Principles of processors
       ↓
8. Memories and I/O
```

Here is the connection.

### Number systems

Teach how binary information is represented.

```text
101101₂
```

### Data storage

Teaches how bits can be retained.

```text
0 / 1
```

### Truth tables

Describe relationships between binary inputs and outputs.

```text
A B | Y
0 0 | 0
0 1 | 1
1 0 | 1
1 1 | 0
```

### Boolean algebra

Provides mathematical rules for digital logic.

### Combinational networks

Build useful circuits from logic gates.

Examples:

```text
Adder
Multiplexer
Decoder
ALU components
```

### Sequential networks

Add memory/state.

Examples:

```text
Flip-flops
Registers
Counters
```

### Processor

Combines these concepts.

```text
Logic
+
Registers
+
ALU
+
Control
+
Memory interface
=
Processor
```

---

# 68. Important terms to know

| Term | Meaning |
|---|---|
| CPU | Central Processing Unit |
| ISA | Instruction Set Architecture |
| ALU | Arithmetic Logic Unit |
| PC | Program Counter |
| IR | Instruction Register |
| SP | Stack Pointer |
| Register | Small fast storage inside CPU |
| Opcode | Encoded operation identifier |
| Datapath | Hardware that moves/processes data |
| Control Unit | Generates/control execution signals |
| MUX | Multiplexer |
| Clock | Timing signal for synchronous logic |
| CPI | Cycles Per Instruction |
| IPC | Instructions Per Cycle |
| ISA | Interface between software and processor architecture |
| Pipeline | Overlapping instruction-processing stages |
| Cache | Fast memory holding likely-needed data/instructions |
| Interrupt | Event requesting CPU attention |
| Branch | Instruction changing control flow |
| Endianness | Byte ordering of multi-byte values |

---

# 69. Exam-style questions

## Conceptual questions

1. What is the purpose of a processor?
2. Explain the fetch-decode-execute cycle.
3. What is the difference between ISA and microarchitecture?
4. What is the role of the ALU?
5. What is the role of the control unit?
6. What is the purpose of the program counter?
7. What is an instruction register?
8. What is a register?
9. What is a datapath?
10. What is a multiplexer and why is it useful inside a CPU?
11. Explain the difference between a data bus and an address bus.
12. Why does a processor need a clock?
13. What is an interrupt?
14. What is a branch instruction?
15. Why are caches needed?
16. What is pipelining?
17. What is a pipeline hazard?
18. Explain the difference between RISC and CISC.
19. What is memory-mapped I/O?
20. Explain little-endian and big-endian byte order.

---

# 70. Calculation questions

### Question 1

A processor operates at:

```text
2 GHz
```

What is its clock period?

### Answer

```text
T = 1 / f

T = 1 / 2×10⁹
  = 0.5 ns
```

---

### Question 2

A program executes:

```text
1,000,000 instructions
```

with an average CPI of:

```text
2
```

on a:

```text
1 GHz
```

processor.

Calculate CPU time.

### Answer

```text
CPU time
=
Instruction count × CPI / frequency

= 1,000,000 × 2 / 1,000,000,000

= 0.002 seconds

= 2 ms
```

---

### Question 3

A processor executes:

```text
500 million instructions
```

with CPI:

```text
1.5
```

at:

```text
2.5 GHz
```

Calculate approximate CPU execution time.

### Answer

```text
CPU time
=
500,000,000 × 1.5
------------------
2,500,000,000

= 0.3 seconds
```

---

# 71. Practical mental model

When you see a processor instruction, ask these questions:

```text
1. Where does the instruction come from?
        ↓
     Memory

2. How does CPU understand it?
        ↓
     Decoder

3. Where are operands?
        ↓
     Registers / memory / immediate

4. What operation is needed?
        ↓
     ALU / other execution unit

5. Where does result go?
        ↓
     Register / memory

6. What instruction executes next?
        ↓
     Program Counter
```

If you can answer those six questions, you understand the basic processor execution model.

---

# 72. Final summary

A processor can be understood as a combination of:

```text
+----------------------------------+
|           PROCESSOR              |
|                                  |
|  +------------+                  |
|  | Registers  |                  |
|  +-----+------+                  |
|        |                         |
|        v                         |
|  +-----------+                   |
|  |    ALU    |                   |
|  +-----+-----+                   |
|        |                         |
|        v                         |
|  +-----------+    +-----------+  |
|  | Datapath  |<-->| Control   |  |
|  +-----------+    | Unit      |  |
|                   +-----------+  |
+----------------------------------+
          |
          v
     Memory / I/O
```

The most important concepts are:

```text
Instruction
    ↓
Fetch
    ↓
Decode
    ↓
Read operands
    ↓
Execute
    ↓
Write result
    ↓
Update PC
    ↓
Repeat
```

The processor is fundamentally a **synchronous digital system that combines combinational logic, sequential state, storage elements, control logic, and interfaces to memory and I/O**.

---

# 73. Study checklist

Before considering this topic complete, make sure you can explain:

- [ ] What a processor does
- [ ] CPU vs memory
- [ ] ISA vs microarchitecture
- [ ] Machine instructions
- [ ] Opcodes
- [ ] Registers
- [ ] Program Counter
- [ ] Instruction Register
- [ ] Stack Pointer
- [ ] Status/flag registers
- [ ] ALU
- [ ] Control Unit
- [ ] Datapath
- [ ] Multiplexers
- [ ] Processor buses
- [ ] Fetch-decode-execute
- [ ] LOAD and STORE
- [ ] Arithmetic instructions
- [ ] Branch instructions
- [ ] Function calls
- [ ] Clock cycles
- [ ] Clock frequency
- [ ] CPI and IPC
- [ ] Processor performance
- [ ] RISC vs CISC
- [ ] Load/store architecture
- [ ] Addressing modes
- [ ] Memory-mapped I/O
- [ ] Interrupts
- [ ] Pipelining
- [ ] Pipeline hazards
- [ ] Superscalar execution
- [ ] Multiple CPU cores
- [ ] Cache hierarchy
- [ ] Branch prediction
- [ ] Out-of-order execution
- [ ] Von Neumann architecture
- [ ] Harvard architecture
- [ ] Von Neumann bottleneck
- [ ] Endianness
- [ ] Processor word size
- [ ] Boot process

---

# 74. Recommended learning order

For this course, a good progression is:

```text
Number Systems
      ↓
Data Storage
      ↓
Truth Tables
      ↓
Boolean Algebra
      ↓
Logic Gates
      ↓
Combinational Networks
      ↓
Sequential Networks
      ↓
Registers & Memory
      ↓
ALU
      ↓
Control Unit
      ↓
Datapath
      ↓
Processor
      ↓
Memory & I/O
```

The key idea is that a processor is not a completely separate subject from digital logic.

It is the **large-scale application of the same digital concepts** you have already studied:

```text
Bits
 ↓
Logic
 ↓
Circuits
 ↓
State
 ↓
Registers
 ↓
Datapath + Control
 ↓
Processor
 ↓
Computer
```