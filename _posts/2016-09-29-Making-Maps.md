---
title: Median Melbourne Property Prices ($) from 2005-2016
layout: post
categories:
  - Uncategorized
---
I stumbled accross an interesting raw dataset from Vic Gov today with Melbourne house and apartment prices from 2005-March 2016 http://www.dtpli.vic.gov.au/property-and-land-titles/property-information/property-prices

Thought it worth a look... 

So I wrote some R code to import the data from excel spreadsheet, tidy it, and then make this animated plot which I think is cool because you can get some insight from it in a much faster than just looking through the raw data in an excel spreadsheet. I thought it was cool how much faster Houses are going up in value compared to Apartments. Also interesting how most of the prices increases are in on the SouthEast side of Melb. 

## Map

```r
p1<-ggmap(Melbourne) + 
    geom_point(data = property_2005_2015, 
               aes(x =lon, y= lat, frame = Year, size=`Median Price ($)`, 
                   colour = `Median Price ($)`), alpha=.75, shape="$") +
        scale_colour_gradientn(colours=rainbow(5)) +
        scale_radius (range = c(4, 14), trans = "identity", guide = "legend") +
    facet_wrap(~`Property Type`) +
    ggtitle("Median Melbourne Property Prices ($) from 2005-2016 \n")

p1 <- p1 + theme(aspect.ratio=1) +
        theme(axis.title.x = element_blank(), 
            axis.text.x  =  element_blank(),
            axis.title.x = element_blank(),
            axis.ticks.x=element_blank(),
            axis.text.y  =  element_blank(), 
            axis.title.y = element_blank(),
            axis.ticks.y=element_blank(),
            legend.title = element_text(size=12, face="bold"),
            legend.text = element_text(size = 12, face = "bold"),
            strip.text.x = element_text(size=12, face="bold"),
            plot.title = element_text(size = 14, face = "bold"),
            legend.position="right")  

gg_animate(p1, 'output.gif', ani.width = 1000, ani.height = 600, interval = 0.75)
```

```
## Executing: 
## ""convert" -loop 0 -delay 75 Rplot1.png Rplot2.png Rplot3.png
##     Rplot4.png Rplot5.png Rplot6.png Rplot7.png Rplot8.png
##     Rplot9.png Rplot10.png Rplot11.png Rplot12.png "output.gif""
```

```
## Output at: output.gif
```

![](https://github.com/DanielPNewman/MelbournePropertyPrices/blob/master/output.gif)

![](http://www.reactiongifs.us/wp-content/uploads/2013/10/nuh_uh_conan_obrien.gif)


{% include figure.html src="/public/images/Blog-29-09-2016/output.gif" %}