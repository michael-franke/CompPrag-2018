---
title: "Homework 1"
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

Solutions are due on Sunday, March 11 2018. Please send your solutions as a zipped archive. Please name the archive `lastName_HW1.zip` and send it to [Michael Franke](mailto:michael.franke@uni-osnabrueck.de). The archive should contain exactly one plain text file or a markdown file (.txt or .md) with your answers and explanations to all questions. Please keep all your answers short and to the point. Also include your name and student number in the text file. Additionally the archive should contain WebPPL code files (.wppl) for all exercises that require code. Name your code files appropriately; e.g., the code file for the 34th part of exercise 27 should be `ex27_part34.wppl`. 

General advice develop all your code on [webppl.org](webppl.org).

#### Exercise 1: Plot samples from a normal distribution

In analogy to the material from [Chapter I of the BDAPPL Webbook](https://mhtess.github.io/bdappl/chapters/01-introduction.html), where we did a similar thing for a Bernoulli distribution, plot 10,000 samples from a normal distribution with mean 0 and standard deviation 1. Please use `Gaussian(...)` or `gaussian(...)` (whichever you find more appealing), together with `repeat(...)` and `viz(...). ` (You can find more information about the normal distribution in WebPPL in the [documentation](http://docs.webppl.org/en/master/distributions.html).)

#### Exercise 2: 2-Box problem

Implement Bayesian reasoning for the 2-box problem in WebPPL in parallel to [the code for the 3-card problem](https://michael-franke.github.io/probLang/chapters/app-01-probability.html).

Jones has two boxes. One contains two gold coins, the other one gold and one silver coin. Jones selects a random box and picks a random coin from it. He shows you a gold coin. What is the probability that the other coin in the box from which Jones presented the gold coin to you is also gold?

#### Exercise 3: Inferring the bias of a coin from the observation of outcomes

Following the example in [Chapter II of the BDAPPL Webbook](https://mhtess.github.io/bdappl/chapters/02-buildingModels.html), let us calculate in WebPPL what a rational agent should believe about the bias of a coin after observing $$k=25$$ heads out of $$n = 30$$ flips, if they initially believe that any bias of the coin is equally likely. Fortunately for us, a friendly programmer has already written code to do this. Unfortunately for us, there are mistakes. (Hint: Some mistakes are easy to spot. But the programmer also seemed to have difficulties keeping apart WebPPL's commands for conditioning on observation: check the [documentation](http://webppl.readthedocs.io/en/master/inference/conditioning.html) on `condition(...)`, `observe(...)` and `factor(...)`.)

{% highlight js %}

var priorDistribution = Uniform({a: 0, b: 1})

viz(Infer({method: "rejection",
           samples: 5000,
           model: function() {
             var theta = repeat(100,sample(priorDistribution))
             var outcome = Binomial({p: theta, n: 25}) 
             observe(outcome == 30) 
             return theta
           }}))
	
{% endhighlight %}

1. Correct the mistakes and send the corrected code as a .wppl file. For each mistake, explain in a few words why it is wrong and how you corrected it. You may do this as a comment in the .wppl file.

2. Plot the result of the code and interpret it. What does the graph show?


#### Exercise 4: Scalar implicatures

Use the code from the first model of [Chapter II from Probabilistic Language Understanding](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html). Extend the model in the following way:

1. Currently, the code fixes that there are only 3 apples whose color the conversation is about. Make the code more general, by having a variable `total_apples` which we can set in the beginning of the code to any arbitrary (but reasonable) value. (**Hints*:* the function `_.range(total_apples+1)` might be really handy; moreover, don't forget to take care of the semantics, in particcular the meaning of "all".)
2. Include messages with the following semantics:
- "one", "two" and "three" with a (natrual?) exact number reading (e.g., "one" is true iff exactly 1 apple is red)
- "many" which is true for any number of red apples bigger than 4
- "most" which is true for any number of red apples bigger than half of `total_apples`

Create a histrogram of the pragmatic listener's interpretation of "some" when `total_apples = 10`.
