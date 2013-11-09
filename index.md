---
title       : Introduction to R and RStudio
subtitle    : 
author      : Ian Lyttle
job         : Analytics for Solutions, Schneider Electric
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}

---

## Installation

You will need to install:

* Base R: [www.r-project.org](http://www.r-project.org/) 

  The `0-Cloud` archive works well. 

* RStudio IDE: [www.rstudio.com](http://www.rstudio.com)

In general, install the latest versions; the defaults work very well. 

Some helpful videos from Amanda Traud:

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
## Vectors


---
## Data Frames


---
## Importing Data from CSV


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

To install a package, you can use the function `install_packages()` at the command line:


```r
install_packages("plyr")
```


Or you can use the RStudio IDE: [Video Demo](http://youtu.be/u1r5XTqrCTQ) from Andrew Jahn


---
## References

<span class="glyphicon glyphicon-star"></span>

|          |            |
|----------|------------|
|  Amanda Traud: [R Installation](http://youtu.be/X_oFb2iAdu8) & [RStudio Installation](http://youtu.be/AZPbg29Plpw)        |  Video walkthrough of installation process    |
| GoogleDeveloplers: [Introduction to R](http://www.youtube.com/playlist?list=PLOU2XLYxmsIK9qQfztXeybpHvru-TrqAP) | Great set of short videos introducing the basics |
| Andrew Jahn: [RStudio: Package Installation](http://youtu.be/u1r5XTqrCTQ) | How to install and detach R packages |
