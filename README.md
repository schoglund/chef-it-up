# Cooking Class Fill Rate Forecasting with Time Series Analysis
## Background
This project will look into cooking class fill rates from 2019-2022 to do demand forecasting on future classes. Predicting how full classes are helps:
* the **chef** 👩‍🍳 know what ingredients and their quantities to buy for the week to *ensure freshness and sufficiency*
* the **store manager** 👩‍🏫 identify which classes are popular to *attract customers and maximize profit*
* the **scheduler** 👨‍💻 slot chefs and kitchen assistants to *provide the appropriate coverage for classes* since some chefs specialize in certain cuisines and the number of assistants needed depends on recipe complexity and class size

## Project Plan
### EDA
* summary statistics of the original data + any new features: count, mean, median, standard deviation
* how to handle missing values
* correlation between fields to eliminate duplicate info
   
### Feature Engineering
Are there any factors I can create from this data that impacts class fill rates or can tell more to the story? I've always thought of feature engineering as a way to give the model more context to the situation in a numerical way. I'll incorporate:
   * weather data to check if it rained/snowed/hailed `did_precipitate` 🌧️🌨️⛈️
   * what day of the week the class falls on 📅 ->> 6 dummy variables for each day or classify dates into two categories: weekday (M-Th) or weekend (F-Su) ->> my EDA will tell me what days I'm rocking with and how to set this up `is_weekday` returns 1/0
   * time of day 🕘🕐🕔 ->> morning (9-12), afternoon (1-4), evening (5-7) `time_of_day`
   * class day proximity to a holiday `proximity_to_holiday` 💌🦃🎅 ->> take the absolute value between the class day and the previous and next holiday, then take the minimum ->> typically classes fill up when it's near a U.S. holiday, like Valentine's Day, Thanksgiving, Christmas, etc.
  
### Data Pre-Processing
* label or one-hot encode categorical fields
* any fields need to be normalized/standardized?
* *insert solution* to handle those missing values
* any additional cleaning I run into as I'm working with the data
* split into train and test sets
* *might need another ML model* but parse the cuisine type based on class description if I can't find a cuisine column

### Run Model
I'll take a look at 4 different types of models:
1. Linear Regression
2. (S)ARIMA: (Seasonal) Autoregressive and Moving Average
3. LSTM: Long Short-Term Memory
4. LightGBM

[Source of ✨Inspiration✨](https://dataconomy.com/2022/11/25/time-series-forecasting-machine-learning/)

### Hyperparameter Tuning
use `sklearn.model_selection.GridSearchCV` on the best model from previous section.





