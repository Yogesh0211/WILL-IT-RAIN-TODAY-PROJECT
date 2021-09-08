# WILL-IT-RAIN-TODAY-PROJECT

The objective of this project was to predict rain based upon historical weather data. This was approached as a binary classification problem, with the ultimate question being “Will it rain tomorrow?” answered by either a yes or no.

Multiple models were built to explore methods of predicting our response variable, RainTomorrow. Models include classification trees, random forests using k-fold validation, and developing a neural network. The naive accuracy (that is, how accurate predictions would be if we assumed the answer is always “yes”) was around 0.78. The procedures for this project were written in RStudio. The full R Markdown, dataset, and write-up are available on GitHub, and will be linked again at the bottom of this write-up.


The data provided includes dates from November 2007 to late-June 2017. This dataset includes 28,003 observations with 20 variables describing various factors. Variables include information such as wind speed, humidity, temperature, and cloud cover. Most variables are missing a number of values, so we’ll need to sanitize the data before proceeding. Phase one of this project will be preparing the data for analysis by eliminating or filling those missing values, then identifying potentially strong predictors of the “RainTomorrow” variable.

With over 28,000 observations, it’s not too surprising to see most variables are each missing at least a few values. the total missing can range widely from 64 “MaxTemp” values to over 11,341 missing values on cloud cover. Cloud9am and Cloud3pm suffer the most from missing data, with almost 40% of values missing. If we were to remove all observations with a missing value, our dataset size would reduce by half to 13,887 observations.

The dataset contains both categorical and quantitative variables, both of which have missing values. For simplicity, we’ll opt to eliminate any observations with missing categorical values. The following code checks for any missing, or “NA”, values in our categorical variables and eliminates the entire observation. Doing so reduces our dataset to 24,351 observations.
rain = rain %>% drop_na(WindGustDir, WindDir9am, WindDir3pm, RainToday, RainTomorrow)