# Studying-Analytics
Cyclistic Bike Share Case Study
 
## Introduction to the project
This project was picked as capstone for the **Google Data Analytics Professional Certificate**. It aims to showcase the skills developed in the process of data analytics: ask, prepare, process, analyze, share and act.

# SCENARIO

I am a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share company in Chicago. The marketing director believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve our recommendations, so they must be backed up with compelling data insights and professional data visualizations.

Cyclistic is a bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand
tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use bikes to commute to work each day.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. The marketing director believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, she believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

The goal is to design marketing strategies to convert casual riders into annual members. In order to do that, however, the team needs to better understand how
annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics.

## 1) Ask

Three questions will guide the future marketing program:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?

I have been assigned the first question: <ins>How do annual members and casual riders use Cyclistic bikes differently?</ins>

I used Cyclistic’s historical trip data to analyze and identify trends for the last 12 months. Csv files for each month from November 2023 to October 2024 refer to the most recent data pulled from Cyclistic usage.

Finally, I have to present my findings to Cyclistic executive team. This notoriously detail-oriented executive team will decide whether to approve the recommended marketing program. This team takes decisions at a very high level and will be interested in headlines. I can disclose details about my analysis in the appendix after the presentation.

## 2) Prepare

**Data Source:** [divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html) <br>
[Note: Data has been made available by Motivate International Inc. under this [<ins>license</ins>](https://www.divvybikes.com/data-license-agreement).]

A download of the original data sets used for analysis has been saved locally for future reference.

The server holds data from 2013 to October 2024. There’s a data set for the year 2013, and from 2014 to 2020 Q1 a data set for each quarter of every year. From April 2020 to  October 2024 there’s a data set for each month.

For the present analysis, I took into consideration data sets from November 2023 to October 2024.

For the purpose of this project, data is considered to be internal and it is structured in 13 fields as following:


| **No.**|  **Variable**       |  **Description**                                        |
|--------|------------------   | --------------------------------------------------------|
| 1      | ride_id             | Unique ID assigned to each ride                         |
| 2      | rideable_type       | classic, docked, or electric                            |
| 3      | started_at          | Date and time at the start of trip                      |
| 4      | ended_at            | Date and time at the end of trip                        |
| 5      | start_station_name  | Name of the station where the ride journey started from |
| 6      | start_station_id    | ID of the station where the ride journey started from   |
| 7      | end_station_name    | Name of the station where the ride trip ended at        |
| 8      | end_station_id      | ID of the station where the ride trip ended at          |
| 9      | start_lat           | Latitude of starting station                            |
| 10     | start_lng           | Longitude of starting station                           |
| 11     | end_lat             | Latitude of ending station                              |
| 12     | end_lng             | Longitude of ending station                             |                            
| 13     | member_casual       | Type of membership of each rider                        |














