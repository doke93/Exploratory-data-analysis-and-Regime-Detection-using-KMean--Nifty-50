
# Exploratory data analysis and Regime Detection using KMean- Nifty-50

The goal of this project is to look at the NIFTY-50 data as well as the sectoral indices and visualise them in order to acquire useful information.
Also, use the scikit learn python library's Kmean (unsupervised learning model) to find regimes.


## Exploratory data analysis

- Visualization market performance 2019 onwards using plotly python library

![App Screenshot](https://user-images.githubusercontent.com/69301816/153367710-ce8d04c9-67d2-4ac5-8357-43d9cb5bf2a2.PNG)

- Major single day fall

![App Screenshot](https://user-images.githubusercontent.com/69301816/153368090-70065e22-48b0-4ef7-8d9d-86cddaca3ba5.PNG)

- Major single day gain

![App Screenshot](https://user-images.githubusercontent.com/69301816/153368679-4c5e864e-26c1-4422-b15b-e817709b0a31.PNG)

- Box plot - Closing price of different indices

![App Screenshot](https://user-images.githubusercontent.com/69301816/153369216-109e6527-32ec-4727-b437-a052b02e3700.PNG)



## Regime Detection - Using unsupervised learning algorithm
### Use of Regime Detection in finance
- To determine which trading model or trading strategy to execute at any particular time, we use regime detection.

-Importing KMeans from scikit learn python library

````
from sklearn.cluster import KMeans
````

- Creating Volatility and Momemtum feature


````
window = 20
data['mom'] = data[symbol].rolling(window).mean()
data['vol'] = data[symbol].rolling(window).std()
````

- Scale the dataset to improve the model's performance
````
data = (data - data.mean())/data.std()
````

- Scatter plot of Momemtum vs Volatility
![App Screenshot](https://user-images.githubusercontent.com/69301816/153371068-e6c5ac98-187a-4389-9bbc-01cfb65f13f4.PNG)

- Implementing KMeans for detecting clusters

````
f = ['mom', 'vol']
model = KMeans(n_clusters=4)
model.fit(data[f])
cluster = model.predict(data[f])
````
- Plotting cluster detected by KMeans model

![App Screenshot](https://user-images.githubusercontent.com/69301816/153381014-824b9e7e-4606-43e7-a892-7ab078e37f66.PNG)

### Regime detected by the model
- Positive Momentum and low Volatility
- Positive Momentum and high Volatility
- Negative Momentum and high volatility
- Negative Momentum and low volatility


