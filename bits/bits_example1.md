# examples for each bitwise operator:

---

### Understanding Bitwise Operators: AND, OR, XOR, and NOT

Bitwise operators are a fundamental part of computer science and programming. They operate at the binary level and can perform operations quickly and efficiently. In this article, we will explore the four main bitwise operators: AND, OR, XOR, and NOT.

#### What are Bitwise Operators?

Bitwise operators work directly with the binary representations of numbers. Instead of dealing with decimal or hexadecimal values, these operators manipulate bits—the smallest unit of data in computing.

#### Bitwise AND (`&`)

The bitwise AND operator compares each bit of two numbers. If both bits are 1, the resulting bit is 1. Otherwise, the resulting bit is 0.

**Example 1:**
```
21 (in binary: 10101)
18 (in binary: 10010)
--------------------
AND            10000 (in decimal: 16)
```

**Example 2:**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
AND            10000 (in decimal: 16)
```

In these examples, only the bits where both numbers have a 1 remain set in the result.

#### Bitwise OR (`|`)

The bitwise OR operator compares each bit of two numbers. If at least one of the bits is 1, the resulting bit is 1. If both bits are 0, the resulting bit is 0.

**Example 1:**
```
21 (in binary: 10101)
18 (in binary: 10010)
--------------------
OR             10111 (in decimal: 23)
```

**Example 2:**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
OR             11001 (in decimal: 25)
```

Here, the result includes all bits that are set in either number.

#### Bitwise XOR (`^`)

The bitwise XOR operator compares each bit of two numbers. If the bits are different, the resulting bit is 1. If the bits are the same, the resulting bit is 0.

**Example 1:**
```
21 (in binary: 10101)
18 (in binary: 10010)
--------------------
XOR            00111 (in decimal: 7)
```

**Example 2:**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
XOR            01001 (in decimal: 9)
```

In these examples, the result includes bits that differ between the two numbers.

#### Bitwise NOT (`~`)

The bitwise NOT operator inverts each bit of a number. If the bit is 1, it becomes 0, and if the bit is 0, it becomes 1. This operation is also known as bitwise complement.

**Example 1:**
```
21 (in binary: 10101)
--------------------
NOT           01010 (in decimal: -22 in 2's complement form for 32-bit integers)
```

**Example 2:**
```
18 (in binary: 10010)
--------------------
NOT           01101 (in decimal: -19 in 2's complement form for 32-bit integers)
```

The result is the inverted bits of the given numbers (assuming a 32-bit signed integer representation).

#### Practical Applications

1. **Masking**: Bitwise AND is often used for masking bits to isolate specific bits in a number.
   - Example: `number & 0xF` will mask all but the last four bits.
2. **Setting Bits**: Bitwise OR can set specific bits.
   - Example: `number | 0x1` will set the least significant bit.
3. **Toggling Bits**: Bitwise XOR can toggle specific bits.
   - Example: `number ^ 0xF` will toggle the last four bits.
4. **Inversion**: Bitwise NOT can be used to invert all bits in a number.
   - Example: `~number` will flip all bits in the number.

#### Conclusion

Bitwise operators are powerful tools that allow for efficient manipulation of binary data. Understanding these operators can greatly enhance your ability to work with low-level data and optimize your code. Whether you're working on embedded systems, encryption algorithms, or data compression, mastering bitwise operations is a valuable skill for any programmer.
