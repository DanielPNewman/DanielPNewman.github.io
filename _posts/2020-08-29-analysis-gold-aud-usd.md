---
layout: post
title: Thoughts on Gold/AUD/USD
author: Daniel Newman
description: Gold exposure via the ASX without AUD/USD timing risk
---

Since different Australian based friends this year have asked for my thoughts on a good way to get direct exposure to the gold price via the ASX, I figured I’d share my answer in a quick public post in case it is useful to others. 

A neat way to hold gold via the ASX and also be impartial AUD/USD exchange rate timing, is holding a split of half QAU half PMGOLD.  I lay out my analysis and reasons for this below.

QAU and PMGOLD are both ETFs that track the price of gold. The key difference between them is that QAU is hedged back to AUD, so when AUD strengthens QAU does relatively better than MPGOLD. On the other hand, PMGOLD is USD based, so when AUD falls against USD, PMGOLD does relatively better than QAU. 

The plot below shows that these gold price tracking ETFs, either hedged to AUD (QAU.AX) or non-hedged (PMGOLD.AX) can perform very differently over time due to AUD/USD movements.  

![]({{"/images/gold1.png"|absolute_url}})

Since it’s too hard to accurately predict how AUD/USD fx rates will move going forward, holding half of each QAU/PMGOLD means one would not have to worry about this - it eliminates timing risks related to AUD/USD value fluctuations. 

Below I lay out real examples on the timing/currency point. First, if one happened to purchase a gold ETF via the ASX in Jan 2020 and then needed to sell for some during March 2020, the returns were great if they picked PMGOLD and poor if they picked QAU. This difference driven by the AUD/USD fx rate, as depicted below:

![]({{"/images/gold2.png"|absolute_url}})

On the other hand, if one happened to purchase mid-March 2020 and needed to sell some now then results are the opposite - returns would have been great if they’d picked PMGOLD and poor if they picked QAU. Again, the difference driven by the AUD/USD fx rate, as depicted below:

![]({{"/images/gold3.png"|absolute_url}})

The final figure below, like the first figure above, shows the time period from the start of 2020 to now, but includes an extra line showing the returns of holding half QAU/PMGOLD. This half AUD-hedged/non-hedged approach gives a way for Aussies to get gold exposure that does not have AUD/USD timing risk. 

![]({{"/images/gold4.png"|absolute_url}})


I’ll provide my code used to get/wrangle the data and make the figures [here](1).

[1]: https://github.com/DanielPNewman/gold
