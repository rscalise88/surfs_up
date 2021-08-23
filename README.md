# surfs_up
## Overview of Project
An investor seeks to know if opening a Surf and Icecream shop is sustainable as a year-round venture.  Using SQLite, we review data for Oahu, HI to determine if the weather in this location is conducive to this business endeavor.

## Results
Using SQLite data analysis, we are able to extract the June temperature statistics:

![June Temperatures](https://github.com/rscalise88/surfs_up/blob/main/juneTemps.PNG)


and the December temperature statistics
![December Temperatures](https://github.com/rscalise88/surfs_up/blob/main/decTemps.PNG)

From this we can see that:
  - Given that these two months typically represent the most extreme seasons in the northern hemisphere, the average temperature between the two seasons is relatively constant, averaging only 3 degrees lower in the winter
  - Further reinforcing are the minimum and maximum temperatures over the dataset.  The max for June is 85, and for December 83.  Very confortable weather for beachgoing and ice-cream consumption.  The lows paint a similar picture, though predictably in winter it has the potential to get much more statistically colder than summer - down to a low of 56 degrees.  However, it's important to remember that these are almost certainly nighttime temperatures and would have little to no impact on a daytime business model.
  - Finally, it's important to note that the data we are tasked with retrieving paints a potentially deceptively positive picture of the prospects for this location.  it would be beneficial to review more than temperature data to ascertai nthe viability of this location.  More on this in the following section.

## Summary 

It would appear based on the comfortable temperatures observed at this location year-round that the potential is there for a thriving business focused on selling surfing equipment and cooling ice-cream for surfers anmd beachgoers looking for a refreshing treat.  However, the data reviewed has severe limitations and further analysis is vital before making any hasty moves on this investment opportunity.

In addition to the temperature data we retrieve in the course of the analysis, precipitation data is also readily available in the dataset and could be used to predict the potential for inclement weather to cause a decline in customers.  This information could be extracted together with the temperatures as follows:

    session.query(Measurement.date, Measurement.tobs, Measurement.prcp).filter(extract('month',Measurement.date)==6).all()

Further, the client seeks to know if the business could succeed as a year-round venture.  However, we are initially tasked with only reviewing the data for June and December.  The code could be refactored to simpyl removed this limitation and retrieve the data for the entire year to ensure that the other 10 months of the year provide favorable weather. This could be done as follows:

    session.query(Measurement.date, Measurement.tobs, Measurement.prcp).all()
    
  
