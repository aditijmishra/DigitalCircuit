# Number Systems — Digital Circuits & Computer Engineering

## Course context

This study note covers **Number Systems**, the first topic in the Digital Circuits & Computer Engineering course at Kristianstad University (HKR). HKR's course page is the official course-plan source. The course plan page identifies the course as **Digital- och datorteknik** and provides sections for course content and learning outcomes. 

---

# 1. What is a number system?

A **number system** is a method of representing numbers using a set of symbols and rules.

In everyday life we normally use the **decimal system**, which has 10 symbols:

```text
0 1 2 3 4 5 6 7 8 9
```

Computers and digital circuits mainly use the **binary system**, which has only two symbols:

```text
0 1
```

Other important systems are:

| Number system | Base (radix) | Digits used | Common use |
|---|---:|---|---|
| Decimal | 10 | 0–9 | Everyday mathematics |
| Binary | 2 | 0–1 | Digital circuits and computers |
| Octal | 8 | 0–7 | Compact representation of binary |
| Hexadecimal | 16 | 0–9, A–F | Memory addresses, machine code, debugging |

The **base** tells us how many different digits are available.

---

# 2. Positional number systems

Most number systems used in computing are **positional**.

This means that the value of a digit depends on:

1. The digit itself
2. Its position
3. The base

For example:

```text
572
```

in decimal means:

```text
5 × 10² + 7 × 10¹ + 2 × 10⁰
```

So:

```text
= 5 × 100 + 7 × 10 + 2 × 1
= 500 + 70 + 2
= 572
```

The powers of the base increase as we move left.

---

# 3. Decimal number system

The decimal system has base **10**.

The place values are:

```text
10³   10²   10¹   10⁰
1000  100   10    1
```

Example:

```text
3486
```

means:

```text
3 × 10³
+ 4 × 10²
+ 8 × 10¹
+ 6 × 10⁰
```

Therefore:

```text
3000 + 400 + 80 + 6 = 3486
```

## Important idea

The rightmost digit has position 0.

```text
3   4   8   6
↑   ↑   ↑   ↑
3   2   1   0   ← position
```

---

# 4. Binary number system

Binary is the most important number system for digital electronics.

It has base **2** and only two digits:

```text
0 and 1
```

Each binary digit is called a **bit**.

## Binary place values

Starting from the right:

```text
2⁰  2¹  2²  2³  2⁴  2⁵  2⁶  2⁷
1   2   4   8   16  32  64  128
```

So:

```text
1101₂
```

means:

```text
1 × 2³
+ 1 × 2²
+ 0 × 2¹
+ 1 × 2⁰
```

Calculate:

```text
= 1 × 8
+ 1 × 4
+ 0 × 2
+ 1 × 1

= 8 + 4 + 0 + 1

= 13
```

Therefore:

```text
1101₂ = 13₁₀
```

The subscript tells us the base.

---

# 5. Binary terminology

## Bit

A **bit** is one binary digit.

It can contain:

```text
0 or 1
```

## Nibble

A **nibble** is 4 bits.

Example:

```text
1011
```

## Byte

A **byte** is 8 bits.

Example:

```text
10110101
```

Therefore:

```text
1 byte = 8 bits
1 nibble = 4 bits
```

---

# 6. Converting binary to decimal

This is one of the most important exam skills.

## Method

1. Write the powers of 2.
2. Multiply each bit by its place value.
3. Add the results.

Example:

```text
101101₂
```

Write the place values:

```text
Binary:       1  0  1  1  0  1
Power:        5  4  3  2  1  0
Value:       32 16  8  4  2  1
```

Now calculate:

```text
1×32 + 0×16 + 1×8 + 1×4 + 0×2 + 1×1
```

```text
= 32 + 8 + 4 + 1
= 45
```

Therefore:

```text
101101₂ = 45₁₀
```

---

# 7. Converting decimal integer to binary

There are two useful methods.

## Method 1 — Repeated division by 2

To convert:

```text
25₁₀ → ?₂
```

Divide repeatedly by 2 and record the remainders.

```text
25 ÷ 2 = 12 remainder 1
12 ÷ 2 = 6  remainder 0
6  ÷ 2 = 3  remainder 0
3  ÷ 2 = 1  remainder 1
1  ÷ 2 = 0  remainder 1
```

Read the remainders **from bottom to top**:

```text
11001
```

Therefore:

```text
25₁₀ = 11001₂
```

### Exam rule

When using repeated division:

> **Divide by 2 → keep the remainder → read remainders upward.**

---

# 8. Decimal to binary using powers of 2

This method is often faster.

Convert:

```text
45₁₀
```

Find powers of 2 that add up to 45:

```text
32 + 8 + 4 + 1 = 45
```

Place 1 under the powers used and 0 under the powers not used.

```text
32  16  8  4  2  1
 1   0   1  1  0  1
```

Therefore:

```text
45₁₀ = 101101₂
```

---

# 9. Binary counting

Binary counting works like decimal counting, but there are only two digits.

Decimal:

```text
0
1
2
3
4
5
...
```

Binary:

```text
0
1
10
11
100
101
110
111
1000
1001
1010
1011
1100
...
```

The first few values are:

| Decimal | Binary |
|---:|---:|
| 0 | 0000 |
| 1 | 0001 |
| 2 | 0010 |
| 3 | 0011 |
| 4 | 0100 |
| 5 | 0101 |
| 6 | 0110 |
| 7 | 0111 |
| 8 | 1000 |
| 9 | 1001 |
| 10 | 1010 |
| 11 | 1011 |
| 12 | 1100 |
| 13 | 1101 |
| 14 | 1110 |
| 15 | 1111 |

Notice:

```text
1111₂ = 15₁₀
```

---

# 10. Maximum value with n bits

For an **unsigned** binary number with `n` bits:

```text
Maximum value = 2ⁿ - 1
```

Examples:

### 1 bit

```text
2¹ - 1 = 1
```

Possible values:

```text
0, 1
```

### 4 bits

```text
2⁴ - 1 = 15
```

Possible values:

```text
0–15
```

### 8 bits

```text
2⁸ - 1 = 255
```

Possible values:

```text
0–255
```

### 16 bits

```text
2¹⁶ - 1 = 65,535
```

---

# 11. Number of values represented by n bits

With `n` bits, the total number of different combinations is:

```text
2ⁿ
```

Examples:

```text
1 bit  → 2 values
2 bits → 4 values
3 bits → 8 values
4 bits → 16 values
8 bits → 256 values
```

For unsigned numbers, those values are normally:

```text
0 to 2ⁿ - 1
```

---

# 12. Leading zeros

Leading zeros do not change the value.

For example:

```text
101₂
```

and

```text
00000101₂
```

represent the same unsigned value:

```text
5₁₀
```

However, fixed-width binary is very important in computers.

For example, an 8-bit representation of 5 is:

```text
00000101
```

---

# 13. Octal number system

Octal has base **8**.

Its digits are:

```text
0 1 2 3 4 5 6 7
```

There is no digit 8 or 9 in octal.

Place values are:

```text
8⁰ = 1
8¹ = 8
8² = 64
8³ = 512
```

Example:

```text
347₈
```

means:

```text
3×8² + 4×8¹ + 7×8⁰
```

```text
= 3×64 + 4×8 + 7×1
= 192 + 32 + 7
= 231
```

Therefore:

```text
347₈ = 231₁₀
```

---

# 14. Binary to octal

This conversion is especially easy because:

```text
8 = 2³
```

Therefore, **3 binary bits correspond to 1 octal digit**.

Example:

```text
101110₂
```

Group from the right into groups of 3:

```text
101 110
```

Convert each group:

```text
101₂ = 5₈
110₂ = 6₈
```

Therefore:

```text
101110₂ = 56₈
```

If necessary, add zeros on the left:

```text
10₂
```

becomes:

```text
010₂
```

so:

```text
010₂ = 2₈
```

---

# 15. Octal to binary

Reverse the same process.

Every octal digit becomes exactly 3 binary bits.

Conversion table:

| Octal | Binary |
|---:|---:|
| 0 | 000 |
| 1 | 001 |
| 2 | 010 |
| 3 | 011 |
| 4 | 100 |
| 5 | 101 |
| 6 | 110 |
| 7 | 111 |

Example:

```text
57₈
```

Convert:

```text
5 → 101
7 → 111
```

Therefore:

```text
57₈ = 101111₂
```

---

# 16. Hexadecimal number system

Hexadecimal has base **16**.

It uses:

```text
0–9
A–F
```

The values are:

| Hex | Decimal |
|---|---:|
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| 5 | 5 |
| 6 | 6 |
| 7 | 7 |
| 8 | 8 |
| 9 | 9 |
| A | 10 |
| B | 11 |
| C | 12 |
| D | 13 |
| E | 14 |
| F | 15 |

The letters are not separate values; they represent decimal values 10–15.

---

# 17. Hexadecimal place values

Because hexadecimal is base 16:

```text
16⁰ = 1
16¹ = 16
16² = 256
16³ = 4096
```

Example:

```text
2A₁₆
```

means:

```text
2×16¹ + A×16⁰
```

Since:

```text
A = 10
```

we get:

```text
2×16 + 10×1
= 32 + 10
= 42
```

Therefore:

```text
2A₁₆ = 42₁₀
```

---

# 18. Binary to hexadecimal

This is extremely important in computer engineering.

Because:

```text
16 = 2⁴
```

**4 binary bits correspond to 1 hexadecimal digit.**

Example:

```text
10101111₂
```

Group into 4 bits:

```text
1010 1111
```

Convert:

```text
1010₂ = A₁₆
1111₂ = F₁₆
```

Therefore:

```text
10101111₂ = AF₁₆
```

---

# 19. Hexadecimal to binary

Every hexadecimal digit becomes exactly 4 bits.

Important conversion table:

| Hex | Binary |
|---|---|
| 0 | 0000 |
| 1 | 0001 |
| 2 | 0010 |
| 3 | 0011 |
| 4 | 0100 |
| 5 | 0101 |
| 6 | 0110 |
| 7 | 0111 |
| 8 | 1000 |
| 9 | 1001 |
| A | 1010 |
| B | 1011 |
| C | 1100 |
| D | 1101 |
| E | 1110 |
| F | 1111 |

Example:

```text
3C₁₆
```

Convert each digit:

```text
3 → 0011
C → 1100
```

Therefore:

```text
3C₁₆ = 00111100₂
```

Leading zeros can be removed if the number is not required to have a fixed width:

```text
111100₂
```

---

# 20. Decimal to hexadecimal

There are two common approaches.

## Method 1 — Repeated division by 16

Convert:

```text
254₁₀
```

Divide by 16:

```text
254 ÷ 16 = 15 remainder 14
15 ÷ 16  = 0  remainder 15
```

Decimal 15 is `F`.

Decimal 14 is `E`.

Read from bottom to top:

```text
FE₁₆
```

Therefore:

```text
254₁₀ = FE₁₆
```

## Method 2 — Use powers of 16

```text
16¹ = 16
16⁰ = 1
```

For 254:

```text
254 = 15×16 + 14
```

Therefore:

```text
254₁₀ = FE₁₆
```

---

# 21. Hexadecimal to decimal

Example:

```text
3F₁₆
```

Calculate:

```text
3×16¹ + F×16⁰
```

Since:

```text
F = 15
```

we get:

```text
3×16 + 15×1
= 48 + 15
= 63
```

Therefore:

```text
3F₁₆ = 63₁₀
```

---

# 22. Fast conversion relationships

Memorize these:

```text
1 octal digit = 3 binary bits

1 hexadecimal digit = 4 binary bits

1 byte = 8 bits

1 byte = 2 hexadecimal digits

1 nibble = 4 bits = 1 hexadecimal digit
```

Example:

```text
1111 1010
```

can be written as:

```text
FA₁₆
```

because:

```text
1111 → F
1010 → A
```

---

# 23. Binary fractions

Binary can also represent fractional numbers.

The positions to the right of the binary point use negative powers of 2:

```text
2⁻¹ = 1/2
2⁻² = 1/4
2⁻³ = 1/8
2⁻⁴ = 1/16
```

Example:

```text
0.101₂
```

means:

```text
1×2⁻¹ + 0×2⁻² + 1×2⁻³
```

```text
= 1/2 + 0 + 1/8
= 0.5 + 0.125
= 0.625
```

Therefore:

```text
0.101₂ = 0.625₁₀
```

---

# 24. Decimal fraction to binary

To convert a decimal fraction to binary, repeatedly multiply the fractional part by 2.

Example:

```text
0.625₁₀
```

Multiply:

```text
0.625 × 2 = 1.25
```

Record the integer part:

```text
1
```

Continue with the fractional part:

```text
0.25 × 2 = 0.5
```

Record:

```text
0
```

Continue:

```text
0.5 × 2 = 1.0
```

Record:

```text
1
```

The bits are:

```text
101
```

Therefore:

```text
0.625₁₀ = 0.101₂
```

---

# 25. Signed and unsigned numbers

A binary pattern can represent different things depending on the representation scheme.

## Unsigned

All bits represent the magnitude.

For 8 bits:

```text
00000000 = 0
11111111 = 255
```

Range:

```text
0 to 255
```

Formula:

```text
0 to 2⁸ - 1
```

## Signed

A signed representation must also represent negative values.

A very common representation is **two's complement**.

For an 8-bit signed two's-complement number:

```text
Range = -128 to +127
```

This is important when studying processor arithmetic.

---

# 26. Two's complement — basic idea

Two's complement is a standard way of representing signed integers in binary.

To find the negative of a positive binary number:

1. Write the positive number in fixed-width binary.
2. Invert every bit.
3. Add 1.

Example using 8 bits:

```text
+5 = 00000101
```

Invert:

```text
11111010
```

Add 1:

```text
11111011
```

So:

```text
11111011₂ = -5
```

in 8-bit two's complement.

### Important

Do not use this method without considering the fixed number of bits.

For example, 8-bit and 16-bit two's-complement representations have different bit patterns.

---

# 27. Binary addition

Binary addition follows four basic rules:

```text
0 + 0 = 0
0 + 1 = 1
1 + 0 = 1
1 + 1 = 10
```

The last rule means:

```text
1 + 1 = 0 with carry 1
```

Example:

```text
   1011
 + 0110
 -------
  10001
```

Check in decimal:

```text
1011₂ = 11
0110₂ = 6

11 + 6 = 17

10001₂ = 17
```

---

# 28. Binary subtraction

Basic rules:

```text
0 - 0 = 0
1 - 0 = 1
1 - 1 = 0
10 - 1 = 1
```

The last rule occurs when borrowing.

Example:

```text
  1010
- 0011
------
  0111
```

Check:

```text
1010₂ = 10
0011₂ = 3

10 - 3 = 7

0111₂ = 7
```

---

# 29. Why hexadecimal is used in computing

Long binary values are difficult for humans to read.

Compare:

```text
Binary:
1101011010111110

Hexadecimal:
D6BE
```

Both represent the same bit pattern.

Hexadecimal is therefore a convenient shorthand for binary.

It is commonly encountered when working with:

- Memory addresses
- Machine-level data
- Debugging
- Bit patterns
- Registers
- Embedded systems
- Digital electronics

---

# 30. Common exam conversions

You should be comfortable with:

```text
Binary → Decimal
Decimal → Binary

Binary → Octal
Octal → Binary

Binary → Hexadecimal
Hexadecimal → Binary

Decimal → Hexadecimal
Hexadecimal → Decimal

Decimal → Octal
Octal → Decimal
```

You should also understand:

```text
Unsigned numbers
Signed numbers
Two's complement
Binary addition
Binary subtraction
```

---

# 31. A useful conversion strategy

When converting between two non-decimal systems, binary can often be used as an intermediate.

For example:

```text
Hex → Binary → Decimal
```

or:

```text
Octal → Binary → Hex
```

Example:

```text
57₈ → ?₁₆
```

First convert octal to binary:

```text
5 → 101
7 → 111

57₈ = 101111₂
```

Add leading zeros so that the number can be grouped into 4:

```text
0010 1111
```

Convert:

```text
0010 → 2
1111 → F
```

Therefore:

```text
57₈ = 2F₁₆
```

---

# 32. Common mistakes to avoid

## Mistake 1 — Reading binary remainders in the wrong direction

For repeated division:

```text
Read remainders from bottom to top.
```

## Mistake 2 — Using 8 or 9 in octal

Invalid:

```text
89₈
```

Octal only uses:

```text
0–7
```

## Mistake 3 — Forgetting that A–F have values

```text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

## Mistake 4 — Grouping binary incorrectly

For octal:

```text
groups of 3
```

For hexadecimal:

```text
groups of 4
```

## Mistake 5 — Forgetting the base

These are different:

```text
101₂
101₁₀
101₁₆
```

Always check the base.

---

# 33. Quick reference tables

## Powers of 2

| Power | Value |
|---:|---:|
| 2⁰ | 1 |
| 2¹ | 2 |
| 2² | 4 |
| 2³ | 8 |
| 2⁴ | 16 |
| 2⁵ | 32 |
| 2⁶ | 64 |
| 2⁷ | 128 |
| 2⁸ | 256 |
| 2⁹ | 512 |
| 2¹⁰ | 1024 |
| 2¹¹ | 2048 |
| 2¹² | 4096 |
| 2¹⁶ | 65536 |

## Binary ↔ Hex

| Binary | Hex |
|---|---|
| 0000 | 0 |
| 0001 | 1 |
| 0010 | 2 |
| 0011 | 3 |
| 0100 | 4 |
| 0101 | 5 |
| 0110 | 6 |
| 0111 | 7 |
| 1000 | 8 |
| 1001 | 9 |
| 1010 | A |
| 1011 | B |
| 1100 | C |
| 1101 | D |
| 1110 | E |
| 1111 | F |

---

# 34. Exam checklist

Before moving to the next topic, make sure you can:

- [ ] Define a number system.
- [ ] Explain what a base/radix is.
- [ ] Explain positional notation.
- [ ] Convert binary to decimal.
- [ ] Convert decimal to binary.
- [ ] Convert binary to octal.
- [ ] Convert octal to binary.
- [ ] Convert binary to hexadecimal.
- [ ] Convert hexadecimal to binary.
- [ ] Convert decimal to hexadecimal.
- [ ] Convert hexadecimal to decimal.
- [ ] Explain bit, nibble and byte.
- [ ] Calculate the number of values represented by `n` bits.
- [ ] Calculate the maximum unsigned value of `n` bits.
- [ ] Explain binary fractions.
- [ ] Perform binary addition.
- [ ] Perform binary subtraction.
- [ ] Explain unsigned representation.
- [ ] Explain the basic idea of signed two's-complement representation.

---

# 35. Practice questions

## Level 1 — Basic

1. What is a number system?
2. What does the base of a number system mean?
3. What is the base of binary?
4. What digits are used in binary?
5. What is a bit?
6. How many bits are in a byte?
7. How many bits are in a nibble?
8. What is the hexadecimal value of decimal 15?
9. What is the binary representation of decimal 10?
10. What is the decimal value of `1010₂`?

## Level 2 — Conversions

11. Convert `110101₂` to decimal.
12. Convert `11110000₂` to decimal.
13. Convert `37₁₀` to binary.
14. Convert `100101₂` to octal.
15. Convert `725₈` to binary.
16. Convert `11011110₂` to hexadecimal.
17. Convert `A7₁₆` to binary.
18. Convert `3B₁₆` to decimal.
19. Convert `255₁₀` to hexadecimal.
20. Convert `73₈` to decimal.

## Level 3 — University-style practice

21. How many different values can be represented using 6 bits?
22. What is the largest unsigned value that can be represented with 10 bits?
23. Represent decimal 45 using 8 bits.
24. Convert `101101.101₂` to decimal.
25. Convert `0.625₁₀` to binary.
26. Add `101101₂ + 11011₂`.
27. Subtract `11010₂ - 1011₂`.
28. Represent `-18` using 8-bit two's complement.
29. Convert `3A7₁₆` to binary.
30. Convert `110101101₂` to hexadecimal.

---

# 36. Answers to selected practice questions

### 10.

```text
1010₂
= 8 + 2
= 10₁₀
```

### 11.

```text
110101₂
= 32 + 16 + 4 + 1
= 53₁₀
```

### 12.

```text
11110000₂
= 128 + 64 + 32 + 16
= 240₁₀
```

### 13.

```text
37₁₀ = 100101₂
```

### 16.

```text
11011110₂
= 1101 1110
= D E
= DE₁₆
```

### 21.

```text
2⁶ = 64
```

So 6 bits represent **64 different bit patterns**.

### 22.

```text
2¹⁰ - 1
= 1024 - 1
= 1023
```

### 24.

```text
101101.101₂

= 32 + 8 + 4 + 1
  + 1/2 + 1/8

= 45.625₁₀
```

### 25.

```text
0.625₁₀ = 0.101₂
```

### 30.

Group from the right:

```text
110101101
→ 0001 1010 1101
→ 1 A D
```

Therefore:

```text
110101101₂ = 1AD₁₆
```

---

# 37. What to learn next

Number systems provide the foundation for the rest of digital circuits.

A useful learning sequence is:

```text
Number Systems
      ↓
Data Storage
      ↓
Truth Tables
      ↓
Boolean Algebra
      ↓
Combinational Networks
      ↓
Sequential Networks
      ↓
Processor Principles
      ↓
Memory and I/O
```

The most important immediate goals are:

```text
1. Binary arithmetic
2. Binary ↔ decimal conversion
3. Binary ↔ hexadecimal conversion
4. Binary ↔ octal conversion
5. Bits, bytes and ranges
6. Signed vs unsigned numbers
7. Two's complement
```

Once these are comfortable, move to **Data Storage** and then **Truth Tables + Boolean Algebra**.
