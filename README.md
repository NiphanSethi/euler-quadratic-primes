# Euler Quadratic Primes

- [Problem Statement](#problem-statement)
- [Potential Optimizations](#potential-optimizations)

## Problem Statement

Euler discovered the remarkable quadratic formula:

$$n^2 + n + 41$$

It turns out that the formula will produce $40$ primes for the consecutive integer values $0 \leq n \leq 39$. However, when $n = 40$, $40^2 + 40 + 41 = 40(40 + 1) + 41$ is divisible by $41$, and certainly when $n = 41$, $41^2 + 41 + 41$ is clearly divisible by $41$.

The incredible formula $n^2 -79n + 1601$ was discovered, which produces $80$ primes for the consecutive values $0 \leq n \leq 79$. The product of the coefficients, $-79$ and $1601$, is $-126470$.

Considering quadratics of the form:

$$n^2 + an + b$$ where $|a| < 1000$ and $|b| \leq 1000$

where $|n|$ is the modulus/absolute value of $n$

e.g. $|11| = 11$ and $|- 4| = 4$

Find the product of the coefficients, $a$ and $b$, for the quadratic expression that produces the maximum number of primes for consecutive values of $n$, starting with $n = 0$.

Please code up a brute-force solution to this problem (it will not finish in a reasonable time). If you pass the exam stage, prepare to explain possible solutions to improve your current approach in relation to runtime during the panel interview.

## Potential Optimizations

1. When $n = 0$, only the constant coefficient $b$ will be relevant. Since the quadratic expression must evaluate to a prime number, it follows that $b$ must be a prime number. Instead of iterating through every value from $-1000$ to $1000$, we only need to iterate through $168$ values (there are $168$ prime numbers between $1$ and $1000$). This reduces the total number of iterations from $1999 \times 2001$ to $1999 \times 168$. We can even pre-compute and hard-code a list of prime numbers from $1$ to $1000$ as a variable in the source code and refer to this variable in the loop to improve performance.

2. When $n = 1$, the quadratic expression evaluates to $1 + a + b$. Since $b$ must be a prime number and $2$ is the only even prime number, we can infer that:
 
 { $a \in$ odd numbers when $b \ne 2$, $a \in$ even numbers when $b = 2$ }
 
for the quadratic expression to evaluate to a prime number. We can use this information to further reduce the total number of iterations: $b$ can be the outer loop while $a$ can be the nested loop iterating through odd numbers when $b \ne 2$ and even numbers when $b = 2$ (respecting the condition that $|a| < 1000$). 
