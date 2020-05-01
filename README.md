##Blog Report
<br />

###Background and explain the data:
As we all know, Mediocre Social Network Apps Incorporated has struggled for a few years as people's preferences change, which is evidenced by its stock price. They are hoping that things are turning around, but also want to be realistic with themselves as to what the fourth quarter will hold this year. Our goal is to forecast their stock price for the first ten trading days of October 2019. 
![](/Users/shixinli/Desktop/Stat153/project/blog/pic/data_description.png)  

As we can see, first, **mathbf data has a decreasing trend** because people's preferences have changed in recent years, which led to a decline in people's expectations for the company's future earnings. Then people sold their stocks and made the stock price fall all the time.

Besides, if you are careful enough, then you could find **the autocorrelation structure of the volatility of the data**. After removing trend and seasonality, we find that stock price fluctuations are not irregular like white noise time series. Instead, the rise in stock prices over a while (although there is a downward trend, on the whole, there is also a group of upward time intervals) indicates the prices may continue to rise afterward. But as the rate of increase slows, stock prices may enter a falling range soon and continue to fall, which shows us an autocorrelation structure of our data.

<br />

###Why our best model approximately models the data?
To begin with, we notice that the magnitude of our data fluctuations at different times seems to be changed. In the earlier periods such as 2015-2016, the volatility of the data is relatively higher, while at a later time like in 2017-2019, the volatility of the data is relatively smaller. Therefore, we decide to use our tool called “log” function to help the variance of our data be constant over time, that’s to say, we keep the volatility of our data being a constant, which is beneficial to our future modeling.
![](/Users/shixinli/Desktop/Stat153/project/blog/pic/log_price.png)
Then, we are going to deal with the trend in our best model. As you can see in the graph above, it seems that we have a quadratic trend like a decreasing parabola in our data after stabilizing its variance. In our best model, we use a method named difference to remove the quadratic trend, which is also suitable for fitting data just like taking the “log” function previously. Specifically, we take the difference twice in order to remove the quadratic trend of our data.

![](/Users/shixinli/Desktop/Stat153/project/blog/pic/diff2.png)


Besides, by observing the ACF and PACF plots of residuals from our current model, we find that there is an autocorrelation structure of our data, specifically a Moving Average (1) pattern. You maybe don’t understand what “Moving Average” is. It’s just a term in statistics, representing a particular type of autocorrelation structure of data. In our best model, we use ARIMA(0,2,1), a combination of taking the difference twice and MA(1), to fit the data and pursue stationarity.


After going through this series of steps, our model has passed several statistical tests. The results of these tests can explain the correctness of our model, for example, the Ljung-Box test and ACF/PACF test. So far, we have finished our goal of pursuing stationarity.

![](/Users/shixinli/Desktop/Stat153/project/blog/pic/model_info.png)


Let me tell you some finance intuition hidden behind our model. The core of our model is MA(1), meaning that there is a link between the price “today” and the price “yesterday”. We find that there is a strong linkage between the stock prices of the two adjacent days, but the linkage between the stock prices of more than two days is very weak or even zero. 


If you have some financial background, you might think of the Efficient Market Hypothesis(EMH) in finance. The Weak Form Efficiency market means that under weak-form effective conditions, the market price has fully reflected all the historical securities price information, including the stock’s transaction price, volume, etc. When the market is not weak-form effective, whoever has the most authentic historical data can make more money than others! And when everyone can grasp historical data, that is, when it is weakly effective, you can no longer make money through historical data. 


There is one way to test whether the market is Weak Form Efficient. If the stock prices have an autocorrelation over time, that is, the price that can be affected by the previous prices, then weak efficiency cannot be established. In our analysis, we have found the autocorrelation in the stock prices, which means that the stock market is not a weak efficient market, and most importantly, people can make money from forecasting the future price by using the historical data, which is why we can predict future stock prices.  

<br />

###Forecast and Meaning
We forecast the stock price for the first ten trading days of October 2019, and the results are as below. Here are the 10 prediction stock prices from our best model: 20.46894, 20.45788, 20.44683, 20.43578, 20.42474, 20.41371, 20.40268, 20.39166, 20.38065, 20.36964. As you see, our predictions decrease monotonically. 
![](/Users/shixinli/Desktop/Stat153/project/blog/pic/prediction.png)

Since our predicted prices are derived based on the average price values of possible future prices, you do not see fluctuations in our predicted value, which sends us a critical message. In the future stock prices, the decreasing quadratic trend is still dominant. Our prediction of stock price also shows that the situation of the company will still not be optimistic, and its stock price will continue to fall.
















# stat153-project
