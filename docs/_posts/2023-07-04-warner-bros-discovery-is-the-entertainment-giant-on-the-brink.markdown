---
layout: post
title: "Warner Bros. Discovery: Is the entertainment giant on the brink?"
date: 2023-07-06 09:02:03 +0100
categories: jekyll update
---

{%- include mathjax.html -%}

### Introduction

This post will be a little bit different from the previous two. I'm going to talk about a specific company, Warner Bros. Discovery---or WBD---the US-based media and entertainment giant with headquarters in New York, and its predecessor Discovery, Inc.

WBD was formed after the spin-off of Warner Media by AT&T, and its merger with Discovery, Inc. on 8 April 2022. Today, WBD owns and operates a portfolio of big names including Warner Bros. Entertainment (the famous film-making division), HBO, CNN, DC Entertainment (the parent of the comic book publisher DC Comics), and, for example, several sports channels such as Eurosport or BT Sport.

First, a short history of the two companies. The original company, Discovery, Inc., was established in 1985 and company operated a group of well known factual and lifestyle television brands popular in the US and beyond, such as the Discovery Channel, Animal Planet, Science Channel, and TLC. Warner Bros. was founded in 1923 by four brothers, Harry, Albert, Sam, and Jack Warner and established itself as a leader in the American film industry before diversifying into animation, television, and video games. Warner merged with Time Inc. in 1990 to become Time Warner. Finally, in 2018, Time Warner was acquired by AT&T which subsequently dissolved the Turner Broadcasting System as part of its reorganization of its media assets in 2019.

So why am I writing about WBD? Well, more than a year after the headlines-making merger, the company has a huge amount of debt which is becoming more expensive as interest rates rise. Is WBD close to default?

### Stock performance

Let's first look at the stock performance of the main actors: AT&T, Discovery, and the newly-formed Warner Bros. Discovery. The figure below shows the respective market caps (using post-merger share numbers) of the three companies, around, and after the merger.

![Stock performance of AT&T, Discovery, and Warner Bros Discovery before and after the merger.](/assets/images/20230706/fig-stock-performance-1.png)

The initial reaction of the market wasn't super positive; in fact, we can see that both AT&T and Discovery lost a non-negligible amount of their market caps immediately after the announcement. The latter company was already on a downward trajectory following the collapse of Bill Hwang's Archegos Capital that had invested heavily in the stock in the previous six months but also the sobering of some investors who'd overreacted to the initial success of Discovery's *discovery+* streaming platform.

Things haven't been going much better for WBD, stock performance-wise, since the merger was finalized. As of 3 July 2023, the stock is down 48% since the company's inception in April last year---hardly a positive result.

Why has the market been so cold to WBD? Well, the new stand-alone company paid AT&T \\$43 billion for Warner Media and assumed Discovery's \\$13.5 billion debt, creating a total gross debt of roughly \\$56.5 billion for itself. In simple terms, WBD is heavily leveraged, which is a big problem in the current macroeconomic environment with high, and rising, interest rates.

### WBD's leverage

Just *how* heavily leveraged is WBD, though? The figure below plots the "market" leverage ratios of the three companies defined as total book liabilities over total market cap. The dashed lines represent the 2.5th, 25th, 50th, 75th, and 97.5th percentiles of the market leverage ratios of the components of the S&P 500 index. Note that, in reality, the leverage ratio of WBD shot up on the day of the merger but WBD's exact financial position was only revealed later when with a new financial statements coming out---hence the delay in the figure.

![Market leverage ratios of AT&T, Discovery, and Warner Bros. Discovery along with selected percentiles of the leverage ratio of the S&P 500 index.](/assets/images/20230706/fig-leverage-1.png)

The picture is quite clear: WBD is *pretty* leveraged in relative terms, with the market leverage ratio moving around and often above the 97.5th percentile among the S&P 500 names. Before the merger, Discovery was in the lower half of the distribution of leverage ratios in this period.

You might counter and say that AT&T's leverage is also quite high; while this is true, AT&T operates in a different industry in which firms are generally more reliant on debt. Comparing WBD to peers such as Paramount or Disney shows that WBD has a lot of debt, given its industry.

### Measuring the default risk

So how much of a problem the high leverage is, really? One way would be to look at its credit rating. A quick check reveals, at the time of writing, a Moody's rating of [Baa3](https://www.moodys.com/credit-ratings/Warner-Bros-Discovery-Inc-credit-rating-600057551) and an S&P rating of [BBB-](https://disclosure.spglobal.com/ratings/en/regulatory/org-details/sectorCode/CORP/entityId/475824), which means that the two agencies very much agree on WBD's credit risk. Based on the regularly-published default rate tables, a rating of Baa3/BBB- is associated with a one-year default rate of approximately [0.22%](https://www.spglobal.com/ratings/en/research/articles/230425-default-transition-and-recovery-2022-annual-global-corporate-default-and-rating-transition-study-12702145#ID97533). While rating agencies are [typically good at predicting defaults](https://polachjan.github.io/jekyll/update/2023/05/10/are-credit-ratings-predicting-defaults.html), it is true that credit ratings are not very responsive to current market conditions and exhibit relatively low levels of variability.

To tackle this issue, banks and asset managers have long been using the Merton model to estimate a point-in-time measure of credit risk. In this model, the market value of equity is modeled as a call option on the assets of the company, with a strike price equal to a function of the company's nominal liabilities. The idea applied is the principle of limited liability that protects equity investors: shareholders would choose not to repay the firm's debt where the value of the firm is less than the value of the outstanding debt and, conversely, where firm value is greater than debt value, the shareholders would choose to repay---exercise their option---and not to liquidate.

To estimate the Merton model for a company, one needs to obtain some general macroeconomic indicators, such as the risk-free rate, and a bit of information about the company's financial position, not too dissimilar from that used in the charts above: the market cap and the amount of debt. The figure below shows the market cap and the estimated firm value for WBD:

![Market cap and firm value of Discovery and Warner Bros. Discovery.](/assets/images/20230706/fig-get-merton-out-1.png)

We observe that, after the merger, the two variables start to diverge; this is, to an extent, driven by the increased amount of debt the new company took on, which automatically pushed the firm value upwards. Is the increase high enough, however? As we know from above, the market cap went down which reduced the "buffer" the company had before it would become insolvent. The figure below shows the Merton-model-based one-year probability of default (PD):

![Estimated one-year probability of default of WBD using the Merton model.](/assets/images/20230706/fig-pd-1.png)

We see that, after the merger, the one-year PD went up rather dramatically to around 10% before settling just below this value for most of the time in the past few months. This represents a big jump compared to the risk of the pre-merger Discovery whose one-year PD was around 1.1% (still more than four times higher than the rating-implied PD of 0.22%) and puts the company into a highly speculative grade and seemingly quite close to default.

### Conclusion

So is WBD on the brink of default, then? Its current estimated one-year PD is around 10%, up from 7.5% in February this year and significantly higher than that of pre-merger Discovery of 1.1%. Despite this, it's not that easy to say---investors are definitely concerned about the high level of debt, a fact manifested in the low stock price and particularly its trend since the merger. This doesn't have to mean a default is imminent, however; it can also be that WBD is a great investment opportunity as the equity might be undervalued. Despite its high debt, the company manages to generate remarkable revenue for an entertainment and media enterprise. In the last year, the WBD recorded an impressive \\$41.3 billion in revenue, surpassing both Netflix and Paramount, which reported \\$32 billion and \\$30 billion in revenue, respectively.

WBD's debt presents a heavy burden to the company and one that is poised to become even more costly due to the anticipated rise in interest rates or, at the very least, their sustained elevation for a considerable duration. While the Merton model-implied PD might be slightly exaggerated, it is possible and indeed quite likely that the company's credit risk exceeds the level implied by the company's current credit ratings.
