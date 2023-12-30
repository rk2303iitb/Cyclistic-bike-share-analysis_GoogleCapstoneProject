# Combining the tables

## Creating tables (PostgreSQL workspace)
- Creating first table for December with variables and its format
```sql
CREATE TABLE "202212-divvy" (
    ride_id VARCHAR(255),
    rideable_type TEXT,
    started_at TIMESTAMP,
    ended_at TIMESTAMP,
    start_station_name TEXT,
    start_station_id TEXT,
    end_station_name TEXT,
    end_station_id TEXT,
    start_lat DOUBLE PRECISION,
    start_lng DOUBLE PRECISION,
    end_lat DOUBLE PRECISION,
    end_lng DOUBLE PRECISION,
    member_casual TEXT
);
```
- Creating other 11 tables with same schema as December table
```sql
CREATE TABLE "202301-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202302-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202303-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202304-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202305-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202306-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202307-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202308-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202309-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202310-divvy" (LIKE "202212-divvy" INCLUDING ALL);
CREATE TABLE "202311-divvy" (LIKE "202212-divvy" INCLUDING ALL);
```
## Importing data from .csv files

- S1: Under schema, select table and then right click to find import option as shown in following image
  ![s2](https://github.com/rk2303iitb/Capstone/assets/155146605/f6c7e622-13de-4d8e-8ee2-3d0ec91edc84)

- S2: Selct the file path of downloaded .csv file to be imported as shown following
  ![s3](https://github.com/rk2303iitb/Capstone/assets/155146605/9d6b440d-b434-47a5-aa9e-d90e3e66516b)

- S3: Tuen on 'header' under option to let pgsql know that .csv file is containing headers as shownn in following image
  ![s4](https://github.com/rk2303iitb/Capstone/assets/155146605/2207f901-a34b-4074-85f2-676eb20568bd) 

## Collate all the tables into one master table as "year_table"
```sql
CREATE TABLE IF NOT EXISTS "year_table" AS ( 
	SELECT * FROM "202212-divvy" 
	UNION ALL 
	SELECT * FROM "202301-divvy" 
	UNION ALL 
	SELECT * FROM "202302-divvy" 
	UNION ALL
	SELECT * FROM "202303-divvy" 
	UNION ALL 
	SELECT * FROM "202304-divvy" 
	UNION ALL 
	SELECT * FROM "202305-divvy" 
	UNION ALL 
	SELECT * FROM "202306-divvy" 
	UNION ALL 
	SELECT * FROM "202307-divvy" 
	UNION ALL 
	SELECT * FROM "202308-divvy" 
	UNION ALL 
	SELECT * FROM "202309-divvy" 
	UNION ALL 
	SELECT * FROM "202310-divvy" 
	UNION ALL 
	SELECT * FROM "202311-divvy" 
);
```
