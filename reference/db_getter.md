# Download radiocarbon source databases and convert them to a **c14_date_list**

`get_c14data()` allows to download source databases and adjust their
variables to conform to the definition in the
[variable_reference](https://github.com/ropensci/c14bazAAR/blob/master/data-raw/variable_reference.csv)
table. That includes renaming and arranging the variables (with
[`c14bazAAR::order_variables()`](https://docs.ropensci.org/c14bazAAR/reference/order_variables.md))
as well as type conversion (with
[`c14bazAAR::enforce_types()`](https://docs.ropensci.org/c14bazAAR/reference/enforce_types.md))
– so all the steps undertaken by
[`as.c14_date_list()`](https://docs.ropensci.org/c14bazAAR/reference/c14_date_list.md).  
All databases require different downloading and data wrangling steps.
Therefore there's a custom getter function for each of them (see
[`?get_all_dates`](https://docs.ropensci.org/c14bazAAR/reference/db_getter_backend.md)).  

`get_c14data()` is a wrapper to download all dates from multiple
databases and
[`c14bazAAR::fuse()`](https://docs.ropensci.org/c14bazAAR/reference/fuse.md)
the results.

## Usage

``` r
get_c14data(databases = c())
```

## Arguments

- databases:

  Character vector. Names of databases to be downloaded. "all" causes
  the download of all databases. `get_c14data()` prints a list of the
  currently available databases

## Examples

``` r

if (FALSE) { # \dontrun{
 get_c14data(databases = c("adrac", "palmisano"))
  get_all_dates()} # }
```
