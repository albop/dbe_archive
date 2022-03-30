# Coursework

You are allowed to work in small groups with up to 3 people. The work must be returned on April X (X to be determined on April 5). It should consist in a jupyter notebook, with all the text and code toghether with the attached datafile(s). The notebook must make for enjoyable reading without any prior knowledge of the paper.

Your goal is to replicate the main result from one of the two following famous papers:

- *Are Emily and Greg More Employable Than Lakisha and Jamal? A Field Experiment on Labor Market Discrimination*, by Marianne Bertrand and Sendhil Mullainathan, Americal Economic Review, 2004
- *Malleable Lies: Communication and Cooperation in a High StakesTV Game*, by 
 Uyanga Turmunkh, Martijn J. van den Assem, Dennie van Dolder, Management Science, October 2019

If you are interested in replicating *another* paper, discuss it with the professor before.

The instructions below apply to any paper.

- read the paper
- identify the main hypothesis, and the empirical strategy
- locate replication files (they are available from the publisher's website)
- import the data / describe the data
- try to reproduce the *main* result(s) from the paper 
    - intepret the statistics and comment on what you get
    - it's ok if the figures are not exactly the same[^footnote]
- make the finishing touches:
    - work on the notebook to make it a nice reading
    - ensure the notebook can be run on any computer (in particuler, it should not reference computer specific file paths)


[^footnote]: In the Bertrand and Mullainathan paper, they use probit regressions rather than logistic regression. They are essentially very similar (they make different distributional assumptions). I would advise to start with logistic regressions as in the course, and possibly compare the results you get with probit regressions.