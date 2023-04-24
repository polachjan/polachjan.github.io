---
layout: post
title: "Cyber events and firms' performance"
date: 2023-04-24 17:40:55 +0100
categories: jekyll update
---

{%- include mathjax.html -%}

### Introduction

This post is my first proper one, so fasten your seat belts and be patient with me!

As part of some research I've been doing---rarely not focused on credit or climate risk---I've come across the [Cyber Events Database](https://cissm.umd.edu/cyber-events-database). Per its website, The Cyber Events Database collects publicly available information on cyber events, beginning in 2014 to the present day. It was created to address a lack of consistent, well-structured data necessary for making strategic decisions about how to invest resources to prevent and respond to cyber events. "What an interesting dataset!" I (almost) exclaimed and thought that I had to look more into it.

### Structural break in cyber risk after start of Covid-19?

![Monthly number of cyber events in time. Thick blue line is a LOESS smooth; vertical dashed line is on 1 March 2020.](/assets/images/20230424/fig-cyber-events-count-1.png)

Looking first at the total number of events in the figure above, we can see that, overall, cyber events have been on the rise in recent years. The second thing we notice is that the Covid-19 pandemic, whose start I've highlighted using the vertical line, might've brough about a structural break or shift in cyber crime. "Why?" I hear you ask---well, I can think of at least 5 reasons why the pandemic and the resulting rise in remote working and movements towards more digital ways of living might've increased the cyber events' incidence:

-   Increased use of personal devices: With remote working, employees are using their personal devices to access the bank's data and systems. These devices may not have the same level of security as the bank's own devices, making them more vulnerable to cyber-attacks.

-   Use of unsecured networks: Remote workers may use public Wi-Fi or other unsecured networks to connect to the bank's systems, making them more susceptible to cyber-attacks such as man-in-the-middle attacks.

-   Phishing attacks: Cybercriminals often use phishing attacks to gain access to sensitive information. With remote working, employees may be more vulnerable to phishing attacks as they are not in a secure office environment and may be distracted by other things at home.

-   Lack of physical security: Remote working means that employees may not have the same level of physical security as they do in the office. This can make it easier for cybercriminals to gain access to company data and systems.

-   Human error: With remote working, employees may be more likely to make mistakes, such as accidentally sending sensitive information to the wrong person or leaving their device unlocked and unattended.

Apart from the obvious security and operational implications, however, should companies be worried about cyber events? Do these events have any meaningful financial impact on the targets? Well, I'm putting my financial analyst hat on and set off to crunch some numbers!

### Cyber risk events negatively impact performance

To assess the impact of cyber events on firms' performance, I've used an approach typical in the event-study literature: I look at whether these events have any impact on the companies' equity returns and, hence, performance. The process has several steps:

1.  Get the data:
    -   [Cyber Events Database](https://cissm.umd.edu/cyber-events-database) from the Center for International Security Studies of the University of Maryland
    -   Equity prices of S&P 500 companies from Yahoo Finance. A nice next step would be to extend to sample to smaller and non-US entities
    -   Fama-French factors from [Kenneth French's website](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html)
2.  Estimate rolling, company-level Fama-French regressions to get abnormal returns. These are equal to the actual return minus the Fama-French-implied return
3.  Calculate cumulative abnormal returns at various horizons after the cyber events occurred
4.  Estimate the fixed effects panel data model
  
$$\sum \limits_{j=1}^\tau r_{i,t \rightarrow t+j} = \alpha + \beta_\tau \times event_{i,t} + \nu_i + \delta_t + \epsilon_{i,t},$$

where $ r_{i,t \rightarrow t+j} $ is the abnormal (log) return of company $ i $ between time $ t $ and time $ t+j $, $ event_{i,t} $ is a dummy variable equal to 1 if company $ i $ experienced a cyber event at time $ t $ and 0 otherwise, $ \nu_i $ are the company fixed effects, and $ \delta_t $ are the time fixed effects.

As the figure below shows, the results of this exercise indicate that there is a meaningful negative impact at various horizons after these cyber events. From 10 days on, the variance of the impact is bigger and hence the confidence intervals wider, but until, then the results are quite robust.

![Cumulative abnormal returns after cyber events based on the fixed effects model. Shaded areas represent the 90% and 95% confidence intervals around the point estimates.](/assets/images/20230424/fig-model-fe-1.png)

As a robustness check of the results of the fixed effects panel model, I also look at the distributions of the cumulative abnormal returns after events. The chart below shows the means and the confidence intervals around them of the cumulative abnormal returns after cyber events affecting the constituents of the S&P 500 index. The results are broadly similar to those obtained from the fixed effects regression---we can spot a negative impact that is statistically different from 0 at the 10% level in all cases and at the 5% level in most cases.

![Average cumulative abnormal returns after 78 cyber events of S&P 500 firms. Shaded areas represent the 90% and 95% confidence intervals around the means. Dashed red lines show the fixed effects model's results.](/assets/images/20230424/fig-abnormal-rets-1.png)

To summarize, this analysis suggests that, as one would intuitively expect, cyber events can and do have significant and economically meaningful impacts on firms' performance. Companies should actively build resilience in the IT security area of the business by design to minimize the exposure to cyber threats.
