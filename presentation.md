---
title       : Historical baby name occurence finder
subtitle    : A Shiny app
author      : M.K. McGregor
job         : Developing Data Products
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : solarized_light      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides

--- .segue .quote .dark

<q> How common is your given name? Is your planned baby name too common?</q>

<style>
.dark q {
  color: white;
}
</style>

--- .class #id

## A new Shiny app

We propose a new simple Shiny app to give this information.

We make use of the US Social Security Administration database of baby names from 1880-2014
- Social security numbers (SSN) first issued in 1936, but only required for people with an income
- As of 1986, all children require a SSN at birth
- Data for males and females



--- .class #id 

## Let's take a look at the dataset




```r
head(babynames,3)
```

```
  year sex name    n       prop
1 1880   F Mary 7065 0.07238359
2 1880   F Anna 2604 0.02667896
3 1880   F Emma 2003 0.02052149
```

```r
tail(babynames,3)
```

```
        year sex    name n         prop
1825431 2014   M Zymiere 5 2.463303e-06
1825432 2014   M   Zyran 5 2.463303e-06
1825433 2014   M   Zyrin 5 2.463303e-06
```

- n: number of records with that name
- prop: proportion = n divided total number of applicants in that year


--- .class #id 

## An Example: "Gertrude"


```r
years <- babynames[which(babynames$name == "Gertrude"), "year"]
props <- 100*babynames[which(babynames$name == "Gertrude"), "prop"]
plot(years, props, xlab= "Year", ylab = "Percent of births (%)", type = "l", lwd=3, col="blue")
```

![plot of chunk plot](figure/plot-1.png)


