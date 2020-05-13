Chapter 20
================
Federico Andrade-Rivas
May 12, 2020

``` r
library(gapminder)

qdiff3 <- function(x, probs = c(0, 1)) {
  stopifnot(is.numeric(x))
  the_quantiles <- quantile(x, probs)
  max(the_quantiles) - min(the_quantiles)
}
```

#### 20.4 Be proactive about NAs

Many built-in R functions have an na.rm = argument through which you can specify how you want to handle NAs. Typically the default value is na.rm = FALSE and typical default behavior is to either let NAs propagate or to raise an error.

``` r
z <- gapminder$lifeExp
z[3] <- NA

quantile(gapminder$lifeExp)
```

    ##      0%     25%     50%     75%    100% 
    ## 23.5990 48.1980 60.7125 70.8455 82.6030

``` r
#quantile(z)
# does not allow to use it. 

quantile(z, na.rm =TRUE)
```

    ##     0%    25%    50%    75%   100% 
    ## 23.599 48.228 60.765 70.846 82.603

NOTE&gt; So quantile() simply will not operate in the presence of NAs unless na.rm = TRUE.
