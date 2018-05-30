---
title: "The inverse part II: ... and free lunches "
date: 2018-05-24
categories:
- data science
- finance
tags:
- theoretical machine learning
- static
keywords:
- arbitrage
- no free lunch theorem
- efficient market hypothesis
- 80-20 principle

autoThumbnailImage: false
thumbnailImagePosition: "top"
thumbnailImage: /images/20180523_free_lunch_cropped.jpg
coverImage: /images/20180522_covering_centred_2.jpg
metaAlignment: center
---
The 'no free lunch' (NFL) theorem resembles the Efficient Market Hypothesis (EMH) from [part I]({{<ref "post/The-inverse-part-I.md">}}) in that their true values lies in exactly the opposite of what they say at face value. The folk version of the NFL says that that no algorithm or optimisation technique will perform any better for all cases. Effectively, that there is no silver bullet or 'algorithmic arbitrage' that will magically solve all your needs. This theorem is frequently used to justify further fine-tuning on models. 
<!--more-->

Again, a closer examination of the underlying assumptions used in the actual proof is rather more insightful. Taking a modified example from [Wikipedia](https://en.wikipedia.org/wiki/No_free_lunch_theorem), there are two friends Amy and Bob who compete to see who can find the highest point (global maximum) of a mountain range first. A third friend Chloe acts as the judge and informs them once they've found the highest point. 

Amy's strategy is quite sensible: she heads in the direction where the slope rises up the steepest (gradient ascent) and once she reaches a local peak (local maximum), she restarts from a random location in the mountain range. The maverick Bob devises the opposite strategy of heading direction where the slope goes *down* the steepest. Each time he reaches a local trough (local minimum) he also restarts from a random location.

![Amy and Bob](/images/20180528_climb_cropped.jpg "Amy and Bob, on the starting line")*Up they go*

We expect that for different mountain ranges, Amy will generally find the highest point faster than Bob. However, aliens have come to join in the fun, planting a 60,000-foot pole in the deepest trough, which then becomes the highest point in the mountain range. This means that Bob now has the advantage against Amy. 

Furthermore, the aliens can potentially assist Bob in each and every mountain range - for every situation where aliens don't come, there's a scenario where aliens do come and Bob holds the advantage. So assuming that there's a 50-50 chance of aliens coming (i.e. averaged over all possible scenarios and mountain ranges), Amy and Bob are evenly matched, and neither strategy has an advantage against the other.

More broadly, aliens can plant the pole at any location (uniform randomness) to nullify the advantage of any strategy involving some form of trial-and-improvement, making it no better than random search. In other words, exhaustively enumerating all possible solutions to examine which one produces the best answer is the optimal strategy.

![Alien pole](/images/20180528_pole_cropped.jpg "In case you were wondering how Bob'll go up")*The alien pole*

Fortunately, uniform randomness doesn't usually hold in the real-world. All algorithms, heuristics and optimisation techniques from data science, machine learning, statistics, etc. implicitly depend on this, only differing by the further assumptions taken.

Under relatively mild conditions, we can use genetic algorithms & simulated annealing, while stronger assumptions (e.g. continuity, differentiability, convexity, etc.) allow us to use ever more efficient techniques (e.g. particle swarm optimisation, gradient descent, Newton-Raphson, etc.). 

Distribution bias relative to some variable is fundamental to allow hidden information and signals to be captured and used. When the solution space is uniformly random and holds no information, machine learning (or any kind of learning, including human input, for that matter) can't be used, since you cannot learn from experience.

The inverse provides the key takeaway: in the real world, there is distributional bias (the 80-20 principle) and the chance of aliens coming with 60,000-foot poles is less than 50%. Because of this, there will *always* be generic strategies and models that are inherently better than others - these strategies are more in tune with what the state of the world is actually like. 

For example, gradient descent is a good strategy for many different classes of problems. In terms of concrete models, XGBoost (and the newer CatBoost and LightGBM), often acts as the go-to option in data science competitions, because it'll very often produce a highly performant model that will beat the vast majority of other models in practice.

In fact, although there will be always be specific situations in which further-fine tuning can improve a top-performing generic model created through these strategies (e.g. by overfitting like there's no tomorrow), then this creates a bias-variance tradeoff and reduces the model's generalisability.

The ultimate free lunch in data science are automated pipelines that are capable of extracting and engineering features, cleaning and transforming data, and even tuning and ensembling models. In supervised learning, well-formed automated pipelines can defeat most other algorithms in practice, without any human intervention, under a wide range of different scenarios.

Here's to algorithmic arbitrage!

[Back to part I]({{<ref "post/The-inverse-part-I.md">}})