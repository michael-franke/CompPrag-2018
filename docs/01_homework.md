## Homework 1: Coins & scalars

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>

Solutions are due on Friday, October 20th by noon. Please send your solutions as a zipped archive, including two *.webppl files with your code and in-code comments to [Michael Franke](mailto:michael.franke@uni-tuebingen.de). Please name the archive `lastName_HW1.zip` and the included files `lastName_HW1_ex1.webppl` and `lastName_HW1_ex2.wppl`. 

#### Exercise 1: Coin flips

Use the code from [Chapter II of the BDAPPL Webbook](https://mhtess.github.io/bdappl/chapters/02-buildingModels.html) to calculate your rational beliefs about the bias of a coin. Suppose that your prior beliefs about the coin's bias $$\theta$$ are given by a Beta distribution with parameters `a = 0.5` and `b = 0.5`. In WebPPL, you can construct this prior distribution by:

```js
var priorDistribution = Beta({a: 0.5, b: 0.5})
```

The coin was flipped 30 times and we observed 25 heads. Use `viz` and `Infer` to generate a density plot from samples from the posterior distribution of the coin's bias after observing 25 heads out of 30 flips. Would you conclude from inspecting this plot that it is likely that the coin is fair, i.e., has a bias $$\theta = .5$$? (Give your short answer as a comment at the end of the code.)

**Hint**: all of the code you need (except for a change in the prior distribution and a change in what was observed) can in principle be copy-pasted from [the relevant chapter](https://mhtess.github.io/bdappl/chapters/02-buildingModels.html), in particular one of the last code boxes on that page. However, please (re-)name variables appropriately. For example, what was a child before is now a coin flip. The propensity of helping is the probability of landing heads. Etc.


#### Exercise 2: Scalar implicatures

Use the code from the first model of [Chapter II from Probabilistic Language Understanding](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html). Extend the model in the following way:

1. Currently, the code fixes that there are only 3 apples whose color the conversation is about. Make the code more general, by having a variable `total_apples` which we can set in the beginning of the code to any arbitrary (but reasonable) value. (**Hints*:* the function `_.range(total_apples+1)` might be really handy; moreover, don't forget to take care of the semantics, in particcular the meaning of "all".)
2. Include messages with the following semantics:
- "one", "two" and "three" with a (natrual?) exact number reading (e.g., "one" is true iff exactly 1 apple is red)
- "many" which is true for any number of red apples bigger than 4
- "most" which is true for any number of red apples bigger than half of `total_apples`

Create a histrogram of the pragmatic listener's interpretation of "some" when `total_apples = 10`.
