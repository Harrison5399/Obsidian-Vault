## Character Encoding
#### ASCII
Each character is assigned a range from 0-127 (7-bits)
Extended ASCII provides +128 characters, using 8-bits
Python -
 - `ord()` char $\rightarrow$ ASCII representation
 - `chr()` ASCII $\rightarrow$ char

#### Unicode
4-bytes to represent character, universal, 100,000 characters

## Text Documents
#### Tokenization
Determine where to delimited what a token is
- Usually a word, punctuation is its own token
- Stop words removed - (the, of, in, is, a)
	- Inflate dimensionality and dominate in similarity

#### Normalization
Lowercase everything, except proper nouns?
Punctuation, use 'locale' normalization, detecting which language it is, ex. U.S.A. to USA
Thesauri, color = colour
Inflection Morphology, never change grammatical class (dog, dogs)
Derivation Morphology, Often change grammatical class (build, building; health, healthy)
Lemmatization, am, are, is $\rightarrow$ be; car, cars, car's, cars' $\rightarrow$ car
Stemming, similar terms derived from a common stem (engineer, engineered, engineering)
- Also used in information retrieval (think about searching for something)
- Consists of removing suffixes and conflating the resulting morphemes, occasionally prefixes are also removed

## Text Representation
#### Vector Space Models (VSM)
Semantic space representation of tokens like what LLM's use
Magnitude and direction represent differences 

Cosine similarity
$$\cos(A, B) = \frac{A \cdot B}{||A||_2 ||B||_2} = \frac{\sum_{i=1}^{n} A_i B_i}{\sqrt{\sum_{i=1}^n A_i^2} \sqrt{\sum_{i=1}^n B_i^2}}$$
Used in information to determine which document $d_1$ or $d_2$ is more similar to query $q$
- The document with the smaller angle (similarity near 1) represents the more similar document
- $cos(d_{j,}q)$

Also used in clustering to group similar documents or sentences

#### Label Encoding
Represents each category as a unique integer then put into a vector

#### One-hot Encoding
Has the Out of Vocabulary (OOV) problem, ex. 'fruit' does not exist in vocabulary, therefore length is directly proportional to vocabulary size

#### Bag of Words
Simplifies a document by treating it as an unordered set of words disregarding grammar and word order but keeping track of word frequency
- 'The cat sat in the hat'
	- $[1,1,1,1,0,0,0]$
- 'The cat sat on the mat'
	- $[1,1,0,0,1,1,1]$

#### Bag of N-Grams
Extension of the BoW model, includes sequence of adjacent words known as 'n-grams' (sequence of n items providing context to the word)
- Unigram (1-gram) - 'apple', 'orange', 'banana'
- Bigram (2-gram) - 'I love', 'natural language', 'machine learning'
- Trigram (3-gram) - 'Bag of N-Grams', 'love natural language', 'natural language processing'
- Vocabulary is expanded to the N-items: ex. consider the 2-gram example, the vocabulary is each of those sequences, not just a single word, each of those is encoded into a vector

**Pros**
- Captures more context than BoW, able to capture some semantic similarity
**Cons**
- As $n$ increases, dimensionality (and therefore sparsity) increases rapidly
- Provides no way to address the OOV problem

#### Term Frequency-inverse Document Frequency (TF-IDF)
**TF** - measures how often a token in a given document occurs $$TF(t, d) = \frac{(\text{Number of occurrences of term } t \text{ in document } d)}{(\text{Total number of terms in the document } d)}$$
**IDF** - measures the importance of the term across a corpus (collection of documents)
$$
IDF(t) = \log_{e}\frac{(\text{Total number of documents in the corpus})}{(\text{Number of documents with term } t \text{ in them})}
$$
**TF-IDF score** - $TF * IDF$

#### Distributed Representation - Word Embeddings
Dense, low-dimensional representation of tokens, like what modern LLM's use
- King - Man + Woman $\sim$ Queen


