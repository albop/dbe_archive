---
title: Introduction to Machine Learning (2)
subtitle: Data-Based Economics
author: Year 2022-2023
format:
  revealjs:
    toc: true
    toc-depth: 1
    toc-title: Plan
    navigation: grid
    width: 1920
    height: 1080
aspectratio: 169
---


# Machine learning (2)

## Classification

---

## Classification Problems 

----

### Classification problem

- Binary Classification 
  - Goal is to make a *prediction* $c_n = f(x_{1,1}, ... x_{k,n})$ ...
  - ...where $c_i$ is a binary variable ($\in\{0,1\}$)
  - ... and $(x_{i,n})_k$, $k$ different features to predict $c_n$
- Multicategory Classification
  - The variable to predict takes values in a non ordered set with $p$ different values

----

### Logistic regression

<div class="container">

<div class="col">

- Given a regression model (a linear predictor)

$$ a_0 + a_1 x_1 + a_2 x_2 + \cdots a_n x_n $$
- one can build a classification model:
$$ f(x_1, ..., x_n) = \sigma( a_0 + a_1 x_1 + a_2 x_2 + \cdots a_n x_n )$$
where $\sigma(x)=\frac{1}{1+\exp(-x)}$ is the logistic function a.k.a. sigmoid 
- The loss function to minimize is:
$$L() = \sum_n (c_n - \sigma( a_{0} + a_1 x_{1,n} + a_2 x_{2,n} + \cdots a_k x_{k,n} ) )^2$$
- This works for any regression model (LASSO, RIDGE, nonlinear...)
</div>

<div class="col">

![](graphs/sigmoid.png)

</div>

</div>

----

### Logistic regression

- The linear model predicts an intensity/score (not a category)
$$ f(x_1, ..., x_n) = \sigma( \underbrace{a_0 + a_1 x_1 + a_2 x_2 + \cdots a_n x_n }_{\text{score}})$$
- To make a prediction: round to 0 or 1.

<img src=graphs/datacamp.jpeg width=60%>

----

### Multinomial regression

- If there are $P$ categories to predict:
  - build a linear predictor $f_p$ for each category $p$
  - linear predictor is also called score

- To predict:
  - evaluate the score of all categories
  - choose the one with highest score

- To train the model:
  - train separately all scores (works for any predictor, not just linear)
  - ... there are more subtle approaches (not here)


---

## Other Classifiers

----

### Common classification algorithms

There are many 
- Logistic Regression
- Naive Bayes Classifier 
- Nearest Distance
- neural networks (replace score in sigmoid by n.n.)
- Decision Trees
- Support Vector Machines

----

### Nearest distance

<dic class="container">

<div class="col">

- Idea: 
  - in order to predict category $c$ corresponding to $x$ find the closest point $x_0$ in the training set 
  - Assign to $x$ the same category as $x_0$
- But this would be very susceptible to noise
- Amended idea: $k-nearest$ neighbours
  - look for the $k$ points closest to $x$
  - label $x$ with the same category as the majority of them
- Remark: this algorithm uses Euclidean distance. This is why it is important to normalize the dataset.

</div>

<div class="col">

![](graphs/k-nearest.png)

</div>

</div>

----

### Decision Tree / Random Forests

<dic class="container">

<div class="col">

- Decision Tree
    - recursively find simple criteria to subdivide dataset

- Problems: 
  - Greedy: algorithm does not simplify branches
  - easily overfits

- Extension : random tree forest 
  - uses several (randomly generated) trees to generate a prediction
  - solves the overfitting problem
</div>

<div class="col">

![](graphs/decision_tree.png)

</div>

</div>

----

### Support Vector Classification

<div class="container">

<div class="col">

- <!-- .element: class="fragment" data-fragment-index="1" --> Separates data by one line (hyperplane).
- <!-- .element: class="fragment" data-fragment-index="2" --> Chooses the largest margin according to <emph>support vectors</emph>
- <!-- .element: class="fragment" data-fragment-index="3" --> Can use a nonlinear kernel.

</div>

<div class="col">

<div class="r-stack">

<img class="fragment current-visible" src="graphs/hyperplanes.png" data-fragment-index=1>
<img class="fragment current-visible" src="graphs/margin.jpg" data-fragment-index=2>
<img class="fragment current-visible" src="graphs/nonlinear_svm.png" data-fragment-index=3>

</div>

</div>
</div>

----

### All these algorithms are super duper easy to use!



```python
from sklearn.tree import DecisionTreeClassifier
clf = DecisionTreeClassifier(random_state=0)
```

...

```python
from sklearn.svm import SVC
clf = SVC(random_state=0)
```

...

```python
from sklearn.linear_model import Ridge
clf = Ridge(random_state=0)
```



---

## Validation

----

### Validity of a classification algorithm

- Independently of how the classification is made, its validity can be assessed with a similar procedure as in the regression.

- Separate training set and test set
  - do not touch test set at all during the training

- Compute score: number of correctly identified categories
  - note that this is not the same as the loss function minimized by the training


----

### Classification matrix

- For binary classification, we focus on the *classification matrix* or *confusion matrix*.
| Predicted | (0) Actual      | (1) Actual      |
| --------- | --------------- | --------------- |
| 0         | true negatives (TN) | false negatives (FN) |
| 1         | false positives  (FP) | true positives (TP) |

- Overall accuracy: $\frac{\text{TN}+\text{TP}}{\text{total}}$
- Sensitivity: $\frac{TP}{FP+TP}$
- False Positive Rate (FPR): $\frac{FP}{TN+FP}$

- In some cases, sensitivity is the actual objective, at the expense of lower FPR
  - example: fraud detection
- Example:
    -  facial recognition by London police: 2% accuracy
    -  facial recognition by South Wales police: 9% accuracy
    -  a success?

----

### Confusion matrix with sklearn

- Predict on the test set:

```python
y_pred = model.predict(x_test)
```
- Compute confusion matrix:

```python
from sklearn.metrics import confusion_matrix
cm = confusion_matrix(y_test, y_pred)
```

----
