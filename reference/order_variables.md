# Order the variables in a **c14_date_list**

Arrange variables according to a defined order. This makes sure that a
**c14_date_list** always appears with the same outline.  
A **c14_date_list** has at least the columns **c14age** and **c14std**.
Beyond that there's a selection of additional variables depending on the
input from the source databases, as a result of the `c14bazAAR`
functions or added by other data analysis steps. This function arranges
the expected variables in a distinct, predefined order. Undefined
variables are added at the end.

## Usage

``` r
order_variables(x)

# Default S3 method
order_variables(x)

# S3 method for class 'c14_date_list'
order_variables(x)
```

## Arguments

- x:

  an object of class c14_date_list

## Value

an object of class c14_date_list
