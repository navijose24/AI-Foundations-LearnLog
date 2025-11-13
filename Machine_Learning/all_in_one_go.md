### Machine Learning (deep dive)
    An algorithmic way of making sense (learning) from data for machines.
## 1 — Forms of learning (short)

* **Supervised learning**: learn mapping X → y from labeled examples. (classification, regression)
* **Unsupervised learning**: find structure in unlabeled data (clustering, dimensionality reduction).
* **Reinforcement learning**: learn a policy via reward signals (agent-environment loop).
* **Semi-supervised, self-supervised, transfer learning** are variants/combinations used in practice.

---

## 2 — Supervised learning (core ideas)

* **Goal:** choose hypothesis (h \in H) that maps inputs (x) to outputs (y) minimizing expected loss.
* **Training data:** ({(x_i,y_i)}_{i=1}^n).
* **Loss / Risk:** empirical risk ( \hat{R}(h)=\frac{1}{n}\sum \ell(h(x_i),y_i)). Choose (h) minimizing (\hat{R}), but watch generalization.

Key concepts: hypothesis space, inductive bias, overfitting vs underfitting, regularization.

---

## 3 — Learning decision trees (ID3 / CART family)

### ID3 / basic decision tree idea

* Build tree top-down: at each node, choose attribute that best splits data by some criterion (Information Gain, Gini, Gain Ratio).
* Stop when node is pure or no attributes left or data too small.
* Optionally prune to avoid overfitting.

### Entropy and Information Gain (ID3)

* For a set (S) with class proportions (p_+) and (p_-):
  [
  Entropy(S) = -\sum_{c} p_c \log_2 p_c.
  ]
* Information Gain for attribute (A):
  [
  Gain(S,A) = Entropy(S) - \sum_{v \in \text{values}(A)} \frac{|S_v|}{|S|} Entropy(S_v)
  ]
* Choose attribute with largest Gain.

(Gini impurity: (Gini(S)=1-\sum p_c^2), used in CART.)

---

### Worked example — your dataset

Examples (A1, A2) → y:

```
x1: (1,1) -> 1  
x2: (1,1) -> 1  
x3: (1,0) -> 0  
x4: (0,0) -> 1  
x5: (0,1) -> 0  
x6: (0,1) -> 0
```

**Step 1 — root entropy**

Counts: positives = 3 (x1,x2,x4), negatives = 3.
So (p_+ = 0.5, p_- = 0.5).
[
Entropy(root)= -0.5\log_2 0.5 - 0.5\log_2 0.5 = 1.0
]

**Step 2 — InfoGain(A1)**

* A1 = 1 subset: x1,x2,x3 (labels 1,1,0) → pos=2, neg=1 → (p_+=2/3).
  Entropy = (-\tfrac{2}{3}\log_2\tfrac{2}{3} - \tfrac{1}{3}\log_2\tfrac{1}{3} \approx 0.9183).

* A1 = 0 subset: x4,x5,x6 (labels 1,0,0) → pos=1, neg=2 → same entropy 0.9183.

Weighted entropy = ( (3/6)*0.9183 + (3/6)*0.9183 = 0.9183).
Gain(A1) = 1.0 − 0.9183 = **0.0817**.

**Step 3 — InfoGain(A2)**

* A2 = 1: x1,x2,x5,x6 → labels 1,1,0,0 → pos=2,neg=2 → entropy = 1.0.
* A2 = 0: x3,x4 → labels 0,1 → pos=1,neg=1 → entropy = 1.0.

Weighted = (4/6)*1 + (2/6)*1 = 1.0 → Gain(A2) = 0.

**Decision at root:** choose **A1** (higher Gain). Small gain but best.

**Step 4 — grow tree**

* For A1 = 1 node, examples x1,x2,x3:

  * A2 = 1 → x1,x2 both y=1 → leaf y=1.
  * A2 = 0 → x3 y=0 → leaf y=0.

* For A1 = 0 node, examples x4,x5,x6:

  * A2 = 0 → x4 y=1 → leaf y=1.
  * A2 = 1 → x5,x6 both y=0 → leaf y=0.

This yields a perfect tree (split A1 then A2) — no further splits needed.

**Exam tip:** show entropy numbers, weighted sums, Gains — scoring expects these calculations.

---

### Decision-tree practicalities 

* **Pruning** reduces overfitting (pre-pruning: stop if small; post-pruning: build full tree, then prune nodes that don’t improve validation error).
* **Gain ratio** (C4.5) penalizes attributes with many values: GainRatio = Gain / SplitInfo.
* **CART** uses Gini and produces binary splits.

---

## 4 — Evaluating and choosing the best hypothesis

### Evaluation methods

* **Train/test split** (common: 70/30 or 80/20).
* **k-fold cross-validation** (e.g., k=5 or 10): rotate hold-out folds, average metric.
* **Leave-One-Out CV** (LOOCV) extreme case.

### Metrics — classification

* **Accuracy** = (TP+TN)/total.
* **Precision** = TP / (TP+FP) — correctness among predicted positives.
* **Recall (Sensitivity)** = TP / (TP+FN) — coverage of true positives.
* **F1** = 2 * (Precision*Recall) / (Precision+Recall).
* **ROC / AUC** — tradeoff across thresholds; AUC summary.

### Metrics — regression

* **MSE** = mean squared error.
* **RMSE** = sqrt(MSE).
* **R²** = 1 − SSE/SST (explained variance).

### Model selection & generalization

* **Bias–Variance tradeoff**:

  * High bias → underfitting (simple model).
  * High variance → overfitting (complex model).
* Use **validation set** or cross-validation to choose complexity/regularization.
* **Regularization** (penalty to loss): L2 (ridge), L1 (lasso) reduces variance.
* **Occam’s razor**: prefer simpler models when performance similar.

---

## 5 — Regression and classification with linear models

### Linear regression (continuous y)

**Univariate (one feature)**:

* Model: ( y = w_0 + w_1 x ).
* Least squares objective: minimize ( \sum (y_i - w_0 - w_1 x_i)^2 ).
* Closed-form solution (centered data or matrix form): ( \mathbf{w} = (X^T X)^{-1} X^T y ).
* Or gradient descent iterative update: ( w \leftarrow w - \eta \nabla_w \text{MSE} ).

**Key exam points:** derive normal equations, mention assumptions (linearity, homoscedasticity, independence).

### Logistic regression (binary classification)

* Model probability: ( P(y=1|x) = \sigma(w^T x) ), where ( \sigma(z)=1/(1+e^{-z}) ).
* Decision: predict y=1 if ( \sigma(w^T x) >= 0.5 ).
* Loss: cross-entropy (negative log-likelihood):
  [
  L(w) = -\sum_{i} [ y_i \log \hat{p}_i + (1-y_i)\log(1-\hat{p}_i) ].
  ]
* Train by gradient descent / Newton-Raphson (IRLS). Regularization commonly used.

**Why logistic?** outputs probabilities and is linear in the log-odds.

---

## 6 — Choosing best hypothesis (concrete steps)

1. **Define hypothesis space H** (linear models, trees, etc.).
2. **Choose loss function** (0/1, MSE, cross-entropy).
3. **Train candidate models** on training set.
4. **Evaluate** using cross-validation (k-fold) with chosen metric.
5. **Select model** with best validation performance balancing complexity.
6. **Test** final model on holdout test set for unbiased estimate.

---

## 7 — Practical tips

* For decision trees: always show entropy/Gini calculations and final tree; mention pruning.
* For regression/classification: show loss, gradient update step, closed-form if asked (OLS).
* On hypothesis selection: mention cross-validation, bias-variance, and regularization.

---

## 8 — Quick formula summary:

* Entropy: ( -\sum p_i \log_2 p_i ).
* InfoGain: ( Gain = Entropy(S) - \sum \frac{|S_v|}{|S|} Entropy(S_v)).
* Linear regression normal eq: ( w = (X^TX)^{-1}X^T y ).
* Logistic sigmoid: ( \sigma(z)=1/(1+e^{-z}) ).
* Cross-entropy loss: ( -[y\log p + (1-y)\log(1-p)] ).
* MSE: ( \frac{1}{n}\sum (y_i-\hat{y}_i)^2 ).

---


