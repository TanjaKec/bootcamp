---
date: "2016-04-09T16:50:16+02:00"
title: Data Visuaisation
output: 
  learnr::tutorial
weight: 2
---

Most of you, if not all, would be familiar in creating the graphs in Excel. Software such Excel has a predifined set of menu options for plotting the data that is focus a the end result: "pritty graph". Those types of menues assume data to be in a format ready for plotting, which when you get a raw data is hardly the case. You are most likelly going to have organse and wrangle your data to make it ready for effective visualisation. 

### Grammar of Graphics

The [grammer of graphics](http://vita.had.co.nz/papers/layered-grammar.html) enables a structured way of creating a plot by adding the components as layers making it look effective and atractive. 

Enables you to specify building blocks of a plot and to combine them to create graphical display you want. There are 8 building blocks:

- data

- aesthetic mapping

- geometric object

- statistical transformations

- scales

- coordinate system

- position adjustments

- faceting

Imagine talking about baking a cake and adding a chery on the top. 🎂🍒 This philosophy has been built into the [`ggplot`](https://ggplot2.tidyverse.org/reference/) package by [Hadle Wickham](http://hadley.nz) for creating elegant and complex plots in R.


#### ggplot2

Learning how to use the `ggplot2` package can be challenging, but the results are higly revording and just like R itself it becomes easier the more you use it.

The best way to master it by practicink. So let us create a first `ggplot`. 😃
What we need to do is the following:

1. Wrangle the data in the format suitable for visualisation.
2. "Initialise" a plot with `ggplot()`
3. Add layers with `geom_` functions


```r
# load the packages
suppressPackageStartupMessages(library(dplyr))
suppressPackageStartupMessages(library(gapminder))
suppressPackageStartupMessages(library(ggplot2))

# wrangle the data (can you remember what does this code do?)
gapminder_pipe <- gapminder %>%
  filter(continent == "Europe" & year ==  2007) %>%
  mutate(pop_e6 = pop / 1000000)

# plot the data
ggplot(gapminder_pipe, aes(x = pop_e6, y = lifeExp)) +
  geom_point(col ="red")
```

<img src="/day2/Visualisation/_index.en_files/figure-html/unnamed-chunk-1-1.png" width="768" style="display: block; margin: auto;" />
🤓💡 **Tip**: You can use the following code template to make graphs with **ggplot2**:

```
ggplot(data = <DATA>, (mapping = aes(<MAPPINGS>)) + <GEOM_FUNCTION>()
```

##### <span style="color:red">ggplot()</span> gallery
Run the following code to see what graphs it's going to produce.


```r
ggplot(data = gapminder, mapping = aes(x = lifeExp), binwidth = 10) +
  geom_histogram()
#
ggplot(data = gapminder, mapping = aes(x = lifeExp)) +
  geom_density()
#
ggplot(data = gapminder, mapping = aes(x = continent, color = continent)) +
  geom_bar()
#
ggplot(data = gapminder, mapping = aes(x = continent, fill = continent)) +
  geom_bar()
```

##### 🗣👥 Confer with your neighbours: 
Does the life expectancy depend upon the population size?

`y = b_0 + b_1 x + e`

Run this code in your console to fit the model `pop` vs `lifeExp`.

Pay attention to spelling, capitalization, and parentheses!

```r
m1 <- lm(gapminder_pipe$lifeExp ~ gapminder_pipe$pop_e6)
summary(m1)
```

**Can you answer the question usig the output of the fitted model?**

```r
m1 <- lm(gapminder_pipe$lifeExp ~ gapminder_pipe$pop_e6)
summary(m1)
```

```
## 
## Call:
## lm(formula = gapminder_pipe$lifeExp ~ gapminder_pipe$pop_e6)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
## -6.324 -2.562  1.007  2.245  4.277 
## 
## Coefficients:
##                        Estimate Std. Error t value Pr(>|t|)    
## (Intercept)           77.477421   0.721723 107.351   <2e-16 ***
## gapminder_pipe$pop_e6  0.008762   0.023779   0.368    0.715    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 3.025 on 28 degrees of freedom
## Multiple R-squared:  0.004826,	Adjusted R-squared:  -0.03072 
## F-statistic: 0.1358 on 1 and 28 DF,  p-value: 0.7153
```

##### 👉 Practice ⏰💻: Use gapminder data.

Does the life expectancy depend upon the GDP per capita?

1) Have a glance at the data. (tip: `sample_n(df, n)`)

2) Produce a scattep plot: what does it tell you?

3) Fit a regression model: is there a relationship? How strong is it?
Is the relationship linear? What conclusion(s) can you draw?

4) What are the other questions you could ask; could you provide the answers to them?

##### 😃🙌 Solution: code Q1; sample

```r
sample_n(gapminder, 30)
```

```
## # A tibble: 30 x 6
##    country       continent  year lifeExp      pop gdpPercap
##    <fct>         <fct>     <int>   <dbl>    <int>     <dbl>
##  1 Colombia      Americas   2002    71.7 41008227     5755.
##  2 Lebanon       Asia       1977    66.1  3115787     8660.
##  3 Sri Lanka     Asia       1982    68.8 15410151     1648.
##  4 Vietnam       Asia       2007    74.2 85262356     2442.
##  5 Guinea-Bissau Africa     1987    41.2   927524      736.
##  6 Tanzania      Africa     1992    50.4 26605473      826.
##  7 Venezuela     Americas   1962    60.8  8143375     8423.
##  8 Togo          Africa     1992    58.1  3747553     1034.
##  9 Ethiopia      Africa     1997    49.4 59861301      516.
## 10 Cuba          Americas   2002    77.2 11226999     6341.
## # … with 20 more rows
```

##### 😃🙌 Solution: code Q2; Plot the data;

```r
ggplot(gapminder, aes(x = gdpPercap, y = lifeExp)) +
    geom_point(alpha = 0.2, shape = 21, fill = "blue", colour="black", size = 5) +
  geom_smooth(method = "lm", se = F, col = "maroon3") +
  geom_smooth(method = "loess", se = F, col = "limegreen") 
```

<img src="/day2/Visualisation/_index.en_files/figure-html/unnamed-chunk-6-1.png" width="768" style="display: block; margin: auto;" />

##### 😃🙌 Solution: code Q3; simple regression model

```r
my.model <- lm(gapminder_pipe$lifeExp ~ gapminder_pipe$gdpPercap)
summary(my.model)
```

```
## 
## Call:
## lm(formula = gapminder_pipe$lifeExp ~ gapminder_pipe$gdpPercap)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -2.79839 -1.30472  0.00807  1.33443  2.87766 
## 
## Coefficients:
##                           Estimate Std. Error t value Pr(>|t|)    
## (Intercept)              7.227e+01  6.942e-01 104.113  < 2e-16 ***
## gapminder_pipe$gdpPercap 2.146e-04  2.514e-05   8.537  2.8e-09 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 1.598 on 28 degrees of freedom
## Multiple R-squared:  0.7225,	Adjusted R-squared:  0.7125 
## F-statistic: 72.88 on 1 and 28 DF,  p-value: 2.795e-09
```

#### Adding layers to your <span style="color:red">`ggplot()`</span>

<img src="/day2/Visualisation/_index.en_files/figure-html/unnamed-chunk-8-1.png" width="768" style="display: block; margin: auto;" />
#### 💪 There is a challenge: 

- `dplyr`'s `group_by()` function enables you to group your data. It allows you to create a separate df that splits the original df by a variable.

- `boxplot()` function produces boxplot(s) of the given (grouped) values.

Knowing about `group_by()` and `boxplot()` function, coud you compute the median life expectancy for year 2007 by continent and visualise your result?

##### 😃🙌 Solution: code

Let us look at the median life expectancy for each continent

```r
gapminder %>%
    group_by(continent) %>%
    summarise(lifeExp = median(lifeExp))
```

```
## # A tibble: 5 x 2
##   continent lifeExp
##   <fct>       <dbl>
## 1 Africa       47.8
## 2 Americas     67.0
## 3 Asia         61.8
## 4 Europe       72.2
## 5 Oceania      73.7
```

**We are lucky that we live in Serbia, ie. Europe!!!** 😅

##### 😃🙌 Solution: graph 

<img src="/day2/Visualisation/_index.en_files/figure-html/unnamed-chunk-10-1.png" width="768" style="display: block; margin: auto;" />

##### useful links: 

[tidyverse, visualization, and manipulation basics](https://www.rstudio.com/resources/webinars/tidyverse-visualization-and-manipulation-basics/)

[Introduction to R graphics with ggplot2](http://tutorials.iq.harvard.edu/R/Rgraphics/Rgraphics.html#introduction)

[`gglopt` cheat sheet](https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf)

[from Data to Viz](https://www.data-to-viz.com/)

[An example from Financial Times](http://johnburnmurdoch.github.io/slides/r-ggplot/#/)

[BBC Visual and Data Journalism cookbook for R graphics](https://bbc.github.io/rcookbook/)



-----------------------------
© 2019 Tatjana Kecojevic
