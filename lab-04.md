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

### Exercise 7

Find out the La Quinta locations that are outside of the U.S.

``` r
laquinta %>% 
  filter(!(state %in% states$abbreviation))
```

    ## # A tibble: 14 × 6
    ##    address                                  city  state zip   longitude latitude
    ##    <chr>                                    <chr> <chr> <chr>     <dbl>    <dbl>
    ##  1 Carretera Panamericana Sur KM 12         "\nA… AG    20345    -102.     21.8 
    ##  2 Av. Tulum Mza. 14 S.M. 4 Lote 2          "\nC… QR    77500     -86.8    21.2 
    ##  3 Ejercito Nacional 8211                   "Col… CH    32528    -106.     31.7 
    ##  4 Blvd. Aeropuerto 4001                    "Par… NL    66600    -100.     25.8 
    ##  5 Carrera 38 # 26-13 Avenida las Palmas c… "\nM… ANT   0500…     -75.6     6.22
    ##  6 AV. PINO SUAREZ No. 1001                 "Col… NL    64000    -100.     25.7 
    ##  7 Av. Fidel Velazquez #3000 Col. Central   "\nM… NL    64190    -100.     25.7 
    ##  8 63 King Street East                      "\nO… ON    L1H1…     -78.9    43.9 
    ##  9 Calle Las Torres-1 Colonia Reforma       "\nP… VE    93210     -97.4    20.6 
    ## 10 Blvd. Audi N. 3 Ciudad Modelo            "\nS… PU    75010     -97.8    19.2 
    ## 11 Ave. Zeta del Cochero No 407             "Col… PU    72810     -98.2    19.0 
    ## 12 Av. Benito Juarez 1230 B (Carretera 57)… "\nS… SL    78399    -101.     22.1 
    ## 13 Blvd. Fuerza Armadas                     "con… FM    11101     -87.2    14.1 
    ## 14 8640 Alexandra Rd                        "\nR… BC    V6X1…    -123.     49.2

There are 14 instances/motels that are not in the United States. I hope
that none of the outside states have the same abbreviations as the U.S.
states. After some googling, I now know where each is from.  
AG - Mexico.  
QR - Mexico.  
CH - Mexico.  
NL - Mexico.  
ANT - Colombia.  
NL - Mexico.  
ON - Canada.  
VE - Mexico.  
PU - Mexico.  
SL - Mexico. FM - Honduras. BC - Canada.  
For the ones that are located outside of the U.S., they are in Mexico,
Canada, Colombia, and Honduras.

### Exercise 8

We want to create a country variable for la quinta data.

``` r
laquinta <- laquinta %>% 
  mutate(country = case_when(
    state %in% state.abb ~ "United States", 
    state %in% c("ON", "BC") ~ "Canada",
    state == "ANT" ~ "Colombia",
    state == "FM" ~ "Honduras",
    state %in% c("AG", "QR", "CH", "NL", "VE", "PU", "SL") ~ "Mexico"
  ))
```

We will filter for only the United States data in la quinta.

``` r
laquinta <- laquinta %>% 
  filter(country == "United States")
```

### Exercise 9

Next, we will calculate which states have the most Denny’s location.  
Count dennys by state and join dennys and states datasets.

``` r
dn <- dennys %>% 
  count(state) %>% 
  inner_join(states, by = c("state" = "abbreviation"))
head(dn)
```

    ## # A tibble: 6 × 4
    ##   state     n name          area
    ##   <chr> <int> <chr>        <dbl>
    ## 1 AK        3 Alaska     665384.
    ## 2 AL        7 Alabama     52420.
    ## 3 AR        9 Arkansas    53179.
    ## 4 AZ       83 Arizona    113990.
    ## 5 CA      403 California 163695.
    ## 6 CO       29 Colorado   104094.
