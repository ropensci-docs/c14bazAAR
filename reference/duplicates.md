# Remove duplicates in a **c14_date_list**

Duplicates are found by comparison of **labnr**s. Only dates with
exactly equal **labnr**s are considered duplicates. Duplicate groups are
numbered (from 0) and these numbers linked to the individual dates in a
internal column **duplicate_group**. If you only want to see this
grouping without removing anything use the `mark_only` flag.
`c14bazAAR::remove_duplicates()` can remove duplicates with three
different strategies according to the value of the arguments
`preferences` and `supermerge`:

1.  Option 1: By merging all dates in a **duplicate_group**. All
    non-equal variables in the duplicate group are turned to `NA`. This
    is the default option.

2.  Option 2: By selecting individual database entries in a
    **duplicate_group** according to a trust hierarchy as defined by the
    parameter `preferences`. In case of duplicates within one database
    the first occurrence in the table (top down) is selected. All
    databases not mentioned in `preferences` are dropped.

3.  Option 3: Like option 2, but in this case the different datasets in
    a **duplicate_group** are merged column by column to create a
    superdataset with a maximum of information. The column **sourcedb**
    is dropped in this case to indicate that multiple databases have
    been merged. Data citation is a lot more difficult with this option.
    It can be activated with `supermerge`.

The option `log` allows to add a new column **duplicate_remove_log**
that documents the variety of values provided by all databases for this
duplicated date.

## Usage

``` r
remove_duplicates(
  x,
  preferences = NULL,
  supermerge = FALSE,
  log = TRUE,
  mark_only = FALSE
)

# Default S3 method
remove_duplicates(
  x,
  preferences = NULL,
  supermerge = FALSE,
  log = TRUE,
  mark_only = FALSE
)

# S3 method for class 'c14_date_list'
remove_duplicates(
  x,
  preferences = NULL,
  supermerge = FALSE,
  log = TRUE,
  mark_only = FALSE
)
```

## Arguments

- x:

  an object of class c14_date_list

- preferences:

  character vector with the order of source databases by which the
  deduping should be executed. If e.g. preferences = c("radon",
  "calpal") and a certain date appears in radon and euroevol, then only
  the radon entry remains. Default: NULL. With preferences = NULL all
  overlapping, conflicting information in individual columns of one
  duplicated date is removed. See Option 2 and 3.

- supermerge:

  boolean. Should the duplicated datasets be merged on the column level?
  Default: FALSE. See Option 3.

- log:

  logical. If log = TRUE, an additional column is added that contains a
  string documentation of all variants of the information for one date
  from all conflicting databases. Default = TRUE.

- mark_only:

  boolean. Should duplicates not be removed, but only indicated?
  Default: FALSE.

## Value

an object of class c14_date_list with the additional columns
**duplicate_group** or **duplicate_remove_log**

## Examples

``` r
library(magrittr)

test_data <- tibble::tribble(
  ~sourcedb, ~labnr,  ~c14age, ~c14std,
 "A",       "lab-1", 1100,    10,
 "A",       "lab-1", 2100,    20,
 "B",       "lab-1", 3100,    30,
 "A",       "lab-2", NA,      10,
 "B",       "lab-2", 2200,    20,
 "C",       "lab-3", 1300,    10
) %>% as.c14_date_list()

# remove duplicates with option 1:
test_data %>% remove_duplicates()
#> You did not provide the argument 'preferences' or your c14_date_list does not contain the necessary column 'sourcedb'. That means that duplicates are removed in a way that obscures conflicting information. As a result of this vital data for your analysis might get lost. 
#> Please check '?duplicates' for more information.
#> Marking duplicates... 
#> -> Search for accordances in Lab Codes...
#> -> Writing duplicate groups...
#>   |                                                          |                                                  |   0%  |                                                          |+++++++++++++++++++++++++                         |  50%  |                                                          |++++++++++++++++++++++++++++++++++++++++++++++++++| 100%
#> Removing duplicates... 
#>  Radiocarbon date list
#>  dates: 3
#>  uncalBP: 2200 - 1300 
#> 
#> # A data frame: 3 × 5
#>   sourcedb labnr c14age c14std duplicate_remove_log                             
#>   <chr>    <chr>  <int>  <int> <chr>                                            
#> 1 C        lab-3   1300     10 NA                                               
#> 2 NA       lab-1     NA     NA sourcedb: A|B, labnr: lab-1, c14age: 1100|2100|3…
#> 3 NA       lab-2   2200     NA sourcedb: A|B, labnr: lab-2, c14age: NA|2200, c1…

# remove duplicates with option 2:
test_data %>% remove_duplicates(
  preferences = c("A", "B")
)
#> Marking duplicates... 
#> -> Search for accordances in Lab Codes...
#> -> Writing duplicate groups...
#>   |                                                          |                                                  |   0%  |                                                          |+++++++++++++++++++++++++                         |  50%  |                                                          |++++++++++++++++++++++++++++++++++++++++++++++++++| 100%
#> Removing duplicates... 
#>  Radiocarbon date list
#>  dates: 2
#>  uncalBP: 1100 - 1100 
#> 
#> # A data frame: 2 × 5
#>   sourcedb labnr c14age c14std duplicate_remove_log                             
#>   <chr>    <chr>  <int>  <int> <chr>                                            
#> 1 A        lab-1   1100     10 sourcedb: A|B, labnr: lab-1, c14age: 1100|2100|3…
#> 2 A        lab-2     NA     10 sourcedb: A|B, labnr: lab-2, c14age: NA|2200, c1…

# remove duplicates with option 3:
test_data %>% remove_duplicates(
  preferences = c("A", "B"),
  supermerge = TRUE
)
#> Marking duplicates... 
#> -> Search for accordances in Lab Codes...
#> -> Writing duplicate groups...
#>   |                                                          |                                                  |   0%  |                                                          |+++++++++++++++++++++++++                         |  50%  |                                                          |++++++++++++++++++++++++++++++++++++++++++++++++++| 100%
#> Removing duplicates... 
#>  Radiocarbon date list
#>  dates: 2
#>  uncalBP: 2200 - 1100 
#> 
#> # A data frame: 2 × 4
#>   labnr c14age c14std duplicate_remove_log                                      
#>   <chr>  <int>  <int> <chr>                                                     
#> 1 lab-1   1100     10 sourcedb: A|B, labnr: lab-1, c14age: 1100|2100|3100, c14s…
#> 2 lab-2   2200     10 sourcedb: A|B, labnr: lab-2, c14age: NA|2200, c14std: 10|…
```
