---
layout: post
title: "Are credit ratings predicting defaults?"
date: 2023-05-10 16:40:55 +0100
categories: jekyll update
---

{%- include mathjax.html -%}

### Introduction

Agency credit ratings are widely recognized as a crucial tool for assessing the creditworthiness of various types of debt securities issued by corporations, governments, and other organizations. These ratings reflect the agency's independent assessment of an issuer's credit risk and the likelihood of default; the big three agencies are Moody's, Standard and Poor's, and Fitch. Moody's ratings, which I'm going to focus on in this post, range from the highest possible rating of "Aaa" to the lowest possible rating of "C" (which is effectively assigned to defaulted issues). Moody's uses a variety of factors to calculate its credit ratings, including financial metrics, industry trends, and geopolitical factors. These ratings are used by investors, financial institutions, and governments around the world to make informed decisions about investing, lending, and risk management.

But how predictive of default events Moody's ratings actually are? I'll try to answer this question in this short post below.

### Data

Credit ratings are publicly available in accordance with Rule 17b-7(b) issued by the U.S. Securities and Exchange Commission (SEC)---you can find more information about the rule [here](https://www.sec.gov/rules/final/2014/34-72936.pdf), for example. Moody's ratings---or, more precisely, Moody's Investors Service's ratings---for corporates, are available directly at Moody's website, after navigating to "Reports & Insights", then "Disclosures" in the "Reports" section, and finally to "Credit Rating Histories Required Under SEC Rule 17g-7(b)" under "Regulatory Affairs". The data is in the XBRL format whose syntax is similar to XML.

The dataset, after applying various simple filters, contains ratings for 3,143 issuers, with rating actions from July 2012 to April 2022. The figure below shows a distribution of the monthly ratings:

![Overall distribution of Moody's credit ratings for corporate issuers.](/assets/images/20230510/fig-rating-distr-1.png)

We see a distinct jump in the count between the "Baa3" and "Ba1" rating categories---the former is the lowest investment-grade rating, meaning that it is the cutoff point for securities that are considered relatively safe investments. Many issuers aim to achieve at least a "Baa3" rating to ensure that their securities are deemed investment-grade, which makes them more attractive to a wider pool of investors and decreases the number of "Ba1" ratings.

The next figure shows the distribution of the broad rating categories---obtained from the granular categories by removing the numerical modifiers---in time:

![Distributions of Moody's credit ratings for corporate issuers in time.](/assets/images/20230510/fig-rating-distr-time-1.png)

We see that, during the entire time period we're interested in, the size of the rated universe increased considerably as did the overall risk, albeit by a relatively small amount. The chart shows the evolution of the average rating in the same time period and confirms that the mean rating went up by slightly more than one rating notch.

![Mean Moody's credit rating for corporate issuers in time.](/assets/images/20230510/fig-rating-distr-mean-1.png)

### Defaults and predictive power

To what extent are Moody's ratings for corporates predictive of default behaviour then? To answer this question, one can take the following steps:

1. Define what "default" means. For the purposes of this post, I'm going to consider the two worst ratings, "Ca" and "C", as default states
2. Create a set of forward-looking default flags. Credit ratings should ideally be able to predict defaults (well) in advance to be useful to investors and other market participants; to this end, the standard procedure is to build an issuer-level default indicator equal to 1 if the issuer defaults within some point in the future and 0 otherwise, where "some point" typically means 1 year or 5 years
3. Measure the predictive power of ratings on the forward-looking default flags

First off, the figure below shows the forward-looking default rates (that is, the averages of the forward-looking default flags) in time by broad rating:

![Default rates by Moody's rating.](/assets/images/20230510/fig-def-rates-1.png)

Perhaps somewhat surprisingly, the defaults, across all five horizons, only come from the bottom two broad rating categories. In other words, if an instrument was at some point rated at least "Ba", it never defaulted within the next five years in this sample. This finding suggests that the ratings are, indeed, overall ordering the issuers in a sensible manner: the well-rated names don't tend to default.

The next figure below shows the calculated accuracy ratios (ARs) for this sample. ARs provide an easy-to-understand way of measuring predictive power; they express the ratio of the area above and under the cumulative accuracy profile (CAP) of the model under consideration versus the perfectly-discriminating model. The CAP of a model represents the cumulative number of positive outcomes along the y-axis versus the corresponding cumulative number of a classifying parameter---here the Moody's rating---along the x-axis. The CAP is distinct from the receiver operating characteristic (ROC) curve, which plots the true-positive rate against the false-positive rate. The AR can take values between zero and one: the closer the AR is to one, i.e., the larger the excess surface covered by the CAP curve, the higher the discriminatory power of the classification system.

![Accuracy ratios for the sample.](/assets/images/20230510/fig-ars-1.png)

This then answers the main question: the ratings are quite predictive. An AR of over 75% is generally really good in the credit risk space, and achieving this threshold across all five time horizons shows that the system clearly works. There are some caveats to this, however, namely:

- The sample is, by definition, only made up of rated names. These are generally big companies followed by several analysts as well as a big portion of the market, which makes the companies' financial situation transparent and the likelihood of default more predictable
- Some ratings are withdrawn before default. That is, we might be missing the defaults that would've happened had the ratings not been withdrawn. This fact increases the ARs, and so the real value is likely somewhat lower

As a robustness check, the next figure shows the ARs by month to make sure that the calculation on monthly data doesn't bias the result:

![Accuracy ratios for the sample.](/assets/images/20230510/fig-ars-monthly-1.png)

As before, the ARs are mostly in the 75--80% range and the main conclusion remains robust. To summarize, the Moody's ratings for corporates, in this particular sample from July 2012 to April 2022, have relatively strong predictive power of 77.5% at the one-year horizon.
