# State Machines and Flip-Flops

## 1. What is a flip-flop?

A **flip-flop** is a small digital circuit that can store **one bit** of information.

A bit can have two values:

- **0** = OFF / False
- **1** = ON / True

Unlike a simple logic gate, a flip-flop can **remember** its previous value. This makes flip-flops important for storing information in digital systems.

## 2. Why are flip-flops useful?

Computers need to store information while they are working. Flip-flops can be combined to create larger storage units such as:

- Registers
- Counters
- Memory circuits
- Digital clocks

Most flip-flops are controlled by a **clock signal**. The clock provides regular timing signals that help digital circuits change state in an organized way.

## 3. Common types of flip-flops

### D flip-flop

A **D (Data) flip-flop** stores the value present at its input when it receives a clock signal.

**Application:** D flip-flops are commonly used in registers and data storage.

### JK flip-flop

A **JK flip-flop** is a flexible type of flip-flop that can store, set, reset, or toggle its value.

**Application:** JK flip-flops can be used in counters and control circuits.

### T flip-flop

A **T (Toggle) flip-flop** changes its output when triggered.

**Application:** T flip-flops are useful for counters and frequency division.

### SR flip-flop

An **SR (Set-Reset) flip-flop** has inputs used to set the output to 1 or reset it to 0.

**Application:** SR flip-flops can be used in simple memory and control circuits.

---

## 4. What is a state?

A **state** describes the current condition of a digital system.

For example, a traffic light can have states such as:

1. Red
2. Green
3. Yellow

The system changes from one state to another according to rules.

---

## 5. What is a state machine?

A **state machine** is a digital system that moves between different states based on its current state and inputs.

A simple example is a traffic-light controller:

**Red → Green → Yellow → Red**

The state machine decides which state should come next.

## 6. Types of state machines

### Finite State Machine (FSM)

A **finite state machine** has a limited number of possible states.

There are two common types:

- **Moore machine:** Output mainly depends on the current state.
- **Mealy machine:** Output depends on the current state and inputs.

## 7. Applications

State machines are used in:

- Traffic-light controllers
- Vending machines
- Washing machines
- Elevators
- Digital communication systems
- Processor control units
- Game controllers

## 8. Key idea

**Flip-flops store bits, while state machines use stored information to control how a digital system behaves over time.**
