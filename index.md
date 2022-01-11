# Data-Based Economics

## Introduction

<style>
.container{
    display: flex;
}
.col{
    flex: 1;
}
</style>

---

## Communication

- Main website: [https://github.com/albop/dbe](https://github.com/albop/dbe)
  - contains slides and exercises
  - you can open github issues if you find typos...
- Slides are also accessible from my [website](https://www.mosphere.fr/dbe)
- Communication about the course in discord
- Collaboration between students is strongly encouraged
- Email: `pwinant@escp.eu`
  - hint: start your mail subject by `[dbe]`

---

## About myself


<div class="container">

<div class="col">

<img src="pablo_winant.png">

</div>
<div>

- professor at ESCP and Ecole Polytechnique since 2019
- formerly at IMF and Bank of England
- computational economist
- involved in various opensource projects including [QuantEcon](https://quantecon.org/)

</div>

---

## Data-based economics

- Most economists use data all the time
  - to illustrate facts
  - for research purposes

- You need to know how to
  - import data, clean it
  - explore it, perform basic data description tasks
  - run regressions

---

## Econometricks

- An art invented by economists: $$\underbrace{y}\_{\text{dependent variable}} = a \underbrace{x}\_{\text{explanatory variable}} + b$$

- Challenge:
  - find $a$
  - control $b$

---

## Econometricks (2)

$$\underbrace{y}\_{\text{dependent variable}} = a \underbrace{x}\_{\text{explanatory variable}} + b$$

- <!-- .element: class="fragment" --> Example 1:
  - I want to establish a link between growth and trade openness
  - <!-- .element: class="fragment" -->but my country has only 10 years of historical data... (within dimension)
  - <!-- .element: class="fragment" -->... let's take 50 countries at the same time (between dimension)
  - <!-- .element: class="fragment" -->find a way to analyze both dimensions at the same time
  - <!-- .element: class="fragment" -->-> panel data

---

## Econometricks (3)

$$\underbrace{y}\_{\text{dependent variable}} = a \underbrace{x}\_{\text{explanatory variable}} + b$$

- <!-- .element: class="fragment" --> Example 2:
  -  young men who go to war receive *in average* lower wages when they return than men who didn't go to war
  - <!-- .element: class="fragment" --> ... is it because they skipped college?
  -  <!-- .element: class="fragment" -->... or did they choose to go to war because they were less skilled for college?
  -  <!-- .element: class="fragment" -->find a way to extract *causality*
  -  <!-- .element: class="fragment" -->-> instrumental variables
  -  <!-- .element: class="fragment" -->This was worth a Nobel Prize! (D. Card, J. Angrist, G.W. Imbens)

---

## Big Data Era and Machine Learning

- Data has become very abundant
- <!-- .element: class="fragment" -->Large amounts of data of all kinds
  - structured (tables, ...)
  - unstructured (text, images, ...)
- <!-- .element: class="fragment" -->Machine learning:
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

<img src=sentiment_analysis.png width=60%>

Sentiment analysis: predict population's optimism by analyzing tweets.

Check [sentiment viz](https://www.csc2.ncsu.edu/faculty/healey/tweet_viz/tweet_app/)

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

## So what will we do ?

- Programming
- Econometrics / Machine Learning
- Talk about economics

---
