---
title: Median Property Prices 2005-2016, PART 2
layout: post
categories:
  - Uncategorized
---

I made this nice little .gif showing change over time in Median Melbourne Property Prices ($) from 2005-2016 in a [previous blog on 39 Sep 2016][1] :

{% include figure.html src="/public/images/Blog-29-09-2016/Melbourne.gif" %}

Well I've just come back to looking at that data set and this time I've plotted the **%** change per annum and overall, and also absolute **$** change from 2005-2016 on some interactive plots.
These plots allow you to zoom in, hover over a suburb to see more info, or click on a suburb to open a new window and explore that suburb in more detail.
 
The R code I used to make the plots below is [here][2] 

Notice that I've not yet figured out how to get the background map to render properly for these interactive plots. 
I've got [a question up on stack overflow][3] if you want to help out...
Although it looks like it might actually be [a bug in the new ggiraph package][4](https://github.com/davidgohel/ggiraph/issues/32) that is causing issue with raster objects.

**Explore below, it's interesting to see that SYNDAL has the greatest per annum and overall % growth, however it's TOORAK that has by far has the highest absolute $ growth over the same period of time.** 

<iframe width="800" height= "2750" frameborder="0" scrolling="no" src="/public/html/Blog-22-10-2016/MelbournePropertyPrices.html"></iframe>


[1]: http://dpnewman.com/Making-Maps/
[2]: https://github.com/DanielPNewman/MelbournePropertyPrices/blob/master/MelbournePropertyPrices.Rmd\
[3]: http://stackoverflow.com/questions/40166761/r-ggiraph-with-ggmap-for-interactive-reactive-longitude-and-latitude-points-sc
[4]: https://github.com/davidgohel/ggiraph/issues/32