Lab 04 - Visualizing spatial data
================
Fiona Wang
02-13-2025

### Load packages and data

``` r
#install.packages("devtools")
#devtools::install_github("rstudio-education/dsbox")
library(tidyverse) 
library(dsbox) 
```

``` r
states <- read_csv("data/states.csv")
```

### Exercise 1

Denny.  
There are 1643 rows in the dataset and 6 variables in the dataset.

``` r
head(dennys)
```

    ## # A tibble: 6 × 6
    ##   address                        city       state zip   longitude latitude
    ##   <chr>                          <chr>      <chr> <chr>     <dbl>    <dbl>
    ## 1 2900 Denali                    Anchorage  AK    99503    -150.      61.2
    ## 2 3850 Debarr Road               Anchorage  AK    99508    -150.      61.2
    ## 3 1929 Airport Way               Fairbanks  AK    99701    -148.      64.8
    ## 4 230 Connector Dr               Auburn     AL    36849     -85.5     32.6
    ## 5 224 Daniel Payne Drive N       Birmingham AL    35207     -86.8     33.6
    ## 6 900 16th St S, Commons on Gree Birmingham AL    35294     -86.8     33.5

Each row corresponds to one restaurant. For each restaurant, the
following variables were reported: address, city, state, zip, longitude,
and latitude.

### Exercise 2

La Quinta.  
There are 909 rows and 6 variables in the dataset.

``` r
head(laquinta)
```

    ## # A tibble: 6 × 6
    ##   address                    city         state zip   longitude latitude
    ##   <chr>                      <chr>        <chr> <chr>     <dbl>    <dbl>
    ## 1 793 W. Bel Air Avenue      "\nAberdeen" MD    21001     -76.2     39.5
    ## 2 3018 CatClaw Dr            "\nAbilene"  TX    79606     -99.8     32.4
    ## 3 3501 West Lake Rd          "\nAbilene"  TX    79601     -99.7     32.5
    ## 4 184 North Point Way        "\nAcworth"  GA    30102     -84.7     34.1
    ## 5 2828 East Arlington Street "\nAda"      OK    74820     -96.6     34.8
    ## 6 14925 Landmark Blvd        "\nAddison"  TX    75254     -96.8     33.0

Each row corresponds to one motel. Variables include: address, city,
state, zip, longitude, and latitude.

### Exercise 3

Looking from the website, there are La Quinta locations outside of the
U.S. The countries that have La Quinta: Canada, Mexico, China, New
Zealand, Turkey, United Arab Emirates, Chile, Colombia, and Ecuador. I
can’t tell from the webiste whether there are any Denny’s outside of the
U.S, because it only let me view U.S. locations. However, when I google,
it says there are Denny’s in Canada, Mexico, Puerto Rico, Phillipines,
New Zealand, Honduras, UAE, and a couple more countries.

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…

Add exercise headings as needed.
