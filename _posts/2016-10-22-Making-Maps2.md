---
title: Median Property Prices 2005-16 - PART 2!
layout: post
categories:
  - Uncategorized
---

A few weeks back I made a blog post with this nice little .gif below, of change over time in Median Melbourne Property Prices ($) from 2005-2016 - see my [previous blog on 29 Sep 2016][1] :

{% include figure.html src="/public/images/Blog-29-09-2016/output.gif" %}

Well I've just come back to looking at that data set and this time I've plotted the **%** change per annum and overall, and also absolute **$** change from 2005-2016 on some interactive plots.
These plots allow you to zoom in, hover over a suburb to see more info, or click on a suburb to open a new window and explore that suburb in more detail.
 
The R code I used to make the plots below is [here][2]. 

**Explore below, it's interesting to see that SYNDAL has the greatest per annum and overall % growth, however it's TOORAK that has by far has the highest absolute $ growth over the same period of time.** 

<iframe width="800" height= "1200" frameborder="0" scrolling="no" src="/public/html/Blog-22-10-2016/MelbournePropertyPrices.html"></iframe>


[1]: http://dpnewman.com/Making-Maps/
[2]: https://github.com/DanielPNewman/MelbournePropertyPrices/blob/master/MelbournePropertyPrices.Rmd\
[3]: http://stackoverflow.com/questions/40166761/r-ggiraph-with-ggmap-for-interactive-reactive-longitude-and-latitude-points-sc
[4]: https://github.com/davidgohel/ggiraph/issues/32