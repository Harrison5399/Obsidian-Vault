
#### Likelihood
$$
L = p^{x_{1}}(1-p)^{1-x^{i}}p^{x_2}(1-p)^{1-x^2}\dots
$$
$$
	= \prod_{i=1}^{N}p^{x_{i}}(1-p)^{1-x_i}
$$
#### Maximum likelihood
- Maximize likelihood
$$
= p^{\sum x_{i}}(1-p)^{N-\sum x_i}
$$
- Take log to make derivation simpler, gives same maximum
$$
= \sum x_{i}\ln p + \sum(1-x_i)\ln(1-p)
$$
$$
\frac{d}{dp} = \frac{\sum x_{i}}{N}
$$
#### Prior
Our belief about what models are possible before we see any data
Given prior distribution -
$$Pr(p) = p^2(1-p)^2$$
$$Pr(p) = Cp^2(1-p)^2$$
- Distributions should integrate to 1
	- Find some C that makes this integrate to 1
$$\int Cp^2(1-p)^{2}dp= 1$$
$$C \int p^{2}(1-p)^{2}dp = 1$$

#### Prior + Data
$$
Pr(Model | Data) = \frac{P(Model)P(Data|Model)}{P(Data)}
$$
?????

$P(H)=p \quad P(T)=1-p$
Data - HTTHH
$P(Data | P) = p^3(1-p)^2$

#### Posterior
$$
Posterior(p) = Prior(P) \quad L(P)
$$
$$
= Cp^{2(1-p)^{2}} \quad p^{H(1-p)^{T}}
$$
$$
= p^{H+2}(1-p)^{T+2}
$$
Given -
Prior 1
0.5, $P(0.9)$
0.6, $P(0.1)$

Prior 2
 $Pr(P)=p^2(1-p)^2$

Take prior 2 -
With likelihood - $p^H(1-p)^T$
$Postierior = p^2(1-p)^{2}\quad p^H(1-p)^T$
             Conjugate Prior
$= c p^{H+2} (1-p)^{T+2}$
- For some c that makes it integrate to 1 (as any distribution should)
- Prior affects posterior make it as if we observed 2 H and 2 T before seeing any data

Posterior Predictive Distribution -
$\int_{p}cp^{H+2}(1-p)^{T+2} p dp$  ?= P(H|p) = p
#### MAP
Max of posterior
arg max posterior

## Beta Distribution
$$
Pr(p) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}p^{a-1}(1-p)^{b-1}
$$
$$
\Gamma(x)=\int\mu^{x-1} e^{-\mu} d\mu
$$
$$
\Gamma(x+1)=x\Gamma(x)=x!
$$
#### Complete form of distribution
$Pr(p)=cp^2(1-p)^2$
$c=\frac{\Gamma(3+3)}{\Gamma(3)\Gamma(3)}$
$=\frac{5!}{2!2!}$

Question why do you add one to plugging in variables
Example - 
$A=\int_{p=0}^{1}p^4(1-p)^3dp$
$= \frac{\Gamma(5+4)}{\Gamma(5)\Gamma{4}}$
CHECK, IT MAY BE -
$= \frac{\Gamma(5+4)}{\Gamma(5)\Gamma{4}} \int \frac{\Gamma(5+4)}{\Gamma(5)\Gamma{4}} p^4(1-p)^3dp$


## Gaussian Distribution
$$X \sim N(\mu, \sigma^{2}) \equiv N(\mu, \frac{1}{\beta})$$
- $\beta = \frac{1}{\sigma^2}$
$E[X]=\mu \quad Var[X]=\sigma^2$
$$

$$

Find likelihood, given -
Data - $x_{1},\dots, x_N$
$L = \prod_{i=1}^Np(x_i)$
using gaussian beta formula instead of sigma
$L=\sqrt{\frac{\beta}{2\pi}}^{N}e^{-\frac{\beta}{2} \sum (x_{i}- \mu)^2}$
take log to do log likelihood
$LogL = \frac{N}{2} \ln\beta -\frac{N}{2}\ln2\pi-\frac{\beta}{2}\sum(x_i-\mu)$

Complete the form of normal distribution
$Pr(x) = e^{-5x^2+6x}$
some how in next line get to:
$= \frac{1}{\sqrt{2\pi}} \frac{1}{\sigma}e^{-\frac{1}{2\sigma^2}(x^{2}-2\mu x + \mu^2)}$
$= \frac{1}{\sqrt{2\pi}} \frac{1}{\sigma}e^{-\frac{1}{2\sigma^{2}}x^2} e^{\frac{\mu}{\sigma^2}x}e^{-\frac{\mu^2}{2\sigma^2}}$
only terms that rely on $x$, pattern match to original formula
$5 = \frac{1}{2\sigma^2}$
$6=\frac{\mu}{\sigma^2}x$
solve and you have your normal distribution

## Properties of an estimator
Estimators are random variables, they are a function of random variables
You want an unbiased estimator
$E[\hat{\theta}]=\theta$
- Shows unbiased
$E[\hat{\mu}]=E[\frac{1}{N} \sum x_i]$
$= \frac{1}{N}\sum E[x_i]$
$=\frac{1}{N}\sum \mu$
$= \mu$
$E[\frac{1}{\beta^{2}}]=E[\frac{1}{N}\sum_i(x_i-\hat{\mu})^2]$
$= E[\frac{1}{N} \sum_i (x_{i}- (\frac{1}{N} \sum_k x_k))^2]$
$= \dots$
$=\frac{N}{N-1}\sigma^2$
- biased, $\hat{\sigma}^2 \not= \sigma^2$
- there is an unbiased one in book

What is a conjugate prior for $\mu$
- normal