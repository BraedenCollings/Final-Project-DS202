
# Final Project DS202

## Marissa Baietto, Ryan Dorle, Braeden Collings

Importing the accident datasets.

``` r
library(readr)
accident_2017 <- read_csv("2017.csv")
```

    ## Rows: 34560 Columns: 91
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (41): STATENAME, COUNTYNAME, CITYNAME, MONTHNAME, DAY_WEEKNAME, HOURNAME...
    ## dbl (50): STATE, ST_CASE, VE_TOTAL, VE_FORMS, PVH_INVL, PEDS, PERSONS, PERMV...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
accident_2018 <- read_csv("2018.csv")
```

    ## Rows: 33919 Columns: 91
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (41): STATENAME, COUNTYNAME, CITYNAME, MONTHNAME, DAY_WEEKNAME, HOURNAME...
    ## dbl (50): STATE, ST_CASE, VE_TOTAL, VE_FORMS, PVH_INVL, PEDS, PERSONS, PERMV...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
accident_2019 <- read_csv("2019.csv")
```

    ## Rows: 33487 Columns: 91
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (41): STATENAME, COUNTYNAME, CITYNAME, MONTHNAME, DAY_WEEKNAME, HOURNAME...
    ## dbl (50): STATE, ST_CASE, VE_TOTAL, VE_FORMS, PVH_INVL, PEDS, PERSONS, PERMV...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
accident_2020 <- read_csv("2020.csv")
```

    ## Rows: 35935 Columns: 81
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (34): STATENAME, COUNTYNAME, CITYNAME, MONTHNAME, DAY_WEEKNAME, HOURNAME...
    ## dbl (47): STATE, ST_CASE, VE_TOTAL, VE_FORMS, PVH_INVL, PEDS, PERNOTMVIT, PE...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
accident_2021 <- read_csv("2021.csv")
```

    ## Rows: 39508 Columns: 80
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (34): STATENAME, COUNTYNAME, CITYNAME, MONTHNAME, DAY_WEEKNAME, HOURNAME...
    ## dbl (46): STATE, ST_CASE, PEDS, PERNOTMVIT, VE_TOTAL, VE_FORMS, PVH_INVL, PE...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.4.0     ✔ dplyr   1.1.0
    ## ✔ tibble  3.1.8     ✔ stringr 1.5.0
    ## ✔ tidyr   1.3.0     ✔ forcats 1.0.0
    ## ✔ purrr   1.0.1     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

Selecting the variables we need.

``` r
accident_2017 <- accident_2017 %>% select(STATENAME, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CITY, MONTH, DAY, YEAR, HOUR, MINUTE, RUR_URBNAME, LATITUDE, LONGITUD, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WRK_ZONENAME, LGT_CONDNAME, WEATHER1NAME, SCH_BUSNAME, FATALS, DRUNK_DR)
accident_2018 <- accident_2018 %>% select(STATENAME, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CITY, MONTH, DAY, YEAR, HOUR, MINUTE, RUR_URBNAME, LATITUDE, LONGITUD, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WRK_ZONENAME, LGT_CONDNAME, WEATHER1NAME, SCH_BUSNAME, FATALS, DRUNK_DR)
accident_2019 <- accident_2019 %>% select(STATENAME, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CITY, MONTH, DAY, YEAR, HOUR, MINUTE, RUR_URBNAME, LATITUDE, LONGITUD, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WRK_ZONENAME, LGT_CONDNAME, WEATHER1NAME, SCH_BUSNAME, FATALS, DRUNK_DR)
accident_2020 <- accident_2020 %>% select(STATENAME, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CITY, MONTH, DAY, YEAR, HOUR, MINUTE, RUR_URBNAME, LATITUDE, LONGITUD, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WRK_ZONENAME, LGT_CONDNAME, WEATHERNAME, SCH_BUSNAME, FATALS, DRUNK_DR)
accident_2021 <- accident_2021 %>% select(STATENAME, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CITY, MONTH, DAY, YEAR, HOUR, MINUTE, RUR_URBNAME, LATITUDE, LONGITUD, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WRK_ZONENAME, LGT_CONDNAME, WEATHERNAME, SCH_BUSNAME, FATALS)
```

Importing the person datasets.

``` r
person_2017 <- read_csv("2017_person.csv")
```

    ## New names:
    ## Rows: 52752 Columns: 14
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (9): SEXNAME, INJ_SEVNAME, REST_USENAME, EJECTIONNAME, DRINKINGNAME, DRU... dbl
    ## (5): ...1, AGE, ST_CASE, VEH_NO, PER_NO
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`

``` r
person_2018 <- read_csv("2018_person.csv")
```

    ## New names:
    ## Rows: 51905 Columns: 14
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (9): SEXNAME, INJ_SEVNAME, REST_USENAME, EJECTIONNAME, DRINKINGNAME, DRU... dbl
    ## (5): ...1, AGE, ST_CASE, VEH_NO, PER_NO
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`

``` r
person_2019 <- read_csv("2019_person.csv")
```

    ## New names:
    ## Rows: 51302 Columns: 14
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (9): SEXNAME, INJ_SEVNAME, REST_USENAME, EJECTIONNAME, DRINKINGNAME, DRU... dbl
    ## (5): ...1, AGE, ST_CASE, VEH_NO, PER_NO
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`

``` r
person_2020 <- read_csv("2020_person.csv")
```

    ## New names:
    ## Rows: 54165 Columns: 14
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (9): SEXNAME, INJ_SEVNAME, REST_USENAME, EJECTIONNAME, DRINKINGNAME, DRU... dbl
    ## (5): ...1, AGE, ST_CASE, VEH_NO, PER_NO
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`

``` r
person_2021 <- read_csv("2021_person.csv")
```

    ## New names:
    ## Rows: 60904 Columns: 14
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (9): SEXNAME, INJ_SEVNAME, REST_USENAME, EJECTIONNAME, DRINKINGNAME, DRU... dbl
    ## (5): ...1, AGE, ST_CASE, VEH_NO, PER_NO
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`

Adding year variable to the datasets.

``` r
person_2017$YEAR = 2017
person_2018$YEAR = 2018
person_2019$YEAR = 2019
person_2020$YEAR = 2020
person_2021$YEAR = 2021
```

Merging the datasets.

``` r
df_2017 <- left_join(accident_2017, person_2017, by=c('YEAR', 'ST_CASE'))
```

    ## Warning in left_join(accident_2017, person_2017, by = c("YEAR", "ST_CASE")): Each row in `x` is expected to match at most 1 row in `y`.
    ## ℹ Row 3 of `x` matches multiple rows.
    ## ℹ If multiple matches are expected, set `multiple = "all"` to silence this
    ##   warning.

``` r
df_2018 <- left_join(accident_2018, person_2018, by=c('YEAR', 'ST_CASE'))
```

    ## Warning in left_join(accident_2018, person_2018, by = c("YEAR", "ST_CASE")): Each row in `x` is expected to match at most 1 row in `y`.
    ## ℹ Row 3 of `x` matches multiple rows.
    ## ℹ If multiple matches are expected, set `multiple = "all"` to silence this
    ##   warning.

``` r
df_2019 <- left_join(accident_2019, person_2019, by=c('YEAR', 'ST_CASE'))
```

    ## Warning in left_join(accident_2019, person_2019, by = c("YEAR", "ST_CASE")): Each row in `x` is expected to match at most 1 row in `y`.
    ## ℹ Row 1 of `x` matches multiple rows.
    ## ℹ If multiple matches are expected, set `multiple = "all"` to silence this
    ##   warning.

``` r
df_2020 <- left_join(accident_2020, person_2020, by=c('YEAR', 'ST_CASE'))
```

    ## Warning in left_join(accident_2020, person_2020, by = c("YEAR", "ST_CASE")): Each row in `x` is expected to match at most 1 row in `y`.
    ## ℹ Row 2 of `x` matches multiple rows.
    ## ℹ If multiple matches are expected, set `multiple = "all"` to silence this
    ##   warning.

``` r
df_2021 <- left_join(accident_2021, person_2021, by=c('YEAR', 'ST_CASE'))
```

    ## Warning in left_join(accident_2021, person_2021, by = c("YEAR", "ST_CASE")): Each row in `x` is expected to match at most 1 row in `y`.
    ## ℹ Row 1 of `x` matches multiple rows.
    ## ℹ If multiple matches are expected, set `multiple = "all"` to silence this
    ##   warning.

Creating one dataset with all years.

``` r
df <- bind_rows(df_2017, df_2018,df_2019,df_2020,df_2021)
```

    ## New names:
    ## New names:
    ## New names:
    ## New names:
    ## New names:
    ## • `...1` -> `...26`

``` r
df1 <- df %>% group_by(STATENAME, YEAR) %>% filter(ST_CASE %% 10000 <= 200)
```

Saving the final dataset to ‘master.csv’

``` r
write.csv(df1, 'master.csv')
```

## Discription of Data

The data we chose to work with is from the National Highway Traffic
Safety Administration. The administration has a system called FARS or
the Fatality Analysis Reporting System in which vehicle crashes are
noted. The data is comprised from police reports, death certificates,
various medical reports, and department data. We chose to look at the
years from 2017-2021 for our report.

``` r
summary(df1)
```

    ##   STATENAME            ST_CASE         PERNOTMVIT         VE_FORMS     
    ##  Length:66042       Min.   : 10001   Min.   : 0.0000   Min.   : 1.000  
    ##  Class :character   1st Qu.:170123   1st Qu.: 0.0000   1st Qu.: 1.000  
    ##  Mode  :character   Median :290016   Median : 0.0000   Median : 2.000  
    ##                     Mean   :288775   Mean   : 0.1542   Mean   : 1.891  
    ##                     3rd Qu.:410087   3rd Qu.: 0.0000   3rd Qu.: 2.000  
    ##                     Max.   :560121   Max.   :12.0000   Max.   :28.000  
    ##                                                                        
    ##     PVH_INVL          PERMVIT           COUNTY            CITY     
    ##  Min.   :0.00000   Min.   : 0.000   Min.   :  0.00   Min.   :   0  
    ##  1st Qu.:0.00000   1st Qu.: 1.000   1st Qu.: 19.00   1st Qu.:   0  
    ##  Median :0.00000   Median : 2.000   Median : 51.00   Median :  20  
    ##  Mean   :0.03243   Mean   : 2.743   Mean   : 70.62   Mean   :1170  
    ##  3rd Qu.:0.00000   3rd Qu.: 3.000   3rd Qu.:101.00   3rd Qu.:1670  
    ##  Max.   :9.00000   Max.   :61.000   Max.   :999.00   Max.   :9999  
    ##                                                                    
    ##      MONTH             DAY             YEAR           HOUR          MINUTE     
    ##  Min.   : 1.000   Min.   : 1.00   Min.   :2017   Min.   : 0.0   Min.   : 0.00  
    ##  1st Qu.: 2.000   1st Qu.: 7.00   1st Qu.:2018   1st Qu.: 8.0   1st Qu.:14.00  
    ##  Median : 3.000   Median :15.00   Median :2019   Median :14.0   Median :30.00  
    ##  Mean   : 3.716   Mean   :14.97   Mean   :2019   Mean   :13.7   Mean   :29.06  
    ##  3rd Qu.: 5.000   3rd Qu.:22.00   3rd Qu.:2020   3rd Qu.:18.0   3rd Qu.:44.00  
    ##  Max.   :12.000   Max.   :31.00   Max.   :2021   Max.   :99.0   Max.   :99.00  
    ##                                                                                
    ##  RUR_URBNAME           LATITUDE         LONGITUD       HARM_EVNAME       
    ##  Length:66042       Min.   : 19.04   Min.   :-170.51   Length:66042      
    ##  Class :character   1st Qu.: 35.37   1st Qu.:-103.58   Class :character  
    ##  Mode  :character   Median : 39.42   Median : -89.67   Mode  :character  
    ##                     Mean   : 39.06   Mean   : -90.05                     
    ##                     3rd Qu.: 42.23   3rd Qu.: -80.81                     
    ##                     Max.   :100.00   Max.   :1000.00                     
    ##                                                                          
    ##  MAN_COLLNAME       RELJCT2NAME        WRK_ZONENAME       LGT_CONDNAME      
    ##  Length:66042       Length:66042       Length:66042       Length:66042      
    ##  Class :character   Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  WEATHER1NAME       SCH_BUSNAME            FATALS         DRUNK_DR    
    ##  Length:66042       Length:66042       Min.   :1.000   Min.   :0.000  
    ##  Class :character   Class :character   1st Qu.:1.000   1st Qu.:0.000  
    ##  Mode  :character   Mode  :character   Median :1.000   Median :0.000  
    ##                                        Mean   :1.117   Mean   :0.279  
    ##                                        3rd Qu.:1.000   3rd Qu.:1.000  
    ##                                        Max.   :8.000   Max.   :4.000  
    ##                                                        NA's   :13273  
    ##      ...26            AGE           SEXNAME          INJ_SEVNAME       
    ##  Min.   :    1   Min.   :  7.00   Length:66042       Length:66042      
    ##  1st Qu.:18045   1st Qu.: 28.00   Class :character   Class :character  
    ##  Median :27704   Median : 42.00   Mode  :character   Mode  :character  
    ##  Mean   :27531   Mean   : 58.78                                        
    ##  3rd Qu.:37871   3rd Qu.: 58.00                                        
    ##  Max.   :54165   Max.   :999.00                                        
    ##  NA's   :13352   NA's   :95                                            
    ##  REST_USENAME       EJECTIONNAME       DRINKINGNAME        DRUGSNAME        
    ##  Length:66042       Length:66042       Length:66042       Length:66042      
    ##  Class :character   Class :character   Class :character   Class :character  
    ##  Mode  :character   Mode  :character   Mode  :character   Mode  :character  
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##    DOANAME          LAG_HRSNAME        WORK_INJNAME           VEH_NO      
    ##  Length:66042       Length:66042       Length:66042       Min.   : 1.000  
    ##  Class :character   Class :character   Class :character   1st Qu.: 1.000  
    ##  Mode  :character   Mode  :character   Mode  :character   Median : 1.000  
    ##                                                           Mean   : 1.448  
    ##                                                           3rd Qu.: 2.000  
    ##                                                           Max.   :28.000  
    ##                                                           NA's   :95      
    ##      PER_NO      WEATHERNAME            ...25      
    ##  Min.   :1.000   Length:66042       Min.   :    1  
    ##  1st Qu.:1.000   Class :character   1st Qu.:20636  
    ##  Median :1.000   Mode  :character   Median :32289  
    ##  Mean   :1.001                      Mean   :31728  
    ##  3rd Qu.:1.000                      3rd Qu.:43824  
    ##  Max.   :6.000                      Max.   :60904  
    ##  NA's   :95                         NA's   :52785

## Marginal Summaries

- STATENAME
- WEATHERNAME
- VEH_NO
- PER_NO
- WORK_INJNAME
- LAG_HRSNAME
- DOANAME
- DRUGSNAME
- DRINKINGNAME  
- EJECTIONNAME
- REST_USENAME
- INJ_SEVNAME
- SEXNAME
- AGE
- DRUNK_DR
- FATALS
- SCH_BUSNAME
- WEATHER1NAME
- LGT_CONDNAME
- WRK_ZONENAME  
- RELJCT2NAME  
- MAN_COLLNAME
- HARM_EVNAME
- LATITUDE
- LONGITUD
- RUR_URBNAME
- HOUR
- MINUTE
- CITY
- MONTH
- DAY
- YEAR
- COUNTY
- PERMVIT
- PVH_INVL
- VE_FORMS
- PERNOTMVIT
- ST_CASE
