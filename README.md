# Data-Based Economics

---

## Shortcuts

[Slides](https://albop.github.io/)

---

## Communication


- Main website: [https://github.com/albop/dbe](https://github.com/albop/dbe)
  - contains slides and exercises
  - you can open github issues if you find typos...
- Communication about the course in discord
- Collaboration between students is strongly encouraged
- Email (personal matter only) : `pwinant@escp.eu`

---

## About myself

<img src="pablo_winant.png" width=40%>

- professor at ESCP and Ecole Polytechnique since 2019
- formerly at IMF and Bank of England
- computational economist
- involved in various opensource projects including [QuantEcon](https://quantecon.org/)

---

## Data-based economics

- All economists use data all the time
  - to illustrate facts
  - for research purposes

- You need to know how to
  - import data, clean it
  - explore it, perform basic data description tasks
  - run regressions

---

## Econometricks

- An art invented by economists: $$\underbrace{y}\_{\text{dependent variable}} = a \underbrace{x}\_{\text{explanatory variable}} + b$$
- <!-- .element: class="fragment" --> Example 1:
  - I want to establish a link between growth and trade openness
  - but my country has only 10 years of historical data... (within dimension)
  - ... let's take 50 countries at the same time (between dimension)
  - find a way to analyse both dimensions at the same time
  - -> panel data
- <!-- .element: class="fragment" --> Example 2:
  -  young men who go to war have in average lower wages when they return
  -  ... is it because they skipped college ?
  -  ... or did they choose to go to way because they were less skilled for college ?
  -  find a way to extract *causality*
  -  -> instrumental variables

---

## Big Data Era and Machine Learning

- Some kinds of data has become very abundant
- <!-- .element: class="fragment" -->Large amounts of data of all kinds
  - structured (tables, ...)
  - unstructured (text, images, ...)
- <!-- .element: class="fragment" -->Machine learning approach:
  - a set of powerful algorithms...
  - ... so powerful some call it *artificial intelligence*
    - they *learn* by processing data
  - ... to extract information and relations in large data sets
  - ... 
- <!-- .element: class="fragment" -->Comparison with econometrics
  - ML has it own, partially redundant, jargon
  - much harder to understand causality, standard deviation (i.e. precision)

---

## Big Data Era and Machine Learning (1)

![](NVIDIA_Portrait_Example.jpeg)

Deep learning: artificial neural nets

---

## Big Data Era and Machine Learning (2)

<img src=sentiment_analysis.png width=80%>

Sentiment analysis: predict opinion optimism by analysing tweets [sentiment viz](https://www.csc2.ncsu.edu/faculty/healey/tweet_viz/tweet_app/)

---

## Programming in Python

- Easy, clean, widespread programming language
  - free
  - libraries for virtually any task
- <!-- .element: class="fragment" -->Lingua franca of machine learning community
- <!-- .element: class="fragment" -->Data analysts/Statisticians/Researchers spend most of their time...
  - ... programming
- <!-- .element: class="fragment" -->Presentation (plots, interactive apps) is super important and relies on ...
  - ... programming
- <!-- .element: class="fragment" -->Worth investing a  bit of time to learn it
  - you can easily become an expert
- <!-- .element: class="fragment" -->Plus it's fun
- <!-- .element: class="fragment" -->In this course we'll be using python, mostly, as a scripting langage

---

![](python.png)

---

## Roadmap

| Session | Date (tbc) | Content                                                                                              |
| ------- | ---------- | ---------------------------------------------------------------------------------------------------- |
| <mark>1</mark>       | <mark>12/01</mark>      | <mark> housekeeping,  basic data types and language structure </mark>                                |
| 2       | 19/01      | databases, data representation, interactivity (matplotlib, altair, widgets)                          |
| 3       | 26/01      | ordinary least squares (linear regression, multiple regression)                                      |
| 4       | 02/02      | regression inference and categorical variables                                                       |
| 5       | 09/02      | instrumental variables                                                                               |
| 6       | 23/02      | panel data                                                                                           |
| 7       | 02/03      | machine learning approach (regression/classification/clustering, training sets validation set, ...) |
| 8       | 09/03      | regression with sklearn (k-nearest neighbors, SVM, sparse regressions)                               |
| 9       | 30/03      | natural language processing                                                                          |
| 10       | ?     | presentation of data project, programming test                                                       |

---

## Evaluation & Final Examination

- Data Project
  - group work
  - goals:
    - import some data
    - perform/replicate some econometric work
    - present result with nice plot
  - handled as a Jupyter Notebook (mixes text and code)
  - subjects proposed by myself and other professors
- Programming test
  - small coding tasks

---

## Work Environment

- local programming environment:
  - install [Anaconda Python](https://www.anaconda.com/products/individual) for your computer
  - install [VSCode](https://code.visualstudio.com/)
  - make sure python extension is activated and configured in VSCode

- online environement:
  - use google' [Colab](https://colab.research.google.com/notebooks/intro.ipynb#recent=true)
