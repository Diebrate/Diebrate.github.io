---
layout: page
title: Applied Optimal Transport
description: random thoughts and ideas
img:
importance: 4
category: fun
github: http://github.com/Diebrate/otapp
---

<!-- {% include mathjax_macro.html %} -->

This page is under construction...

Optimal transport is the study of transitional process from one object to another. In statistics, it usually involves searching for an optimal joint distribution given two marginal distributions. Mathematically, an optimal transport problem is defined as the following optimization problem:

$$
\begin{equation}
\begin{gathered}
    \pi^* = \argmin_\pi \int\int c(x,y)\pi(x,y)dxdy \\
    \begin{cases}
        \int \pi(x,y)dy = p_X(x) \\
        \int \pi(x,y)dx = p_Y(y)
    \end{cases}
\end{gathered}
\end{equation}
$$

Here $\pi$ is called the joint distribution between $p_X$ and $p_Y$. In other words, $\pi:\Omega\times\Omega\to\mathbb{R}^+$ is a probability density function.

Let's consider the original problem of optimal transport introduced by Monge.