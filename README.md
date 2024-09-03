# Tech-Stocks-Market-Analysis-and-Prediction #
The provided code is a comprehensive Python script that performs an analysis of various tech stocks. Below is a detailed description of each section of the code:

1. Data Collection and Preparation:

The code starts by defining a list of technology companies' stock tickers (tech_list) such as Google (GOOG), Microsoft (MSFT), Amazon (AMZN), etc.
It then retrieves historical stock data for the last two years for each company using the yfinance library (yf.download). The data is stored in variables named after each ticker symbol (e.g., GOOG, MSFT).
After retrieving the data, the script adds a column called "company_name" to each DataFrame, labeling the data with the respective company name (e.g., "GOOGLE", "MICROSOFT").

2. Exploratory Data Analysis:

For each company, the script prints general information about the stock data (company.info()) and descriptive statistics (company.describe()).
The script calculates the global minimum and maximum adjusted closing prices across all companies to ensure consistency in the visualizations.

3. Interactive Visualizing: Interactive graphs are implemented which cannot be rendered using github compiler. Using interactive graphs helps in getting precise values and improves insights.
   a. Closing Prices:

The script creates subplots for the adjusted closing prices of each company using the plotly library. Each subplot displays the closing prices over time, with consistent y-axis ranges.

  b.  Trading Volume:

Another set of subplots is generated to visualize the trading volume of each company. These subplots are also created using plotly, with x-axes labeled as "Date" and y-axes labeled as "Sales volume".

5. Moving Averages:

The code calculates moving averages (10-day, 20-day, and 50-day) for each stock's adjusted closing prices. These moving averages are added as new columns to each company's DataFrame.
The moving averages and adjusted closing prices are plotted using Matplotlib in subplots, allowing for easy comparison across different companies.

6. Daily Returns Analysis:

The script calculates the daily returns for each stock by taking the percentage change of the adjusted closing prices.
Interactive Subplots are created to visualize these daily returns, displayed as dashed lines with markers for better insights.

7. Histogram of Daily Returns:

The script generates histograms for the daily returns of each company, providing a  Interactive visual representation of the distribution of returns.

8. Correlation Analysis:

The code retrieves the adjusted closing prices for all the tech stocks in a single DataFrame (closing_df) and calculates the percentage change to get the daily returns (tech_rets).
A pairplot and a pair grid are used to visualize the relationships between the daily returns of different companies. The upper triangle of the grid contains scatter plots, the lower triangle shows KDE plots, and the diagonal shows histograms.
Finally, two heatmaps are created to visualize the correlation matrices: one for the daily returns and one for the closing prices, providing insights into the relationships between different stocks.

9. Risk vs. Expected Return Scatter Plot:

The code calculates the standard deviation (risk) and mean (expected return) of the daily returns for each stock.
It then creates an interactive scatter plot using plotly to visualize the relationship between risk and expected return.
The plot is enhanced with custom marker sizes based on the squared standard deviation (to emphasize risk differences) and a color scale to represent the expected return-to-risk ratio and provide better insights of each stock.
The layout is adjusted for clarity, with hover templates providing detailed information for each stock.

10. LSTM Model for Stock Price Prediction Using Target Value Only:

The first predictive model in the script focuses on forecasting future stock prices using only the historical closing prices of each stock.
Approach:
This model exclusively uses the closing price (the target variable) to identify patterns within a rolling window of 60 days. It relies on the inherent temporal patterns within the closing prices to make predictions.
Model Architecture:
The model consists of LSTM layers, well-suited for capturing sequential dependencies in time series data. However, since it only uses the target variable, its ability to model more complex relationships is limited.
Outcome:
The model performs reasonably well for predicting future prices based on past trends, but it might miss out on potential insights that could be derived from other related features.

11. Enhanced LSTM Model Using Multiple Features:

The second predictive model improves upon the first by incorporating all available features, not just the target variable (closing price).
Approach:
In addition to the closing price, this model utilizes various other features (e.g., trading volume, other technical indicators) that could influence stock prices. By considering multiple features, the model can capture both linear and non-linear relationships between the features and the target variable.
Model Architecture:
This enhanced LSTM model is still designed to recognize temporal dependencies, but it now leverages a richer dataset to make more informed predictions. The inclusion of additional features allows the model to detect more complex patterns that go beyond what can be identified from the closing price alone.
Outcome:
By using a broader set of features, this model is generally more accurate in its predictions, as it accounts for a wider range of factors that can influence stock prices.

12. Function to Prepare and Train a Model:
The prepare_and_train_model function generalizes the LSTM model training process, making it reusable for different datasets and predictive scenarios:
Feature and Target Preparation:
The function separates features from the target variable (closing price) and scales them. It then prepares the dataset for time series prediction using the specified time_steps.
Train-Validation-Test Split:
The data is split into training, validation, and test sets to ensure proper model evaluation.
Model Training:
The model is trained with the training set, and its performance is validated using the validation set. Finally, it is evaluated on the test set.
Prediction and Visualization:
The model's predictions are rescaled to the original price scale, and the results are plotted against the actual prices for comparison.

13. Iterative Model Training for Each Company:

The script iterates over each company, applies the prepare_and_train_model function, and prints out the results.
This approach enables a systematic analysis of each company's stock, providing both a predictive model and a visual comparison of predicted vs. actual stock prices.

14. Summary:
The extended code builds upon the initial analysis by incorporating two approaches to predictive modeling. The first approach uses only the historical closing prices, focusing on identifying patterns within the target variable itself. The second approach enhances prediction accuracy by including multiple features, allowing the model to capture both linear and non-linear relationships.
The use of LSTM networks, which are particularly suited for time series forecasting, enables the models to make predictions based on historical data. The enhanced model, with its ability to consider a broader set of influencing factors, generally provides more accurate and insightful predictions.
The code is modular and flexible, with functions that allow for the application of different datasets, and it includes comprehensive visualizations to aid in the interpretation of results.
This explanation highlights how the second, more feature-rich model provides a better prediction by leveraging the full set of available data, rather than relying solely on the target variable.
