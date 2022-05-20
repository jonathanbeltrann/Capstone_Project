# Capstone_Project

NYC Yellow Taxi Data
Jonathan Beltran


Rhe NYC TLC Trip Record Data includes trip records include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts. The data ranged from 2009-2022 and could be found at the following website: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page


### Contents:
- [Problem Statement](#Problem-Statement)
- [Summary](#Summary)
- [Methodology](#Methodology)
- [Findings and Observations](#Findings-and-Observations)
- [Conclusions](#Conclusions) and [Next Steps](#Next-Steps)



### Data Dictionary
| Feature | Description |
|---|---|
| VendorID | A code indicating the TPEP provider that provided the record<br><br>1= Creative Mobile Technologies, LLC; 2= VeriFone Inc. |
| tpep_pickup_datetime  | The date and time when the meter was engaged. |
| tpep_dropoff_datetime | The date and time when the meter was disengaged. |
| Passenger_count | The number of passengers in the vehicle.<br>This is a driver-entered value |
| Trip_distance | The elapsed trip distance in miles reported by the taximeter. |
| PULocationID | TLC Taxi Zone in which the taximeter was engaged |
| DOLocationID | TLC Taxi Zone in which the taximeter was disengaged |
| RateCodeID | The final rate code in effect at the end of the trip.<br>1= Standard rate<br>2=JFK<br>3=Newark<br>4=Nassau or Westchester<br>5=Negotiated fare<br>6=Group ride |
| Store_and_fwd_flag | This flag indicates whether the trip record was held in vehicle<br>memory before sending to the vendor, aka “store and forward,”<br>because the vehicle did not have a connection to the server.<br>Y= store and forward trip<br>N= not a store and forward trip |
| Payment_type | A numeric code signifying how the passenger paid for the trip.<br>1= Credit card<br>2= Cash<br>3= No charge<br>4= Dispute<br>5= Unknown<br>6= Voided trip |
| Fare_amount | The time-and-distance fare calculated by the meter |
| Extra | Miscellaneous extras and surcharges. Currently, this only includes<br>the $0.50 and $1 rush hour and overnight charges |
| MTA_tax | $0.50 MTA tax that is automatically triggered based on the metered<br>rate in use. |
| Improvement_surcharge | $0.30 improvement surcharge assessed trips at the flag drop. The<br>improvement surcharge began being levied in 2015. |
| Tip_amount | Tip amount – This field is automatically populated for credit card<br>tips. Cash tips are not included. |
| Tolls_amount | Total amount of all tolls paid in trip. |
| Total_amount | The total amount charged to passengers. Does not include cash tips. |
| Congestion_Surcharge | Total amount collected in trip for NYS congestion surcharge. |
| Airport_fee | $1.25 for pick up only at LaGuardia and John F. Kennedy Airports |


### Problem Statement
Using historical data, how can we forecast passenger counts, fare amounts from rides and distance traveled?
Additionally, where are the top pick-up zones historically?



### Summary
I collected data from the NYC TLC from 2019 - 2020, and as I mentioned before I took a look at passenger counts, fare amounts from rides and distance traveled. For these features, I was trying to determine with what accuracy I could forecast the amounts of passengers, fares, and distances.



### Methodology
In order to complete the process I cleaned the data that I beleived to be necessary to improve my model. I wanted to first analyze the largest correlations and see how those features had an effect on fatalities. I did this by using a variety of different data vizualization techniques. The eda process involved me dropping rows that harmed the overall data set. 

>* All files were segregated by month for every year
>* Shapefiles were provided to help visualize taxi zones by borough
>* Data included pickups that happened outside the city but dropped off in the city and vice versa
>* Binned the data by Borough

Feature Engineering:
>* Binned time of day: Morning, Afternoon, Evening, Late Night
>* Extracted hour and month data using datetime on pickup_time column
>* Got rid of any rides with trip distance over 100 miles
>* Got rid of any rows where there were more than 6 passengers as they were outliers
>* Only looked at Brooklyn, Bronx and Queens

### Findings and Observations
Since I chose 2020 as one of the years to analyze, I saw a big decline for all features due to the global COVID-19 pandemic. Trying to see seasonality was not possible as regular rider behaviour.

Additionally, Boroughs like the Bronx and Brookly, we saw steady declines in ridership even long before the pandemic.

### Conclusions and Next Steps

>* All RMSEs were calculated using differential data rather than the actual values of the data, would need to undifferentiated again and rerun predictions
>* Models performed badly due to the non seasonality of the data since the pandemic hit NYC badly in 2020. Could use past years where ride behavior are not externally affected
>* Use other models to predict number of passengers by zones and plotting using shapely or other geographic visualizations to compare
>* I could Add weather data by the hour to see how that affects behaviour in the data
>* Doing a market share analysis against rideshare apps could also add another interesting dimesnion to this project
