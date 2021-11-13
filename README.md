# Surfs Up - Investment Analysis
### Overview of Weather Analysis: 
The weather analysis will provide insights into the prospective location of Surf n' Shake. The investor W.Avy found that the weather data is a good indicator of a surf shop's success from his previous business venture. The analysis will provide descriptive statistics of the temperatures during June and December. This includes the central tendency, dispersion, and shape of the weather dataset distribution, which will help the investor determine if the surf and ice cream shop business is sustainable year-round.

### Results: 
* The average temperature in June is 74ºF, and the average temperature in December is 71ºF. 
* The temperature range for June is between 64ºF and 85ºF.
* The temperature range for December is between 56ºF and 83ºF.

![](https://i.imgur.com/xskWRUu.png)
![](https://i.imgur.com/WbLWc7L.png)

### Summary: 
The temperature data from June and December did not vary, which indicates that the business would be sustainable year-round. It would be beneficial to find out if it rained during those months and how much to expand on this analysis. Tourists are more likely to visit an ice cream shop if the weather is above 70º and clear skies. Below are examples of how to pull information on the precipitation during June and December. Additionally, it will be important to filter to weather stations closest to the shop.

1. For June Precipitation: 
``` 
june_rain = session.query(Measurement).filter(extract('month', Measurement.date) == 6)
june_rain_lists = [rain.prcp for rain in june_rain]
june_rain_df = pd.DataFrame(june_rain_lists,columns=['June Precipitation'])
june_rain_df.describe()
```
2. For December Precipitation: 
```
dec_rain = session.query(Measurement).filter(extract('month', Measurement.date) == 12)
dec_rain_lists = [rain.prcp for rain in dec_rain]
dec_rain_df = pd.DataFrame(dec_rain_lists,columns=['December Precipitation'])
dec_rain_df.describe()
```
3. To filter for the Weather Station closest to the shop:
```
# Add to the end of the query
filter(Measurement.station == 'USC00519281')

june_rain = session.query(Measurement).filter(extract('month', Measurement.date) == 6).filter(Measurement.station == 'USC00519281')
dec_rain = session.query(Measurement).filter(extract('month', Measurement.date) == 12).filter(Measurement.station == 'USC00519281')
```
