# Cryptocurrency Market Data Visualization Project Specification

https://github.com/beeblebr0x702/snoonan-CryptoDataViz.git

## General Description

The app will display historical cryptocurrency market data to show trends, patterns, and performance of various cryptocurrencies over time.

It will use the  CoinGecko API (https://www.coingecko.com/en/api/documentation) to fetch historical market data for various cryptocurrencies. 

Users can select specific cryptocurrencies, time frames, and visualization types to suit their analysis needs.

It will use Python libraries such as pandas for data manipulation, and matplotlib or plotly for creating interactive charts. 

It will be developed primarily as a Jupyter Notebook

## Task Vignettes (User Activity Flow)

### 1. Data Retrieval and Selection

Sarah is interested in crypto but wants to learn more about it's performance over the years. She opens the Jupyter Notebook and runs the initial cells to import necessary libraries and set up the environment. She then encounters a cell where she can input her parameters:

```python
cryptocurrency = "bitcoin"
start_date = "2023-01-01"
end_date = "2023-12-31"
chart_type = "candlestick"
```

Sarah inputs her choices and runs the cell. The application then uses these parameters to fetch the relevant data from the CoinGecko API.

Technical details:
- API request is made using the `requests` library
- JSON response is parsed and converted into a pandas DataFrame
- Data is validated and cleaned to handle any missing values or inconsistencies

### 2. Data Visualization

After the data is retrieved and processed, Sarah runs the next cell to generate the visualization. The notebook displays a candlestick chart showing Bitcoin's price movement throughout 2023.

Sarah examines the chart, noticing key support and resistance levels. She decides she wants to add a 50-day moving average to the chart for additional insight. She modifies the parameters in the previous cell:

```python
chart_type = "candlestick"
indicators = ["MA50"]
```

She reruns the cells, and a new chart is generated with the moving average overlay.

Details for later:
- Visualization is created using the `plotly` library for interactive charts
- Candlestick data is formatted from the DataFrame
- Moving average is calculated using pandas' rolling window functions
- Chart is rendered inline in the notebook
- 
## Technical Flow

1. User Input Handling:
   - Collect user inputs (cryptocurrencies, date range, chart type)
   - Validate inputs

2. Data Retrieval:
   - Construct API URL based on user inputs
   - Send HTTP request to CoinGecko API
   - Receive JSON response

3. Data Processing:
   - Parse JSON data
   - Create pandas DataFrame
   - Clean and format data
   - Calculate additional indicators

4. Visualization Generation:
   - Select appropriate plotting function based on chart type
   - Prepare data for chosen visualization
   - Create plot using plotly or matplotlib

5. Output Display:
   - Render plot in Jupyter Notebook
   - Provide options for saving or exporting the visualization

Data Flow:
User Input -> API Request -> JSON Response -> DataFrame -> Processed DataFrame -> Visualization Object -> Rendered Plot
