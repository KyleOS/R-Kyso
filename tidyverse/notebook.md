---
title: "Test-notebook"
author: "Kyle"
date: 08/01/2021"
output: html_document AND markdown_document
---



Just a summary table.


```r
library(tidyverse)

mtcars %>% 
	group_by(cyl) %>% 
	summarise(mean_hp = mean(hp))
```

```
## # A tibble: 3 x 2
##     cyl mean_hp
##   <dbl>   <dbl>
## 1     4    82.6
## 2     6   122. 
## 3     8   209.
```

Interactive plot


```r
library(plotly)

plot_ly(mtcars, x = ~hp, y = ~qsec)
```

```
## Error in file(con, "rb"): cannot open the connection
```
