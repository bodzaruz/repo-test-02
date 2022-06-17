---
title: "Zadanie 1"
author: "imię nazwisko"
date: "2022-06-17 15:34:15"
output:
  html_document:
    keep_md: true
  html_notebook:
    css: style_wej.css
---









## Zad. 1.
W podkatalogu 'data' znajdują dane o finalistach z olimpiady matematycznej, wraz z informacją z jakich szkół i jakich województw pochodzą (dane pochodzą ze strony: http://smarterpoland.pl).

### a) [1 pkt.]
Wczytać dane i zapisać pod nazwą `TT`.

<div class='rozwiazanie'> Rozwiązanie</div>
<!-- start rozwiązanie -->

```r
library(readr)
T1 <- read_delim("data/olimp.csv", ";", 
    escape_double = FALSE, trim_ws = TRUE)
```

```
## Rows: 4104 Columns: 8
## -- Column specification --------------------------------------------------------
## Delimiter: ";"
## chr (6): imie, nazwisko, klasa, szkola, miasto, wojewodztwo
## dbl (2): olimpiada, miejsce
## 
## i Use `spec()` to retrieve the full column specification for this data.
## i Specify the column types or set `show_col_types = FALSE` to quiet this message.
```
<!-- koniec rozwiązanie -->
<div class='punkty' pkt='0.9' pktdod=''>Nazwa tabeli miała być `TT`</div>


### b) [1 pkt.]
Ile zarejestrowano olimpiad?

<div class='rozwiazanie'> Rozwiązanie</div>
<!-- start rozwiązanie -->

```r
max(unique(T1$olimpiada))
```

```
## [1] 59
```
<!-- koniec rozwiązanie -->
<div class='punkty' pkt='0' pktdod=''>Ile zarejestrowano, nie ile było.</div>


### c) [1 pkt.]
Z tabeli finalistów wybrać tylko tych, którzy znaleźli się w pierwszej trójce.

<div class='rozwiazanie'> Rozwiązanie</div>
<!-- start rozwiązanie -->

```r
library(tidyverse)
```

```
## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --
```

```
## v ggplot2 3.3.5     v dplyr   1.0.8
## v tibble  3.1.6     v stringr 1.4.0
## v tidyr   1.2.0     v forcats 0.5.1
## v purrr   0.3.4
```

```
## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
T1%>%filter(miejsce%>%between(1,3))
```

```
## # A tibble: 168 x 8
##    olimpiada miejsce imie      nazwisko    klasa szkola miasto       wojewodztwo
##        <dbl>   <dbl> <chr>     <chr>       <chr> <chr>  <chr>        <chr>      
##  1         1       1 Witold    Bohdanowicz <NA>  <NA>   Zyrardow     mazowieckie
##  2         1       2 Andrzej   Ehrenfeucht <NA>  <NA>   Lodz         lodzkie    
##  3         1       3 Stanislaw Basinski    <NA>  <NA>   Dabrowa Gor~ slaskie    
##  4         2       1 Andrzej   Schinzel    <NA>  <NA>   Sandomierz   swietokrzy~
##  5         2       2 Cezary    Bowszyc     <NA>  <NA>   Wabrzezno    kujawsko-p~
##  6         2       3 Wiktor    Galazka     <NA>  <NA>   Garwolin     mazowieckie
##  7         3       1 Jerzy     Browkin     <NA>  <NA>   Warszawa     mazowieckie
##  8         3       2 Edward    Jozefowicz  <NA>  <NA>   Lodz         lodzkie    
##  9         3       3 Jacek     Kudrewicz   <NA>  <NA>   Warszawa     mazowieckie
## 10         4       1 Wieslaw   Szlenk      <NA>  <NA>   Warszawa     mazowieckie
## # ... with 158 more rows
```
<!-- koniec rozwiązanie -->
<div class='punkty' pkt='1' pktdod=''> </div>

### d) [1 pkt.]
Jaka była średnia i mediana pozycji finalistów pochodzących z Krakowa?

<div class='rozwiazanie'> Rozwiązanie</div>
<!-- start rozwiązanie -->

```r
library(dplyr)
T1%>%filter(
  T1$miasto=="Krakow",
  ) %>%
  group_by(miasto) %>%
  summarise(
    miejsce_sr=miejsce%>% mean(),
    miejsce_med=miejsce%>% median(),
    .groups='drop'
  )
```

```
## # A tibble: 1 x 3
##   miasto miejsce_sr miejsce_med
##   <chr>       <dbl>       <dbl>
## 1 Krakow       45.3          42
```
<!-- koniec rozwiązanie -->
<div class='punkty' pkt='0.9' pktdod=''>Syntaktycznie nie jest to błąd, ale proszę nie stosować 'T1$miasto' filtrze odwołującej się do tabeli `T1`. Wystarczy 'miasto'.</div>


### e) [1 pkt.]
Ilu finalistów było z każdego województwa?

<div class='rozwiazanie'> Rozwiązanie</div>
<!-- start rozwiązanie -->

<!-- koniec rozwiązanie -->
<div class='punkty' pkt='0' pktdod=''> </div>
