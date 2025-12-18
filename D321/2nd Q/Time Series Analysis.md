A time series can be generally expressed as a sum or product of four distinct components
$Y_{t}= M_{t}+ S_{t}+C_{t}+\epsilon_t$
- $M$ - trend
- $S$ - seasonality
- $C$ - cyclical fluctuations
- $\epsilon$ - noise
**Univariate Models**
Autoregressive (AR) models
Current value $Y_t$ is expressed as a function of its past values, capturing self-dependence in the series
$Y_{t}= f(Y_{t-1,}Y_{t-2}, \dots, Y_{t-p}) + \epsilon_t$
$Y_{t}= \phi_{0} +\phi_{1}Y_{t-1}+ \phi_{2}Y_{t-1}+ \dots +\phi_{p}Y_{t-p}+\epsilon_t$
- $\phi$ - parameters/weights to learn
**Autocovariance** - measures the linear dependence between two points, choppy series tend to have a value near 0
$\gamma_x(s,t)=\text{cov}(x_{s,}x_{t})=\mathbb{E}[(x_s-\mu_s)(x_t-\mu_t)]$
- With $s, t$ being two values in a time series $X_{t}, X_t-k$ shows how they vary together over lag $k$
	- Positive, both values move in the same direction
	- Negative, when one is above the mean, the other tends to be below
	- Large values, shows strength of dependence
**Autocorrelation function (ACF)** - measures the linear predictability
$\rho(s, t) = \frac{\gamma(s,t)}{\sqrt{\gamma(s,s)\gamma(t,t)}}$
**Stationary**
Stationary if the mean is constant and does not depend upon time
- Means a time series has constant mean, variance, and autocovariance over time
- Most models rely on stationary data
- Must achieve stationary data
**Simple moving average**
$SMA_{t}= (x_{t}+ x_{t-1}+\dots+x_{t-n+1})/n$
- $x_t$ - value at time $t$
- $n$ - window size
**Exponential moving average**
$EMA_{t}= \alpha \cdot x_{t} + (1-\alpha)\cdot EMA_t-1$
- $\alpha$ - smoothing factor
- $EMA_0$ - is set to the first datapoint or the SMA of initial values
**Holt Smoothing**
