# How Different Data Types Are Stored

## 1. How computers store data

Computers ultimately store information using **binary**.

Binary uses only two values:

- **0**
- **1**

A single binary digit is called a **bit**.

Eight bits make one **byte**.

**1 byte = 8 bits**

Larger amounts of storage are measured using units such as kilobytes, megabytes, gigabytes, and terabytes.

---

## 2. Integers

An **integer** is a whole number, such as:

- 5
- 100
- -20

Positive integers can be represented using binary.

For example:

**5 in decimal = 101 in binary**

Computers use specific binary representations to store both positive and negative integers.

---

## 3. Real numbers

Numbers containing fractions or decimals, such as:

- 3.14
- 0.5
- -12.75

are commonly stored using **floating-point representation**.

Floating-point storage allows computers to represent a wide range of values, although some decimal values cannot be represented exactly.

---

## 4. Characters and text

Letters, numbers, and symbols are stored as numerical codes.

Common character encoding systems include:

- **ASCII**
- **Unicode**

For example, a computer does not store the letter "A" as the shape of the letter. It stores a numerical code representing that character.

**Unicode** supports a very large range of characters and languages.

---

## 5. Boolean values

A **Boolean** value has only two possible states:

- True
- False

These can be represented using:

- True = 1
- False = 0

Boolean values are widely used in logic, conditions, and programming.

---

## 6. Images

Digital images are made from many small points called **pixels**.

Each pixel contains numerical information describing its colour.

For example, an RGB image can store values for:

- Red
- Green
- Blue

The combination of these values determines the colour of each pixel.

The more pixels an image has, the more information is required to store it.

---

## 7. Audio

Computers store digital audio as numerical samples.

When sound is recorded:

1. A microphone detects sound waves.
2. The sound is converted into electrical information.
3. The computer samples the signal at regular intervals.
4. The samples are stored as numbers.

Two important concepts are **sample rate** and **bit depth**.

---

## 8. Video

Digital video is usually stored as a sequence of individual images called **frames**.

Video can also contain audio.

A video therefore requires storage for:

- Image frames
- Audio
- Additional information such as timing

Compression is often used to reduce the amount of storage required.

---

## 9. Why data types matter

Different types of information require different representations.

| Data type | Typical representation |
|---|---|
| Integer | Binary integer |
| Decimal/real number | Floating-point |
| Character/text | ASCII or Unicode |
| Boolean | 0 or 1 |
| Image | Pixels and colour values |
| Audio | Numerical samples |
| Video | Frames and audio |

## 10. Key idea

**Everything stored by a computer is ultimately represented as binary data, but different data types use different methods to represent that binary information.**
