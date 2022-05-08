# Question 1

Suppose that we are attempting to estimate the mean μ of a Gaussian distribution describing a set of scalar measurements x. Assume that the variance of the distribution is known to be σ2 = 10 .

Suppose that we have some independent sample measurements *D* as shown below.

D = {18, 8, 15, 12, 9}

What is the maximum likelihood estimate of the mean μ? Give your answer to one decimal place.

***Ans:***
$$
ML\space\ estimate=sample\ \ mean=\frac{(18+8+15+12+9)}{5}\approx12.4
$$

# Question 2

Suppose that we are attempting to estimate the mean μ of a Gaussian distribution describing a set of scalar measurements x. Assume that we know the variance of x to be σ2 = 2.

Suppose that we have some independent sample measurements *D* as shown below.

*D* = {7, 15, 12, 10, 14}

Suppose that based on some prior knowledge, we have a prior distribution on the mean μ. In particular, we assume that it is Gaussian with mean μ0 = 2 and variance σ02  = 12.

By combining the data and the prior information, we estimate that x has a Gaussian distribution with mean μ5  and variance σx2 .

Find the value of the mean μ5 to one decimal place. 

***Ans:***

weighted average of ML and prior estimate:
$$
\begin{align*}
\mu_n&=\frac{n\sigma_0^2}{n\sigma_0^2+\sigma^2}\hat\mu+\frac{\sigma^2}{n\sigma_0^2+\sigma^2}\mu_0\\&=\frac{5\times12}{5\times12+2}\times\frac{7+15+12+10+14}{5}+\frac{2}{5\times12+2}\times2
\\&\approx11.3
\\\sigma_n^2&=\frac{\sigma_0^2\sigma^2}{n\sigma_0^2+\sigma^2}
\\E&=\mu_n
\\\sigma&=\sigma^2+\sigma_n^2

\end{align*}
$$

# Question 3

Suppose that X is a Bernoulli random variable where the probability that X=1 is p.

Suppose that we have some independent sample measurements *D* as shown below.

D = {0, 1, 0, 1, 1, 0, 0, 0}

What is the maximum likelihood estimate of p ? Give your answer to two decimal places.

***Ans:***
$$
p=\frac{3}{8}\approx0.38
$$

# Question 4

Suppose that X is a Bernoulli random variable where the probability that X=1 is μ .

Suppose that we have some independent sample measurements D  as shown below.

D = {1, 0, 0, 0, 0, 0, 0, 1}

Suppose that based on some prior knowledge, we have a prior distribution over μ, which is given by a beta distribution with hyper parameters a  = 5 and b  = 10. 

Combining the data and the prior information, we find that X is given by a Bernoulli distribution with parameter p=P(X=1|D,a,b) .

Find the value of p to two decimal places.

***Ans:***

Beta distribution:
$$
\begin{align*}
p(\mu|a,b) &= \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\mu^{a-1}(1-\mu)^{b-1}
\\E[\mu] &= \frac{a}{a+b}
\\var[\mu] &= \frac{ab}{(a+b)^2(a+b+1)}
\end{align*}
$$
Posterior distribution for u:
$$
\begin{align*}
p(\mu|m,l,a,b) &= \frac{\Gamma(m+a+l+b)}{\Gamma(m+a)\Gamma(l+b)}\mu^{m+a-1}(1-\mu)^{l+b-1}

\\E[\mu]&= \frac{a+m}{a+m+b+l} = \frac{7}{23}\approx0.3
\end{align*}
$$

# Question 5

Suppose that we are attempting to estimate the mean μ and varianceσ2 of a Gaussian distribution describing a set of scalar measurements x. 

Suppose that we have some independent sample measurements *D* as shown below.

*D* = {19, 17, 6, 14, 14}

What is the maximum likelihood estimate of the variance σ2? Give your answer to one decimal place.

***Ans:***
$$
\begin{align*}
E &= \frac{19+17+6+14+14}{5}=14
\\\sigma^2 &= \frac{(19-14)^2+(17-14)^2+(6-14)^2}{5} = 19.6
\end{align*}
$$

# Question 6

Suppose that an input feature vector x=[x1x2] is distributed according to a bivariate (two dimensional) Gaussian with unknown mean vector and covariance matrix.

Given the observations

D = { (8,9), (5,7), (4,7), (10,6) }

Find the maximum likelihood estimate of the covariance between x1 and x2 to one decimal place.

***Ans:***
$$
\begin{align*}
E &= \frac{(8,9)+(5,7)+(4,7)+(10,6)}{4}=(6.75,7.25)
\\E(XY)&=\frac{8\times9+5\times7+4\times7+10\times6}{4}=48.75
\\Cov(X,Y)&=E(XY)-E(X)E(Y)=48.75-6.75\times7.25=-0.1867\approx-0.2
\end{align*}
$$

# Question 7

Suppose that we are attempting to estimate the mean μ of a Gaussian distribution describing a set of scalar measurements x. Assume that we know the variance of x to be σ2 = 2.

Suppose that we have some independent sample measurements *D* as shown below.

*D* = {13, 11, 15, 13, 11}

Suppose that based on some prior knowledge, we have a prior distribution on the mean μ. In particular, we assume that it is Gaussian with mean μ0 = 7 and variance σ02  = 8.

By combining the data and the prior information, we estimate that x has a Gaussian distribution with mean μ5  and variance σx2 .

Find the value of the variance σx2 to one decimal place. 
***Ans:***

weighted average of ML and prior estimate:
$$
\begin{align*}
\mu_n&=\frac{n\sigma_0^2}{n\sigma_0^2+\sigma^2}\hat\mu+\frac{\sigma^2}{n\sigma_0^2+\sigma^2}\mu_0\\&=\frac{5\times8}{5\times8+2}\times\frac{13+11+15+13+11}{5}+\frac{2}{5\times8+2}\times7

\\\sigma_n^2&=\frac{\sigma_0^2\sigma^2}{n\sigma_0^2+\sigma^2}=\frac{8\times2}{5\times8+2}=\frac{8}{21}
\\\sigma &= \frac{8}{21}+2\approx2.4
\end{align*}
$$
