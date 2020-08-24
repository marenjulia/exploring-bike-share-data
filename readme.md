# Exploring Bike Share Data: Visualizing the effects of a global pandemic on San Francisco Bay Area's bike share system
## by Maren Zoller

Bay Wheels (previously Ford GoBike) is a bike share system in the San Francisco Bay Area. Bay Wheels is operated by Lyft, and provides its bikes in the San Francisco, San Jose, and East Bay area. A docked bike can be checked out 24/7 at any station and must be returned to a Bay Wheels station when the trip is complete. 

## Dataset

Bay Wheels trip data is open for public use, and can be downloaded on their [website](https://www.lyft.com/bikes/bay-wheels/system-data). The system data offers information on start and end station location, start and end date and time of the trip, and some additional information on the bike user, and the bike in use. I extracted trip data for January to June 2019 and 2020, and loaded it into a 2019 and a 2020 dataframe. Before starting my exploration, I performed several data wrangling steps. E.g. I used the trip start time to extract month, weekday and hour of the trip, and the latitude and longitude data to add a start city and end city feature to the dataset. Also, I performed several cleaning steps to change datatypes and deal with missing data and outliers. During 2020, some columns were renamed, so I transferred their values from the new column to their respective place in the old column, and then dropped the old column. All wrangling steps are documented in detail in the Assessing and Cleaning steps in the exploration notebook. While exploring the data, I circled back to some more wrangling steps to calculate duration minutes from duration seconds, to add a duration category column, and to recalculate 2020 latitude and longitude data by station based on the station means. 


## Summary of Findings

As expected, there were notable differences in the feature distributions between the 2019 and 2020 dataset. 

In 2019, Bay Wheels bikes seem to be primarily used for commuting to and from work, especially to bridge the "last mile" between commuter hubs like the ferry building, or commuter train and office locations. 
- The average trip duration was at ca. 13 minutes and 10 seconds. I transformed seconds to minutes and log-transformed the x-axis, still trip duration has a highly right-skewed distribution.
- Trips are ranging from a few seconds to about one day, 75% of trips are shorter than 15 minutes.
- There are very little trips between 11pm and 5 am, trips by hours of the day has a bimodal distributions with one peak at 8am and another, slightly higher one at 5pm.
- Bay Wheels bikes are more popular during the week than on the weekend (ca. 17% of trips).
- Surprisingly, bike trips are not increasing with warmer months, March and April have more trips than both January and February and May and June.
- 85% of all trips are subscriber trips (subscribers pay a monthly or annual fee, customers pay per ride duration).
- Three out of four trips start in San Francisco, the top 10 start and end stations are all located at commuter hubs in central San Francisco.
- The distribution of bike trip durations does not change vastly over the months, but the median trip duration increases by ca. a minute from January to June.
- On weekends, median trip duration is slightly longer than during the work week, due to less trips below 20 minutes and more trips above 30 minutes of trip length taking place.
- Bike trips up to 10 minutes of length follow the 8am and 5m peaks, with an additional smaller peak at 12pm. Bike trips above 30 minutes of length follow a left-skewed distribution, with a 5pm peak.
- Median trip duration in San Francisco is at ca. 10 minutes, at San Jose and East Bay only at ca. 8 and 7 minutes. 
- More than 50% of subscriber trips are shorter than 10 minutes, while customers median trip duration lies closer to 15 minutes. Ca. a quarter of customer trips is longer than 20 minutes.
- Subscriber trips peak at 8am and 5pm, customer trips do not follow commuter hours closely. Customer trips are almost equally distributed amongst weekdays, more subscribers use the bikes on work week days than the weekend.
- There is no observable relation between user type and month
- When relating start station and trip duration, and visualizing it on the map, stations in outskirts of the 3 evaluated cities have longer trip durations than central stations.
- While trip duration stays similar on work week days in all months, trip duration on weekends is longer from March to June than in January and May
- Average subscriber trip duration in San Francisco is ca. 2 minutes longer than in San Jose and East Bay. Average customer trip duration is shortest in East Bay (ca. 23 minutes) and longest in San Jose (ca. 27 minutes).

In 2020, a similar commuter focus was visible. At the same time trip duration, distribution of user types and duration and number of trips in certain months, at certain weekdays and hours of the day have changed - possibly impacted by the lockdown measures due to the Covid-19 pandemic. 
- The number of trips longer than 20 minutes is higher than in 2020, the average trip duration was at ca. 16 minutes and 20 seconds. I transformed seconds to minutes and log-transformed the x-axis, still trip duration has a highly right-skewed distribution.
- Trips are ranging from a few seconds to about one day, 75% of trips are shorter than 18 minutes.
- There are very little trips between 11pm and 5 am, trips by hours of the day now follow a left-skewed distribution with its peak at 5pm (with the exception of a smaller peak at 8 am - the commuter distribution is not entirely lost)
- The difference of week days and weekend trip number is a lot less pronounced. In 2019 the weekday weekend difference was up to 9%, in 2020 it is only around 3%.
- On a month level, the difference in trip numbers becomes very obvious. In January and February, trip numbers are higher than in 2019 (March 2019: just over 25,000, February 2020: over 40,000 trips). In March 2020, trips fall to under 20,000, then even under 10,000 in April. In May and June they slowly increase, still staying under 20,000 trips per month. 
- The ratio of subscribers and customers shifts tremendously, with subscribers decreasing by 30% to 55%, and customers increasing to 45%.
- Four out of five trips start in San Francisco, trips starting in East Bay more than halfed. The top 10 start and end stations are still located at commuter hubs in central San Francisco.
- January to March have similar bike trip duration distributions like 2019, from April onwards, the median trip duration increases. The curve is more distributed, hinting at more long recreational bike trips and less short commuter trips. 
- Median trip duration stays similar to 2019, both during the week and on weekends. The difference in trip length disitrubition is most obvious at and beyond the third quartile, which moves from ca. 14 minutes on weekdays and 18 minutes on weekends in 2019 to ca. 17 minutes during the week and above 20 minutes on weekends in 2020. Trips below 20 minutes of length decrease in number, above 30 minutes increase in number from March onwards.
- Median trip duration in San Francisco in all cities increases by ca. a minute, due to more trips above 20 minutes than in 2019. The regional distributions were more distinct in 2019 than in 2020. 
- There is an increase in subscriber trips above 20 minutes length and an increased median subscriber trip duration. The customer trips have a lower median trip duration than in 2019, caused by an extreme increase in shorter trips below 20 minutes. The number of customer trips increased in all categories, also the longer trips, but no category shows a greater increase than the one below 5 minutes.
- While in 2019, subscriber trips and customer trips were following different distributions over the hours of the day, they are following the same curve with a minor peak at 8 am and a bigger peak at 5pm in 2020. the number of subscriber trips decreased by ca. 50.000 trips per day during the work way, and stayed near constant on weekends. Customer trips almost quadrupled during the work week, with most trips on Wednesdays and Fridays. Saturday and Sunday customer trips increased as well, but are not more common than work week days anymore. 
- It seems that from 2019 to 2020, Bay Wheels has promoted the customer user type more successful, as January and February have a lot more customer trips in 2020 than in 2019. From January to February 2020, subscriber trips increase by ca. 100.000 trips - and then drop by around 150.000 trips from February to March. Subscriber trips seem to be hit by the lockdown much more than customer trips. They recover faster and are now on a higher trip number level than the subscriber trips.
- When relating start station and trip duration, and visualizing it on the map, stations in outskirts of the 3 evaluated cities have longer trip durations than central stations, the overall trip duration increases both in the centers and outskirts of the three bike hubs.
- Trip duration stays similar on work week days from January to March. In April, May and June, average trip duration increases both on weekdays and the weekend, and weekdays are not as similar in average duration length as before.
- In 2020, the average trip duration for subscribers increases by a few minutes in San Francisco and San Jose - and more than doubles in East Bay. Average trip duration for customers stays similar to 2019 levels in San Francisco and East Bay, but decreases in San Jose.

## Key Insights for Presentation

For the presentation, I focus on the influence of the time-related variables and user type on the trip duration. I start by introducing the distribution of trip duration, and distribution of the features with the biggest change from 2019 to 2020, month and user type. 

Afterwards, I introduce the influence of month, weekday, hour of the day, and user type on trip duration in 2019 and 2020. I am using violin plots for month, weekday, and user type, and a bar chart for hour of the day. For all violin plot visualizations I focus on a snapshot of trips with a duration below 60 minutes. After asking for feedback on the exploration visualizations, I decided to include a representation of average trip time by month by user type in the presentation. To finish the presentation, I am visualizing a map of trip duration by station location to confirm that the change in trip duration is visible in all three evaluated regions. 

## Resources Used for the Exploration

Libraries used: 
- Numpy
- Pandas
- Matplotlib
- Seaborn

Resources used: 
- Bay Wheels System Data: https://www.lyft.com/bikes/bay-wheels/system-data
- Pandas Documentation: https://pandas.pydata.org/docs/
- Seaborn Documentation: https://seaborn.pydata.org/
- Open Street Map: https://www.openstreetmap.org/#map=14/37.7656/-122.3990
- Blog on how to create simple map visualizations with Open Street Map and Matplotlib: https://towardsdatascience.com/easy-steps-to-plot-geographic-data-on-a-map-python-11217859a2db
- Stack overflow forum entries: https://stackoverflow.com/questions/45615306/get-top-rows-from-column-value-count-with-pandas, https://stackoverflow.com/questions/30244952/how-do-i-create-a-new-column-from-the-output-of-pandas-groupby-sum
