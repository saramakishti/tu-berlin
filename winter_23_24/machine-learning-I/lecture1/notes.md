## Bayesian Decision Theory

Bayes' Theorem is a principle in probability theory that describes how to update the probabilities of hypotheses when given evidence. It plays a crucial role in decision theory by allowing decision-makers to update their beliefs about the likelihood of different outcomes based on new information.

**Bayesian decision theory is a fundamental statistical approach to the problem of pattern classification.**

It makes the assumption that the decision problem is posed in probabilistic terms, and that all of the relevant probability values are known.

Let's the problem of designing a classifier that separates two types of fish: sea bass and salmon.

**State of Nature**
We let ω denote the state of nature, with $\ ω = ω_1 $ for sea bass and $\ ω = ω_2 $ for salmon. Because the state of nature is so unpredictable, we consider ω to be a variable that must be described probabilistically.

**Prior Probability**
We assume that there is some a priori probability (or simply prior) $\ P(ω_1) $ that the next fish is sea bass, and some prior probability $\ P(ω_2) $ that it is salmon. If we assume there are no other types of fish relevant here, then $\ P(ω_1) $ and $\ P(ω_2) $ sum to one.

Assume that any incorrect classification entails the same cost or consequence, and that the only information we are allowed to use is the value of the prior probabilities. If a decision must be made with so little information, it seems logical to use the following decision rule: Decide $\ ω_1$ if $\ P(ω_1) > P(ω_2) $; otherwise decide $\ ω_2$.

If $\ P(ω_1)$ is very much greater than $\ P(ω_2)$, our decision in favor of $\ ω_1$ will be right most of the time.
If $\ P(ω_1) = P(ω_2) $, we have only a fifty-fifty chance of being right.

In general, the probability of error is the smaller of $\ P(ω_1) $ and $\ P(ω_2) $, and we shall see later that under these conditions no other decision rule can yield a larger probability of being right.

**Class-conditional probability density function**

Different fish will yield different lightness readings and we express this variability in probabilistic terms; we consider $\ x$ to be a continuous random variable whose distribution depends on the state of nature, and is expressed as $\ p(x|ω_1)$.

This is the probability density function for $\ x $ given that the state of nature is $\ ω_1$. (It is also sometimes called state-conditional probability density.)

Then the difference between $\ p(x|ω_1)$ and $\ p(x|ω_2)$ describes the difference in lightness between populations of sea bass and salmon

> We generally use an upper-case P to denote a probability mass function and a lower-case p to denote a probability density function.

**Bayes Formula**

$\ P(ω_j|x) = \dfrac{ p(x|ω_j) * P(ω_j)}{p(x)}$

where in this case of two categories:

$$\mathrm{p(x)} = \sum_{j=1}^{2} {p(x|w_j)}{P(wj)}$$

Or informally in English:

$\ posterior = \dfrac{likelihood * prior}{evidence}$

Bayes' formula shows that by observing the value of $\ x$ we can convert the prior
probability $\ P(ω_j)$ to the _a posteriori_ probability (or posterior) probability $\ P(ω_j|x)$ posterior
— the probability of the state of nature being $\  ω_j$ given that feature value $\ x$ has been measured.

We call $\ p(x|ω_j)$ the _likelihood_ of $\ ω_j$ with respect to $\ x$

- a term chosen to indicate that, other things being equal, the category $\ ω_j$ for which $\ p(x|ω_j)$ is large is more "likely" to be the true category.

> Notice that it is the product of the likelihood and the prior probability that is most important in determining the posterior probability; the evidence factor, $\ p(x)$, can be viewed as merely a scale factor that guarantees that the posterior probabilities sum to one, as all good probabilities must.

Let us calculate the probability of error whenever we make a decision. Whenever we observe a particular $\ x$:

$$
P(error|x)=
\begin{cases}
P(ω_1|x) & \quad \text{if we decide $ω_2$}\\
P(ω_2|x) & \quad \text{if we decide $ω_1$}
\end{cases}

(Equation 1)
$$

Clearly, for a given $\ x$ we can minimize the probability of error by deciding $\ ω_1$ if $\ P(ω_1|x) > P(ω_2|x)$ and $\ ω_2$ otherwise.

Of course, we may never observe exactly the same value of $\ x$ twice. Will this rule minimize the average probability of error? Yes, because the average probability of error is given by

$$ P(error) = \int*{-\infty}^\infty P(error,x) dx = \int*{-\infty}^\infty P(error|x)p(x) dx$$

and if for every $\ x$ we insure that $\ P(error|x)$ is as small as possible, then the integral must be as small as possible.

So under this rule, Equation 1 becomes:

$\ P(error|x) = min [P(ω_1|x), P(ω_2|x)]$
