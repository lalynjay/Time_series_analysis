# Forecasting Real Estate Value in San Jose, CA


## Using Time Series Analysis to Predict Future Values


### Lynn Anderson


# Overview

The objective of this project was to use time series analysis to build a model that accurately predict future real estate values in San Jose, CA. Specifically, I sought to identify which zipcodes are forecasted to provide the highest return on investment in the next 3 years. I investigated the performance of a SARIMAX model and Prophet model on one zipocde, and subsequently selected the higher performing model to forecast future real estate values on all relevant zipcodes.


# Business Understanding

An investment company is looking to invest in real estate in the San Jose metro area. Many tech start ups are based in this location, and, with an influx of high-income tech workers, there is lkely to be a demand for property in the future. To give enough time to allow values to appreciate, yet minimize risks that come with uncertainty of trying to predict far into the future, they are initially looking for 3 year investments. Therefore, in order to make informed decisions, they want to know the 5 zipcodes predicted to provide the highest 3 year return on investment. Additionally, they are mindful of their starting budget, and are most interested in areas whose average price is under $2 million.


# Data Understanding

The dataset consisted of a csv file obtained from Zillow Housing dataset. Each record represented a zipcode, with information including the city, metro area, county and state, as well as the average sale price of real estate taken at one month intervals. The original dataset consisted of records from 14,723 zip codes across all 50 states and DC, and spanned April 1996- April 2018. The data used in this project only looked at zip codes in the San Jose metro area. Additionally, to minimize the effects of the 2008 crash and model for more recent trends, only data from 2012 onwards was used for modeling.

![zipcode history](https://github.com/lalynjay/Time_series_analysis/blob/main/images/history_all_years.png)

Most zipcodes follow a similar trend. The housing market bubble and subsequent crash is clear, with growth beginning again around 2012.


![recent history](https://github.com/lalynjay/Time_series_analysis/blob/main/images/history_2012.png)

With the effects of the housing bubble removed, there now appears to be overall steady growth in the area.


# Data Preparation

The csv file was loaded into a dataframe and all unnecessary rows were removed. Additionally, the %ROI from 2012-2018 was calculated for each zipcode and added to the dataframe. In this analysis, 40 zipcodes in the San Jose area were be evaluated. 3 were in San Benito county, and the remaining in Santa Clara county. Average price for all zipcodes in April 2018 was $1.16 million, and the average ROI was 127%. 

![ROI all zips](https://github.com/lalynjay/Time_series_analysis/blob/main/images/ROI_all_zips.png)

94089 was the highest growing zipcode by a substantial amount. Roughly half the zipcodes fell above the mean, and half below it. 

![price all zips](https://github.com/lalynjay/Time_series_analysis/blob/main/images/price_all_zips.png)

94086, the second highest performing zipcode in terms of ROI, had the highest average home value. 

# Modeling and Evaluation

The zipcode with the highest 2012-2018 %ROI, 94089, was chosen as the zipcode to explore modeling. The last 2 years were witheld from from the training models and used as test data to evaluate model performance. First, a SARIMA (Seasonal Autoregressive Integrated Moving Average) model on the zipcode 94089 was examined. An auto-ARIMA was run to generate optimal parameter values for the SARIMA model. The SARIMA model was then used to predict values from the last 2 years, and those predictions were compared with the actual values in order to evaluate how well the model performed. Then, a similar approach was used to run a Prophet model, whose performance was evaluated by comparing predicted prices with the actual observed values. Since both models take care of trends and seasonality, it was not necessary to make the input data stationary. 

For this dataset, the Prophet model (RMSE of \$59,000) was considerably higher performing than the SARIMA model (RMSE \$73,000). Additionally, the confidence interval was considerably narrower for the Prophet model, (about \\$300k for the prophet vs over \\$500k for the SARIMA by the end of the preticted time period) indicating less uncertainty.


![sarima eval](https://github.com/lalynjay/Time_series_analysis/blob/main/images/sarima_eval.png)

Comparing the results of the last 2 years of actual data with the SARIMA's predicted values after being fit on the training data. The confidence interval is rather wide at the end.

![prophet eval](https://github.com/lalynjay/Time_series_analysis/blob/main/images/proph_preds.png)

Evaluation of the Prophet model. Overall it performed better.


# Forecasting

The 3 year forecast, along with confidence intervals, was then calcultated for zipcode 94089 using the Prophet model from above. A linnear upward trend is predicted. The confidence interval is relatively narrow for the first year, but widens considerably by the end of the forecast time period. Even if actual values are on the low end of forecast values, these is still growth predicted in the near future. 
The Prophet model was then used to forecast future values for all relevant zipcodes. The zipcode and corresponding forecasted 3 year ROI were stored in a list, which was sorted and used to make conclusions.

![prophet forecast](https://github.com/lalynjay/Time_series_analysis/blob/main//images/proph_forecast.png)


# Recommendations

The zipcodes forecasted to have the highest ROI in the next 3 years are 94086, 95008, 95134, 95117, and 95118. Forecasted 3 year ROI for the top 5 zipcodes ranged between 51% and 55%. All 5 zipcodes had an average 2018 home value between roughly \$1.3 and \$1.9 million, possibly indicating the zipcodes already on the higher end of the price rance are forecasted to grow even more. Sunnyvale had only 2 zipcodes represented, yet one of them was the highest forecasted %ROI. The rest of the zipcodes belonged to San Jose.

![top 5](https://github.com/lalynjay/Time_series_analysis/blob/main//images/top5_ROI.png)

# Conclusions

Given the growth the area has seen in the last decade, any of the above 5 zipcodes would be a good investment choice. A brief summary about each zipcode is provided below. Statistics sourced from https://www.zipdatamaps.com/   

## Zipcode 94086:
- Predicted to grow by 55%
- Sunnyvale, CA
- population of 48,000 
- 18,500 households

## Zipcode 95008:
- Predicted to grow by 51%
- San Jose and Campbell, CA
- population of 49,000
- 18,400 households

## Zipcode 95134:
- Predicted to grow by 51%
- San Jose, CA
- population of 31,000
- 6,500 households

## Zipcode 95117:
- Predicted to grow by 51%
- San Jose, CA
- population of 29,000
- 10,800 households

## Zipcode 95118:
- Predicted to grow by 51%
- San Jose, CA
- population of 33,000
- 11,200 households

![map](https://github.com/lalynjay/Time_series_analysis/blob/main/images/map.png)

Location of the top 5 zipcodes. The leftmost point is located in Sunnyvale, the rest in San Jose.

# Next Steps and Limitations:

- Economic recessions are hard to predict and can have drastic influences on real estate prices. 


- Other factors that contribute to housing demand- work-from-home opportunities, a booming start-up, job markets, and weather.


- The Zillow dataset had its most recent observations from April 2018. Finding more recent data will allow for more accurately forecasting future home values in the next few years.


# For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/lalynjay/Time_series_analysis/blob/main/Time_series_analysis.ipynb) or review [this presentation](https://github.com/lalynjay/Time_series_analysis/blob/main/ts_presentation.pdf)

For additional info, contact Lynn Anderson at lalynjay@gmail.com

Repository Structure

├── data 

├── images

├── README.md

├── ts_presentation.pdf

└── notebook.ipynb
