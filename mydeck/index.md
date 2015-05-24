---
title       : Mortgage Calculator App
subtitle    : A quick introduction
author      : jmfuch02
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : zenburn      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

With interest rates in the United States at all-time lows, more people are looking to buy a house or refinance their current mortgage.

This tool shows you much prinicipal you will have on a loan at a given time, so you can compare different mortgage rates.

--- .class #id 

## Amortization Explained

The amount of principal left at any point in time can be calculated this way:

$p\left ( t \right ) = P \left [ \frac{(1+i/12)^{t}-1}{(1+i/12)^{n}-1} \right ]$

where:

P is the original loan amount

i is the interest rate

t id the number of months passed

n is the total number of months in the loan

Source: http://en.wikipedia.org/wiki/Amortization_calculator

--- .class #id

## An Example

Assume P = $100,000, i = 3.5%, and the term is 30 years.
We want to see what the principal should be at month 100.


```r
p <- function (t, P, i, n) {
    top = ((1 + (i / 12)) ^ t) - 1
    bottom = ((1 + (i / 12)) ^ n) - 1
    p = P * (1 - top/bottom)
    return(p)
    }

p(100, 100000, .035, 30*12)
```

```
## [1] 81757.36
```

If you check month 101 in the App, you will find $81,757.3573.
You have to check the next month because of a slight different in how the 2 formulas are calculated

--- .class #id

## Recommendations For Further Improvement

- Show the monthly payment amount
- Add lines showing how much of the payment goes to interest and principal each month
- Add comparison feature for different loans
