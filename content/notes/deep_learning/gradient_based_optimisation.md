---
title: Gradient-Based Optimisation
linktitle: Gradient-Based Algorithms
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
url_code: "https://github.com/andneo/andneo_code/tree/master/deep_learning/optimisation_algorithms"
menu:
  deep_learning:
    parent: Optimising Functions
    weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

First we need to introduce some notation:
* $\textbf{x}$: the $n$-dimensional vector of parameters to be optimised.
* $f(\textbf{x})$: the objective function. 
* $\nabla f(\textbf{x})\equiv\textbf{g}(\textbf{x})$: the gradient of the objective function.

Formally an optimisation problem can be written as:
\begin{equation}
    \min_{\textbf{x}\in\mathbb{R}^{n}}f(\textbf{x})
\end{equation}

Optimisation algorithms iteratively update an initial guess for $\textbf{x}$ until they satisfy the above condition.
The difference between them comes from how we move from $\textbf{x}\_{i}$, at iteration $i$ of our algorithm, to $\textbf{x}\_{i+1}$.

## Line Search Strategies
We are going to focus on line search strategies -- algorithms where we select a direction $\textbf{d}\_{i}$ from $\textbf{x}\_{i}$, and search along that direction to find a new set of coordinates $\textbf{x}\_{i+1}$ where $f(\textbf{x}\_{i}) < f(\textbf{x}\_{i+1})$. We write this as:
\begin{equation}
    \textbf{x}\_{i+1} = \textbf{x}\_{i} + \alpha\_{i}\textbf{d}\_{i}
\end{equation}
Therefore, we have two tasks at each iteration:
1. Determine $\textbf{d}\_{i}$
2. Determine $\alpha\_{i}$ (the step length).

We want to write some Python code that can optimise arbitrary functions.
The first step is to define a ``` Class ```:
```python
class Optimise:
    def __init__(self, X, function, gradient, err, method):
    #   Initialise input parameters for the optimisation algorithms
        self.X      = X         # Initial coordinates.
        self.f      = function  # Function to be optimised.
        self.g      = gradient  # Gradient of the function.
        self.err    = err       # Threshold convergence value
```
This ``` Class ``` has three key attributes:
1. ``` X ```: The initial coordinates from which to optimise from, $\textbf{x}\_{i=0}$.
2. ``` f ```: The objective function to be optimised, $f(\textbf{x})$.
3. ``` g ```: The gradient of the objective function, $\textbf{g}(\textbf{x})$.

There are two more parameters, ``` err ``` and ``` method ```, which we'll discuss later.
### Deciding the Search Direction
Different line search algorithms use different search directions, and the ``` method ``` variable will let our program know which to use.

We are going to focus on two methods: 
* ``` method=1```: Steepest Descent
* ``` method=2```: Conjugate Gradient

Which we will call them from the ``` __init__ ``` method:
```python
#   Perform local optimisation.
    if(method==1):
        self.steepest_descent()
    elif(method==2):
        self.conjugate_gradient()
```
#### Steepest Descent
The steepest descent direction of a function is given by $-\textbf{g}(\textbf{x})$, and so is the most obvious choice for a search direction.
```python
def steepest_descent(x0,errsq):
    xi = x0
#   Compute the gradient and the square of its magnitude at i=0
    gi = np.array( g(*xi) )
    gd = np.dot(gi,gi)
#   Iteratively update the coordinates using the Steepest Descent algorithm
#   until the convergence criterion is met.
    while gd > errsq:
#   Update the coordinates using the negative gradient
        xi = xi - a*gi
#   Calculate the gradient and the square of its magnitude at the new coordinates
        gi = np.array( g(*xi) )
        gd = np.dot(gi,gi)
```

#### Conjugate Gradients

### Deciding the Step Length
#### Backtracking

## Testing our Optimisation Algorithms
[test functions](https://en.wikipedia.org/wiki/Test_functions_for_optimization) for optimisation algorithms
### Defining a function in Python
#### Bethe function
$$ f(x,y) = (1.5-x+xy)^{2} + (2.25-x+xy^{2})^{2} + (2.625-x+xy^{3})^{2} $$

```python
f = lambda x,y: (1.5-x+x*y)**2 + (2.25-x+x*y**2)**2 + (2.625-x+x*y**3)**2
```

\begin{align}
    \dfrac{\partial f(x,y)}{\partial x} = 2\big[(1.5-x&+xy)(y-1) + (2.25-x+xy^{2})(y^{2}-1) \\\\
    &+ (2.625-x+xy^{3})(y^{3}-1)\big]
\end{align}

\begin{align}
    \dfrac{\partial f(x,y)}{\partial y} = 2\big[(1.5&-x+xy)x + (2.25-x+xy^{2})(2xy) \\\\
    &+ (2.625-x+xy^{3})(3xy^{2})\big]
\end{align}
```python
g = lambda x,y: [2*( (1.5-x+x*y)*(y-1) + (2.25-x+x*y**2)*(y**2-1) + (2.625-x+x*y**3)*(y**3-1)   ),
                 2*( (1.5-x+x*y)*x     + (2.25-x+x*y**2)*(2*x*y)  + (2.625-x+x*y**3)*(3*x*y**2) )]
```
## Comparing the different algorithms 
{{< video library="true" src="deep_learning/videos/linesearch.mp4" controls="yes" >}}
