# Queries for data exploration

## Number of rows
```sql
SELECT
COUNT(*) AS count_rows
FROM year_table;
```

## Columns ans type of data in each column
```sql
SELECT column_name, data_type
FROM INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'year_table';
```

## Number of null or blank values in each column

Note: Only text value can have blank space ' ', not data types like timestamp
```sql
SELECT 'ride_id' AS column_name, 
       COUNT(*) FILTER (WHERE ride_id IS NULL OR ride_id LIKE ' ') AS total_null_or_blank
FROM year_table
UNION ALL 
SELECT 'rideable_type', COUNT(*) FILTER (WHERE rideable_type IS NULL OR rideable_type LIKE ' ') FROM year_table
UNION ALL 
SELECT 'started_at', COUNT(*) FILTER (WHERE started_at IS NULL) FROM year_table
UNION ALL 
SELECT 'ended_at', COUNT(*) FILTER (WHERE ended_at IS NULL) FROM year_table
UNION ALL 
SELECT 'start_station_name', COUNT(*) FILTER (WHERE start_station_name IS NULL OR start_station_name LIKE ' ') FROM year_table
UNION ALL 
SELECT 'start_station_id', COUNT(*) FILTER (WHERE start_station_id IS NULL OR start_station_id LIKE ' ') FROM year_table
UNION ALL  
SELECT 'end_station_name', COUNT(*) FILTER (WHERE end_station_name IS NULL OR end_station_name LIKE ' ') FROM year_table
UNION ALL 
SELECT 'end_station_id', COUNT(*) FILTER (WHERE end_station_id IS NULL OR end_station_id LIKE ' ') FROM year_table
UNION ALL 
SELECT 'start_lat', COUNT(*) FILTER (WHERE start_lat IS NULL) FROM year_table
UNION ALL 
SELECT 'start_lng', COUNT(*) FILTER (WHERE start_lng IS NULL) FROM year_table
UNION ALL 
SELECT 'end_lat', COUNT(*) FILTER (WHERE end_lat IS NULL) FROM year_table
UNION ALL 
SELECT 'end_lng', COUNT(*) FILTER (WHERE end_lng IS NULL) FROM year_table
UNION ALL 
SELECT 'member_casual', COUNT(*) FILTER (WHERE member_casual IS NULL OR member_casual LIKE ' ') FROM year_table;
```

## Total duplicate rows

Checked repitition of ride_id
```sql
SELECT COUNT(ride_id) - COUNT(DISTINCT ride_id) AS duplicate_rows
FROM year_table;
```

## Number of long rides(more than 24 hours)
```sql
SELECT COUNT(*) AS long_ride
FROM year_table
WHERE Extract (HOUR FROM (ended_at - started_at)) >=24
```

## Number of short rides(less than 1 minute)
```sql
SELECT COUNT(*) AS SHORT_RIDE
FROM YEAR_TABLE
WHERE (
  EXTRACT(HOUR FROM (ended_at - started_at)) * 60 +
  EXTRACT(MINUTE FROM (ended_at - started_at)) +
  EXTRACT(SECOND FROM (ended_at - started_at)) / 60) <= 1;
```

## Types of bikes and their ride numbers
```sql
SELECT rideable_type, 
COUNT(rideable_type) AS no_of_rides
FROM year_table
GROUP BY rideable_type;
```

## Total casual ans member riders
```sql
SELECT member_casual, 
COUNT(member_casual) AS rides_taken
FROM year_table
GROUP BY member_casual;
```

