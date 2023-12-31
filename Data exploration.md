SELECT
COUNT(*) AS count_rows
FROM year_table;

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/e31661eb-8d7a-4666-b113-0c23943cbe19)

SELECT column_name, data_type
FROM INFORMATION_SCHEMA.COLUMNS
WHERE table_name = 'year_table';

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/f9a01b56-641f-4d78-81c0-98b2db4726f9)

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

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/0c2a1f89-9b39-4bc7-b19e-6f7d2b525ab6)

SELECT COUNT(ride_id) - COUNT(DISTINCT ride_id) AS duplicate_rows
FROM year_table;

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/d4c324d7-1ee3-453f-be0a-fda64f9c99b4)

SELECT COUNT(*) AS long_ride
FROM year_table
WHERE Extract (HOUR FROM (ended_at - started_at)) >=24

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/73d2ae98-4bf1-4b3a-843d-f05d45ea884b)

SELECT COUNT(*) AS SHORT_RIDE
FROM YEAR_TABLE
WHERE (
  EXTRACT(HOUR FROM (ended_at - started_at)) * 60 +
  EXTRACT(MINUTE FROM (ended_at - started_at)) +
  EXTRACT(SECOND FROM (ended_at - started_at)) / 60) <= 1;

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/a6c27850-1a88-409b-b103-4752ecff5b0e)


SELECT rideable_type, 
COUNT(rideable_type) AS no_of_rides
FROM year_table
GROUP BY rideable_type;

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/494cb29e-b39a-4550-9c6d-72167c4fd612)

SELECT member_casual, 
COUNT(member_casual) AS rides_taken
FROM year_table
GROUP BY member_casual;

![image](https://github.com/rk2303iitb/Cyclist-bike-share-analysis/assets/155146605/acd548cd-4d4f-4dd7-8686-dd349f9fa02e)


