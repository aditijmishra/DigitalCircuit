# Memories and I/O

## Digital & Computer Technology — Study Notes

> **Purpose:** Detailed study notes for understanding computer memory systems and Input/Output (I/O), including memory organization, addressing, buses, memory technologies, I/O devices, interfaces, interrupts, DMA, and practical processor–memory–I/O communication.
>
> **Prerequisites:** Number systems, data storage, Boolean algebra, combinational networks, sequential networks, and principles of processors.

---

# 1. What are Memory and I/O?

A computer needs two fundamental things besides processing:

1. **Memory** — to store instructions and data.
2. **I/O (Input/Output)** — to communicate with the outside world.

A simplified computer system is:

```text
                  +----------------+
                  |      CPU       |
                  |                |
                  | ALU + Control  |
                  | + Registers    |
                  +-------+--------+
                          |
                System interconnect
                  /       |       \
                 /        |        \
                v         v         v
             Memory      Input    Output
                         Devices   Devices
```

The CPU performs computation, memory stores information, and I/O allows the computer to interact with users, sensors, networks, disks, displays, and other hardware.

---

# 2. The Three Major Parts

A simplified computer can be divided into:

```text
+----------------------------------+
|          Computer System         |
|                                  |
|   +------+   +--------+          |
|   | CPU  |   | Memory |          |
|   +------+   +--------+          |
|       \          /               |
|        \        /                |
|         +------+                 |
|         |  I/O |                 |
|         +------+                 |
+----------------------------------+
```

## CPU

Responsible for:

- executing instructions
- arithmetic
- logical operations
- control
- communication with memory and I/O

## Memory

Stores:

- instructions
- program data
- temporary values
- operating-system data

## I/O

Allows communication with:

- keyboard
- mouse
- display
- storage devices
- network interfaces
- sensors
- printers
- other computers
- embedded devices

---

# 3. Memory Hierarchy

Computer systems use several levels of memory.

A simplified hierarchy is:

```text
                 Faster
                   ↑
             +-----------+
             | Registers |
             +-----------+
                   |
             +-----------+
             | L1 Cache  |
             +-----------+
                   |
             +-----------+
             | L2 Cache  |
             +-----------+
                   |
             +-----------+
             | L3 Cache  |
             +-----------+
                   |
             +-----------+
             |    RAM    |
             +-----------+
                   |
             +-----------+
             | SSD / HDD |
             +-----------+
                   |
                 Slower
```

Generally:

```text
Moving downward:

Capacity       increases
Cost/bit       decreases
Latency        increases
Speed          decreases
```

There are exceptions and architectural differences, but this is the fundamental idea.

---

# 4. Why Do We Need a Memory Hierarchy?

Fast memory is expensive and physically limited.

Large memory is usually cheaper per bit but slower.

Therefore, computer systems combine multiple technologies.

The goal is to create the illusion of:

```text
large + inexpensive + fast memory
```

using:

```text
small + very fast memory
+
larger + slower memory
```

This works because programs often demonstrate **locality**.

---

# 5. Locality

Two important forms of locality are:

## Temporal locality

If a program accesses something recently, it may access it again soon.

Example:

```text
for (i = 0; i < 1000; i++)
```

The loop variable is repeatedly accessed.

## Spatial locality

If a program accesses one memory location, it may soon access nearby locations.

Example:

```text
array[0]
array[1]
array[2]
array[3]
```

Caches exploit both types of locality.

---

# 6. Registers

Registers are storage elements inside the processor.

They are extremely fast but limited in number.

Examples:

```text
R0
R1
R2
R3
...
```

Special registers may include:

```text
PC  → Program Counter
SP  → Stack Pointer
IR  → Instruction Register
FLAGS → Status information
```

Conceptually:

```text
CPU
 |
 +--- Registers
 |
 +--- ALU
 |
 +--- Control Unit
```

---

# 7. Cache Memory

Cache memory is fast memory located close to the CPU.

A typical hierarchy is:

```text
CPU
 |
L1
 |
L2
 |
L3
 |
RAM
```

Cache stores copies of data and instructions that are likely to be used again.

---

# 8. Cache Hit

A **cache hit** occurs when requested data is already in the cache.

```text
CPU
 |
 v
Cache
 |
 +--> Data found
```

This is fast.

---

# 9. Cache Miss

A **cache miss** occurs when requested data is not in the cache.

```text
CPU
 |
 v
Cache
 |
 +--> MISS
       |
       v
      RAM
```

The required data must be retrieved from a lower level of the memory hierarchy.

This takes longer.

---

# 10. Hit Rate

The cache hit rate is:

```text
Hit rate =
number of cache hits
--------------------
total memory accesses
```

For example:

```text
900 hits
100 misses

total = 1000
```

Then:

```text
Hit rate = 900 / 1000
         = 90%
```

The miss rate is:

```text
Miss rate = 1 - Hit rate
```

Therefore:

```text
Miss rate = 10%
```

---

# 11. SRAM

**SRAM** means:

> Static Random-Access Memory

SRAM is commonly used for cache.

Advantages:

- very fast
- does not require periodic refresh like DRAM
- good for high-speed cache

Disadvantages:

- larger physical area per bit
- more expensive
- lower density

Conceptually:

```text
CPU
 ↓
SRAM Cache
 ↓
DRAM
```

---

# 12. DRAM

**DRAM** means:

> Dynamic Random-Access Memory

DRAM is commonly used as main memory.

A simplified DRAM cell uses:

```text
transistor + capacitor
```

The capacitor stores charge representing information.

Because the stored charge changes over time, DRAM requires refresh operations.

Advantages:

- high density
- lower cost per bit than SRAM
- suitable for large main memory

Disadvantages:

- slower than SRAM
- requires refresh
- more complicated timing

---

# 13. SRAM vs DRAM

| Property | SRAM | DRAM |
|---|---|---|
| Typical use | Cache | Main memory |
| Refresh | Not periodically required | Required |
| Speed | Very high | High |
| Density | Lower | Higher |
| Cost/bit | Higher | Lower |
| Typical capacity | Smaller | Larger |

Remember:

```text
SRAM → fast, expensive, small
DRAM → slower, cheaper, large
```

---

# 14. ROM

ROM means:

> Read-Only Memory

Historically, ROM referred to memory whose contents were fixed or difficult to change.

ROM and related non-volatile technologies can be used for:

- firmware
- boot code
- embedded systems
- configuration data

The important characteristic is:

```text
Power OFF
     ↓
Data remains
```

---

# 15. PROM

PROM means:

> Programmable Read-Only Memory

A PROM can be programmed after manufacturing.

Typically:

```text
Manufacture
     ↓
Program
     ↓
Permanent contents
```

Traditional PROM is generally programmed once.

---

# 16. EPROM

EPROM means:

> Erasable Programmable Read-Only Memory

EPROM can be erased and programmed again.

Historically, UV light was used to erase many EPROM devices.

The general idea is:

```text
Program
   ↓
Use
   ↓
Erase
   ↓
Program again
```

---

# 17. EEPROM

EEPROM means:

> Electrically Erasable Programmable Read-Only Memory

EEPROM can be erased electrically.

This is more convenient than physically removing a chip and using ultraviolet light.

Flash memory is closely related to electrically erasable non-volatile semiconductor memory.

---

# 18. Flash Memory

Flash is non-volatile semiconductor memory.

It is widely used in:

- SSDs
- USB drives
- memory cards
- smartphones
- embedded systems
- firmware storage

Flash stores information using specialized semiconductor cells.

Advantages:

- non-volatile
- no mechanical movement
- relatively fast
- low power
- compact

---

# 19. Flash Memory Organization

Flash storage is not simply a giant array where every byte can be independently overwritten.

It is organized into structures such as:

```text
Cells
  ↓
Pages
  ↓
Erase blocks
```

Reads and writes occur according to the characteristics of the flash technology.

An SSD controller manages these details.

---

# 20. SSD Controller

An SSD contains a controller between the computer and flash memory.

Simplified:

```text
CPU
 |
I/O interface
 |
SSD Controller
 |
+--------------------+
| Flash | Flash      |
| Flash | Flash      |
+--------------------+
```

The controller performs functions such as:

- logical-to-physical address translation
- error correction
- wear leveling
- garbage collection
- bad-block management
- caching
- command processing

---

# 21. HDD

A Hard Disk Drive stores data magnetically.

Main components include:

- platters
- spindle
- read/write heads
- actuator
- controller

Simplified:

```text
          Head
           ↓
      +---------+
     /           \
    |  Platter    |
     \           /
      +---------+
          |
       Spindle
```

The platters rotate while the read/write heads access magnetic regions.

---

# 22. SSD vs HDD

| Feature | SSD | HDD |
|---|---|---|
| Technology | Flash | Magnetic |
| Moving parts | No | Yes |
| Random access | Generally fast | Slower |
| Noise | No mechanical noise | Mechanical noise |
| Shock resistance | Generally better | Generally lower |
| Cost/GB | Often higher | Often lower |
| Large capacity | Available | Widely available |

---

# 23. Memory Addressing

Memory is organized into addressable locations.

Example:

```text
Address     Data
0000        10101100
0001        01011001
0010        11110000
0011        00010101
```

The address identifies the location.

The data is the stored value.

---

# 24. Address Bus

The **address bus** carries the address of the location the CPU wants to access.

```text
CPU
 |
 | Address
 v
Memory
```

If a processor has `n` address lines:

```text
Number of possible addresses = 2ⁿ
```

---

# 25. Example: Address Bus

Suppose:

```text
Address bus = 8 bits
```

Then:

```text
2⁸ = 256
```

possible addresses exist.

If each address stores one byte:

```text
256 × 1 byte
= 256 bytes
```

---

# 26. Data Bus

The data bus carries the actual data being transferred.

For example:

```text
CPU
 |
 | Data = 10101100
 v
Memory
```

For a read:

```text
Memory → CPU
```

For a write:

```text
CPU → Memory
```

---

# 27. Control Signals

The system also needs control information.

Examples include:

```text
READ
WRITE
ENABLE
CLOCK
INTERRUPT
RESET
```

Conceptually:

```text
             CPU
              |
       +------+------+
       |      |      |
    Address  Data  Control
       |      |      |
       +------+------+
              |
           Memory
```

---

# 28. Three-Bus Model

A simplified traditional system can be represented as:

```text
              +-------+
              |  CPU  |
              +---+---+
                  |
       +----------+----------+
       |          |          |
       v          v          v
 Address Bus   Data Bus   Control Bus
       |          |          |
       +----------+----------+
                  |
             +----+----+
             | Memory  |
             +---------+
```

Modern systems may use more sophisticated interconnects rather than a simple shared bus.

---

# 29. Memory Read Operation

Suppose the CPU wants to read address `1000`.

A simplified sequence:

```text
1. CPU places 1000 on address bus.
2. CPU activates READ.
3. Memory decodes address 1000.
4. Memory retrieves data.
5. Memory places data on data bus.
6. CPU receives the data.
```

Diagram:

```text
CPU
 |
 | Address = 1000
 | READ
 v
Memory
 |
 | Data
 v
CPU
```

---

# 30. Memory Write Operation

Suppose the CPU wants to write:

```text
10101010
```

to address:

```text
1000
```

Sequence:

```text
1. CPU places 1000 on address bus.
2. CPU places 10101010 on data bus.
3. CPU activates WRITE.
4. Memory stores the data.
```

Diagram:

```text
CPU
 |
 | Address
 | Data
 | WRITE
 v
Memory
```

---

# 31. Address Decoding

A memory system needs to determine which device or memory region corresponds to a given address.

This is the job of **address decoding**.

Example:

```text
Address
  |
  v
+---------+
| Decoder |
+---------+
 |   |   |
 v   v   v
RAM I/O ROM
```

For example:

```text
0000–7FFF → RAM
8000–8FFF → I/O
9000–FFFF → ROM
```

These ranges are examples only.

---

# 32. Memory Map

A **memory map** describes which address ranges correspond to which resources.

Example:

```text
+-------------------+ FFFF
|       ROM         |
+-------------------+ C000
|       I/O         |
+-------------------+ B000
|       RAM         |
+-------------------+ 0000
```

The CPU uses addresses to access these regions.

This is particularly important in memory-mapped I/O.

---

# 33. Memory-Mapped I/O

In **memory-mapped I/O**, device registers are assigned addresses within the processor's address space.

For example:

```text
0x0000 – 0x7FFF → RAM
0x8000 – 0x80FF → Device A
0x8100 – 0x81FF → Device B
0x9000 – 0xFFFF → ROM
```

The CPU can communicate with a device using normal load/store operations.

Conceptually:

```text
CPU
 |
 | WRITE 0x8000
 | DATA = 0x01
 v
Device register
```

The device interprets the write as a command or configuration change.

---

# 34. I/O

I/O means:

> Input / Output

Input transfers information **into** the computer.

Output transfers information **out of** the computer.

Examples:

### Input

- keyboard
- mouse
- microphone
- camera
- temperature sensor
- network interface

### Output

- display
- speaker
- printer
- motor controller
- network interface

Some devices perform both input and output.

---

# 35. I/O Device

An I/O device typically contains hardware that converts between:

```text
Physical / external world
          ↕
     Device electronics
          ↕
      Digital data
          ↕
      Computer bus
```

For example, a keyboard:

```text
Key press
   ↓
Keyboard electronics
   ↓
Digital code
   ↓
I/O controller
   ↓
CPU
```

---

# 36. I/O Controller

The CPU often does not communicate directly with the physical device.

An **I/O controller/interface** manages the device.

Simplified:

```text
CPU
 |
System interconnect
 |
I/O Controller
 |
Physical Device
```

The controller may contain:

- data registers
- status registers
- control registers
- buffering
- protocol logic
- interrupt logic

---

# 37. Device Registers

An I/O device often exposes registers.

Typical types:

## Data register

Contains data being transferred.

## Status register

Reports device state.

For example:

```text
READY = 1
BUSY  = 0
ERROR = 0
```

## Control register

Allows the CPU to configure or command the device.

Example:

```text
ENABLE = 1
MODE = 2
```

Conceptually:

```text
+----------------+
| Device         |
|                |
| Data Register  |
| Status Register|
| Control Reg.   |
+----------------+
```

---

# 38. Polling

One method of handling I/O is **polling**.

The CPU repeatedly checks the device status.

Example:

```text
while READY == 0:
    check again
```

Conceptually:

```text
CPU
 |
 | Is device ready?
 v
Device
 |
 | NO
 v
CPU
 |
 | Is device ready?
 v
Device
```

This is simple but can waste CPU time.

---

# 39. Interrupt-Driven I/O

Instead of constantly checking the device, the CPU can continue doing other work.

When the device needs attention:

```text
Device
   |
   | Interrupt
   v
 CPU
```

The CPU then executes an interrupt handler.

Sequence:

```text
1. CPU performs normal work.
2. Device becomes ready.
3. Device generates interrupt.
4. CPU recognizes interrupt.
5. CPU saves necessary state.
6. Interrupt handler runs.
7. Device is serviced.
8. CPU resumes previous work.
```

---

# 40. Polling vs Interrupts

| Feature | Polling | Interrupt |
|---|---|---|
| CPU checks device | Repeatedly | Only when notified |
| Simplicity | High | More complex |
| CPU efficiency | Can be poor | Usually better for infrequent events |
| Response | Depends on polling frequency | Event-driven |
| Hardware/software complexity | Lower | Higher |

Neither method is universally better.

The appropriate method depends on the application.

---

# 41. Direct Memory Access

**DMA** means:

> Direct Memory Access

DMA allows certain devices/controllers to transfer data to or from memory without requiring the CPU to handle every individual data transfer.

Without DMA:

```text
Device → CPU → Memory
```

With DMA:

```text
Device ↔ DMA Controller ↔ Memory
```

The CPU mainly configures the transfer and handles completion/errors.

---

# 42. DMA Example

Suppose a network device receives a large block of data.

Without DMA:

```text
Network
   ↓
CPU
   ↓
Memory
```

The CPU may have to participate heavily in each transfer.

With DMA:

```text
Network
   ↓
DMA Controller
   ↓
Memory
```

The CPU can continue other work while the DMA transfer proceeds.

---

# 43. DMA Sequence

A simplified DMA operation:

```text
1. CPU configures DMA.
2. CPU specifies:
   - source
   - destination
   - amount of data
   - direction
3. DMA controller performs transfer.
4. Transfer completes.
5. DMA can generate an interrupt.
6. CPU handles completion.
```

Conceptually:

```text
CPU
 |
 | Configure
 v
DMA
 |
 | transfer
 v
Memory
```

---

# 44. DMA Advantages

DMA is useful because it can:

- reduce CPU overhead
- transfer large blocks efficiently
- improve I/O performance
- allow CPU and I/O activity to overlap

Common applications include:

- disk transfers
- network interfaces
- audio
- video
- high-speed data acquisition

---

# 45. DMA and Cache Coherency

Modern processors often use caches.

If a device writes directly to RAM using DMA, the CPU's cache may contain an older copy of the same data.

Therefore, systems need mechanisms to maintain consistency.

Conceptually:

```text
CPU Cache → old data
RAM       → new DMA data
```

The system must ensure the CPU eventually sees the correct value.

This is part of **cache coherency/consistency management**.

The exact mechanism depends on the architecture.

---

# 46. I/O Addressing

There are two broad approaches to addressing I/O.

## Memory-mapped I/O

I/O registers occupy memory address space.

```text
LOAD/STORE → memory or device
```

## Isolated I/O / port-mapped I/O

Some architectures provide a separate I/O address space and special instructions for I/O.

Conceptually:

```text
Memory address space
        +
I/O address space
```

The exact mechanism depends on the processor architecture.

---

# 47. Memory-Mapped I/O Example

Imagine:

```text
0x8000 → LED control register
```

Writing:

```text
0x01
```

could turn an LED on.

Conceptually:

```text
CPU
 |
 | WRITE 0x8000, 0x01
 v
I/O decoder
 |
 v
LED controller
 |
 v
LED
```

The address is not necessarily RAM.

It identifies a hardware register.

---

# 48. Input Example: Keyboard

A simplified keyboard system:

```text
User presses key
       ↓
Keyboard hardware
       ↓
Keyboard controller
       ↓
Data/status register
       ↓
Interrupt
       ↓
CPU
       ↓
Operating system
       ↓
Application
```

This demonstrates multiple layers between a physical input and application software.

---

# 49. Output Example: Display

A simplified display path:

```text
Application
    ↓
Operating system
    ↓
Graphics subsystem
    ↓
Display controller
    ↓
Display interface
    ↓
Monitor
```

The processor may configure the display hardware, while specialized hardware handles high-volume graphics operations.

---

# 50. Storage I/O

A storage device is also an I/O device.

For example:

```text
Application
     ↓
Operating system
     ↓
File system
     ↓
Storage driver
     ↓
Storage controller
     ↓
SSD
```

When reading a file:

```text
SSD
 ↓
Controller
 ↓
Memory
 ↓
CPU/application
```

DMA is commonly useful for moving large blocks efficiently.

---

# 51. I/O Buffers

A buffer temporarily holds data while two components operate at different speeds.

Example:

```text
Fast producer
     ↓
+----------+
|  Buffer  |
+----------+
     ↓
Slow consumer
```

Buffers are useful because:

```text
CPU speed ≠ device speed
```

For example, a network device can receive data while software processes previously received data.

---

# 52. FIFO

A **FIFO** means:

> First In, First Out

The first item inserted is the first item removed.

```text
Input
 ↓
[A][B][C][D]
 ↑
Output
```

If A entered first:

```text
A comes out first.
```

FIFOs are common in data-transfer systems.

---

# 53. I/O Queues

When multiple operations are waiting:

```text
Request 1
Request 2
Request 3
Request 4
```

the system can maintain a queue.

For example:

```text
Application
    ↓
I/O Queue
    ↓
Storage Controller
    ↓
Device
```

Queues help coordinate asynchronous operations.

---

# 54. Handshaking

Two devices may need to coordinate when transferring data.

A simplified handshake can use signals such as:

```text
READY
VALID
ACKNOWLEDGE
```

Conceptually:

```text
Sender                    Receiver

VALID  -------------------->
       <-------------------- READY
DATA   -------------------->
```

The exact protocol depends on the interface.

The principle is:

> Both sides agree when data is valid and when it has been accepted.

---

# 55. Synchronous vs Asynchronous I/O

## Synchronous

The software waits for an operation to complete.

Conceptually:

```text
Start operation
      ↓
     wait
      ↓
Operation complete
      ↓
Continue
```

## Asynchronous

The software starts the operation and continues doing other work.

Later:

```text
completion event / interrupt
```

notifies the system.

---

# 56. I/O Latency

I/O operations can be much slower than CPU operations.

For example:

```text
CPU operation
     ↓
very short time

Storage operation
     ↓
much longer time
```

This difference is why systems use:

- caches
- buffers
- queues
- DMA
- interrupts
- asynchronous I/O

The objective is to avoid leaving the CPU idle while waiting for slow devices.

---

# 57. Memory latency vs I/O latency

A rough conceptual hierarchy:

```text
CPU register
    ↓
CPU cache
    ↓
RAM
    ↓
SSD
    ↓
Network
    ↓
Remote storage
```

Latency generally increases as we move away from the processor.

This is not a strict universal ordering for every operation, but it is a useful architectural model.

---

# 58. Memory Protection

Modern operating systems need to prevent programs from accessing arbitrary memory.

For example:

```text
Program A
   ↓
Allowed memory

Program B
   ↓
Different memory
```

Hardware mechanisms such as:

- privilege levels
- page tables
- memory-management units
- access permissions

help enforce these boundaries.

---

# 59. Virtual Memory

Virtual memory provides each process with an abstraction of its own address space.

Conceptually:

```text
Program
   |
Virtual addresses
   |
MMU
   |
Physical memory
```

The program may see:

```text
0x00000000
0x00001000
0x00002000
...
```

while the physical RAM locations are different.

---

# 60. Memory Management Unit

The **MMU** means:

> Memory Management Unit

It translates virtual addresses into physical addresses.

Conceptually:

```text
Virtual address
      ↓
     MMU
      ↓
Physical address
      ↓
     RAM
```

The MMU can also enforce access permissions.

---

# 61. Pages

Virtual memory is commonly organized into **pages**.

Physical memory is divided into corresponding **frames**.

Conceptually:

```text
Virtual memory:

Page 0
Page 1
Page 2
Page 3

       ↓ MMU

Physical memory:

Frame 7
Frame 2
Frame 9
Frame 4
```

Pages do not necessarily have to occupy physically adjacent memory.

---

# 62. Page Tables

A page table maps virtual pages to physical frames.

Example:

```text
Virtual Page → Physical Frame

0 → 7
1 → 2
2 → 9
3 → 4
```

The processor's memory-management hardware uses this information during address translation.

---

# 63. TLB

A **Translation Lookaside Buffer (TLB)** is a cache for recent virtual-to-physical address translations.

Without a TLB:

```text
Virtual address
      ↓
Page table lookup
      ↓
Physical address
```

With a TLB:

```text
Virtual address
      ↓
TLB
  ↙       ↘
Hit       Miss
 ↓          ↓
Physical   Page table
address       ↓
          update TLB
```

The TLB improves address-translation performance.

---

# 64. Memory Protection Example

Suppose:

```text
Process A
```

tries to access memory belonging to:

```text
Process B
```

The MMU and operating system can detect that the access is not permitted.

Conceptually:

```text
Process A
   ↓
Virtual address
   ↓
MMU
   ↓
Permission check
   ↓
DENIED
```

This prevents many classes of accidental or malicious memory access.

---

# 65. User Mode and Kernel Mode

Modern processors commonly provide privilege levels.

A simplified model:

```text
User mode
   ↓
Applications

Kernel mode
   ↓
Operating system
   ↓
Hardware access
```

Applications normally cannot perform arbitrary privileged operations.

They request services from the operating system through controlled mechanisms.

---

# 66. System Calls

A **system call** allows an application to request an operating-system service.

For example:

```text
Application
    ↓
system call
    ↓
Operating system
    ↓
device / memory / file system
```

Examples include requests to:

- open files
- read data
- write data
- create processes
- communicate with devices

---

# 67. Complete I/O Example

Consider an application reading a file from an SSD.

A simplified sequence is:

```text
Application
     ↓
System call
     ↓
Operating system
     ↓
File system
     ↓
Storage driver
     ↓
SSD controller
     ↓
Flash memory
```

Then the data returns:

```text
Flash
 ↓
SSD controller
 ↓
DMA
 ↓
RAM
 ↓
Operating system
 ↓
Application
```

An interrupt may notify the CPU that the transfer has completed.

---

# 68. Complete System View

We can combine the concepts:

```text
                    +----------------+
                    |      CPU       |
                    |                |
                    | ALU            |
                    | Registers      |
                    | Control Unit   |
                    +-------+--------+
                            |
                    System Interconnect
                _________/ | \_________
               /           |           \
              v            v            v
           +------+      +------+    +--------+
           | Cache|      | RAM  |    | I/O    |
           +------+      +------+    |Devices |
                                      +---+----+
                                          |
                            +-------------+-------------+
                            |             |             |
                         Keyboard      Network       Storage
                                                        |
                                                       SSD
```

The processor, memory, and I/O form an integrated system.

---

# 69. Important Performance Concepts

## Memory latency

Time required to access memory.

## Memory bandwidth

Amount of data transferred per unit time.

## I/O latency

Time required for an I/O operation to produce a result.

## I/O throughput

Amount of data successfully transferred per unit time.

These are different measurements.

A device can have:

```text
high bandwidth
```

but still have:

```text
high latency
```

for individual operations.

---

# 70. Worked Example: Memory Capacity

Suppose a memory has:

```text
16 address lines
8 data lines
```

Number of addresses:

```text
2¹⁶ = 65,536
```

Each location contains:

```text
8 bits = 1 byte
```

Therefore:

```text
Capacity = 65,536 bytes
         = 64 KiB
```

---

# 71. Worked Example: Wider Memory

Suppose:

```text
20 address lines
16 data lines
```

Number of locations:

```text
2²⁰ = 1,048,576
```

Each location:

```text
16 bits = 2 bytes
```

Capacity:

```text
1,048,576 × 2
= 2,097,152 bytes
= 2 MiB
```

---

# 72. Worked Example: Address Lines

Suppose a memory contains:

```text
64 KiB
```

and is byte-addressable.

Since:

```text
64 KiB = 65,536 bytes
```

and:

```text
65,536 = 2¹⁶
```

the memory needs:

```text
16 address bits
```

---

# 73. Worked Example: Cache Hit Rate

Suppose a CPU performs:

```text
10,000 memory accesses
```

and:

```text
9,500 are cache hits
```

Hit rate:

```text
9,500 / 10,000
= 0.95
= 95%
```

Miss rate:

```text
5%
```

---

# 74. Worked Example: Average Memory Access Time

Suppose:

```text
Cache hit time = 1 ns
Miss penalty = 50 ns
Hit rate = 95%
```

A simplified average access-time calculation is:

```text
AMAT
=
Hit time
+
Miss rate × Miss penalty
```

Therefore:

```text
AMAT
=
1 + 0.05 × 50
=
1 + 2.5
=
3.5 ns
```

The exact definition of miss penalty can vary depending on what timing is included, but this is the standard simplified model.

---

# 75. Common Misconceptions

## Misconception 1

> RAM and storage are the same thing.

Not exactly.

RAM is normally volatile working memory, while SSDs/HDDs provide persistent storage.

---

## Misconception 2

> More RAM automatically makes the CPU faster.

Not necessarily.

More RAM can help if insufficient memory is causing excessive paging or resource pressure, but CPU performance also depends on many other factors.

---

## Misconception 3

> Cache is just another name for RAM.

No.

Cache is a smaller, faster memory layer designed to reduce the effective cost of accessing slower memory.

---

## Misconception 4

> I/O means only keyboard and mouse.

No.

I/O includes communication with many devices:

```text
storage
network
display
audio
sensors
USB devices
controllers
```

---

## Misconception 5

> DMA means the CPU is completely uninvolved.

Not necessarily.

The CPU normally configures the DMA operation and handles completion or errors, while the DMA mechanism performs the actual bulk transfer.

---

# 76. Connection to Processors

Memory and I/O are tightly connected to processor operation.

Recall:

```text
Fetch
 ↓
Decode
 ↓
Execute
```

Fetching requires memory access:

```text
PC
 ↓
Memory
 ↓
Instruction
```

A LOAD instruction may require another memory access:

```text
Register
 ↓
Address
 ↓
Memory
 ↓
Data
```

An I/O operation may involve:

```text
CPU
 ↓
I/O controller
 ↓
Device
```

Therefore:

```text
Processor
    ↕
Memory
    ↕
I/O
```

forms the foundation of a complete computer system.

---

# 77. Connection to Sequential Networks

Memory itself is built from digital storage concepts.

At a conceptual level:

```text
Logic gates
    ↓
Flip-flops / storage cells
    ↓
Registers
    ↓
Memory arrays
    ↓
Cache / RAM
    ↓
Computer memory system
```

This is why sequential logic is an important prerequisite for understanding memory.

---

# 78. Connection to Number Systems

Addresses and data are represented in binary.

For example:

```text
Address:
101101001010₂
```

is simply a binary number identifying a memory location.

Hexadecimal makes addresses easier for humans:

```text
1011 0100 1010
 ↓    ↓    ↓
 B    4    A

= 0xB4A
```

This is why hexadecimal appears frequently in:

- memory addresses
- machine code
- debugging
- registers
- hardware documentation

---

# 79. Connection to Boolean Algebra

Memory and I/O controllers use logic to determine:

```text
Which device?
Which address?
Read or write?
Which register?
Is the device ready?
Should an interrupt be generated?
```

These decisions are implemented using digital logic.

For example:

```text
Address bits
     ↓
Decoder
     ↓
Chip-select signal
```

This is a direct application of Boolean logic and combinational networks.

---

# 80. Connection to Combinational Networks

Examples of combinational circuits used in memory/I/O systems include:

- decoders
- multiplexers
- address logic
- comparators
- bus-selection logic
- control logic

Example:

```text
Address
   ↓
Comparator / Decoder
   ↓
Device select
```

---

# 81. Connection to Sequential Networks

Sequential circuits are used for:

- registers
- counters
- state machines
- buffers
- controllers
- memory elements

An I/O controller can be implemented as a state machine:

```text
IDLE
 ↓
START
 ↓
TRANSFER
 ↓
COMPLETE
 ↓
IDLE
```

This connects I/O directly to sequential-network concepts.

---

# 82. Exam-Style Questions

## Conceptual Questions

1. What is the difference between memory and I/O?
2. Why is a memory hierarchy necessary?
3. Explain temporal locality.
4. Explain spatial locality.
5. What is the difference between SRAM and DRAM?
6. Why is SRAM commonly used for cache?
7. Why is DRAM commonly used as main memory?
8. What is an address bus?
9. What is a data bus?
10. What are control signals?
11. What is address decoding?
12. What is a memory map?
13. Explain memory-mapped I/O.
14. What is an I/O controller?
15. What are data, status, and control registers?
16. What is polling?
17. What is interrupt-driven I/O?
18. What is DMA?
19. Why are buffers useful?
20. What is a FIFO?
21. What is the difference between synchronous and asynchronous I/O?
22. What is virtual memory?
23. What does an MMU do?
24. What is a page table?
25. What is a TLB?
26. Why does cache coherency matter with DMA?

---

# 83. Calculation Questions

### Question 1

A memory has:

```text
12 address lines
8 data lines
```

What is its capacity?

### Question 2

A memory has:

```text
18 address lines
16 bits per location
```

What is its capacity in bytes?

### Question 3

A byte-addressable memory has:

```text
1 MiB
```

How many address bits are required?

### Question 4

A cache performs:

```text
20,000 accesses
19,000 hits
```

What are the hit and miss rates?

### Question 5

A cache has:

```text
Hit time = 2 ns
Hit rate = 98%
Miss penalty = 80 ns
```

Calculate simplified average memory access time.

---

# 84. Answers

## Answer 1

```text
Number of locations = 2¹²
                    = 4096

Each location = 8 bits
              = 1 byte

Capacity = 4096 bytes
         = 4 KiB
```

## Answer 2

```text
Number of locations = 2¹⁸
                    = 262,144

Each location = 16 bits
              = 2 bytes

Capacity = 262,144 × 2
         = 524,288 bytes
         = 512 KiB
```

## Answer 3

```text
1 MiB = 2²⁰ bytes
```

Therefore:

```text
20 address bits
```

are required for byte addressing.

## Answer 4

```text
Hits = 19,000
Total = 20,000

Hit rate = 19,000 / 20,000
         = 95%

Miss rate = 5%
```

## Answer 5

```text
AMAT
=
Hit time + Miss rate × Miss penalty

Miss rate = 1 - 0.98
          = 0.02

AMAT = 2 + 0.02 × 80
     = 2 + 1.6
     = 3.6 ns
```

---

# 85. Practical Mental Model

Whenever you see a memory or I/O problem, ask:

```text
1. Who is requesting the operation?
        ↓
       CPU

2. What address is being accessed?
        ↓
     Address bus

3. What data is involved?
        ↓
      Data bus

4. Is it READ or WRITE?
        ↓
   Control signals

5. Which memory/device responds?
        ↓
   Address decoding

6. Where is the data transferred?
        ↓
   Memory / I/O register

7. How does CPU know it is finished?
        ↓
   Polling / Interrupt / DMA
```

This mental model is extremely useful for exam questions.

---

# 86. Complete Computer Communication Model

A useful overall model is:

```text
                         +-------------+
                         |     CPU     |
                         |             |
                         | ALU         |
                         | Registers   |
                         | Control     |
                         +------+------+
                                |
                         System Interconnect
                                |
            +-------------------+-------------------+
            |                   |                   |
            v                   v                   v
       +---------+         +---------+        +-----------+
       | Cache   |         |   RAM   |        | I/O       |
       +---------+         +---------+        | Controller|
                                              +-----+-----+
                                                    |
                               +--------------------+----------------+
                               |            |           |            |
                               v            v           v            v
                           Keyboard     Display      Network       Storage
```

Data can move through multiple layers:

```text
Application
    ↓
Operating System
    ↓
Drivers
    ↓
I/O Controller
    ↓
Device
```

---

# 87. What You Should Be Able to Explain

After studying this topic, you should be able to explain:

```text
CPU
 ↓
Cache
 ↓
RAM
 ↓
Storage
```

and:

```text
CPU
 ↓
I/O Controller
 ↓
Device
```

You should understand:

- why computers use multiple memory levels
- how addresses select memory locations
- how data moves through buses/interconnects
- how memory read/write operations work
- how I/O devices communicate with processors
- how polling differs from interrupts
- how DMA transfers data
- why buffers are necessary
- how virtual memory works conceptually
- how an MMU translates addresses
- how memory protection works
- how caches improve processor performance

---

# 88. Final Summary

The fundamental relationship is:

```text
                 COMPUTER
                    |
       +------------+------------+
       |            |            |
       v            v            v
      CPU         Memory         I/O
       |            |            |
       |            |            |
       +------------+------------+
                    |
             System Interconnect
```

The CPU executes instructions.

Memory stores instructions and data.

I/O connects the computer to external devices.

The memory system is hierarchical:

```text
Registers
   ↓
Cache
   ↓
RAM
   ↓
SSD / HDD
```

I/O can be handled using:

```text
Polling
Interrupts
DMA
```

And the CPU communicates with memory and devices through concepts such as:

```text
Addresses
Data
Control signals
Memory maps
Device registers
Buses/interconnects
```

The complete picture is:

```text
              +----------------+
              |      CPU       |
              |                |
              | ALU            |
              | Registers      |
              | Control Unit   |
              +-------+--------+
                      |
              System Interconnect
               /       |       \
              /        |        \
             v         v         v
          Cache       RAM        I/O
                                  |
                           +------+------+
                           |             |
                         Devices       Storage
```

The key principle to remember is:

> **A computer is a coordinated system in which the processor executes instructions, memory stores information, and I/O provides communication with the outside world.**
 
---

# 89. Final Study Checklist

## Memory Fundamentals

- [ ] Understand bits, bytes, and words
- [ ] Understand memory addresses
- [ ] Understand addressable locations
- [ ] Calculate memory capacity
- [ ] Understand address buses
- [ ] Understand data buses
- [ ] Understand control signals
- [ ] Understand address decoding
- [ ] Understand memory maps

## Memory Technologies

- [ ] Registers
- [ ] SRAM
- [ ] DRAM
- [ ] ROM
- [ ] PROM
- [ ] EPROM
- [ ] EEPROM
- [ ] Flash
- [ ] SSD
- [ ] HDD

## Cache

- [ ] Cache hierarchy
- [ ] Cache hit
- [ ] Cache miss
- [ ] Hit rate
- [ ] Miss rate
- [ ] Temporal locality
- [ ] Spatial locality
- [ ] Average memory access time

## I/O

- [ ] Understand input
- [ ] Understand output
- [ ] I/O controllers
- [ ] Device registers
- [ ] Data registers
- [ ] Status registers
- [ ] Control registers
- [ ] Memory-mapped I/O
- [ ] Port-mapped I/O

## I/O Techniques

- [ ] Polling
- [ ] Interrupts
- [ ] DMA
- [ ] Buffers
- [ ] FIFO
- [ ] Queues
- [ ] Handshaking
- [ ] Synchronous I/O
- [ ] Asynchronous I/O

## Memory Management

- [ ] Virtual memory
- [ ] MMU
- [ ] Virtual addresses
- [ ] Physical addresses
- [ ] Pages
- [ ] Frames
- [ ] Page tables
- [ ] TLB
- [ ] Memory protection
- [ ] User/kernel modes

## System Understanding

- [ ] CPU ↔ memory communication
- [ ] CPU ↔ I/O communication
- [ ] Storage I/O
- [ ] DMA + cache interaction
- [ ] Interrupt-driven I/O
- [ ] Memory hierarchy
- [ ] Relationship between processor, memory, and I/O

---

# 90. The Big Picture

The topics in your course can now be connected like this:

```text
NUMBER SYSTEMS
      ↓
Binary representation
      ↓
DATA STORAGE
      ↓
Bits / bytes / memory
      ↓
TRUTH TABLES
      ↓
BOOLEAN ALGEBRA
      ↓
COMBINATIONAL NETWORKS
      ↓
Adders / MUX / Decoder / ALU
      ↓
SEQUENTIAL NETWORKS
      ↓
Flip-flops / Registers / Counters
      ↓
PRINCIPLES OF PROCESSORS
      ↓
CPU / ALU / Control / Datapath
      ↓
MEMORIES AND I/O
      ↓
RAM / Cache / Storage / Devices
      ↓
COMPLETE COMPUTER SYSTEM
```

Once you understand this chain, the individual course topics stop looking like separate subjects. They become different layers of the same computer system.