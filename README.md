# Surf's Up
Module 9: Jupyter Notebook &amp; SQLite &amp; VS Code: Surf's Up with Advanced Data Storage and Retrieval
## Overview of the statistical analysis
The purpose of the original analysis of the module was to analyze trends in weather data including temperatures and precipitation in Hawaii for W. Avy's ice cream and surfing supply shop. This was done using jupyter notebooks and SQLite queries into a database for weather data according to date. An additional analysis was asked which required temperature data for the months of June and December in Oahu, in order to determine if the surf and ice cream shop business was sustainable year-round. 
## Results
Using filtered queries to find temperatures for specific months, the following code was used to query the data. This was added to a list which was further converted to a data frame to be easier to analyze. 

    results = session.query(Measurement.date, Measurement.tobs).filter(extract('month', Measurement.date)==6 ).all()
    
The following screenshots are the summary statistics of the created dataframes.

### June
<img width="132" alt="June" src="https://user-images.githubusercontent.com/87828174/138989007-e242c801-95ff-48db-ab6b-2c6e2773c74f.png">

### December
<img width="158" alt="December" src="https://user-images.githubusercontent.com/87828174/138989045-9930103a-b1a3-44f3-ab4f-0ba5031f7b66.png">

### Analysis

Looking at the two screenshots the following differences are oberserved:

1. The minimum and maximum temperature is higher by 2.0 and 8.0 degrees respectively for June as compared to December:
   * Maximum Temperature of 85.0 degrees  and Minimum Temperature of 64.0 degrees for June
   * Maximum Temperature of 83.0 degrees and Minimum Temperature of 56.0 degrees for December

2. The mean temperature for June was higher by 3.902589 degrees than December:
   * Mean temperature for June was 74.944118 degrees
   * Mean temperature for December was 71.041529 degrees 

3. The number of records for June were more than December while the December temperature results were more dispersed in values in relation to the mean.
   * Standard Deviation of results in December was higher than the June standard deviation of temperature results
   * The lower and upper quartiles were higher for June than for December temperature results

## Summary
### Summary
A standard summary shows that although december has more spread out values in temperature, the average temperature of June is more. Although the mean temperatures do not differ by much, there are other factors that should also be taken into account such as rainfall, extreme weather occurances, ideal locations and tourist seasons. Positive opportunities of these would result in more people coming who are available to surf or eat ice cream and have favourable weather conditions to do so. This would result in higher sales and profit. Two additional queries can be written to get more data. 
### Additional Queries

1. The following query would give us the dates with recordings of precipitation. Summary statistics could be found for average, max and min precipitation for month "n". This could help in finding out which months had higher rainfall which would cause disruptions to customers for surfing or ice cream.
   *       session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date)==n ).all()

2. The second query for "station" could help us find the best locations for the shop. Locations with suitable temperatures and lower rainfall. Measurement.station would query the locations of these recordings and summary statistics could be found for average rainfall and temperature at these locations. Locations with ideal conditions would serve as good places to set up the business.
   *       session.query(Measurement.date, Measurement.prcp, Measurement.tobs, Measurement.station).filter(extract('month', Measurement.date)==n ).all()







