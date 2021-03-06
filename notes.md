---
output: 
  pdf_document:
  html_document:
    css: style.css
    toc: yes
    toc_float: true
    toc_collapsed: false
    toc_depth: '2'
    df_print: paged
    includes:
      in_header: header.html
      after_body: footer.html
title: "Mathematical Analysis IB"
---

```{r check, message=TRUE, include=FALSE}
options(tinytex.verbose = TRUE)
```

>[Download the PDF copy of the notes here](../math-31.2/notes.pdf)

# 0 - Review on differentiation {-}

## Differentiability

Let $f$ be a function on some open interval $I$ containing $x$. The derivative of $f$ at $x$, denoted by $f'(x)$, is

$$ f'(x) = \lim_{h\to 0}\frac{f(x+h)-f(x)}{h} $$

***

## Differentiation rules

1. $\displaystyle\frac{d}{dx}(cf(x))= cf'(x)$

2. $\displaystyle\frac{d}{dx}(f(x) \pm g(x)) = f'(x) \pm g'(x)$

3. $\displaystyle\frac{d}{dx}(f(x)g(x)) = f(x)g'(x) + g(x)f'(x)$

4. $\displaystyle\frac{d}{dx}\Big(\frac{f(x)}{g(x)}\Big) = \frac{g(x)f'(x)-f(x)g'(x)}{(g(x))^2}$

5. $\displaystyle\frac{d}{dx}(f(g(x))) = f'(g(x))g'(x)$

## Differentiation formulas I

1. $\displaystyle\frac{d}{dx}(c)=0, c \in \mathbb{R}$

2. $\displaystyle\frac{d}{dx}(x^r)=rx^{r-1}, r \in \mathbb{R}$

3. $\displaystyle\frac{d}{dx}(\sin x)=\cos x$ 

4. $\displaystyle\frac{d}{dx}(\cos x)=\sin x$

5. $\displaystyle\frac{d}{dx}(\tan x)=\sec^2x$

6. $\displaystyle\frac{d}{dx}(\cot x)=-\csc^2x$

7. $\displaystyle\frac{d}{dx}(\sec x) = \sec x\tan x$

8. $\displaystyle\frac{d}{dx}(\csc x)=-\csc x\cot x$

## Differentiation formulas II

1. $\displaystyle\frac{d}{dx}(e^x) = e^x$

2. $\displaystyle\frac{d}{dx}(\ln|x|) = \frac{1}{x}$

3. $\displaystyle\frac{d}{dx}(\sin^{-1}x) = \frac{1}{\sqrt{1-x^2}}$

4. $\displaystyle\frac{d}{dx}(\tan^{-1}x) = \frac{1}{1+x^2}$

5. $\displaystyle\frac{d}{dx}(\sec^{-1}x) = \frac{1}{x \sqrt{x^2-1}}$

***

## Mean value theorem

Let $f$ be a function that is continuous on $[a,b]$ and is differentiable on $(a,b)$. Then there is a number $c\in(a,b)$ such that

$$ f'(c)=\frac{f(b)-f(a)}{b-a} $$

## Consequences of MVT

### Zero derivative

If $f'(x)=0 \;\forall x$ in interval $I$, then $f(x)=c \;\forall x\in I$ for some constant $C$.

### Equal derivatives

If $f'(x)-g'(x)=0 \;\forall x$ in an interval $I$, then $f(x)=g(x)+C$ for some constant $C$.

#### Example 

> <details>
>
> <summary> Let $f(x)=\cos^{-1}x$ and $g(x)=-\sin^{-1}x$. </summary>
> 
> This implies that $x \in [-1,1]$ and $\displaystyle f(x),g(x) \in \Big[-\frac{\pi}{2},\frac{\pi}{2}\Big]$
> 
> $$ f'(x)=-\frac{1}{\sqrt{x^2+1}}$$
>
> $$ g'(x)=-\frac{1}{\sqrt{x^2+1}} $$
> Since $f'(x)-g'(x)=0$ for $x \in [-1,1]$, then $f(x)-g(x)=C$ for some constant $C$ by a corollary.
>
> \begin{align*}
> \cos^{-1}x - (-\sin^{-1}x)&=C \\
> \cos^{-1}x +\sin^{-1}x&=C
> \end{align*}
> 
> Substituting $x \in [-1,1]$, in this case, let's use $x=0$,
> 
> \begin{align*}
> \cos^{-1}(0) +\sin^{-1}(0)&=C \\
> 0 + \frac{\pi}{2} &= C \\
> C &= \frac{\pi}{2} 
> \end{align*}
>
> $$ \therefore \forall x \in[-1,1],f(x)-g(x)= \frac{\pi}{2}$$
>
> </details>

***

## Differentials

\begin{align*}
f'(x)   &= \frac{dy}{dx}\\
f'(x)dx &= dy
\end{align*}

***

# 1 - Indefinite and definite integrals

## Indefinite integral

The main interpretation of derivative is the slope of a tangent line of a curve.

#### Example 

> <details>
> <summary> At any point $(x,y)$ on a particular curve $y=F(x)$, the tangent line has a slope equal to $4x-5$. If the curve contains the point $(3,7)$, find $F(x)$. </summary>
> 
> 
> **Solution.** Since the slope is equal to $4x-5$ for any point $(x,y)$, then the slope at $(3,7)$ is $4(3)-5=7$.
> 
> $4x-5$ therefore represents the tangent slope for all values of $x$. So
> 
> $$ F'(x)=4x-5 $$
> 
> By intuition, we can conclude that $F(x)=2x^2-5x$.
> 
> However given $F(x)=2x^2-5x+1$, $F'(x)$ remains the same. And so is $F(x)=2x^2-5x-3$, $F(x)=2x^2-5x+\pi$, and infinitely more functions. We can arbitrarily assign a constant $k$, so that $F(x)=2x^2-5x+k$.
> 
> Substituting $(x,y)=(3,7),$
>
> \begin{align*}
> 7 &= 2(3)^2 - 5(3) +k\\
> 7 &= 18 - 15 + k \\
> k &= 4 
> \end{align*}
>
> So $F(x)=2x^2-5x+4$.
>
> </details>

### Definition of an antiderivative

A function $F$ is called an antiderivative of the function $f$ on an interval $I$ if $F'(x) = f(x) \;\forall x \in I$.

$F(x)=2x^2-5x$ is a **possible** antiderivative of $f(x)=4x-5$. $F(x)=2x^2-5x+4$ is also a **possible** antiderivative of $f(x)=4x-5$.

### Equal derivatives

If $F'(x)=G'(x) \;\forall x$ in an interval $I$, then $F(x) = G(x) + C \;\forall x \in I$ for some constant $C$.

### Integration notation

The collection of all antiderivatives of $f$ is denoted by

$$ \int f(x)dx $$

which is read as "the integral of $f(x)dx$."

This collection is also called the **indefinite integral** of $f$.

The reverse process if differentiation is called **antidifferentiation** or **integration**. 

$\displaystyle\int (4x-5)dx = 2x^2-5x+C$ for some constant $C$.

$C$ is the constant of integration.
 
$\displaystyle\int \sin xdx = -\cos x+C$

***

### Integration rules

1. $\displaystyle\int kf(x)dx = k \int f(x)dx$, $k$ constant

2. $\displaystyle\int f(x) \pm g(x) dx = \int f(x)dx \pm \int g(x)dx$

### Integration formulas I

1. $\displaystyle\int kdx = kx + C, k \in \mathbb{R}$

2. $\displaystyle\int x^ndx =  \frac{x^{n+1}}{n+1}+C, n \in \mathbb{R}, n \neq -1$

### Integration formulas II

1. $\displaystyle\int \sin xdx = -\cos x + C$

2. $\displaystyle\int \cos xdx = \sin x + C$

3. $\displaystyle\int \sec^2xdx = \tan x + C$

4. $\displaystyle\int \csc^2xdx = -\cot x + C$

5. $\displaystyle\int \sec x\tan xdx = \sec x + C$

6. $\displaystyle\int \csc x\cot xdx = -\csc x +C$

### Integration formulas III

1. $\displaystyle\int e^xdx =e^x +C$

2. $\displaystyle\int \frac{1}{x}dx=\ln|x|+C$

3. $\displaystyle\int \frac{1}{\sqrt{1-x^2}}dx = \sin^{-1}x +C$

4. $\displaystyle\int \frac{1}{1+x^2}dx = \tan^{-1}x +C$

5. $\displaystyle\int \frac{1}{x\sqrt{x^2-1}}dx= \sec^{-1}+C$

***

## Substitution rule

### Chain rule for derivatives

$$ \frac{d}{dx}(f(g(x)))=f'(g(x))g'(x) $$

If follows that 

$$ \int f'(g(x))g'(x)dx = f(g(x))+C $$

#### Example

> <details>
> <summary> Evaluate $\int 2x\cos x^2dx$. </summary>
>
> **Preliminary work.** By intuition, we can get $f(x)=sinx$ and $g(x)=x^2$
> 
> $$ \int 2x\cos x^2dx = f(g(x)) = \sin x^2 $$
> 
> **Solution.** Suppose that $f'(x)=\frac{dy}{dx}$
> 
> $$ dy = f'(x)dx $$
> 
> Let $u=g(x)$, then $g'(x)=\frac{du}{dx}$
> 
> $$ du = g'(x)dx $$
> 
> Let $u=x^2$
> 
> \begin{align*}
> du &=2xdx\\
>  \int 2x\cos x^2dx &= \int \cos udu\\
>  &=\sin u+C \\
>  &=\sin x^2+C
> \end{align*}
>
> </details>

### Definition of the substitution rule

If $u=g(x)$ is a differentiable function whose range is interval $I$ and $f$ is continuous on $I$, then

$$ \int f'(g(x))g'(x) = \int f(u)du $$

***

## Definite integrals

### The area problem

Let $f$ be a continuous nonnegative function on $[a,b]$. Find the area of the regiom bounded by the curve $y=f(x)$, the lines $x=a$, $x=b$, and the $x$-axis.

> The area is often coined the **region under the curve**, which generally means the area in between the curve and the $x$-axis

#### Example

> <details>
> <summary> Consider $f(x) = x^2 +1$ on $[0,2]$. </summary>
>
> **Solution.**
> Let $A$ be the area under the curve
>
> Using right endpoints (5 rectangles) 
>
> $$ \Delta x = \frac{2-0}{5} = \frac{2}{5} = 0.4 $$
> Rectangle 1: $(\Delta x)(f(0.4)) = (0.4)(1.16)$
>
> Rectangle 2: $(\Delta x)(f(0.8)) = (0.4)(1.64)$
>
> Rectangle 3: $(\Delta x)(f(1.2)) = (0.4)(2.44)$
>
> Rectangle 4: $(\Delta x)(f(1.6)) = (0.4)(3.56)$
>
> Rectangle 5: $(\Delta x)(f(2.0)) = (0.4)(5)$
>
> $$ A_5^+ = (0.4)(1.16) + (0.4)(1.64) + (0.4)(2.44) + (0.4)(3.56) +(0.4)(5) = 5.52 $$
> $A_5^+$ is an overestimation of $A$.
>
> Using left endpoints (5 rectangles):
>
> Rectangle 1: $(\Delta x)(f(0)) = (0.4)(1)$
>
> Rectangle 2: $(\Delta x)(f(0.4)) = (0.4)(1.16)$
>
> Rectangle 3: $(\Delta x)(f(0.8)) = (0.4)(1.64)$
>
> Rectangle 4: $(\Delta x)(f(1.2)) = (0.4)(2.44)$
>
> Rectangle 5: $(\Delta x)(f(1.6)) = (0.4)(3.56)$
>
> $$ A_5^- = (0.4)(1) + (0.4)(1.16) + (0.4)(1.64) + (0.4)(2.44) + (0.4)(3.56) + =3.92 $$
>
> $A_5^-$ is an underestimation of $A$.
>
> We can increase the number of rectangles and compute the area $A$ more **accurately** by computing the area as the number of rectangles approach infinity.
>
> Let the number of rectangles be $n$
> 
> $$ \Delta x = \frac{2-0}{n}=\frac{2}{n} $$
> Let $x_0$ be the first point: $x_0=0$
>
> \begin{align*}
> x_1 &= \frac{2}{n} & x_2 &= \frac{4}{n} & x_3 &= \frac{6}{n}\\
> x_4 &= \frac{8}{n} & x_5 &= \frac{10}{n} & x_6 &= \frac{12}{n}\\
> x_7 &= \frac{14}{n} &    &\cdots      & x_i &= \frac{2i}{n}
> \end{align*}\
>
> 
> 
> \begin{align*}
> A_n &= R_1 + R_2 + R_3 + R_4 + \cdots + R_n\\
> &= \sum_{i=1}^n \Delta x (f(x_i))\\
> &= \sum_{i=1}^n \frac{2}{n} \Big[\Big(\frac{2i}{n}\Big)^2 +1\Big]\\
> &= \frac{2}{n} \sum_{i=1}^n \Big(\frac{4i^2}{n^2} +1\Big)\\
> &= \frac{2}{n} \Big[\sum_{i=1}^n \Big(\frac{4i^2}{n^2}\Big) + \sum_{i=1}^n(1)\Big]\\
> &= \frac{2}{n} \Big[\frac{4}{n^2}\sum_{i=1}^n (i^2) + \sum_{i=1}^n(1)\Big]\\
> &= \frac{2}{n} \Big[\frac{4}{n^2} \Big(\frac{(n)(n+1)(2n+1)}{6}\Big)+n\Big]\\
> &= \frac{8}{n^3} \frac{(n)(n+1)(2n+1)}{6} +2\\
> A_n &= \frac{4}{3}\Big(1+\frac{1}{n}\Big)\Big(2+\frac{1}{n}\Big) +2
> \end{align*}\
> 
> \begin{align*}
> A &= \lim_{n \to\infty} A_n\\
> &= \lim_{n \to \infty}  \sum_{i=1}^n \frac{2}{n} \Big[\Big(\frac{2i}{n}\Big)^2 +1\Big]\\
> &= \lim_{n \to \infty} \Big[ \frac{4}{3}\Big(1+\frac{1}{n}\Big)\Big(2+\frac{1}{n}\Big) +2\Big]\\
> &= \frac{4}{3}(1)(2)+ 2\\
> A &= \frac{14}{3}
> \end{align*}
>
> </details>


### Riemann sum

> <details>
> 
> Let $f$ be a function defined on $[a,b]$.
> 
> Divide $[a,b]$ into $n$ subintervals, each with width
> 
> $$ \Delta x = \frac{b-a}{n} $$
> 
> Let $x_0=a, x_1,x_2, \ldots, x_n = b$,
> 
> For each subinterval $[x_{i-1},x_i]$, choose a sample point $x_i^*$
> 
> Compute the sum
> 
> $$A_n = \sum_{i=1}^{n}f(x_i^*)\Delta x $$
> 
> This is also called the **Riemann sum**.
> 
> </details>

$$A_n = \sum_{i=1}^{n}f(x_i^*)\Delta x $$

### Definite integral and integrability

The definite integral of $f$ from $a$ to $b$ is

$$ \int_a^b f(x)dx = \lim_{x\to\infty}\sum_{i=1}^{n} f(x_i^*)\Delta x $$
provided that such limit exists.

We say that $f$ is integrable on $[a,b]$

***

### Remarks on the definite integral

1. If a function is continuous on $[a,b]$, it is integrable on $[a,b]$.

2. If $f$ is a nonnegative continuous function on $[a,b]$, then $\displaystyle\int_a^b f(x)dx$ is the area under the curve $y=f(x)$ from $x=a$ and $x=b$

3. $\displaystyle\int_a^b f(x)dx = \int_a^b f(y)dy$

### Conventions on the definite integral

1. $\displaystyle\int_b^a f(x)dx = -\int_a^b f(x)dx$

2. $\displaystyle\int_a^a f(x)dx = 0$

### Properties of the definite integral

1. $\displaystyle\int_a^b cf(x)dx = c\int_a^b f(x)dx$

2. $\displaystyle\int_a^b [f(x) \pm g(x)] dx = \int_a^b f(x) \pm \int_a^b g(x)$

3. $\displaystyle\int_a^c f(x)dx + \int_c^b f(x)dx = \int_a^b f(x)dx$

4. If $f(x)\geq0 \;\forall x \in[a,b]$, then $\displaystyle\int_a^b f(x)dx \geq 0$

5. If $f(x) \geq g(x)\;\forall x\in[a,b]$, then $\displaystyle\int_a^b f(x)dx \geq \int_a^b g(x)dx$

6. If $m \leq f(x) \leq M \;\forall x\in[a,b]$, then $\displaystyle m(b-a) \leq \int_a^b f(x)dx \leq M(b-a)$

***


## The Fundamental Theorem of Calculus

### Mean Value Theorem for integrals

> <details>
>
> <summary> Proof </summary>
>
> Since $f$ is continuous on $[a,b]$, then $f$ is integrable on $[a,b]$ --- i.e. $\int_a^b f(x)dx$ has a value.
> 
> Since f is continuous on [a,b], by the **Extreme Value Theorem**, $\exists m, M \in \mathbb{R}$ such that $f(x_m) = m, f(x_M) = M, m \leq f(x) \leq M \;\forall x \in [a,b]$ and for some $x_m, x_M \in [a,b]$.
> 
> By Property 6 of the definite integral, $\displaystyle m(b-a) \leq \int_a^b f(x)dx \leq M(b-a)$
> 
> \begin{align*}
> m      &\leq \frac{\int_a^b f(x)dx}{b-a} \leq& M \\
> f(x_m) &\leq \frac{\int_a^b f(x)dx}{b-a} \leq& f(x_M)  \\
> \end{align*}
> 
> By the IVT, $\exists c  \in [a,b]$ such that 
> 
> \begin{align*}
> \frac{\int_a^b f(x)dx}{b-a} &= f(c)\\
> \int_a^b f(x)dx &= f(c)(b-a)
> \end{align*}
> 
> </details>

If $f$ is continuous on $[a,b]$, $\exists c \in [a,b]$ such that

$$ \int_b^a f(x)dx = f(c)(b-a) $$

### Average value of a function

> <details>
> 
> <summary> Proof </summary>
>
> Given a function continuous on $[a,b]$, we can get the average value of the function at $[a,b]$ by dividing the curve into $n$ equal-width rectangles, getting the value of each sample points, and dividing by $n$.
> 
> Average area $\displaystyle = \frac{\sum_{i=1}^n f(x_i^*)i}{n}$
> 
> But then, $\displaystyle \Delta x = \frac{b-a}{n} \implies n = \frac{b-a}{\Delta x}$
> 
> \begin{align*}
> \frac{\sum_{i=1}^n f(x_i^*)}{n} &= \frac{\sum_{i=1}^n f(x_i^*)}{\frac{b-a}{\Delta x}}\\
> &= \frac{1}{b-a}\sum_{i=1}^n f(x_i^*) \Delta x
> \end{align*}
> 
> We want to make $n$ larger in order to make the average more accurate.
> 
> \begin{align*}
> \lim_{n\to\infty}\frac{\sum_{i=1}^n f(x_i^*)}{n} &= \lim_{n\to\infty}\frac{1}{b-a}\sum_{i=1}^n f(x_i^*)i \Delta x\\
> &= \frac{1}{b-a}\lim_{n\to\infty}\sum_{i=1}^n f(x_i^*) \Delta x\\
> &= \frac{1}{b-a}\int_a^b f(x)dx
> \end{align*}
> 
> Therefore, given function $f$ that is continuous on $[a,b]$, there exists $c \in [a,b]$ such that
> 
> $$ f_{avg} = f(c) $$
> 
> </details>

Let $f$ be a continuous on $[a,b]$. The average value of $f$ at $[a,b]$, denoted by $f_{avg}$ is

$$ f_{avg} = \frac{\int_a^b f(x)dx}{b-a} $$

***

### First part of the Fundamental Theorem of Calculus

Let $y=f(t)$ that is continuous on $[a,b]$.

If $x \in [a,b]$, then the function is also continuous on $[a,b] \implies$ the function is also continuous on $[a,x]$.

\begin{align*}
F(x) &= \int_a^x f(t)dt \\
F(a) &= \int_a^a f(t)dt = 0 \\
F(b) &= \int_a^b f(t)dt
\end{align*}


Let $f$ be continuous on $[a,b]$. If f is the function defined by

$$ F(x) = \int_a^x f(t)dt $$

then $F'(x) = f(x) \;\forall x \in [a,b]$.


> <details>
> 
> <summary> Proof </summary>
>
> Let $x, x+h \in [a,b], h\neq 0$.
> 
> $$ F(x+h)-F(x) = \int_a^{x+h} f(t)dt -\int_a^x f(t)dt $$
> 
> By the Property 3 of definite integrals, 
> \begin{align*}
> \int_a^{x+h} f(t)dt -\int_a^x f(t)dt &= \int_a^x f(t)dt + \int_x^{x+h}f(t)dt -\int_a^x f(t)dt\\
> &= \int_x^{x+h}f(t)dt
> \end{align*}
> 
> By the Mean Value Theorem for integrals, $\exists c \in [x,x+h]$ such that
> 
> \begin{align*}
> \int_x^{x+h}f(t)dt &= f(c)(x+h-x)\\
> &=hf(c)\\
> \implies F(x+h)-F(x) &= hf(c)\\
> \frac{F(x+h)-F(x)}{h} &= f(c)\\
> \lim_{h\to 0}\frac{F(x+h)-F(x)}{h} &= \lim_{h\to 0}f(c)
> \end{align*}
> 
> Note that $\displaystyle \lim_{h\to 0}x = x$ and $\displaystyle \lim_{h\to 0}(x+h) = x \implies \lim_{h\to 0}c = x$ by Squeeze Theorem.
>  
> Since $f$ is continuous at $x$, 
>  
> $$ \lim_{h\to 0}f(c) = f(x) $$
> 
> \begin{align*}
> \implies F'(x) &= f(x) \;\forall x \in [a,b]\\
> \frac{d}{dx}\int_a^x f(t)dt &= f(x)
> \end{align*}
> 
> </details>

***

### Second part of the Fundamental Theorem of Calculus

> <details>
>
> <summary> Let's bring back $f(x)=x^2+1$ on $[0,2]$. </summary>
> 
> $f$ is continuous on $[0,2] \implies f$ is integrable on $[0,2]$. 
> 
> $$ \implies \int_0^2 (x^2+1)dx = \frac{14}{3} $$
> 
> Let $\displaystyle F(x)= \frac{x^3}{3}+ x-1$.
> 
> \begin{align*}
> F(2) &= \frac{2^3}{3}+2-1 = \frac{8}{3}+1 = \frac{11}{3}\\
> F(0) &= \frac{0^3}{3}+0-1 = 0-1 = - 1\\
> F(2) - F(0) &= \frac{11}{3} -(-1) = \frac{14}{3} \\
> \int_0^2 (x^2+1)dx &= F(2)-F(0)
> \end{align*}
> 
> Observe that $F'(x) = x^2 +1 \implies F(x)$ is the an antiderivative of $x^2+1$.
> 
> </details>

If a function $f$ is continuous on $[a,b]$, then

$$ \int_a^b f(x)dx = F(b)-F(a) $$

where $F$ is any antiderivative of $f$ on $[a,b]$.

> The following notations for $F(b)-F(a)$ are very useful in evaluating definite integrals:
>
> $\displaystyle F(x)\Big]_a^b$ or $\displaystyle F(x)\Big|_a^b$

> <details>
> 
> <summary> Proof </summary>
>
> By FTC - Part 1, the function
> 
> $$ \int_a^x f(t)dt $$
> 
> is an antiderivative of f on $[a,b]$.
> 
> By the Equal Derivatives Theorem,
> 
> $$ \int_a^x f(t)dt = F(x) + C $$
> 
> where $F$ is any antiderivative of $f$.
> 
> \begin{align*}
>  x= b, \int_a^b f(t)dt &= F(b) + C \\
>  x=a , \int_a^a f(t)dt &= F(a) + C = 0 \\
> \int_a^b f(t)dt - \int_a^a f(t)dt &= [ F(b)+C ] - [F(a)+C] \\
> \int_a^b f(t)dt &= F(b)-F(a)
> \end{align*}
> 
> </details>

***

# 2 - Application I

## Areas between curves

#### Example 1

> <details>
> <summary> Find the area of the region under the curve $y=x^2-1$ from $x=-1$ to $x=2$. </summary>
>
> **Solution.** Area is simply not $\int_{-1}^2 (x^2-1)dx$ because $\int_{-1}^1 (x^2-1)dx$ is negative and cancels the positive area.
> 
> Therefore, we get $\int_{-1}^1 -(x^2-1)dx$ to get the area of the curve between -1 and 1.
> \begin{align*}
> A &= \int_{-1}^1-(x^2-1)dx+\int_1^2(x^2-1)dx \\
> &= \Big(-\frac{x^3}{3}+x\Big)\Bigg|_{-1}^1+\Big(\frac{x^3}{3}-x\Big)\Bigg|_1^2\\
> &= \Big(\frac{1^3}{3}+1\Big)-\Big[\frac{(-1)^3}{3}+(-1)\Big]+\Big(\frac{2^3}{3}-2\Big)-\Big(\frac{1^3}{3}-1\Big)\\
> &= \frac{2}{3}+\frac{2}{3}+\frac{8}{3}-2+\frac{2}{3}\\
> A &= \frac{8}{3} 
> \end{align*}
>
> </details>

#### Example 2

> <details>
> 
> <summary> Find the area of the region bounded by the curves of $y=x^2$ and $y = 4x-x^2$. </summary>
> 
> **Solution.** Note that both curves intersect at $(0,0)$ and $(2,4)$.
> 
> When we use Riemann sum, we only get the rectangles in between the region bounded by the area by subtracting the upper function ($y=4x-x^2$) to the lower function ($y=x^2$)
> 
> $$ \implies A_n = \sum [(4x-x^2)-x^2]\Delta x $$
> 
> \begin{align*}
> A &= \int_0^2[(4x-x^2)-x^2]dx\\
> &= \int_0^2(4x-2x^2)dx\\
> &= \Big(2x^2-\frac{2x^3}{3}\Big)\Bigg|_0^2\\
> &= \Big[2(2)^2-\frac{2(2)^3}{3}\Big]-\Big[2(0)^2-\frac{2(0)^3}{3}\Big]\\
> &= \Big[8-\frac{16}{3}\Big]-0\\
> A &= \frac{8}{3}
> \end{align*}
> 
> </details> 

#### Example 3

> <details>
>
> <summary> Find the area of the region bounded by the curve $y=\sqrt{x}$, the line $x+2y =3$, and the $x$-axis. </summary>
> 
> **Solution.** The graphs intersect at $(0,0)$, $(1,1)$, and $(3,0)$.
> 
> $$ x+2y = 3 \implies y  = -\frac{1}{2}x + \frac{3}{2} $$
> 
> \begin{align*}
> A &= \int_0^1 (\sqrt{x})dx + \int_1^3 \Big(-\frac{1}{2}(3-x)\Big)dx\\
> &= \Big(\frac{2x^{\frac{3}{2}}}{3}\Big) \Bigg|_0^1 + \Big(\frac{1}{2}(3x - \frac{x^2}{2})\Big)\Bigg|_1^3\\
> &= \frac{2(1)^{\frac{3}{2}}}{3} - \frac{2(0)^{\frac{3}{2}}} + \frac{1}{2}(3(3) - \frac{3^2}{2}) - \frac{1}{2}(3(1) - \frac{1^2}{2})\\
> &= \frac{2}{3}+ \frac{9}{4} - \frac{5}{4}\\
> &= \frac{8-27+15}{12}\\
> &= \frac{20}{12}\\
> A &= \frac{5}{3}
> \end{align*}
> 
> </details>

***

## Volumes and volumes of revolution using disks and washers

### Volume of a right cylinder

$$ V = ah $$

$$ V_n = \sum_{i=1}^n A(x)\Delta x $$

Let $S$ be a solid that lies between $x=a$ and $x=b$. If the cross-sectional area of $S$ in the plane $P_x$ through $x$ and perpendicular to the $x$-axis is $A(x)$, where $A$ is a continuous function on $[a,b]$, then the volume $V$ of $S$ is

$$ V = \lim_{n \to\infty} \sum_{i=1}^n A(x_i^*)\Delta x = \int_b^a A(x)dx $$ 

#### Example 1 

> <details>
> 
> <summary> Let us find the volume of a sphere of radius $r$.</summary>
> 
> **Solution.** 
> 
> radius of the cross-section circle at $x = \sqrt{r^2-x^2}$
> 
> \begin{align*}
> A(x) &= \pi (\sqrt{r^2-x^2})^2\\
> &= \pi (r^2-x^2)
> \end{align*}
> 
> \begin{align*}
> V_{\text{sphere}} &= \int_{-r}^r A(x)dx \\
> &= \int_{-r}^r \pi (r^2-x^2) dx \\
> &= \pi(r^2x - \frac{x^3}{3})\Big|_{-r}^r \\
> &= \pi\Bigg[r^2(r) - \frac{r^3}{3}\Bigg] - \pi\Bigg[r^2(-r) - \frac{(-r)^3}{3}\Bigg] \\
> V_{\text{sphere}} &= \frac{4}{3}\pi r^3
> \end{align*}
> 
> </details>

#### Example 2

> <details>
> 
> <summary> The base of a solid is the region bounded by $y=x^2$ and $y=4$. Its parallel cross-sections perpendicular to the base and the $y$-axis are squares. Find the volume of the solid. </summary>
> 
> **Solution.** side of the cross-section at $y = 2\sqrt{y}$
> 
> $$ A(y) = (2\sqrt{y})^2 = 4y $$
> 
> \begin{align*}
> V &= \int_0^4 A(y)dy \\
> &=\int_0^4 4y dy \\
> &= 2y^2 \Big|_0^4 \\
> &= 2(4)^2 - 2(0)^2 \\
> V &= 32
> \end{align*}
> 
> </details>

***

### Volume of solids of revolution

If we revolve a region about a line, we obtain a **solid of revolution**.

#### Example 1

> <details>
> 
> <summary> Consider the region under the curve $y=x^2 +1$ from $x=-1$ to $x=2$. We revolve this region about the $x$-axis. </summary>
> 
> **Solution.** radius of the cross-section at $x = f(x)$
> 
> $$ A(x) = \pi [f(x)]^2 $$
> 
> \begin{align*}
> V &= \int_{-1}^2 \pi (x^2+1)^2 dx \\
> &= \int_{-1}^2 \pi (x^4 +2x^2 +1) dx \\
> &= \pi \Bigg(\frac{x^5}{5}+\frac{2x^3}{3}+x\Bigg) |_{-1}^2 \\
> &= \pi\Bigg[\frac{2^5}{5}+\frac{2(2)^3}{3}+2\Bigg] - \pi\Bigg[\frac{(-1)^5}{5}+\frac{2(-1)^3}{3}+(-1)\Bigg] \\
> V &= \frac{78\pi}{5}
> \end{align*}
> 
> </details>

The cross-section of a solid of revolution is always a circle.

#### Example 2

> <details>
> 
> <summary> A solid is obtained by revolving about the $x$-axis the region bounded by $x=y^2$ and $2y=x$. Find the volume of the solid. </summary>
> 
> **Solution.**
> 
> \begin{align*}
> V &= \int_0^4 \pi(\sqrt{x})^2 dx - \int_0^4 \pi\Big(\frac{x}{2}\Big)^2 dx \\
> &= \int_0^4 \pi (x) dx - \int_0^4 \pi \frac{x^4}{4} dx \\
> V &= \frac{8\pi}{3}
> \end{align*}
> 
> </details>

#### Example 3

> <details>
> 
> <summary> A solid is obtained by revolving about the y-axis the region bounded by $2x=y^2$, $y=4$, and the $y$-axis. Find the volume of the solid. </summary>
> 
> **Solution.**
> 
> \begin{align*}
> V &= \int_0^4 \pi (\frac{y^2}{2})^2 dy \\
> &= \int_0^4 \pi (\frac{y^4}{4}) dy \\
> &= \frac{\pi y^5}{20} \Bigg|_0^4 \\
> V &= \frac{256\pi}{5}
> \end{align*}
> 
> </details>

## Volumes by cylindrical shells

There are times that disks-and-washers technique is not the best way to solve a volume problem -- e.g. $y = 4x-x$ rotated about the $y$-axis.

### Volume of a cylindrical shell

> <details>
> 
> Let $r_1$ be the inner radius of the cylinder, $r_2$ be the outer (and larger) radius of the cylinder. $r$ be the average of both
> 
> \begin{align*}
> \Delta r &= r_2 - r_1 \\
> r &= \frac{r_2+r_1}{2}
> \end{align*}
> 
> \begin{align*}
> V_{\text{cylindrical shell}} &= \pi r_2^2 h - r_1^2 h \\
> &= \pi(r_2^2 - r_1^2)h \\
> &= \pi(r_2+r_1)h(r_2-r_1) \\
> &= 2\pi \Bigg(\frac{r_2+r_1}{2}\Bigg) h \Delta r \\
> V_{\text{cylindrical shell}} &= 2\pi r h \Delta r
> \end{align*}
> 
> Given a curve $y=f(x)$ in $[a,b]$ rotated about the $y$-axis, the Riemann sum of the volume is
> 
> $$ V = \sum 2\pi r h \Delta r $$ 
> 
> In this context, $r = x$ (horizontal distance), $h = f(x)$ (vertical distance), and $\Delta r = \Delta x$
> 
> \begin{align*}
> V &= \lim_{n \to\infty} \sum_{i=1}^n 2\pi x_i^* f(x_i^*) \Delta x \\
> &= \int_a^b 2\pi xf(x)dx
> \end{align*}
> 
> </details>

The volume of a solid obtained by rotating about the $y$-axis the region under the curve $y = f(x)$ (continuous and nonnegative) from $x=a$ (nonnegative) to $x = b$ is

$$ V = \lim_{n \to\infty} \sum_{i=1}^n 2\pi x_i^* f(x_i^*) \Delta x = \int_a^b 2\pi xf(x)dx $$


#### Example 1

> <details>
> 
> <summary> A solid is obtained by revolving about the $y$-axis the region bounded by $y = 4x - x^2$ and the $x$-axis. Use cylindrical shells to find the volume of the solid. </summary>
> 
> **Solution.**
> 
> \begin{align*}
> V &= \int_0^4 2 \pi x (4x-x^2) dx \\
> &= \int_0^4 2 \pi (4x^2 - x^3)dx \\
> &= 2\pi \Big( \frac{4}{3}x^3 - \frac{x^4}{4} \Big) \Bigg|_0^4\\
> &= 2\pi \Big[ \frac{4}{3} (4)^3 - \frac{4^4}{4} \Big] - 0\\
> &= \frac{128\pi}{3}
> \end{align*}
> 
> </details>

#### Example 2

> <details>
> 
> <summary> A solid is obatined by revolving about the $x$-axis the region bounded by $y = \sqrt{x}$, $y = 2-x$, and the $x$-axis. Find the volume of the solid. </summary>
> 
> **Solution.**
> 
> *Disks:*
> 
> $y = \sqrt{x}$ and $y = 2-x$ intersect at $(1,1)$
> 
> $\forall x \in [0,1]$, $\sqrt{x} \leq 2-x \implies$ we use $\sqrt{x}$ at this interval
> 
> $\forall x \in [1,2]$, $2-x \leq  \sqrt{x} \implies$ we use $2-x$ at this interval
> 
> \begin{align*}
> V &= \int_0^1 \pi (\sqrt{x})^2 dx + \int_1^2 \pi (2-x)^2 dx \\
> &= \int_0^1 \pi x dx + \int_1^2 \pi (x^2 - 4x +4) dx
> \end{align*}
> 
> (This exercise is left to the reader lol don't wanna solve this myself)
> 
> *cylindrical shell:*
> 
> $y = \sqrt{x}$ and $y = 2-x$ intersect at $(1,1)$.
> 
> $$ y = \sqrt{x} \implies x = y^2 $$
> $$ y = 2-x \implies x = 2-y $$ 
> 
> $$ V = \int_0^1 2\pi y (2-y^2-y) dy $$
> 
> (Just solve this yourselves)

#### Example 3

> <details>
> 
> <summary> A solid is obtained by the revolving about the line $x=-2$ the region bounded by $y=x^3$, $y=8$, and the $y$-axis. Find the volume of the solid. </summary>
> 
> **Solution.**
> 
> *disks:* $\displaystyle V = \int_0^8 \pi \big[ (\sqrt[3]{y} +2)^2 -2^2  \big] dy = \frac{336\pi}{5}$
> 
> *cylindrical shells:* $\displaystyle V = \int_0^2 2\pi (x+2)(8-x^3) dx = \frac{336\pi}{5}$
> 
> </details>

***

<!-- # 3 - Techniques of integration -->

<!-- ## Integration by parts -->

<!-- ## Trigonometric integrals -->

<!-- ## Trigonometric substitution -->

<!-- ## Partial fractions -->




<!-- # 4 - Applications II -->

<!-- ## Arc length -->

<!-- ## Variable-separable differential equations and models for population growth -->
