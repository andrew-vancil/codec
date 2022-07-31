
<!-- README.md is generated from README.Rmd. Please edit that file -->

# CODECtools

<!-- badges: start -->

[![R-CMD-check](https://github.com/geomarker-io/CODECtools/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/geomarker-io/CODECtools/actions/workflows/R-CMD-check.yaml)
<!-- badges: end -->

The goal of CODECtools is to support CODEC data infrastructure through:

-   capturing, creating, and accessing metadata for tabular data in R
-   importing and exporting tabular data resources (CSV file) with
    metadata (YAML file)
-   defining CODEC data format specifications (as vignette in package)
-   providing tools and workflows to validate CODEC data and contribute
    it to CODECdata repository
-   creation of online data catalog

## Installation

You can install the development version of CODECtools from
[GitHub](https://github.com/) with:

``` r
# install.packages("devtools")
devtools::install_github("geomarker-io/CODECtools")
```

## Metadata Example

Here is a basic example of adding metadata to data in R, saving it to
disk, and reading it back into R with the metadata:

``` r
library(CODECtools)

my_mtcars <-
  mtcars |>
    add_attrs(name = "Motor Trend Cars", year = "1974") |>
    add_type_attrs() |>
    add_col_attrs(mpg, name = "MPG", description = "Miles Per Gallon")

get_descriptors(my_mtcars)
#> # A tibble: 3 × 2
#>   name  value           
#>   <chr> <chr>           
#> 1 name  Motor Trend Cars
#> 2 year  1974            
#> 3 class data.frame

save_tabular_data_resource(my_mtcars)

## yaml::yaml.load_file("tabular-data-resource.yaml")
```
