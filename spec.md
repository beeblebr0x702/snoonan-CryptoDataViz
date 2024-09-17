# Cryptocurrency Market Data Visualization Project Specification

https://github.com/beeblebr0x702/snoonan-CryptoDataViz.git

## General Description

The Cryptocurrency Market Data Visualization project is a Python-based application designed to provide insightful and interactive visualizations of historical cryptocurrency market data. This tool aims to assist crypto traders, enthusiasts, and financial analysts in understanding market trends, patterns, and performance of various cryptocurrencies over time.

The application will leverage the CoinGecko API (https://www.coingecko.com/en/api/documentation) to fetch historical market data for a wide range of cryptocurrencies. Users will have the flexibility to select specific cryptocurrencies, time frames, and visualization types to suit their analysis needs. The core functionality will include generating candlestick charts, moving averages, heatmaps, and time-series graphs.

For data processing and visualization, the project will utilize popular Python libraries such as pandas for data manipulation, and matplotlib or plotly for creating interactive and aesthetically pleasing charts. The application will be developed primarily as a Jupyter Notebook, allowing for an interactive and exploratory user experience.

While the initial implementation will focus on a Jupyter Notebook interface, the project has the potential to evolve into a web-based application using frameworks like Dash or Streamlit, which would provide a more user-friendly GUI. In its current form, users will interact with the notebook cells to input parameters and generate visualizations.

As for remote control capabilities, the project could be extended to offer a simple API endpoint that accepts parameters and returns visualization data, allowing for integration with other applications or services.

## Task Vignettes (User Activity Flow)

### 1. Data Retrieval and Selection

Sarah, a crypto enthusiast, opens the Jupyter Notebook and runs the initial cells to import necessary libraries and set up the environment. She then encounters a cell where she can input her desired parameters:

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

Technical details:
- Visualization is created using the `plotly` library for interactive charts
- Candlestick data is formatted from the DataFrame
- Moving average is calculated using pandas' rolling window functions
- Chart is rendered inline in the notebook with zoom and pan capabilities

### 3. Multi-Cryptocurrency Analysis

Intrigued by Bitcoin's performance, Sarah wants to compare it with Ethereum. She modifies the input cell:

```python
cryptocurrencies = ["bitcoin", "ethereum"]
chart_type = "line"
start_date = "2023-01-01"
end_date = "2023-12-31"
```

After running the cells, a line chart appears showing the price trends of both Bitcoin and Ethereum over the specified period.

Sarah then decides to explore the correlation between multiple cryptocurrencies. She changes the chart type:

```python
cryptocurrencies = ["bitcoin", "ethereum", "cardano", "solana", "polkadot"]
chart_type = "heatmap"
```

The notebook generates a heatmap visualizing the correlation between the selected cryptocurrencies.

Technical details:
- Multiple API requests are made to fetch data for different cryptocurrencies
- Data is aligned and normalized for comparison
- Correlation matrix is calculated using pandas
- Heatmap is generated using seaborn or plotly

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
   - Clean and format data (handle missing values, convert timestamps)
   - Calculate additional indicators (e.g., moving averages)

4. Visualization Generation:
   - Select appropriate plotting function based on chart type
   - Prepare data for chosen visualization
   - Create plot using plotly or matplotlib
   - Add interactive elements (zoom, hover tooltips)

5. Output Display:
   - Render plot in Jupyter Notebook
   - Provide options for saving or exporting the visualization

Data Types:
- User Inputs: Strings and Lists
- API Response: JSON
- Processed Data: pandas DataFrame
- Visualization Data: plotly Figure object

Data Flow:
User Input -> API Request -> JSON Response -> DataFrame -> Processed DataFrame -> Visualization Object -> Rendered Plot

[A simple flow diagram could be included here to visually represent the data flow]

Key Components:
- Input Handler: Manages user inputs and parameter validation
- API Client: Handles communication with the CoinGecko API
- Data Processor: Cleans and formats the retrieved data
- Indicator Calculator: Computes additional market indicators
- Visualization Generator: Creates the requested chart types
- Output Manager: Handles the display and export of visualizations

User Interaction Points:
- Input cells for parameter selection
- Interactive plots for data exploration
- Optional: Widgets for dynamic parameter adjustment (if implementing with ipywidgets)

This technical flow provides a high-level overview of the application's structure and data processing pipeline. It can serve as a starting point for implementing the project, with each component being developed as a separate module or class to maintain a clean and modular codebase.
