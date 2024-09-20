## Scenario
Singapore’s URA and HDB is monitoring the rise in HDB flat resale prices over the past few years, and is understandably concerned that some units are being priced out for a lot of buyers. 
They also are about to launch the HDB Resale Portal, which will allow HDB unit owners to list their flats on their own.

We - **JAKS Pte Ltd** - are a specialist consultant firm and have been asked by URA and HDB to to help them identify the factors and levers affecting a HDB unit’s price appreciation. 
This will help to:


1. Offer HDB unit owners pricing suggestions on the HDB Resale Portal


2. Plan for future developments as well as identify HDB estates for renewal and refurbishment plans in the future.

## Problem Statement
Based on given historical data of HDB resale prices and conditions prevalent at the time of resale, identify and present a data science model, which can accurately predict resale prices for HDB units, given the same criteria.

## Project Summary
As part of the dataset analysis, we performed the following tasks in order:

**1. Basic Initial Data Analysis**:
The training dataset is quite large and extensive - with over 150K records, and over 70+ columns.
Our target variable was resale_price - i.e. predict the resale value of a HDB unit, using historical data.

**2. Baseline Model and EDA**: We established a Baseline Linear Regression model with just one feature (_floor_area_sqm_), and got R2 = 0.431

**3. Feature Categorization**:
To manage and select features, we identified a few categories and bucketed the features accordingly:
### HDB Resale Dataset Categories

|Transaction Details|Location Details|HDB Unit|HDB Block Utilities|HDB Units sold/rented|Nearby Amenities|Transportation|Education|
|-|-|-|-|-|-|-|-|
| Tranc_YearMonth|town|flat_type|residential|1room_sold|Mall_Nearest_Distance| mrt_nearest_distance| pri_sch_nearest_distance|
| Tranc_Year| block| flat_model| commercial| 2room_sold| Mall_Within_500m| mrt_name| pri_sch_name|
| Tranc_Month| street_name| storey_range| market_hawker| 3room_sold| Mall_Within_1km| bus_interchange| vacancy|
|resale_price| address| floor_area_sqm| multistorey_carpark| 4room_sold| Mall_Within_2km| mrt_interchange| pri_sch_affiliation|
|| postal| floor_area_sqft| precinct_pavilion| 5room_sold| Hawker_Nearest_Distance| mrt_latitude| pri_sch_latitude|
|| Latitude| full_flat_type| total_dwelling_units| exec_sold| Hawker_Within_500m| mrt_longitude| pri_sch_longitude|
|| Longitude| lease_commence_date|| multigen_sold| Hawker_Within_1km| bus_stop_nearest_distance | sec_sch_nearest_dist|
|| planning_area| hdb_age|| studio_apartment_sold| Hawker_Within_2km| bus_stop_name| sec_sch_name|
||| max_floor_lvl|| 1room_rental| hawker_food_stalls| bus_stop_latitude | cutoff_point|
||| year_completed|| 2room_rental| hawker_market_stalls| bus_stop_longitude| affiliation|
||| mid_storey|| 3room_rental||| sec_sch_latitude|
||| lower|| other_room_rental||| sec_sch_longitude|
||| upper||||||
||| mid||||||

To select relevant features for the data modelling process, we tried a different view on the problem statement, taking a home buyer's perspective, and chose the features accordingly.

**4. Data Modelling**:
We selected multiple features from the categories above - and used Linear Regression and then Regularization thereafter.


|Models|R2|RMSE|
|-|-|-|
|Baseline|0.43|107,444.37|
|Linear Regression|0.88|48,515.28|
|Lasso|0.88|48,516.65|
|Ridge|0.88|48,516.37|
|ElasticNet|0.88|48,515.31|

Of these, the 'vanilla' Linear Regression model performed the best at an R2 of 0.883 and RMSE of SGD 48,5155.28

**5. Kaggle Prediction**:

## Conclusion and Recommendations

We were able to establish and test a data science model - Linear Regression - and use it to predict the values for the Kaggle dataset.

From a business standpoint, we recommend

1. Inclusion of polyclinic and health-related amenities
2. Account for change in population growth across planning areas and towns as well as influx of new residents
3. Factor in economic conditions and interest rates as data points
