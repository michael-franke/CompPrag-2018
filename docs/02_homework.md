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

Solutions are due on Sunday, April 15 2018. Please send your solutions as a zipped archive. Please name the archive `lastName_HW2.zip` and send it to [Michael Franke](mailto:michael.franke@uni-osnabrueck.de). The archive should contain exactly one plain text file or a markdown file (.txt or .md) with your answers and explanations to all questions. Please keep all your answers short and to the point. Also include your name and student number in the text file. Additionally the archive should contain WebPPL code files (.wppl) for all exercises that require code. Name your code files appropriately; e.g., the code file for the 34th part of exercise 27 should be `ex27_part34.wppl`. 

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

Notice that [Chapter 9](https://michael-franke.github.io/probLang/chapters/09-politeness.html) does essentially the same thing. But, unlike in [Chapter 9](https://michael-franke.github.io/probLang/chapters/09-politeness.html), here you should use `factor`, not `condition`.

1. In the first model from [Chapter 2](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html), change only the meaning of the quantifier *some* so that it gets the following fuzzy truth values for states 0, ..., 3: 0.01, 0.5, 1, 1. Run the model and compare the predictions for the pragmatic listener's interpretation of *some* with this fuzzy semantics to the original one with a standard two-valued semantics. What are the differences? Which model's predictions do you think are better? Which model do you prefer conceptually? (Give short answers and good reasons for your judgements.)
2. In the first model from [Appendix Chapter 5](https://michael-franke.github.io/probLang/chapters/app-05-quantifiers.html), exchange the given two-valued semantics for all quantifiers with one that implements an S-shaped meaning function, using [logistic functions](https://en.wikipedia.org/wiki/Logistic_function). Concretely, instead of fixing a lower and upper bound for each quantifier, now fix a triple consisting of parameter $$k$$ and parameter $$x_0$$ of the [logistic function](https://en.wikipedia.org/wiki/Logistic_function), as well as a Boolean parameter that defines whether the quantifiers truth values are increasing or decreasing as the true state gets larger (stupidly put, whether its meaning is an S-shaped curve or a "mirrored S"-shaped curve). Fix parameter values for each quantifiers meaning function and test the model. Is this a better model than the second model from [Appendix Chapter 5](https://michael-franke.github.io/probLang/chapters/app-05-quantifiers.html)? To answer this question, think about what would naturally be free parameters in each model, which we would like to infer from empirical data (maybe after formulating a specific prior for each). Which model has more "degrees of freedom", so to speak? Which model, if any, could therefore make more precise predictions?

#### Exercise 3: Politeness

Let us use the first model from the [chapter on polite language use](https://michael-franke.github.io/probLang/chapters/09-politeness.html), but change the speaker's utility function. Previously the social utility function was independent of the true state. The result was a speaker who is a mixture between being totally honest and calling everything *amazing*. Let us now use a social utility function that does depend on the true state: the speaker wants the (literal) listener to believe that the state is near the true state *plus an additive constant* $$b$$, which will be our new parameter that substitutes the previous mixture parameter $$\phi$$. The new parameter $$b$$ regulates how much the speaker wants to induce exaggerated beliefs in the (literal) listener.

Concretely, epistemic utility remains as it was:

$$
U_{\text{epistemic}}(u; s) = \log(P_{L_0}(s \mid u))
$$

Social utility also remains the same (on the surface):

$$
U_{\text{social}}(u; s) = \mathbb{E}_{P_{L_0}(s' \mid u)}[V(s, s')]
$$

But now the value function $$V$$ is defined as a function of both the true state $$s$$ and the listener's inferred interpretation $$s'$$ as:

$$V(s,s') = -(s - (s'+b))^2$$

where $$b$$ regulates how much the speaker wants, on a social dimension, to have the listener have more positive beliefs about the true state than is warranted by reality.

Assume that $$\alpha = 3$$ in the new model and that the pragmatic listener has prior beliefs about $$b$$ as follows:

{% highlight js %}

var b = categorical({vs: [0,1,2,3,4],
                     ps: [5,4,3,2,1]})

{% endhighlight js %}

1. Implement this model by changing as little as possible in the code from [Chapter 9](https://michael-franke.github.io/probLang/chapters/09-politeness.html). 
2. Inspect the model's predictions for `speaker1(1,b)` with various values for $$b$$. Compare the new model's predictions to the old one for various calls to `speaker1(1,phi)` for various values of $$\phi$$. Which model, if any, is better? Which model, if any, is good? (Short answer, good reasons!)
3. Inspect the model's predictions for `pragmaticListener("good")`. If you have this function end with `return { b , state }` plot the results with `viz(listenerPosterior)` and interpret what you see.
4. Give a parameter value for $$\alpha$$ and a prior of the pragmatic listener for $$b$$ which produces predictions for both speaker and listener that you find (most) satisfying. Briefly justify your choice.

#### Exercise 4: Bayesian data analysis for reference games

Building on the code from [Appendix Chapter 4](https://michael-franke.github.io/probLang/chapters/app-04-BDA.html) we will run basically the same analyses for the same models, but for another data set. The data comes from [Franke & Degen (2016)](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0154854). The full data is available online ([here](http://journals.plos.org/plosone/article/file?type=supplementary&id=info:doi/10.1371/journal.pone.0154854.s007) and [here](http://journals.plos.org/plosone/article/file?type=supplementary&id=info:doi/10.1371/journal.pone.0154854.s008)), but we will work just with a summary that abstracts from individual participant's choices. To understand what these labels for objects and utterances mean, have a look at Figure 1 from [Franke & Degen (2016)](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0154854). Below is a cope snippet that includes this new data, and also allows you to flexibly (after possibly minor tweaks) reuse the code for the vanilla RSA model in order to apply it to the classic example from class, or the simple or complex condition from [Franke & Degen (2016)](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0154854). In this exercise we will only have one free parameter, namely $$\alpha$$, but no costs.

{% highlight js %}

// Frank and Goodman (2012) RSA model

var classic = {objects: ["blue_circle", "green_square", "blue_square"],
               utterances: ["blue", "green", "square", "circle"],
               salience: [71, 139, 30],
               prod_data: { blue_circle:  {blue:  9, circle: 135, green:   0, square:  0},
                            green_square: {blue:  0, circle:   0, green: 119, square: 25},
                            blue_square:  {blue: 63, circle:   0, green:   0, square: 81}
                          },
               comp_data: {
                 blue:   {blue_circle: 65, green_square:   0, blue_square: 115},
                 square: {blue_circle:  0, green_square: 117, blue_square:  62}
               },
               triggerObj: "green_square",
               triggerUtt : "blue"}

var simple = {objects: ["redhat_robot", "redhat_bigboy", "bluehat_randall"],
              utterances: ["bigboy", "redhat", "bluehat", "randall"],
              salience: [0.3, 0.26, 0.44], 
              prod_data: {redhat_bigboy: {bigboy:  779, 
                                          redhat: 120, 
                                          bluehat:   0, 
                                          randal:  0}},
              comp_data: {redhat: {redhat_robot: 689, 
                                   redhat_bigboy: 209, 
                                   bluehat_randall: 0}},
              triggerObj: "redhat_bigboy",
              triggerUtt: "redhat"}

var complex = {objects: ["redhat_bigboy", "bluehat_bigboy", "redhat_robot"],
               utterances: ["bigboy", "redhat", "bluehat"],
               salience: [0.21, 0.39, 0.4],
               prod_data: {redhat_bigboy: {bigboy:  427, 
                                           redhat: 471, 
                                           bluehat:   0, 
                                           bluehat:  0}},
               comp_data: {bigboy: {redhat_bigboy: 486, 
                                    bluehat_bigboy: 374, 
                                    redhat_robot: 0}},
               triggerObj: "redhat_bigboy",
               triggerUtt: "bigboy"}

var game = simple
var objects = game.objects
var utterances = game.utterances
var triggerUtt = game.triggerUtt
var salience = game.salience
var comp_data = game.comp_data
var prod_data = game.prod_data

{% endhighlight js %}

Compute the posterior over $$\alpha$$, for all three types of games, once given data from only production, once from only comprehension and once when conditioning on both data observations. For inference, use `method: "MCMC"` with parameters `samples: 10000` and `burn: 1000`. Send us your code. Report the expected value of the posterior and the interval where its probability density is non-negligible (the latter can be a rough approximate obtained from visual inspection). Send a screenshot for $$\alpha$$'s posterior when conditioning on the whole data from the simple game. Does anything strike you as noteworthy? Anything unexpected that you can explain when you look more closely at data and model?

