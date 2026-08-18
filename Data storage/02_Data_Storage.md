# DT102A: Computer Science Principles & Digital Logic
## Module 02: Data Storage (Detailed Study & Reference Guide)

---

## 1. Introduction to Data Representation

At the lowest physical layer, computer storage devices store binary digits (bits). However, software requires higher-level abstractions to represent text, integers, floating-point real numbers, images, and audio. This guide covers how primitive and structured data types are encoded into physical bit patterns.

---

## 2. Text & Character Encoding Formats

### 2.1 ASCII (American Standard Code for Information Interchange)
* **Bit Width:** 7-bit standard code ($128$ characters: $0 \dots 127$).
* **Structure:**
  * `0`–`31` & `127`: Control characters (e.g., `0x0A` LF, `0x0D` CR, `0x09` TAB).
  * `32`: Space character.
  * `48`–`57`: Digits `'0'` to `'9'` (`0x30` to `0x39`).
  * `65`–`90`: Uppercase letters `'A'` to `'Z'` (`0x41` to `0x5A`).
  * `97`–`122`: Lowercase letters `'a'` to `'z'` (`0x61` to `0x7A`).
* **Key Feature:** Case toggling is achieved by flipping bit 5 (`'A'` $01000001_2 \leftrightarrow$ `'a'` $01100001_2$).

### 2.2 Extended ASCII
* **Bit Width:** 8-bit ($256$ characters).
* Uses values $128 \dots 255$ for regional symbols (e.g., ISO-8859-1 for Western European accents like `Å, Ä, Ö`).

### 2.3 Unicode Standard
Designed to unify characters from all human languages into a single universal character set.
* **Code Points:** Denoted as `U+XXXX` (e.g., `U+0041` = 'A', `U+1F600` = 😀).
* **Encoding Schemes:**
  1. **UTF-8 (Variable-Length):**
     * Uses $1$ to $4$ bytes per code point.
     * Fully backward-compatible with 7-bit ASCII (ASCII chars take 1 byte).
     * Dominant web and Linux standard.
     * **Encoding Table:**
       * `U+0000` to `U+007F`: `0xxxxxxx`
       * `U+0080` to `U+07FF`: `110xxxxx 10xxxxxx`
       * `U+0800` to `U+FFFF`: `1110xxxx 10xxxxxx 10xxxxxx`
       * `U+10000` to `U+10FFFF`: `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx`
  2. **UTF-16:** Uses $16$-bit code units (1 or 2 pairs / surrogate pairs).
  3. **UTF-32:** Fixed 4 bytes per code point. Simple indexing but memory inefficient.

---

## 3. Real Numbers & IEEE 754 Floating-Point Standard

To represent real numbers with arbitrary fractional components and large dynamic ranges, computers use floating-point arithmetic based on scientific notation:

$$V = (-1)^S \times M \times 2^E$$

### 3.1 IEEE 754 Single-Precision (32-bit) Standard

#### Bit Allocation Layout:
| Field | Bit Positions | Width | Description |
| :--- | :---: | :---: | :--- |
| **Sign ($S$)** | Bit 31 | 1 bit | $0 =$ Positive, $1 =$ Negative |
| **Biased Exponent ($E$)** | Bits 30–23 | 8 bits | Stored with bias $127$ ($E = e + 127$) |
| **Mantissa/Fraction ($F$)** | Bits 22–0 | 23 bits | Fractional part of normalized mantissa $1.F$ |

```text
 31 30        23 22                               0
+--+------------+----------------------------------+
|S | Exponent E |           Fraction F             |
+--+------------+----------------------------------+
 1b    8 bits                23 bits
```

### 3.2 Normalized Numbers Formula
For $0 < E < 255$:
$$\text{Value} = (-1)^S \times (1 + F) \times 2^{E - 127}$$
* **Implicit Leading One:** The integer $1$ before the decimal point ($1.F$) is implied and not stored in memory, giving 24 bits of precision from 23 stored bits.

### 3.3 Step-by-Step Example: Encoding $-6.625_{10}$ to IEEE 754 32-bit Hex

1. **Sign bit $S$:** Number is negative $\implies S = 1$.
2. **Convert absolute value to binary:**
   * $6_{10} = 110_2$
   * $0.625_{10} = 0.101_2$
   * Combined: $110.101_2$
3. **Normalize binary representation:**
   * $110.101_2 = 1.10101_2 \times 2^2$
   * Significant fraction $F = 10101000000000000000000_2$ (padded to 23 bits).
   * Unbiased exponent $e = 2$.
4. **Calculate Biased Exponent $E$:**
   * $E = e + \text{Bias} = 2 + 127 = 129_{10}$
   * $129_{10} = 1000\,0001_2$
5. **Assemble 32-bit Pattern:**
   * $S = 1$
   * $E = 1000\,0001$
   * $F = 1010\,1000\,0000\,0000\,0000\,000$
   * Binary string: `1100 0000 1101 0100 0000 0000 0000 0000`
   * **Hexadecimal:** `0xC0D40000`

### 3.4 Special IEEE 754 Cases

| Exponent ($E$) | Fraction ($F$) | Represented Value / Meaning |
| :---: | :---: | :--- |
| `0000 0000` | $0$ | Zero ($+0$ or $-0$ depending on $S$) |
| `0000 0000` | Non-zero | Denormalized / Subnormal numbers ($0.F \times 2^{-126}$) |
| `1111 1111` | $0$ | Infinity ($+\infty$ or $-\infty$) |
| `1111 1111` | Non-zero | Not-a-Number (NaN) — e.g., $\sqrt{-1}, 0/0$ |

---

## 4. Error Detection & Correction Codes

Data stored on physical media or transmitted across buses can experience bit flips due to noise, cosmic radiation, or wear.

### 4.1 Parity Bits
* **Odd/Even Parity:** Append a single bit to ensure total count of 1-bits is even or odd.
* **Limitation:** Can detect single bit errors, but cannot pinpoint error location or detect even numbers of bit errors.

### 4.2 Checksums & Cyclic Redundancy Checks (CRC)
* Used for block data integrity (e.g., storage disk sectors, network frames). Polynomial division produces a fixed-size tag.

### 4.3 Hamming Distance & Hamming Code (SEC-DED)
* **Hamming Distance:** Minimum number of single-bit flips required to change one valid codeword into another.
* **Hamming (7, 4) Code:** Encodes 4 data bits into 7 total bits by adding 3 parity bits at positions $1, 2, 4$ ($2^k$).
* Capable of **Single-Error Correction, Double-Error Detection (SEC-DED)**.

---

## 5. Byte Ordering: Endianness

When multi-byte primitives (e.g., 32-bit `int` `0x12345678`) are stored in byte-addressable memory, the order of bytes matters.

### 5.1 Big-Endian
* The **Most Significant Byte (MSB)** is stored at the lowest memory address.
* Used in network protocols (IP header standard) and legacy RISC architectures.

### 5.2 Little-Endian
* The **Least Significant Byte (LSB)** is stored at the lowest memory address.
* Used by standard x86, x86-64, and modern ARM processors.

#### Memory Layout Example for `0x12345678` at base address `0x1000`:

| Memory Address | `0x1000` | `0x1001` | `0x1002` | `0x1003` |
| :--- | :---: | :---: | :---: | :---: |
| **Big-Endian** | `0x12` | `0x34` | `0x56` | `0x78` |
| **Little-Endian** | `0x78` | `0x56` | `0x34` | `0x12` |

---

## 6. Real-World Applications & Exam Practice Questions

### Practice Question 1
Decode the 32-bit IEEE 754 floating-point number represented in hexadecimal as `0x40C00000` into its decimal equivalent.

<details>
<summary><b>Click to View Solution</b></summary>

1. **Convert Hex to Binary:**
   `0x40C00000` = `0100 0000 1100 0000 0000 0000 0000 0000`
2. **Parse Fields:**
   * $S = 0$ (Positive)
   * $E = 1000\,0001_2 = 129_{10}$
   * $F = 100\,0000\,0000\,0000\,0000\,0000_2 = 0.5_{10}$
3. **Calculate Value:**
   * Unbiased exponent $e = 129 - 127 = 2$
   * Mantissa $= 1 + F = 1.5$
   * Value $= (-1)^0 \times 1.5 \times 2^2 = 1.5 \times 4 = \mathbf{6.0}$
</details>

### Practice Question 2
Encode the ASCII string `"DT102A"` into Hexadecimal bytes.

<details>
<summary><b>Click to View Solution</b></summary>

* `'D'` $\rightarrow 68_{10} = \text{0x44}$
* `'T'` $\rightarrow 84_{10} = \text{0x54}$
* `'1'` $\rightarrow 49_{10} = \text{0x31}$
* `'0'` $\rightarrow 48_{10} = \text{0x30}$
* `'2'` $\rightarrow 50_{10} = \text{0x32}$
* `'A'` $\rightarrow 65_{10} = \text{0x41}$

**Hex sequence:** `0x44 0x54 0x31 0x30 0x32 0x41`
</details>
