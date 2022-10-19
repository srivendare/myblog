---
title: Playing yfinance with Pandas
author: "Rui"
categories:
- pandas, finance
date: 2022-07-20
---



Due to personal issue, I need to track Forex info recently. However, unlike professional trader, I don't need ticker for every minutes, but day by date is to rough. So this project is a simple `pandas` manuplation about `yfinance` API in python, the final aim is to build a FastAPI with `['morning', 'day', 'evening']`  avg forex data,



Let's start by import dependencies:

```python
# For data manipulation
import numpy as np
import pandas as pd

# To fetch financial data
import yfinance as yf
```



Get the data frame in API

```python
# Set the ticker as 'EURUSD=X'
forex_data_minute = yf.download('CADCNY=X', period='60d', interval='15m')

# Clear the index info with Api
forex_data_minute  = forex_data_minute.reset_index()

# Set date and hour from timestamp in API
forex_data_minute['hour'] = pd.to_datetime(forex_data_minute['Datetime']).dt.hour
forex_data_minute['date'] = pd.to_datetime(forex_data_minute['Datetime']).dt.date

```



Next step is the core part, which used `pd.cut` method to create bins

```python
# Provide bin& lebals info
bins = [0, 12, 18, 24]
labels = ['Morning', 'Day time', 'Evening']

# Make bin info within dataframe
from numpy import average
forex_data_minute['day_time'] = pd.cut(x=forex_data_minute['hour'], bins= bins, labels=labels, include_lowest =True)

# Aggregate final results
forex_data_minute.groupby(['date','day_time']).agg({'Adj Close': average })
```



Next step make a function for creating a FastAPI ...
