# Adding the tables

## Creating table (PostgreSQL workspace)
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
```sql

```
