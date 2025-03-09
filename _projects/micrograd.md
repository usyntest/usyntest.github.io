---
layout: page
title: Micrograd
description: A lightweight, educational autograd engine and neural network library implemented in pure Python.
importance: 1
# category: work
---

#### Overview
Micrograd is a minimalistic automatic differentiation engine inspired by PyTorch's autograd. It allows backpropagation through computational graphs and supports basic deep learning operations. This project is useful for understanding the internals of autodiff without the complexity of large frameworks.

#### Technologies Used
- Python
- Jupyter Notebooks

#### How to Use
Installation

```bash
git clone https://github.com/usyntest/micrograd.git
python
```
Example Usage

```python
>> from micrograd import Value
>> a = Value(2.0)
>> b = Value(-3.0)
>> c = a * b
>> c.backward()
>> print(a.grad)  # Should print -3.0
```

#### Key Code Snippet
Backpropagation Implementation

```python
class Value:
    def __init__(self, data, _children=(), _op=''):
        self.data = data
        self.grad = 0
        self._backward = lambda: None
        self._children = _children
        self._op = _op

    def backward(self):
        topo, visited = [], set()
        def build_topo(v):
            if v not in visited:
                visited.add(v)
                for child in v._children:
                    build_topo(child)
                topo.append(v)
        build_topo(self)
        self.grad = 1
        for v in reversed(topo):
            v._backward()
```

This snippet shows the core logic for computing gradients using reverse-mode autodiff.

#### Links
- 📂 [GitHub Repository](https://github.com/usyntest/micrograd)
