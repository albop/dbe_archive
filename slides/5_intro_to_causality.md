# Intro to Causality

---

##  Categorical Variables

---

### Data

- Our multilinear regression: 
$$y = \alpha + \beta x_1 + \cdots + \beta x_n$$

- So far, we have only considered real variables: ($x_i \in \mathbb{R}$).
  - ex: TODO

- How do we deal with the following cases?
  - __binary variable__: $x\in \{0,1\}$ (or $\{True, False}$)
    - ex: $\text{gonetowar}$, $\text{hasdegree}$
  - __hierarchical index__: 
    - ex: survey result (0: I don't know, 1: I strongly disagree, 2: I disagree, 3: I agree, 4: I strongly agree)
    - there is no ranking of answers
  - __nonnumerical variables__:
    - ex: (flower type: $x\in \text{myosotis}, \text{rose}, ...$)


----

### Binary variable

There is nothing to be done: just make sure variables take values 0 or 1.

$$y_\text{salary} = \alpha + \beta x_{\text{gonetowar}}$$

Interpretation: having gone to war is associated with  a $\beta$ increase (or decrease?) in salary (still no causality)

----

### Hierarchical index: 

- Look at the model:

$$y_{\text{CO2 emission}} = \alpha + \beta x_{\text{yellow vest support}} $$

- Where $y_{\text{CO2 emission}}$ is an individuals CO2 emissions and $x_{\text{yellow vest support}}$ is the response the the question *Do you agree with the yellow vests demands?*.

- Response is coded up as:
  - 0: No idea
  - 1: Strongly disagree
  - 2: Disagree
  - 3: Agree
  - 4: Strongly agree

- If the variable was used directly, how would you intepret the coefficient $\beta$ ?
  - index is (partly) hierarchical
  - but proportions are random...

----

### Hierarchical index (2):

- We use one __dummy variable__ per possible answer.
| $D_{\text{No idea}}$ | $D_{Strongly Disagree}$ | $D_{Disagree}$ | $D_{Agree}$ | $D_{Strongly Agree}$ |
| -------------------- | ----------------------- | -------------- | ----------- | -------------------- |
| 0                    | 1                       | 0              | 0           | 0                    |
| 0                    | 0                       | 1              | 0           | 0                    |
| 0                    | 0                       | 0              | 1           | 0                    |
| 0                    | 0                       | 0              | 0           | 1                    |
- Values are linked by the specific __dummy coding__.
  - the choice of the reference group (with 0) has some implications (not so much in linear regressions)
  - it must be frequent enough in the data
  - __effects__ coding: reference group takes -1
- Now our variables are perfectly __colinear__:
  - we can deduce one from the all others
  - we drop one from the regression: the reference group

----

### Hierarchical index (3)

$$y_{\text{CO2 emission}} = \alpha + \beta_1 x_{\text{strdis}} + \beta_2 x_{\text{dis}} + \beta_3 x_{\text{agr}} + \beta_4 x_{\text{stragr}}$$

Interpretation: being in the group which strongly agrees to the yellow vest's claim is associated with an additional $\beta_4$ increase in CO2 consumption.

----

### Nonnumerical variables

<div class="container">

<div class="col">

- When variables take nonnumerical variables, we convert them to numerical variables. 
- Example: 
| activity          | code |
| ----------------- | ---- |
| massage therapist | 1    |
| mortician         | 2    |
| archeologist      | 3    |
| financial clerks  | 4    |

</div>

<div class="col">

- Then we convert to dummy variables exactly like hierarchcal indices
  - here $\text{massage therapist}$ is taken as reference

| $D_{\text{mortician}}$ | $D_{\text{archeologist}}$ | $D_{\text{financial clerks}}$ |
| ---------------------- | ------------------------- | ----------------------------- |
|           1             |            0               |              0                 |
|           0             |            1               |              0                 |
|           0             |             0              |              1                 |

</div>

</div>

----

### Hands-on

Use `statsmodels` to create dummy variables with formula API.

---

## Causality

----

### Spurious correlation

We have seen spurious correlation before

TODO: include some graph here

But actual correlation, or actual causality are not easy to define
  - in statistics they refer to the generating process

----

### How do we define causality

- In math, we have implication: $A \implies B$
  - applies to *statements* that can be either true or false
  - given $A$ and $B$, $A$ implies $B$ unless $A$ is true and $B$ is false
- In a mathematical world taking values $\omega$, we can define causality between statement $A(\omega)$ and $B(\omega)$ as :
$$\forall \omega, A(\omega) \implies B(\omega)$$
- But what is causality in the *real* world?
  - Usually, we observe $A(\omega)$ only once...
    - Example: state of the world: big financial crisis, A: Ben Bernanke chairman of the Fed, B: successful economic interventions
  - Then there is the uncertain concept of time... let's take it as granted.

----

### Causality in Statistics

- Variables $A$ causes $B$ if:
  - $A$ and $B$ are correlated
  - $A$ is known before $B$
    - more precisely $A_{t-1}$ is correlated with $B_t$
  - correlation between $A$ and $B$ is unaffected by other variables

- Examples: TODO

- There exist statistical tests
  - like Granger causality...
  - ... but not for this course

---

## Experiments

----

### Experiment

TODO
- same variables
- same state of the world (other variables)
- What if we can reproduce the same experimen, in the same state of the world

----

### Factual and counterfactual

Suppose we observe an event:


TODO

----

### Experiment

<div class="container">

<div class="col">

Example: cognitive dissonance

Experiment in GATE Lab

Volunteers play an investment game.

They are also asked whether they support OM, PSG, or none.

TODO: overprint for 1 and 2

- Experiment 1: 
Before the experiment, some of them are given a football shirt of their preferred team (treatment 1)

Having a football shirt seems to boost investment performance...

- Experiment 2: subjects are given randomly a shirt of either Olympique  de Marseille or PSG. 

Having the good shirt improves performance.
Havign the wrong one deteriorates it badly.


How would you code up this experiment? Can we conclude on some form of causality?

</div>
<div class="col">

![](gate_lab.jpg)

</div>

</div>

----

###  Formalisation of the problem



<!-- treatment 1: matching group -->
<!-- treatment 2: wrong group -->
<!-- reference group: no shirt -->

Conclusion : two group of people, those given a shirt those not given a shirt

Potential consequence: performance

- Take a given agent *Alice*: she performs well with a PSG shirt. 
  - maybe she is a good investor ?
  - or maybe she *is* playing for her team ?

- Let's try have her play again without the football shirt
  - now the experiment has changed: she has gained experience, is more tired, misses the shirt...
  - it is impossible to get a perfect counterfactual (i.e. where only A changes)

- Let's take somebody else then ? Bob was really bad without a PSG shirt.
  - he might be a bad investor ? or he didn't understand the rules ?
  - some other variables have changed, not only the treatment

- How to make a perfect experiment ? Choose randomly whether assigning a shirt or not
  - by construction the treatment will not be correlated with other variables
  - 

----

### Randomized Control Experiment

Randomize the control
Randomize the treatment


both need to be independent

----

### Natural experiments


Exemple: gender bias in french local elections 
(jean-pierre eymeoud, paul vertier)

![https://spire.sciencespo.fr/hdl:/2441/3k0m7r593p8gs9njjtpupmlknu/resources/wp-78-eymeoud-vertier.pdf]()

are women discriminated against in local elections ?

- 1.5 % for far right voters

----

### Quasi experiment

- split between treatment group and non-treatment group is not random

- examples: parents spank their kid

- how to deal with them ?
  - diff in diff (panels) TODO: quick explanation
  
----

## Introduction to Instrumental variables

----


### Example



### Problem


$$y = \alpha + \beta x + \epsilon$$


We want to establish causality from x to y.

But there can be confounding factors:
  - variable z which causes both x and y
  - exemple: chocolate and nobel price


We could *control* for y:
$$y = \alpha + \beta_1 x + \beta_2 y + \epsilon$$

- we would get a better predictor of $y$ but more uncertainty about $\beta_1$ ($x$ and $y$ are colinear)

----

### Reformulate the problem

Let's assume $T$ is a binary variable: the treatment

$$y = \alpha + \beta T + z + \epsilon$$


There are two groups:

- those who receive the treatment
$$y = \alpha + \beta + z_{T=1} + \epsilon$$

- the others
$$y = \alpha + z_{T=0} + \epsilon$$


Problem: if $z$ is higher in the treatment group, its effect can't be separated from the treatment effect.

Intuition: what if we make groups differently?
  - completely independent from $z$ (and $\epsilon$)
  - not independently from $x$ so that one group will receive more treatment than the other
To make this group we need a variable $q$ that is:
  - uncorrelated to $z$ or $\epsilon$ (exogenous)
  - correlated with $x$


----


### Two stage regression

$$y = \alpha + \beta x + z + \epsilon$$

$$y = \alpha + \beta x + z + \epsilon$$


