---
layout: page
title: Applied Optimal Transport
description: 
img:
importance: 4
category: fun
github: http://github.com/Diebrate/otapp
---
{% include mathjax_macro.html %}

# Optimal Transport

Optimal transport is the study of transitional processes from one object to another. In statistics, it usually involves searching for an optimal joint distribution given two marginal distributions. Mathematically, an optimal transport problem is defined as the following optimization problem:

$$
\begin{equation}
\begin{gathered}
    \pi^* = \argmin_\pi \int\int c(x,y)\pi(x,y) \, dx \, dy \\
    \begin{cases}
        \int \pi(x,y) \, dy = p_X(x) \\
        \int \pi(x,y) \, dx = p_Y(y)
    \end{cases}
\end{gathered}
\end{equation}
$$

Here, $\pi$ is called the joint distribution between $p_X$ and $p_Y$. In other words, $\pi:\Omega\times\Omega\to\mathbb{R}^+$ is a probability density function.

Let's consider the original problem of optimal transport introduced by Monge.

### The Monge Problem

Gaspard Monge first formulated the problem of optimal transport in 1781. The Monge problem can be described as follows: given two distributions, one representing the initial distribution of mass and the other representing the target distribution, how can we transport the mass from the initial to the target distribution in the most efficient way?

Formally, the Monge problem seeks a map \(T: \Omega \to \Omega\) that minimizes the transportation cost:

$$
\min_T \int_\Omega c(x, T(x)) p_X(x) \, dx
$$

subject to the constraint that  $T$ pushes forward $p_X$ to $p_Y$ meaning $T_\# p_X = p_Y$. Here, $c(x, y)$ represents the cost of transporting a unit mass from $x$ to $y$.

### Kantorovich Relaxation

Leonid Kantorovich later relaxed Monge's formulation, allowing for the mass to be split and transported in fractions, which led to a more general and solvable problem. This relaxation leads to the formulation we initially described, which involves finding an optimal coupling $\pi$. The Kantorovich problem is formulated as:

$$
\min_\pi \int_{\Omega \times \Omega} c(x, y) \, d\pi(x, y)
$$

subject to the marginal constraints:

$$
\int_{\Omega} d\pi(x, y) = p_X(x), \quad \int_{\Omega} d\pi(x, y) = p_Y(y).
$$

### Applications of Optimal Transport

Optimal transport has found applications in various fields such as economics, machine learning, image processing, and more. Here are a few examples:

1. **Economics**: In resource allocation problems, optimal transport theory can be used to find the most efficient way to allocate resources.
2. **Machine Learning**: In generative modeling, optimal transport distances, like the Wasserstein distance, are used to measure the difference between distributions.
3. **Image Processing**: Optimal transport can be used to morph one image into another, providing a mathematically sound method for image interpolation.

### Computational Methods

Solving optimal transport problems, especially in high dimensions, can be computationally challenging. Several algorithms have been developed to address this, including:

1. **Linear Programming**: The Kantorovich problem can be formulated as a linear programming problem, which can be solved using standard techniques.
2. **Sinkhorn Algorithm**: An efficient iterative method that solves the entropy-regularized optimal transport problem.
3. **Network Flow Algorithms**: These algorithms leverage the structure of transportation networks to find optimal solutions efficiently.

For further computational procedures, you may refer to my Python package [**otsde**](https://github.com/diebrate/otsde) on my GitHub profile.

### Conclusion

Optimal transport provides a powerful framework for understanding and solving problems involving the movement and distribution of resources. Whether in theoretical research or practical applications, the principles of optimal transport continue to offer valuable insights and solutions.
