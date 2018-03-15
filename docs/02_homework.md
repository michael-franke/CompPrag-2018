## Homework 2: Exploring RSA models

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


