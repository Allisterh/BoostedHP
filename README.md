# Project of BoostedHP Package   ![image](https://github.com/chenyang45/A_N/blob/master/graph/gganimation/preview.gif)

R package for Peter Phillips and Zhentao Shi (2018): "Boosting the Hodrick-Prescott Filter"

version : 0.5.0

2018-07-17 

## Introduction

This is an accompanying repository for the paper:

Peter Phillips and Zhentao Shi (2018): "Boosting the Hodrick-Prescott Filter" (to provide the arxiv link)

The main function is: 

* `BoostedHP.R` contains the R function to implement the automated boosted HP filter.
The inputs and outputs are detailed in the beginning of the function.

Comments are welcome. 

#### Installation

A very preliminary R package can be installed by running in `R`
```
install.packages("devtools")
devtools::install_github("chenyang45/BoostedHP/BoostedHP")
library("BoostedHP")
```
The package is in progress.

#### Example
```
data("IRE") # Ireland Annual GDP example in the paper, which is saved in the package.

lam = 100 # tuning parameter for the annual data

# raw HP filter
bx_HP = BoostedHP(IRE, lambda = lam, iter= FALSE)

# by BIC
bx_BIC = BoostedHP(IRE, lambda = lam, iter= TRUE, test_type = "BIC")

# by ADF
bx_ADF = BoostedHP(IRE, lambda = lam, iter= TRUE, test_type = "adf", sig_p = 0.050)

# summarize the outcome
outcome = cbind(IRE, bx_HP$trend, bx_BIC$trend, bx_ADF$trend) 
matplot(  outcome, type = "l", ylab = "", lwd = rep(2,4)  )
```

