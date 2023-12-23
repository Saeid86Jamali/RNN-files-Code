# Recurrent Neural Network Time Series Forecasting with Dynamic Lag Identification
Initialization:

The code starts by importing the necessary libraries:

collections: Used for creating a deque object to store data for dynamic finding.
numpy: Used for numerical operations.
pandas: Used for reading and manipulating data.
keras: Used for building and training RNN models.
sklearn: Used for data preprocessing and splitting.
matplotlib: Used for plotting the autocorrelation function.
Dynamic finding:

The dynamic_finding function takes a time series data set as input and uses its autocorrelation function to identify the appropriate lag for forecasting. The function takes the following arguments:

data: The time series data set.
max_lag: The maximum lag to consider. If not specified, it defaults to the length of the data set minus 1.
th: The threshold value for determining the autocorrelation cutoff point.
mode: The mode of calculation, either 'unbiased' or 'biased'.
The function calculates the autocorrelation of the data at each lag and stores it in a deque. It then flips the deque and appends the autocorrelation values to the end of the deque. Finally, it plots the autocorrelation function, draws two horizontal lines at the threshold values, and shows the plot.

Sequence generation:

The sequence_making function creates sequences of data points from the original time series data set. The function takes the following arguments:

sequence: The original time series data set.
n_step: The number of data points in each sequence.
The function iterates through the data set, creating a sequence of n_step data points for each time step. It appends the sequence to two deques: X and y. X stores the sequences of data points, and y stores the corresponding values at the next time step.

Data loading:

The code reads the time series data set from an Excel file named Data.xlsx. It then scales the data using MinMaxScaler to a range of -1 to 1.

Examine dynamic finding:

The code calls the dynamic_finding function to identify the appropriate lag for forecasting. It sets the threshold value to 0.6.

Test train splitting:

The code divides the data into training and testing sets using scikit-learn's train_test_split function. It sets the test size to 30% of the data set.

Modeling using vanilla recurrent neural network:

The code builds a vanilla RNN model using Keras. The model consists of two layers:

A SimpleRNN layer with 10 units and tanh activation.
A Dense layer with a single unit and linear activation for the output prediction.
The model is compiled using the Adam optimizer, mean squared error (MSE) as the loss function, and MSE as the metric for evaluating the model's performance.

Fitting the model:

The code trains the RNN model on the training data. It sets the number of epochs to 100, the batch size to 5, and uses the validation data to monitor the model's performance.
