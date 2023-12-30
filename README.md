# Cyclist Bike Share Analysis
- Project Referece: [Google Data Analytics Capstone](https://www.coursera.org/learn/google-data-analytics-capstone)

## Introduction
- As a junior data analyst at a fictional bike share company, Cyclistic, I have to utilise data analysis to to help management to convert casual riders into annual subscription based members
- Marketing team will use my insights to run campaigns and hence the analysis must be backed by compellng insights
- Broad steps followed in the process: Ask, Prepare, Process, Analyse, Share and Act
- Tools used: PostgreSQL, Tableau.

### Background of Cyclistic(company)
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships.Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable
than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno(director of marketing) believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

## Ask
This step requires us to understand, what are the **business questions** that needs to be answered and who are the **key stakeholders**

Three questions that will guide the future marketing program:
  1. How do annual members and casual riders use Cyclistic bikes differently?
  2. Why would casual riders buy Cyclistic annual memberships?
  3. How can Cyclistic use digital media to influence casual riders to become members?

Moreno has assigned me(junior analyst) the first question.

## Prepare
This step generally requires us to go through following steps-
  1. Find and download required data and store it appropriately
  2. Identify how it’s organized
  3. Sort and filter the data.
  4. Determine the credibility of the data.

### Data Source
- The data used is historical trip data of Cyclistic from: [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html)
- [Licensing Agrrement](https://ride.divvybikes.com/data-license-agreement) to use data
- NOTE: Rider's personally identifiable info can't be used to prevent their privacy

### Data description
- Downloaded files in .zip fomrat was extracted to finally have 12 months of data in 12 .csv files each containing data of particu;ar month
- Name of .csv files in format YYYYMM-divvy-tripdata
- Downloaded data's timeframe: Dec 2022- Nov2023 (Past 1 year)
- Each file have same column format with self explainable column names being ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.

### Creating database
- S1: Database file created manually in PostgreSQL as following
  ![Screenshot 2023-12-30 150004](https://github.com/rk2303iitb/Capstone/assets/155146605/e870288d-b00f-4292-bed8-d29b5dd7d207)
- S2: All the tables are added to database

  SQL query: [Link](https://github.com/rk2303iitb/Capstone/blob/main/Database_creation.md#adding-the-tables)
  




