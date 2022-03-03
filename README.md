# CryptoCurrencyPrediction-FbProphet
The key advantage of this project is that the prophet library allows prediction of not only 1 coin but multiple alt coins such as BTC-USD","ETH-USD","ADA-USD","XRP-USD","SOL.USD","MATIC-USD","LINK-USD", "FTM-USD", "LTC-USD”. This means multiple datasets will be used each time the user chooses a coin to achieve his desired goals of predictions.
# DataSet Exploration 
![Screenshot (105)](https://user-images.githubusercontent.com/88887839/156530654-f9b5e9e5-46b2-4ae3-9cf1-04c49ce99d15.png)

In the above figure the user chose bitcoin as an alt coin to start his prediction with and he wants to forecast one year ahead. Accordingly, the data is being loaded successfully and displayed on the screen. The start date is from 2015-01-01 and the current date will be the date the user trying to forecast. So, the last 5 rows were displayed on the screen using the .tail method

# Loading the dataset

Now, to load the dataset a function load_data passing to it a positional argument is created. Then a variable called data is declared and is initialized to the datasets that are found in yfinance package where all the needed alt coins that were used in this project are found in this package. Moreover, the date column is needed for the prophet model, so to make sure it’s one of the columns that is listed we did reset our indexes so surely the Date will be now from the columns. The good part about stream lit library is the caching mechanism it possesses. Since manipulation of large datasets is done here and loading of data from web so a number of huge computations is performed. So, to preserve the performance a decorator @st.cahce is used.

A code snippet of this function is shown below:
