# Convert a **c14_date_list** to a sf object

Most 14C dates have point position information in the coordinates
columns **lat** and **lon**. This allows them to be converted to a
spatial simple feature collection as provided by the `sf` package. This
simplifies for example mapping of the dates.

## Usage

``` r
as.sf(x, quiet = FALSE)

# Default S3 method
as.sf(x, quiet = FALSE)

# S3 method for class 'c14_date_list'
as.sf(x, quiet = FALSE)
```

## Arguments

- x:

  an object of class c14_date_list

- quiet:

  suppress warning about the removal of dates without coordinates

## Value

an object of class sf

## Examples

``` r
sf_c14 <- as.sf(example_c14_date_list)
#> Warning: Dates without coordinates were removed.

if (FALSE) { # \dontrun{
library(mapview)
mapview(sf_c14$geom)
} # }
```
