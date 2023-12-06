
# Final Project DS202

## Marissa Baietto, Ryan Dorle, Braeden Collings

Here is the link to all of the csv files we used:
<https://www.nhtsa.gov/file-downloads?p=nhtsa/downloads/FARS/>

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
df1 <- df %>% group_by(STATENAME, YEAR) %>% filter()
```

Saving the final dataset to ‘master.csv’

``` r
write.csv(df1, 'master2.csv')
```

## Discription of Data

The data we chose to work with is from the National Highway Traffic
Safety Administration. The administration has a system called FARS or
the Fatality Analysis Reporting System in which vehicle crashes are
noted. The data is comprised from police reports, death certificates,
various medical reports, and department data. We chose to look at the
years from 2017-2021 for our report.

``` r
master <- read_csv('master2.csv')
```

    ## New names:
    ## Rows: 271395 Columns: 41
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (19): STATENAME, RUR_URBNAME, HARM_EVNAME, MAN_COLLNAME, RELJCT2NAME, WR... dbl
    ## (22): ...1, ST_CASE, PERNOTMVIT, VE_FORMS, PVH_INVL, PERMVIT, COUNTY, CI...
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...1`
    ## • `...26` -> `...27`
    ## • `...25` -> `...41`

``` r
head(master)
```

    ## # A tibble: 6 × 41
    ##    ...1 STATENAME ST_CASE PERNOTMVIT VE_FORMS PVH_INVL PERMVIT COUNTY  CITY
    ##   <dbl> <chr>       <dbl>      <dbl>    <dbl>    <dbl>   <dbl>  <dbl> <dbl>
    ## 1     1 Alabama     10001          0        1        0       1     73   330
    ## 2     2 Alabama     10002          0        1        0       1     89  1730
    ## 3     3 Alabama     10003          0        3        0       3    101  2130
    ## 4     4 Alabama     10003          0        3        0       3    101  2130
    ## 5     5 Alabama     10003          0        3        0       3    101  2130
    ## 6     6 Alabama     10004          0        1        0       1     73   350
    ## # ℹ 32 more variables: MONTH <dbl>, DAY <dbl>, YEAR <dbl>, HOUR <dbl>,
    ## #   MINUTE <dbl>, RUR_URBNAME <chr>, LATITUDE <dbl>, LONGITUD <dbl>,
    ## #   HARM_EVNAME <chr>, MAN_COLLNAME <chr>, RELJCT2NAME <chr>,
    ## #   WRK_ZONENAME <chr>, LGT_CONDNAME <chr>, WEATHER1NAME <chr>,
    ## #   SCH_BUSNAME <chr>, FATALS <dbl>, DRUNK_DR <dbl>, ...27 <dbl>, AGE <dbl>,
    ## #   SEXNAME <chr>, INJ_SEVNAME <chr>, REST_USENAME <chr>, EJECTIONNAME <chr>,
    ## #   DRINKINGNAME <chr>, DRUGSNAME <chr>, DOANAME <chr>, LAG_HRSNAME <chr>, …

## Marginal Summaries

- STATENAME: The state the fatal crash occured in
- WEATHERNAME: The type of weather outside at the time and location of
  the crash.
- VEH_NO: Vehicle Number, a number assigned to each vehicle in the
  crash.
- PER_NO: Person Number, A unique number assigned to any person involved
  in the crash.
- WORK_INJNAME: Fatal injury at work, whether the person was at work at
  the time of the crash.
- LAG_HRSNAME: Lag Time, hours between the crash and the time of death.
- DOANAME:
- DRUGSNAME: Were there drugs involved in the crash if so the name of
  the drug.
- DRINKINGNAME: Was drinking involved in the crash if so what alcohol.  
- EJECTIONNAME: Was there an ejection of a person in the crash.
- REST_USENAME: Restraint System Used, was there a seatbelt used in the
  crash.
- INJ_SEVNAME: What is the severity of the injury.
- SEXNAME: The gender of people related to the crash.
- AGE: Age of people in the crash.
- DRUNK_DR: Drinking Drivers, The number of drinking drivers involved in
  the crash.
- FATALS: The number of fatalities in the crash.
- SCH_BUSNAME: Was there a school bus related in the crash.
- WEATHER1NAME: Atmospheric conditions at the time of the crash.
- LGT_CONDNAME: What was the lighting condition at the time of the
  crash.
- WRK_ZONENAME: Did the crash occur in the boundaries of a work zone.  
- RELJCT2NAME: Location of the crash with respect to presence to a
  junction or interchange areas.  
- MAN_COLLNAME: Manner of the collision, were ther multiple vechiles
  involed in the crash.
- HARM_EVNAME: First harmful event, first injury produced by the event
  of a crash.
- LATITUDE: The location of the crash using global positioning (East and
  West).
- LONGITUD: The location of the crash using global positioning (North
  and South).
- RUR_URBNAME: Land Use, the segment of the traffic way on which the
  crash occurred based on urbanized areas.
- HOUR: The time of the crash in hours.
- MINUTE: The time of the crash in minutes.
- CITY: The location of the crash.
- MONTH: The month the crash occurred in.
- DAY: The day the crash occurred on.
- YEAR: The year in which the crash happened.
- COUNTY: The county in which the crash occurred in.
- PERMVIT: Number of motorists involved in the crash.
- PVH_INVL: Number of parked vehicles involved in the crash.
- VE_FORMS: Number of vehicles in-transport involved in the crash.
- PERNOTMVIT: The number of non-motorists in the crash.
- ST_CASE: Unique case number assigned to each crash.

# Research Goals and Questions

The goal of the project is to explore the data set to better understand
vehicle crashes. Understanding this topic better can lead to increased
awareness, targeted policing efforts, and identification of common
trends for accidents. Ultimately, the goal is the circumstances in which
individuals get into vehicular accidents, and how to avoid fatal
crashes.

In pursuit of the stated goal, we will explore the following questions:

1.  Does impairment affect fatality in crashes overall? When are
    impaired crashes most likely?

2.  What regions of the United States have the most fatal crashes? What
    conditions are present in those regions?

3.  How does the demographics of the driver affect crashes? Are changes
    based on occupants more prevalent for younger drivers?

4.  Are crashes affected by lighting and road conditions? How so, and
    what conditions are most impact?

5.  When are crashes most likely? Are there any seasonal effects, and
    are night crashes more likely than in the morning or afternoon?

6.  Does seatbelt use reduce injuries? Are people more likely to be
    ejected without wearing a seatbelt, and does seatbelt use prolong
    the time between the crash and the death of the driver?

### When are crashes most likely? Are there any seasonal effects, and are night crashes more likely than in the morning or afternoon?

``` r
df1 %>% ggplot(aes(x = DAY)) + geom_histogram() + facet_wrap(~MONTH)
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](README_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
df1 %>% ggplot(aes(x = MONTH)) + geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](README_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

It appears that fatal crashes occur the most in the beginning of the
year, and decrease heavily until December for all of the years.

``` r
df1 %>% ggplot(aes(x = HOUR)) + geom_histogram(bins = 100)
```

![](README_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

There is a strange outlier with hour, so I will remove that.

``` r
df1 %>% filter(HOUR <=24) %>% ggplot(aes(x = HOUR)) + geom_histogram() + scale_x_continuous(name="Hour", limits=c(0, 24))
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

    ## Warning: Removed 2 rows containing missing values (`geom_bar()`).

![](README_files/figure-gfm/unnamed-chunk-13-1.png)<!-- --> It appears
that the peak is around 17:00 military time, which is 5pm. Thus, crashes
appear to be increasingly likely as the day goes on, peaks at 5pm, and
has a minimum at around 4pm.

### Does seatbelt use reduce injuries? Are people more likely to be ejected without wearing a seatbelt, and does seatbelt use prolong the time between the crash and the death of the driver?

``` r
master$REST_USENAME %>% unique()
```

    ##  [1] "None Used / Not Applicable"                        
    ##  [2] "Shoulder and Lap Belt Used"                        
    ##  [3] "Unknown"                                           
    ##  [4] "DOT-Compliant Motorcycle Helmet"                   
    ##  [5] "No Helmet"                                         
    ##  [6] "Helmet, Other than DOT-Compliant Motorcycle Helmet"
    ##  [7] NA                                                  
    ##  [8] "Not Reported"                                      
    ##  [9] "Lap Belt Only Used"                                
    ## [10] "Helmet, Unknown if DOT Compliant"                  
    ## [11] "Other"                                             
    ## [12] "Shoulder Belt Only Used"                           
    ## [13] "Restraint Used - Type Unknown"                     
    ## [14] "Unknown if Helmet Worn"                            
    ## [15] "Reported as Unknown"                               
    ## [16] "None Used/Not Applicable"                          
    ## [17] "Racing-Style Harness Used"

``` r
master$RESTRAINT <- ifelse(master$REST_USENAME %in% c("None Used / Not Applicable", "Not Reported", "Reported as Unknown", "None Used/Not Applicable", "No Helmet"), "No", "Yes")
master %>% ggplot(aes(x = RESTRAINT)) + geom_bar()
```

![](README_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

Difficult to see if this is a result of the strange types of variables
possible. It isn’t possible to determine whether the person was wearing
the seatbelt or not in each individual crash.

``` r
master %>% filter(REST_USENAME == "Shoulder and Lap Belt Used") %>% ggplot(aes(x = YEAR)) + geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](README_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

It apppears that seat belt use has not changed over the years.

### Does impairment affect fatality in crashes overall? When are impaired crashes most likely?

``` r
master$ImpairmentAlcohol <- ifelse(master$DRINKINGNAME %in% c("No (Alcohol Not Involved)", "Unknown (Police Reported)", "Not Reported", "Reported as Unknown"), FALSE, TRUE)

master$ImpairmentDrugs <- ifelse(master$DRUGSNAME %in% c("No (drugs not involved)", "Unknown (Police Reported)", "Not Reported", "Reported as Unknown"), FALSE, TRUE)

master <- master %>% mutate(
  Impairment = as.logical(pmax(ImpairmentDrugs, ImpairmentAlcohol))
)

master %>% ggplot(aes(x = Impairment)) + geom_bar()
```

![](README_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
master %>% filter(Impairment == TRUE) %>%
  filter(HOUR <=24) %>% ggplot(aes(x = HOUR), fill = factor(MONTH)) + geom_bar(bins = 24)
```

    ## Warning in geom_bar(bins = 24): Ignoring unknown parameters: `bins`

![](README_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

### What regions of the United States have the most fatal crashes? What conditions are present in those regions?

``` r
master$West <- ifelse(master$STATENAME %in% c("Alaska", "Arizona", "California","Colorado", "Hawaii", "Idaho", "Montana", "Nevada", "New Mexico", "Oregon", "Utah", "Washington", "Wyoming"), "West", NA)

  
master$NorthEast <- ifelse(master$STATENAME %in% c("Connecticut", "Maine", "Massachusetts", "New Hampshire", "Rhode Island", "Vermont", "New Jersey", "New York", "Pennsylvania"), "NorthEast", NA)

master$South <- ifelse(master$STATENAME %in% c("Alabama", "Arkansas", "Delaware", "Florida", "Georgia", "Kentucky", "Louisiana", "Maryland", "Mississippi", "North Carolina", "Oklahoma", "South Carolina", "Tennessee", "Texas", "Virginia", "West Virginia"), "South", NA)

master$MidWest <- ifelse(master$STATENAME %in% c("Illinois", "Indiana", "Iowa", "Kansas", "Michigan", "Minnesota", "Missouri", "Nebraska", "North Dakota", "Ohio", "South Dakota", "Wisconsin"), "MidWest", NA)

master <- master %>% mutate(
  Region = as.logical(pmax(NorthEast, West, South, MidWest))
)
```
