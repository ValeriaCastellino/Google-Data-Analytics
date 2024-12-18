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

## :muscle: 2) Prepare

**Data Source:** [divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html) <br>
[Note: Data has been made available by Motivate International Inc. under this [<ins>license</ins>](https://www.divvybikes.com/data-license-agreement).]

A download of the original data sets used for analysis has been saved locally for future reference.

The server holds data from 2013 to October 2024. There’s a data set for the year 2013, and from 2014 to 2020 Q1 a data set for each quarter of every year. From April 2020 to  October 2024 there’s a data set for each month.

For the present analysis, I took into consideration data sets from November 2023 to October 2024.

For the purpose of this project, data is considered to be internal and it is structured in 13 fields as following:

<details>
<summary>Data description</summary>


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

</details>


<details>
<summary>Data Schema</summary>


| **Field**           | Type       |
|---------------------|------------|
| ride_id             | STRING     |
| rideable_typeq      | STRING     |
| started_at          | TIMESTAMP  |
| ended_at            | TIMESTAMP  |
| start_station_name  | STRING     |
| start_station_id    | STRING     |
| end_station_name    | STRING     |
| end_station_id      | STRING     |
| start_lat           | FLOAT      |
| start_long          | FLOAT      |
| end_lat             | FLOAT      |
| end_long            | FLOAT      |
| member_casual       | STRING     |

</details>

Riders' personal information was made unavailable for this analysis.

Because the datasets used for this analysis were large, I used SQL to explore and clean the data. The environment was Google Big Query.

Each table was imported into the Cyclistic dataset following the name convention: users_yearmonth (e.i: users_202311).

I merged the 12 tables into one, with a total of 6,012,003 records, of which 532,455 records resulted in having NULL values for the start and end stations.

## :rocket: 3) Process

The dataset counts more than  6,012,003 entries so I pick SQL to conduct my analysis on it.

I chose Tableau for the visual rendering.

Checked that data replication did not compromise data integrity: the sum of each of the 12 datasets matches the total entries for the 12 months from 11 2023 to October 2024.

Data for the end station is largely missing but we have 1,083,523 null records about the start stations. Considering that our population is 5,788,839 distinct journeys, a sample of 4,705,316 records can lead to a 0.03% margin of error.

Before analyzing the data, the dataset was cleaned by:

- Checking for null values in the ride_id, rideable_type, and member_casual columns and none was found;
- Removing the trips with null values in start and end stations;
- Removing duplicate values (223,164 records were removed);
- Testing data for consistency: date format, spelling mistakes, extra spaces.


I had been keeping track of the cleaning process on a change log.

I saved a table which contains distinct ride_ids, that hold no null values for start and end stations. The table contains 4,159,741 records and was named users_analysis_cleandata.

From this dataset, I removed outliers (trips with a duration of less than 1 minute, or more than a day) and created three columns: trip duration in minutes, month and day of the week.

The final tab I worked on, was of 4,045,952 records and 16 fields:

<details>
<summary>Data Schema</summary>


| **Field**           | Type       |
|---------------------|------------|
| ride_id             | STRING     |
| rideable_typeq      | STRING     |
| started_at          | TIMESTAMP  |
| ended_at            | TIMESTAMP  |
| trip_duration_minute| INTEGER    |
| month               | STRING     |
| day_of_week         | STRING     |
| start_station_name  | STRING     |
| start_station_id    | STRING     |
| end_station_name    | STRING     |
| end_station_id      | STRING     |
| start_lat           | FLOAT      |
| start_long          | FLOAT      |
| end_lat             | FLOAT      |
| end_long            | FLOAT      |
| member_casual       | STRING     |

</details>

## :brain: 4) Analysis

The business question to answer to was: **How do annual members and casual riders use Cyclistic bikes differently?** 

I sorted and filtered data for analysis in order to identify trends and patterns in how casual riders and members use Cyclistic’s service. The results for each query was saved and imported as .csv file on Tableau to be represented and shared.

**Do the casual riders ride as much as members?**

Our dataset counts 1483393 casuals' rides against 2562559 members' rides.


![rides_per_cust_type](https://github.com/user-attachments/assets/d9034d53-a3d9-4b22-b918-9ac6ee4396bc)


**What is the favorite rideable type for both,casual riders and members?**

Both casual riders and members prefer classic bikes(954714 and 1696622)over electric bikes (503854 and 844887). The less favorite in both cases are electric scooters (24825 and 21050).


![favorite_rideable](https://github.com/user-attachments/assets/f7f2fcd6-307c-46fd-8c31-9faa63aff3c1)


**What is the average trip duration for casual riders and members?**

Casual riders rent a bike for longer than members (24 minutes against 12).

![trip_duration](https://github.com/user-attachments/assets/c8360e01-a5a8-4bb5-9bc8-5eddb171ae82)


**Which months are the favorite for casual and members to ride?**

Casual riders prefer to ride in July and August, when less favorite months seem to be December and February. Members dislike December and February the most too, but they prefer September and August for their rides.


![monthly_trips](https://github.com/user-attachments/assets/556b4ed2-4a12-43b9-a77e-4806e3b01924)


**What day of the week are casual riders and members most keen to a ride?**

Casual riders need a bike especially on Saturday and Sunday (which suggest a leisure consume, against commuting), when members ride the most on Wednesdays and Thursday. Casual rides less favorite days for a ride are Tuesday and Monday. Members don't ride on Sunday and Saturday.

![trips_day_of_week](https://github.com/user-attachments/assets/bf5b8366-0f75-440b-aed7-7fa1b504fda0)


**Are there favorite hours for a ride?**

Casual riders likely rent a bike in the afternoon hours. For members the use of bikes is spread over the all day.

![trips_x_hour](https://github.com/user-attachments/assets/635ea11e-9106-40dc-b8dd-30e7d039891c)


**How rides distribute over the week?**


![trips_distribution_x_hour_over_week](https://github.com/user-attachments/assets/359a2a83-c855-4fe5-8edc-595ca3407f21)


## 👀 5) Share

The present study on Cyclistics users will be used to address the marketing strategy. The goal is to convert casual riders into members.

To facilitate the marketing director and the other stakeholders, I have summarized all the insight into a dashboard

![cyclistics_user_analysis_dashboard](https://github.com/user-attachments/assets/dbb93c0f-fa04-4281-8b42-59d0f913f0c6)

The present analysis confirms the trends of previous years.

Casual users requested less rides but the ride for longer than members.
As expected, rides went up in number over the good season from April to October. Although the best months for a ride seem to be July and August for casual members.

The analysis confirms that casual riders still use Cyclistic for leisure rather than commuting.

Both, casual riders and members, mostly need a ride in the peak hours of the working days. The distribution looks more uniform in the weekend, when central hours of the day are a good moment for a ride.


## :fist_right: 6) Act

According to the findings of present analysis a campaign addressed to casual members might leverage on their specific use of the service.

A special price may be reserved for weekends, offering a by minute submission.

For example, casual riders might be tempted to submit the service by a low subscription fee and a different amount corresponding to their needs of minutes riding per week/month.

A marketing campaign should start in April.







