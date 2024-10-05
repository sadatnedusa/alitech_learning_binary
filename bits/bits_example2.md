# Let's break down bitwise operators in a way that's easy to understand, along with examples and pseudocode for each operator.

### Understanding Bitwise Operators: AND, OR, XOR, and NOT

Bitwise operators are used to perform bit-level operations on binary numbers. These operators are essential in low-level programming and are widely used in fields like computer graphics, cryptography, and networking. Here are the four primary bitwise operators:

#### 1. Bitwise AND (`&`)

**Operation**: The bitwise AND operator compares each bit of two numbers. If both bits are 1, the resulting bit is set to 1. Otherwise, it is set to 0.

**Example**:
```
  5  ->  0101
  3  ->  0011
  -----------
AND   ->  0001 (1 in decimal)
```

**Pseudocode**:
```pseudo
function bitwiseAND(a, b):
    result = 0
    position = 1
    while a > 0 or b > 0:
        if (a & 1) == 1 and (b & 1) == 1:
            result += position
        a = a >> 1
        b = b >> 1
        position = position << 1
    return result
```

#### 2. Bitwise OR (`|`)

**Operation**: The bitwise OR operator compares each bit of two numbers. If at least one of the bits is 1, the resulting bit is set to 1. Otherwise, it is set to 0.

**Example**:
```
  5  ->  0101
  3  ->  0011
  -----------
OR    ->  0111 (7 in decimal)
```

**Pseudocode**:
```pseudo
function bitwiseOR(a, b):
    result = 0
    position = 1
    while a > 0 or b > 0:
        if (a & 1) == 1 or (b & 1) == 1:
            result += position
        a = a >> 1
        b = b >> 1
        position = position << 1
    return result
```

#### 3. Bitwise XOR (`^`)

**Operation**: The bitwise XOR operator compares each bit of two numbers. If the bits are different, the resulting bit is set to 1. If they are the same, the resulting bit is set to 0.

**Example**:
```
  5  ->  0101
  3  ->  0011
  -----------
XOR   ->  0110 (6 in decimal)
```

**Pseudocode**:
```pseudo
function bitwiseXOR(a, b):
    result = 0
    position = 1
    while a > 0 or b > 0:
        if (a & 1) != (b & 1):
            result += position
        a = a >> 1
        b = b >> 1
        position = position << 1
    return result
```

#### 4. Bitwise NOT (`~`)

**Operation**: The bitwise NOT operator inverts all the bits of a number. In most systems, this operation also changes the sign of the number due to the way negative numbers are represented in binary (using two's complement).

**Example**:
```
  5  ->  0101
  -----------
NOT   ->  1010 (-6 in decimal, due to two's complement representation)
```

**Pseudocode**:
```pseudo
function bitwiseNOT(a):
    result = 0
    position = 1
    while a != 0:
        if (a & 1) == 0:
            result += position
        a = a >> 1
        position = position << 1
    result = -result - 1  // Adjust for two's complement representation
    return result
```

### Conclusion

Bitwise operators are powerful tools in programming that allow you to manipulate data at the bit level. Understanding how these operators work can help you write more efficient and optimized code for tasks that involve low-level data manipulation.
