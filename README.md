# CryptoCurrencyPrediction-FbProphet
The key advantage of this project is that the prophet library allows prediction of not only 1 coin but multiple alt coins such as BTC-USD","ETH-USD","ADA-USD","XRP-USD","SOL.USD","MATIC-USD","LINK-USD", "FTM-USD", "LTC-USD”. This means multiple datasets will be used each time the user chooses a coin to achieve his desired goals of predictions.
# DataSet Exploration 
![Screenshot (105)](https://user-images.githubusercontent.com/88887839/156530654-f9b5e9e5-46b2-4ae3-9cf1-04c49ce99d15.png)

In the above figure the user chose bitcoin as an alt coin to start his prediction with and he wants to forecast one year ahead. Accordingly, the data is being loaded successfully and displayed on the screen. The start date is from 2015-01-01 and the current date will be the date the user trying to forecast. So, the last 5 rows were displayed on the screen using the .tail method

# Loading the dataset

Now, to load the dataset a function load_data passing to it a positional argument is created. Then a variable called data is declared and is initialized to the datasets that are found in yfinance package where all the needed alt coins that were used in this project are found in this package. Moreover, the date column is needed for the prophet model, so to make sure it’s one of the columns that is listed we did reset our indexes so surely the Date will be now from the columns. The good part about stream lit library is the caching mechanism it possesses. Since manipulation of large datasets is done here and loading of data from web so a number of huge computations is performed. So, to preserve the performance a decorator @st.cahce is used.

A code snippet of this function is shown below:

![Screenshot (106)](https://user-images.githubusercontent.com/88887839/156532270-7dc1b395-0811-4237-be4d-b88fa3507d4f.png)

# DataSet Columns:
Now checking the columns of the dataset after the implementation of reset_index method:

![Screenshot (117)](https://user-images.githubusercontent.com/88887839/156533411-ef882139-a8a0-4794-ae3c-0f5f643b16e3.png)

It appears that data column is in the list of indexed columns. 

# Visulization of the dataset: 
Visualizing the data would be considered a good practice to check and compare between the opening and closing of a certain bitcoin in terms of time. The below figure is plotted using the pyplot library.

A zoomed out version that shows the fluctutations over the years.

![Screenshot (108)](https://user-images.githubusercontent.com/88887839/156534045-7b06a346-a949-44ac-b589-4e5d857fa827.png)

A zoomed in version that shows the fluctuations over the months:

![Screenshot (109)](https://user-images.githubusercontent.com/88887839/156534278-066ab8af-e049-43fb-b7fc-dc030d2841ab.png)

And finally a more zoomed in figure over the recent days:

![Screenshot (110)](https://user-images.githubusercontent.com/88887839/156534747-002f0ec8-07d3-4826-82ae-040104e48536.png)

# Preparing the Prophet Model: 
The prophet has some limitations where it requires only to have 2 columns and in this case: the date and the close columns are the 2 columns needed. So, these 2 columns will be collected and put in a new data frame and the rename function is used to change the name of the columns following the correct name conventions. Again the .tail method is used to check the new data.

![Screenshot (111)](https://user-images.githubusercontent.com/88887839/156534860-67a1e4e8-9ccc-4f92-8004-c4fea7623365.png)

# Prophet Model

To forecast the values of the time series data in the future the prophet library should be applied now. A new Prophet object called m, a lot of arguments can be specified using prophet but the interval_width is used here that follows the concepts of confidence interval which is a set of estimates for an unknown parameter that's defined as an interval with a bottom and upper bound. The 95% confidence level is most common so 0.95 is used for the interval width. After the Prophet model has been used, fit method with the new data frame as input is being utilized. To get forecasts for this time series, the prophet shall have a new data frame with a ds column containing the dates. Prophet has a handy method called make future data frame which is a helper functions that completes the job. A period is passed which refers to the timestamp where in this case the number of years chosen by the user will be multiplied b 365 days so the make_future_dataframe will generate daily timestamps based on the user choice of prediction. The data frame with future dates is subsequently passed to the fitted model's forecast method.

The output would be: 

![Screenshot (115)](https://user-images.githubusercontent.com/88887839/156535478-74a9c9ea-3e5f-4b31-908f-4d0fe04cbc41.png)

# Prophet Plots: 

![Screenshot (116)](https://user-images.githubusercontent.com/88887839/156535989-d6b6d9b3-35fb-4135-8438-ea3e6f1ab328.png)


