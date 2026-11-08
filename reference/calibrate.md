# Calibrate all valid dates in a **c14_date_list**

Calibrate all dates in a **c14_date_list** with
[`Bchron::BchronCalibrate()`](https://andrewcparnell.github.io/Bchron/reference/BchronCalibrate.html).
The function provides two different kinds of output variables that are
added as new list columns to the input **c14_date_list**:
**calprobdistr** and **calrange**. **calrange** is accompanied by
**sigma**. See
[`?Bchron::BchronCalibrate`](https://andrewcparnell.github.io/Bchron/reference/BchronCalibrate.html)
and `?c14bazAAR:::hdr` for some more information.  
**calprobdistr**: The probability distribution of the individual date
for all ages with an individual probability \>= 1e-06. For each date
there's a data.frame with the columns **calage** and **density**.  
**calrange**: The contiguous ranges which cover the probability interval
requested for the individual date. For each date there's a data.frame
with the columns **dens** and **from** and **to**.

## Usage

``` r
calibrate(
  x,
  choices = c("calrange"),
  sigma = 2,
  calCurves = rep("intcal20", nrow(x)),
  ...
)

# Default S3 method
calibrate(
  x,
  choices = c("calrange"),
  sigma = 2,
  calCurves = rep("intcal20", nrow(x)),
  ...
)

# S3 method for class 'c14_date_list'
calibrate(
  x,
  choices = c("calrange"),
  sigma = 2,
  calCurves = rep("intcal20", nrow(x)),
  ...
)
```

## Arguments

- x:

  an object of class c14_date_list

- choices:

  whether the result should include the full calibrated probability
  dataframe ('calprobdistr') or the sigma range ('calrange'). Both
  arguments may be given at the same time.

- sigma:

  the desired sigma value (1,2,3) for the calibrated sigma ranges

- calCurves:

  a vector of values containing either intcal20, shcal20, marine20, or
  normal (older calibration curves are supposed such as intcal13).
  Should be the same length the number of ages supplied. See
  [BchronCalibrate](https://andrewcparnell.github.io/Bchron/reference/BchronCalibrate.html)
  for more information

- ...:

  passed to
  [BchronCalibrate](https://andrewcparnell.github.io/Bchron/reference/BchronCalibrate.html)

## Value

an object of class c14_date_list with the additional columns
**calprobdistr** or **calrange** and **sigma**

## Examples

``` r
calibrate(
  example_c14_date_list,
  choices = c("calprobdistr", "calrange"),
  sigma = 1
)
#> Calibrating dates... 
#>   |                                                          |                                                  |   0%  |                                                          |++                                                |   5%  |                                                          |++++++++++++++++++++++++++++++++++++++++++++++++  |  95%  |                                                          |++++++++++++++++++++++++++++++++++++++++++++++++++| 100%
#>  Radiocarbon date list
#>  dates: 9
#>  sites: 4
#>  countries: 5
#>  uncalBP: 9000 - 1000 
#> 
#> # A data frame: 9 × 22
#>   sourcedb method labnr c14age c14std calprobdistr   calrange sigma c13val site 
#>   <chr>    <chr>  <chr>  <int>  <int> <list>         <list>   <dbl>  <dbl> <chr>
#> 1 A        Conv   lab-1   1000     20 <df [212 × 2]> <df>         1    -15 Site…
#> 2 A        Conv   lab-2   2000     30 <df [386 × 2]> <df>         1    -20 Site…
#> 3 A        AMS    lab-3   3000     40 <df [490 × 2]> <df>         1    -25 Site…
#> 4 B        NA     lab-4   4000     50 <df [694 × 2]> <df>         1    -15 Site…
#> 5 B        AMS    lab-5   5000     50 <df [420 × 2]> <df>         1    -20 Site…
#> 6 B        AMS    lab-6   6000     60 <df [702 × 2]> <df>         1    -25 Site…
#> 7 C        AMS    lab-7   7000     70 <df [586 × 2]> <df>         1    -15 Site…
#> 8 C        AMS    lab-8   8000     80 <df [979 × 2]> <df>         1    -20 Site…
#> 9 C        AMS    lab-9   9000     90 <df>           <df>         1    -25 Site…
#> # ℹ 12 more variables: sitetype <chr>, feature <chr>, period <chr>,
#> #   culture <chr>, material <chr>, species <chr>, region <chr>, country <chr>,
#> #   lat <dbl>, lon <dbl>, shortref <chr>, comment <chr>
```
