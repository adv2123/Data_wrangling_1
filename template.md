Data import
================

This file is for doing data import .

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.2.1     ✔ readr     2.2.0
    ## ✔ forcats   1.0.1     ✔ stringr   1.6.0
    ## ✔ ggplot2   4.0.3     ✔ tibble    3.3.1
    ## ✔ lubridate 1.9.5     ✔ tidyr     1.3.2
    ## ✔ purrr     1.2.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

ALways use relative path to acces/import data

import ourt first dataset.

``` r
litters_df = 
  read_csv(file = "data/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

the janitor function changed the name from tibble to clean names.

Import your second dataset.

## Import two data

``` r
pups_df = 
  read_csv(file = "data/FAS_litters.csv", skip = 3)
```

    ## Rows: 46 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Con7, #5/5/3/83/3-3, 26, 41.4
    ## dbl (4): 19, 6, 0, 5
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
pups_df = janitor::clean_names(pups_df)
```

## Look at the data

``` r
litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>           <chr>      <chr>             <dbl>           <dbl>
    ##  1 Con7  #85             19.7       34.7                 20               3
    ##  2 Con7  #1/2/95/2       27         42                   19               8
    ##  3 Con7  #5/5/3/83/3-3   26         41.4                 19               6
    ##  4 Con7  #5/4/2/95/2     28.5       44.1                 19               5
    ##  5 Con7  #4/2/95/3-3     <NA>       <NA>                 20               6
    ##  6 Con7  #2/2/95/3-2     <NA>       <NA>                 20               6
    ##  7 Con7  #1/5/3/83/3-3/2 <NA>       <NA>                 20               9
    ##  8 Con8  #3/83/3-3       <NA>       <NA>                 20               9
    ##  9 Con8  #2/95/3         <NA>       <NA>                 20               8
    ## 10 Con8  #3/5/2/2/95     28.5       <NA>                 20               8
    ## # ℹ 39 more rows
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
pups_df
```

    ## # A tibble: 46 × 8
    ##    con7  number_5_5_3_83_3_3 x26   x41_4   x19    x6    x0    x5
    ##    <chr> <chr>               <chr> <chr> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con7  #5/4/2/95/2         28.5  44.1     19     5     1     4
    ##  2 Con7  #4/2/95/3-3         <NA>  <NA>     20     6     0     6
    ##  3 Con7  #2/2/95/3-2         <NA>  <NA>     20     6     0     4
    ##  4 Con7  #1/5/3/83/3-3/2     <NA>  <NA>     20     9     0     9
    ##  5 Con8  #3/83/3-3           <NA>  <NA>     20     9     1     8
    ##  6 Con8  #2/95/3             <NA>  <NA>     20     8     0     8
    ##  7 Con8  #3/5/2/2/95         28.5  <NA>     20     8     0     8
    ##  8 Con8  #5/4/3/83/3         28    <NA>     19     9     0     8
    ##  9 Con8  #1/6/2/2/95-2       <NA>  <NA>     20     7     0     6
    ## 10 Con8  #3/5/3/83/3-3-2     <NA>  <NA>     20     8     0     8
    ## # ℹ 36 more rows

``` r
litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>           <chr>      <chr>             <dbl>           <dbl>
    ##  1 Con7  #85             19.7       34.7                 20               3
    ##  2 Con7  #1/2/95/2       27         42                   19               8
    ##  3 Con7  #5/5/3/83/3-3   26         41.4                 19               6
    ##  4 Con7  #5/4/2/95/2     28.5       44.1                 19               5
    ##  5 Con7  #4/2/95/3-3     <NA>       <NA>                 20               6
    ##  6 Con7  #2/2/95/3-2     <NA>       <NA>                 20               6
    ##  7 Con7  #1/5/3/83/3-3/2 <NA>       <NA>                 20               9
    ##  8 Con8  #3/83/3-3       <NA>       <NA>                 20               9
    ##  9 Con8  #2/95/3         <NA>       <NA>                 20               8
    ## 10 Con8  #3/5/2/2/95     28.5       <NA>                 20               8
    ## # ℹ 39 more rows
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
tail(litters_df, 5)
```

    ## # A tibble: 5 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ## 1 Low8  #100          20         39.2                 20               8
    ## 2 Low8  #4/84         21.8       35.2                 20               4
    ## 3 Low8  #108          25.6       47.5                 20               8
    ## 4 Low8  #99           23.5       39                   20               6
    ## 5 Low8  #110          25.5       42.7                 20               7
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

skim variables:

``` r
skimr::skim(pups_df)
```

|                                                  |         |
|:-------------------------------------------------|:--------|
| Name                                             | pups_df |
| Number of rows                                   | 46      |
| Number of columns                                | 8       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |         |
| Column type frequency:                           |         |
| character                                        | 4       |
| numeric                                          | 4       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |         |
| Group variables                                  | None    |

Data summary

**Variable type: character**

| skim_variable       | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| con7                |         0 |          1.00 |   4 |   4 |     0 |        6 |          0 |
| number_5_5_3_83_3_3 |         0 |          1.00 |   3 |  15 |     0 |       46 |          0 |
| x26                 |        13 |          0.72 |   1 |   4 |     0 |       23 |          0 |
| x41_4               |        15 |          0.67 |   1 |   4 |     0 |       28 |          0 |

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |  mean |   sd |  p0 |   p25 | p50 |   p75 | p100 | hist  |
|:--------------|----------:|--------------:|------:|-----:|----:|------:|----:|------:|-----:|:------|
| x19           |         0 |             1 | 19.67 | 0.47 |  19 | 19.00 |  20 | 20.00 |   20 | ▃▁▁▁▇ |
| x6            |         0 |             1 |  7.46 | 1.68 |   3 |  6.25 |   8 |  8.75 |   11 | ▁▃▂▇▁ |
| x0            |         0 |             1 |  0.26 | 0.53 |   0 |  0.00 |   0 |  0.00 |    2 | ▇▁▂▁▁ |
| x5            |         0 |             1 |  6.50 | 2.04 |   1 |  5.00 |   7 |  8.00 |    9 | ▁▃▂▇▇ |
