# IE534-Project

## Group Members

1. Duo Zhou	
2. Jialin Liu	
3. Mingxuan Cui
4. Ray Fang	

## Github Address

https://github.com/Lemutisme/IE534-Project

## Project Background

For over a hundred years, everyone has wanted to move to California. California is by far the most populous and economically developed state in the United States. Whether it's tech, art, science, or cooking, by the turn of the century, the "Golden State" looks set to be the global center from north to south, and it seems like the best place in America to start over.

Naturally, California became the top destination for UIUC freshmen, and many were lured by the allure of the Golden State and decided to give up everything and go to Silicon Valley to find new jobs. However, it's one thing to have a steady job before making such a move, and it's another to have a backup set of jobs in case anything goes wrong with the current job.

The purpose of our group's project is to use data to predict California's employment rate over the next decade. Such predictions could be useful to future Californians, California lawmakers, or California citizens looking to leave or stay in the state. We might use some new feature engineering and use many different models to make predictions on employment data.

## Main Objectives

    - To collect data of estimations of total employment and unemployment in California state that is maintained monthly by the government, and perform cleaning, filtering, and normalization on the data.
    
    - To train some benchmark regression classifiers to predict the California unemployment rates and observe patterns and insights on the data.
    
    - To train an RNN model to predict the future employment rates in different regions in California for a higher accuracy.

## Milestones

### Milestone 1:
1. Construct Google Folder.
2. Download data and create Debugging dataset and Working dataset.
3. Convert these datasets to pandas and create pickle for use
4. Make a README.md file
5. Stating a MIT license

### Milestone 2:

1. visualization of the data and some descriptive statistics. 
2. Carry out a linear regression model as a benchmark
3. Carry out 2 time series model, ARIMA and Prophet as a benchmarks.

### Milestone 3: 
1. Build a deep learning model for the dataset
2. Investigate effects of mini-batch learning
3. Investigate effects of different optimizers
4. Tune hyperparameters

### Milestone 4: 

1. Feature Importance
2. Conclusions
3. Documentation and cleanup of files
4. Conversion to repo
5. Video summary of project.

## Data Sources

This project is based on the Local Area Unemployment Statistics (LAUS) dataset (https://data.ca.gov/dataset/local-area-unemployment-statistics-laus/resource/b4bc4656-7866-420f-8d87-4eda4c9996ed) managed by the California Open Data Portal. 

## Data Descriptions

### Local Area Unemployment Statistics (LAUS) dataset:

Up to 2022/11/1, there are 192,180 entries of employment data span from January 1976 to September 2022. 

The dataset has 12 columns: ID, Area Type, Area Name, Date, Year, Month, Seasonally Adjusted (Y/N), Status (Preliminary/Final), Labor Force, Employment, Unemployment, Unemployment Rate.

## Methodologies

In the preprocessing step, we first converted the datetime data in the Date column to Pandas timestamps, which will allow for time deltas and time manipulations. We also pulled out 2000 rows of data as our debug dataset.

Using the original data, we generated some descriptive charts to look for some patterns in California employment. For example, a bar chart of the average unemployment rates of California counties over the past 45 years.

We carried out a linear regression benchmark to see if we can explain the past unemployment rates with a straight line. We filtered out the columns that have a "Y" value for "Seasonally Adjusted" column and "Preliminary" for the "Status" column, since these data can be regarded as outliers that will negatively affect the performance. We one-hot-encoded the categorical values like the "Month" column, and normalized the numerical values. 

We trained and fit a linear regression model. The model gave an R-squared score of 0.06, and RMSE of 0.02.

We trained a few models that utilize time series to aim at a higher accuracy. At the data preprocessing step, we removed all unnecessary features and only left with date and unemployment rate, for a dedicated time series analysis. One of the methods we tried was to implement an ARIMA model to forecast our time series. We also tried to use a prophet model. The prophet model predicts that the unemployment rate is likely to increase in the future 10 years. The loss of the prophet model is relatively low, meaning that the estimations we made are pretty close to actual values.

Finally, we used the LSTM implementation of the RNN model and tried with three different loss functions for the model. LSTM stands for Long short-term memory. Unlike ARIMA and Prophet, LSTM networks are not restricted to time series. One of the difficulties we faced while training the LSTM models was that the network requires very careful tuning of its hyperparameters For example, we have to carefully tune the number of LSTM cells, as too many cells will lead to overfitting.

We tried three loss functions with the model to increase the accuracy of the predictions. One is SGD, or Stochastic Gradient Descent. One is Adam, and the other one is Adagrad. Among the three optimizers, Adagrad gave us the lowest RMSE score, meaning that it has the best predictions. But overall speaking, the LSTM models perform better than the prophet model.


## License

MIT License

Copyright (c) 2022 Group 26

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
