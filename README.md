# Forecasting Real Estate Value in San Jose, CA


### Lynn Anderson


# Overview

The aim of this project was to use time Series analysis to build a model that predicts the future real estate  values of zip codes in the San Jose, CA metro area. Specifically, I sought to identify which zipcodes are forecasted to provide the highest return on investment in the next 3 years. I investigated the performance of a SARIMAX model and Prophet model on one zipocde, and subsequently selected the higher performing model to forecast future real estate values on all relevant zipcodes.


# Business Understanding

Bay Area Properties Group is looking to invest in real estate in the San Jose area. Many tech start ups are based in this location, and, with an influx of high-income tech workers, there is lkely to be a demand for property in the future. To give enough time to allow values to appreciate, yet minimize risks that come with uncertainty of trying to predict far into the future, they are initially looking for 3 year investments. Therefore, in order to make informed decisions, they want to know the 5 zipcodes predicted to provide the highest 3 year return on investment. Additionally, they are mindful of their starting budget, and are most interested in areas whose average priceis under 2 million.


# Data Understanding

The dataset consisted of a csv file obtained from Zillow Housing dataset. Each record represented a zipcode, with information including the city, metro area, county and state, as well as the average sale price of real estate taken at one month intervals. The original dataset consisted of records from 14,723 zip codes across all 50 states and DC, and spanned April 1996- April 2018. The data used in this project only looked at zip codes in the San Jose metro area. Additionally, to minimize the effects of the 2008 crash and model for more recent trends, only data from 2012 onwards was used for modeling.

# Data Preparation

I loaded the csv file into a dataframe and removed all unnecessary columns before investigating some basic statistical info. Additionally, the %ROI was calculated for each zipcode and added to the dataframe. In this analysis, 40 zipcodes in the San Jose area will be evaluated. 3 are in San Benito county, and the remaining in Santa Clara county. Average price for all zipcodes in April 2018 was $1.16 million, and average ROI was 127%. 

(img marker) ![outcomes](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)

(comments)

 (Marker) ![months](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)

(comments)


# Modeling

The zipcode with the highest 2012-2018 ROI, 94089, was chosen as the zipcode to explore modeling. The last 2 years were witheld from from the training models and used as test data to evaluate model performance. First, an auto-ARIMA was run to generate optimal parameter values for the SARIMA model. The SARIMA model was then used to predict values from the last 2 years, and those predictions were compared with the actual values in order to evaluate how well the model performed. Then, a similar approach was used to run a Prophet model, whose performance was evaluated by comparing predicted prices with the actual observed values. 

For this dataset, the SARIMA model was much higher performing than the Prophet model. 

First, I am going to examine a SARIMA (Seasonal Autoregressive Integrated Moving Average) model on the zipcode 94089. The SARIMA model takes care of trends and seasonality, so it is not necessary to make the input data stationary. First, an auto ARIMA model was used to generate the optimal p, d, and q values and seasonal order. Those parameters are then used to fit a SARIMA model, which is then used to generate future forecasts.

The Prophet model was developed by Facebook to account for datasets often encountered at Facebook, which typically contain any or all of the following- hourly, daily, or weekly observations with at least a few months of history, multiple seasonality trends, holidays, missing observations, large outliers, and non-linear trends. While the dataset used in this project only has a couple of those qualities, it will be interesting to see how it performs.



(img marker) ![outcomes](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)
(img marker) ![outcomes](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)

# Evaluation

# Forecasting

I will now calculate the 3 year forecast, along with confidence intervals, for zipcode 94089 using the SARIMA model from above. A linnear upward trend is predicted. The confidence interval is relatively narrow for the first year, but widens considerably by the end of the forecast time period. Even if actual values are on the low end of forecast values, these is still growth predicted in the near future. 
Using the SARIMA model that was used to predict and forecast future values for 94089 on all relevant zipcodes. The zipcode and corresponding forecasted 3 year ROI were stored in a list, which was sorted and used to make conclusions.

# Recommendations

The zipcodes forecasted to have the highest ROI in the next 3 years are 95050, 95054, 95128, 94089, and 95126. Forecasted 3 year ROI for the top 5 zipcodes range between 68% and 92%. All 5 zipcodes had an average 2018 home value between roughly \\$1.2 and \\$1.4 million. Although Santa Clara only had 3 zipcodes represented, 2 of them were in the top 5, indicating considerable growth in that city. 

(img marker) ![outcomes](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)


# Conclusions

Given the growth the area has seen in the last decade, any of the above 5 zipcodes would be a good investment choice. A brief summary about each zipcode is provided below. Statistics sourced from https://www.zipdatamaps.com/   

## Zipcode 95050:
- Predicted to grow by 91%
- Santa Clara, CA
- population of 40,000 
- 14,000 households

## Zipcode 95054:
- Predicted to grow by 86%
- Santa Clara, CA
- population of 24,000
- 8,000 households

## Zipcode 95128:
- Predicted to grow by 85%
- San Jose, CA
- population of 35,000
- 13,800 households

## Zipcode 94089:
- Predicted to grow by 78%
- Sunnyvale, CA
- population of 24,000
- 7,500 households

## Zipcode 95126:
- Predicted to grow by 68%
- San Jose, CA
- population of 35,000
- 13,200 households

(img marker) ![outcomes](https://github.com/lalynjay/weather_classification/blob/main/images/pic.png)

# Next Steps and Limitations:

- Economic recessions are hard to predict and can have drastic influences on real estate prices. 


- Other factors that contribute to housing demand- work-from-home opportunities, a booming start-up, job markets, and weather.


- The Zillow dataset had its most recent observations from April 2018. Finding more recent data will allow for more accurately forecasting future home values in the next few years.


# For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/lalynjay/Time_series_analysis/blob/main/Time_series_analysis.ipynb) or review [this presentation](https://github.com/lalynjay/weather_classification/blob/main/weather_classification.pdf)

For additional info, contact Lynn Anderson at lalynjay@gmail.com

Repository Structure

├── data 

├── images

├── README.md

├── ts_presentation.pdf

└── notebook.ipynb
