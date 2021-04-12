# Data-Based Economics

---

## Slides

<style>
.container{
    display: flex;
}
.col{
    flex: 1;
}
</style>

<div class="container">

<div class="col">

- [Slides](https://albop.github.io/dbe/)
  - [Introduction](https://albop.github.io/dbe/slides/index)
  - [Numeric Python and Data Frames](https://albop.github.io/dbe/slides/2_dataframes)
  - [Linear Regression](https://albop.github.io/dbe/slides/3_linear_regression)
  - [Multiple Regression](https://albop.github.io/dbe/slides/4_multiple_regressions)
  - [Causality](5_intro_to_causality.html)
  - [Panels](6_panels.html)
  - [Machine Learning](7_machine_learning.html)
  - [Machine Learning 2](8_machine_learning_2.html)
  - [Text Analysis](9_text_analysis.html)
  - [Recap](10_recap.html)


</div>
<div class="col">

How to create pdfs?
- open a set of slides
- add ?print-pdf to the url (for instance: `https://albop.github.io/dbe/slides/2_dataframes?print-pdf`)
- print the page as a pdf with your navigator

</div>
</div>

---

## Shortcuts

Direct links:
- Python basics: ([exercises](https://raw.githubusercontent.com/albop/dbe/main/Session_1/Exercises.ipynb), [correction](https://raw.githubusercontent.com/albop/dbe/main/Session_1/Exercises-correction.ipynb))
- Dataframe: ([exercises](https://raw.githubusercontent.com/albop/dbe/main/Session_2/Exercises.ipynb), [correction](https://raw.githubusercontent.com/albop/dbe/main/Session_2/Exercises_correction.ipynb))
- Regressions: ([data](https://raw.githubusercontent.com/albop/dbe/main/Session_4/Regressions.ipynb), [correction](https://raw.githubusercontent.com/albop/dbe/main/Session_4/data.dta))

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

| Session | Date (tbc)         | Content                                                                                             |
| ------- | ------------------ | --------------------------------------------------------------------------------------------------- |
| 1       | 12/01              | housekeeping,  basic data types and <mark>language structure </mark>                                |
| 2       | 19/01              | databases, data representation, interactivity (matplotlib, altair, widgets)                         |
| 3       | 26/01              | ordinary least squares (inear regression, multiple regression)                                      |
| 4       | 02/02              | regression inference and categorical variables                                                      |
| 5       | 23/02              | instrumental variables                                                                              |
| 6       | 02/03              | panel data                                                                                          |
| 7       | 09/03              | machine learning approach (regression/classification/clustering, training sets validation set, ...) |
| 8       | 23/03              | regression with sklearn (k-nearest neighbors, SVM, sparse regressions)                              |
| 9       | 24/03              | natural language processing, mock exam                                                              |
| 10      | <mark>30/03</mark> | quick recap, Q&A                                                                                    |

---

## Evaluation & Final Examination

- Data Project
  - group work
  - goals:
    - import some data
    - perform/replicate some econometric work
    - present results with nice plot
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
