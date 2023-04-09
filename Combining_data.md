# ---
title: "Cyclistics_combining_data"
author: "Mansi Raghav"
date: '2023-04-09'
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

# CaseStudy: Cyclistic

## Case Background

As a junior data analyst working in the marketing analyst team at Cyclistic (a bike-sharing company active in Chicago), I am tasked with understanding how casual riders and annual members use Cyclistic bikes differently. Casual riders consist of customers that purchase single-ride or full-day passes, whereas annual members subscribe yearly for unlimited biking access. The marketing director theorizes that the company's future success depends on maximizing the number of yearly memberships by converting casual riders into annual members. Pending executive approval, my team will be designing a new marketing strategy that pursues this idea.

To inform any decision-making behind Cyclistic's new marketing strategy, the goal of this project will be to uncover and convey actionable insights.

This is to document how i used R language to be able to work with 12 large data sets of 12 previous months data of a fictional company Cyclistic Bike share:

```{r}
library(tidyverse) #basic functions
library(janitor) #to clean data
library(lubridate)
library(hms)
```

### Importing the Files

just to make sure there are no previous objects open in our directory.

```{r}
rm(list = ls()) #removing any previous objects
dir("data", full.names = T)
```

Now a directory names data is created lets import the xlsx files we have.
```{r}
df1 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202106-divvy-tripdata.csv")
df2 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202107-divvy-tripdata.csv")
df3 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202108-divvy-tripdata.csv")
df4 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202109-divvy-tripdata.csv")
df5 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202110-divvy-tripdata.csv")
df6 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202111-divvy-tripdata.csv")
df7 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202112-divvy-tripdata.csv")
df8 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202201-divvy-tripdata.csv")
df9 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202202-divvy-tripdata.csv")
df10 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202203-divvy-tripdata.csv")
df11 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202204-divvy-tripdata.csv")
df12 <- read.csv("C:/Users/agraj/OneDrive/Desktop/Data Analyst/case study/data/202205-divvy-tripdata.csv")
```

all 12 data frames containing data are now stored in 12 variables. Next we Combine them into one file where we can work on them.

```{r}
ride_data <- rbind(df1,df2,df3,df4,df5,df6,df7,df8,df9,df10,df11,df12)
```
used rbind as it will row-bind the data and thats what we needed, ride_data now contains the data of all 12 data frames (12 months) you can think of it like UNION in SQL.

### cleaning & saving the file

Now to be sure we remove any empty cols n rows we run a little code

```{r}
ride_data <- remove_empty(ride_data, which = "rows")
ride_data <- remove_empty(ride_data, which = "cols")
```

saving:

```{r}
write.csv(ride_data, "C:\\Users\\agraj\\OneDrive\\Desktop\\Data Analyst\\case study\\data\\ride_data.csv", row.names = FALSE)
```

now ride_data file is downloaded we can now easily work on excel and after making the columns we want for analysis we will go to tableau to make its visualizations to see whats the story data is telling us.

after creating visualizations in tableau i created a report of the findings and possible paths we can take for meeting our business goals, check that out:

https://github.com/Agraj/Cyclistic_bikeshare_analysis/blob/main/CyclisticsReport.pptx
