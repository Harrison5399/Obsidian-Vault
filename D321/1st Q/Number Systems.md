
| System      | Base |
| ----------- | ---- |
| Decimal     | 10   |
| Binary      | 2    |
| Octal       | 8    |
| Hexadecimal | 16   |
## Conversion
#### $x$ Base to Decimal

A number is summed for each position in the number as - $\text{value} \times \text{base}^{\text{position}}$

| **Position**       | 3      | 2      | 1      | 0      | -1             | -2              | -3               |
| ------------------ | ------ | ------ | ------ | ------ | -------------- | --------------- | ---------------- |
| **Position Value** | $10^3$ | $10^2$ | $10^1$ | $10^0$ | $10^{-1}$      | $10^{-2}$       | $10^{-3}$        |
| **Quantity**       | 1000   | 100    | 10     | 1      | $\frac{1}{10}$ | $\frac{1}{100}$ | $\frac{1}{1000}$ |
- 352
	- $(3 \times 10^{2}) + (5 \times 10^{1}) + (2 \times 10^{0})$
- 0.542
	- $(5 \times 10^{-1}) + (4 \times 10^{-2}) + (2 \times 10^{-3})$
- $[52]_{8}\rightarrow [42]_{10}$
	- $(5 \times 8^{1}) + (2 \times 8^{0})$

#### Decimal Integer to $x$ Base Successive Division Method
1. Divide the decimal number by the base
2. Record the remainder
3. Repeat the division with the quotient obtained in the previous step until the quotient becomes 0
4. The binary representation is the sequence of remainders read in **reverse order**

$[27]_{10} \rightarrow [11011]_2$

| Divide by 2 | Remainder |
| ----------- | --------- |
| $27 / 2=13$ | 1         |
| $13/2=6$    | 1         |
| $6/2=3$     | 0         |
| $3/2=1$     | 1         |
| $1/2=0$     | 1         |

$[42]_{10} \rightarrow [52]_8$

| Divide by 8 | Remainder |
| ----------- | --------- |
| $42/8=5$    | 2         |
| $5/8=0$     | 5         |

$[125]_{10} \rightarrow [7D]_{16}$

| Divide by  16 | Remainder |
| ------------- | --------- |
| $125/16=7$    | 13        |
| $7/16=0$      | 7         |

#### Decimal Float to $x$ Base Successive Multiplication
1. Multiply the float number with $x$, record the resulting number
2. The record the non-fractional part of the resulting number
3. Keep the first digit record in order from top to bottom, that's the answer

$[0.625]_{10} \rightarrow [0.101]_2$

| Multiply by 2          | Non-fractional |
| ---------------------- | -------------- |
| $0.625 \times 2 =1.25$ | 1              |
| $0.25\times 2 = 0.5$   | 0              |
| $0.5 \times 2 = 1.0$   | 1              |

$[0.3]_{10} \rightarrow [0.23]_8$

| Multiply by 8        | Non-fractional |
| -------------------- | -------------- |
| $0.3 \times 8 = 2.4$ | 2              |
| $0.4 \times 8 = 3.2$ | 3              |
- Question stated here was only to 2 points of precision 

$[0.75]_{10} \rightarrow [0.C]_{16}$

| Multiply by 16        | Non-fractional |
| --------------------- | -------------- |
| $0.75 \times 16 = 12$ | 12             |
| $0.0 \times 16 = 0$   | 0              |

## Non-Base 10 Conversion
For lower base $x$ to higher base $y$, (2 $\rightarrow$ 10), group $x$'s digits in groups of $n$ groups such that $x=2^{n}$
For higher base to lower base, use chart provided for binary

#### Binary to Octal

| Binary | Octal |
| ------ | ----- |
| 000    | 0     |
| 001    | 1     |
| 010    | 2     |
| 011    | 3     |
| 100    | 4     |
| 101    | 5     |
| 110    | 6     |
| 111    | 7     |
$[110 \s 101]_{2}=[65]_8$
- Binary to Octal
	- $[110]_{2}=[6]_8$
	- $[101]_2 = [5]_8$
- Octal to Binary
	- $[6]_{8}= [110]_2$
	- $[5]_{8}=[101]_2$
- Fill left side of base 2 numbers with 0's to fit groups of 3
#### Binary to Hexadecimal

| Binary | Hexadecimal |
|--------|-------------|
| 0000   | 0           |
| 0001   | 1           |
| 0010   | 2           |
| 0011   | 3           |
| 0100   | 4           |
| 0101   | 5           |
| 0110   | 6           |
| 0111   | 7           |
| 1000   | 8           |
| 1001   | 9           |
| 1010   | A           |
| 1011   | B           |
| 1100   | C           |
| 1101   | D           |
| 1110   | E           |
| 1111   | F           |
$[\_\_ 11\s0101]_{2} = [35]_{16}$
- Binary to Octal
	- $[0011]_{2}= [3]_{16}$
	- $[0101]_{2}=[5]_{16}$
- Octal to Binary
	- $[3]_{16}=[0011]_2$
	- $[5]_{16}=[0101]_2$

#### Octal to Hexadecimal
Convert to Binary, and then to that base

#### Powers of 2 (Decimal)

| Position | Power | Decimal |
| -------- | ----- | ------- |
| 1        | 2⁰    | 1       |
| 2        | 2¹    | 2       |
| 3        | 2²    | 4       |
| 4        | 2³    | 8       |
| 5        | 2⁴    | 16      |
| 6        | 2⁵    | 32      |
| 7        | 2⁶    | 64      |
| 8        | 2⁷    | 128     |
| 9        | 2⁸    | 256     |
| 10       | 2⁹    | 512     |
| 11       | 2¹⁰   | 1024    |
| 12       | 2¹¹   | 2048    |
| 13       | 2¹²   | 4096    |
| 14       | 2¹³   | 8192    |
| 15       | 2¹⁴   | 16384   |
| 16       | 2¹⁵   | 32768   |
