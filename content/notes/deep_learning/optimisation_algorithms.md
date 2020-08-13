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

A key component of neural networks is an optimisation algorithm. 
These are usually iterative algorithms used to minimise the error our neural network model makes.
Usually, in books and notes that I've read, this is introduced after a big picture style introduction.

But these algorithms are tools to be used to build a neural network, and I personally prefer to understand how they work first.
So I am starting these notes off with an introduction to gradient-based optimisation algorithms and automatic differentiation. 
