# Forex-Machine-learning-model
using deep learning to predict price changes in Forex. This is because, deep learning has shown promising results in predicting financial time series data, including Forex.



<b>Here are the general steps you can follow to develop a deep learning model for predicting Forex prices and make it available to users through a frontend platform:</b>

- <b>Data Collection and Preparation:</b> The first step is to gather the relevant data for your project. You will need to collect historical Forex price data, along with other relevant features that could impact the price movements. This data can be obtained from various sources, including financial APIs or Forex data providers. Once you have collected the data, you will need to preprocess it by cleaning, transforming, and normalizing it to make it suitable for deep learning.

- <b>Model Development: </b>After data preparation, you can start building your deep learning model. The type of model you choose will depend on the problem you are trying to solve. For example, you can use recurrent neural networks (RNNs) or convolutional neural networks (CNNs) to model the sequential and time series nature of Forex data. You can also use hybrid models that combine different types of networks to achieve better results.

- <b>Training and Evaluation:</b> Once your model is developed, you can train it on the prepared data. During training, you will adjust the model's weights and biases to minimize the prediction error. After training, you will evaluate the model's performance using various metrics such as Mean Squared Error (MSE) or Root Mean Squared Error (RMSE).

- <b>Integration with a Frontend Platform:</b>After developing and testing your model, you can integrate it with a frontend platform to make it accessible to users. You can use a web development framework such as Flask or Django to build an API for your model, which can handle user requests and return predictions. You can also develop a web application that interacts with your API to display the predictions to users.

- <b>Deployment and Maintenance:</b> Once your model is integrated with a frontend platform, you can deploy it on a web server or a cloud-based platform such as AWS or Google Cloud. You should also consider ongoing maintenance and updates to ensure that the model remains accurate and up-to-date.


# Sources of Data

There are various sources where you can obtain Forex data, both free and paid. This is the dataset i will be using. <a href="https://github.com/Code-with-jaycee/Forex-Machine-learning-model/blob/main/DAT_XLSX_EURUSD_M1_202301.xlsx">Forex data</a>. Some of the popular sources are : 

1. <b>Forex Data Providers:</b> There are many data providers that offer Forex historical and real-time data, including Oanda, Alpha Vantage, and Quandl. These providers offer APIs that you can use to fetch the data programmatically.

2. <b>Financial News Sources:</b> Financial news sources such as Bloomberg, Reuters, and CNBC can provide Forex data, including economic indicators, news events, and announcements that can affect currency prices.

3. <b>Central Banks:</b> Central banks often publish Forex data, including exchange rates, monetary policy statements, and interest rates. You can access this data through the central bank's website or API.

4. <b>Open Data Repositories:</b> There are various open data repositories that offer Forex data, such as the World Bank's Data Catalog or Kaggle.

When collecting Forex data, it is essential to ensure that the data is accurate, complete, and timely. You will also need to ensure that the data is in a format that can be easily processed and analyzed. Once you have obtained the data, you will need to preprocess it by cleaning, transforming, and normalizing it to make it suitable for deep learning.



# Here are some platforms where you can download Forex data for free:

1. <b>HistData:</b> <a href="https://www.histdata.com/download-free-forex-data/">HistData</a> provides free historical Forex data for different currency pairs and timeframes. You can download the data in CSV format, and it includes features such as open, high, low, and close prices, as well as volume data.

2. <b><a href="https://www.forexite.com/traderoom/">Forexite:</a></b> Forexite offers free Forex historical data for various currency pairs and timeframes. The data is available in CSV format, and it includes bid and ask prices, as well as other features such as the opening and closing times for each trading session.

3. <b><a href="https://www.investing.com/">Investing.com:</a></b> Investing.com provides free Forex historical data for various currency pairs and timeframes. The data is available in CSV format, and it includes features such as open, high, low, and close prices, as well as volume data.

4. <b><a href="https://www.kaggle.com/datasets">Kaggle:</a></b> Kaggle hosts many publicly available datasets, including Forex data. You can search for Forex data on Kaggle and download the datasets in various formats.

Before downloading and using the data, make sure to read the license and terms of use of the data source to ensure that you can use it for your project. Additionally, as I mentioned earlier, make sure to clean, preprocess, and transform the data to make it suitable for deep learning.


# Here are some general steps you can follow to prepare the data for deep learning:

1. <b>Clean the data:</b> Forex data can have missing values, outliers, or other errors that can affect the performance of your deep learning model. Therefore, you will need to clean the data by identifying and removing or imputing missing values, handling outliers, and correcting errors.

2. <b>Normalize the data:</b> Forex data can have different ranges and scales, which can make it difficult for deep learning models to learn. Therefore, you will need to normalize the data to ensure that all features have similar ranges and scales. Common normalization techniques include standardization and min-max scaling.

3. <b>Reshape the data:</b> Deep learning models typically require the data to be in a specific shape, such as a time series or a sequence. Therefore, you may need to reshape the data to make it suitable for your deep learning model.

4. <b>Split the data into training, validation, and testing sets:</b> To evaluate the performance of your deep learning model, you will need to split the data into training, validation, and testing sets. The training set is used to train the model, the validation set is used to tune the hyperparameters, and the testing set is used to evaluate the final performance of the model.

5. <b>Create input and output sequences:</b> Depending on the deep learning architecture you choose, you may need to create input and output sequences from the data. For example, if you want to predict the next day's Forex prices based on the past ten days' prices, you will need to create a sequence of ten input data points and a single output data point.

These are some general steps you can follow to prepare the data for deep learning. However, the specific steps you need to take will depend on the requirements of your project and the deep learning architecture you choose.

# Step 1: Cleaning data

<h3>Imports</h3>

```
import numpy as np
import pandas as pd
```

```
data = pd.read_excel("forex_data.xlsx")
```
<h3> Adding columns</h3>
it's a good practice to assign column headings to the data. Column headings will make it easier for you and others to understand and work with the data, and it will help you to avoid errors when cleaning and preprocessing the data.

To assign column headings to the data, you will need to know what each column represents. Forex data usually contains the following columns:

- <b>Date:</b> The date and time of the Forex price.

- <b>Open:</b> The opening price of the Forex currency pair.

- <b>High:</b> The highest price of the Forex currency pair during the time period.

- <b>Low:</b> The lowest price of the Forex currency pair during the time period.

- <b>Close:</b> The closing price of the Forex currency pair.

- <b>Volume:</b> The trading volume during the time period.

You can assign these column headings to your data by creating a new row at the top of the data and filling in the column headings. For example, you can use the following column headings:

```
data.columns = ['Date', 'Open', 'High', 'Low','Close', 'Volume']

# Save the updated Dataframe to a new CSV file
data.to_csv('forex_data.csv', index=False)
```

Lets load our updated dataset.
```
data = pd.read_csv("forex_data.csv")
```

Make sure to assign the correct column headings to each column to ensure that the data is correctly interpreted and used in your deep learning model.


# Checking For missing values
Check if there are any missing values in the data and decide how to handle them. You can either remove the rows with missing values or impute the missing values with appropriate techniques such as mean or median imputation.<br>
In our case we will use the mean

```
if data.isnull().values.any():
    data = data.fillna(data.mean())
```

# Checking for Duplicates.
Check if there are any duplicate rows in the data and remove them if necessary.

```
if data.duplicated().values.any():
    data= data.drop_duplicates()
```
<hr>

# Remove outliers from the 'Close' column using z-score
Next, we remove outliers from the 'Close' column using z-score, where any data point that lies outside 3 standard deviations from the mean is considered an outlier and removed.

```
data = data[(data['Close'] - data['Close'].mean())/ data['Close'].std() < 3]
```

# Step 2: Normalize the data usng StandardScaler
Finally, we normalize the data using StandardScaler by first initializing a StandardScaler object, and then applying it to the relevant columns using the fit_transform() method.

```
scaler = StandardScaler()
data[['Open', 'High', 'Low', 'Close', 'Volume']] = scaler.fit_transform(data[['Open', 'High', 'Low', 'Close', 'Volume']])
```

```
# Save the Cleaned DataFrame to a new CSV file
data.to_csv('Cleaned_forex_data.csv', index=False)
```


 # Step 3: Reshaping the dataset
In the case of time series data like Forex, the shape of the input data is very important. The input data should be a 3D array of shape (num_samples, sequence_length, num_features), where:

```num_samples``` is the number of samples in the dataset.
```sequence_length``` is the length of the input sequence that the model will process at once.
```num_features``` is the number of features in the input data.
This 3D array can be interpreted as a sequence of ```num_samples``` input sequences, each of length ```sequence_length``` and with ```num_features``` features.


```
# Read the cleaned data CSV file into pandas DataFrame
data = pd.read_csv("Cleaned_forex_data.csv")


# Define the sequence length
sequence_length = 50
```

```
# Create a function to reshape the data
def create_sequences(data, sequence_length):
    X = []
    y = []
    for i in range(len(data)-sequence_length-1):
        X.append(data.iloc[i:(i+sequence_length), 1:6])
        y.append(data.iloc[(i+sequence_length), 4])
    return np.array(X), np.array(y)

# Reshape the data
X, y = create_sequences(data, sequence_length)
```

# Step 4. Spliting the data into training, validation and test sets

```
# Split the data into training , validation and test sets
train_X, test_X, train_y, test_y = train_test_split(X, y, test_size=0.2, shuffle=False)
train_X, val_X, train_y, val_y = train_test_split(train_X, train_y, test_size=0.25, shuffle=False)


# Save the split data to an HDF5 file
with h5py.File('data.h5', 'w') as f:
    f.create_dataset('train_X', data=train_X)
    f.create_dataset('train_y', data=train_y)
    f.create_dataset('val_X', data=val_X)
    f.create_dataset('val_y', data=val_y)
    f.create_dataset('test_X', data=test_X)
    f.create_dataset('test_y', data=test_y)
```

This will create an HDF5 file named ```data.h5``` in write mode (```'w'```). It will then create six datasets within the file and save the corresponding arrays to them. You can then load the data from the HDF5 file using the ```h5py``` library. Here is an example of how to load the data:


# Load the data from the HDF5 file

```

with h5py.File('data.h5', 'r') as f:
    train_X = f['train_X'][:]
    train_y = f['train_y'][:]
    val_X = f['val_X'][:]
    val_y = f['val_y'][:]
    test_X = f['test_X'][:]
    test_y = f['test_y'][:]
```