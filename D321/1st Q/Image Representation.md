## Color Space and Encodings
#### RGB
0-255, takes 24-bits

#### LAB
- L (Lightness) - perceived brightness (0-100)
- a (Green-Red axis) - positive values represent red hues, negative represent green hues
- b (Blue-Yellow axis) - positive values represent yellow, negative represent blue hues 

#### HSL
- Hue (H) - angular dimension, $0\degree$ corresponding to red, $120\degree$ corresponding to green, $240\degree$ corresponding to blue
- Saturation (S) - 0% corresponding to gray, 100% corresponding to full color
- Lightness (L) - 0% corresponding to black, 100% corresponding to white with 50% representing the pure color

#### HSV
Pretty much the same as HSL but Lightness is now Value and 100% represents the full color instead of 50%

#### YUV
- Luminance (Y) - brightness or intensity of the image (grayscale information)
- Chrominance (U and V) - U represents the blue projection and V represents the red projection

#### RGB to HSL Conversion
max = $\max(R, G, B)$
min = $min(R, G, B)$
$$ 
H = 
\begin{cases} 
0 & \text{if } \max = \min \\
60\degree \times \frac{G-B}{\max-\min} & \text{if } \max = R \\  
60\degree \times \frac{B-R}{\max - \min} + 120\degree & \text{if } \max = G  \\
60\degree \times \frac{R-G}{\max - \min} + 240\degree & \text{if } \max = B  \\
\end{cases} 
$$
$$ 
S = 
\begin{cases} 
0 & \text{if } \max = \min \\
\frac{\max-\min}{\max+\min} & \text{if } L\leq\frac{1}{2} \\  
\frac{\max-\min}{2 - (\max+\min)} & \text{if } L > \frac{1}{2} \\
\end{cases} 
$$
$$L = \frac{1}{2}(\max + \min)$$

#### RGB to HSV Conversion
$\min = \min(R, G, B)$
$V = \max = \max(R, G, B)$
$S = (\max - \min) / \max$
- Or $S=0$ if $V=0$
$$
H = 60 \times 
\begin{cases} 
0 & \text{if } \max = \min \\
0 + (R-B) / (\max - \min) & \text{if } \max = R \\  
2 + (B-R) / (\max - \min) & \text{if } \max = G  \\
4 + (R-G) / (\max - \min) & \text{if } \max = B  \\
\end{cases} 
$$
- $H = H +360$, if $H < 0$

#### RGB to YUV
- $Y = (0.299 \times R) + (0.587 \times G) + (0.114 \times B)$
- $U = 0.492 \times (B-Y)$
- $V = 0.877 \times (R-Y)$

