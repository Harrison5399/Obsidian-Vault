## Addition

| Input 1 | Input 2 | Sum | Carry |
| ------- | ------- | --- | ----- |
| 0       | 0       | 0   | 0     |
| 0       | 1       | 1   | 0     |
| 1       | 0       | 1   | 0     |
| 1       | 1       | 0   | 1     |
$[1100]_{2}+ [1010]_{2}= [10110]_2$

## Subtraction
$$\begin{align*}\\
  & \quad \textcolor{red}{\s\s\, \s2 \, \s\s2 \, \s2} \\
  & \quad \textcolor{red}{0 \, \cancel{0} \, \cancel{0} \, 2} \\
  & \quad 1 \,\s\s 1 \,\s\s 1 \,\s 0 \\
- & \quad 0 \,\s\s 1 \,\s\s 1 \,\s 1 \\
\hline
  & \quad 0 \, \s\s1 \,\s\s 1 \,\s 1 \\
\end{align*}$$

## Multiplication 

$$\begin{align*}\\
		& \quad \s\s\s\s\s\s 1 \, 0 \, 1 \, 0 \\
\times  & \quad \s\s\s\s\s\s 0 \, 1 \, 1 \, 0 \\
\hline
  & \quad \s\s\s\s\s\s 0 \, 0 \, 0 \, 0 \\
  & \quad \s\s\s 1 \, 0 \, 1 \, 0 \\
  & \s\s\s\s 1 \, 0 \, 1 \, 0 \\
+ \s\s & \s 0 \, 0 \, 0 \, 0 \\
\hline
  & \s 0 \, 1 \, 1 \, 1 \, 1 \, 0 \, 0
\end{align*}$$

## Division
$$
\begin{align*}\\
  & \quad \quad \s\s\s 0 \, 0 \, 1 \, 0 \, 1 \\
  & 1 \, 0 \, 1 \s\s \overline{) 1 \, 1 \, 0 \, 1 \, 1} \\
  & \quad \quad -  1 \, 0 \, 1 \downarrow \, \downarrow \\ 
\hline
  & \quad \quad \s\s\s 0 \, 0 \, 1 \, 1 \, 1 \\
  & \quad \quad \s\s\s\s  - 1 \, 0 \, 1\\
\hline
  & \quad \quad \quad \quad \s 0 \, 1 \, 0 \\
\end{align*}
$$
- $101$ goes into $110$ 1 time, remainder of $001$
- $101$ goes into $111$ 1 time, remainder of $010$
- If you wanted to add more precision, continue with adding a decimal place at the end

## Signed Binary Numbers
Most significant bit is the sign bit, the remaining $n-1$ denote the magnitude of the number
- $0$ - positive
- $1$ - negative

#### Complement of Binary Numbers
**1's Complement** - Flipping all the bits
- 1's to 0's, 0's to 1's
- Used for quicker subtraction

**2's Complement** - Adding 1 to the 1's complement
- $101$ 2's complement - $010 + 1 = 011$
- $1011$ 2's complement - $0100 + 1 = 0101$
- $1101100$ 2's complement - $0010011 + 1 = 0010100$ (does carrying)
- Used for negative numbers
#### Representation 
Consider an 8-bit binary system
$[0000 \s 0000]_{2}=[0]_{10}$
$[0111 \s 1111]_{2}=[127]_{10}$    (max)
$[1000 \s 0000]_{2}= [-128]_{10}$    (min)
$[1111 \s 1111]_{2}= [-1]_{10}$

Negative numbers represented by 2's complement
- converting the given int to binary (without consideration of the negative sign) and then doing 2's complement
Positive numbers represented by their normal binary representation with the MSB being 0

## Handling Fractional Points in Systems
#### Fixed Point Number Representation
Position of the binary point (decimal point) is fixed, predetermined how many bits are for the integer part and how many are used for the fractional part.
- Used in signal processing

##### Packed Binary Coded Decimal (PBCD)
Each digit is encoded using 4-bit binary, two decimal digits are packed into a single byte (8-bits)

| Decimal | BCD  |
| ------- | ---- |
| +       | 1100 |
| -       | 1101 |
- All other numbers convert to binary normally
$[94]_{10}= [1001 \s 0100]_2$
$\quad \quad \quad \quad \text{10's} \quad \text{1's}$

##### Offset or Biased N Binary
Introduces a bias/offset to allow for representation of positive and negative
- $N$ represents bias/offset

Add $N$, typically 127 in 8-bit systems
- **Decimal to Biased Binary**
	- $[23]_{10}+ [127]_{10}= [150]_{10}$
	- or can convert number and offset to binary and do binary addition
	- You are making the half way point 0
		- Number line spans from $-N$ to $0$ to $2^N-1-N$
- **Biased Binary  to Decimal**
	- $[0010 \s 1111]_{2}= [47]_{10}$
	- $47-127 = -80$

#### Floating Point Number Representation
Dynamic format that allows for a wide range of values and precision
- Number is expressed in the form $N=M\times2^E$
	- $M$ - Mantissa (significant digits)
	- $E$ - Exponent (determines position of binary point)


##### IEEE 754
32-bit or 64-bit
- 32-bit - 1-bit sign, 8-bit exponent, 23-bit mantissa, in that order (MSB to LSB)
- 64-bit - 1-bit sign, 11-bit exponent, 52-bit mantissa, in that order (MSB to LSB)

Float $+85.125$ representation - 
- $[85]_{10}= [1010101]_2$
- $[0.125]_{10}=[0.001]_2$
- $[1010101.001]_{2}\times 2^{6}= [1.010101001]_2$ (Normalization)
	- Multiplying a binary by a power of $2^x$ shifts it the places left by $x$
	- So normalize the number such that there is one digit to the left of the decimal
	- The 1 at the left is implied so it **does not need to be stored** and isn't in the final representation
- $[6]_{10}+[127]_{10} = [133]_{10}= [10000101]_2$
- 0 for sign
- Final representation - $[0 \s 10000101 \s 01010100100000000000000]$
