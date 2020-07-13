# Predicting Indian Trade values using Autoregression Time Series

## Inspiration

The most deciding factors of a country’s economic status and performance include ‘Imports’ and ‘Exports’ that the country does. This being the reason, inspired me to work on something that can predict such factors which may further find applications in various economic areas.

## About Data

The data for this Time Series model was picked up from Kaggle and originally collected from the official website of Department of Commerce of India.
It contain 3 columns and 165 rows. First column is timestamp which is from January, 2006 to September, 2019. Other two columns are for total amount of Import and Export for the respective month in US Billion Dollars.

The value of each data entry being so high, increases the chances of error. But still the model is successful to achieve quite close predictions and hence can be used to gain broader idea of Imports and Exports of India.

## Checking Seasonality and Trend
For this, firstly the mean and variences of both(Import and Export) were checked. After which it was clear that the data was not stationary.

On applying Dicky-Fuller test on both series gave the same intuition.

By this time it was clear that the data lagged stationarity, hence it wasn’t appropriate to proceed with such data. Introducing stationarity to the data was required.

## Introducing Stationarity to Data:

The square root of the reciprocal [(x)**(-1/2)] were taken for each element of the series. This was followed by a ‘Differencing’ operation which played a major role in removing tred and introducing stationarity.

The Dicky-Fuller test when applied on the new series confirmed the stationarity.

## Forecasting

And now comes the most exciting part! 

The Autoregression regressor(AutoReg) was imported from ‘statsmodels.tsa.ar_model’.
Autoregression is a time series model that uses observations from previous time steps as input to a regression equation to predict the value at the next time step.

To make predictions, the last 7 values of data were taken as ‘test set’ while the rest were used for training the Time Series model.

So the training and prediction was over. But, the predictions made were’nt in their original scale.

## Scaling predictions to original scale

The .cumsum() operation was used to rescale the values which were changed due to ‘Diffrencing operation’. Also the last element of unscaled training set was added to predictions. This was followed by taking the squares of reciprocal of each element in predictions.

The above set of operations gave the required prediction values.
