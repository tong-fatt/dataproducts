---
title       : Diamond Valuation
subtitle    : Price Predicator Based On Carat
author      : Tong-Fatt
job         : Data Explorer
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Executive Summary

Linear Model Regression of one predictor and one outcome is the starting point for anyone who want to understand how  predictive modelings work. At a high level, it is similar, in terms of the approach, to more complex modeling such as  generalized linear modeling, machine learning and neural network modeling.

It involves building a model that fits current set of observations and then use the model to predict after validation and testing.

The simple diamond valuation app (https://tong-fatt.shinyapps.io/shinyapp/)
for this project attempts to provide visualization of the basic principles behind linear model.

Source codes are available at https://github.com/tong-fatt/dataproducts 

--- .class #id 

## Correlation of Price vs Carats

1. The plot shows that the points are not randomly distributed.
2. The points are distributed along a line.
3. It suggests tht mass of diamond in carats is correlated to price.

![plot of chunk plot](assets/fig/plot-1.png)

--- .class #id 

## Building a model

1. The model is built by fitting a line across points (observations).
2. The best fit line means least distance between line and points
3. The model can then be used to predict expected outcome.

![plot of chunk plotline](assets/fig/plotline-1.png)

--- class #id
## Making Prediction

1. The accuracy of prediction depends on how best fit the line is.
2. It depends on the the quality of datasets used for training phase.
3. Prediction made can be validated visusally without going into computaion.


```r
fit <- lm(price ~ carat, data = diamond)
y <- diamond$price
yhat <- predict(fit)
e <- resid(fit)
max(abs(e -(y - yhat)))
```

```
## [1] 9.485746e-13
```

