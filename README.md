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
- 
  ![Screenshot 2023-12-30 150004](https://github.com/rk2303iitb/Capstone/assets/155146605/e870288d-b00f-4292-bed8-d29b5dd7d207)
- S2: Tables are created in database with names in "YYYYMM-divvy" format 
- S3: Data from downloaded .csv is imported to tables of database
- S4: All the 12 tables are combined into one master table "year_table"

  [Detail SQL query and explanations for above steps](https://github.com/rk2303iitb/Capstone/blob/main/Database_creation.md#adding-the-tables)

## Process
This step requires 
  1. Check the data for errors.
  2. Choose your tools.
  3. Transform the data so you can work with it effectively.
  4. Document the cleaning process

### Exploring the combined table

[SQL queries for data exploration](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/blob/main/Data%20exploration.md#queries-for-data-exploration)

#### Results:-

- Data type

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/f9a01b56-641f-4d78-81c0-98b2db4726f9)

- Total rows
  
    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/e31661eb-8d7a-4666-b113-0c23943cbe19)

- Total null or blank values in each column

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/0c2a1f89-9b39-4bc7-b19e-6f7d2b525ab6)

- Total duplicate rows in table(checked whether unique ride_id is repeated)

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/d4c324d7-1ee3-453f-be0a-fda64f9c99b4)

- Rides longer than a day

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/73d2ae98-4bf1-4b3a-843d-f05d45ea884b)

- Rides shorter than a minute

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/a6c27850-1a88-409b-b103-4752ecff5b0e)

- Distinctinct rideable_type and number of rides on them

    ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/494cb29e-b39a-4550-9c6d-72167c4fd612)

- Number of casual riders and member riders

     ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/acd548cd-4d4f-4dd7-8686-dd349f9fa02e)
  
### Data cleaning and transformation

#### [SQL queries for cleaning and transformation](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/edit/main/data%20cleaning%20and%20transformation.md#queries-for-data-cleaning-and-transformation)

#### Steps taken:-
  1. Removing rows with null or blank values
  2. Removing outliers to avoid any bias (>24 hours ride and <1 mins ride)
  3. Removing columns of station_id as they are not useful in analysis
  4. Adding new columns-
       - month
       - day_of_week
       - start_hour_of_day
       - ride_length
    
  #### Result of data cleaning and transformation
  
  - Final number of rows after cleaning
    
      ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/fb938690-e487-4c4b-96a3-9c10658f8466)

    So, total 1465681 rows removed in data cleaning process. 

  - New columns added
    
      ![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/11b0491c-f3a7-4ca9-a369-282a892b6833)

## Analyse and Share
  
- Data has been cleaned and transformed into a table which can be analysed comfortably
- The 'year_table' after all the updates is downloaded in .csv format and uploaded to Tableau for further analysis
- [Link to Tableau Analysis](https://public.tableau.com/shared/W7F2ZM5J4?:display_count=n&:origin=viz_share_link)

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/c2933db2-a846-4208-97f6-a972af90b67d)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/a4096fca-fda1-4fd1-8094-0752f08013ff)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/578f193a-c7cf-4f16-97af-8bc9cfbcf3ea)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/63939c96-53ee-48f1-89c1-329d557c11d7)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/a5faecd1-5e24-4c67-bce1-5bc8a37d9a84)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/f5dd5fc4-392b-4480-a4dd-40930ae70ab1)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/afc53996-beb3-4541-95ec-a90c083873f4)
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/9a900203-a5e1-4c4c-b1ad-47a3c05cf2c4)

### Insights
  1. **Rideable type**: Most used bike is classic bike followed by the electric bike, docked bikes are used the least and by only casual riders.
  2. **Week days vs weekends behaviour**: Casual riders make more journeys on the weekends while members show a decline over the weekend in contrast to the other days of the week. It can be assumed that members are using bike for work commutation while casual riders for recreational or other purposes.
  3. **Month/Season based behaviour**: Both casual and members have similar behavior, with more trips in the spring and summer and fewer in the winter(Nov-Feb).
  4. **Peak hours of the day**: Members are more frequently using bikes around 8AM and 6PM which are office hours further confirming our assunption in point 3 that members are mostly using bike for work/office related commutation, For casual riders no such specific peak, frequency consistently increases from morning to evening.
  5. **Stations used**: Most frequent staions for member riders are near universities, commercial/office places, residential areas while for casual riders are near parks, museum, beaches and other leisure areas.
  6. **Ride duration**: Average ride duration for casual rider is nearly double compared to member riders. However, average ride duraion for members remains more or less same throughout the year while casual rider's ride duration peaks during sprin and ummer on weekends.

## Recommendations to convert casual riders into members

- Make regular membership discount to casual riders, especially from June to August. Start campaigns from early spring.

- Promotions during weekends to reach out casual riders.

- Provide and promote additional perks for having a Cyclistic membership account, such as holding a membership only events and prizes.

- Collaborate with leisure activity based businesses providing museum passes, movie ticket discounts etc. with annual membership to attract casual riders

- Run promotions at the top 5 stations that casual riders often use.

- Increase the bikes’ renting price for casual riders during the weekends, especially electic bikes to push them to chose membership.
