# Machine Learning: Introduction, MLE

Lecture Notes on Jan 13

Modified by Zhou (Spring 2025)

# About the class...

Instructor: Dongruo Zhou

dz13@iu.edu Office: Luddy Hall 3130

![](./images/fHYVovzqIP48ogxgOZUMLmXy8k2i3gftT.png)

Research interest:

Machine learning, including....

Reinforcement learning (how to explore environment efficiently?)

Optimization (how to train deep learning model?) Adversarial training (how to make your model robust?)

3

# Introduction of ML

Slides adapted from Tang, B455 SP 2021

# What is Machine Learning?

·Machine learning: making computers modify or adapt their actions (whether these actions are making predictions, or controlling a robot) so that these actions get more accurate, where accuracy is measured by how well the chosen actions reflect the correct ones.

- Computational complexity of machine learning algorithms is particularly important in the context of learning on verylarge datasets.

·Complexity of training vs. complexity of inferencing (e.g., applying the trained algorithm to making predictions). Training is one-time computation, and thus can be relatively slow.

# Applications of Machine Learning:

examples

 Speech recognition Recommendation system Autonomous driving. Autonomous robots Disease diagnosis Natural language synthesis / Machine translation Games: AlphaGo Spam-filter for e-mail

# Type of Machine Learning

 Supervised Learning: "learn" a model from input objects with desired output

 Regression Classification

- Unsupervised Learning: discovering patterns in input objects without labels

 Clustering Compression

- Reinforcement Learning: "enhance" a model for an environment with maximum some cumulative rewards

IGame Behavior Selectior Planning

# Supervised Learning: Regression

![](./images/fM38P7qLKMafu6T89kwihfnPEGvvexbUI.png)

![](./images/fGtY7an7Ba3e9soxPy7ToCd61XfZn10Rh.png)

FIGURE 1.3 Top left: A few datapoints from a sample problem. Bottom left: Two possible ways to predict the values between the known datapoints: connecting the points with straight lines, or using a cubic approximation (which in this case misses all of the points). Top and bottom right: Two more complex approximators (see the text for details) that pass through the points, although the lower one is rather better than the top.

when $\mathbf{x}=0.44,\mathbf{t}=?$

# Supervised Learning: Classification.

![](./images/fqn8xfGdLtHsaAayNthhm1reMgpnrQyCm.png)

To build a coin classifier (e.g. for the vendor machines using New Zealand coins), based on the measures of the color, diameter, the weight, and possibly the shape (choosing a number to represent the shape would involve an encoding for example that 1= circle, 2= hexagon, etc.). Note:. color alone does not work: $20\zeta$ and $50c$ coins areboth silver and the $\grave{S}1$ and 52 coins both bronze. Combining color with shape, however, may work.

![](./images/frLQo8Rir7LL1uABluPOpmF5gX5ScSbek.png)

FIGURE 1.5 Left: A set of straight line decision boundaries for a classification problem. Right: An alternative set of decision boundaries that separate the plusses from the lightening strikes better, but requires a line that isn't straight.

## Un-supervised Learning: Clustering

![](./images/f3ZwmZENuCzY4XDxKZUDTy08YsTDyHagU.png)

Un-supervised Learning: Dimension Reduction by Principle Componente Analvsis (PCA)

![](./images/flRVdKNdgxm9gtuZinW1ggPL49RzUfC58.png)

FIGURE 6.7 Computing the principal components of the 2D dataset on the left and using only the first one to reconstruct it produces the line of data shown on the right, which is along the principal axis of the ellipse that the data was sampled from.

# Machine Learning Processes.

· Data Collection and Preparation

- Feature Selection / Engineering

·Identification of features that are useful for the learning

·The features can be collected without significant expense or time, and that they are robust to noise and other corruption of the data that may arise in the collection process.

- Exploratory data analysis.

 Algorithm Choice.

Parameter and Model Selection

·For many of the algorithms there are parameters that have to be set manually, or that require experimentation to identify appropriate values.

# Machine Learning using Python

·Why Python?

·Easy to implement

· Lots of packages for ML

- Python scientific packages

·NumPy (Appendix A in MLAP)

 Matplotlib ·pandas . Scikit-learn Sample codes: - PML: https://github.com/rasbt/python-machine-learning-book-2nd-edition

Course logistics

# Course Information

· Instructor: Prof. Dongruo Zhou, Office Location: Luddy 3130

. Teaching Assistants: Ruhan Wang, Al Runze Zhao, Al

.QA:

.Email: b455iub@gmail.com (Emails sent to other addresses will not be considered . Canvas Discussion channel

. Class Schedule: Time: 2:20-3:35 PM, Monday and Wednesday Location: Global and International Studies Building (GlS) 1118

· Office Hours: Refer to Canvas for the schedule.

# What do you need for this course?

· Lots of machine learning courses at IU...

 ...This course provides an introduction to machine learning algorithms that learn from and make predictions on data. We will explore the statistical, mathematical, and computational foundations of these frameworks. Emphasis will be placed on understanding mathematical derivations and implementing algorithms to gain hands-on experience...

·This course requires a solid foundation in linear algebra and statistics. Additionally, a sufficient programming background is needed, with a primary focus on Python.

· Don't forget to try Homework 1 to test your skills—the deadline is in two weeks!

# Grading Breakdown

1. Homework Assignments: 45 points 2. Exams (Midterm and Final): 50 points 3. Participation: 5 points

# Homework - 45 pts

. Structure:

6 homework assignments, each worth 9 points.

The final score will be the sum of the top 5 homework scores.

Each homework includes $\sim5$ written problems and 1-2 coding problems.

Each homework covers about 2 weeks content, from the released date

. Submission Guidelines:

·Submit a single PDF file containing your answers, including plots or tables generated by your code. Both written answers and typed answers (for example, Latex) are accepted. Source code is not required in submissions.

# Homework - 45 pts

· Grading and Regrading Policy:

Solutions will be provided 7 days after the deadline. Scores will be released no later than 14 days after the deadline. Regrading requests will be accepted for up to 21 days after the deadline.

· Late Submission Policy: A penaltyof $0.5\%$ per hour will be applied to late submissions, calculated as:

Final Score = max(0, 1 - 0.5% $x$ Late Hours)* Original Score

.Rules:

Programming Language: Python (preferred) Title of Homework-related emails must follow this format (otherwise it will be ignored): [B455-your_id-Hw#] Topic of Request Example: [B455-dz13-Hw1] Concerns about Question 1'.

# Exam - 50 pts

.Structure:

Two exams: Midterm (Week 9) and Final (Week 16), each worth 25 points.

Both exams will include multiple-choice and fill-in-the-blank questions.

. Coverage:

Midterm: Content from Weeks 1-7.

.Final: Content from Weeks 816.

·Rules:

 No makeup exams will be offered. Bring a calculator for calculations.

You may prepare a 1-page, double-sided A4 "cheat sheet."

# Participation - 5 pts

Structure:

There will be 10 in-class open-ended discussions, lasting 5-10 minutes each.

Studentsmustparticipate in at least 2 discussions to earn full credit:

. 1 point: No participation. . 3 points: Participation in 1 discussion. . 5 points: Participation in 2 discussions.

. Process:

Speakfor 30seconds to 1 minute on the topic. ：Record theuniqueparticipation codedisplayed on the screen and take apicture of it. Submit the code to Canvas after class.

.Rules:

Using another student's code or submitting fabricated codes will result in a loss of all participation points.

### 21 Probability review

Slides adapted from UW CSE 446

# Definitions

- Random Variable: A variable that takes on different values determined randomly.

Example: The height of a person from the US.·

Distribution: The different values a random variable can take on along with the probability of that value.

· We talk about sampling from a distribution:

"Considera sample of 1o0 different heights of people from the US drawn randomly from the distribution of all heights."

# Independence

### Let X and Y be random variables

Ex. X is the outcome of the first roll of a 6-sided dice, Y is the outcomeof thesecond roll of the dice (X and Y take values in {1,2,3,4,5,6} each with equal probability)

An event is statement about the world that holds or not:

Define events
$$\begin{aligned}
&A=\{X\in\{3,4\}\}, \\
&B=\{X=1\}, \\
&C=\{Y\in\{3,4\}\}
\end{aligned}$$

$$P(A)=P(X\in\{3,4\})=$$

# Independence

### Let X and Y be random variables.

Ex. X is the outcome of the first roll of a 6-sided dice, Y is the outcome of the second roll of the dice (X and Y take values in {1,2,3,4,5,6} each with equal probability

An event is statement about the world that holds or not:

Define events
$$\begin{aligned}
&A=\{X\in\{3,4\}\}, \\
&B=\{X=1\}, \\
&C=\{Y\in\{3,4\}\}
\end{aligned}$$

Every event is assigned aprobability:
$$P(A)=P(X\in\{3,4\})=1/3$$

# Independence

### Let X and Y be random variables.

Ex. X is the outcome of the first roll of a 6-sided dice, Y is the outcome of the second roll of the dice. (X and Y take values in {1,2,3,4,5,6} each with equal probability)

An event is statement about the world that holds or not:

Define events.
$$\begin{aligned}
&A=\{X\in\{3,4\}\}, \\
&B=\{X=1\}, \\
&C=\{Y\in\{3,4\}\}
\end{aligned}$$

For say events $U_{\boldsymbol{'}}V$ are independent if $P(U\cap V)=P(U)P(V)$

# Independence

### Let X and Y berandom variables

Ex. X is the outcome of the first roll of a 6-sided dice, Y is the outcome of the second roll of the dice. (X and Y take values in {1,2,3,4,5,6} each with equal probability)

An event is statement about the world that holds or not:

Define events
$$\begin{aligned}
&A=\{X\in\{3,4\}\}, \\
&B=\{X=1\}, \\
&C=\{Y\in\{3,4\}\}
\end{aligned}$$

For say events $U_{\boldsymbol{\prime}}V$ are independent if $P(U\cap V)=P(U)P(V)$

We define the conditional probability of event $U$ given $V$ as

![](./images/fWgpI2eTRGC9ssDcuTlLH2pmwheg6M2vQ.png)

What is $P(X\leq4|X\geq3$ ？

# Independence

### Let X and Y berandom variables

Ex. X is the outcome of the first roll of a 6-sided dice, Y is the outcome of the second roll of the dice (X and Y take values in {1,2,3,4,5,6} each with equal probability)

An event is statement about the world that holds or not:

Define events
$$\begin{aligned}
&A=\{X\in\{3,4\}\}, \\
&B=\{X=1\}, \\
&C=\{Y\in\{3,4\}\}
\end{aligned}$$

For say events $U_{\boldsymbol{\prime}}V$ are independent if $P(U\cap V)=P(U)P(V)$

We define the conditional probability of event $U$ given $V$ as

![](./images/fiiLg8WTlrB7LITEwggUlZuRhIyPLmhtG.png)

Observe: if $U,V$ are independent then $P(U|V)=P(U)$ In words: if independent, V tells you nothing about U (and vice versa)

# Mean, variance

Mean

Var(X), 02 Variance

Median

# Mean, variance

The mean is a prediction of the value of the random variable. Answers the question "What do I expect the height of a random person to be?"

![](./images/fUhLio4Q72F3zzprLFI1pc6BdTl4wRugP.png)

The variance captures the spread in your data. Also captures the error in the prediction using the mean. "How much do people's heights deviate?"

$$\mathbb{E}[(X-\mathbb{E}[X])^2]$$

Maximum Likelihood Estimation

Slides adapted from UW CSE 446

# Your first consulting job

 Billionaire: I have special coin, if I flip it, what's the probability it will be heads?

·You: Please flip it a few times:

·You: The probability is: Billionaire: Why?

# Coin - Binomial Distribution

Data: sequence $D=$ (HHTHT...), k heads out of n flips

Hypothesis:
$$\mathrm{s:P(Heads)=\theta,P(Tails)=1-\theta}$$

· Flips are i.i.d.: Independent events Identically distributed according to Binomial distribution

$$P(\mathcal{D}|\theta)=\theta^k(1-\theta)^{n-k}$$

# Maximum Likelihood Estimation

- Maximum likelihood estimation (MLE): Choose $\theta$ that maximizes the probability of observed data:

![](./images/fU3VT7T8GayzD6ryVtToakWytOxvqKlV7.png)

## Maximum Likelihood Estimation

$$\begin{aligned}\widehat{\theta}_{MLE}&=\arg\max_{\theta}\:\log P(\mathcal{D}|\theta)\\&=\arg\max_{\theta}\:\log\theta^{k}(1-\theta)^{n-k}\end{aligned}$$

$$\boxed{\frac d{d\theta}\log P(\mathcal{D}|\theta)=0}$$

# Maximum Likelihood Estimation.

Observe $X_{1},X_{2},\ldots,X_{n}$ drawn IID from $f(x;\theta)$ for some “true” $\theta=\theta_{*}$ Likelihood
$$\begin{aligned}&\mathbf{function}\quad L_{n}(\theta)=\prod_{i=1}^{n}f(X_{i};\theta)\\&\mathbf{ood}\:\mathbf{function}\:l_{n}(\theta)=\log(L_{n}(\theta))=\sum_{i=1}^{n}\log(f(X_{i};\theta)\end{aligned}$$

Log-Likelihood

Maximum
$$\mathrm{hood~Estimator~(MLE)~}\widehat{\theta}_{MLE}=\arg\max_{\theta}$$

# What about continuous variables?

Billionaire: What if I am measuring a continuous variable? You: Let me tell you about Gaussians...

$$P(x\mid\mu,\sigma)=\frac1{\sigma\sqrt{2\pi}}e^{\frac{-(x-\mu)^2}{2\sigma^2}}$$

![](./images/fsXQCWGnbeQyMp9fNXZtBX1toqgBVWMRF.png)

# Some properties of Gaussians

· affine transformation (multiplying by scalar and adding a constant)

$$\begin{array}{ll}{\bullet\:\mathrm{X}\sim N(\mu,\sigma^{2})}\\{\bullet\:\mathrm{Y}=\mathrm{aX}+\mathrm{b}}&{\rightarrow\:\mathrm{Y}\sim N(\mathrm{a\mu}+\mathrm{b},\mathrm{a}^{2}\sigma^{2})}\\\end{array}$$

· Sum of Gaussians
$$\begin{aligned}
&\text{Vulli Vi Vunvoluliv} \\
&\bullet\times\sim N(\mu_X,\sigma_X^2) \\
&\bullet\mathrm{~Y\sim N(\mu_Y,\sigma_Y^2)} \\
&\bullet\mathrm{~Z=X+Y~\to~Z\sim N(\mu_{X}+\mu_{Y},~\sigma_{X}^{2}+\sigma_{Y}^{2})}
\end{aligned}$$

# MLE for Gaussian

. Prob. of i.i.d. samples $D{=}\{\mathbf{x}_{1},\ldots,\mathbf{x}_{\mathrm{n}}\}$ (e.g., temperature):

$$\begin{aligned}
P(\mathcal{D}|\mu,\sigma)& =P(x_1,\ldots,x_n|\mu,\sigma)  \\
&=\left(\frac{1}{\sigma\sqrt{2\pi}}\right)^{n}\prod_{i=1}^{n}e^{-\frac{(x_{i}-\mu)^{2}}{2\sigma^{2}}}
\end{aligned}$$

· Log-likelihood of data:

$$\operatorname{og}P(\mathcal{D}|\mu,\sigma)=-n\operatorname{log}(\sigma\sqrt{2\pi})-\sum_{i=1}^{n}\frac{(x_{i}-\mu)^{2}}{2\sigma^{2}}$$

· What is $\widehat{\theta}_{MLE}$
$$\theta=(\mu,\sigma^2)?$$

# MLE for mean of a Gaussian

![](./images/fmRHkss5bUcFQuGGUWHORIs0PXFyiGAOg.png)

 Recall what we have done for Binomial distribution..

## MLE for variance

![](./images/fZOz1dmWaqaCPQxB0qndDi37RSXxrvAy6.png)

# Learning Gaussian parameters

·MLE:

![](./images/fSPr9tGGe72X4smSIQvr89V2eMqbxHMK8.png)

· MLE for the variance of a Gaussian is biased

$$\mathbb{E}[\widehat{\sigma^2}_{MLE}]\neq\sigma^2$$

· Unbiased variance estimator:
$$\widehat{\sigma^2}_{unbiased}=\frac{1}{n-1}\sum_{i=1}^n(x_i-\widehat{\mu}_{MLE})^2$$

# Maximum Likelihood Estimation

Observe $X_{1},X_{2},\ldots,X_{n}$ drawn IID from $f(x;\theta)$ for some “true" $\theta=\theta_{*}$

Likelihood
$$\begin{aligned}&\mathbf{function}\quad L_{n}(\theta)=\prod_{i=1}^{n}f(X_{i};\theta)\\&\mathbf{ood}\:\mathbf{function}\:l_{n}(\theta)=\log(L_{n}(\theta))=\sum_{i=1}^{n}\log(f(X_{i};\theta)\end{aligned}$$

Log-Likelihood

Maximum Likelihood Estimator (MLE) OMLE = arg max Ln(0)

Under benign assumptions, as the number of observations $n\to\infty$ we have $\widehat{\theta}_{MLE}\to\theta_{\text{ 求}}$

# Application

·Why is it useful to recover the “true" parameters of a probabilistic model?

· ·Estimation of the parameters $\theta_{*}$ is the goal

· · Help interpret or summarize large datasets

··Make predictions about future data ·Generate new data $X\sim f(\cdot;\widehat{\theta_{MLE}})$

# Estimation

Observe $X_{1},X_{2},\ldots,X_{n}$ drawn ID from $f(x;\theta)$ for some “true” $\theta=\theta_{*}$

A/B testing

How do we figure out which ad results in more click-through?

. $\theta_{*}$ are the “true" average rates . $X_1$ $X_1$ $X_1,X_2.$ $X_2$ $X_2$ .... are binary "clicks"

![](./images/f16LBGMA0NRC8tewPc4gZA5qvtTpSbLfr.png)

# Prediction

Observe $X_1,X_2,\ldots,X_n$ drawn IID from $f(x;\theta)$ for some “true” $\theta=\theta_{*}$

### Content recommendation

Can we predict how much someone will like a movie based on past ratings? . $\theta_{z_{k}}$ describes user's preferences.

. $X_1,X_2$, .... are (movie, rating) pairs

![](./images/fFgS4NIuArFG9U2Gc78M4YBLst83wuKed.png)

Object recognition / classification Identify a flower given just its picture? . $\theta_{_{\text{冰}}}$ describes the characteristics of

each kind of flower. . $X_1,X_2$ .... are the (image, label) pairs

![](./images/fL1vcE7GIqSGayTaMkPuIEiOnhF5qr9ie.png)

Figure I.1: Three types of Iris flowers: Setosa, Versicolor and Virginicn.Used with kind permission of Dennis Kramb and SIGNA

# Generate

Observe $X_1,X_2,\ldots,X_n$ drawn IID from $f(x;\theta)$ for some “true” $\theta=\theta_{*}$

"Kaia the dog wasn't a natural pick to go to mars. No one could have predicted she would..."

### Text generation

Can Al generate text that could have been written like a human?. . $\theta_{*}$ describes language structure . $X_1,X_2$, .. are text snippets found online

![](./images/fsvthNY0kGCS2c00cUSGiokx5KxXYkMg6.png)
https://chat.openai.com/chat

"dog talking on cell phone under water, oil painting"

### Image to text generation

![](./images/fNLOZxeSXPxUMHagXCe7fv6pWG1wrG4NZ.png)
https://labs.openai.com/

Can Al generate an image from a prompt? . $\theta_{\text{添}}$ describes the coupled structure of images and text . X $X_{1}$ $X_1,X_2.$ X2 $X_2$ .... are the (image, caption) pairs found online

# Machine Learning: Linear Regression

Lecture Notes on Jan 22

Modified by Zhou (Spring 2025)

### 2

# Linear Regression

Slidesadapted from UW CSE 446

# The regression problem, 1-dimensional

Given past sales data on zillow.com, predict:

$y=$ House sale price from $x=$ {# sq. ft.}

$$\text{Training Data:}\quad x_i\in\mathbb{R}\\\{(x_i,y_i)\}_{i=1}^{n}y_i\in\mathbb{R}$$

![](./images/fgZWvESGAYw6xkl9t2o63xq3glwTR7cyq.png)

# The regression problem, 1-dimensional

Given past sales data on zillow.com, predict: $y=$ House sale price from $x=$ {# sq. ft.}

c E R Training Data: yiER {(ci, yi)}=1

![](./images/fRbscyiLEZOOVGkiXiG00TLdfIfOgCxUL.png)

![](./images/ftUgvZuzmcwO6aEACoBLguPPOhp5ybe0B.png)

# The regression problem, d-dim

Given past sales data on zillow.com, predict: $y=$ House sale price from $x=$ {# sq. ft., zip code, date of sale, etc.}

![](./images/fS40qlTR2GZSd18HBuIwRONPgyWpTweza.png)

![](./images/fLrX2r8Py6gGNFfgO0kiHzYu9v5NNkgmD.png)

![](./images/fVEHT0w9sF825AGE41TGIUxabAX02311Y.png)

# The regression problem, d-dim

Given past sales data on zillow.com, predict: $y=$ House sale price from $x=$ {# sq. ft., zip code, date of sale, etc.}

![](./images/fBibfBYmgn8whaRkbXBAFIbxwOhabUk3N.png)

![](./images/ffEwGTKfhoGE7hdk28lqDOGOHyOm2u0UY.png)

![](./images/fqSvgPh5FhVqxY8guwK2wxNdEklgSZTaS.png)

# Maximizing log-likelihood

$$\begin{aligned}&\text{raining Data:}\quad x_{i}\in\mathbb{R}^{d}\\&(x_{i},y_{i})\}_{i=1}^{n}\quad y_{i}\in\mathbb{R}\quad p(y|x,w,\sigma)=\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-(y-x^{\top}w)^{2}/2\sigma^{2}}\end{aligned}$$

Likelihood:
$$P(\mathcal D|w,\sigma)=\prod_{i=1}^np(y_i|x_i,w,\sigma)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(y_i-x_i^\top w)^2/2\sigma^2}$$

$$\mathrm{imize~(wrt~}w\};\quad\log P(\mathcal{D}|w,\sigma)=\log\left(\prod_{i=1}^{n}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-(y_{i}-x_{i}^{\top}w)^{2}/2\sigma^{2}}\right)$$

# Maximizing log-likelihood

$$\begin{aligned}&\text{iraining Data:}\quad x_{i}\in\mathbb{R}^{d}\\&(x_{i},y_{i})\}_{i=1}^{n}\quad y_{i}\in\mathbb{R}\quad p(y|x,w,\sigma)=\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-(y-x^{\top}w)^{2}/2\sigma^{2}}\end{aligned}$$

Likelihood:
$$P(\mathcal{D}|w,\sigma)=\prod_{i=1}^np(y_i|x_i,w,\sigma)=\prod_{i=1}^n\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(y_i-x_i^\top w)^2/2\sigma^2}$$

$$\mathrm{imize~(wrt~}w\};\quad\log P(\mathcal{D}|w,\sigma)=\log\left(\prod_{i=1}^{n}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-(y_{i}-x_{i}^{\top}w)^{2}/2\sigma^{2}}\right)$$

![](./images/flxHcgyPXmiCOw29rrFoSEr30LFgc93ry.png)

# Maximizing log-likelihood

$$\widehat{w}_{MLE}=\arg\min_w\sum_{i=1}^u(y_i-x_i^\top w)^2$$
Set derivate=0,solve for w

# Maximizing log-likelihood

$$\widehat{w}_{MLE}=\arg\min_w\sum_{i=1}^u(y_i-x_i^\top w)^2$$
Set derivate=0,solve for w

![](./images/fXzZvztvh7RRgOeOQqdi4oE9U6BsvAi60.png)

# The regression problem in matrix

notation

$$\widehat{w}_{MLE}=\arg\min_w\sum_{i=1}^n(y_i-x_i^\top w)^2$$

d:#of features n : # of examples/datapoints

![](./images/fGDDbmaioIX8cnzuEdetG0tHE6p92puaH.png)

# The regression problem in matrix

notation

![](./images/fRwzgk9Wz2xgLnDn68ogZSyZETgc7TDx3.png)

# The regression problem in matrix

notation

d : # of features n :# of examples/datapoints

$$\widehat{w}_{MLE}=\arg\min_w\sum_{i=1}^n(y_i-x_i^\top w)^2$$

![](./images/f3dYsTFx6pWEIPVEG6g2lCOmFOiAx8TXT.png)

$$\begin{aligned}
\widehat{w}_{LS}& =\arg\min_{w}||\mathbf{y}-\mathbf{X}w||_{2}^{2}  \\
&=\arg\min_{w}(\mathbf{y}-\mathbf{X}w)^{T}(\mathbf{y}-\mathbf{X}w)
\end{aligned}$$

$$\boxed{\ell_2\text{norm:}\|z\|_2=\sqrt{\sum_{i=1}^nz_i^2}=\sqrt{z^\top z}}$$

# The regression problem in matrix

notation

$$\widehat{w}_{MLE}=\arg\min_w\sum_{i=1}^n(y_i-x_i^\top w)^2$$

d :#of features n : # of examples/datapoints

![](./images/ftuTeIDi7sEw1aKI3G6dFOxCTpTlRkK6U.png)

$$\boxed{\widehat w_{LS}=\widehat w_{MLE}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{Y}}$$

The regression problem in matrix

notation

![](./images/fXgsKbGoCtcEzbNkwPauSvgp1qpuLg2If.png)

$$\begin{gathered}
\widehat{w}_{LS} =\arg\min_w||\mathbf{y}-\mathbf{X}w||_2^2 \\
=(\mathbf{X}^{T}\mathbf{X})^{-1}\mathbf{X}^{T}\mathbf{y} 
\end{gathered}$$

What about an offset?

$$\begin{aligned}\widehat{w}_{LS},\widehat{b}_{LS}&=\arg\min_{w,b}\sum_{i=1}^{n}\left(y_{i}-(x_{i}^{T}w+b)\right)^{2}\\&=\arg\min_{w,b}||\mathbf{y}-(\mathbf{X}w+1b)||_{2}^{2}\end{aligned}$$

## Dealing with an offset

$$\widehat{w}_{LS},\widehat{b}_{LS}=\arg\min_{w,b}||\mathbf{y}-(\mathbf{X}w+\mathbf{1}b)||_2^2$$

# Dealing with an offset

$$\widehat{w}_{LS},\widehat{b}_{LS}=\arg\min_{w,b}||\mathbf{y}-(\mathbf{X}w+1b)||_2^2$$

$$\mathbf{X}^{T}\mathbf{X}\widehat{w}_{LS}+\widehat{b}_{LS}\mathbf{X}^{T}\mathbf{1}=\mathbf{X}^{T}\mathbf{y}\\\mathbf{1}^T\mathbf{X}\widehat{w}_{LS}+\widehat{b}_{LS}\mathbf{1}^T\mathbf{1}=\mathbf{1}^T\mathbf{y}$$

$\mathbf{X}^{T}1=0$ (i.e., if each feature is mean-zero) then
$$\begin{aligned}&\widehat{w}_{LS}=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{Y}\\&\widehat{b}_{LS}=\frac{1}{n}\sum_{i=1}^{n}y_{i}\end{aligned}$$

# Make Predictions

$$\begin{aligned}
\widehat{w}_{LS}& =(\mathbf{X}^{T}\mathbf{X})^{-1}\mathbf{X}^{T}\mathbf{Y}  \\
\widehat{b}_{LS}& =\frac1n\sum_{i=1}^ny_i 
\end{aligned}$$

A new house is about to be listed. What should it sell for?
$$\hat{y}_\mathrm{new}=x_\mathrm{new}^T\hat{w}_{LS}+\hat{b}_{LS}$$

# Process

· Decide on a model for the likelihood function $f(x;\theta)$

·Find the function which fits the data best ·Choose a loss function- least squares ·Pick the function which minimizes loss on data · Use function to make prediction on new examples

# Machine Learning: (non) Linear Regression, cross-validation, biasvariance tradeoff

Lecture Notes on Jan 27,29

Modified byZhou (Spring 2025)

2

With
$$\text{Linear regressic}\\\text{nonlinear}\\\text{basis functions}$$

Slides adapted from Uw CsE 446

## Recap: Linear Regression

![](./images/fViqAG9pbGpfZBS2kcqDs5EiATpaQ1G5m.png)

· In general high-dimensions, we fit a linear model with intercept $y_{i}\simeq w^{T}x_{i}+b$ . or equivalently $y_{i}=w^{T}x_{i}+b+\epsilon_{i}$ with model parameters $(w\in\mathbb{R}^{d},b\in\mathbb{R})$ I that minimizes $\ell_2$ -loss

![](./images/fiHklM9fgnbfa53ZVQCC6VkxG3KBmb3Eo.png)

# Recap: Linear Regression.

· The least squares solution, i.e. the minimizer of the $\ell_2$ -loss can be written in a closed form as a function of data $X$ and y as

or equivalently using straightforward linear algebra by setting the gradient to zero:

$$\begin{bmatrix}\widehat{w}_\mathrm{LS}\\\widehat{b}_\mathrm{LS}\end{bmatrix}\:=\:\left(\begin{bmatrix}\mathbf{X}^T\\\mathbf{1}^T\end{bmatrix}[\mathbf{X}&\mathbf{1}]\right)^{-1}\begin{bmatrix}\mathbf{X}^T\\\mathbf{1}^T\end{bmatrix}\mathbf{y}$$

## Quadratic regression in 1-dimension

![](./images/fkEL8f05ytqy5p0TYxnw61uy330eWREIR.png)

![](./images/f6lOCU9KDfBV3xLE829lO9hupzUs49YtM.png)

## Quadratic regression in 1-dimension

![](./images/f81XKXdqM5FgDWSMEXn32GiL9LsV7vhQw.png)

![](./images/fAOE5Q8QOQoyAtIqbah9wt7UB5aDKcww2.png)

· Linear model with parameter $(b,w_1)$
$$\bullet\:\hat{y_{i}}=b+\underline{w_{1}\:x_{i}}$$

· Quadratic model with parameter (b, w =
$$\cdot\hat{y}_i=b+w_1x_i+w_2x_i^2$$

### Quadratic regression in 1-dimension

![](./images/fpVGRS25sI9Vr2PYnCpWyYbOM8NF1aZYd.png)

![](./images/fz3goAgewPuaNkvp5kusVutGlOayPysom.png)

· Linear model with parameter $(b,w_1)$

![](./images/fI9iHNwAXM7bc54ihIlx01MxDwgQRF7Vq.png)

[]

### Quadratic regression in 1-dimension.

![](./images/fEaokcklG223kKBHKfcPo6BrK7M8FZ0MP.png)

![](./images/fAdN9Dhwfw5EzYlIgDDBg1vuDyGuEr4ED.png)

· Linear model with parameter $(b,w_1)$
$$\begin{array}{l}{{\textbf{lean inouel witil p.}}}\\{{\textbf{o }\hat{y_{i}}=b+\underline{{w_{1}\:x_{i}}}}}\end{array}$$

![](./images/fTVEyc9m5gDogYHtfn0xRec7CY1uSbwOR.png)

[

![](./images/fpE7XYiu1ywFWRuDt9zpzUSn2l9RXGfWn.png)

# Quadratic regression in 1-dimension
![](./images/fsBy6gT3Gqva3anrWslsy1BUWCUlBk6MD.png)

General p-features with parameter w =

· $\hat{y}_{i}=\langle w,h(x_{i})\rangle$ where $h:\mathbb{R}\to\mathbb{R}^p$

Note: h can be arbitrary non-linear functions!

$$h(x)=\begin{bmatrix}\log(x),x^2,\sin(x),\sqrt{x}\end{bmatrix}^\top $$

## Quadratic regression in 1-dimension

![](./images/f570i1N2aSouEOiXxMDOatmPGdI6HWiG8.png)

![](./images/fcMifsYyGPnt33uUM1FkcPVhkOPG5Xh2x.png)

General p-features with parameter w =

? $\hat{y}_{i}=\langle w,h(x_{i})\rangle$ where $h:\mathbb{R}\to\mathbb{R}^{P}$

How do we learn w?

## Quadratic regression in 1-dimension

![](./images/fHZyeg8KIcnenkXAWon8G9r2gLn8vo9cf.png)

![](./images/fBDuSYTzggyFN0Zio52xX8QMLhlA1LaLB.png)

General p-features with parameter w =

? $\hat{y}_{i}=\langle w,h(x_{i})\rangle$ where $h:\mathbb{R}\to\mathbb{R}^{P}$

How do we learn w?

![](./images/fNaN1S2GUDKDtHtNrCzgo3frxFmWQYC3I.png)

![](./images/frW1X4b97Em4y0fAxogkZ5Opg30wlTUOl.png)

For a new test point x, predict $\widehat{y}=\langle\widehat{w},h(x)\rangle$

# Which p should we choose?

· First instance of class of models with different representation power = model complexity

![](./images/flsCdEbctgG9xm5fHDe0LBwFcgMyGcW2D.png)
· How do we determine which is better model?

![](./images/fxpQniaGTy4HIuuMaAfe3xLoUHHbDHwBG.png)

# Generalization

· we say a predictor generalizes if it performs as well on unseen data as on training data (we will formalize the next lecture)

· the data used to train a predictor is training data or in-sample data

· we want the predictor to work on out-of-sample data

· we say a predictor fails to generalize if it performs well on in- sample data but does not perform well on out-of-sample data

# Generalization

· we say a predictor generalizes if it performs as well on unseen data as on training data (we will formalize the next lecture)

· the data used to train a predictor is training data or in-sample data

· we want the predictor to work on out-of-sample data

· we say a predictor fails to generalize if it performs well on in- sample data but does not perform well on out-of-sample data

![](./images/fgSUMw9k40r2BzEQ806txZKPDQpSvAGTZ.png)

train a cubic predictor on 32(in-sample)white circles: Mean Squared Error (MSE) 174

predict label y for 30(out-of-sample)blue circles: MSE 192

 conclude this predictor/model generalizes, as in-sample MSE~out-of-sample MSE

# Split the data into training and testing

a way to mimic how the predictor performs on unseen data

given a single dataset $S=\{(x_{i},y_{i})\}_{i=1}^{n}$

we split the dataset into two: training set and test set (e.g., 90/10)

training set used to train the model

$$\bullet\quad\mathrm{minimize}\:\mathscr{L}_{\mathrm{train}}(w)=\frac{1}{|S_{\mathrm{train}}|}\sum_{i\in S_{\mathrm{train}}}(y_{i}-x_{i}^{T}w)^{2}$$

test set used to evaluate the model
$$\mathcal{L}_{\mathrm{test}}(w)=\frac{1}{|S_{\mathrm{test}}|}\sum_{i\in S_{\mathrm{test}}}(y_{i}-x_{i}^{T}w)^{2}$$

this assumes that test set is similar to unseen data

test set should never be used in training or picking unknowns

# Train/test error vs. complexity

![](./images/fUntBspfcROnQZ1WEZpCsu7V8imkbUq6C.png)

·Degree $p=5$ , since it achieves minimum test error · Train error monotonically decreases with model complexity · Test error has a U shape

![](./images/fwKpVDyGlaGPsiw3EwADuKCdz5b2PmBAF.png)

Overfitting

![](./images/fdrKkHNq17awHu91mOddCRHHHCY1822Tu.png)

### 17 Cross-Validation

Slides adapted from Uw CsE 446

## How... How... How???????.

> How do we pick the number of basis functions...

> We could use the test data, but...

# (LOO) Leave-one-out cross validation

>Consider a validation set with 1 example:

D - training data Dlj - training data with j th data point (x; ,y) moved to validation set > Learn prediction function $f_{D\backslash j}$ with Dlj dataset > Estimate true error as squared error on predicting yj: Unbiased estimate of errortrue(fDy)!

# (LOO) Leave-one-out cross validation

> Consider a validation set with 1 example:

D - training data DIj - training data with j th data point (x; ,y;) moved to validation set

> Learn prediction functione $f_{Dij}$ with Dj dataset

Estimate true error as squared error on predicting yj:

Unbiased estimate of erro $r_{\mathrm{true}}(f_{D\mathrm{lj}})!$

>

> LOO cross validation: Average over all data points j:

For each data point you leave out, learn a new classifier $f_{D\mathrm{Nj}}$ Estimate error as:

$$\text{error}_{LOO}=\frac{1}{n}\sum_{j=1}^n(y_j-f_{\mathcal{D}\setminus j}(x_j))^2$$

# LoO cross validation is (almost) unbiased estimate!

> When computing LoocV error, we only use N-1 data points So it's not estimate of true error of learning with N data points Usually pessimistic, though - learning with less data typically gives worse answer

> LOO is almost unbiased! Use LOO error for model selection!!! E.g., picking degree

## Computational cost of Loo

> Suppose you have 100,000 data points

> You implemented a great version of your learning algorithm

Learns in only 1 second > Computing LoO will take about 1 day!!!

# Use k-fold cross validation

Randomly divide training data into k equal parts $\mathcal{D}_1,\ldots,\mathcal{D}_k$

Foreach i

Learn classifier $f_{D|Di}$ using data point not in $D_i$ Estimate error of $f_{D|Di}$ on validation set $D_i.$

$$\mathrm{error}_{\mathcal{D}_i}=\frac{1}{|\mathcal{D}_i|}\sum_{(x_j,y_j)\in\mathcal{D}_i}(y_j-f_{\mathcal{D}\setminus\mathcal{D}_i}(x_j))^2$$

<table>
	<tbody>
		<tr>
			<th>1</th>
			<th>2</th>
			<th>3</th>
			<th>4</th>
			<th>5</th>
		</tr>
		<tr>
			<td>Train</td>
			<td>Train</td>
			<td>Validation</td>
			<td>Train</td>
			<td>Train</td>
		</tr>
	</tbody>
</table>

# Use k-fold cross validation

> Randomly divide training data into k equal parts — $\mathcal{D}_1,\ldots,\mathcal{D}_k$

<table>
	<tbody>
		<tr>
			<th>1</th>
			<th>2</th>
			<th>3</th>
			<th>4</th>
			<th>5</th>
		</tr>
		<tr>
			<td>Train</td>
			<td>Train</td>
			<td>Validation</td>
			<td>Train</td>
			<td>Train</td>
		</tr>
	</tbody>
</table>

 For each i

Learn classifier $f_{D|Di}$ using data point not in $D_i$ Estimate error of $f_{D|Di}$ on validation set $D_i.$

$$\mathrm{error}_{\mathcal{D}_i}=\frac{1}{|\mathcal{D}_i|}\sum_{(x_j,y_j)\in\mathcal{D}_i}(y_j-f_{\mathcal{D}\setminus\mathcal{D}_i}(x_j))^2$$

k-fold cross validation error is average over data splits:

$$error_{k-fold}=\frac1k\sum_{i=1}^kerror_{\mathcal{D}_i}$$

k-fold cross validation properties:

Much faster to compute than LOO - More (pessimistically) biased - using much less data, only $n(k-1)/k$ - Usually, $k=10$

# Recap

> Given a dataset, begin by splitting into

![](./images/f9lifIhvKY5DlF7gOKCxvfoWr09hNh8r4.png)

> Model selection: Use k-fold cross-validation on TRAlN to train predictor and choose magic parameters such as degree

![](./images/f6MnNypgX6zvsK7gv0uiD7Fal6xviG96D.png)

> Model assessment: Use TEsT to assess the accuracy of the model you output

■ Never ever ever ever ever train or choose parameters based on the test data

# Example

> Given 10,000-dimensional data and n examples, we pick a subset of 50 dimensions that have the highest correlation with labels in the entire dataset:

$$\frac{|\sum_{i=1}^nx_{i,j}y_i|}{\sqrt{\sum_{i=1}^nx_{i,j}^2}}$$

50 indices j that have largest

>After picking our 50 features, we then break data into train and test dataset.

>We train linear regression on these selected features on the training set. We compute the test error and report it >What's wrong with this procedure?

# Recap

> Learning is...

Collect some data

> E.g., housing info and sale price

Randomly split dataset into TRAIN, $VAL$, and TEST

> E.g., $80\%$ $10\%$, and $10\%$ , respectively

Choose a hypothesis class or model

> E.g., linear with non-linear transformations

Choose a loss function

> E.g., least squares on TRAIN

Choose an optimization procedure.

> E.g., set derivative to zero to obtain estimator, crossvalidation on vAL to pick num. features

> Justifying the accuracy of the estimate

> E.g., report TEST error

$$\text{Bias-Variance}\\\text{Tradeoff}$$

# Bias-variance tradeoff: intuition

Model too simple: does not fit the data well - A biased solution

![](./images/fA0AL9U66a6RrHdw8ByUZPiM2xIEUdCZu.png)

Model too complex: small changes to the data, solution changes a lot - A high-variance solution

# Bias-variance tradeoff

 consider the task of learning a regression model $f(x|D)$ ,where

$$D=\{(x_{1},y_{1}),...,(x_{n},y_{n})\}$$

· Recall what is $f(x|D)$ when...

Linear regression ·Linear regression with nonlinear basis

· We would like to reason about the expected loss (Prediction Risk) over:

· Training data $D$ · Test data $(x_*,y_*)$

Variance
$$_{y_*}\Big[(y_*-f(x_*|D))^2\Big]=\text{Noise }+\text{ Bias}^2+$$

# Definitions

·Assume that $y_{*}=h(x_{*})+\epsilon_{*}$ $\epsilon_*$ is noise independent of $\chi_*$

![](./images/fOTwzgEk4PEfX1sbgBGnx5AGOQzdvQgs1.png)

$$\mathbf{E}_{D,\:y_*}\big[(y_*-f(x_*|D))^2\big]=$$

$$\begin{aligned}
&\nu,\:y_{*\lfloor}\backslash\nu^{*}\quad J(\:r|\:)\:]& LAPC  \\
&\mathbf{E}_{\epsilon_*}\left[(y_*-h(x_*))^2\right] \\
&+(h(x_*)-\mathbf{E}_D\left[f(x_*|D)\right])^2 \\
&+\mathbf{E}_D\left[(f(x_*|D)-\mathbf{E}_D\left[f(x_*|D)\right])^2\right]
\end{aligned}$$

Expected Loss

Noise

(Bias)2

Variance

## Derivation

$$\mathbf{E}_{D,\:y_*}\big[(y_*-f(x_*|D))^2\big]$$

# Derivation

$$\begin{aligned}
&_{,\:y_{*}}\big[(y_{*}-f(x_{*}|D))^{2}\big]\text{Ехресted Loss} \\
&\mathbf{E}_{D,(y_*,x_*)}\left[(y_*-h(x_*)+h(x_*)-f(x_*|D\right. \\
&\mathbf{E}_{\epsilon_{*}}\left[(y_{*}-h(x_{*}))^{2}\right]+\mathbf{E}_{D}\left[(h(x_{*})-f(x_{*})\right]
\end{aligned}$$

Model Estimation Error (we want to minimize this)

Noise Term (out of our control) ?

Expand

# Derivation

· Expanding on the model estimation error:

$$\mathbf{E}_D\left[(h(x_*)-f(x_*|D))^2\right]$$

Completing the squares with E ${:}[f(x_{*}|D)]=\bar{f}_{*}$ (omit $\chi_*$ for simplicity)

## Derivation

$$\begin{aligned}\mathbf{E}_{D}\left[(h(x_{*})-f(x_{*}|D))^{2}\right]\\&=(h(x_*)-\mathbf{E}\left[f(x_*|D)\right])^2+\mathbf{E}\left[(f(x_*|D)-\mathbf{E}\left[f(x_*|\right]\right]\\&\text{(Bias)2}\end{aligned}$$

# Summary

· Tradeoff between bias and variance:

· - Simple Models: High Bias, Low Variance

· - Complex Models: Low Bias, High Variance

![](./images/fU4AtGghSSBytGegaBLIdfwix8gUpIrGk.png)

![](./images/fMzhHgUVBTVb6KWVzBIukggVU65Fcdby0.png)

# Machine Learning: Linear Regression with Regularization.

Lecture Notes on Feb 3,5.

Modified by Zhou (Spring 2025)

## Regularization in Linear Regression: Intuition

Recall Least Squares:
$$\begin{aligned}
\widehat{w}_{LS}& =\arg\min_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}  \\
&=\arg\min_{w}(\mathbf{y}-\mathbf{X}w)^{T}(\mathbf{y}-\mathbf{X}w)
\end{aligned}$$

$$=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$$

When (X I X)-1 exists..

# Regularization in Linear Regression:.

# Intuition

$$-X\in\mathbb{R}^{n\times d}$$

·When $d$ is large, $X^{\top}X$ is not invertible!

![](./images/fH1C3Zi0nZQ8sYmY0ehaoQwMyhR1bKcXd.png)

Example: regression with genomic data. $n$ is the number of patients (usually less than 1K) $d$ is the number of genes (usually more than 100K)

# Solutions:

## · Ridge regression

· Lasso regression

· Summary (will revisit later)

<table>
	<tbody>
		<tr>
			<th>Property</th>
			<th>Lasso Regression</th>
			<th>Ridge Regression</th>
		</tr>
		<tr>
			<td>Feature selection?</td>
			<td>Yes (some coefficients exactly 0)</td>
			<td>No (all coefficients are small but nonzero)</td>
		</tr>
		<tr>
			<td>Handling of correlated features</td>
			<td>Selects one feature, others set to 0</td>
			<td>Keeps all, shrinks them together</td>
		</tr>
		<tr>
			<td>Stability</td>
			<td>Less stable (different data - different selected feature)</td>
			<td>More stable (coefficients smoothly adjusted)</td>
		</tr>
		<tr>
			<td>Interpretability</td>
			<td>Easier (fewer features remain)</td>
			<td>Harder (all features contribute)</td>
		</tr>
	</tbody>
</table>

Regression with

regularization

Slides adapted from UW CSE 446

$$\text{Ridge Regression}$$

Old Least squares objective:

$$:\\\widehat{w}_{LS}=\arg\min_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}$$

![](./images/fxglAGq1dMOMnRkpPY5g8zzDR4rRrnfx3.png)

Ridge Regression
$$\stackrel{\text{objective:}}{w}_{ridge}=\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2+\lambda||w||_2^2$$

![](./images/fk3YqefAzqHN8c1xyiaIv5NiD4RFXb6ut.png)

$$\text{Shrinkage Propertie}$$

$$\begin{gathered}
\widehat{w}_{ridge} =\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2+\lambda||w|| \\
=(\mathbf{X}^T\mathbf{X}+\lambda I)^{-1}\mathbf{X}^T\mathbf{y} 
\end{gathered}$$

# Bias-Variance Properties

$$\begin{aligned}&\widehat{w}_{ridge}=(\mathbf{X}^{T}\mathbf{X}+\lambda I)^{-1}\mathbf{X}^{T}\mathbf{y}\\&^T\mathbf{X}=nI_{and}\quad\mathbf{y}=\mathbf{X}w+\boldsymbol{\epsilon}\quad\boldsymbol{\epsilon}\sim\mathcal{N}(0\end{aligned}$$

Assume:

If $x\in\mathbb{R}^{d}$ and $Y\sim\mathcal{N}(x^{T}w,\sigma^{2})$ , what is $\mathbb{E}_{Y|x,\mathrm{tan}}[(Y-x^{T}\widehat{w}_{ridge})^{2}|X=x]?$

$$y_*=h(x_*)+\epsilon_*$$

Recall bias-variance tradeoff....

$$\mathbf{E}_{D,\:y_*}\big[(y_*-f(x_*|D))^2\big]=$$
Expected Loss Noise (Bias)2
$$\begin{aligned}
&\text{一, J*L(O J}& \text{T}  \\
&\mathbf{E}_{\epsilon_*}\left[(y_*-h(x_*))^2\right] \\
&+(h(x_*)-\mathbf{E}_D[f(x_*|D)])^2 \\
&+\mathbf{E}_D\left[(f(x_*|D)-\mathbf{E}_D\left[f(x_*|D)\right])^2\right]
\end{aligned}$$
Variance

# Bias-Variance Properties

$$\begin{aligned}&\widehat{w}_{ridge}=(\mathbf{X}^{T}\mathbf{X}+\lambda I)^{-1}\mathbf{X}^{T}\mathbf{y}\\&^T\mathbf{X}=nI_{and}\quad\mathbf{y}=\mathbf{X}w+\boldsymbol{\epsilon}\quad\boldsymbol{\epsilon}\sim\mathcal{N}(0\end{aligned}$$

Assume:

If $x\in\mathbb{R}^{d}$ and $Y\sim\mathcal{N}(x^{T}w,\sigma^{2})$ , what is $\mathbb{E}_{Y|x,\mathrm{tan}}[(Y-x^T\widehat{w}_{ridge})^2|X=x]?$

$$\begin{aligned}\widehat{w}_{ridge}&=(\mathbf{X}^T\mathbf{X}+\lambda I)^{-1}\mathbf{X}^T(\mathbf{X}w+\boldsymbol{\epsilon})\\&=\frac n{n+\lambda}w+\frac1{n+\lambda}\mathbf{X}^T\boldsymbol{\epsilon}\end{aligned}$$



$$\begin{aligned}&\text{s-Variance Properties}\\&\widehat{w}_{ridge}=(\mathbf{X}^T\mathbf{X}+\lambda I)^{-1}\mathbf{X}^T\mathbf{y}\\&\mathbf{X}^T\mathbf{X}=nI\:and\quad\mathbf{y}=\mathbf{X}w+\epsilon\quad\boldsymbol{\epsilon}\sim\mathcal{N}(0,\sigma^2I\end{aligned}$$

Assume:

If $x\in\mathbb{R}^{d}$ and $Y\sim\mathcal{N}(x^{T}w,\sigma^{2})$ , what is $\mathbb{E}_{Y|x,\mathrm{tan}}[(Y-x^{T}\widehat{w}_{ridge})^{2}|X=x]?$

![](./images/fta6UCAluBihBMrmYMuEWNPPE0E64neG3.png)

# Ridge Regression: Effect of Regularization

![](./images/fERIccZwZNIOPDADIUHf5LeGTo9DIuGgI.png)

Solution is indexed by the regularization parameter 入

Larger 入

 Smaller 入

![](./images/fyWoUTISdwqfz0OgKgXlwAlbmW7nxeIPT.png)

As入→ 0,

As 入 →∞,

# Ridge Regression: Effect of Regularization

![](./images/feTilCKS2Wgk3Q2iCNqoLTN0LYfvD3YZZ.png)

![](./images/fickAkbtKKAVueHsV0Ih41tDpOygaEPgY.png)
·this gain in test MSE comes from

shrinking w's to get a less sensitive predictor (which in turn reduces the variance)

# Bayesian!

·Recall MLE: Choose the parameters that maximize the likelihood of the datas.

·Given $x_1,\ldots,x_n$ and a probability model $p(\cdot|\theta)..$

$$\bullet\:\theta^{MLE}=\arg\max_{\theta}p(x_1,...,x_n|\theta)=\arg\max_{\theta}\prod_{i=1}p(x_i|\theta)$$

· Another point of view: Maximum a posteriori (MAP) Estimation
$$\bullet\:\theta^{MAP}=\arg\max_{\theta}p(\theta|x_{1},...,x_{n})$$

![](./images/fVQOXCvcrswlRHYmQIwo0gfKqfCVSUuQC.png)

Another viewpoint of ridge regression:

### Bayesian!

$$p(\theta|x_1,...,x_n)$$

Bayesian!

$$\theta^{MAP}=\arg\max_\theta p(\theta|x_1,...,x_n)=\arg\max_\theta\left[\prod_{i=1}^np(x_i|\theta)\right]p(\theta)$$

$$\theta^{MLE}=\arg\max_\theta p(x_1,...,x_n|\theta)=\arg\max_\theta\prod_{i=1}p(x_i|\theta)$$

$p(\theta)$ : prior distribution of $\theta$

Represents the 'prior knowledge' of θ without observing any data!

Bayesian!

Let us come back to ridge regression...

 Ridge Regression
$$\begin{aligned}&\text{objective:}\\&\hat{w}_{ridge}=\arg\operatorname*{min}_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}+\lambda||w||_{2}^{2}\end{aligned}$$

Claim: it is associated with a MAP solution!

$\begin{aligned}&\text{1}\\&\text{1}\\&\text{1}\\&\text{1}\\&\text{1}\\&\text{1}\end{aligned}$

# Bayesian!

We assume a linear model.

$$y=X\beta+\varepsilon,\quad\mathrm{where}\:\varepsilon\sim\mathcal{N}(0,I).$$

(yβ
$$=\frac{1}{(2\pi)^{n/2}}\exp\left(-\frac{1}{2}\|y-X\beta\|^{2}\right)\quad p(\beta)=\frac{1}{(2\pi)^{d/2}\lambda^{d/2}}\exp\left(-\frac{\lambda}{2}\|\beta\|^{2}\right)$$

$$p(\beta|y)\propto\exp\left(-\frac12\|y-X\beta\|^2\right)\cdot\exp\left(-\frac\lambda2\|\beta\|^2\right)$$

$$\hat{\beta}_{\mathrm{MAP}}=\arg\min_\beta\left(\|y-X\beta\|^2+\lambda\|\beta\|^2\right)$$

# What you need to know...

Regularization

Penalizes complex models towards preferred, simpler models

> Ridge regression

L2 penalized least-squares regression Regularization parameter trades off model complexity with training error Never regularize the offset!

### 21 LASSO

$$\widehat{w}_{LS}=\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2$$

Vector w is sparse, if many entries are zero

$$\widehat{w}_{LS}=\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2$$

Vector w is sparse, if many entries are zero

Efficiency: If $\mathsf{size}(\mathbf{w})=100$ Billion, each prediction is expensive: ·If w is sparse, prediction computation only depends on number of non-zeros

![](./images/f5itrULnsWABni92YSTunnEfYUnz8aCnf.png)

$$\widehat{w}_{LS}=\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2$$

# ■Vector w is sparse, if many entries are zero

Interpretability: What are the relevant dimension to make a prediction?

![](./images/f8018Da1mU81D6Ncxg4twLLMz0oYXvG1x.png)

Lot size Single Family Year built Last sold price Last sale price/sqft Finished sqft Unfinished sqft Finished basement sqft #floors Flooring types Parking type Parking amount Cooling Heating Exterior materials Roof type Structure style

How do we find "best" subset among all possible?

Dishwasher Garbage disposal Microwave Range/ Oven Refrigerator Washer Dryer Laundry location. Heating type Jetted Tub Deck Fenced Yard Lawn Garden Sprinkler System

# Finding best subset: Exhaustive

> Try all subsets of size 1, 2, 3, ... and one that minimizes yalidation error > Problem?

# Finding best subset: Greedy

### Forward stepwise:

Starting from simple model and iteratively add features most useful to fit

### Forward Greedy

1: $T\leftarrow\varnothing$
$$\begin{aligned}
&2\colon\mathsf{For}\:j=1,\ldots,k\:\mathsf{do} \\
&3\colon\quad j^{*}\leftarrow\arg\operatorname*{min}_{\ell}\operatorname*{min}_{w}\:\sum_{i=1}^{n}\Big(\:y_{i}-\sum_{j\in T\cup\{\ell\}}w[j]\times x_{i}[j]\:\Big)^{2} \\
&4\colon T\leftarrow T\cup\{j^{*}\}
\end{aligned}$$

### Backward stepwise:

Start withfull model and iterativelyremove featuresleast useful to fit

## Combining forward and backward steps:

In forward algorithm, insert steps to remove features no longer as important

Lots of other variants, too.

# Finding best subset: Regularize

Ridge regression makes coefficients small

$$\widehat{w}_{ridge}=\arg\min_w\sum_{i=1}^n\left(y_i-x_i^Tw\right)^2+\lambda||w||_2^2$$

![](./images/ftOzuDEadhypLOzk1efraoGVTIcixBzPG.png)

### Recall Ridge Regression

![](./images/fBI4VxLUd1geLm886wQ9W3uc2gnemepPE.png)

$$\|w\|_p=\left(\sum_{i=1}^d|w|^p\right)^{1/p}$$

## Recall Ridge Regression

Ridge Regression
$$\begin{aligned}&\text{on objective:}\\&\widehat{w}_{ridge}=\arg\min_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}+\lambda||w||_{2}^{2}\end{aligned}$$

![](./images/f6xkKm9E0G4MBPxxdpLYXK5MkpbepnSQM.png)

![](./images/f6aw5ORzGqxBRVxZEOxHR8vP4czT5BvWV.png)

# Example: house price with 16 features

![](./images/fyFRRA1NdcgntkiKr96dwr55csYb9g1uS.png)

·Regularization path for Lasso shows that weights drop to exactly zero as increases

![](./images/fdgWBC8lwGdGlwLuu6tQNXFlT9LO8E9Ga.png)
Ridge regression

![](./images/fMpX5nUGkuBBTu1LpkKgPlZhwa6GzNUKc.png)
Lasso regressionsparse

Lasso regression naturally gives sparse features

feature selection with Lasso regression

1. Model selection: choose based on cross validation error

2. Feature selection: keep only those features with non-zero (or not-too-small) parameters in w at optimal w

3. (optional) retrain with the sparse model and $\lambda=0$

## Why LASSO finds sparse solution?

$$\begin{gathered}
\text{ularized o} \\
\widehat{w}_{r}=\arg\min_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}+\lambda r(w) \\
\mathrm{Ridge}:r(w)=||w||_{2}^{2} \\
\mathrm{Lasso}:r(w)=||w||_{1} 
\end{gathered}$$

# Why LASSO finds sparse solution?

$$\begin{gathered}
\text{ularizedo} \\
\widehat{w}_{r}=\arg\min_{w}\sum_{i=1}^{n}\left(y_{i}-x_{i}^{T}w\right)^{2}+\lambda r(w) \\
\mathrm{Ridge}:r(w)=||w||_{2}^{2} \\
\mathrm{Lasso}:r(w)=||w||_{1} 
\end{gathered}$$

· For any $\lambda^*\geq0$ for which $\hat{w}_r$ achieves the minimum, there exists a $\mu^*\geq0$ such that the solution of the constrained optimization, $\widehat{w}_{c^{\prime}}$ is the same as the solution of the regularized optimization , $\widehat{w}_{r^{\prime}}$ where

≤μ*
$$\widehat{w}_{C}=\arg\min_{w}\sum_{i=1}^{n}\:(y_{i}-x_{i}^{T}w)^{2}\quad\text{subject to}\:r(v$$

· so there are pairs of $(\lambda,\mu)$ whose optimal solution $\widehat{w}_r$ are the same for the regularizes optimization and constrained optimization

# Why LASSO finds sparse solution?

 Consider a 2-dimension problem, $w=(w_{1},w_{2})$

$$\text{minimize}_w\:\sum_{i=1}^n\:(w^Tx_i-y_i)^2$$

subject to $\| w\| _1$ $\leq$ $\mu$

the level set of a function $\mathscr{L}(w_1,w_2)$ is defined as the set of points $(w_1,w_2)$ that have the same function value the level set of a quadratic function is an oval the center of the oval is the least squares solution $\hat{w}_{\mu=\infty}=\hat{w}_{\mathrm{LS}}$

1-D example with quadratic loss

![](./images/fgIglGG4Uff3GmctoMOORLRZqNghswYa4.png)

![](./images/fDnLhWgaHMyAUgkvyDPWT2IWGNOqGenye.png)
1 is [a,b]

# Why LASSO finds sparse solution?

 Consider a 2-dimension problem, $w=(w_{1},w_{2})$

$$\text{minimize}_w\:\sum_{i=1}^n\:(w^Tx_i-y_i)^2$$

subject to $\| w\| _1$ $\leq$ $\mu$

·as we decrease $\mu$ from infinity, the feasible set becomes smaller

the shape of the feasible set is what is known as $L_1$ ball, which is a high dimensional diamond

In 2-dimensions, it is a diamond
$$\left\{\left(w_{1},w_{2}\right)\left|\left|w_{1}\right|+\left|w_{2}\right|\leq\mu\right\}\right.$$

When $\mu$ is large enough such that $\|\hat{w}_{\mu=\infty}\|_{1}<\mu$ then the optimal solution does not change as the feasible set includes the un-regularized optimal solution

W1

feasible set: $\{w\in\mathbb{R}^2|\left\|w\right\|_1\leq\mu\}$

# Why LASSO finds sparse solution?

 Consider a 2-dimension problem, $w=(w_{1},w_{2})$

$$\text{minimize}_w\:\sum_{i=1}^n\:(w^Tx_i-y_i)^2$$

subject to $\| w\| _1$ $\leq$ $\mu$

As $\mu$ decreases (which is equivalent to increasing regularization A) the feasible set (blue diamond) shrinks The optimal solution of the above optimization is ?

![](./images/fZXTghrhL0gyqT3Dq6zEibfqVLG83uoO5.png)

feasible set: $\{w\in\mathbb{R}^2|\left\|w\right\|_1\leq\mu\}$

# Why LASSO finds sparse solution?

 Consider a 2-dimension problem, $w=(w_{1},w_{2})$

$$\text{minimize}_w\:\sum_{i=1}^n\:(w^Tx_i-y_i)^2$$

subject to $\| w\| _1$ $\leq$ $\mu$

For small enough $\mu$ , the optimal solution becomes sparse

This is because the $L_{\mathrm{l}}$ -ball is "pointy",i.e., has sharp edges aligned with the axes

![](./images/fl55WgZ0yeqY79kAFpc4khlOgs6f7iViu.png)

feasible set: $\{w\in\mathbb{R}^2|\left\|w\right\|_1\leq\mu\}$

# Why LASSO finds sparse solution?

Lasso regression finds sparse solutions, as $L_1$ -ball is “"pointy" Ridge regression finds dense solutions, as $L_{2}$ -ball is “smooth"

![](./images/fU8YFgCZ7XYgAOvq2M0vXNoZtPaxY3tAo.png)

![](./images/f724HYPqaimG5dkmcNUXeZ7H8G8352zN6.png)

subject to $\|w\|_1\leq\mu$

subject to $\|w\|_2^2\leq\mu$

# Machine Learning: Gradient Descent and Stochastic Gradient Descent

Lecture Notes on Feb 10, 12

Modified byZhou (Spring 2025)

Gradient Descent

# Running example: linear regression

Given data:
$$\{(x_i,y_i)\}_{i=1}^n\quad x_i\in\mathbb{R}^d\quad y_i\in\mathbb{R}$$

Learning model parameters:

![](./images/fi065DWaMiywvc2rzivMO0ink8ymRp1XQ.png)

![](./images/fY44W18ZeCdgYTZtn5qr1uw5XeOgNE7gf.png)

· Although we know the optimal solution in a closed form, we will use this as a running example to understand GD

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation: For $w$ very close to $W_0$ wehave
$$f(w_0)+\left.(w-w_0)\frac{df(w)}{dw}\right|_{w=w_0}$$
is very close to $f(w)$

![](./images/fxpNgyMF6u9eVuufkreb1HgifSWGooDIf.png)

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation:. For w very close to. $w_0$ wehave
$$f(w_0)+(w-w_0)\frac{df(w)}{dw}|_{w=w_0}$$
is very close to $f(w)$

![](./images/fgod39CMa7cWcbFIKUvVgrsKdKvMHKHBG.png)

Thus, for very small $\eta>0$ ifW d th 2 f(wg) n(dr(w)|) is very close to $f(w_{1})<f(w_{0})$

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation:. For $w$ very close to $w_0$ wehave
$$f(w_0)+\left.(w-w_0)\frac{df(w)}{dw}\right|_{w=w_0}$$
is very close to $f(w)$

![](./images/fhkR1Ys2lK2BFQPUca8UKg4SUhhFO5tm8.png)

Thus, for very small $\eta>0.$ ifw od the 2 f(w)- n(d/w)|w) is very close to $f(w_1)<f(w_0)$

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation:.

Forvery close to $w_0$ wehave $f( w_0) +$ $( w- w_0) ^{\frac {df( w) }{dw}}$ Iy is very close to $f(w)$

![](./images/f2XiI4PxQDx2OLhvbTSADibiwe2clghxL.png)

Thus, for very small $\eta>0.$ ifw =wo"www then 2 f(w)- n(d/m)|) is very close to $f(w_1)<f(w_0)$

Gradient descent For $k=0,1,2,3,...$ $w_{k+1}=\left.w_{k}-\eta\frac{df(w)}{dw}\right|_{w=w_{k}}$

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation:.

Forvery close to $w_0$ wehave $f( w_0) +$ $( w- w_0) ^{\frac {df( w) }{dw}}$ Ivis very close to $f(w)$

![](./images/fk5bziU7TnTiYKO7ryRGGhPI0aAO3LUOG.png)

Thus, for very small $\eta>0.$ ifW adw the 2 f(w)- n(d/m)|) is very close to $f(w_1)<f(w_0)$

![](./images/fzKmUXvfNrG3tpRDBrv4Wm08ykrs7WrM4.png)

# 1-dimensional gradient descent

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation:.

Forvery close to $w_0$ wehave $f( w_0) +$ $( w- w_0) ^{\frac {df( w) }{dw}}$ is very close to $f(w)$

![](./images/f07IUxiTgHgqZtOEy2xNVLm1GvR8pkXCO.png)

Thus, for very small $\eta>0.$ ifw =wo-Iww then 2 f(w)- n(d/m)|) is very close to $f(w_1)<f(w_0)$

![](./images/f29VgmhoD6m8FhuVHtu9WrenhegAfW2OE.png)

![](./images/fH0mllDEQMaOhT9dNGLAGkE1Nz2xmaGuO.png)

# Running example: linear regression

Given data:
$$\{(x_i,y_i)\}_{i=1}^n\quad x_i\in\mathbb{R}^d\quad y_i\in\mathbb{R}$$

Learning model parameters:

WLs = arg min Il - Xwll2

![](./images/fqM4ULEp9g6FwGSLdGVUXcHt6lGQhNH9R.png)

Gradient descent:

 Initialize: $w_0=0$ ·For $\mathbf{t=0,1,2,...}$
$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fcmwdsl9W2TMSbz7l0hIwuvk27Xys4oPS.png)

Evolution of the predictor

· Which direction will the GD move?

$$\bullet w_0=\{900,-0.1\}$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/frnULa3TLSbGgGKiGaxp7wsGYPkVOlVER.png)

GD dynamics in the Parameter space

![](./images/fLSC5inux0YYEq9g7dZfs9OGT2GnTU02R.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_{t}-\eta\cdot\nabla_{w}f(w_{t})$$

![](./images/foNlmXSMecAwYuA3ccGWdAAXIPWEAa1wk.png)

GD dynamics in the Parameter space

![](./images/fGLbga0Oul64qVUv9qY5qaAmfQ2cmBXqX.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_{t}-\eta\cdot\nabla_{w}f(w_{t})$$

![](./images/f74G4eicX8R3gMTEgBsIkzNruknk5dGG8.png)

GD dynamics in the Parameter space

![](./images/fvr0SeuqlzLFdYu3VPQaGLpcDRv3ZeeX6.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fy2BL04PcwD45OPgGwYnAqwudwQ6iHHa7.png)

GD dynamics in the Parameter space

![](./images/fpdY58NU3CW7hz5kKkLfE02DRvBt6982n.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fs5uE3vhUWk79Gm5eTCRgzAm41DsdPWsn.png)

GD dynamics in the Parameter space

![](./images/fYqOy3eBIXPAY6PU9LXRzxUnp8CsGP0G7.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fWpf1kevy6gmP9gqehoQPrtI0haaWAYdu.png)

GD dynamics in the Parameter space

![](./images/ffFObpsFc6Cd6Po5KrTclcL1wa2ApHpqL.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fttWK3ag49rLtkVHVwubnh8y1QMpOmwmE.png)

GD dynamics in the Parameter space

![](./images/f6LkEKVUBHqSteFgOu5HiEyYwGCDAMe6e.png)

Evolution of the predictor

$$\bullet w_0=(900,-0.1)$$
# ·For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

![](./images/fgGsrc7KnG9YGEl3ddiQgk0U7f5fqIrKG.png)

GD dynamics in the Parameter space

![](./images/fzfKgL64TkzzKRZimg79tqDlMitKLvFX4.png)

$$\begin{aligned}&\bullet w_0=(900,-0.1)\\&\bullet\text{For t=0,1,2,...}\\&\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)\end{aligned}$$

![](./images/fH0hNdG2N6vUCEIyPprAqVVsvNr2LKXO9.png)

GD dynamics in the Parameter space

Evolution of the predictor

# Gradient descent for linear regression

· In this example of linear regression, we can derive exactly the gradient descent trajectory

· Initialize: $w_0=0$

·For $\mathbf{t=0,1,2,..}$
$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)\\\nabla f(w_t)\:=\:-\:2\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)$$

For linear regression, we have

![](./images/fDEow4qSYd5RkdPYI5s8f98gvOQnUkwBp.png)

# Gradient descent for linear regression

For linear regression, we have

· In this example of linear regression, we can derive exactly the gradient descent trajectory

 Initialize: $w_0=0$

![](./images/ftHxO1A3Glieo4FVaGzpTEkyTiDNS4xmP.png)

·For $\mathbf{t=0,1,2,...}$

$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

$$\begin{aligned}\nabla f(w_t)&=-2\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)\\w_{t+1}&=\quad w_t+\eta2\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)\quad=\quad(\mathbf{I}-2\eta\mathbf{X}^T\mathbf{X})w_t+\end{aligned}$$

+2nXTy

# Gradient descent for linear regression

For linear regression, we have

· In this example of linear regression, we can derive exactly the gradient descent trajectory

$$\begin{gathered}
·IIIILIaIILE.W_{0}-0 \\
\bullet\text{For t=0,1,2,...} \\
\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t) \\
\nabla f(w_t)\:=\:-\:2\mathbf{X}^T(\mathbf{y}-\:\mathbf{X}w_t) \\
\begin{array}{rcl}w_{t+1}&=&w_t+\eta2\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)&=&(\mathbf{I}-2\eta\mathbf{X}^T\mathbf{X})w_t+2\eta\mathbf{X}^T\mathbf{y}\end{array} 
\end{gathered}$$

![](./images/fWsCZGcgFPDB9fGLgWk5aOTiuvLoEqGYI.png)

Let the least-squares solution be $w^*=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$

$$\begin{aligned}
\nu_{t+1}-\:w^{*}& =(\mathbf{I}-2\eta\mathbf{X}^T\mathbf{X})w_t+2\eta\mathbf{X}^T\mathbf{y}-w^*  \\
&=(\mathbf{I}-2\eta\mathbf{X}^T\mathbf{X})(w_t-w^*)+2\eta\mathbf{X}^T\mathbf{y}-2\eta\mathbf{X}^T\mathbf{X} \\
&=(\mathbf{I}-2\eta\mathbf{X}^T\mathbf{X})(w_t-w^*)
\end{aligned}$$

# Gradient descent for linear regression

For linear regression, we have Initialize: $w_0=0$ ·For $\mathbf{t=0,1,2,..}$
$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

$$\begin{aligned}&\text{,...}\\&-\:w_{t}-\:\eta\cdot\nabla_{w}\:f(w_{t})&&\hat{w}_{\mathrm{LS}}\:=\:\arg\min_{w\in\mathbb{R}^{d}}\:\underbrace{\|\mathbf{y}-\mathbf{X}_{f(w)}}\end{aligned}$$

$$\begin{aligned}&(w_{t})\:=\:-\:2\mathbf{X}^{T}(\mathbf{y}-\mathbf{X}w_{t})\\&v_{t+1}\:=\:w_{t}\:+\:\eta2\mathbf{X}^{T}(\mathbf{y}-\mathbf{X}w_{t})\:=\:(\mathbf{I}-\:2\eta\mathbf{X}^{T}\mathbf{X})w_{t}+\:2\eta\mathbf{X}\end{aligned}$$

Let the least-squares solution be $w^*=(\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$

$$\begin{aligned}
w_{t+1}-\:w^{*}& =\:(\mathbf{I}-\:2\eta\mathbf{X}^{T}\mathbf{X})w_{t}+\:2\eta\mathbf{X}^{T}\mathbf{y}-\:w^{*}  \\
&=\:(\mathbf{I}-\:2\eta\mathbf{X}^{T}\mathbf{X})(w_{t}-w^{*})+\:2\eta\mathbf{X}^{T}\mathbf{y}-\:2\eta\mathbf{X}^{T} \\
&=\:(\mathbf{I}-2\eta\mathbf{X}^{T}\mathbf{X})(w_{t}-w^{*})
\end{aligned}$$

# How do you choose step size?

Let $w_0$ be an initial guess. How can we improve this solution?

Taylor series approximation: For very close to $w_0$ wehave $f( w_0) +$ $( w- w_0) ^{\frac {df( w) }{dw}}$ Iu is very close to $f(w)$

![](./images/f90fxnNevHMMWPeXdFFLigozrUFYt8bQq.png)

If $\eta$ too big, does not converge!

If $\eta$ too small, converges very, very slowly.

In practice: choose the largest value of $\eta$ that converges (guess and check)

Initialize: $w_0=0$ ●For t=0,1,2...
$$\bullet w_{t+1}\leftarrow w_t-\eta\cdot\nabla_wf(w_t)$$

For Ridge we have
$$\hat{w}_{\mathrm{Ridge}}\:=\:\arg\min_{w\in\mathbb{R}^{d}}\frac{1}{2}\|\mathbf{y}-\mathbf{X}w\|_{2}^{2}+\frac{\lambda}{2}\|w\|_{2}^{2}\\f(w)$$

$$\nabla f(w_t)\:=-\:\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)+\lambda w_t$$

$$w_{t+1}\:=\:(1-\lambda)w_t+\eta\mathbf{X}^T(\mathbf{y}-\mathbf{X}w_t)$$

· Initialize: $w_{0}=0$ ●For t=0,1,2,..

$$\bullet w_{t+1}\leftarrow w_{t}-\eta\cdot\nabla_{w}f(w_{t})$$

For Lasso we have

$$\hat{w}_{\mathrm{Lasso}}\:=\:\arg\min_{w\in\mathbb{R}^{d}}\:\frac{1}{2}\|\mathbf{y}-\mathbf{X}w\|_{2}^{2}+\lambda\|w\|_{1}\\f(w)$$

$$\nabla f(w_{t})\:=-\:\mathbf{X}^{T}(\mathbf{y}-\mathbf{X}w_{t})+\lambda\mathrm{sign}(w_{t})\\w_{t+1}\:=\:w_{t}+\eta\mathbf{X}^{T}(\mathbf{y}-\mathbf{X}w_{t})-\lambda\mathrm{sign}(w_{t})$$

# Why gradient descent works..

What is a convexset?

A set $K\subset\mathbb{R}^{d}$ is convex if $(1-\lambda)x+\lambda y\in K$ for all $x,y\in K$ and $\lambda\in[0,1]$

![](./images/fHUhFCEAG0pXP0p87XB3QiznyO90T2VNR.png)

## A set $K\subset\mathbb{R}^d$ is convex if $(1-\lambda)x+\lambda y\in K$ for all $x,y\in K$ and $\lambda\in[0,1]$

![](./images/faBhr8fbRDB6HL8B8dDvUCSO2ogCDgq4E.png)

A function $f:\mathbb{R}^d\to\mathbb{R}$ is convex if $f((1-\lambda)x+\lambda y)\leq(1-\lambda)f(x)+\lambda f(y)$ for all $x,y\in\mathbb{R}^d$ and $\lambda\in[0,1]$

![](./images/fhCwKeoF1vmRE9xqXH7uwEevg8oOvHYPb.png)

# Recap: Ridge vs. Lasso

· Ridge

$$\text{minimize}_w\:\sum_{i=1}^n(w^Tx_i-y_i)^2+\lambda\|w\|_2^2$$

Very fast:

·Closed form solution if used with linear models · Even with other loss functions, optimization is fast for squared $\ell_2$ regularization, because $\|w\|_2^2$ is convex and smooth

· Lasso
$$\text{minimize}_w\:\sum_{i=1}^n{(w^Tx_i-y_i)^2}+\lambda\|w\|_1$$

Slower than Ridge:

. Requires iterative optimization algorithm like sub-gradient descent · In particular, it is slower because $\|w\|_1$ is convexbut non-smooth

Stochastic gradient descent

$$chineLearningProble$$

 Given data:

$$\{(x_i,y_i)\}_{i=1}^n\quad x_i\in\mathbb{R}^d\quad y_i\in\mathbb{R}$$

![](./images/fi8e2YgikfbqgbW1akbzURaTw8xG7QR6z.png)

Learning a model's

Gradient
$$\begin{aligned}&\text{escent:}\\&w_{t+1}=w_t-\eta\nabla_w\left(\frac{1}{n}\sum_{i=1}^n\ell_i(w)\right)\Big|_{w=w_t}\end{aligned}$$

$$chineLearningProble$$

 Given data:

$$\{(x_i,y_i)\}_{i=1}^n\quad x_i\in\mathbb{R}^d\quad y_i\in\mathbb{R}$$

![](./images/fU3xcliFGAepPvTaABFRgMgXrVVmlbmrD.png)

Learning a model's

Gradient
$$\begin{aligned}&\text{escent:}\\&w_{t+1}=w_t-\eta\nabla_w\left(\frac{1}{n}\sum_{i=1}^n\ell_i(w)\right)\Big|_{w=w_t}\end{aligned}$$

Stochastic Gradient Descent:
$$\begin{aligned}
asticolaulcillocsceill. \\
&w_{t+1}=w_{t}-\eta\nabla_{w}\ell_{I_{t}}(w)\Big|_{w=w_{t}}&& I_{t}\mathrm{~drawn~uniform~a} && \mathrm{random~from~}\{1,\ldots   \\
&\mathbb{E}[\nabla\ell_{I_{t}}(w)]=
\end{aligned}$$

$$chineLearningProbl$$

Given data:

$$\{(x_i,y_i)\}_{i=1}^n\quad x_i\in\mathbb{R}^d\quad y_i\in\mathbb{R}$$

![](./images/fXP8GIux6QNcchuD4R8dMesgcmlSUeNTl.png)

Learning a model's parameters:

Stochastic Gradient Descent:
$$w_{t+1}=w_t-\eta\nabla_w\ell_{I_t}(w)\Big|_{w=w_t}$$

$I_{t}$ drawn uniform at random from $\{1,\ldots,n\}$

$$\mathbb{E}[\nabla\ell_{I_t}(w)]=\nabla\ell(w)$$

# Mini-batch SGD

· Instead of one iterate, average B stochastic gradient together

· Advantages:

· Smaller variance: the variance of the stochastic gradient is smaller by a factor of $1/\sqrt{B}$ · Parallelization: each gradient in the mini-batch can be computed in parallel

Iro $\frac1n\sum_{i=1}^n\ell_i(w)+r(w)$ Tsnri

regularizer

$$w_{t+1}=w_t-\eta\nabla_wl_{I_1,...,I_B}(w_t)$$

![](./images/fXvm08PI3N3B79aaqMF648Pr2r1Fhs9Tz.png)

![](./images/fzRgEsqYcBsCu6qOtRPWk5DFnXvQxvZTD.png)

Batch gradient descent Mini-batch gradient Descent Stochastic gradient descent