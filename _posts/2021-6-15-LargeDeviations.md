---
layout: post
title: Large Deviations
---

_In this post, I am going to give an introduction to Large Deviations, a theory for analyzing the probability of very rare events.  I am going to focus on why Large Deviations theory is useful in some situations where more standard probability is not._ 

Let's pretend that you are at a casino, and there is a game in which a player has a 20% chance of winning \\$1 and a 80% chance of winning nothing.  If the player plays the game 30 times, how likely is it that the player wins at least \\$24?  Surely the player winning at least \\$24 is very rare, since the player only has a 20% chance of winning anything on each turn.  But the casino owner might be interested in exactly how rare something like this is when deciding how much to for example charge for each round of the game.  

This is a situation in which we can use the theory of large deviations. We can start by formalizing this setup mathematically.  Let $X_1, X_2, \ldots$ be independent and identically distribution (i.i.d.) random variables and let $$\bar{X}_n = \frac{1}{n} \sum_{i=1}^n X_i$$ be the average of the first $n$.  We will be interested in the probability

<center>$P(\bar{X}_n \geq x)$</center>

for some constant $x > EX_i$.  Estimating this probability will be the central focus of our discussion of large deviations.  

(Note: large deviations is a much broader field of math than just analyzing such a probability.  In fact, the theory of large deviations provides a much higher abstracted framework for studying rare events.  See e.g. [Dembo's textbook](https://link.springer.com/book/10.1007/978-3-642-03311-7) for the general framework.  For this post, I will focus on this specific use case of the large deviations theory as it is perhaps the most important and also the most interesting to me.)

Returning to the casino example, if we let $X_i$ be the winnings of the player on their $i$th playing of the game, then $X_i \sim \text{Bernoulli}(p=0.2)$ and the large deviations probability which we want to estimate is $P(\bar{X}_{30} \geq 0.8)$.  Recall that the sum of Bernoulli random variables is a Binomial random variable, and so in this case the probability is fairly straightfoward to calculate:

$$
\begin{align}
    P(\bar{X}_{30} \geq 0.8) &= P(30 \cdot \bar{X}_{30} \geq 24) \\
    &= P(30 \cdot \bar{X}_{30} = 24) + \cdots + P(30 \cdot \bar{X}_{30} = 30)
\end{align}
$$

and since $30 \cdot \bar{X}_{30} \sim \text{Binomial}(30, 0.2)$ we can use the known mass function of the binomial distribution to find this probability, which turns out to be

<center>$P(\bar{X}_{30} \geq 0.8) \approx 2.78 \cdot 10^{-12}$ </center>

That is in fact extremely small!  Now let's pretend that we weren't able to easily calculate this probability, since in many cases the sum of i.i.d. random variables does not have a nice distribution.  We do know from the Central Limit Theorem that the average of i.i.d. random variables converges to a normal random variable (assuming finite variance), so for our Bernoulli example, the Central Limit Theorem tells us

<center>$$\frac{(\bar{X}_n - p)}{\sqrt{p(1-p) / n}} \stackrel{d}{\longrightarrow} N(0, 1)$$ </center>

With $n=30$ and $p=0.2$ as we have been using, we get the approximation

<center> $$\frac{(\bar{X}_{30} - 0.2)}{\sqrt{0.2(0.8) / 30}} \stackrel{d}{\longrightarrow} N(0, 1)$$ </center>

and so if $\Phi$ is the cumulative distribution function of a standard normal, then we can approximate our large deviation probability as

$$
\begin{align*}
    P(\bar{X}_{30} \geq 0.8) &= P\left( \frac{\bar{X}_{30} - 0.2}{\sqrt{0.2(0.8)/30}} \geq \frac{0.8 - 0.2}{\sqrt{0.2(0.8)/30}}\right) \\
    &\approx 1 - \Phi\left(\frac{0.8 - 0.2}{\sqrt{0.2(0.8)/30}}\right)
\end{align*}
$$

A few quick notes.  First, you might wonder if 30 data points is enough to make this CLT approximation valid.  The classic assumption is that if $np > 5$ and $n(1-p) > 5$, then this approximation is good.  We have $np = 6$ and $n(1-p) = 24$, so we pass this condition check.  Second, if we want to be careful, we should actually use a [continuity correction](https://www.statisticshowto.com/what-is-the-continuity-correction-factor/) since we are approximating a discrete distribution with a continuous distribution.  What you should think is that $$30 \cdot \bar{X}_{30}$$ can only take on integer values, so really 

<center>$P(30 \cdot \bar{X}_{30} \geq 24) = P(30 \cdot \bar{X}_{30} > 23)$ </center>  

Thus, when we approximate using a continuous distribution, we should in a sense meet-in-the-middle and use 23.5 to account for this gap.  With this continuity correction, our approximation using the CLT is

$$
\begin{align*}
    P(\bar{X}_{30} \geq 0.8) &\approx 1 - \Phi\left(\frac{23.5/30 - 0.2}{\sqrt{0.2(0.8)/30}}\right) \\
    &\approx 6.66 \cdot 10^{-16}
\end{align*}
$$

Recall that the actual value is $2.78 \cdot 10^{-12}$, so while our CLT approximation is very small as desired, it is off from the known value by a factor of 4167!  You might wonder how important this large relative error is, since these numbers are all so small anyway.  In some situations it might not be extremely significant; in our running casino example, the risk of paying out \\$24 to a player after 30 games is hardly a risk at all, so this difference is surely negotiable.  However, if we were instead looking at the probability of a much higher risk event, such as a player winning a billion dollars, this error is not acceptable.   


It's worth asking at this point what we did wrong in using the CLT approach to give us this bad approximation.   I would actually argue that nothing went "wrong", we are actually just working on such a small scale that the CLT approximation is not guaranteed to be good.  More specifically, we know from the [Berry-Esseen Theorem](https://en.wikipedia.org/wiki/Berry%E2%80%93Esseen_theorem) that the difference between the CDF of $\frac{\bar{X}_n - 0.2}{\sqrt{0.2(0.8)/n}}$ and $\Phi$ is on the order of $1/\sqrt{n}$.  The important note here is the Berry-Esseen bound is a bound on the <em>difference</em> or <em>absolute error</em> from the CLT approximation.  In terms of absolute error, the CLT approximation in our example is tiny, yet the <em>relative error</em> is still large.  So when dealing with very small probabilities in the context of large deviations, this CLT approximation is not wrong per se, but it is not sufficient.

Now that we've motivated a need for a different approach, let's introduce how we can approximate this probability using large deviations theory.  The core result of large deviations theory (again, for the purposes of this post) is [Cramer's Theorem](https://en.wikipedia.org/wiki/Cram%C3%A9r%27s_theorem_(large_deviations)).  To state Cramer's Theorem, we first define the cumulant generating function and the Legendre transform.  Given a random variable $X$, the cumulant generating function $\Lambda(t)$ is the logarithm of the moment generative function, that is, 

<center> $\Lambda(t) = \log E \left[ e^{tX} \right]$ </center>

Further, the Legendre transform $\Lambda^*(x)$ of the cumulant generating function at a given $x\in\mathbb{R}$ is

<center> $$\Lambda^*(x) = \sup_{t\in\mathbb{R}} (tx - \Lambda(t))$$ </center>

Using these, Cramer's Theorem gives us the following asymptotic result: for every $x > EX_i$, we have

<center> $$\lim_{n \to \infty} \frac{1}{n} \log P(\bar{X}_n \geq x) = -\Lambda^{*}(x)$$ </center>

Let's think for a second about what this theorem is telling us.  First, we get an appoximation for our large deviation probability

<center> $P(\bar{X}_n \geq x) \approx e^{-n \cdot \Lambda^*(x)}$ </center>

and so this gives us an alternative way to approximate the probability we have been interested in.  But this theorem is more than just an approximation, it is an asymptotic result about the rate of exponential decay as $n$ approached infinity.  This is a core feature that distinguishes large deviations and the CLT: the CLT provides asymptotics for convergence in distribution of properly scaled and centered random variable averages, while large deviations provides asymptotics for decay rates of tail probabilities.  So while the CLT can be used to approximate these large deviations probabilities, the asymptotics from Cramer's Theorem are specifically for this task, while the asymptotics from the CLT are not.   

A few additional notes to keep in mind about Cramer's Theorem:

- Cramer's Theorem tells us that the large deviations probability $P(\bar{X}_n \geq x)$ decreases exponentially as $n\to\infty$.  We already knew from the Law of Large Numbers that this probability converges to 0 as $n\to\infty$, but this further tells us that the decrease to 0 is exponential.  The value of $$\Lambda^*(x)$$ further tells us how fast this decay occurs, therefore $$\Lambda^*(x)$$ is often called the <em>rate function</em>.

- Notice that the rate function $$\Lambda^*(x)$$ depends on the distribution of $X_i$ since it depends on the cumulant generating function.  The CLT approximation, on the other hand, does not depend on the distribution of $X_i$.  So while the CLT is good for approximating common events such as confidence intervals, when approximating rare events it is helpful to consider the distribution of the random variables at hand.  

- We have to put some sort of assumption on the moment generating function in order to use Cramer's Theorem.  This is because the probability $P(\bar{X}_n \geq x)$ does not decrease exponentially for all distributions (e.g. heavy tail distributions), and so approximating with exponential decay does not always make sense.  The most common assumption is to assume that $\Lambda(t) = \log E \left[ e^{tX} \right] < \infty$ for all $t \in \mathbb{R}$ (as done on [Klenke](https://books.google.com/books/about/Probability_Theory.html?id=eTYMnQEACAAJ)), but alternatively one can assume that there exists a single $t\in\mathbb{R}$ such that $\Lambda(t) < \infty$ and that $P(\bar{X}_n \geq x) \to 0$ exponentially (as done in [Durrett](https://services.math.duke.edu/~rtd/PTE/PTE5_011119.pdf)).

- [Using Markov's Inequality](http://page.math.tu-berlin.de/~scheutzow/ld.pdf), we can show that the approximation from Cramer's Theorem is actually always an upper bound.  It just so happens that it is a tight upper bound that gets closer to the true probability as $n\to\infty$.    

Alright, now let's return to our casino example.  In order to find the large deviations approximation, we need to find the rate function for the Bernoulli distribution.  The moment generating function for a Bernoulli is $(1-p) + pe^t$, so the rate function is

<center> $$\Lambda^*(x) = \sup_{t\in\mathbb{R}} (tx - \log[(1-p) + pe^t])$$ </center>

Solving this using calculus yields

<center> $$\Lambda^*(x) = x\log(x/p) + (1-x)\log((1-x)/(1-p))$$ </center>

Therefore, the large deviations approximation is

$$
\begin{align*}
    P(\bar{X}_{30} \geq 0.8) &\approx \exp\left(-30 \cdot  [0.8\log(0.8/0.2) + 0.2\log(0.2/0.8) ]\right) \\
    &= 1.48 \cdot 10^{-11}
\end{align*}
$$

Compared to the known probability is $2.78 \cdot 10^{-12}$, this approximation is much closer, with a relative error of only about 5.   

In conclusion, we have illustrated how to use the framework of large deviations to approximate probabilities of the form $P(\bar{X}_n \geq x)$ more accurately than using the CLT.  Further, this framework gives a way to demonstrate asymptotic results for these small probability situation, something the CLT does not provide at all.

## Further Reading

Dembo, A., Zeitouni, O.: Large Deviations Techniques and Applications. (1998).

Klenke, Achim: Large Deviations. (2008)

Durrett, R: Probability: Theory and Examples (Version 5). (2019)

Arratia, R., Gordon, L.: Tutorial on large deviations for the binomial distribution. (1989)