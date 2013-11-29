---
title       : Introduction to R & RStudio
subtitle    : http://ijlyttle.github.io/r_intro
author      : Ian Lyttle
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
assets:
  css: "http://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.css"

---
## Introduction




There are other options for open-source data analysis: Octave, Python, and Rapid Miner (GUI).

This presentation focuses on R and RStudio:

* R is an <b>outstanding</b> tool for prototyping a data-analysis.

* Everything demonstrated here is available without license fees.

* There is an investment in yourself to learn. It will be frustrating.

* Exchange of programs and snippets is simple exchange of text.

Warning:

* about 80% of data-analysis is simply wrestling with data

* does not lend itself to an introductory presentation

<i class="fa fa-link"></i> [Octave](http://www.gnu.org/software/octave/)
<i class="fa fa-link"></i> [Python](http://www.python.org/)
<i class="fa fa-link"></i> [Rapid Miner](http://rapidminer.com/) 

---
## This presentation

### Philosohpy

I want to show as many features as I can in an hour.

An hour, even a week, is not enough time for thoughtful discussion, demonstration, and practice.  

I have tried to leave links to other references, so that you may learn at your pace.

Everything in this presentation is reproducible - all the R code is shown.

### More help (?$%^#!!)

Google is your friend

Stack Overflow (likely someone has already asked)

Informal R networks at work

---
## Installation

You will need to install:

* Base R: [www.r-project.org](http://www.r-project.org/) 

  The `0-Cloud` archive works well. 

* RStudio IDE: [www.rstudio.com](http://www.rstudio.com)

In general, install the latest versions; the defaults work very well. 

Some helpful videos from Amanda Traud:

* <i class="fa fa-youtube"></i> [Installing R](http://youtu.be/X_oFb2iAdu8)
* <i class="fa fa-youtube"></i> [Installing RStudio](http://youtu.be/AZPbg29Plpw)

### Alternative

<i class="fa fa-link"></i> http://r-fiddle.org - try a little R coding - no installation - runs on your browser 

--- &my_twocol  w1:33% w2:65%
## Tour of RStudio IDE

*** =left

`Screencast` at
  
<i class="fa fa-play-circle-o"></i> [www.rstudio.com/ide](http://www.rstudio.com/ide/)

*** =right

 <img src="figure/rstudio-windows.png", width="100%"/>


--- &my_twocol  w1:33% w2:65%
## Vectors

*** =left

Collection of like objects

Assembled using `c()`

*** =right


```r
a <- c(1, 2, 3)
b <- c(4, 5, 6)
a
```

```
[1] 1 2 3
```

```r
b
```

```
[1] 4 5 6
```

```r
c(a, b)
```

```
[1] 1 2 3 4 5 6
```


*** =foot

GoogleDeveloplers <i class="fa fa-youtube"></i> 
[Create and Work With Vectors](http://youtu.be/YhQOV27pQfg)

--- &my_twocol  w1:33% w2:65%
## Vectors

*** =left

Can be:

* numeric
* character
* logical

*** =right


```r
c(1,2)
```

```
[1] 1 2
```

```r
c("Square D", "Merlin Gerin")
```

```
[1] "Square D"     "Merlin Gerin"
```

```r
c(TRUE, FALSE)
```

```
[1]  TRUE FALSE
```


*** =foot

GoogleDeveloplers <i class="fa fa-youtube"></i> 
[Character and Boolean Vectors](http://youtu.be/GKu5tw_bIpA)


--- &my_twocol  w1:33% w2:65%
## Lists 

*** =left

Collections of not-necessarily like objects

*** =right


```r
a <- list(title="Star Wars", year=1977)
a
```

```
$title
[1] "Star Wars"

$year
[1] 1977
```

```r
a$title
```

```
[1] "Star Wars"
```


*** =foot

GoogleDeveloplers <i class="fa fa-youtube"></i> 
[Lists](http://youtu.be/UffunYeERV0)

--- &my_twocol  w1:40% w2:55%
## Data Frames

*** =left

This is where the "action" is. 

Data frames are lists where each member is a vector of the same length.

Rows often called "observations"

Columns often called "variables"

*** =right


```r
a <- data.frame(title=c("Star Wars", 
                        "The Empire Strikes Back",
                        "Return of the Jedi"),
                year=c(1977, 1980, 1983))
a
```

```
                    title year
1               Star Wars 1977
2 The Empire Strikes Back 1980
3      Return of the Jedi 1983
```


*** =foot

To import a csv file into a data frame, use `read.csv()` function. 

Be mindful of options such as `quote`, `header`.

GoogleDeveloplers <i class="fa fa-youtube"></i>
[Loading Data and Working With Data Frames](http://youtu.be/qK1ElUMkhq0)

GoogleDeveloplers <i class="fa fa-youtube"></i>
[Loading Data, Object Summaries, and Dates](http://youtu.be/cx_3zWo4sUs)

---
## Packages

User-contributed packages are a big part of R's success.

Here's a subjective list of "essential" packages to be installed:

|               |                      |         |
| ------------- | -------------------- | ------- |
| `plyr`        | data transformation  | [Website](http://plyr.had.co.nz/), [JSS Article](http://www.jstatsoft.org/v40/i01/paper)  | 
| `reshape2`    | data transformation  | [Website](http://had.co.nz/reshape/), [JSS Article](http://www.jstatsoft.org/v21/i12/paper)  | 
| `ggplot2`     | visualization        | [Website](http://ggplot2.org/), [Cookbook](http://www.cookbook-r.com/Graphs/), [Reference](http://docs.ggplot2.org/current/)  |
| `stringr`     | work with strings    | [R Journal Article](http://journal.r-project.org/archive/2010-2/RJournal_2010-2_Wickham.pdf) |
| `lubridate`   | work with date-times | [JSS Article](http://www.jstatsoft.org/v40/i03/paper) |
<br/>

One consequence of user-contributed packages is a lack of consistency in interface.

Hadley Wickham's contribution is a set of useful packages that are well-written, well-documented, and well-consistent.

---
## Package Installation


To install a package, you can use the command-line:

```r
install_packages("reshape2")
install_packages("plyr")
install_packages("ggplot2")
```

To load a package:

```r
require("reshape2", quietly=TRUE)
require("plyr", quietly=TRUE)
require("ggplot2", quietly=TRUE)
```


`require()` and `library()` are used interchangeably.

Using RStudio IDE: Andrew Jahn  <i class="fa fa-youtube"></i>
[Installing Packages in R Studio](http://youtu.be/u1r5XTqrCTQ) 

--- &my_twocol  w1:40% w2:60%
## Case Study: U.S. REDTI

### Residential Energy Demand Temperature Index

*** =left

* import using `read.csv()`

* functions to tidy and clean data

* subsetting

* visualization using `ggplot2`

* model using `lm()`

* predict using `predict()`, `resid()`

*** =right

<img src="figure/us_redti_spring.jpg", width="85%"/>

*** =foot

Purpose is to highlight some steps in an analysis, not to show a complete analysis

<i class="fa fa-link"></i> [U.S. National Climatic Data Center](http://www.ncdc.noaa.gov/societal-impacts/redti/)

--- &my_twocol  w1:33% w2:65%
## Case Study: U.S. REDTI

### Import the data

Install these packages first, using `install.packages()`, if you don't have them.

```r
library(reshape2, quietly=TRUE)
library(plyr, quietly=TRUE)
library(ggplot2, quietly=TRUE)
```


Read csv file, parse into data frame

```r
us_redti_raw <- 
  read.csv("http://ijlyttle.github.io/r_intro/data/us_redti_consumption.csv")
```


<br/>
Preview: 
<i class="fa fa-link"></i> [us_redti_consumption.csv](https://github.com/ijlyttle/r_intro/blob/master/data/us_redti_consumption.csv) 

---  &my_twocol  w1:60% w2:40%
## Case Study: U.S. REDTI

*** =left

### Tidy data 

Variables are stored in columns

Observations are stored in rows

Single type of experimental unit per dataset 

*** =right


```r
head(us_redti_raw)
```

```
  Year  Winter Spring Summer Fall
1 1973  -99.99   2579   1499 1951
2 1974 3628.97   2489   1496 1884
3 1975 3627.84   2726   1489 1775
4 1976 3816.05   2424   1519 2047
5 1977 4374.53   2304   1513 1859
6 1978 3953.53   2600   1545 1922
```


This is <b>not</b> tidy data.

"Winter" is a season, not a variable.
<br/>

*** =foot

Hadley Wickham <i class="fa fa-vimeo-square"></i> [Tidy Data](http://vimeo.com/33727555)  <i class="fa fa-link"></i> [Paper](http://vita.had.co.nz/papers/tidy-data.pdf)


---  &my_twocol  w1:65% w2:35%
## Case Study: U.S. REDTI

### Tidy data

`reshape2` provides some tidying tools, such as the `melt()` function.

*** =left


```r
us_redti_tidy <- melt(
  us_redti_raw,              # input data frame 
  id.vars = "Year",          # vars *not* to be melted
  variable.name = "season",  # column for melted var-names
  value.name = "consumption" # column for melted values  
)
```


*** =right

```r
head(us_redti_tidy)
```

```
  Year season consumption
1 1973 Winter      -99.99
2 1974 Winter     3628.97
3 1975 Winter     3627.84
4 1976 Winter     3816.05
5 1977 Winter     4374.53
6 1978 Winter     3953.53
```


*** =foot
The function `dcast()` is used to reverse the process.

---  &my_twocol  w1:50% w2:50%
## Case Study: U.S. REDTI


```r
summary(us_redti_tidy)    # Useful functions to examine data
```

```
      Year         season    consumption  
 Min.   :1973   Winter:29   Min.   :-100  
 1st Qu.:1980   Spring:29   1st Qu.:1686  
 Median :1987   Summer:29   Median :2104  
 Mean   :1987   Fall  :29   Mean   :2301  
 3rd Qu.:1994               3rd Qu.:2678  
 Max.   :2001               Max.   :4406  
```

```r
str(us_redti_tidy)        # Can also use RStudio GUI
```

```
'data.frame':	116 obs. of  3 variables:
 $ Year       : int  1973 1974 1975 1976 1977 1978 1979 1980 1981 1982 ...
 $ season     : Factor w/ 4 levels "Winter","Spring",..: 1 1 1 1 1 1 1 1 1 1 ...
 $ consumption: num  -100 3629 3628 3816 4375 ...
```


---  &my_twocol  w1:50% w2:50%
## Case Study: U.S. REDTI

### Clean data

In our dataset, `-99.99` denotes missing data. In R, `NA` is used for this purpose.

Let's use a function to fix the "missing" values. This one was written by Hadley:


```r
fix_missing <- function(x, na.value) {
  x[x == na.value] <- NA                # for those values of x equal to na.value,
  x                                     # replace the value with NA                                   
} 
```


This function:

* takes a vector, `x`, and a value, `na.value`.

* returns a vector replicating `x`, where `na.value` is replaced by `NA`. 

Hadley Wickham <i class="fa fa-link"></i> 
[Advanced R: Functional Programming](http://adv-r.had.co.nz/Functional-programming.html)


---  &my_twocol  w1:50% w2:50%
## Case Study: U.S. REDTI

### Clean data

The `mutate()` function from the `plyr` package is useful.

Mutate a data frame by adding new or replacing existing columns

*** =left


```r
us_redti_clean <- mutate(
  us_redti_tidy,
  consumption = 
    fix_missing(consumption,  -99.99)
)
```


*** =right


```r
summary(us_redti_clean)
```

```
      Year         season    consumption  
 Min.   :1973   Winter:29   Min.   :1335  
 1st Qu.:1980   Spring:29   1st Qu.:1725  
 Median :1987   Summer:29   Median :2135  
 Mean   :1987   Fall  :29   Mean   :2387  
 3rd Qu.:1994               3rd Qu.:2866  
 Max.   :2001               Max.   :4406  
                            NA's   :4     
```


---  &my_twocol  w1:55% w2:45%
## Case Study: U.S. REDTI

*** =left

### Visualize data

`qplot()` from `ggplot2` package


```r
plot_cons <- qplot(
  x = Year,
  y = consumption,
  color = season,
  data = us_redti_clean
)
```



```r
plot_cons
```


*** =right

<img src="figure/unnamed-chunk-13.png" title="plot of chunk unnamed-chunk-13" alt="plot of chunk unnamed-chunk-13" style="display: block; margin: auto;" />


---  &my_twocol  w1:55% w2:45%
## Case Study: U.S. REDTI

*** =left

### Detrend data

We want to remove the time-trend effects for data after 1979.


```r
index_later <-     # identify observations
  us_redti_clean$Year > 1979

us_redti_later <-  # subset on observations
  us_redti_clean[index_later, ]

plot_cons +                 # add to plot
  geom_smooth(              # a smoothing geometry
    data = us_redti_later,  # using subset data
    method = "lm"           # and a linear model
  )
```


*** =right

<img src="figure/unnamed-chunk-15.png" title="plot of chunk unnamed-chunk-15" alt="plot of chunk unnamed-chunk-15" style="display: block; margin: auto;" />


---
## Case Study: U.S. REDTI

### Detrend data

Although we can do this more generally, we will demonstrate by subsetting on winter


```r
us_redti_later_winter <- us_redti_later[us_redti_later$season == "Winter", ]
```


The `lm()` function returns a linear model.


```r
model_time_winter <- lm(
  consumption ~ Year,            # independent variable ~ dependent variable(s), "1" implied
  data = us_redti_later_winter   # man page is very useful
)
coef(summary(model_time_winter)) # summary() gives more info; we want just coefficients for now
```

```
             Estimate Std. Error t value  Pr(>|t|)
(Intercept) -56817.64  12327.119  -4.609 1.697e-04
Year            30.38      6.193   4.906 8.531e-05
```


---
## Case Study: U.S. REDTI

### Detrend data

Use `predict()` to establish baseline at 1980


```r
consumption_baseline <- 
  predict(model_time_winter, newdata=data.frame(Year = 1980))

consumption_baseline
```

```
   1 
3341 
```


---
## Case Study: U.S. REDTI

### Detrend data

Use `resid()` to get difference between data and model

Use `mutate()` to create detrended data frame

Create new variable, `detrended`, to denote if observation is detrended


```r
us_redti_later_winter_dt <- mutate(
  us_redti_later_winter,
  detrended = TRUE,
  consumption = consumption_baseline + resid(model_time_winter) 
)

us_redti_later_winter$detrended <- FALSE
```


---  &my_twocol  w1:50% w2:50%
## Case Study: U.S. REDTI

### Detrend data

Compare original and detrended data-frames

*** =left


```r
head(us_redti_later_winter)
```

```
   Year season consumption detrended
8  1980 Winter        3472     FALSE
9  1981 Winter        3630     FALSE
10 1982 Winter        3536     FALSE
11 1983 Winter        3285     FALSE
12 1984 Winter        3438     FALSE
13 1985 Winter        3465     FALSE
```


*** =right


```r
head(us_redti_later_winter_dt)
```

```
   Year season consumption detrended
8  1980 Winter        3472      TRUE
9  1981 Winter        3600      TRUE
10 1982 Winter        3476      TRUE
11 1983 Winter        3194      TRUE
12 1984 Winter        3317      TRUE
13 1985 Winter        3313      TRUE
```




---  &my_twocol  w1:50% w2:50%
## Case Study: U.S. REDTI

*** =left

### Detrend data


```r
# combine data frames by binding rows
us_redti_combined <- rbind(
  us_redti_later_winter,
  us_redti_later_winter_dt
)

plot_detrend <- 
  qplot(
    x = Year,
    y = consumption,
    color = detrended,
    data = us_redti_combined,
    geom = "point"
  ) + 
  geom_smooth(method="lm")
```


*** =right

<img src="figure/unnamed-chunk-23.png" title="plot of chunk unnamed-chunk-23" alt="plot of chunk unnamed-chunk-23" style="display: block; margin: auto;" />


--- &my_twocol  w1:33% w2:65%
## Case Study: U.S. Energy 2012

*** =left

### Demonstration

* import using `read.csv()`

* aggregation using `plyr`

* visualization using `ggplot2`

* interactivity using `rCharts`

Purpose is to show different ways of visualizing same data.

*** =right

 <img src="figure/primary_energy_consume_source_sector_2012_endnotes.jpg", width="100%"/>

*** =foot

Source: <i class="fa fa-link"></i> [U.S. Energy Information Administration](http://www.eia.gov/energy_in_brief/article/major_energy_sources_and_users.cfm)

---
## Case Study: U.S. Energy 2012

### Import the data


```r
# install these packages, if you don't have them
library(plyr, quietly=TRUE)
library(ggplot2, quietly=TRUE)
# read this csv file; parse into a data frame 
us_energy_2012 <- read.csv("http://ijlyttle.github.io/r_intro/data/us_energy_2012.csv")
```


```r
# advanced
install.packages(devtools)
library(devtools, quietly=TRUE) # requires RTools from CRAN 
install_github(repo="rCharts", username="ramnathv", ref="dev")
library(rCharts, quietly=TRUE)
```



<br/>
 Preview: <i class="fa fa-link"></i> [us_energy_2012.csv](https://github.com/ijlyttle/r_intro/blob/master/data/us_energy_2012.csv)

---
## Case Study: U.S. Energy 2012

### Examine the data


```r
head(us_energy_2012) # print the first six lines
```

```
       source                 sector consumption
1   petroleum         transportation      24.637
2   petroleum             industrial       7.981
3   petroleum residential_commercial       1.735
4   petroleum         electric_power       0.347
5 natural_gas         transportation       0.780
6 natural_gas             industrial       8.580
```


Note that the consumption is expressed in quads ($10^{15}$ BTU).

Keeping track of metadata such as units is a challenge.

---
## Case Study: U.S. Energy 2012

### Aggregate by source


```r
us_energy_by_source_2012 <- ddply(  # transform data-frame to data_frame
  .data = us_energy_2012,           # input data-frame
  .variable = .(source),            # split by variable "source"
  .fun = summarize,                 # use summarize() function 
  consumption = sum(consumption)    # column "consumption" in output data-frame
)                                   #   is sum of column "consumption" in input data-frame

us_energy_by_source_2012
```

```
       source consumption
1        coal        17.4
2 natural_gas        26.0
3     nuclear         8.1
4   petroleum        34.7
5   renewable         8.9
```


---
## Case Study: U.S. Energy 2012

### Aggregate by sector


```r
us_energy_by_source_2012 <- ddply(  # transform data-frame to data_frame
  .data = us_energy_2012,           # input data-frame
  .variable = .(sector),            # split by variable "sector"
  .fun = summarize,                 # use summarize() function 
  consumption = sum(consumption)    # column "consumption" in output data-frame
)                                   #   is sum of column "consumption" in input data-frame

us_energy_by_source_2012
```

```
                  sector consumption
1         electric_power      38.288
2             industrial      20.352
3 residential_commercial       9.886
4         transportation      26.574
```


--- &my_twocol  w1:45% w2:55%
## Case Study: U.S. Energy 2012

*** =left

### Stacked bar plot

```r
plot_1 <- qplot(
  x = source,
  y = consumption,
  fill = sector,
  data = us_energy_2012,
  geom = "bar",
  stat = "identity",
  ylab = "consumption (quads)",
  main = "U.S. Energy Consumption 2012"
)
```


*** =right

<img src="figure/plot_1_vis.png" title="plot of chunk plot_1_vis" alt="plot of chunk plot_1_vis" style="display: block; margin: auto;" />


--- &my_twocol  w1:45% w2:55%
## Case Study: U.S. Energy 2012

*** =left

### Dodged bar plot

```r
plot_2 <- qplot(
  x = source,
  y = consumption,
  fill = sector,
  data = us_energy_2012,
  geom = "bar",
  stat = "identity",
  position = "dodge",
  ylab = "consumption (quads)",
  main = "U.S. Energy Consumption 2012"
)
```


*** =right

<img src="figure/plot_2_vis.png" title="plot of chunk plot_2_vis" alt="plot of chunk plot_2_vis" style="display: block; margin: auto;" />


--- &my_twocol  w1:45% w2:55%
## Case Study: U.S. Energy 2012

*** =left

### Faceted bar plot

```r
plot_3 <- qplot(
  x = source,
  y = consumption,
  data = us_energy_2012,
  geom = "bar",
  stat = "identity",
  facets = sector ~ .,
  ylab = "consumption (quads)",
  main = "U.S. Energy Consumption 2012"
) + 
  coord_flip()
```


*** =right

<img src="figure/plot_3_vis.png" title="plot of chunk plot_3_vis" alt="plot of chunk plot_3_vis" style="display: block; margin: auto;" />


--- &my_twocol  w1:40% w2:60%
## Case Study: U.S. Energy 2012


```r
# Using `rCharts` and `NVD3` (http://nvd3.org/)
n1 <- nPlot(consumption ~ source, group="sector", data=us_energy_2012, type='multiBarChart')
n1$yAxis(axisLabel = "consumption (quads)", width=45)
```


<iframe src=figure/nvd3_vis.html seamless></iframe>


--- &my_twocol  w1:40% w2:60%
## Case Study: U.S. Energy 2012


```r
# Using `rCharts` and `NVD3` (http://nvd3.org/)
n1 <- nPlot(consumption ~ sector, group="source", data=us_energy_2012, type='multiBarChart')
n1$yAxis(axisLabel = "consumption (quads)", width=45)
```


<iframe src=figure/nvd3_2_vis.html seamless></iframe>

--- &my_twocol  w1:60% w2:40%
## Case Study: U.S. Energy 2012

*** =left

```r
# Using `rCharts` to make a Sankey plot
sankey_lib <- 
  'http://timelyportfolio.github.io/rCharts_d3_sankey'
sankeyPlot <- rCharts$new()
sankeyPlot$setLib(sankey_lib)
sankeyPlot$set(
  data = summarize(
    us_energy_2012[us_energy_2012$consumption > 0, ],
    source,
    target = sector,
    value = consumption
  ),
  layout = 32,
  nodeWidth = 20, nodePadding = 5,
  width = 375, height = 475
)
```


<i class="fa fa-link"></i> [timelyportfolio Sankey diagrams](http://timelyportfolio.github.io/rCharts_d3_sankey/example_build_network_sankey.html)
*** =right

<iframe src=figure/sankey_vis.html seamless></iframe>


---
## Further Learning

| Introductory         |            |
|----------|------------|
| Hadley Wickham <i class="fa fa-youtube"></i> [Google Tech Talk](http://youtu.be/TaxJwC_MP9Q) | Use of programming languages for data analysis <i class="fa fa-coffee"></i> |
| GoogleDeveloplers <i class="fa fa-youtube"></i>  [Introduction to R](http://www.youtube.com/playlist?list=PLOU2XLYxmsIK9qQfztXeybpHvru-TrqAP) | Great set of short videos introducing the basics |
| Computerworld <i class="fa fa-link"></i> [Beginner's Guide to R](http://www.computerworld.com/s/article/9239625/Beginner_s_guide_to_R_Introduction)| Nice walktrough of base R for non-programmers  |
|  Norman Matloff <i class="fa fa-book"></i> [The Art of R Programming](http://amzn.com/1593273843)| Solid tutorial introduction |
| Garrett Grolemund  <i class="fa fa-book"></i> [Data Analysis with R](http://amzn.com/1449359019)  | Incorporates Hadley packages `plyr`, `ggplot2`. Avail. June 2014|
|  Hadley Wickham <i class="fa fa-vimeo-square"></i> [Tidy Data](http://vimeo.com/33727555)  <i class="fa fa-link"></i> [Paper](http://vita.had.co.nz/papers/tidy-data.pdf) | Essential work on organizing data (even for non-R people) <i class="fa fa-coffee"></i> |

<br/>

| Advanced         |            |
|----------|------------|
| Yihui Xie  <i class="fa fa-link"></i> [knitr](http://yihui.name/knitr/) | Reproducible research: dynamic report generation
|  Ramnath Vaidyanathan <i class="fa fa-github"></i>  [slidify](http://slidify.org/) | Create html5 presentations, blog posts using R |
| Ramnath Vaidyanathan  <i class="fa fa-github"></i> [rCharts](http://ramnathv.github.io/rCharts/) | Create `d3.js` charts using R |
|  RStudio <i class="fa fa-link"></i> [shiny](http://www.rstudio.com/shiny/) | Create interactive web-applications using R |
|  Hadley Wickham <i class="fa fa-link"></i> [Advanced R](http://adv-r.had.co.nz/) | Learn what's behind the curtain  |

<i class="fa fa-coffee"></i> - longer video
