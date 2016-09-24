---
title: Python for an R and matlab user
layout: post
categories:
  - Uncategorized
---
I managed to find a few spare hours this weekend so I'm trying out Python for the first time. I usually use Matlab and R for data processing, visualisation and statistics, but I wanted to give Python a try, since some of my colleagues at Vokke seem to really love it. 

It’s early days so I haven’t actually managed to produce anything useful with Python yet, but I thought I’d start to document the steps I’m taking to learn Python for data science, from the point of view of a Matlab and R user.  

1.	First off, I downloaded and installed [Anaconda] [1] which includes a distribution of Python, plus all the popular python packages you might need for data science.

2.	Then I searched for an IDE that I like the feel of. Anaconda comes with a couple of IDE’s including one called “Spyder” which I thought seemed very good. However, I ended up deciding on using the [Rodeo] [2] IDE for starters. The reason I decided on Rodeo is it is set out very similarly to the Rstudio and matlab IDEs, so I’m a little more comfortable with it to start with. 

3.	Third I started searching for the “python equivalents” to my favourite R packages for data science. I’m a major fan of most of [Hadley Wickham’s] [3]’s R packages including ggplot2, dplyr, tidyr, lubridate, readr and readxl.  So far for python I’ve found:

	* [Pandas] [4] seems to be the popular package for manipulating data in python, but another package that seems closer to [dplyr] [5] in R, is [dplython] [7] which maintains the functional programing ideas of dplyr, including my favourite feature from [magrittr] [8] and dplyr: the pipe-operator! 
	
	* The python plotting packages [seaborn] [9], [bokeh] [10] and [matplotlib] [11] all seem really nice. Matplotlib in particular seems very familiar to the plotting system in matlab. But since I’ve recently become very comfortable using Hadley’s ggplot2 ‘grammar of graphics’ type plotting system, I think [ggplot] [12] for python will suit me perfectly for starters! 
	
…annnd that’s all I’ve got time for today, BUT I plan to keep updating this post with more info, as I come across it, that I think could be useful for somebody learning python for data science who is coming from a background of R and Matlab….so stay tuned!! 

[1]: https://www.continuum.io/downloads 
[2]: https://www.yhat.com/products/rodeo 
[3]: http://hadley.nz/ 
[4]: https://github.com/pydata/pandas
[5]: https://github.com/hadley/dplyr 
[7]: https://github.com/dodger487/dplython 
[8]: https://github.com/smbache/magrittr 
[9]: https://github.com/mwaskom/seaborn 
[10]: https://github.com/bokeh/bokeh 
[11]: http://matplotlib.org/ 
[12]: https://github.com/yhat/ggplot 
