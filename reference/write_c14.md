# write **c14_date_list**s to files

write **c14_date_list**s to files

## Usage

``` r
write_c14(x, format = c("csv"), ...)

# Default S3 method
write_c14(x, format = c("csv"), ...)

# S3 method for class 'c14_date_list'
write_c14(x, format = c("csv"), ...)
```

## Arguments

- x:

  an object of class c14_date_list

- format:

  the output format: 'csv' (default) or 'xlsx'. 'csv' calls
  [`utils::write.csv()`](https://rdrr.io/r/utils/write.table.html),
  'xlsx' calls
  [`writexl::write_xlsx()`](https://docs.ropensci.org/writexl//reference/write_xlsx.html)

- ...:

  passed to the actual writing functions

## Examples

``` r
csv_file <- tempfile(fileext = ".csv")
write_c14(
  example_c14_date_list,
  format = "csv",
  file = csv_file
)
# \donttest{
xlsx_file <- tempfile(fileext = ".xlsx")
write_c14(
  example_c14_date_list,
  format = "xlsx",
  path = xlsx_file,
)
# }
```
