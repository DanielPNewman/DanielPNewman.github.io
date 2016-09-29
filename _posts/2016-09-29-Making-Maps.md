---
title: Median Melbourne Property Prices ($) from 2005-2016
layout: post
categories:
  - Uncategorized
---
I stumbled across an interesting raw dataset from Vic Gov today with Melbourne, Australia house and apartment prices from 2005-March 2016 http://www.dtpli.vic.gov.au/property-and-land-titles/property-information/property-prices

Thought it worth a look... 

So I wrote some R code to import the data from excel spreadsheet, tidy it, and then make this animated plot which I think is cool because you can get some insight from it in a much faster than just looking through the raw data in an excel spreadsheet. I thought it was cool how much faster Houses are going up in value compared to Apartments. Also interesting how most of the prices increases are in on the SouthEast side of Melbourne. 

The R code I used to make the plot below is [here][1] 

*Click the plot to enlarge* 

{% include figure.html src="/public/images/Blog-29-09-2016/output.gif" %}


[1]: https://github.com/DanielPNewman/MelbournePropertyPrices/blob/master/MelbournePropertyPrices.Rmd