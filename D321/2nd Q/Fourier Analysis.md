## Fourier Transform
Converts complex waveforms into simple sinusoidal components, providing insight into frequency content
Data can be expressed in multiple equivalent forms, time vs frequency domain

```desmos-graph
height=100
---
y=5\sin(x)
```
+
```desmos-graph
height=100
---
y=5\sin((1/3)x)
```
+
```desmos-graph
height=100
---
y=5\sin(5x)
```
=
```desmos-graph
height=100
---
y=5(\sin(x) + \sin((1/3)x) + \sin(5x))
```
 $$S(f)=\int_{-\infty}^{\infty} s(t) \cdot e^{-i2\pi f t} dt$$
 - $s(t)$ - time domain function
 - $\cdot$ - dot product
- $S(f)$ - frequency domain function
#### Complex Numbers
$z = a + bi$
- $a$ - real part of the complex number
- $b$ - imaginary part of the complex number
- $i$ - imaginary unit, $i = \sqrt{-1}$
$2-3i$ would be placed at 2 on the $x$ real number axis, -3 would be on the $y$ imaginary axis
**Magnitude of a complex number**
$|z|^{2} = \mathbb{R}(z)^{2}+ \mathbb{I}(z)^2$
$|2-3i| = \sqrt{2^{2}+ 3^{2}} = \sqrt{13}$
**Complex conjugate**
$a + bi \s => \s a - bi$
**Squared magnitude by conjugation**
$z \cdot z^{*}= (a+bi)(a-bi)=a^2+b^2=|a+bi|^2$
**Phase angle, relative to the positive real axis**
$z=a+bi$
$\tan(\theta)=\mathbb{I}(z) / \mathbb{R}(z)$
$\theta = \tan^{-1}(\mathbb{I}(z) / \mathbb{R}(z))$
#### Polar Coordinates
$(r, \theta)$
- $r$ - distance from the origin (radius or magnitude)
- $\theta$ - angle, measured from the positive x-axis (radians or degrees)
- $x = r \cos(\theta)$
- $y=r\sin(\theta)$
- $r = \sqrt{x^{2}+ y^2}$
- $\theta = \tan^{-1} (\frac{y}{x})$
- A complex number $z =a+bi \s => \s z=r(\cos(\theta)+ i\sin(\theta))$ 
**Euler's formula**
$e^{ik}=\cos(k)+i\sin(k)$
$z = a + bi\s=>\s z=r \cdot e^{i\theta}$
- $r$ - magnitude of $z$
- $\theta$ - phase angle of $z$
You represent some $k$ on a unit circle with $k$ as its angle and the magnitude of $e^{ik}=1$
- Circle defined by identity $cos^2(\theta)+\sin^2(\theta)=1$ to get magnitudes = 1
- $cos(k)$ as x-axis, $sin(k)$ as y-axis
#### Fourier Analysis
**Sine Waves**
$y(t)=A\cdot \sin(2\pi f t + \phi)$
- $A$ - amplitude
- $f$ - frequency, periods per second/x-unit
- $\phi$ - phase
**Cosine**
$x(t)=A \cdot \cos(2\pi f t + \phi)$
$\cos(2\pi f t) = \sin(2\pi f t + (\pi/2))$
- just a $90\degree$ shifted sine wave
**Analysis**
Any complex waveform can be reconstructed by adding enough sine waves together
- The summed waves are independent, meaning that their dot products are 0
	- This is important because it means that none of these frequencies, (if no duplicates) will interfere with one another
Cosine terms capture even (symmetric) parts of the signal. x-axis
Sine terms capture odd (asymmetric parts), y-axis
You can rewrite these waves into Euler's formula
- $e^{ik} = \cos(k) + i\sin(k) \s=>\s k=2\pi f t  + \theta$
- Still a function of time, like cosine and sine
If you only used real-valued sines or cosines, it would vary based on the phase offset
**Discrete Time Fourier Transform**
Given timeline of frequencies,
Loop over frequencies
- Create sine wave and add it to the sum
Compute dot product between this complex summed sine wave and the signal, this measures how much of the signal aligns with the complex sine wave
The square of the magnitude/amplitude spectrum is called power spectrum
**Continuous Fourier Transform**
$$F(\mu)=\int_{\infty}^{\infty} f(t)e^{j2\pi\mu t} dt$$
If given $F(\mu)$, you can do inverse Fourier transform
$$f(t)=\int_{-\infty}^{\infty}F(\mu)e^{j2\pi\mu t} d\mu$$
- $f(t)$ - time domain
- $F(\mu)$ - frequency domain
**Convolution Theorem**
Convolution is a mathematical operation on two function $f, g$ that produces a third function. It is defined as the integral of the product of the two functions after one is reflected about the y-axis and shifted
Convolution of two functions $f(x)$ and $g(x)$
$g(x) = f(x) * h(x) = \int_{-\infty}^{\infty}f(\tau)h(x-\tau)d\tau$
**Sampling**
Using some $\Delta T$ to probe some function at equal distances to do Fourier transform
**Nyquist Rate**
$\frac{1}{\Delta T} > 2\mu_\max$
Where $\mu$ is the highest frequency or highest frequency that you want to capture from sampling
$\mu_{\max}= \frac{1}{2}\Delta T \s=>\s 2 \mu_{\max}= \Delta T$
2 times the highest frequency is called the Nyquist rate
We want M equally spaced sample of $\tilde{F}(\mu)$ taken over the interval from $\mu=0$ to $\mu=\frac{1}{\Delta T}$
$\mu = \frac{m}{M\Delta T}$
Gives us the Discrete Fourier Transform
$F_{m}= \sum_{n=0}^{M-1} f_{n}e^{-j2\pi m n / M}$
**2D Fourier Transform**
Can do a 2D Fourier transform to represent images and apply filters
**Aliasing**
When the origin function of the wave has overlapping non-independent frequencies that may throw off what your Nyquist rate is and therefore result in overlapping or offsets in the Fourier function, also created from using some sampling rate less than Nyquist rate