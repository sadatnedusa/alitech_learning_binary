# cheat sheet for the bitwise operators AND, OR, XOR, and NOT:
## This cheat sheet provides a quick reference to understand and use bitwise operators effectively.

---

## Bitwise Operators Cheat Sheet

### Bitwise AND (`&`)
- **Description**: Compares each bit of two numbers. The resulting bit is 1 if both bits are 1; otherwise, the resulting bit is 0.
- **Example**:
  ```
  21 (in binary: 10101)
  18 (in binary: 10010)
  --------------------
  AND            10000 (in decimal: 16)
  ```

### Bitwise OR (`|`)
- **Description**: Compares each bit of two numbers. The resulting bit is 1 if at least one of the bits is 1; otherwise, the resulting bit is 0.
- **Example**:
  ```
  21 (in binary: 10101)
  18 (in binary: 10010)
  --------------------
  OR             10111 (in decimal: 23)
  ```

### Bitwise XOR (`^`)
- **Description**: Compares each bit of two numbers. The resulting bit is 1 if the bits are different; otherwise, the resulting bit is 0.
- **Example**:
  ```
  21 (in binary: 10101)
  18 (in binary: 10010)
  --------------------
  XOR            00111 (in decimal: 7)
  ```

### Bitwise NOT (`~`)
- **Description**: Inverts each bit of the number. If the bit is 1, it becomes 0; if the bit is 0, it becomes 1.
- **Example**:
  ```
  21 (in binary: 10101)
  --------------------
  NOT           01010 (in decimal: -22 in 2's complement form for 32-bit integers)
  ```

### Additional Examples

**Bitwise AND (`&`)**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
AND            10000 (in decimal: 16)
```

**Bitwise OR (`|`)**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
OR             11001 (in decimal: 25)
```

**Bitwise XOR (`^`)**
```
24 (in binary: 11000)
17 (in binary: 10001)
--------------------
XOR            01001 (in decimal: 9)
```

**Bitwise NOT (`~`)**
```
18 (in binary: 10010)
--------------------
NOT           01101 (in decimal: -19 in 2's complement form for 32-bit integers)
```

### Practical Applications

1. **Masking Bits**: 
   - Example: `number & 0xF` isolates the last four bits.
   ```
   29 (in binary: 11101)
   0xF (in binary: 01111)
   --------------------
   AND            01101 (in decimal: 13)
   ```

2. **Setting Bits**: 
   - Example: `number | 0x1` sets the least significant bit.
   ```
   22 (in binary: 10110)
   0x1 (in binary: 00001)
   --------------------
   OR             10111 (in decimal: 23)
   ```

3. **Toggling Bits**: 
   - Example: `number ^ 0xF` toggles the last four bits.
   ```
   29 (in binary: 11101)
   0xF (in binary: 01111)
   --------------------
   XOR            10010 (in decimal: 18)
   ```

4. **Inversion**: 
   - Example: `~number` inverts all bits.
   ```
   45 (in binary: 101101)
   --------------------
   NOT          010010 (in decimal: -46 in 2's complement form for 32-bit integers)
   ```

---

