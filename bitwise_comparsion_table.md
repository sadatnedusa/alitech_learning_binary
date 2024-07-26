### Bitwise Comparison Table

#### Input Combinations
```
A    B
0    0
0    1
1    0
1    1
```

#### AND (`&`)
- The result bit is 1 if both corresponding bits are 1, otherwise the result bit is 0.
```
A    B    AND
0    0    0
0    1    0
1    0    0
1    1    1
```

#### OR (`|`)
- The result bit is 1 if at least one of the corresponding bits is 1, otherwise the result bit is 0.
```
A    B    OR
0    0    0
0    1    1
1    0    1
1    1    1
```

#### XOR (`^`)
- The result bit is 1 if the corresponding bits are different, otherwise the result bit is 0.
```
A    B    XOR
0    0    0
0    1    1
1    0    1
1    1    0
```

#### NOT (`~`)
- The NOT operator inverts each bit of a single number. Here we apply it to each single input separately.

**Applying NOT to A**
```
A    NOT A
0    1
1    0
```

**Applying NOT to B**
```
B    NOT B
0    1
1    0
```

### Summary

This table provides a detailed comparison of the bitwise operations AND, OR, XOR, and NOT for the provided bit combinations:

| A    | B    | AND  | OR   | XOR  | NOT A | NOT B |
|------|------|------|------|------|-------|-------|
| 0    | 0    | 0    | 0    | 0    | 1     | 1     |
| 0    | 1    | 0    | 1    | 1    | 1     | 0     |
| 1    | 0    | 0    | 1    | 1    | 0     | 1     |
| 1    | 1    | 1    | 1    | 0    | 0     | 0     |

---



# Given the bit sequences:

```
0 0 0 0
0 0 0 1
0 0 1 0
0 0 1 1
0 1 0 0
0 1 0 1
0 1 1 0
0 1 1 1
1 0 0 0
```

#### Bitwise AND Results

| A         | B         | A AND B   |
|-----------|-----------|-----------|
| 0 0 0 0   | 0 0 0 0   | 0 0 0 0   |
| 0 0 0 0   | 0 0 0 1   | 0 0 0 0   |
| 0 0 1 0   | 0 0 0 0   | 0 0 0 0   |
| 0 0 1 1   | 0 0 0 0   | 0 0 0 0   |
| 0 1 0 0   | 0 0 0 0   | 0 0 0 0   |
| 0 1 0 1   | 0 0 0 0   | 0 0 0 0   |
| 0 1 1 0   | 0 0 0 0   | 0 0 0 0   |
| 0 1 1 1   | 0 0 0 0   | 0 0 0 0   |
| 1 0 0 0   | 0 0 0 0   | 0 0 0 0   |

#### Bitwise OR Results

| A         | B         | A OR B    |
|-----------|-----------|-----------|
| 0 0 0 0   | 0 0 0 0   | 0 0 0 0   |
| 0 0 0 0   | 0 0 0 1   | 0 0 0 1   |
| 0 0 1 0   | 0 0 0 0   | 0 0 1 0   |
| 0 0 1 1   | 0 0 0 0   | 0 0 1 1   |
| 0 1 0 0   | 0 0 0 0   | 0 1 0 0   |
| 0 1 0 1   | 0 0 0 0   | 0 1 0 1   |
| 0 1 1 0   | 0 0 0 0   | 0 1 1 0   |
| 0 1 1 1   | 0 0 0 0   | 0 1 1 1   |
| 1 0 0 0   | 0 0 0 0   | 1 0 0 0   |

#### Bitwise XOR Results

| A         | B         | A XOR B   |
|-----------|-----------|-----------|
| 0 0 0 0   | 0 0 0 0   | 0 0 0 0   |
| 0 0 0 0   | 0 0 0 1   | 0 0 0 1   |
| 0 0 1 0   | 0 0 0 0   | 0 0 1 0   |
| 0 0 1 1   | 0 0 0 0   | 0 0 1 1   |
| 0 1 0 0   | 0 0 0 0   | 0 1 0 0   |
| 0 1 0 1   | 0 0 0 0   | 0 1 0 1   |
| 0 1 1 0   | 0 0 0 0   | 0 1 1 0   |
| 0 1 1 1   | 0 0 0 0   | 0 1 1 1   |
| 1 0 0 0   | 0 0 0 0   | 1 0 0 0   |

#### Bitwise NOT Results

Applying NOT to each bit individually for A:

| A        | NOT A       |
|----------|-------------|
| 0 0 0 0  | 1 1 1 1     |
| 0 0 0 1  | 1 1 1 0     |
| 0 0 1 0  | 1 1 0 1     |
| 0 0 1 1  | 1 1 0 0     |
| 0 1 0 0  | 1 0 1 1     |
| 0 1 0 1  | 1 0 1 0     |
| 0 1 1 0  | 1 0 0 1     |
| 0 1 1 1  | 1 0 0 0     |
| 1 0 0 0  | 0 1 1 1     |

This gives you a detailed comparison table for AND, OR, XOR, and NOT operations on the provided bit pairs.
