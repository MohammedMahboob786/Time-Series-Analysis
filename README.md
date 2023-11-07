 # Time Series Analysis Using LSTM


This GitHub repository contains a Jupyter Notebook for time series prediction using Long Short-Term Memory (LSTM) neural networks. The script loads temperature data, preprocesses it, builds an LSTM-based model, trains the model, and makes predictions. Here's a step-by-step explanation of the code:

## Table of Contents
1. [Importing Libraries](#importing-libraries)
2. [Downloading and Extracting Data](#downloading-and-extracting-data)
3. [Reading Data](#reading-data)
4. [Data Preprocessing](#data-preprocessing)
5. [Data Visualization](#data-visualization)
6. [Data Transformation](#data-transformation)
7. [Data Splitting](#data-splitting)
8. [Model Definition](#model-definition)
9. [Model Compilation](#model-compilation)
10. [Model Training](#model-training)
11. [Model Loading](#model-loading)
12. [Model Evaluation and Visualization](#model-evaluation-and-visualization)
13. [Model Validation](#model-validation)

---

## 1. Importing Libraries
- TensorFlow, a deep learning framework, is imported for model building and training.
- Other standard Python libraries like os, pandas, and numpy are imported for data handling and manipulation.

## 2. Downloading and Extracting Data
- The code uses `tf.keras.utils.get_file` to download a compressed ZIP file containing climate data (a CSV file) from a Google Cloud Storage URL.
- The ZIP file is extracted, and the path to the CSV file is stored in `csv_path`.

## 3. Reading Data
- The CSV data is read into a Pandas DataFrame using `pd.read_csv`.
- The DataFrame `df` contains various columns, including temperature data.

## 4. Data Preprocessing
- Some preprocessing is applied to the data:
  - The code selects every 6th row of the DataFrame, effectively downsampling the data to reduce the number of data points.
  - The index of the DataFrame is set to the parsed date and time from the "Date Time" column.

## 5. Data Visualization
- The code visualizes the temperature data using `temp.plot`. It shows a time series plot of temperature data.

## 6. Data Transformation
- A function `df_to_Xy` is defined to transform the time series data into sequences of input-output pairs.
- It takes a DataFrame (`df`) and a window size as input.
- The function creates input sequences (X) and corresponding output values (y) by sliding a window of the given size over the data.

## 7. Data Transformation
- The `df_to_Xy` function is applied to the temperature data, creating sequences of input (X) and output (y) pairs.
- `X` contains sequences of temperature values, and `y` contains the corresponding target values.
- The shape of `X` and `y` is printed.

## 8. Data Splitting
- The dataset is split into training, validation, and testing sets.
- `X_train` and `y_train` contain the training data and labels.
- `X_val` and `y_val` contain the validation data and labels.
- `X_test` and `y_test` contain the testing data and labels.

## 9. Model Definition
- A Sequential Keras model (`model1`) is defined.
- The model consists of an input layer, an LSTM layer with 64 units, a Dense layer with 8 units and ReLU activation, and a final Dense layer with a linear activation function.

## 10. Model Compilation
- The model is compiled with the mean squared error (MSE) loss function, the Adam optimizer with a specific learning rate, and the root mean squared error (RMSE) as a metric.
- A ModelCheckpoint callback is set up to save the best model during training.

## 11. Model Training
- The model is trained using the training data (`X_train` and `y_train`) and validated on the validation data (`X_val` and `y_val`) for 10 epochs.
- The best model is saved based on validation performance using the ModelCheckpoint callback.

## 12. Model Loading
- The trained model is loaded from the saved checkpoint.

## 13. Model Evaluation and Visualization
- The model is used to make predictions on the training and test data, and the results are stored in DataFrames.
- The training and testing results are visualized using Pandas plots.

## 14. Model Validation
- The model is used to make predictions on the validation data, and the results are stored in a DataFrame.
- The validation results are visualized using Pandas plots.

This code demonstrates a complete workflow for time series prediction using an LSTM-based deep learning model, including data preprocessing, model definition, training, and evaluation.

---
