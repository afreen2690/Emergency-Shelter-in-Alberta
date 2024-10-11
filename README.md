# Emergency Shelter Capacity Prediction Project

## Project Overview
The goal of this project is to develop a predictive model to assess the capacity of emergency shelters in Alberta using a combination of economic, weather, and demographic data. This predictive model will help identify whether future emergency shelters will have adequate capacity based on historical data and relevant factors.

## Questions Addressed

### Question 1: Data Ingestion and Storage
#### Data Sources
1. **Emergency Shelter Capacity Data**: Obtained using the OpenAlberta API in CSV or JSON format.
2. **Economic Data**: Sourced from Statistics Canada, including GDP, CPI, and Unemployment Rates.
3. **Weather Data**: Retrieved via Python code from the Government of Canada website, containing climate stations and historical weather data.
4. **Demographic Data**: Collected through surveys or data provided by Statistics Canada.

#### Tools and Technologies
- **AWS Platform**: Used for data storage and computational services to support our online dashboard.
- **Python**: Employed for data cleaning, ingestion, and manipulation.
- **Streamlit**: An interactive web application for displaying the dashboard to external users.

### Data Processing and Storage Pipeline
The data ingestion and storage pipeline will be structured as follows:

1. **Data Ingestion**:
   - Fetch Emergency Shelter Capacity Data from OpenAlberta API.
   - Retrieve Economic Data from Statistics Canada API.
   - Collect Weather Data using weather station IDs and fetching historical data from 2013 to 2023.
   - Optionally collect Demographic Data from Statistics Canada.

2. **Process Flow**:
   - **Data Transformation**: Transform fetched data into suitable formats using the Pandas library.
   - **Storage in DynamoDB**: Use DynamoDB to store project objects, including images and tables, and enable querying.
   - **Lambda Functions**: Implement Lambda to forecast future emergency shelter capacities using a pre-trained model.
   - **Docker**: Set up a Docker environment to rerun the statistical model.
   - **Model Training and Deployment**: Train the logistic regression model using combined data, deploying it for predictions.
   - **CloudWatch**: Monitor the execution of each stage of the pipeline.
   - **Streamlit**: Display the dashboard interactively to users.

### Question 2: Economic Data Retrieval
We utilized the `stats_can` library to obtain economic data, focusing on selecting specific variables. The process involves:
- Searching for variable IDs (vectors) and fetching metadata such as description, unit of measure, and update frequency.
- Transforming JSON files to DataFrames and adjusting the layout to match vector IDs with corresponding metadata.
- For GDP data, we processed 1506 variables, retrieving data for two years within 1 minute and 36 seconds.
- Plans to isolate specific variables for historical data to improve efficiency and prevent unnecessary data retrieval.

The weather script employs Pandas, NumPy, Matplotlib, and Streamlit to process and visualize emergency shelter occupancy and climate data. After cleaning, it retrieves relevant climate station data, generating URLs for data fetches, and adding temperature columns to the shelter dataset. A logistic regression model predicts shelter capacity status based on temperature.
