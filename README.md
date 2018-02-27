## Course content

Pragmatic reasoning is reasoning about what a speaker may have meant by an utterance at a given occasion. Pragmatic reasoning requires listeners to draw on different sources of possibly uncertain information from context and world-knowledge. Likewise, listeners need to reason about the speaker’s state of mind, her beliefs and goals, and possibly even about the speaker’s idiosyncratic use of language. To combine these sources of information about what the speaker has likely meant, we turn towards probabilistic modelling. This course will cover a sequence of increasingly complex models of listeners’ probabilistic inferences about speaker meaning, including applications to referential communication, scalar implicatures, vagueness, generics, politeness and tropes.

To harness the complexity of pragmatic reasoning we will formulate models in a probabilistic programming language called [WebPPL](http://webppl.org/), which the course will introduce and which will help us understand the models and calculate their (quantitative) predictions. We will exercise with model code by going through selected chapters of the web-book [Probabilistic Language Understanding](https://michael-franke.github.io/probLang/).

## Time & venue

The course will be held on two weekends. On each day we convene from 9am to 5pm. Notice the change of location after the first weekend:

- October 14 & 15: room 0.02, Wilhelmstraße 19 
- October 21 & 22: room 1.13, Wilhelmstraße 19 

## Schedule

##### Day 1

- Introduction to probabilistic pragmatics, the vanilla RSA model, reference games
  - [[slides]](slides/CompPrag-2017_intro.pdf)

- Probabilistic programming in WebPPL, Bayesian inference
  - [JavaScript / WebPPL basics](http://probmods.org/chapters/13-appendix-js-basics.html)
  - [BDAPPL: Introduction to randomness in programs](https://mhtess.github.io/bdappl/chapters/01-introduction.html)
  - [BDAPPL: Constructing posterior distributions](https://mhtess.github.io/bdappl/chapters/02-buildingModels.html)


##### Day 2

- vanilla RSA model & reference games
  - [PLU: Chapter I: Introducing the Rational Speech Act framework](https://michael-franke.github.io/probLang/chapters/01-introduction.html)
    - vanilla RSA & reference game paper: [Frank & Goodman (2012)](http://science.sciencemag.org/content/336/6084/998)

- RSA models for scalar implicature (vanilla version & extension with uncertain speakers)
  - [PLU, Chapter II: Enriching literal interpretations](https://michael-franke.github.io/probLang/chapters/02-pragmatics.html)
    - Scalar implicature paper: [Goodman & Stuhlmüller (2013)](https://web.stanford.edu/~ngoodman/papers/GS-TopiCS-2013.pdf)

- Non-literal language (hyperbole, irony, metaphor)
  - [PLU, Chapter III: Inferring the Question-Under-Discussion](https://michael-franke.github.io/probLang/chapters/03-nonliteral.html)
    - Hyperbole paper: [Kao et al., (2014)](http://cocolab.stanford.edu/papers/KaoEtAl2014-PNAS.pdf)
    - Metaphor paper: [Kao et al., (2014)](http://cocolab.stanford.edu/papers/KaoEtAl2014-Cogsci.pdf)
    - Irony paper: [Kao & Goodman (2015)](http://cocolab.stanford.edu/papers/KaoEtAl2015-Cogsci.pdf)

##### Day 3

- Adjectives ("John is tall.")
  - - [PLU, Chapter V: Fixing free parameters](https://michael-franke.github.io/probLang/chapters/05-vagueness.html)
  - RSA model paper: [Lassiter & Goodman (2016)](https://web.stanford.edu/~danlass/Lassiter-Goodman-adjectival-vagueness-Synthese.pdf)

- Politeness ("Your lecture was interesting!")
  - [PLU, Chapter VIII: Social reasoning about social reasoning](https://michael-franke.github.io/probLang/chapters/08-politeness.html)
    - White lies paper: [Yoon, Tessler, et al. (2016)](http://langcog.stanford.edu/papers_new/yoon-2016-cogsci.pdf)
    - Indirectness paper: [Yoon et al., (2017)](http://langcog.stanford.edu/papers_new/yoon-2017-cogsci.pdf)

- Experimental data & Bayesian data analysis
  - [PLU: Appendix Chapter II](https://michael-franke.github.io/probLang/chapters/app-02-BDA.html)
    - paper with data & model comparison: [Qing & Franke (2015)](http://www.sfs.uni-tuebingen.de/~mfranke/Papers/QingFranke_2013_Variations_on_Bayes.pdf)

##### Day 4

- further selected chapters from [Probabilistic Language Understanding](https://michael-franke.github.io/probLang/)

## Course material

### Probabilistic pragmatics

##### Main

[Probabilistic Language Understanding](https://michael-franke.github.io/probLang/): webbook on probabilistic models of pragmatic inference

**Caveat:** there are (at least) two versions of this book; we will be using only the version accessible through the link above!

##### Additional

- [Pragmatic language interpretation as probabilistic inference](http://langcog.stanford.edu/papers_new/goodman-2016-underrev.pdf): A recent review of the Rational Speech Act framework
- [Probabilistic pragmatics, or why Bayes' rule is probably important for pragmatics](https://www.degruyter.com/view/j/zfsw.2016.35.issue-1/zfs-2016-0002/zfs-2016-0002.xml): Position piece by Michael Franke and Gerhard Jaeger
- [Probabilistic Models of Cognition](http://probmods.org/): An introduction to computational cognitive science and the probabilistic programming language WebPPL
- [Modeling Agents with Probabilistic Programs](http://agentmodels.org): An introduction to formal models of rational agents using WebPPL
- [Forest](http://forestdb.org): A Repository for probabilistic models

### Probabilistic programming in WebPPL

##### Main

- [webppl.org](http://webppl.org): An online editor for WebPPL (use this for development!)
- [WebPPL Tutorials](https://mhtess.github.io/bdappl/): Basic tutorials for WebPPL
- [WebPPL documentation](http://webppl.readthedocs.io/en/master/)

##### Additional 

- [The Design and Implementation of Probabilistic Programming Languages](http://dippl.org): An introduction to probabilistic programming languages, WebPPL in particular
- [WebPPL-viz](http://probmods.github.io/webppl-viz/): A summary of the vizualization options in WebPPL
- [RWebPPL](https://github.com/mhtess/rwebppl): If you would rather use WebPPL within R



