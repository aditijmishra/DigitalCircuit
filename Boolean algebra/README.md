# Boolean algebra — Exam study guide

Comprehensive checklist and study plan for Boolean algebra and logic-simplification topics frequently examined in digital-circuits courses.

## Core concepts (must-know)
- Boolean variables, functions, and truth tables
- Basic operators: NOT (¬), AND (·), OR (+), XOR, NAND, NOR
- Constants: 0 and 1; duality principle
- Algebraic laws: identity, null, idempotent, complement, commutative, associative, distributive
- De Morgan's laws and application
- Absorption, consensus (redundancy), involution, complementation

## Canonical forms & representations
- Minterms (sum-of-products, SOP) and maxterms (product-of-sums, POS)
- Canonical SOP/POS and converting between forms
- Algebraic factorization and multi-level expressions
- Boolean function as truth table → expression → gate network

## Simplification techniques
- Algebraic manipulation using identities and theorems
- Karnaugh maps (K-maps): grouping rules, powers-of-two groups, handling don't-care conditions
- Quine–McCluskey (tabulation) method — prime implicants and essential implicants (for systematic minimization)
- Espresso heuristic minimizer (conceptual awareness)
- XOR/XNOR simplifications and parity functions

## Implementation & practical topics
- Implementing functions with NAND-only or NOR-only gates (functional completeness)
- Multi-level network vs two-level implementation trade-offs
- Factorization to reduce gate inputs and levels
- Fan-in, fan-out, and practical gate limitations

## Hazards, timing & physical concerns
- Static-1, static-0, and dynamic hazards: causes and detection via K-maps or race analysis
- How hazards are eliminated (redundant terms, design techniques)
- Propagation delay basics, contamination delay, and impact on combinational correctness

## Proofs & reasoning skills (exam style)
- Prove equivalence of two Boolean expressions algebraically and by truth table
- Demonstrate step-by-step simplification with justifications (cite identity used)
- Find minimal SOP/POS and show why alternate answers are non-minimal
- Show derivation of canonical form from truth table

## Common example circuits to master
- Logic gates truth tables and symbol recognition
- 1-bit half adder and full adder (derive sum and carry expressions)
- Multiplexer (2:1, 4:1) as function implementer and its boolean expression
- Decoder (n-to-2^n), encoder, and priority encoder logic
- Comparator circuits and parity generator/checker

## Worked problem types to practice
- Convert between truth table, Boolean expression, K-map grouping, and minimized circuit
- Minimize functions with don't-care entries and explain group choices
- Transform expression to NAND-only/NOR-only implementation
- Detect and remove hazards in a given circuit
- Use algebraic identities to simplify multi-level expressions

## Practice exercises (progression)
1. List and apply the basic identities on small expressions (10 problems)
2. Generate truth tables for 3–5 variable functions and derive canonical SOP/POS
3. K-map minimization: 3-, 4-, and 5-variable maps with and without don't-cares (15 problems)
4. Quine–McCluskey on a 5–6 variable example (2 problems)
5. Implement half/full adder and 4-bit ripple adder expressions; analyze carry propagation
6. Given a circuit, identify hazards; propose fixes and justify
7. Convert expressions to NAND-only and NOR-only gate networks (10 problems)

## Exam tips
- Always show steps: truth table or K-map grouping + reason for each simplification
- For minimization, label groups clearly and verify final expression with a truth table for correctness
- Practice timed problems: K-map simplification under 5–8 minutes for typical 4-variable tasks
- Memorize key identities and De Morgan forms for speed

## Additional resources
- Textbooks: "Digital Design" (M. Morris Mano), "Fundamentals of Digital Logic with Verilog Design" (Brown & Vranesic)
- Online: Karnaugh map tutorials, Boolean algebra cheat-sheets, logic simulators (Logisim/electronic workbench)
- Tools: logic minimizers, truth-table generators, Verilog/VHDL simulators for validating expressions

## Suggested file-based exercises in this repo
- examples/boolean-exercises.md — collection of graded problems
- solutions/ — verified solutions and step-by-step reductions
- verilog/ or vhdl/ — implement small circuits and run testbenches

---
Study systematically: start with identities and truth tables, progress to K-maps and algebraic minimization, then practice applied circuit design and hazard/timing analysis. Good luck on the exam!

