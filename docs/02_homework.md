---
title: "Homework 2"
hide: true
---

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

<link rel="stylesheet" href="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-editor-1.0.9.css">
<link rel="stylesheet" href="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-viz-0.7.11.css">
<link rel="stylesheet" href="https://yui.yahooapis.com/pure/0.6.0/pure-min.css">
<script src="https://code.jquery.com/jquery-2.1.4.min.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-editor-1.0.9.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-viz-0.7.11.js"></script>
<script src="https://s3-us-west-2.amazonaws.com/cdn.webppl.org/webppl-v0.9.7.js" defer async></script>

Solutions are due on Thursday, March 29 2018. Please send your solutions as a zipped archive. Please name the archive `lastName_HW1.zip` and send it to [Michael Franke](mailto:michael.franke@uni-osnabrueck.de). The archive should contain exactly one plain text file or a markdown file (.txt or .md) with your answers and explanations to all questions. Please keep all your answers short and to the point. Also include your name and student number in the text file. Additionally the archive should contain WebPPL code files (.wppl) for all exercises that require code. Name your code files appropriately; e.g., the code file for the 34th part of exercise 27 should be `ex27_part34.wppl`. 

General advice develop all your code on [webppl.org](webppl.org).

#### Exercise 1: Hyperbole and imprecise interpretation of numerals

Take the hyperbole model of [Chapter 3](https://michael-franke.github.io/probLang/chapters/03-nonliteral.html) as a starting point.

1. Make the following changes to the model:
  - Make the utterance prior a function of $$\alpha$$, like described in [Appendix Chapter 3](https://michael-franke.github.io/probLang/chapters/app-03-costs.html).
  - Make the QUD prior a function of `valence`. Introduce a parameter $$n$$. If the speaker is emotionally aroused, any QUD which includes valence information should be $$n$$ times more likely than any QUD without valence information. If the speaker is not emotionally aroused, any QUD which does not include valence information should be $$n$$ times more likely than any QUD which includes valence information. (The intuition is that speakers want to "talk emotions" more likely whenever they are aroused. Being expressive about a mellow state of mind is infrequent.)
  - Introduce a parameter $$\beta$$ which scales the `prizePrior`. If $$P_{old}(p)$$ is the old prior of price $$p$$, then we will now consider $$P_{new}(p) \propto P_{old}(p)^\beta$$.
2. In the extended model, set $$\alpha = 10$$ and $$\beta = 4$$ and explore the predictions for the joint inference of the pragmatic listener of prize and valence. Describe the main differences when compared to the model as it was in [Chapter 3](https://michael-franke.github.io/probLang/chapters/03-nonliteral.html). Which predictions make more sense to you?
3. Explore different values for $$\alpha$$, $$\beta$$, and $$n$$. Find the constellation which gives a prediction that you like best. Explain what you like about it (and possibly what you still do not like about it).

#### Exercise 2: Fuzzy semantics for quantifiers

In this exercise, we will extend models on quantifier use/interpretation from [Chapter 2](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html) and [Appendix Chapter 5](https://michael-franke.github.io/probLang/chapters/app-05-quantifiers.html) by implement a **fuzzy semantics**. So far we have usually assumed that an utterance is either true or false for any given state. Now we relax this assumption, to go beyond Boolean semantics, and also allow "fuzzy truth values", so to speak. A generalized meaning function $$M \colon U \times S \rightarrow [0;1]$$ maps any pair of utterance $$u$$ and state $$s$$ to a value between 0 and 1. The literal listener then updates prior beliefs about states, not by conditioning with the set of all states where $$u$$ is true (as we did before), but rather in this manner:

$$P_{LL}(s \mid u) \propto P(s) M(u,s)$$

1. In the first model from [Chapter 2](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html), change only the meaning of the quantifier *some* so that it gets the following fuzzy truth values for states 0, ..., 3: 0.01, 0.5, 1, 1. Run the model and compare the predictions for the pragmatic listener's interpretation of *some* with this fuzzy semantics to the original one with a standard two-valued semantics. What are the differences? Which model's predictions do you think are better? Which model do you prefer conceptually? (Give short answers and good reasons for your judgements.)
2. In the first model from [Appendix Chapter 5](https://michael-franke.github.io/probLang/chapters/app-05-quantifiers.html), exchange the given two-valued semantics for all quantifiers with one that implements an S-shaped meaning function, using [logistic functions](https://en.wikipedia.org/wiki/Logistic_function). Concretely, instead of fixing a lower and upper bound for each quantifier, now fix a triple consisting of parameter $$k$$ and parameter $$x_0$$ of the [logistic function](https://en.wikipedia.org/wiki/Logistic_function), as well as a Boolean parameter that defines whether the quantifiers truth values are increasing or decreasing as the true state gets larger (stupidly put, whether its meaning is an S-shaped curve or a "mirrored S"-shaped curve). Fix parameter values for each quantifiers meaning function and test the model. Is this a better model than the second model from [Appendix Chapter 5](https://michael-franke.github.io/probLang/chapters/app-05-quantifiers.html)? To answer this question, think about what would naturally be free parameters in each model, which we would like to infer from empirical data (maybe after formulating a specific prior for each). Which model as more "degrees of freedom", so to speak?
