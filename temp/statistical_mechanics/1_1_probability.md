---
title: The Basics
linktitle: The Basics
toc: true
type: docs
date: "2019-05-05T00:00:00Z"
draft: false
menu:
    statistical_mechanics:
        parent: Probability
        weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

Probability theory deals with quantities and events that are distributed randomly and shows how to calculate average values of various kinds.

## Discrete Distributions
We denote some variable of interest as $x$ and the discrete values that it may take as $x_i$ ($i = 1, 2, ..., N$).
If the probability that $x_i$ occurs is $p_i$, then the **_mean value_** (or _expectation value_) of $x$ is:

\begin{equation}  
    \langle x \rangle = \sum_{i=1}^{N}x_ip_i
\end{equation}

The mean values of higher powers of $x$ may be computed similarly:

\begin{equation}  
    \langle x^{n} \rangle = \sum_{i=1}^{N}x^{n}_ip_i 
\end{equation}

Although the mean is a useful measure it is important to know the width in the scatter of outcomes around the mean.
There are two related measures: one is the **_variance_**, $V(x)$, and the other is the **_standard deviation_**, $\sigma(x)$, the square root of the variance:

\begin{equation}  
    V(x) = \langle x^{2} \rangle - \langle x \rangle^{2}
\end{equation}

\begin{equation} 
    \sigma(x) = \sqrt{V(x)} = \sqrt{\langle x^{2} \rangle - \langle x \rangle^{2}} 
\end{equation}

In certain cases, the probabilities can be expressed in a simple way, depending on the nature of events being considered.

### The Binomial Distribution
In a **_Bernoulli trial_**, the outcome of an observation is one of a mutually exclusive pair ( like _heads_ or _tails_ in a coin toss) and successive trials are independent (so that getting _heads_ on one toss does not influence the following toss).
Suppose the probability of outcome 1 is $p$ and that of the alternative outcome 2 is $q$, with $p+q=1$.
For a fair coin, $p=q=0.5$.
Then one series of $N=12$ trials might be _THHTTHTHTTHT_, which has a probability of occurrence $=p^{5}q^{7}$.
In general the probability of any such series of trials is $p^{n}q^{N-n}$.

However, if the order in which _heads_ appear is irrelevant there are $12! / 5!7!$ ways of achieving 5 _heads_ in 12 tosses, and in general $N!/n!(N-n)!$ ways of achieving $n$ _heads_ in $N$ trials.
The probability of getting exactly $n$ _heads_ is therefore the product of $p^{n}q^{N-n}$ and the number of ways of distributing $n$ _heads_ over $N$ trials:

\begin{equation}
    P(n) = \begin{pmatrix} N \\\\ n \end{pmatrix}p^{n}q^{N-n} \quad \text{where} \ \begin{pmatrix} N \\\\ n \end{pmatrix} = \dfrac{N!}{n!(N-n)!}
\end{equation}

The symbol $\begin{pmatrix} N \\\\ n \end{pmatrix}$ is known as the **_binomial coefficient_**, as it occurs in the **_binomial expansion_**:

\begin{equation}
    (x+y)^{N} = \sum_{n=0}^{N}\begin{pmatrix} N \\\\ n \end{pmatrix}x^{n}y^{N-n}
\end{equation}

### The Poisson Distribution

