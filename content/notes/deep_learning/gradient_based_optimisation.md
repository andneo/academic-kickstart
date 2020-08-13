---
title: Gradient-Based Optimisation
linktitle: Gradient-Based Algorithms
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  deep_learning:
    parent: Optimising Functions
    weight: 3

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 4
---

#### Defining a function
[test functions](https://en.wikipedia.org/wiki/Test_functions_for_optimization) for optimisation algorithms
\begin{equation}
    f(x,y) = (1.5-x+xy)^{2} + (2.25-x+xy^{2})^{2} + (2.625-x+xy^{3})^{2}
\end{equation}
```python
f  = lambda x, y: (1.5 - x + x*y)**2 + (2.25 - x + x*y**2)**2 + (2.625 - x + x*y**3)**2
```
#### Calculating the gradient
\begin{equation}
    \dfrac{\partial f(x,y)}{\partial x} = 2(1.5-x+xy)(y-1) + 2(2.25-x+xy^{2})(y^{2}-1) + 2(2.625-x+xy^{3})(y^{3}-1)
\end{equation}
\begin{equation}
    \dfrac{\partial f(x,y)}{\partial y} = 2(1.5-x+xy)x + 2(2.25-x+xy^{2})(2xy) + 2(2.625-x+xy^{3})(3xy^{2})
\end{equation}
```python
g  = lambda x, y: [(2*(1.5 - x + x*y)*(y-1)) + (2*(2.25 - x + x*y**2)*(y**2-1)) + (2*(2.625 - x + x*y**3)*(y**3-1)),
                   (2*(1.5 - x + x*y)*x) + (2*(2.25 - x + x*y**2)*(2*x*y)) + (2*(2.625 - x + x*y**3)*(3*x*y**2))]
```
{{< video library="true" src="deep_learning/videos/linesearch.mp4" controls="yes" >}}
