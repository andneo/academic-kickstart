---
title: Optimisation Algorithms
linktitle: Optimisation Algorithms
toc: true
type: docs
date: "2019-05-05T00:00:00+01:00"
draft: false
menu:
  deep_learning:
    name: Optimising Functions
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

Optimisation is a ubiquitous process, people do it everyday. A classic example would be: _How do I get somewhere as (**fast, cheap, environmentally friendly**) as possible?_ 
Nature optimises too, a big part of what I do in my PhD is finding out how systems of particles optimise their potential energy. 

Needless to say optimisation is an important process, and quite a bit of effort has been dedicated to developing algorithms that do it well.
Optimisation algorithms form a key component of neural networks, as we will see. 
The first section of these notes introduce gradient-based optimisation algorithms, and how to implement in Python. 
