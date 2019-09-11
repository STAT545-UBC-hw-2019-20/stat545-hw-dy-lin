Gapminder Exploration
================

## Function \#1: `mean()`

Calculate the average life expectancy of all countries in `gapminder`:

``` r
mean(gapminder$lifeExp)
```

    ## [1] 59.47444

Calculate the average life expectancy of Canada:

``` r
mean(gapminder[which(gapminder$country == "Canada"),]$lifeExp)
```

    ## [1] 74.90275

Calculate the continental average for each numeric data column:

``` r
header <- c("Life Expectancy", "Population", "GDP per Capita")
temp <- data.frame()
for (continent in unique(gapminder$continent)) {
    current <- c(
        mean(gapminder[gapminder$continent==continent,]$lifeExp, na.rm = TRUE), 
        mean(gapminder[gapminder$continent==continent,]$pop, na.rm = TRUE),
        mean(gapminder[gapminder$continent==continent,]$gdpPercap, na.rm=TRUE))
    temp <- rbind(temp,current)
}
names(temp) <- header
rownames(temp) <- unique(gapminder$continent)

temp
```

    ##          Life Expectancy Population GDP per Capita
    ## Asia            60.06490   77038722       7902.150
    ## Europe          71.90369   17169765      14469.476
    ## Africa          48.86533    9916003       2193.755
    ## Americas        64.65874   24504795       7136.110
    ## Oceania         74.32621    8874672      18621.609

## Function \#2: `max()` and `which()`

Extract the country (or countries) with the highest life expectancy:

``` r
gapminder[which(gapminder$lifeExp == max(gapminder$lifeExp)),]
```

    ## # A tibble: 1 x 6
    ##   country continent  year lifeExp       pop gdpPercap
    ##   <fct>   <fct>     <int>   <dbl>     <int>     <dbl>
    ## 1 Japan   Asia       2007    82.6 127467972    31656.

## Function \#3: `min()` and `which()`

Extract the country (or countries) with the lowest GDP per capita:

``` r
gapminder[which(gapminder$gdpPercap == min(gapminder$gdpPercap)),]
```

    ## # A tibble: 1 x 6
    ##   country          continent  year lifeExp      pop gdpPercap
    ##   <fct>            <fct>     <int>   <dbl>    <int>     <dbl>
    ## 1 Congo, Dem. Rep. Africa     2002    45.0 55379852      241.

## Function \#4: `length()` and `unique()`

Extract the number of unique countries in `gapminder`:

``` r
length(unique(gapminder$country))
```

    ## [1] 142

## Function \#5: `summary()`

Get a summary of `gapminder`:

``` r
summary(gapminder)
```

    ##         country        continent        year         lifeExp     
    ##  Afghanistan:  12   Africa  :624   Min.   :1952   Min.   :23.60  
    ##  Albania    :  12   Americas:300   1st Qu.:1966   1st Qu.:48.20  
    ##  Algeria    :  12   Asia    :396   Median :1980   Median :60.71  
    ##  Angola     :  12   Europe  :360   Mean   :1980   Mean   :59.47  
    ##  Argentina  :  12   Oceania : 24   3rd Qu.:1993   3rd Qu.:70.85  
    ##  Australia  :  12                  Max.   :2007   Max.   :82.60  
    ##  (Other)    :1632                                                
    ##       pop              gdpPercap       
    ##  Min.   :6.001e+04   Min.   :   241.2  
    ##  1st Qu.:2.794e+06   1st Qu.:  1202.1  
    ##  Median :7.024e+06   Median :  3531.8  
    ##  Mean   :2.960e+07   Mean   :  7215.3  
    ##  3rd Qu.:1.959e+07   3rd Qu.:  9325.5  
    ##  Max.   :1.319e+09   Max.   :113523.1  
    ##
