---
layout: page
title: Higgs Boson ML
description: Leveraging machine learning techniques to analyze ATLAS Higgs Boson datasets.
importance: 1
# category: work
---

#### Overview

The **ATLAS Higgs Boson Machine Learning** project focuses on analyzing datasets from the ATLAS experiment to identify and classify events associated with the Higgs Boson. Utilizing advanced machine learning techniques, including XGBoost and neural network ensembles, this project aims to enhance the accuracy of event classification in high-energy physics experiments.

#### Technologies Used

- **Python:** The primary programming language for data analysis and model development.
- **XGBoost:** A scalable and accurate implementation of gradient boosting machines.
- **Neural Networks:** Deep learning models constructed using frameworks like TensorFlow or PyTorch.
- **Jupyter Notebooks:** Interactive notebooks for data exploration and model development.

#### Notebooks and Key Highlights

1. **Ensemble of Deep Learning and XGBoost:**
   - Combines the strengths of deep learning models and XGBoost to improve classification performance.
   - Techniques such as stacking and blending are employed to create a robust ensemble model.
   - 📂 [Notebook Link](https://github.com/usyntest/atlas-higgs-boson-ml/blob/main/ensemble%20of%20deep%20learning%20%20and%20xgboost.ipynb)

2. **Ensemble of Neural Networks:**
   - Develops multiple neural network architectures and ensembles them to enhance predictive accuracy.
   - Explores various neural network configurations and their impact on model performance.
   - 📂 [Notebook Link](https://github.com/usyntest/atlas-higgs-boson-ml/blob/main/ensemble_of_neural_networks.ipynb)

3. **Higgs Boson XGBoost:**
   - Implements the XGBoost algorithm to classify Higgs Boson events.
   - Focuses on feature engineering, parameter tuning, and model evaluation.
   - 📂 [Notebook Link](https://github.com/usyntest/atlas-higgs-boson-ml/blob/main/higgs%20boson%20xgboost.ipynb)

#### How to Use

1. **Clone the Repository:**
```bash
git clone https://github.com/usyntest/atlas-higgs-boson-ml.git
cd atlas-higgs-boson-ml
```

2. **Set Up the Environment:**
- Create a virtual environment:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use 'env\Scripts\activate'
    ```
- Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

3. **Run the Notebooks:**
- Launch Jupyter Notebook:
    ```bash
    jupyter notebook
    ```
- Open and execute the desired notebook (e.g., ensemble_of_neural_networks.ipynb).
