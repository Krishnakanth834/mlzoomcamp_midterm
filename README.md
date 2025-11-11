# mlzoomcamp_midterm
Stock Price Prediction (Linear Regression)
Overview

This project performs Exploratory Data Analysis (EDA) and builds a Linear Regression model to predict same-day closing stock prices using basic numerical features derived from historical stock data.

The focus is on understanding relationships between features such as Open, High, Low, Volume and Close prices, and building a simple baseline model.

Technologies Used

Python
Pandas
NumPy
Matplotlib
Seaborn
Scikit-learn

Dataset

The dataset (APPL_Stock_Data - APPL.csv) contains the following columns:

date
open
high
low
close
volume

Data Preparation

Remove Duplicates
Duplicate dates (if any) are dropped to keep only unique daily entries.

Feature Engineering
Two new numerical features are derived:
df['daily_return'] = (df['close'] - df['open']) / df['open']
df['volatility_ratio'] = (df['high'] - df['low']) / df['close']

Feature Matrix Preparation
Only numeric columns are used for modeling.
Example function:

def prepare_X(df):
    df = df.copy()
    df['daily_return'] = (df['close'] - df['open']) / df['open']
    df['volatility_ratio'] = (df['high'] - df['low']) / df['close']
    features = ['open', 'high', 'low', 'volume', 'daily_return', 'volatility_ratio']
    df_num = df[features].fillna(0)
    X = df_num.values
    return X

Exploratory Data Analysis (EDA)

The following EDA steps were performed:

Checking missing values
Visualizing distributions (close, volume)
Plotting trends in stock prices
Checking correlations between features

Model Building
A Linear Regression model is trained to predict the same-day close price.

Results:

Evaluation Metric: Root Mean Squared Error (RMSE)
Example Result: RMSE = 1.89
Indicates the model predicts same-day closing prices with reasonable accuracy given limited features.