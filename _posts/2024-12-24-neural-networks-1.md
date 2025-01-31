---
layout: post
title: Understanding Artificial Neural Networks Part 1
date: 2024-12-24 16:40:16
description: A brief description of how artificial neural networks work part 1
tags: math, neural-networks, ml
categories: machine-learning, math
---

## Introduction

Artificial Intelligence (AI) is all the hype these days, every other day OpenAI, Google, or Meta is making headlines with a breakthrough in the field. Every other day we get a paper with a new state of the art method for doing something. When writing this Meta recently came out with its new LLM architecture Large Concept Models (LCMs). 

*Why isn't this blog about LCMs?* Understanding these breakthroughs is not an easy task and as you know "Rome wasn't built in a day". These concepts require you to have basic understanding of machine learning and deep learning, we cannot just jump onto stuff like LLMs, Transformers, CNNs, etc.

Artificial Neural Networks (ANNs) help us build this foundational knowledge in deep learning to move to advanced topics. As a matter of fact, convolutional neural networks (CNNs) which are prominently used to recognize objects in images are a special type of neural networks.

This blog will focus on how ANNs work at core and we'll also build a neural network from scratch and a scalar auto-gradient library without using any library of any sorts to  which will shed a little light on the foundations of deep learning.

## What are neural networks?

Artificial Neural Networks (ANNs) are known by several names such as multilayer perceptrons, deep feedforward networks, feedforward neural networks, or just neural networks. ANNs comes under the category of Supervised Learning where a mapping from $$ x \to y$$ is provided to the algorithm and from there it learns complex relationships between independent and dependent variables. This mapping which we provide to the neural network is called the **training data**.


The goal of neural networks is to approximate some function $$f^*$$ so that we can predict the value of a given set of inputs based on the data provided during the training. Neural networks just like other learning algorithms like linear regression or SVM are just a mathematical function.

$$ y = f_{NN}(x)$$

{% include figure.liquid loading="eager" path="assets/img/neural_net_structure.jpeg" %}



Neural Networks are structures made up of layers of neurons laid out sequentially. The function $$f_{NN}$$ has a particular form: it’s a nested function.  Each layer of NN can be thought of as one level of nesting in the $$f_{NN}$$ function. The structure of neural networks allows the algorithm to learn complex decision boundaries which is not possible in algorithms like linear Regression, logistic regression, etc.

$$ y = f_{NN} = f_3(f_2(f_1(x)))$$

Neural networks also eliminate the need for doing steps like feature engineering as the structure is not just a single function but a combination of different functions which are able to evaluate many combinations of data.

There is a misconception that ANNs try to mimic the human brain or the way it works which is wrong, a better statement would be that ANNs are inspired by the structure of the brain. We don't have enough information on how brains work or function to model it mathematically.


## Neurons

A neuron is the smallest unit in the neural network, these are the building blocks of neural networks. It can be thought of as a simple mathematical function where inputs are provided and output is received. Every neuron has an activation function which is applied to the input data to get an output. Multiple neurons combine to create a layer of neural network and multiple layers then combine to create the entire neural network. 



The image shown above is an example of a neuron, as you can see a neuron body is provided with multiple inputs $$(x_i)$$, and every input is given a weight $$(w_i)$$. Along with these inputs, there is also a variable bias $$(b)$$, an activation function is applied to these inputs to get an output.

$$ f(x, w, b) = x_1w_1 + x_2w_2 + \cdots + x_iw_i + b$$

## Activation Functions

## Layers and Architectures

## Forward Propagation

## Loss Functions

## Backpropagation