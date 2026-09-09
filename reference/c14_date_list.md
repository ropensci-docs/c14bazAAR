# **c14_date_list**

The **c14_date_list** is the central data structure of the `c14bazAAR`
package. It's a tibble with set of custom methods and variables. Please
see the
[variable_reference](https://github.com/ropensci/c14bazAAR/blob/master/data-raw/variable_reference.csv)
table for a description of the variables. Further available variables
are ignored.  
If an object is of class data.frame or tibble (tbl & tbl_df), it can be
converted to an object of class **c14_date_list**. The only requirement
is that it contains the essential columns **c14age** and **c14std**. The
`as` function adds the string "c14_date_list" to the classes vector of
the object and applies
[`order_variables()`](https://docs.ropensci.org/c14bazAAR/reference/order_variables.md),
[`enforce_types()`](https://docs.ropensci.org/c14bazAAR/reference/enforce_types.md)
and the helper function `clean_latlon()` to it.

## Usage

``` r
as.c14_date_list(x, ...)

is.c14_date_list(x, ...)

# S3 method for class 'c14_date_list'
format(x, ...)

# S3 method for class 'c14_date_list'
print(x, ...)

# S3 method for class 'c14_date_list'
plot(x, ...)
```

## Arguments

- x:

  an object

- ...:

  further arguments passed to or from other methods

## Examples

``` r
as.c14_date_list(data.frame(c14age = c(2000, 2500), c14std = c(30, 35)))
#>  Radiocarbon date list
#>  dates: 2
#>  uncalBP: 2500 - 2000 
#> 
#> # A data frame: 2 × 2
#>   c14age c14std
#>    <int>  <int>
#> 1   2000     30
#> 2   2500     35
is.c14_date_list(5) # FALSE
#> [1] FALSE
is.c14_date_list(example_c14_date_list) # TRUE
#> [1] TRUE

print(example_c14_date_list)
#>  Radiocarbon date list
#>  dates: 9
#>  sites: 4
#>  countries: 5
#>  uncalBP: 9000 - 1000 
#> 
#> # A data frame: 9 × 19
#>   sourcedb method labnr c14age c14std c13val site   sitetype     feature period 
#>   <chr>    <chr>  <chr>  <int>  <int>  <dbl> <chr>  <chr>        <chr>   <chr>  
#> 1 A        Conv   lab-1   1000     20    -15 Site A Burial mound Grave 1 NA     
#> 2 A        Conv   lab-2   2000     30    -20 Site A NA           Grave 2 Bronze…
#> 3 A        AMS    lab-3   3000     40    -25 Site B settlement   NA      Bronze…
#> 4 B        NA     lab-4   4000     50    -15 Site B settlement   House 5 Late N…
#> 5 B        AMS    lab-5   5000     50    -20 Site C settlement   NA      NA     
#> 6 B        AMS    lab-6   6000     60    -25 Site C settlement   Oven 4  Early …
#> 7 C        AMS    lab-7   7000     70    -15 Site D Camp         Hut 2   Mesoli…
#> 8 C        AMS    lab-8   8000     80    -20 Site D Camp         Hut 2   Mesoli…
#> 9 C        AMS    lab-9   9000     90    -25 Site D Camp         Hut 3   Mesoli…
#> # ℹ 9 more variables: culture <chr>, material <chr>, species <chr>,
#> #   region <chr>, country <chr>, lat <dbl>, lon <dbl>, shortref <chr>,
#> #   comment <chr>
plot(example_c14_date_list)

```
