# module_11_assignment google_search_analysis

This file serves to analyze MercadoLibre's search traffic and revenue to identify patterns in search traffic, determine it's correlation with stock volatility, and predict future revenue.

As fbprophet does not work well with hvplot on Windows systems, Google Colab was used to prepare this file. To accomodate the platform's environment, the file begins by setting up the necessary installs before importing the libraries and dependancies.

![Installs and imports](/Images/1.PNG)

It uploads "google_hourly_search_trends.csv" into a dataframe, then slices it to create another dataframe showing only May 2020 data and plots it.

![May 2020 search trends](/Images/2.PNG)

The file compares the montly median search traffic across all months and compares the May 2020 traffic against this, showing that this period's traffic was higher than the median.

Next, the search traffic data is mined for seasonality, beginning with a plot showing average trends by day of the week,

![Search traffic by day of week](/Images/3.PNG)

and uses a heat map to identify traffic concentrations in certain hours for each day of the week.

![Search traffic by hour per day of week](/Images/4.PNG)

It then plots the traffic by week of the year, averaged across all of the years in the data set.

![Search traffic by week of year](/Images/5.PNG)

After this, another csv file is imported to relate the search traffic to the stock price patterns. It begins by plotting the newly imported stock price data.

![Stock price](/Images/6.PNG)

To allow for relational analysis, the search traffic dataframe is concatenated with the stock price dataframe. Then it slices to the first half of 2020 to analyze this relationship over a smaller timeframe and plots the two variables side by side.

![Stock price vs search trends](/Images/7.PNG)

Two new columns - "Lagged Search Trends" and "Stock Volatility", which show the 1-hour lagged search data and the standard deviation, respectively, are added to the combined dataframe. The volatility is plotted, one more column - "Hourly Stock Return", is added to the dataframe, and a correlation table is created for "Stock Volatility", "Lagged Search Trends", and "Hourly Stock Return".

![Stock volatility](/Images/8.PNG)

![Correlation table](/Images/9.PNG)

Next, a time series model was created using FBProphet by using the original search trends dataframe, reseting the index, and renaming the columns to the acceptable format for this model. The model was fit to the formatted dataframe and a future dataframe generated 2000 hours forward from the last entry, which is used to predict future trends.

![Future trends](/Images/10.PNG)

The forecast dataframe is then pared down to show just the price prediction, along with lower and upper bounds, and these are plotted, as well as their components.

![Predictions](/Images/11.PNG)

![Component trends](/Images/12.PNG)

Finally, another dataframe is created by importing the "mercado_daily_revenue.csv" file.

![Revenue](/Images/13.PNG)

A prophet model is created and fitted to this data to predict future revenue. The component trends as well as future revenue forecasts are plotted.

![Revenue components](/Images/14.PNG)

![Revenue forecast](/Images/15.PNG)

And to finish the analysis, a revenue forecast for the next quarter is produced and formatted for presentation to the finance division.

![Next quarter revenue forecast](/Images/16.PNG)
