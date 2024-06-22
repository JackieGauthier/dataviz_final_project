---
title: "Data Visualization for Exploratory Data Analysis"
author: "Jacqueline Gauthier `jgauthier3710@floridapoly.edu`"
output: 
  html_document:
    keep_md: true
    toc: true
    toc_float: true
---

# Data Visualization Project 03


In this exercise you will explore methods to create different types of data visualizations (such as plotting text data, or exploring the distributions of continuous variables).


## PART 1: Density Plots

Using the dataset obtained from FSU's [Florida Climate Center](https://climatecenter.fsu.edu/climate-data-access-tools/downloadable-data), for a station at Tampa International Airport (TPA) for 2022, attempt to recreate the charts shown below which were generated using data from 2016. You can read the 2022 dataset using the code below: 


``` r
library(tidyverse)
library(lubridate)
library(ggridges)
library(viridis)
library(tidytext)
library(ggplot2)

weather_tpa <- read_csv("https://raw.githubusercontent.com/reisanar/datasets/master/tpa_weather_2022.csv")
# random sample 
sample_n(weather_tpa, 4)
```

```
## # A tibble: 4 × 7
##    year month   day precipitation max_temp min_temp ave_temp
##   <dbl> <dbl> <dbl>         <dbl>    <dbl>    <dbl>    <dbl>
## 1  2022     3     6          0          89       66     77.5
## 2  2022     9     9          0.13       88       75     81.5
## 3  2022     5    26          0          92       78     85  
## 4  2022     4     5          0          88       72     80
```

See https://www.reisanar.com/slides/relationships-models#10 for a reminder on how to use this type of dataset with the `lubridate` package for dates and times (example included in the slides uses data from 2016).

Using the 2022 data: 

(a) Create a plot like the one below:

<img src="https://github.com/reisanar/figs/raw/master/tpa_max_temps_facet.png" width="80%" style="display: block; margin: auto;" />

``` r
# Convert month to a factor to ensure correct ordering
weather_tpa$month <- factor(weather_tpa$month, levels = 1:12, labels = month.name)

# Create histograms for each month
ggplot(weather_tpa, aes(x = max_temp)) +
  geom_histogram(binwidth = 1, color = "black", aes(fill = month)) +
  scale_fill_viridis(discrete = TRUE, option = "D", direction = 1) +
  facet_wrap(~ month, ncol = 4) +
  labs(title = "",
       x = "Max Temperature",
       y = "Number of Days") +
  theme_bw() +
  theme(legend.position = "none")
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-3-1.png)<!-- -->



Hint: the option `binwidth = 3` was used with the `geom_histogram()` function.

(b) Create a plot like the one below:

<img src="https://github.com/reisanar/figs/raw/master/tpa_max_temps_density.png" width="80%" style="display: block; margin: auto;" />

Hint: check the `kernel` parameter of the `geom_density()` function, and use `bw = 0.5`.


``` r
# Create the density plot
ggplot(weather_tpa, aes(x = max_temp)) +
  geom_density(kernel = "gaussian", bw = 0.5, fill = "gray", alpha = 0.5) +
  labs(x = "Maximum temperature",
       y = "density") +
  theme_minimal()
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-5-1.png)<!-- -->



(c) Create a plot like the one below:

<img src="https://github.com/reisanar/figs/raw/master/tpa_max_temps_density_facet.png" width="80%" style="display: block; margin: auto;" />

Hint: default options for `geom_density()` were used.


``` r
ggplot(weather_tpa, aes(x = max_temp, fill = factor(month))) +
  geom_density(alpha = 0.5, color = "black") +
  facet_wrap(~ month, ncol = 4) +
  scale_fill_viridis_d() +
  scale_y_continuous(breaks = seq(0, 1, by = 0.05)) +
  scale_x_continuous(breaks = c(60, 70, 80, 90)) +
  labs(title = "Density Plot for each month in 2022",
       x = "Maximum Temperature",
       y = "") +
  theme_bw() +
  theme(legend.position = "none")
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-7-1.png)<!-- -->



(d) Generate a plot like the chart below:


<img src="https://github.com/reisanar/figs/raw/master/tpa_max_temps_ridges_plasma.png" width="80%" style="display: block; margin: auto;" />

Hint: use the`{ggridges}` package, and the `geom_density_ridges()` function paying close attention to the `quantile_lines` and `quantiles` parameters. The plot above uses the `plasma` option (color scale) for the _viridis_ palette.


``` r
ggplot(weather_tpa, aes(x = max_temp, y = month, fill = stat(x))) +
  geom_density_ridges_gradient(scale = 3, size = 1, rel_min_height = 0.01) +
  scale_fill_viridis_c(name = "", option = "C") +
  labs(title = "Maximum Temperature (in Fahrenheit)",
       x = "",
       y = "") +
  theme_minimal()
```

```
## Warning in geom_density_ridges_gradient(scale = 3, size = 1, rel_min_height =
## 0.01): Ignoring unknown parameters: `size`
```

```
## Warning: `stat(x)` was deprecated in ggplot2 3.4.0.
## ℹ Please use `after_stat(x)` instead.
## This warning is displayed once every 8 hours.
## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
## generated.
```

```
## Picking joint bandwidth of 1.93
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-9-1.png)<!-- -->
> I can't figure out how to add this line:  stat_density_ridges(quantile_lines = TRUE, quantiles = 0.5)



(e) Create a plot of your choice that uses the attribute for precipitation _(values of -99.9 for temperature or -99.99 for precipitation represent missing data)_.


``` r
# Replace missing values for precipitation with NA
weather_tpa <- weather_tpa %>%
  mutate(precipitation = na_if(precipitation, -99.99))

averagePrepMonth <- weather_tpa %>%
  group_by(month) %>%
  summarize(mean_temp = mean(ave_temp),
            meanPrep = mean(precipitation))

ggplot(averagePrepMonth, aes(x = month, y = meanPrep, fill = mean_temp)) +
  geom_col(alpha = 0.6, color = "black") +  # Use geom_col for bar plot
  labs(title = "Average Precipitation by Month",
       x = "", y = "",
       fill = "Mean Temperature") +
  scale_fill_viridis_c(option = "plasma", name = "Mean Temp [F]") +  # Color scale
  theme_minimal() +
  coord_flip()
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-10-1.png)<!-- -->



## PART 2 

> **You can choose to work on either Option (A) or Option (B)**. Remove from this template the option you decided not to work on. 


### Option (A): Visualizing Text Data

Review the set of slides (and additional resources linked in it) for visualizing text data: https://www.reisanar.com/slides/text-viz#1

Choose any dataset with text data, and create at least one visualization with it. For example, you can create a frequency count of most used bigrams, a sentiment analysis of the text data, a network visualization of terms commonly used together, and/or a visualization of a topic modeling approach to the problem of identifying words/documents associated to different topics in the text data you decide to use. 

Make sure to include a copy of the dataset in the `data/` folder, and reference your sources if different from the ones listed below:

- [Billboard Top 100 Lyrics](https://github.com/reisanar/datasets/blob/master/BB_top100_2015.csv)

- [RateMyProfessors comments](https://github.com/reisanar/datasets/blob/master/rmp_wit_comments.csv)

- [FL Poly News Articles](https://github.com/reisanar/datasets/blob/master/flpoly_news_SP23.csv)


(to get the "raw" data from any of the links listed above, simply click on the `raw` button of the GitHub page and copy the URL to be able to read it in your computer using the `read_csv()` function)


``` r
FLpolyNews <- read_csv("https://raw.githubusercontent.com/reisanar/datasets/master/flpoly_news_SP23.csv")
```

```
## Rows: 480 Columns: 3
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (2): news_title, news_summary
## date (1): news_date
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
head(FLpolyNews)
```

```
## # A tibble: 6 × 3
##   news_date  news_title                                             news_summary
##   <date>     <chr>                                                  <chr>       
## 1 2023-04-13 Purple Fire Robotics team tops U.S. combat bot stats,… Florida Pol…
## 2 2023-04-12 Q&A: Phoenix proud to be one of Florida Poly's first … David Schin…
## 3 2023-04-07 Florida Poly to carry out Board of Governors amended … Florida Pol…
## 4 2023-04-06 Q&A: Grad dreams of making impact with transportation… Isabella Mo…
## 5 2023-04-05 Florida Poly inks international partnership with Fulb… Florida Pol…
## 6 2023-04-03 Florida Poly researcher: Scrapping recycling programs… As municipa…
```


``` r
# Combine title and summary into one text column
FLpolyNews <- FLpolyNews %>%
  mutate(text = paste(news_title, news_summary),
         year = year(ymd(news_date)))
```


``` r
# Tokenize bigrams
FLpoly_bigrams <- FLpolyNews %>%
  unnest_tokens(bigram, text, token = "ngrams", n = 2) %>%
  separate(bigram, c("word1", "word2"), sep = " ") %>%
  filter(!word1 %in% stop_words$word) %>%  # remove stopwords
  filter(!word2 %in% stop_words$word) %>%  # remove stopwords
  filter(!word1 %in% c("fla", "florida", "poly", "university", "polytechnic")) %>%
  filter(!word2 %in% c("fla", "florida", "poly", "university", "polytechnic")) %>%
  unite(bigram, word1, word2, sep = " ") %>%
  count(bigram, sort = TRUE) %>%
  top_n(20, n) %>%
  ungroup() %>%
  mutate(bigram = fct_inorder(bigram))

# Create a bar plot showing the token frequency (bigrams)
ggplot(FLpoly_bigrams, aes(x = n, y = fct_rev(bigram))) +
  geom_col(fill = "pink") +
  guides(fill = FALSE) +
  labs(x = "", y = "") +
  scale_fill_viridis_d() +
  theme_minimal() +
  ggtitle("Frequency of Top 20 Bigrams in FLpolyNews Dataset")
```

```
## Warning: The `<scale>` argument of `guides()` cannot be `FALSE`. Use "none" instead as
## of ggplot2 3.3.4.
## This warning is displayed once every 8 hours.
## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
## generated.
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-13-1.png)<!-- -->


``` r
library(wordcloud)
```

```
## Warning: package 'wordcloud' was built under R version 4.3.3
```

```
## Loading required package: RColorBrewer
```

``` r
library(RColorBrewer)

# Preprocess the text
FLpolyNews_words <- FLpolyNews %>%
  unnest_tokens(word, text) %>%
  anti_join(stop_words) %>%
  filter(!word %in% c("fla", "florida", "poly", "university", "polytechnic")) %>%
  count(word, sort = TRUE)
```

```
## Joining with `by = join_by(word)`
```

``` r
# Set up the color palette for the word cloud
pal <- brewer.pal(8, "Dark2")

# Create the word cloud
set.seed(1234)
wordcloud(words = FLpolyNews_words$word,
          freq = FLpolyNews_words$n,
          min.freq = 2,
          max.words = 100,
          random.order = FALSE,
          rot.per = 0.35,
          colors = pal)
```

![](Gauthier_project_03_files/figure-html/unnamed-chunk-14-1.png)<!-- -->

``` r
# Save the word cloud as an image
png("FLpolyNews_wordcloud.png", width = 800, height = 600)
wordcloud(words = FLpolyNews_words$word,
          freq = FLpolyNews_words$n,
          min.freq = 2,
          max.words = 100,
          random.order = FALSE,
          rot.per = 0.35,
          colors = pal)
dev.off()
```

```
## png 
##   2
```
