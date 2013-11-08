---
title       : Introduction to R and RStudio
subtitle    : 
author      : Ian Lyttle
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
---

## Installation

You will need to install:

* Base R: [www.r-project.org](http://www.r-project.org/) 

  The `0-Cloud` archive works well. 

* RStudio IDE: [www.rstudio.com](http://www.rstudio.com)

In general, install the latest versions; the defaults work very well. 

Some helpful videos:

* [Installing R](http://youtu.be/X_oFb2iAdu8)
* [Installing RStudio](http://youtu.be/AZPbg29Plpw)

--- &my_twocol  w1:33% w2:65%

## Tour of RStudio IDE

*** =left

* Live demo

* Alternative: 

  View `Screencast` at
  
  [www.rstudio.com/ide](http://www.rstudio.com/ide/)

*** =right

 <img src="figure/rstudio-windows.png", width="100%"/>

---

## Packages

User-contributed packages are a big part of R's success.

Here's a subjective list of essential packages:

* `plyr`
* `reshape2`
* `ggplot2`
* `stringr`
* `lubridate`

To install a package, you can use the function `install_packages()` at the command line:


```r
install_packages("plyr")
```


Or you can use the RStudio IDE: [Video Demo](http://youtu.be/u1r5XTqrCTQ)



