# Module 2 homework

1. Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)? <br>
I went to Google Storage Bucket and see the file size there.

2. What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution? <br>
green_tripdata_2020-04.csv

3. How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?<br>
```
SELECT count(*) FROM `dtc-de-course-2026.zoomcamp2.yellow_tripdata` 
WHERE filename like 'yellow_tripdata_2020%'
LIMIT 1000
```

4. How many rows are there for the Green Taxi data for all CSV files in the year 2020?<br>
```
SELECT count(*) FROM `dtc-de-course-2026.zoomcamp2.green_tripdata` 
WHERE filename like 'green_tripdata_2020%'
LIMIT 1000
```

5. How many rows are there for the Yellow Taxi data for the March 2021 CSV file?<br>
```
SELECT count(*) FROM `dtc-de-course-2026.zoomcamp2.yellow_tripdata` 
WHERE filename like 'yellow_tripdata_2021_03%'
LIMIT 1000
```

6. How would you configure the timezone to New York in a Schedule trigger?
I googled the 'Kestra timezone schedule trigger' and found the answer. Add a timezone property set to America/New_York in the Schedule trigger configuration
