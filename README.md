# DE-zoomcamp-homework-module-1
1. docker run -it \
    --rm \
    --entrypoint=bash \
    python:3.13

   After you are in the container, type: pip --version

2. 
    pgadmin needs to connect to "db" as a hostname, which is the service name of postgres
    port is 5432

Prepare Data: (a) use jupyter notebook to load data into Postgres.
(b) run postgres and pgadmin in the same network

3.
    select count(*)
    from public."green_tripdata_2025-11"
    where lpep_pickup_datetime >= '2025-11-01' 
	    and lpep_pickup_datetime < '2025-12-01'
	    and trip_distance <= 1
4. SELECT date(lpep_pickup_datetime)
    from public."green_tripdata_2025-11"
    where  trip_distance = (SELECT MAX(trip_distance) from public."green_tripdata_2025-11"
                            where trip_distance < 100)
5. SELECT "Zone", SUM(total_amount)
    from public."green_tripdata_2025-11" tx 
        LEFT JOIN public.taxi_zone_lookup lkp ON tx."PULocationID" = lkp."LocationID"
    GROUP BY "Zone"
    ORDER BY SUM(total_amount) desc
    LIMIT 1
6. SELECT tip_amount, total_amount, lkp."Zone" as "PU Zone", lkp2."Zone" as "DO Zone"
from public."green_tripdata_2025-11" tx 
LEFT JOIN public.taxi_zone_lookup lkp ON tx."PULocationID" = lkp."LocationID"
LEFT JOIN public.taxi_zone_lookup lkp2 ON tx."DOLocationID" = lkp2."LocationID"
WHERE lpep_pickup_datetime >= '2025-11-01' 
	and lpep_pickup_datetime < '2025-12-01'
	and lkp."Zone" = 'East Harlem North'
ORDER BY tip_amount DESC
LIMIT 1
