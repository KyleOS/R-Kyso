---
title: "Mass Shooting in US (using plotly)"
author: "Anton Aksyonov"
date: "9 oct 2017"
output:
  html_document:
    number_sections: true
    toc: true
    fig_width: 8
    fig_height: 5.5
    theme: yeti
    highlight: textmate
    code_folding: hide
---
<style type="text/css">

body{ /* Normal  */
      font-family: "PT Serif";
      font-size: 14px;
  }
td {  /* Table  */
  font-family: "PT Serif";
  font-size: 12px;
}
h1.title {
  font-family: "PT Serif";
  font-size: 38px;
  color: Black;
}
h1 { /* Header 1 */
  font-family: "PT Serif";
  font-size: 28px;
  color: Black;
}
h2 { /* Header 2 */
    font-family: "PT Serif";
    font-size: 22px;
  color: Black;
}
h3 { /* Header 3 */
  font-size: 18px;
  color: Black;
}
code.r{ /* Code block */
    font-size: 12px;
}
pre { /* Code block - determines code spacing between lines */
    font-size: 12px;
}
</style>



# Intro
The purpose of this report is to consolidate the basic data visualization skills with the Plotly package. Periodically, I will add new graphics using the new features. I really like the Plotly package, because it allows you to open a lot of hidden information in the data due to its interactivity.

# Context
Mass Shootings in the United States of America (1966-2017) The US has witnessed 398 mass shootings in last 50 years that resulted in 1996 deaths and 2488 injured. The latest and the worst mass shooting of October 2, 2017 killed 58 and injured 515 so far. The number of people injured in this attack is more than the number of people injured in all mass shootings of 2015 and 2016 combined. The average number of mass shootings per year is 7 for the last 50 years that would claim 39 lives and 48 injured per year. 

# Load Data
## Download Packages
Download the necessary packages for the manipulation and visualization of data

```r
library(data.table)
library(readr)
library(plotly)
library(ggplot2)
library(maps)
library(tm)
library(wordcloud)
```

## Loading data, and a small addition to them.
Load the data from [source](https://www.kaggle.com/zusmani/us-mass-shootings-last-50-years). 
Perform the first manipulations with the date.
Extract the year and month from the date and combine the variables of gender


```r
MS_dataset <- read_csv("./us-mass-shootings-last-50-years/Mass Shootings Dataset Ver 5.csv"
                              , col_types = cols(Date = col_date(format = "%m/%d/%Y")))

MS_dataset <- data.table(MS_dataset)

MS_dataset[,Month:=as.factor(month(Date))]
MS_dataset[,Year_n:=as.numeric(year(Date))]
MS_dataset[,Year:=as.factor(year(Date))]

MS_dataset[Gender=='M',Gender:="Male"]
MS_dataset[Gender=='M/F',Gender:="Male/Female"]
MS_dataset[is.na(Gender),Gender:="Unknown"]
MS_dataset[,Gender:=as.factor(Gender)]
```


# Basic examples of visualization using the Plotly package

## Mass Shootings in US by years and month



































