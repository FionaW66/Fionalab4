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

``` r
#dennys <- dennys
```

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

``` r
#laquinta <- laquinta
```

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

In terms of ways of evaluating whether they have locations outside of
the U.S., I think there are two ways. First, we can determine whether
the states are the ones in the U.S. Second, we can look at the Zip code.
There is a range for U.S. zip code, and the ones that do not fall
between this range will be a location outside of the U.S. Third, the
combination of longitude and latitude should also fall into the range of
coordinates, but I think this will be very difficult.

### Exercise 5

Finding Dennys locations that are outside of the U.S.

``` r
dennys %>% 
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 0 × 6
    ## # ℹ 6 variables: address <chr>, city <chr>, state <chr>, zip <chr>,
    ## #   longitude <dbl>, latitude <dbl>

There are no locations in this dataset that are outside of the U.S.
Looking at the description in packages, this dataset describes the 1643
Denny’s Restaurants in the United States. So, there are no locations
outside of the U.S. in this dataset.

### Exercise 6

Add a country variable in the Dennys dataset. All are from the United
States.

``` r
dennys <- dennys %>% 
  mutate(country = "United States")
head(dennys)
```

    ## # A tibble: 6 × 7
    ##   address                        city     state zip   longitude latitude country
    ##   <chr>                          <chr>    <chr> <chr>     <dbl>    <dbl> <chr>  
    ## 1 2900 Denali                    Anchora… AK    99503    -150.      61.2 United…
    ## 2 3850 Debarr Road               Anchora… AK    99508    -150.      61.2 United…
    ## 3 1929 Airport Way               Fairban… AK    99701    -148.      64.8 United…
    ## 4 230 Connector Dr               Auburn   AL    36849     -85.5     32.6 United…
    ## 5 224 Daniel Payne Drive N       Birming… AL    35207     -86.8     33.6 United…
    ## 6 900 16th St S, Commons on Gree Birming… AL    35294     -86.8     33.5 United…
