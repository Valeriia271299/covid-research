# covid-research

## prediction of covid dynamics

Many scientists around the world are literally now dealing with the problem of the coronavirus COVID-19. The Data Scientists community, who are trying not only to predict the development of the pandemic, but to help determine the most significant factors influencing the spread of the infection, did not remain on the sidelines. For example, on the notorious Kaggle.

In a small study, we used daily updated data from the repository, specifically time-series-19-covid-combined.csv. To obtain agreement between the results of the model and the conclusions written in the laptop, I attach specific data in the repository, on the basis of which the final run of the models was carried out.

## Part 1
As in any work with data, to begin with, an EAD was carried out (for a complete acquaintance with it, I suggest trying to start the laptop yourself: this way you can even see a map with the spread of the pandemic). As part of the EAD, the boundaries of the study period were investigated, the number of cases, deaths, recovered, and an increase in the number of countries that confirmed cases of infection was visualized. Until about mid-February, the total number of countries with coronavirus cases remained at about 25, but since mid-February there has been a sharp and large jump, such that in a month the number of countries exceeded 170. World trends in the number of cases were visualized | dead | recovered and plotted graphs that reflect mortality from the virus in different countries or on different continents. The dynamics of global trends is similar: until mid-March, the number of cases, deaths and recovered grows moderately slowly, and in mid-March these numbers begin to grow very quickly, this trend is most clearly manifested with the number of cases (for a month the number grows 5 times from 0.5 million to 2 , 5 million). In addition to various visualizations and analysis of the situation in the world in a laptop, you can find a comparison of the spread of the pandemic in Russia with the whole world. In general, the trends are similar, but in Russia the situation begins to deteriorate significantly and sharply in late March - early April, and in the world - from mid-March and more smoothly. Moreover, there are very few deaths in Russia compared to world statistics. Top 10 leaders in the distribution of covid in May 2020: USA, Italy, Spain, France, Germany, Great Britain, Turkey, Iran, Hubei (province in China), Russia. In the conducted EAD, in addition to the already voiced facts, one can find various comparisons of other indicators and, accordingly, small conclusions on them.

The key conclusion from the first part of the study: if since the appearance of the virus in China, the number of cases increased mainly in it, and other countries were on the sidelines and did not understand the danger of the whole situation, now the situation, one might say, has changed. There are countries where the number of cases and deaths exceeded China, and in a very short time, because the countries either did not want to introduce quarantine, or were not prepared. China is entering a "plateau". The foci of infection spread throughout the regions at about the same time - such a conclusion can be made by looking at Europe and the time when a rapid trend of the infected began in European countries. It is worth noting that in Russia the upward trend begins to increase later than in European countries, which gives the right to assume that our country is only on the way to the peak of coronavirus infection. As for the number of deaths from the virus, it is higher in countries where life expectancy is longer than the average, and in those who were not ready for a pandemic for any reason (in the case of the United States, as already mentioned, private health care, in the case of poor countries - lack of money, not equipment and quality medicine). If we talk about the indicators themselves as those that will be predicted in part 2 of the study, then with almost 100% certainty we can say that we will have to deal with the nonstationarity of the series due to the characteristic trend.

Part 2

In the second part of the work, several models were built and a time series was predicted for such an indicator as mortality from the virus. Mortality is calculated using the formula:

$$ CFR = \frac{Deaths}{Confirmed} $$

For each type of model, 3 forecasts are implemented for Russia, Italy and Spain. Russia was chosen because the statistics and the situation in the country where we live are interesting. Italy and Spain were chosen because in a short time they managed to catch up and even surpass the number of cases in China, where the virus appeared, moreover, these countries have a high life expectancy, and it is known that the probability of dying from coronavirus is greater in old age, and it is in the task that lethality is analyzed. The USA, the leaders in the number of cases, was not chosen, because, in my opinion, it would be more difficult to fight the trend in their case.

## RMSE quality metric.

The notebook presents the results of the following models for predicting mortality in selected countries: mean constant model, linear trend model, exponential smoothing, MA - Moving average, AR - Autoregressive model, ARMA, ARIMA (Auto Regressive Integrated Moving Average), SARIMA, Linear Regression Model , xgboost (not fully implemented). Also, the Prophet library was used to predict the time series.

From the second part of this small study, the following conclusions can be drawn: exponential smoothing works well for all countries, but then the results are different. Models AR, MA, ARIMA work well for Russia. For Italy, those related to the trend (linear trend model, smoothing models). And for Spain, as well as for Russia, there are AR, MA and ARIMA models. It seems to me that such a situation may have developed, because in Italy the trend is more pronounced than in Russia and Spain, therefore, models with a trend work better on the data of this country. One more thing that I would like to note in the conclusion on the second part is the need in ARIMA models to deal with the nonstationarity of the series, which was common for all three countries.

## Conclusions on covid research

Despite the external similarity in the development of the disease around the world, when analyzing the three countries separately, it turns out that different models are suitable for them, more precisely, different models work better. Of course, visualization and correlations help to see general patterns, but in order to better predict the series, it is necessary to carefully analyze one country, trying different models and, most importantly, hyperparameters. An interesting feature of covid data was the non-stationarity caused, most likely, by a characteristic trend. It was necessary to fight with it for adequate forecasting of the series. As for other models, there were no problems with them.







