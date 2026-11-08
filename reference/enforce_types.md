# Enforce variable types in a **c14_date_list**

Enforce variable types in a **c14_date_list** and remove everything that
doesn't fit (e.g. text in a number field). See the
[variable_reference](https://github.com/ropensci/c14bazAAR/blob/master/data-raw/variable_reference.csv)
table for a documentation of the variable types. `enforce_types()` is
called in
[`c14bazAAR::as.c14_date_list()`](https://docs.ropensci.org/c14bazAAR/reference/c14_date_list.md).

## Usage

``` r
enforce_types(x, suppress_na_introduced_warnings = TRUE)

# Default S3 method
enforce_types(x, suppress_na_introduced_warnings = TRUE)

# S3 method for class 'c14_date_list'
enforce_types(x, suppress_na_introduced_warnings = TRUE)
```

## Arguments

- x:

  an object of class c14_date_list

- suppress_na_introduced_warnings:

  suppress warnings caused by data removal in type transformation due to
  wrong database entries (such as text in a number column)

## Value

an object of class c14_date_list

## Examples

``` r
# initial situation
ex <- example_c14_date_list
class(ex$c14age)
#> [1] "integer"

# modify variable/column type
ex$c14age <- as.character(ex$c14age)
class(ex$c14age)
#> [1] "character"

# fix type with enforce_types()
ex <- enforce_types(ex)
class(ex$c14age)
#> [1] "integer"
```
