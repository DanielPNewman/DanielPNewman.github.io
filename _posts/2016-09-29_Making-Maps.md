---
title: Python for an R and matlab user
layout: post
categories:
  - Uncategorized
---
I stumbled accross an interesting raw dataset from Vic Gov today with Melbourne house and apartment prices from 2005-March 2016 http://www.dtpli.vic.gov.au/property-and-land-titles/property-information/property-prices

Thought it worth a look 

It took me about 80 lines of R code to import the data from excel spreadsheet, tidy it, and then make this animated plot which I think is cool because you can get some insight from it in a much faster than just looking through the raw data in an excel spreadsheet. I thought it was cool how much faster Houses are going up in value compared to Apartments. Also interesting how most of the prices increases are in on the SouthEast side of Melb. 

I will drill into this dataset further when I get time, zooming in to certain suburbs, plotting vacant land over time (also included in the raw data), etc etc. Unfortunately the raw data didn't include any bedroom number or m^2 house size data, just Suburb and Median Price each year, but I'm sure I could probably find some if I searched hard enough. Another interesting thing is that there is also another dataset with finer time-resolution for 2016 only showing Apartment prices per month for the first 6 or so months of 2016 that I want to explore too when I get time


```r
#Set working directory where this script and the raw excel file are saved 
setwd("C:/Users/Dan/Documents/GitHub/MelbournePropertyPrices")

#load the required packages
library(ggmap)
```

```
## Loading required package: ggplot2
```

```r
library(readr)
library(ggplot2)
library(knitr)
library(dplyr)
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(tidyr)
library(readxl)
library(stringr)
#When installing Imagemagik from http://www.imagemagick.org/script/binary-releases.php
# remember to select the "instal legacy files such as convert.exe" option:
library(gganimate)
library(animation)

#Set decimal points and disable scientific notation
options(digits=3, scipen=999) 

#Load Maps
load("Melbourne.rda")

#Load Apartment price data
suburb_Apartment_2015<-read_excel("suburb_unit_2015.xls", col_names=F, skip = 3) %>% 
            na.omit() %>%
            distinct() %>%
            mutate(`Property Type`="Apartment")
#Load House Price Data and row bind it to Apartment price data 
property_2005_2015<-read_excel("suburb_house_2015.xls", col_names=F, skip = 3) %>% 
            na.omit() %>%
            distinct() %>%
            mutate(`Property Type`="House") %>%
            bind_rows(suburb_Apartment_2015)
rm(suburb_Apartment_2015)

#rename the columns 
names(property_2005_2015)<-c("suburb", 2005:2015, "Prelim 2016", "Change 2014-2015", "Change 2005-2015", "Growth PA 2005-2015","Property Type")

# assuming that "-" and "0" means data not available (NA), 
property_2005_2015[property_2005_2015 == 0] <- NA
property_2005_2015[property_2005_2015 == "-"] <- NA


#Read in the lat/long data
lat_long<-read_csv("Australian_Post_Codes_Lat_Lon.csv")  %>% 
    mutate(postcode=as.character(postcode)) %>%
    distinct() %>%
    select(-dc, -type)
```

```
## Parsed with column specification:
## cols(
##   postcode = col_integer(),
##   suburb = col_character(),
##   state = col_character(),
##   dc = col_character(),
##   type = col_character(),
##   lat = col_double(),
##   lon = col_double()
## )
```

```r
#create VIC only lat_long
VIC_lat_long<- lat_long %>% 
    filter(state=="VIC") %>%
    select(-postcode) %>%
    distinct() %>% 
    filter(suburb %in%  property_2005_2015$suburb)

#Merge VIC_lat_long into property_2005_2015
property_2005_2015<- full_join(property_2005_2015, VIC_lat_long,  by=c("suburb"))
rm(VIC_lat_long)


#melt from wide to long format
property_2005_2015<-property_2005_2015 %>% 
    gather(key=Year, value=`Median Price ($)`, -suburb, -lon, -lat, -state, -`Property Type`, -`Change 2014-2015`, -`Change 2005-2015`, -`Growth PA 2005-2015`) %>%
    mutate(`Median Price ($)`=as.numeric(`Median Price ($)`))
```


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



