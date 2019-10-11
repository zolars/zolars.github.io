---
title: Probability Theory Notes
date: 2017-06-03 14:42:20
categories: Study
tags:
- math
toc: true
mathjax: true
---

> This is the course notes for Probability Theory and Stochastic Processes.

<!--more-->

# Chapter 1 Event and Their Probabilities

## 1.1 The History of Probability

## 1.2 Experiment, Sample Space and Random Event

### 1.2.1 Basic Definitions

* Random experiment

  1. **Repeatability**
  2. **Predictability**
  3. **Uncertainty**

* Sample place

  The set of all possible outcomes of an ramdom experiment is known as the sample place.

* Inevitable events & Impossible events

  Those events must / can not occur in the experiment are called the inevitable / impossible events.

### 1.2.2 Events as Sets

Here we list their connections and differences in the following Table.

|    Typical notation    | Set jargon            | Probability jargon                     |
| :--------------------: | :-------------------- | :------------------------------------- |
|        $\Omega$        | Collection of objects | Sample space                           |
|        $\omega$        | Member of $\Omega$    | Elementary event, outcome              |
|          $A$           | Subset of $\Omega$    | Events that some outcome in $A$ occurs |
| $A$ or $\overline{A} $ | Complement of $A$     | Event that no outcome in $A$ occurs    |
|       $A \cap B$       | Intersection          | Both $A$ and $B$                       |
|       $A \cup B$       | Union                 | Either $A$ or $B$ or both              |
|        $A - B$         | Difference            | $A$, but no $B$                        |
|    $A \subseteq B$     | Inclusion             | If $A$, then $B$                       |
|     $\varnothing$      | Enpty set             | Impossible event                       |
|        $\Omega$        | Whole space           | Certain set                            |

---

Let $A$, $B$, $C$ be the random events of experiment $E$. The operations of the events will satisfy the following rules,

* Commutatively

  $A \cup B = B \cup A, AB=BA.$

* Associatively

  $A \cup (B \cup C) = (A \cup B)  \cup C = A  \cup B  \cup C.$

  $A(BC) = (AB)C = ABC.$

* Distributively

  $A \cup (B \cap C) = (A \cup B) \cap (A \cup C).$

  $A(B \cup C) = (AB) \cup (AC).$

* De Morgan's law

  $\overline{A \cup B}=\overline{A} \cap \overline{B}, \overline{A \cap B}=\overline{A} \cup \overline{B}.$

## 1.3 Probabilities Defined on Events

### 1.3.1 Classical Probabilities

Generally, a random experiment $E$ is **classical** if,

1. $E$ contains only different limited basic events, that is, $\Omega = \{\omega_1, \omega_2, \omega_3, \dotsb \omega_n\} $. We call this kind of sample space **simple space**.
2. All outcomes are equally likely to occur.

That is, for classical random experiment $E$, $\Omega = \{\omega_1, \omega_2, \omega_3, \dotsb \omega_n\} $, we define the probability of event $A$ as,
$$
P(A)=\frac{ \#A} { \#\Omega}.
$$
where `#A` means the number of all possible outcomes of event $A$, `#Ω` Means the number of all possible outcomes of sample space $\Omega$. The probability of impossible event is defined as,
$$
P(\varnothing)=0.
$$

### 1.3.2 Geometric Probabilities

Generally, a random experiment $E$ is called to be **geometric** if,

1. The sample space is a a measurable (such as length, area, volume, etc.) region, i.e., $0<L(\Omega)<\infty$.
2. The probability of every event $A\subset\Omega$ is proportional to the measure $L(A)$ and has nothing to do with its position and shape.

In this case, we define the probability of event $A$ as,
$$
P(A)=\frac{L(A)} {L(\Omega)} \text{  and } P(\varnothing)=0.
$$
---

For Geomatrical random experiment $E$, the probability has the following properties,

1. For every event $A$, $P(A)\geqslant 0$.

2. $P(\Omega)=1$.

3. For every countable disjoint events $A_1, A_2, \dotsb ,$
   $$
   P (\text{ } \bigcup^{\infty}_{i=1}A_i \text{ }) = \sum^{\infty}_{i=1}P(A_i).
   $$
   

### 1.3.3 The Frequency Interpretation of Probabilities

Let $E$  be a random experiment, $A$ be a random event. Suppose that $E$ was repeated $n$ times under similar conditions. Let $f_n(A)$ be the times that $A$ occurs. The ration
$$
F_n(A)=\frac{f_n(A)} {n}
$$
is said to be the **frequency** of event $A$ in the $n$ trials. If $n$ is large enough, the probability of event $A$ will be approximated by $F_n(A)$.

---

For a random experiment $E$, the probability has the following properties,

1. For every event $A$, $F_n(A)\geqslant 0$.

2. $F_n(\Omega)=1$.

3. For every countable disjoint events $A_1, A_2,  \dotsb  , A_n,$
   $$
   F_n (\text{ } \bigcup^{\infty}_{i=1}A_i \text{ }) = \sum^{\infty}_{i=1}F_n(A_i).
   $$


## 1.4 Probability Space

### 1.4.1 Axiomatic Definition of Probability

A collection $\mathscr{F} $ of subsets of $\Omega$ is a $\sigma$-**algebra** if,

1. $\Omega \in \mathscr{F} $.

2. $F \in \mathscr{F} \Longrightarrow \overline{F} \in \mathscr{F} $.

3. If $F_n$ is a countable collection of sets, $n=1,2, \dotsb$  such that $F_n \in \Omega$ for all n, then,
   $$
   \bigcup_{n}F_n \in \mathscr{F}
   $$
   
---

Let $P(A) (A \in \mathscr{F})$ be a non-negative set function on the $\sigma$-algebra $\mathscr{F} $. $P(A)$ is called the probability measure or **probability of event** $A$  if it satisfies the following three axioms,

1. For every $A \in \mathscr{F}, P(A) \geqslant 0$.

2. $P(\Omega)=1$.

3. (countable additivity) For every infinite sequence of countable disjoint events $A_1, A_2, \dotsb ,$
   $$
   P (\text{ } \bigcup^{\infty}_{i=1}A_i \text{ }) = \sum^{\infty}_{i=1} P(A_i).
   $$
   The set in $\sigma$-algebra $\mathscr{F} $ are called events. $\mathscr{F} $ is called to be the algebra of events. The triple($\Omega, \mathscr{F}, P$) is a **probability space** or **probability triple**.

### 1.4.2 Properties of Probability

* $P(\varnothing) = 0$

* For every finite sequence of countable disjoint events $A_1, A_2,  \dotsb , A_n,$
  $$
  P (\text{ } \bigcup^{n}_{i=1}A_i \text{ }) = \sum^{n}_{i=1} P(A_i).
  $$

* For every event $A$, $P(\overline{A}) = 1 - P(A)$.

* If $A \subset B$, then $P(A - B) = P(B) - P(A) \text{ } and \text{ } P(A) \leqslant P(B)$.

* For every event $A$, $0 \leqslant P(A) \leqslant 1$.

* For every two events $A$ and $B$,
  $$
  P(A \cup B) = P(A) + P(B) - P(AB).
  $$


## 1.5 Conditional Probabilities

### 1.5.1 The Definition of Conditional Probability

Given two events $A$ and $B$ with $P(B) > 0$, the **conditional probability of** $A$ **given** $B$ is defined as the quotient of the joint probability of $A$ and $B$, and the probability of $B$,

$$
P(A|B) = \frac{P(AB)} {P(B)}
$$
---

If $P(B)>0$, then the conditional probability $P(A|B)$ is also a probability, that is,

1. For every event $A$, $P(A|B) \geqslant 0$.

2. $P(A|B)=1$.

3. For every infinite sequence of countable disjoint events $A_1, A_2,  \dotsb ,$
   $$
   P (\text{ } \bigcup^{\infty}_{i=1}A_i|B \text{ }) = \sum^{\infty}_{i=1} P(A_i|B).
   $$


If $P(B) > 0$, then,

1. $P(\varnothing|B)=0$.

2. For every finite sequence of countable disjoint events $A_1, A_2,  \dotsb , A_n,$
   $$
   P (\text{ } \bigcup^{n}_{i=1}A_i|B \text{ }) = \sum^{n}_{i=1} P(A_i|B).
   $$

### 1.5.2 The Multiplication Rule

Assume that $P(B)>0$, then,
$$
P(AB)=P(B) \cdot P(A|B)
$$
Or if $P(A)>0$, then,
$$
P(AB)=P(A) \cdot P(B|A)
$$

### 1.5.3 Total Probability Formula

Suppose that the events $B_1, B_2, \dotsb, B_n$ form a partition of the sample space $\Omega$ and $P(B_i)>0$ for $i=1,2,\dotsb, n$. Then, for every event $A$ in $\Omega$,
$$
P(A)=\sum^n_{i=1} {P(Bi)P(A|B_i)}
$$

### 1.5.4 Bayes' Theorem

Let the events $B_1, B_2, \dotsb, B_n$ form a partition of the sample space $\Omega$ such that $P(B_i)>0$ for $i=1,2,\dotsb,n$, and let $A$ be an event such that $P(A)>0$. Then, for $i=1,2,\dotsb,n,$
$$
P(B_i|A)=\frac{P(B_i)P(A|B_i)} {\sum^n_{j=1}P(A|B_j)}
$$

##  1.6 Independence of Events

### 1.6.1 Independence of Events

Two events $A$ and $B$ are independent if,
$$
P(AB)=P(A)P(B).
$$
Suppose that $A$ and $B$ are disjoint events  for an experiment, each with positive probability. Then $A$ and $B$ are dependent.

If $A$ and $B$ are independent events in an experiment, then each of the following pairs of events is independent,

1. $\overline{A} $ and $B$.
2. $A$ and $\overline{B} $.
3. $\overline{A} $ and $\overline{B} $.

### 1.6.2 Independence of Several Events

Three events $A_1, A_2, \dotsb,A_n$ in the sample space $S$ of a random experiment are said to be **mutually independent** (or independent) if,
$$
P(A_iA_j)=P(A_i)P(A_j) \\[2ex]
P(A_1A_2 \dotsb A_n)=P(A_1)P(A_2) \dotsb P(A_n)
$$
Events $A_1, A_2, \dotsb,A_n$ are said to be **pairwise independent** if the first three equations hold.

### 1.6.3 Bernoulli Trial

A **Bernoulli experiment** $E$ is such kind of random experiment, the outcome of which can be classified in but one of two mutually exclusive and exhaustive ways. Mainly, success (denoted by $S$) or failure (denoted by $F$).

The outcomes of $E_n$ are the $2^n$ sequences of length $n$. The number of outcomes of $E_n$ that contains a exactly $k$ times is given by the binomial coefficient,
$$
\begin{pmatrix} n \\ k \end{pmatrix} =\frac{n!} {k!(n-k)!}
$$
The probability that the outcome of an experiment that consists of $n$ Bernoulli trails has $k$ successes and $n-k$ failures is given by,
$$
P_n(k)=P_n(\#S=k)=
\begin{pmatrix} n \\ k \end{pmatrix}
~ p^k ~ q^{n-k}
$$

# Chapter 2 Random Variable

## 2.1 The Definition of a Random Variable

A **random variable** is a function that assigns a real number to each outcome in the sample space.

A random variable is said to be of **discrete type** if the number of different values it can take is finite or countably infinite.

## 2.2 The Distribution Function of a Random Variable

### 2.2.1 The Definition and Properties of Distribution Function

We can denote the probability that the values of $X$ belong to the subset $I$ by $P(X \in I)$. Then $P(X \in I)$ is equal to the probability that the outcome $\omega$ of the experiment will be such that $X(\omega) \in I$. In symbols,
$$
P(X \in I) = P(\omega : X(\omega) \in I).
$$
The function $F(x)$ that associates with each real number $x$ the probability $P(X \leqslant x )$ that the random variable $X$ takes on a value smaller than or equal to this number is called the **distribution function** of $X$. That is,
$$
F(x)=P(X \leqslant x), \forall ~ x \in R.
$$
**d.f.** : distribution function.

**c.d.f.** : cumulative distribution function.

---

The d.f. $F(x)$ of every random variable $X$ has the following three properties,

1. It is nondecreasing as $x$ increases; that is, if $x_1 < x_2$, then $F(x_1) \leqslant F(x_2)$.
2. $\lim_{x \to -\infty} F(x) = 0$ and $\lim_{x \to + \infty} F(x) = 1$.
3. It is always right-continuous; that is, $F(x) = F(x^+)$ at every point $x$.

---

For every value $x$,
$$
P(X=x) = F(x)-F(x^-) \qquad and \qquad P(X \geqslant x) = 1 - F(x^-).
$$
For all values $x_1$ and $x_2$ such that $x_1 < x_2$,
$$
P(x_1 < X < x_2) = F(x^-_2) - F(x_1), \\
P(x_1 \leqslant X < x_2) = F(x^-_2) - F(x^-_1), \\
P(x_1 \leqslant X \leqslant x_2) = F(x_2) - F(x^-_1).
$$

#### <u>Discrete Case</u>

For a discrete random variable $X$, we define the **probability (mass) function** $p(x)$ of $X$ by,
$$
p(x) = P(X=x).
$$
**p.f.** : probability function.

---

Let $\{x_1, x_2, \dotsb\} $ be the set of possible values of the discrete random variable $X$. The function $p$ has the following properties,

1. $p(x_k) \leqslant 0$ for all $x_k$; $p(x)=0$ for all other value $x$.
2. $\sum^\infty_{k=1}p(x_k)=1$.

If $X$ has a discrete distribution, the probability of each subset $I$ of the real line can be determined from the relation,
$$
P(X \in I) = \sum_{x_k\in I} p(x_k).
$$
The relationship between d.f. $F(x)$ and p.f. $p(x)$ of $X$ is,
$$
F(x)=P(X \leqslant x) = \sum_{x_k \leqslant x} p(x_k).
$$

#### <u>Continuous Case</u>

We call $X$ a continuous random variable if there is a function $f$ defined for all $x \in R$ and having the following properties,

1. $f(x) \leqslant 0$ for any real number $x$.

2. If $I$ is any subset of $R$, then,

3. $$
   P(X \in I) = \int_I{f(x)dx},
   $$

   Where $f(x)$ is called the **probability density function**.

**p.d.f.** : probability density function.

---

If $f$ is a p.d.f. pf the r.v. $X$, then,
$$
P(a \leqslant X \leqslant b) = \int^a_b{f(x)dx}.
$$
If $I=(-\infty,x]$,then the distribution function $F$ of $X$ is given by,
$$
F(x) = P(X \leqslant x) = \int^x_{-\infty} {f(x)dx}.
$$

---

**Remark**

1. Indeed, $f$ does not give the probability that the random variable $X$ takes on the value $x$. The d.f. $F(x)$ of continuous r.v. $X$ is continuous since $P(X=x)=0$.

2. By using equation $\lim_{x \to + \infty} F(x) = 1$, we get,
   $$
   \int^{\infty}_{-\infty}f(x)dx = F(\infty) = 1.
   $$
   To be a p.d.f. pf some contiuous randome variables, the nonnegative function $f(x)$ needs satisfy this equation.

3. Moreover, we also deduce that,
   $$
   \frac{d} {dx}F(x)=f(x),
   $$
   for any $x$ where $F(x)$ is differentiable.

   When $F(x)$ is not differentiable at point $P$, so $f(x)=0$ at point $P$. 

### 2.2.2 The Distribution Function of Function of a Random Variable

#### <u>Discrete Case</u>

$$
p_Y(y)= P(Y = y) = P(g(X) = y) = \sum_{x:g(x)=y}p(x).
$$

#### <u>Continuous Case</u>

**The distribution function method** is a the usual way to obtian p.d.f. of a function of a continuous random variable. This method can be divided into four steps:

1. Transform the event $\{Y \leqslant y\} $ to $\{ g(X) \leqslant y\} $.
2. Transform the event $\{g(X) \leqslant y\} $ to $\{ g(X) \leqslant I_y\} $, where $I_y = \{x:g(x) \leqslant y\} $.
3. Calculate the probability $P(X \in I_y)$, which is just the d.f. $F(y)(=P(Y \leqslant y))$ of $Y$.
4. Obtain p.d.f. $f(y)$ of $Y$ by $f(x)=F'(x)$.

---

Let $X$ be a continuous random variable having p.d.f. $f_X$. Suppose that $g(x)$ is a strictly monotonic (increasing or decreasing), differentiable (and thus continuous) function of $x$. Then the random variable $Y$ defined by $Y = g(X)$ has a p.d.f. given by,
$$
f_Y(y) = 
\begin{cases}
f_X(g^{-1}(y))

\left|
\cfrac{d} {dx}g^{-1}(y)
\right|

& \text{if $y=g(x)$ for some $x$,} \\[2ex]
0 & \text{if $y \neq g(x)$ for all $x$,}
\end{cases}
$$
where $x=g^{-1}(y)$ is defined to equal that value of $x$ such that $g(x)=y$. 

## 2.3 Mathematical Expectation and Variance

### 2.3.1 Expectation of a Random Variable

The **expectation** (the mean or the **expected value**) of a random variable $X$ is given by,
$$
\mu := E(X) = 
\begin{cases}
\displaystyle{\sum^\infty_{i=1}x_ip(x_i)} & \text{if $X$ is discrete,} \\[2ex]
\displaystyle{\int^{\infty}_{-\infty}xf(x)dx}   & \text{if $X$ is continuous.}
\end{cases}
$$

### 2.3.2 Expectation of Function of a Random Variable

The mathematical expectation of a function $g(X)$ of a random variable $X$ can be calculated by,

$$
E[g(X)] = 
\begin{cases}
\displaystyle{\sum^\infty_{i=1}g(x_i)p(x_i)}   & \text{if $X$ is discrete,} \\[2ex]
\displaystyle{\int^\infty_{-\infty}g(x)f(x)dx} & \text{if $X$ is continuous.}
\end{cases}
$$

---

The mathematical expectation $E(x)$ has the following properties,

1. $E(c)=c.$
2. Suppose that $g(X)$ is a function of the random variable $X$. Then for all constants $a$ and $b$,

$$
E[ag(X) + b] = aE[g(X)] + b.
$$

​	Specially, if $g(X)=X$, then,
$$
E(aX+b)=aE(X)+b.
$$

### 2.3.3 Variance of a Random Variable

The **variance** of a random variable $X$ is defined by,
$$
\sigma^2 \equiv E[(X-E(X))^2] = Var(X) = 
\begin{cases}
\displaystyle{\sum^\infty_{i=1}(x_i-\mu)^2p(x_i)} & \text{if $X$ is discrete,} \\[2ex]
\displaystyle{\int^\infty_{-\infty}(x-\mu)^2f(x)} & \text{if $X$ is continuous.} \\[2ex]
\end{cases}
$$
Where $\mu = E(X)$.

---

The **standard deviation** of a random variable $X$ is given by,
$$
\sigma = SD(X) = \sqrt{Var(X)}.
$$

---

$$
Var(X)=E(X^2)-[E(X)]^2.  \\[2ex]
Var(X)=\int^\infty_{-\infty}x^2f(x)dx-\left(\int^\infty_{-\infty} xf(x)dx \right)^2
$$

---

The variance $Var(x)$ has the following properties,

1. $Var(c)=0.$
2. $Var(aX+b) = a^2Var(X)$.

### 2.3.4 The Application of Expectation and Variation

**Markov's inequality** : If $X$ is a random variable that takes only nonnegative values, then for any value $\varepsilon > 0$,
$$
P(X \leqslant \varepsilon) \geqslant \frac{E(X)} {\varepsilon}.
$$
**Chebyshev's inequality** : If $X$ is a random variable with mean $\mu$ abd variance $\sigma^2$, then, for any value $\varepsilon > 0$,
$$
P(|X-\mu| \geqslant \varepsilon) \leqslant \frac{\sigma^2} {\varepsilon^2}.
$$

## 2.4 Discrete Random Variables

### 2.4.1 Binomial Distribution with Parameters $n$ and $p$

$$
P(X=1)=p, P(X=0)=1-p, 0<p<1.
$$

We call $X$ a **Bernoulli random variable**. We can say $X$ has **Bernoulli distribution with parameter** $p$. The p.f. of $X$ is written as follows,
$$
p(x) = 
\begin{cases}
1-p & \text{if $x=0$}, \\[2ex]
p   & \text{if $x=1$}.
\end{cases}
$$
The mean and variance of $X$ are
$$
E(X)=p, \qquad Var(X)=p(1-p).
$$

---

The random variable $X$ that counts the number of successes, $k$ , in the $n$ Bernoulli trials is said to have a **binomial distribution with parameters $n$ and** $p$, written as $X \sim B(n,p)$.
$$
p(x) = \begin{pmatrix} n \\ k \end{pmatrix} p^xq^{(n-x)} \qquad \text{for $x=0,1,\dotsb,n,$}
$$
where $q=1-p$.

---

Suppose that $X$ is a random variable which has binomial distribution with paramaeters $n$ and $p$. Then we have
$$
E(X)=np \quad and \quad Var(X)=np(1-p).
$$

---

**Poisson limit theorem** : Suppose that $\lambda$ is a constant and $n$ is a positive integer. If that $lim_{n\to \infty}np_n=\lambda$, then we have,
$$
\displaystyle{
\lim_{n\to+\infty} 
\begin{pmatrix} n \\ x \end{pmatrix} 
p^x_n(1-p_n)^n-x=e^{-\lambda} 
\frac{\lambda^x} {x!}
}
$$
for any fixed nonnegative integer $x$.

### 2.4.2 Geometric Distribution

Let $X$ be the random variable that counts the number of Bernoulli trials needed to obtain a first success. We say that $X$ has a **geometric distribution with parameter** $p$, where $p$ is the probability of success on any trial. We write that $X \sim G(p)$ (or $Geom(p)$). The p.f. of $X$ is,
$$
p(x)=q^{x-1}p
$$

for $x=1,2,\dotsb,$ where $q = 1-p$.

---

Suppose that $X$ is a random variable which has a geometric distribution with parameters $p$. Then we have,
$$
E(X)=\frac1p \quad and \quad Var(X)=\frac{1-p} {p^2}.
$$

### 2.4.3 Poisson Distribution with Parameters $\lambda$

We say that the discrete random variable $X$ whose probability function is given by equation $p(x)=\displaystyle\frac{e^{-\lambda}\lambda^x} {x!}  \ for \ x=0,1,\dotsb$ has a **Poisson distribution with parameter** $\lambda>0$. We write that $X \sim Poi(\lambda)$.

---

Suppose that $X$ is a random variable which has Poisson distribution with parameter $\lambda$. Then we have, 
$$
E(X)=Var(X)=\lambda.
$$

## 2.5 Contiuous Random Variables

### 2.5.1 Uniform Distribution

The distribution of the random $X$ is called the **uniform distribution** of the interval $[a,b]$ if the p.d.f. of $X$ is,
$$
f(x)=
\begin{cases}
\displaystyle{\frac1{b-a} } & \text{for } a\leqslant x \leqslant b, \\[2ex]
0 & otherwise.
\end{cases}
$$

We write that by $X \sim U(a,b)$.

---

The corresponding d.f. of $X$ is,

$$
F(x)=
\begin{cases}
0 & \text{for }x<a, \\[2ex]
\displaystyle\frac{x-a} {b-a} & \text{for } a\leqslant x\leqslant b, \\[2ex]
1 & \text{for } x \geqslant b.
\end{cases}
$$

---

Suppose that $X$ is a random variable which has uniform distribution of the interval $[a,b]$. Then we have,

$$
E(X)=\frac{a+b} {2} \quad and \quad Var(X)=\frac{(b-a)^2} {12}.
$$

### 2.5.2 Exponential Distribution

Let $X$ be a continuous random variable whose density function is of the form,
$$
f(x) =
\begin{cases}
\lambda e ^{-\lambda x} & for \ x>0, \\[2ex]
0 & for \ x \leqslant 0,
\end{cases}
$$
where $\lambda > 0$ is the scale parameter. We say that $X$ follows an **exponential distribution** with parameter $\lambda$. We write that $X \sim Exp(\lambda)$. The case where $\lambda=1$ is called the standard exponential distribution.

---

The corresponding d.f. of $X$ is,
$$
F(x)=
\begin{cases}
1-e ^{-\lambda x} & for \ x\geqslant0, \\[2ex]
0 & for \ x < 0.
\end{cases}
$$

---

Suppose that $X$ is a random variable which has exponential distribution with parameter $\lambda$. Then we have,
$$
E(X)=\frac1\lambda \quad and \quad Var(X)=\frac1{\lambda^2}
$$

### 2.5.3 Normal Distribution

Let $X$ be a continuous random variable that can take any real value. if its density function is given by,
$$
\displaystyle f(x)=\frac1{\sqrt{2\pi}\sigma}e^\frac{-(x-\mu)^2} {2\sigma^2} \ for \ -\infty<x<\infty,
$$
then we say that $X$ has a normal (or Gaussian) distribution with parameters $\mu$ and $\sigma^2$, where $\mu \in R$ and $\sigma > 0$. We write that $X \sim N(\mu,\sigma^2)$.

---

The corresponding d.f. of $X$ is,
$$
F(x)=\frac 1{\sqrt{2\pi}\sigma} \int^x_{-\infty}e^\frac{-(t-\mu)^2} {2\sigma^2}  dt.
$$

---

Suppose that $X \sim N(\mu,\sigma^2)$. Then we have,
$$
E(X)= \mu \quad and \quad Var(X)=\sigma^2.
$$

---

The normal distribution with parameter values $\mu=0$ and $\sigma = 1$ is called the **standard normall distribution** and it will be denoted by $Z$. The p.d.f. of $Z$ is,
$$
\phi(z)=\frac1{\sqrt{2\pi} }e^\frac{-z^2} {2} \ for \ -\infty<z<\infty,
$$
The corresponding d.f. of $Z$ is,
$$
\Phi(z):=P(Z \leqslant z)= \int^z_{-\infty}\phi(z)dy.
$$

---

Proposition of the standard normall distribution,

1. $\Phi(x)+\Phi(-x)=1$.
2. $\displaystyle \Phi(0)=\frac12.$
3. If $X \sim N(\mu,\sigma^2)$, then the d.f. $F(x)$ of $X$ is given by $\displaystyle \Phi(\frac{x-\mu} {\sigma})$, i.e.,

$$
F(x)=\displaystyle \Phi(\frac{x-\mu} {\sigma}).
$$

## 2.6 Review

| Distribution |                                            p.f. or p.d.f.                                             |      Parameters      |              Mean               |               Variance               |
| :----------: | :---------------------------------------------------------------------------------------------------: | :------------------: | :-----------------------------: | :----------------------------------: |
|  Bernoulli   |                                     $p(x)=p^x(1-p)^{1-x}, x=0,1$                                      |         $p$          |               $p$               |                 $pq$                 |
|   Binomial   |            $ p(x) = \begin{pmatrix} n \\ k \end{pmatrix} p^x(1-p)^{n-x} \ x=0,1,\dotsb,n$             |     $n $ and $p$     |              $np$               |              $np(1-p)$               |
|  Geometric   |                                $ p(x)=(1-p)^{x-1} · p, \ x=1,2,\dotsb$                                |         $p$          |     $\displaystyle \frac1p$     |  $\displaystyle \frac{1-p} {p^2} $   |
|   Poisson    |              $p(x)=\displaystyle\frac{e^{-\lambda}\lambda^x} {x!}  \ for \ x=0,1,\dotsb$              |      $\lambda$       |            $\lambda$            |              $\lambda$               |
|   Uniform    |                   $ f(x)=\displaystyle{\frac1{b-a} } \ , a\leqslant x \leqslant b$                    |       $[a,b]$        |   $\displaystyle \frac{a+b}2$   | $\displaystyle \frac{(b-a)^2} {12} $ |
| Exponential  |                           $f(x)= \lambda e ^{-\lambda x} \ ,\ x\geqslant0$                            |      $\lambda$       | $\displaystyle\frac1{\lambda} $ |  $\displaystyle\frac1{\lambda^2} $   |
|    Normal    | $ \displaystyle f(x)=\frac1{\sqrt{2\pi}\sigma}e^\frac{-(x-\mu)^2} {2\sigma^2} \ , \ -\infty<x<\infty$ | $\mu$ and $\sigma^2$ |              $\mu$              |               $\sigma$               |

# Chapter 3 Random  Vectors

## 3.1 Random Vectors and Joint Distributions

### 3.1.1 Random Vectors and Joint Distributions

The **joint distribution function (joint d.f.)** of $X$ and $Y$ is defined by,
$$
F(x,y)=P(X \leqslant x, Y \leqslant y), -\infty <x, y<\infty.
$$

---

The joint distribution function $F(x,y)$ is such that,

1. For any $x_1<x_2$, $F(x_1,y)<F(x_2,y)$; for any $y_1<y_2$, $F(x,y_1)<F(x,y_2)$.
2. $F(-\infty,y)=0$, $F(x,-\infty)=0$, $F(\infty,\infty)=1$.
3. $\displaystyle \lim_{x \to x_0} F(x,y)=F(x_0,y)$,  $\displaystyle \lim_{y \to y_0} F(x,y)=F(x,y_0)$.

 ### 3.1.2 Discrete Random Vectors

For discrete bivariate random vectors, we always use the **joint probability function** (joint p.f.),
$$
p(x,y):= P(\{X = x\} \ \cap \ \{ Y = y\} ) \equiv P(X=x, Y=y)
$$
of the discrete random vector $(X,Y)$, whose possible values form a set of points $(x_j,y_k)$ in the plane, where $p(x,y)$ has the following properties,

1. $p(x_j,y_k) \geqslant 0, \forall (x_j,y_k) \in R \times R$.
2. $\displaystyle \sum^\infty_{j=1}\sum^\infty_{k=1}p(x_j,y_k)=1$.

---

We can describe **joint probability table** by suing a tabular.

| $Y    \setminus    X$ |    $x_1$     |    $x_2$     | $\dotsb$ |  $p_Y(y)$  |
| :-------------------: | :----------: | :----------: | :------: | :--------: |
|         $y_1$         | $p(x_1,y_1)$ | $p(x_2,y_1)$ | $\dotsb$ | $p_Y(y_1)$ |
|         $y_2$         | $p(x_1,y_2)$ | $p(x_2,y_2)$ | $\dotsb$ | $p_Y(y_2)$ |
|       $\dotsb$        |   $\dotsb$   |   $\dotsb$   | $\dotsb$ |  $\dotsb$  |
|       $p_X(x)$        |  $p_X(x_1)$  |  $p_X(x_2)$  | $\dotsb$ |     1      |

### 3.1.3 Continuous Random Vectors

 Let $X$ and $Y$ be two continuous random variables. The random variables $X$ and $Y$ are called **(jointly) continuous** if the joint distribution function $F(x,y)$ can be expressed by the **joint probablity density function** (joint p.d.f.) $f(x,y)$ as,
$$
F(x,y)=\int_{-\infty}^y\int_{-\infty}^xf(u,v)dudv.
$$
The joint p.d.f. $f(x,y)$ has the following properties,

1. $f(x,y)\geqslant0$ for any point $(x,y)\in R \times R$.
2. $\displaystyle \int_{-\infty}^\infty\int_{-\infty}^\infty f(x,y)dxdy=1$.

---

The **marginal probability density functions** of $X$ and $Y$ are defined by,
$$
f_X(x)= \int_{-\infty}^\infty f(x,y)dy \quad and \quad f_Y(y)= \int_{-\infty}^\infty f(x,y)dx.
$$

---

$$
P((X<,Y)\in A)=\frac{L(A)} {ab}.
$$

We call $(X,Y)$ has uniform distribution on the domain $D$, denoted by $(X,Y) \sim U(D)$.

## 3.2 Independence of Random Variable

Two **random variable $X$ and $Y$ are said to be independent** if for every pair of $x$ and $y$,
$$
F(x,y)=F_X(x)F_Y(y).
$$
We denoted it by $X \bot Y$.

---

Two **random variable $X$ and $Y$ are said to be independent** if for every pair of $x$ and $y$,
$$
\begin{cases}
p(x,y)=p_X(x) · p_Y(y) \quad \text{when X and Y are discrete,} \\[2ex]
f(x,y)=f_X(x) · f_Y(y) \quad \text{when X and Y are continuous.}
\end{cases}
$$
If the equations above are not satisfied for all $(x,y)$, then $X$ and $Y$ are said to be dependent.

---

Let $a$, $b$, $c$ and $d$ be given values such that $-\infty \leqslant a < b \leqslant +\infty $ and $-\infty \leqslant c < d \leqslant +\infty $, and let $S$ be a rectangle in the xy-plane,
$$
S=\{(x,y)|a\leqslant x \leqslant b \ and \ c\leqslant y \leqslant d\}.
$$
Suppose that $f(x,y)=0$ for every point $(x,y)$ outside $S$. Then the continuous (discrete) random variable $X$ and $Y$ are indepent if and only if their joint p.d.f. (or p.f.) can be expressed as,
$$
f(x,y) = h(x)g(y).
$$
for all points in $S$.

---

Let $X$ and $Y$ be two independent random variables. Then for any two real functions $g(·)$ and $h(·)$， $g(X)$ and $h(Y)$ are independent.

## 3.3 Conditional Distribution

### <u>Discrete Case</u>

If $X$ and $Y$ are discrete random variables, then it is natural to define the **conditional probability function of $X$ given that $Y=y$**, by,
$$
p_{X|Y}(x|y) = P(X=x|Y=y)= \frac{P(X=x,Y=y)} {P(Y=y)}=\frac{p(x,y)} {p_Y(y)}
$$
for all values of $y$ such that $p_Y(y)>0$. 

If $X$ and $Y$ are discrete random variables, then it is natural to define the **conditional probability function of $Y$ given that $x=x$**, by,
$$
p_{Y|X}(y|x) = P(Y=y|X=x)= \frac{P(X=x,Y=y)} {P(X=x)}=\frac{p(x,y)} {p_X(x)}
$$
for all values of $x$ such that $p_X(x)>0$. 

### <u>Continuous Case</u>

If $X$ and $Y$ have joint p.d.f. $f(x,y)$, then the **conditional probability density function of $X$ given** $Y=y$ is given by,
$$
f_{X|Y}(x|y)=
\begin{cases}
\displaystyle \frac{f(x,y)} {f_Y(y)} & if \ 0<f_Y(y)< +\infty, \\[2ex]
\displaystyle 0 & elsewhere.
\end{cases}
$$
If $X$ and $Y$ have joint p.d.f. $f(x,y)$, then the **conditional probability density function of $Y$ given** $X=x$ is given by,
$$
f_{Y|X}(y|x)=
\begin{cases}
\displaystyle \frac{f(x,y)} {f_X(x)} & if \ 0<f_X(x)< +\infty, \\[2ex]
\displaystyle 0 & elsewhere.
\end{cases}
$$

## 3.4 One Function of Two Random Variables

### <u>Discrete Case</u>

Make sure what values $Z$ can take according to all possible values of $(X,Y)$.

---

If $X$ and $Y$ are independent discrete random variables, then $X+Y$ has probability function,
$$
p_{X+Y}(n)=\sum_np_X(x)p_Y(n-x).
$$
The function $p_{X+Y} $ is called the convolution of $p_X$ and $p_Y$, and is written as,
$$
p_{X+Y} = p_X*p_Y
$$

### <u>Continuous Case</u>

1. **The case of** $X+Y$

   If $X$ and $Y$ are independent, then,
   $$
   f_{X+Y}(z) = \int^{\infty}_{-\infty}f_X(x)f_Y(z-x)dx, \quad -\infty<z<\infty
   $$
   The equation above can be written as,
   $$
   f_{X+Y}=f_X · f_Y
   $$
   If $X$ and $Y$ are nonnegative independent random variables, then,
   $$
   f_{X+Y}(z)=
   \begin{cases}
   \displaystyle \int^z_0 f_X(x)f_Y(z-x)dx & 0<z<\infty, \\[2ex]
   0 & elsewhere.
   \end{cases}
   $$

   ---

   If $X \sim N(\mu_1, \sigma_1^2)$, $Y \sim N(\mu_2, \sigma_2^2)$ and $X \bot Y$, then,
   $$
   aX + bY + c \sim N(a\mu_1 + b\mu_2 + c, a^2\sigma_1^2 + b^2\sigma_2^2),
   $$
   where $a$, $b$ are constants.

2. **The case of** $max(X,Y)$

   For $Z=max(X,Y)$ and $X \bot Y$, we have,
   $$
   F_Z(z)=[F(z)]^2. \\[2ex]
   f_Z(z)=2F(z)f(z)
   $$

3. **The case of** $min(X,Y)$

   For $W=min(X,Y)$ and $X \bot Y$, we have,
   $$
   F_W=1-[1-F(w)]^2. \\[2ex]
   f_W(w)=F_W^\prime (w)=2[1-F(w)]f(w).
   $$







## 3.5 Transformation of Two Random Variables

I have no idea.

## 3.6 Numerical Characteristics of Random Variables

### 3.6.1 Expectation of Sums and Products

Let $X$ and $Y$ be jointly distributed random variables with p.f. $p(x,y)$ or p.d.f. $f(x,y)$ according to whether the variables are discrete or continuous. Then the expected value of a function $h(X,Y)$, denoted by $E[h(X,Y)]$, is given by,
$$
E[h(X,Y)]=
\begin{cases}
\displaystyle \sum_x\sum_y h(x,y) · p(x,y) & \text{if $X$ and $Y$ are discrete,} \\[2ex]
\displaystyle \int^\infty_{-\infty} \int^\infty_{-\infty} h(x,y) · f(x,y) dxdy & \text{if $X$ and $Y$ are continuous.} 
\end{cases}
$$

---

Suppose that $E(X)$ and $E(Y)$ are noth finite, we have,
$$
E(X+Y)=E(X)+E(Y).
$$

---

If $X$ and $Y$ are two independent random variables, then,
$$
E(XY)=E(X)E(Y).
$$
And for any functions $g$ and $h$,
$$
E[g(X)h(Y)]=E[g(X)]E[h(Y)].
$$

---

**The Cauchy-Schwarz inequality** : Let $X$ and $Y$ be jointly distributed random variables having finite second moments. Then,
$$
[E(XY)]^2 \leqslant E(X^2)E(Y^2).
$$

---

Let $X$ and $Y$ be two independent random variables. Then,
$$
Var(X+Y) = Var(X) + Var(Y). \\[2ex]
Var(aX+bY+c)=a^2Var(X)+b^2Var(Y).
$$

### 3.6.2 Covariance and Correlation

The **covariance** between two random variables $X$ and $Y$ is,
$$
Cov(X,Y)= E(XY)-E(X)E(Y).
$$

---

For jointly distributed random variables $X$ and $Y$, and constants $a, \ b$, we have,

1. $Cov(X,Y) = Cov(Y,X).$
2. $Cov(X,X)=E(X^2)-[E(X)]^2-[E(X)]^2=Var(X)$.
3. $Cov(aX,bY) = abCov(X,Y).$
4. $Cov(X+Y,Z)=Cov(X,Z)+Cov(Y,Z).$

---

The correlation coefficient of $X$ and $Y$, denoted by $\rho(X,Y)$, $\rho_XY$, or just $\rho$, is defined by,
$$
\rho(X,Y)=\frac{Cov(X,Y)} {\sigma_X· \sigma_Y},
$$
where $\sigma_X$ and $\sigma_Y$ are standard deviation of $X$ and $Y$ respectively.

## 3.7 Multivariate Distributions

### 3.7.1 Distribution Functions of Multiple Random Vectors 

### 3.7.2 Numerical Characteristics of Random Vectors

### 3.7.3 Multiple Normal Distribution

# Chapter 4 Sequences of Random Variables

## 4.1 Family of Distribution Functions and Numerical Characteristics

Let $\Omega$ be a sample space. We say that $\{X_n(\omega),\omega\in \Omega\}_{n=1}^\infty$ is a **sequence of random variables** defined on the sample space $\Omega$ if all the random variables $X_n$ belonging to the sequence $\{X_n\}_{n=1}^\infty$ are functions from $\Omega$ to $R$. We usually denote the sequence of random variable by $\{X_n\}_{n=1}^\infty$. 

---

Suppose that $\{X_n\}_{n=1}^\infty$ is a random sequence. The **family of distribution functions** of $\{X_n\}_{n=1}^\infty$ is defined by,
$$
\{F(x_1, x_2, \dotsb, x_k;n_1, n_2, \dotsb, n_k), \ \forall k, \ \forall n_1=1,2,\dotsb, \ i=1,2,\dotsb,k\}.
$$

We say that $\{X_n\}_{n=1}^\infty$ is a **sequence of identically distributed random variables** if any two elements of the sequence have the same distribution function:
$$
\forall x \in R, \forall i,j\in \N, F_i(x)=F_j(x).
$$
We say that $\{X_n\}_{n=1}^\infty$ is a **sequence of independent and identically distributed random variables** (or an **IDD** sequence of random variables), if $\{X_n\}_{x=1}^\infty$  is both a sequence of independent random variables and a sequence of identically distributed random variables.

## 4.2 Chebyshev's Inequality and the Law of Large Numbers

**Markov's inequality** : If $X$ is a random variable that takes only nonnegative values, then for any value $a>0$,
$$
P\{X\geqslant a\} \leqslant \frac{E[X]} {a}.
$$

---

**Chebyshev's inequality** : If $X$ is a random variable with finite mean $\mu$ and variance $\sigma^2$, then for any value $k>0$,
$$
P\{|X-\mu|\geqslant k\}\leqslant \frac{\sigma^2} {k^2}.
$$

---

If $Var(X)=0$, then $P\{X=E[X]\}=1.$

---

**The weak law of large numbers** : Let $X_1,X_2,\dotsb$ be a sequence of independent and identically distributed random variables and $S_n=X_1+X_2+\dotsb+X_n$. Then, for any $\varepsilon >0$,
$$
\displaystyle{\lim_{n\to\infty} }P \left\{ \left| \frac{S_n}n-E\left(\frac{S_n}n\right)\right| \geqslant \varepsilon\right\} =0.
$$
Use $\displaystyle \overline{X}_n = \frac{S_n}n$, for any $\varepsilon >0$,
$$
\displaystyle{\lim_{n\to\infty} }P \{ | \overline{X}_n-E(\overline{X}_n)| \geqslant \varepsilon\} =0.
$$

---

**The strong law of large numbers** : for any $\varepsilon >0$,
$$
P ( \lim_{n\to\infty}|\overline X_n-E(\overline X_n)|=0)=1.
$$

---

**Chebyshev's law of large number** : 

---

**Bernoulli's law of large numbers** : Suppose the $n_A$ is the number of success in $n$ Bernoulli trials with probability $p$ for success. The for any $\varepsilon > 0$,
$$
P \left( \left| \frac{n_A}n -p \right|<\varepsilon \right) \to 1 \quad as \quad n\to \infty.
$$

## 4.3 The Central Limit Theorem

We have,
$$
E(S_n)=n\mu. \\[2ex]
\sigma_{S_n} = \sqrt{n}\sigma.
$$

---

The standardized sum of $S_n$ is given by,
$$
S_n^*=\frac{S_n-n\mu} {\sigma\sqrt{n} }.
$$
$S_n^*$ always has expected value $0$ and variance $1$.

---

**De Movire-laplace central limit theorem** : Suppose that $X \sim B(n,p)$. Then the distribution of
$$
\displaystyle \frac{X-np} {\sqrt{np(1-p)} }
$$
Tends to the standard normal as $n \to \infty$. That is,
$$
\lim_{n\to \infty}P \left( \displaystyle \frac{X-np} {\sqrt{np(1-p)} } \leqslant x\right)=\frac1{\sqrt{2\pi} }\int_{-\infty}^{x}e^{-s^2/2}ds=\Phi(x).
$$

# Chapter 5 Introduction to Stochastic Processes

## 5.1 Definition and Classification

A **stochastic process** is a family of time functions depending on the parameter $\omega$.

A stochastic process $X(t)$ is a function of $t$ and $\omega$, $\{X(t,\omega), t\in T\} $.

---

**State Space $S$**

This is the space in which the possible values of each $X_t$ lie.

In the case that $S=\{1,2,\dotsb\},$ we refer to the process at hand as integer valued, or alternately as a discrete state process.

If $S=(-\infty, \infty)$, then we call $X_t$ a real-valued stochastic process.

---

**Classical Types of stochastic Process**

1. **Stationary Processes**
2. **Markov Processes**
3. **Process with Stationary Independent Increments**

## 5.2 The Distribution Family and the Moment Functions

For a specific $t$, $X_t$ is a random variable with distribution,
$$
F(x;t)=P\{X_t \leqslant x\}.
$$
The distribution function of this random variable, in general depend on $t$. The function $F(x;t)$ is called the first-order distribution function of the process $X_t$. It's derivative with respect to $x$,
$$
f(x,t)=\frac{\partial {F(x,t)} } {\partial x}
$$
is the first-order density of $X_t$.

The second-order distribution of the process $X_t$ is the joint distribution
$$
f(x_1,x_2;t_1,t_2)=P(X_{t_1} \leqslant x_1, X_{t_2}\leqslant x_2).
$$
The corresponding density equals
$$
\displaystyle f(x_1,x_2;t_1,t_2)=\frac{\partial^2F(x_1,x_2;t_1,t_2)} {\partial x_1 \partial x_2}.
$$

---

**Two-dimensional process** : $\{(X_t,Y_t), t\in T\} $.

---

**The complex process** : $Z_t=X_t+iY_t$.

## 5.3 The Moments of the Stochastic Processes

### 5.3.1 Mean, Autocorrelation and Autocovariance

If $X_t$ is a real stochastic process, then its mean function is,
$$
\mu_X(t)=E(X_t), t\in T.
$$
The variance function is,
$$
\sigma^2_X(t)=Var(X_t).
$$
The autocorrelation function is,
$$
R_X(t_1,t_2)=R_{XX}(t_1,t_2)=E(X_{t_1}X_{t_2}).
$$
<待续>

### 5.3.2 Cross-correlation and Cross-covariance

If two stochastic processes are independent, then they are uncorrelated.

## 5.4 Stochastic Analysis

**Continuity in Mean** : A stochastic process $X_t$ is **continuous in mean square** at $t_0$ if,
$$
\displaystyle \lim_{\varepsilon\to 0} E\left[ (X_{t_0+\varepsilon }-X_{t_0})^2 \right]=0
$$

---

If $X_t$ is a mean square continuous process, then its mean is also continuous (but not mean square continuous), i.e.
$$
\displaystyle \lim_{\varepsilon \to 0}\mu_X(t+\varepsilon) = \mu_X(t).
$$

---

**Hint** 

$\displaystyle cos(\alpha)cos(\beta)=\frac12 (cos(\alpha+\beta)+cos(\alpha-\beta))$
