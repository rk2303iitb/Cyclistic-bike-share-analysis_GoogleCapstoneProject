# Queries for data cleaning and transformation

```sql
Delete FROM year_table
WHERE 
end_lat IS NULL OR
end_lng IS NULL OR
start_station_name IS NULL OR 
start_station_name LIKE ' ' OR
start_station_id IS NULL OR 
start_station_id LIKE ' ' OR
end_station_name IS NULL OR 
end_station_name LIKE ' ' OR
end_station_id IS NULL OR 
end_station_id LIKE ' ';
```
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/5f8b6047-ba50-4cd0-a196-e106f5d3f56e)

```sql
Delete FROM year_table
WHERE 
	Extract (HOUR FROM (ended_at - started_at)) >=24 OR 
	(EXTRACT(HOUR FROM (ended_at - started_at)) * 60 +
  	EXTRACT(MINUTE FROM (ended_at - started_at)) +
  	EXTRACT(SECOND FROM (ended_at - started_at)) / 60) <= 1 ;
```
![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/7aab151e-d19c-4a81-88d5-ecefa1f900e4)

```sql
ALTER TABLE year_table
DROP COLUMN start_station_id, 
DROP COLUMN end_station_id;
```
```sql
ALTER TABLE year_table
ADD month_of_year VARCHAR,
ADD day_of_week VARCHAR,
ADD hour_of_day int,
ADD ride_length TIME;
```
```sql
UPDATE year_table
SET 
  ride_length = ended_at - started_at,
  month_of_year = TO_CHAR(started_at, 'Month'),
  day_of_week = TO_CHAR(started_at, 'Day'),
  hour_of_day = EXTRACT(HOUR FROM started_at);
```
