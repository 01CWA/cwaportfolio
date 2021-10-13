---
title: R Process for Cyclistic's Bike-Share Project
subtitle: " "
author: Carol Addassi
excerpt: "These are the cleaning and analysis steps in R."
date: '2021-08-10'
slug: []
categories: []
tags:
  - case-study
---

### Cyclistic_Exercise_Full_Year_Analysis ###

This analysis is based on the Divvy case study ["Sophisticated, Clear, and Polished’: Divvy and Data Visualization"](https://artscience.blog/home/divvy-dataviz-case-study) written by Kevin Hartman. The purpose of this script is to consolidate downloaded Divvy data into a single dataframe and then conduct simple analysis to help answer the key question: “In what ways do members and casual riders use Divvy bikes differently?”



### Load required packages

library(tidyverse)  #helps wrangle data
library(lubridate)  #helps wrangle date attributes
library(ggplot2)  #helps visualize data  
library(openxlsx)  #read in xlsx data files
getwd() #displays your working directory
setwd("/Users/caroladdassi/RProjects/Case_Study_Cyclistics/data/e_xlsx") #sets your working directory to simplify calls to data ... make sure to use your OWN username instead of mine.)

#=====================
### Step 1: Collect Data
#=====================
### Upload  datasets (xlsx files transformed in Excel) here

m1_07_2020 <- read.xlsx("D2020_07_e.xlsx")
m2_08_2020 <- read.xlsx("D2020_08_e.xlsx")
m3_09_2020 <- read.xlsx("D2020_09_e.xlsx")
m4_10_2020 <- read.xlsx("D2020_10_e.xlsx")
m5_11_2020 <- read.xlsx("D2020_11_e.xlsx")
m6_12_2020 <- read.xlsx("D2020_12_e.xlsx")
m7_01_2021 <- read.xlsx("D2021_01_e.xlsx")
m8_02_2021 <- read.xlsx("D2021_02_e.xlsx")
m9_03_2021 <- read.xlsx("D2021_03_e.xlsx")
m10_04_2021 <- read.xlsx("D2021_04_e.xlsx")
m11_05_2021 <- read.xlsx("D2021_05_e.xlsx")
m12_06_2021 <- read.xlsx("D2021_06_e.xlsx")

#====================================================
### Step2: Wrangle Data and Combine Into a Single File
#====================================================
### Compare column names each of the files
### While the names don't have to be in the same order, they DO need to match perfectly before we can use a command to join them into one file
colnames(m1_07_2020)
colnames(m2_08_2020)
colnames(m3_09_2020)
colnames(m4_10_2020)
colnames(m5_11_2020)
colnames(m6_12_2020)
colnames(m7_01_2021)
colnames(m8_02_2021)
colnames(m9_03_2021)
colnames(m10_04_2021)
colnames(m11_05_2021)
colnames(m12_06_2021)

### Rename columns  to make them consisent with q1_2020 (as this will be the supposed going-forward table design for Divvy. Turns out it wasn't as the data I'm using is well after q1_2020.)
### Note there are currently 3 additonal columns in my files after some data transforming in Excel.
(m1_07_2020 <- rename(m1_07_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m2_08_2020 <- rename(m2_08_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m3_09_2020 <- rename(m3_09_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m4_10_2020 <- rename(m4_10_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m5_11_2020 <- rename(m5_11_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m6_12_2020 <- rename(m6_12_2020
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m7_01_2021 <- rename(m7_01_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m8_02_2021 <- rename(m8_02_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m9_03_2021 <- rename(m9_03_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m10_04_2021 <- rename(m10_04_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m11_05_2021 <- rename(m11_05_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

(m12_06_2021 <- rename(m12_06_2021
                      ,trip_id = ride_id
                      ,bikeid = rideable_type 
                      ,start_time = started_at  
                      ,end_time = ended_at  
                      ,from_station_name = start_station_name 
                      ,from_station_id = start_station_id 
                      ,to_station_name = end_station_name 
                      ,to_station_id = end_station_id 
                      ,usertype = member_casual))

### Inspect the dataframes and look for incongruencies
str(m1_07_2020)
str(m2_08_2020)
str(m3_09_2020)
str(m4_10_2020)
str(m5_11_2020)
str(m6_12_2020)
str(m7_01_2021)
str(m8_02_2021)
str(m9_03_2021)
str(m10_04_2021)
str(m11_05_2021)
str(m12_06_2021)

#### Convert ride_id and rideable_type to character so that they can stack correctly
#### Convert trip_id and bike_type to character so that they can stack correctly
m1_07_2020 <-  mutate(m1_07_2020, trip_id = as.character(trip_id)
                   ,bikeid = as.character(bikeid))
m2_08_2020 <-  mutate(m2_08_2020, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m3_09_2020 <-  mutate(m3_09_2020, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m4_10_2020 <-  mutate(m4_10_2020, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m5_11_2020 <-  mutate(m5_11_2020, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m6_12_2020 <-  mutate(m6_12_2020, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m7_01_2021 <-  mutate(m7_01_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m8_02_2021 <-  mutate(m8_02_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m9_03_2021 <-  mutate(m9_03_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m10_04_2021 <-  mutate(m10_04_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m11_05_2021 <-  mutate(m11_05_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))
m12_06_2021 <-  mutate(m12_06_2021, trip_id = as.character(trip_id)
                      ,bikeid = as.character(bikeid))

### Convert ride_length to double so that they can stack correctly
- m1_07_2020 <-  mutate(m1_07_2020, ride_length = as.double(ride_length))
- m2_08_2020 <-  mutate(m2_08_2020, ride_length = as.double(ride_length))
- m3_09_2020 <-  mutate(m3_09_2020, ride_length = as.double(ride_length))
- m4_10_2020 <-  mutate(m4_10_2020, ride_length = as.double(ride_length))
- m5_11_2020 <-  mutate(m5_11_2020, ride_length = as.double(ride_length))
- m6_12_2020 <-  mutate(m6_12_2020, ride_length = as.double(ride_length))
- m7_01_2021 <-  mutate(m7_01_2021, ride_length = as.double(ride_length))
- m8_02_2021 <-  mutate(m8_02_2021, ride_length = as.double(ride_length))
- m9_03_2021 <-  mutate(m9_03_2021, ride_length = as.double(ride_length))
- m10_04_2021 <-  mutate(m10_04_2021, ride_length = as.double(ride_length))
- m11_05_2021 <-  mutate(m11_05_2021, ride_length = as.double(ride_length))
- m12_06_2021 <-  mutate(m12_06_2021, ride_length = as.double(ride_length))

### Convert from_station_id and to_station_id  to double so that they can stack correctly.
- m1_07_2020 <-  mutate(m1_07_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m2_08_2020 <-  mutate(m2_08_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m3_09_2020 <-  mutate(m3_09_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m4_10_2020 <-  mutate(m4_10_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m5_11_2020 <-  mutate(m5_11_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m6_12_2020 <-  mutate(m6_12_2020, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m7_01_2021 <-  mutate(m7_01_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m8_02_2021 <-  mutate(m8_02_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m9_03_2021 <-  mutate(m9_03_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m10_04_2021 <-  mutate(m10_04_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- m11_05_2021 <-  mutate(m11_05_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))
- 12_06_2021 <-  mutate(m12_06_2021, from_station_id = as.double(from_station_id)
                      ,to_station_id = as.double(to_station_id))

### Stack individual month's data frames into one big data frame
all_trips <- bind_rows(m1_07_2020, m2_08_2020, m3_09_2020, m4_10_2020, m5_11_2020, m6_12_2020, m7_01_2021, m8_02_2021, m9_03_2021, m10_04_2021, m11_05_2021, m12_06_2021)

#======================================================
### Step 3: Clean Up and Add Data to Prepare for Analysis
#======================================================
### Inspect the new table that has been created
### Good to do this again after doing it on the individual files in Excel.
- colnames(all_trips)  #List of column names
- nrow(all_trips)  #How many rows are in data frame?
- dim(all_trips)  #Dimensions of the data frame?
- head(all_trips)  #See the first 6 rows of data frame.  Also tail(qs_raw)
- str(all_trips)  #See list of columns and data types (numeric, character, etc)
- summary(all_trips)  #Statistical summary of data. Mainly for numerics


### There are a few problems we may need to fix:

all_trips %>% group_by(usertype) %>% summarise()
### This yields only the 2 user types our analysis concerns: members and casual riders.
table(all_trips$usertype)
### This shows there are 2529695 members and 1928711 casual riders which equal the total number of observations in the file, 4458406.

(1) The data can only be aggregated at the ride-level, which is too granular. We will want to add some additional columns of data -- such as day, month, year -- that provide additional opportunities to aggregate the data.

### Add columns that list the date, month, day, and year of each ride
 This will allow us to aggregate ride data for each month, day, or year ... before completing these operations we could only aggregate at the ride level.
Check out [more](https://www.statmethods.net/input/dates.html) on date formats in R.

- all_trips$date <- as.Date(all_trips$start_time, origin="1899-12-30") #The default format is yyyy-mm-dd
#Used origin="1899-12-30" since earlier had converted date info with Excel's time format with 37:30:55.
- all_trips$month <- format(as.Date(all_trips$date), "%m")
- all_trips$day <- format(as.Date(all_trips$date), "%d")
- all_trips$year <- format(as.Date(all_trips$date), "%Y")
- all_trips$day_of_week <- format(as.Date(all_trips$date), "%A")

(2) We will want to add a calculated field for length of ride since the 2020Q1 data did not have the "tripduration" column. We will add "ride_length" to the entire dataframe for consistency.
### This was already done in the file from the analysis in Excel after formatting started_at and ended_at with Excel's time format with 37:30:55. I'm doing it again here for comparison to the calcuations in Excel.
###The two columns (ride_length and ride_length_r are the same.
all_trips_v2$ride_length_r <- as.difftime(all_trips_v2$end_time,tz,
                                          units = c("secs))
### Inspect the structure of the columns
str(all_trips)

(3) There are some rides where tripduration shows up as negative, including several hundred rides where Divvy took bikes out of circulation for Quality Control reasons. We will want to delete these rides. (I've previously deleted the rides in Excel where they showed up as ############# in the field prior to loading the individual files in R, and noted this in the changelog. I left the rows in the individual files with actual negative numbers to delete in R.) Will delete these in both ride_length (created in Excel) and ride_length_2, created in R.

### We will create a new version of the dataframe (v2) since data is being removed
all_trips_v2 <- all_trips[!(all_trips$from_station_id == "HQ QR" | all_trips$ride_length<0),]

8,127 rows were deleted.

### Will create another new version of the dataframe (v3) since data is being removed.

all_trips_v3 <- all_trips[!(all_trips$from_station_id == "HQ QR" | all_trips$ride_length_r<0),]

#=====================================
### Step 4: Conduct Descriptive Analysis
#=====================================
### Descriptive analysis on ride_length (all figures in seconds)
- mean(all_trips_v3$ride_length_r, na.rm = TRUE) #straight average (total ride length / rides)
- median(all_trips_v3$ride_length_r, na.rm = TRUE) #midpoint number in the ascending array of ride lengths
- max(all_trips_v3$ride_length_r, na.rm = TRUE) #longest ride
- min(all_trips_v3$ride_length_r, na.rm = TRUE) #shortest ride

### You can condense the four lines above to one line using summary() on the specific attribute

summary(all_trips_v3$ride_length_r, na.rm = TRUE)

### Compare members and casual users
- aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype, FUN = mean)
- aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype, FUN = median)
- aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype, FUN = max)
- aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype, FUN = min)

### See the average ride time by each day for members vs casual users

aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype + all_trips_v3$day_of_week, FUN = mean)

### Notice that the days of the week are out of order. Let's fix that.

all_trips_v3$day_of_week <- ordered(all_trips_v3$day_of_week, levels=c("Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"))

### Now, let's run the average ride time by each day for members vs casual users

aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype + all_trips_v2$day_of_week, FUN = mean)

### Analyze ridership data by type and weekday

all_trips_v3 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>%
  group_by(usertype, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length_r)) %>% 
  arrange(usertype, weekday)

### Let's visualize the number of rides by rider type

all_trips_v3 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(usertype, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length_r)) %>% 
  arrange(usertype, weekday)  %>% 
  ggplot(aes(x = weekday, y = number_of_rides, fill = usertype)) +
  geom_col(position = "dodge")

### Let's create a visualization for average duration

all_trips_v3 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(usertype, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length_r)) %>% 
  arrange(usertype, weekday)  %>% 
  ggplot(aes(x = weekday, y = average_duration, fill = usertype)) +
  geom_col(position = "dodge")

#=================================================
### Step 5: Export Summary File for Further Analysis
#=================================================
### Create a csv file that we can visualize in Excel or Tableau

To export the data as a csv file you can read [more here](https://datatofish.com/export-dataframe-to-csv-in-r/). 

counts <- aggregate(all_trips_v3$ride_length_r ~ all_trips_v3$usertype + all_trips_v3$day_of_week, FUN = mean)
write.csv(counts, file = '/Users/caroladdassi/RProjects/Case_Study_Cyclistics/data/avg_ride_length.csv')

### Save dataframe as .csv file

write.csv(all_trips_v3,'/Users/caroladdassi/RProjects/Case_Study_Cyclistics/data/all_trips_v3.csv')

#=================================================
### Step 6: Further Analysis Continued
#=================================================

### Visualization for the number of roundtrip rides at stations having more than 800 roundtrip rides per year by user type. (The distance between station is 0 and the ride_length is > 0 since we deleted all rows with negative ride_length earlier.)

- all_trips_v3 %>% 
  filter(distance_traveled_mi == 0) %>% 
  group_by(usertype, from_station_name) %>% 
  summarise(number_of_rides = n()) %>% 	
  filter(number_of_rides > 800) %>%
  arrange(-number_of_rides) %>% 
  ggplot(aes(x = number_of_rides, y = from_station_name, fill = usertype)) +
  geom_col(position = "stack") +
  labs(title= "Most Popular Stations for Roundtrip Rides", 
       subtitle = "Roundtrip Rides by Casual Riders and Members \nJuly 2020 to June 2021, Chicago \n(Less than 801 per year not shown.)", 
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Number of roundtrip rides") +
  ylab("Start / End Station") +
  theme(axis.text.y = element_text(size = 6))

### Visualization of the most popular start stations to begin rides (over 10,000 rides/year), including unknown start stations.
- all_trips_v3 %>% 
  group_by(usertype, from_station_name) %>% 
  summarise(number_of_rides = n()) %>% 	
  filter(number_of_rides > 10000) %>% 
  arrange(-number_of_rides, rm.na = TRUE) %>% 
  ggplot(aes(x = from_station_name, y = number_of_rides, fill = usertype)) +
  geom_col(position = "stack")+
  scale_y_continuous(name="Number of Rides", labels = scales::comma) +
  labs(title= "Most Popular Start Stations", 
       subtitle = "Stations With Over 10,000 Rides from July 2020 - June 2021, Chicago, \nUnknown Start Stations Shown",
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Station Names") +
  coord_flip() +
  theme(axis.text.y = element_text(size = 6))

### Visualization of the most popular start stations to begin rides (over 10,000 rides/year), unknown stations omitted.
- all_trips_v3 %>% 
   na_if("") %>% na.omit %>% 
  group_by(usertype, from_station_name) %>% 
  summarise(number_of_rides = n()) %>% 	
  filter(number_of_rides > 10000) %>% 
  arrange(-number_of_rides, rm.na = TRUE) %>% 
  ggplot(aes(x = from_station_name, y = number_of_rides, fill = usertype)) +
  geom_col(position = "stack")+
  scale_y_continuous(name="Number of Rides", labels = scales::comma) +
  labs(title= "Most Popular Start Stations", 
       subtitle = "Stations With Over 10,000 Rides from July 2020 - June 2021, Chicago,\nUnknown Start Stations Omitted",
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Station Names") +
  coord_flip() +
  theme(axis.text.y = element_text(size = 6))

### Visualization of the number of rides by rider type including unknown users
- all_trips_v3 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>%
  group_by(usertype, weekday) %>%
  summarise(number_of_rides = n()) %>%
  arrange(usertype, weekday)  %>%
  ggplot(aes(x = weekday, y = number_of_rides, fill = usertype)) +
  geom_col(position = "dodge")+
  scale_y_continuous(name="Number of Rides", labels = scales::comma) +
  labs(title= "Number of Rides by Type of Rider: Member or Casual", 
       subtitle = "Total Rides from July 2020 - June 2021 per Day, Chicago,    \nIncluding Unknown Users", 
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Day of Week")
  
### Visualization of the number of rides by rider type including unknown users by month
- all_trips_v3 %>% 
  group_by(month, usertype) %>%
  summarise(number_of_rides = n()) %>%
  arrange(usertype, month)  %>%
  ggplot(aes(x = month, y = number_of_rides, fill = usertype)) +
  geom_col(position = "dodge")+
  scale_y_continuous(name="Number of Rides", labels = scales::comma) +
  labs(title= "Number of Rides by Type of Rider: Member or Casual", 
       subtitle = "Total Rides from July 2020 - June 2021 per Month, Chicago, \nIncluding Unknown Users", 
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Month")

### Visualization of the number of rides by rider type exluding unknown users
- all_trips_v3 %>% 
  na_if("") %>% na.omit %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(usertype, day_of_week) %>% 
  summarise(number_of_rides = n()) %>% 
  arrange(usertype, day_of_week)  %>% 
  ggplot(aes(x = day_of_week, y = number_of_rides, fill = usertype)) +
  geom_col(position = "dodge")+
  scale_y_continuous(name="Number of Rides", labels = scales::comma) +
  labs(title= "Number of Rides by Type of Rider: Member or Casual", 
       subtitle = "Total Rides from July 2020 - June 2021 per Day, Chicago, \nExcluding Unknown Users", 
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Day of Week")+
  ylab("Number of Rides")

### Visualization for average duration including unknown users
- all_trips_v3 %>% 
  mutate(weekday = wday(start_time, label = TRUE)) %>% 
  group_by(usertype, weekday) %>% 
  summarise(number_of_rides = n()
            ,average_duration = mean(ride_length_r)) %>% 
  arrange(usertype, weekday)  %>% 
  ggplot(aes(x = weekday, y = average_duration, fill = usertype)) +
  geom_col(position = "dodge") +
  labs(title= "Average Ride Length by Type of Rider: Member or Casual", 
       subtitle = "July 2020 - June 2021 by Day of Week in Seconds, Chicago", 
       caption = "Public data has been made available by Motivate International Inc.") +
  xlab("Day of Week") +
  ylab("Average Ride Duration in Seconds")
  
