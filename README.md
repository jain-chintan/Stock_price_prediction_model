README: Google Stock Price Prediction Using LSTM

Project Overview

This project implements a Long Short-Term Memory (LSTM) neural network model to predict Google's stock prices based on historical data. It preprocesses the data, trains an LSTM model, and then uses the model to predict future stock prices. The model is evaluated using the difference between actual and predicted stock prices, visualized through matplotlib plots.

Requirements

To run this project, you need the following Python libraries:

- numpy

- pandas

- matplotlib

- scikit-learn

- keras

- tensorflow

You can install the necessary packages by running:

    pip install numpy pandas matplotlib scikit-learn keras tensorflow

Dataset

This code works with two CSV files:

1.  Google_train_data.csv: Historical stock prices used for training the model.

2.  Stock_Price_data_set_(1).csv: Stock prices used for testing and validation.

Both datasets should have the following columns:

- Date

- Open

- High

- Low

- Close

- Volume

Data Preprocessing

The following steps are applied to prepare the data:

1.  Reading the CSV file: The historical stock price data is loaded using pandas.

2.  Handling missing values: Non-numeric values in the "Close" price column are coerced to NaN and dropped.

3.  Feature scaling: The "Close" price is normalized using MinMaxScaler to fit the data into a range between 0 and 1.

4.  Creating sequences: The data is structured into sequences of 60-day windows (timestep) to be used as input for the LSTM.

Model Architecture

A Sequential LSTM model is built using the Keras library. The architecture includes:

- Four LSTM layers: Each with 100 units. The first three layers return sequences for further LSTM layers, and the last one outputs a single value.

- Dropout layers: Each LSTM layer is followed by a 20% dropout to prevent overfitting.

- Dense layer: The final Dense layer outputs a single prediction (the next stock price).

The model uses Adam optimizer and mean squared error as the loss function. It is trained for 20 epochs with a batch size of 32.

Training the Model

The data is split into training and test datasets. For the training set, sequences of 60 previous stock prices are used as input (X_train), and the next stock price is used as the target (y_train). The model is trained over 20 epochs.

Predicting Stock Prices

Once the model is trained, it is used to predict stock prices on the test dataset. The test data is also scaled using MinMaxScaler and structured into sequences of 60 previous stock prices.

Inverse Transform and Visualization

The predicted values are transformed back to the original scale using the inverse of the MinMaxScaler. Both the actual and predicted stock prices are plotted for visual comparison.

Running the Code

1.  Prepare your environment by installing the required libraries.

2.  Place the datasets Google_train_data.csv and Stock_Price_data_set_(1).csv in the same directory as the script.

3.  Run the script. It will:

- Train the model using the historical data from Google_train_data.csv.

- Predict future stock prices from Stock_Price_data_set_(1).csv.

- Plot a comparison between the actual and predicted stock prices.

Output

- Training Loss Plot: A graph showing the loss over epochs during the training process.

- Prediction Plot: A graph comparing the actual stock prices and predicted stock prices for the test dataset.

License

This project is for educational purposes only and may not be used for actual trading. Use it at your own risk.
