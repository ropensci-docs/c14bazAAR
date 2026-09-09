# Fuse multiple **c14_date_list**s

This function combines **c14_date_list**s with
[`dplyr::bind_rows()`](https://dplyr.tidyverse.org/reference/bind_rows.html).  
This is not a joining operation and it therefore might introduce
duplicates. See
[`c14bazAAR::mark_duplicates()`](https://docs.ropensci.org/c14bazAAR/reference/deprecated_functions.md)
and
[`c14bazAAR::remove_duplicates()`](https://docs.ropensci.org/c14bazAAR/reference/duplicates.md)
for a way to find and remove them.

## Usage

``` r
fuse(...)

# Default S3 method
fuse(...)

# S3 method for class 'c14_date_list'
fuse(...)
```

## Arguments

- ...:

  objects of class c14_date_list

## Value

an object of class c14_date_list

## Examples

``` r
# fuse three identical example c14_date_lists
fuse(example_c14_date_list, example_c14_date_list, example_c14_date_list)
#>  Radiocarbon date list
#>  dates: 27
#>  sites: 4
#>  countries: 5
#>  uncalBP: 9000 - 1000 
#> 
#> # A data frame: 27 × 19
#>    sourcedb method labnr c14age c14std c13val site   sitetype     feature period
#>    <chr>    <chr>  <chr>  <int>  <int>  <dbl> <chr>  <chr>        <chr>   <chr> 
#>  1 A        Conv   lab-1   1000     20    -15 Site A Burial mound Grave 1 NA    
#>  2 A        Conv   lab-2   2000     30    -20 Site A NA           Grave 2 Bronz…
#>  3 A        AMS    lab-3   3000     40    -25 Site B settlement   NA      Bronz…
#>  4 B        NA     lab-4   4000     50    -15 Site B settlement   House 5 Late …
#>  5 B        AMS    lab-5   5000     50    -20 Site C settlement   NA      NA    
#>  6 B        AMS    lab-6   6000     60    -25 Site C settlement   Oven 4  Early…
#>  7 C        AMS    lab-7   7000     70    -15 Site D Camp         Hut 2   Mesol…
#>  8 C        AMS    lab-8   8000     80    -20 Site D Camp         Hut 2   Mesol…
#>  9 C        AMS    lab-9   9000     90    -25 Site D Camp         Hut 3   Mesol…
#> 10 A        Conv   lab-1   1000     20    -15 Site A Burial mound Grave 1 NA    
#> # ℹ 17 more rows
#> # ℹ 9 more variables: culture <chr>, material <chr>, species <chr>,
#> #   region <chr>, country <chr>, lat <dbl>, lon <dbl>, shortref <chr>,
#> #   comment <chr>
```
