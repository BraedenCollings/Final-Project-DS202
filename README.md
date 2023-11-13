
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

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.2     ✔ purrr     1.0.2
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

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
df_2018 <- left_join(accident_2018, person_2018, by=c('YEAR', 'ST_CASE'))
df_2019 <- left_join(accident_2019, person_2019, by=c('YEAR', 'ST_CASE'))
df_2020 <- left_join(accident_2020, person_2020, by=c('YEAR', 'ST_CASE'))
df_2021 <- left_join(accident_2021, person_2021, by=c('YEAR', 'ST_CASE'))
```

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
head(df1)
```

    ## # A tibble: 6 × 40
    ## # Groups:   STATENAME, YEAR [1]
    ##   STATENAME ST_CASE PERNOTMVIT VE_FORMS PVH_INVL PERMVIT COUNTY  CITY MONTH
    ##   <chr>       <dbl>      <dbl>    <dbl>    <dbl>   <dbl>  <dbl> <dbl> <dbl>
    ## 1 Alabama     10001          0        1        0       1     73   330     2
    ## 2 Alabama     10002          0        1        0       1     89  1730     2
    ## 3 Alabama     10003          0        3        0       3    101  2130     1
    ## 4 Alabama     10003          0        3        0       3    101  2130     1
    ## 5 Alabama     10003          0        3        0       3    101  2130     1
    ## 6 Alabama     10004          0        1        0       1     73   350     1
    ## # ℹ 31 more variables: DAY <dbl>, YEAR <dbl>, HOUR <dbl>, MINUTE <dbl>,
    ## #   RUR_URBNAME <chr>, LATITUDE <dbl>, LONGITUD <dbl>, HARM_EVNAME <chr>,
    ## #   MAN_COLLNAME <chr>, RELJCT2NAME <chr>, WRK_ZONENAME <chr>,
    ## #   LGT_CONDNAME <chr>, WEATHER1NAME <chr>, SCH_BUSNAME <chr>, FATALS <dbl>,
    ## #   DRUNK_DR <dbl>, ...26 <dbl>, AGE <dbl>, SEXNAME <chr>, INJ_SEVNAME <chr>,
    ## #   REST_USENAME <chr>, EJECTIONNAME <chr>, DRINKINGNAME <chr>,
    ## #   DRUGSNAME <chr>, DOANAME <chr>, LAG_HRSNAME <chr>, WORK_INJNAME <chr>, …

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

1.  Does impairment affect crashes overall? When are impaired crashes
    most likely?

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
