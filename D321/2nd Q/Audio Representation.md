## Binary Representation
Sample the height of the audio wave at at least the Nyquist rate, or 2 times the maximum frequency
**Bit Depth** - refers to the number of bits of information used in each sample of the wave
$File Size = Duration (sec) \times Sample Rate (Hz) \times Bit Depth \times Channels$
- Channels is how many separate audio signals there are
**Short form Fourier Transform**
Using some window size and hop size, both units of time, to do Fourier transforms
## Data Compression
**Lossless** - original data can be perfectly reconstructed
- Ex. bitmaps
**Lossy** - some data may be lost during compression
- Ex. JPEG (joint photographic experts group)
Data contains irrelevant or repeated information called redundant data $R$
$R = 1 - 1/C$
- $C$ - Compression ratio
$C = b/b'$
- $b, b'$ - denote the number of bits in two representation of the same information
- $C=10$ means larger representation has 10 bits of data for every 1 bit of data in the smaller representation
How many bits are needed to represent the information
$I(E)=\log_{b}(1/p(E))$
- Where $p(E)$ probability of seeing event $E$
	- $p(E)$ can be entropy
**Huffman Code**
Binary tree where leaf nodes are characters at that level, the higher up the tree (less bits) represent more frequently occurring characters