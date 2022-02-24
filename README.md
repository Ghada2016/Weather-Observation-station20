# Weather-Observation-station20
HackerRank - Weather Observation station20

A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to  decimal places.

Input Format

The STATION table is described as follows:

Station.jpg

where LAT_N is the northern latitude and LONG_W is the western longitude.
https://www.hackerrank.com/challenges/weather-observation-station-20/problem?isFullScreen=true

My Correct Solution :

SELECT cast(ROUND(AVG(LAT_N),4) as numeric(10,4))
FROM
(SELECT *, ROW_NUMBER() OVER(ORDER BY LAT_N DESC) AS LAT_DESC
        , ROW_NUMBER() OVER(ORDER BY LAT_N ASC) AS LAT_ASC
FROM STATION) AS A
WHERE LAT_ASC IN (LAT_DESC, LAT_DESC+1, LAT_DESC-1);
