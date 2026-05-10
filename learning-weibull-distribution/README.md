# Learning Weibull Distribution
---
## **Overview**
The Weibull Distribution using a dataset of time-to-failure (TTF) values. It estimates the shape factor ($k$) and scale parameter ($\lambda$) using a linear regression approach and plots both the Cumulative Distribution Function (CDF) and Probability Density Function (PDF).

### Key Equations
1. Cumulative Distribution Function (CDF):
$$F(t) = 1 - e^{-\left( \frac{t}{\lambda} \right)^k}$$
2. Probability Density Function (PDF):
$$f(t) = \frac{k}{\lambda} \left(\frac{t}{\lambda}\right)^{k-1} e^{-\left( \frac{t}{\lambda} \right)^k}$$
3. Estimating Shape Factor ($k$) and Scale Parameter ($\lambda$) using Regression:
  - The equation for $k$ (also known as beta) is determined by fitting a straight line to the transformed failure data.
  - The intercept of this line helps estimate $\lambda$ (also called eta).

---
## **Comparison of Probability Distributions**  

1. **Normal Distribution**  
   - Defined over the interval ($-\infty, \infty$).  
   - A continuous distribution characterized by its mean ($\mu$) and standard deviation ($\sigma$).  
   - Forms a symmetric bell-shaped curve.  

2. **Binomial Distribution**  
   - Defined over a discrete interval $[a, b]$, where $a$ and $b$ are real numbers representing the possible number of successes.  
   - A discrete probability distribution that models the number of successes in $n$ independent trials, each with probability $p$ of success.  

3. **Poisson Distribution**  
   - Defined over the interval $[a, \infty)$, where $a$ is a real number.  
   - A discrete probability distribution that models the number of occurrences of an event in a fixed interval of time or space.  

4. **Exponential Distribution**  
   - Similar to the Poisson distribution but differs in its parameters.  
   - A continuous probability distribution that models the time between occurrences of a Poisson process.  
   - Defined over the interval $[0, \infty)$.  

5. **Weibull Distribution**  
   - A generalization of the exponential distribution, defined over $[0, \infty)$.  
   - Characterized by two parameters:  
     - Shape parameter $k$ (beta), which controls the shape of the distribution.  
     - Scale parameter $\lambda$ (lambda), which determines the scale of the distribution.  
   - Special cases:  
     - When $k = 1$, the Weibull distribution reduces to the **Exponential Distribution**.  
     - When $k = 2$, it forms the **Rayleigh Distribution**.  
   - The estimation of $k$ (beta) is done using **Bernard’s Approximation**, requiring the calculation of median ranks.  

---
## **Conclusion**  
Each probability distribution serves a distinct purpose:  
- The **Normal distribution** is used for modeling continuous data that follows a symmetric bell curve.  
- The **Binomial distribution** is useful for discrete trials with two outcomes (success/failure).  
- The **Poisson and Exponential distributions** are related, with the Poisson modeling event counts and the Exponential modeling time between events.  
- The **Weibull distribution** is a flexible model for reliability analysis and failure time prediction.  
