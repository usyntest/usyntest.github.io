---
layout: page
title: NanoGPT
description: A minimal, efficient implementation of GPT using PyTorch, optimized for small-scale training and fine-tuning.
importance: 1
# category: work
---

#### Overview
NanoGPT is a lightweight and efficient implementation of the Generative Pre-trained Transformer (GPT) model using PyTorch. It is designed for small-scale training and fine-tuning on custom datasets, making it ideal for educational and research purposes. I created two models in this:

1. **Bigram Language Model** `(bigram.py)` – A simple neural network-based bigram model.
2. **Transformer-based GPT Model** `(gpt.py)` – A more advanced language model using self-attention.


#### Features

- Implements a basic bigram language model with embeddings.
- Implements a Transformer-based language model inspired by GPT.
- Uses PyTorch for model training and inference.
- Includes text generation capabilities.

#### Technologies Used
- Python  
- PyTorch  
- NumPy  

#### How to Use
Installation  

```bash
git clone https://github.com/usyntest/nanogpt.git
cd nanogpt
pip install -r requirements.txt
python gpt.py
```

#### Links
- 📂 [GitHub Repository](https://github.com/usyntest/nanogpt)
