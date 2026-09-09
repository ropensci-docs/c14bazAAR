# Determine the country of all dates in a **c14_date_list** from their coordinates

`c14bazAAR::determine_country_by_coordinate()` adds the column
**country_coord** with standardized country attribution based on the
coordinate information for the dates. Due to the inconsistencies in the
**country** column in many c14 source databases it's often necessary to
rely on the coordinate position (**lat** & **lon**) for country
attribution information. Unfortunately not all source databases store
coordinates.

## Usage

``` r
determine_country_by_coordinate(x, suppress_spatial_warnings = TRUE)

# Default S3 method
determine_country_by_coordinate(x, suppress_spatial_warnings = TRUE)

# S3 method for class 'c14_date_list'
determine_country_by_coordinate(x, suppress_spatial_warnings = TRUE)
```

## Arguments

- x:

  an object of class c14_date_list

- suppress_spatial_warnings:

  suppress some spatial data messages and warnings

## Value

an object of class c14_date_list with the additional column
**country_coord**

## Examples

``` r
library(magrittr)
example_c14_date_list %>%
  determine_country_by_coordinate()
#> Determining country by coordinates... 
#>  Radiocarbon date list
#>  dates: 9
#>  sites: 4
#>  countries: 5
#>  uncalBP: 9000 - 1000 
#> 
#> # A data frame: 9 × 20
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
#> # ℹ 10 more variables: culture <chr>, material <chr>, species <chr>,
#> #   region <chr>, country <chr>, country_coord <chr>, lat <dbl>, lon <dbl>,
#> #   shortref <chr>, comment <chr>
```
