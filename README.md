# data-engineering-zoomcamp

Question 1. Understanding docker first run

docker run -it --entrypoint bash python:3.12.8
pip --version

Answer: pip 24.3.1

Question 2. Understanding Docker networking and docker-compose

Answer: db:5432

Question 3. Trip Segmentation Count

1. Up to 1 mile

SELECT COUNT(1) FROM public.green_taxi
WHERE trip_distance <= 1.0
AND lpep_pickup_datetime >= '2019-10-01'::DATE
AND lpep_dropoff_datetime < '2019-11-01'::DATE

Answer: 104802

2. In between 1 (exclusive) and 3 miles (inclusive)

SELECT COUNT(1) FROM public.green_taxi
WHERE trip_distance > 1.0 AND 
trip_distance <= 3.0
AND lpep_pickup_datetime >= '2019-10-01'::DATE
AND lpep_dropoff_datetime < '2019-11-01'::DATE

Answer: 198924

3. In between 3 (exclusive) and 7 miles (inclusive)

SELECT COUNT(1) FROM public.green_taxi
WHERE trip_distance > 7 AND 
trip_distance <= 10
AND lpep_pickup_datetime >= '2019-10-01'::DATE
AND lpep_dropoff_datetime < '2019-11-01'::DATE

Answer: 109603

4. In between 7 (exclusive) and 10 miles (inclusive)
   
SELECT COUNT(1) FROM public.green_taxi
WHERE trip_distance > 7 AND 
trip_distance <= 10
AND lpep_pickup_datetime >= '2019-10-01'::DATE
AND lpep_dropoff_datetime < '2019-11-01'::DATE

Answer: 27678

5. Over 10 miles

SELECT COUNT(1) FROM public.green_taxi
WHERE trip_distance >= 10
AND lpep_pickup_datetime >= '2019-10-01'::DATE
AND lpep_dropoff_datetime < '2019-11-01'::DATE

Answer: 35281

Question 4. Longest trip for each day

SELECT CAST(lpep_dropoff_datetime AS DATE) AS "day", MAX(trip_distance)
FROM green_taxi
GROUP BY CAST(lpep_dropoff_datetime AS DATE)
ORDER BY 2 DESC

Answer: 2019-10-11
