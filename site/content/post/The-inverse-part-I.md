---
title: "The inverse part I: Why there's always arbitrage ..."
date: 2018-05-23
categories:
- data science
- finance
tags:
- theoretical finance
- static
keywords:
- arbitrage
- no free lunch theorem
- efficient market hypothesis
- 80-20 principle

autoThumbnailImage: false
thumbnailImagePosition: "top"
thumbnailImage: /images/20180528_money_cropped.jpg
coverImage: /images/20180522_covering_centred_2.jpg
metaAlignment: center
---
In my university days, we had a course named 'Finance and Financial Management', delivered by a former investment banker. Unsurprisingly, it was heavily oversubscribed (I studied maths in London), and any students landing a seat can count themselves very fortunate indeed. Rather less fortunately, half way through the first lecture, I wanted nothing better than to walk out the door.
<!--more-->

You see, the former investment banker told us to assume there's no arbitrage, which means that all assets are priced fairly. He also stated that similar assumptions will be necessary throughout the course. 

I was devastated: I took the course because I wanted to make money, so what's the point in learning models that will never do so? 

But clearly, various parts of the financial sector do use and make money from those models, or otherwise they'd be out of business. A few days later I had an epiphany, no doubt like countless other before me. 

The solution requires a change of perspective: the way to profit from those models is to notice when things don't add up somewhere, thus violating the equality and creating the opportunity for arbitrage.

A few weeks later, we were introduced to the efficient market hypothesis (EMH), which essentially proposes that it's impossible to beat the market, because the stocks always trade at their fair value.

"The true insight from the EMH," our professor said, "is that it's tough to beat the market." Fair enough, but there's another interesting implication that we can uncover by examining the key underlying assumption of the EMH.

![stock market](/images/20180523_stocks_cropped.jpg "Obviously this guy's not fast enough")*The stock market: fortune to the fast*

What happens if stock prices deviate from their fair values? Arbitrageurs take profit and drive the prices back where they belong. This constant negative feedback loop guarantees the efficiency of the stock market, but also necessitates the fact that there's always arbitrage. 

After all, arbitrageurs constantly profit, which is why there's arbitrage. So the other half of the story is that it's tough to beat the market unless you're faster than everyone else. But if you are always faster, then there's *always* arbitrage for you somewhere out there. 

As long as this is large enough to overcome market friction (e.g. transaction costs), you're pretty much guaranteed riskless profit.

[Continue to part II]({{<ref "post/The-inverse-part-II.md">}})