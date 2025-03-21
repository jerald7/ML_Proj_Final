Machine Learning for HDB Price Prediction with Sentiment Analysis

Project Overview 

Buying a house in Singapore is a complex and expensive decision. This project leverages machine learning and sentiment analysis to predict HDB resale prices, incorporating location, property attributes, and public sentiment from online discussions.

By analyzing resale transaction data, geospatial features, and sentiment data, this project aims to:

  1. Provide a **data-driven valuation** of HDB flats based on historical trends.
  2. Incorporate **public sentiment analysis** to measure how location desirability impacts prices.
  3. Offer insights into **MRT accessibility and amenities** as key pricing factors.

Project Phases

The development process is divided into three main phases:

**Phase 1: Data Collection & Preprocessing**  
- Collect historical HDB resale transaction data.  
- Use OneMap API to retrieve geospatial data (MRT proximity, walking distance).  
⁃	- OneMap API Setup
	To fetch HDB coordinates and calculate walking routes to MRT stations, you must obtain an API key from OneMap.
	Step 1: Sign Up for OneMap API
⁃	Go to: OneMap API Registration
⁃	Sign up for an account and log in.
⁃	Navigate to "Generate API Token" and request a new key.
⁃	Copy your access token (a long alphanumeric string).
	Step 2: Add Your API Key to the Code
	Once you have your API token, insert it into your script:
		# Replace this with your actual OneMap API token
		ONEMAP_API_TOKEN = "your_api_key_here"

		# Initialize OneMap API
		onemap = OneMapAPI(ONEMAP_API_TOKEN)

- Scrape Reddit discussions to extract sentiment on housing and locations.  

**Phase 2: Feature Engineering & Model Training**  
- Perform feature selection (location, flat type, amenities, sentiment scores).  
- Train multiple regression models (Linear Regression, XGBoost, Deep Learning).  
- Validate models using RMSE, MAE, and R² scores.  

**Phase 3: Model Optimization & Evaluation**  
- Fine-tune hyperparameters using RandomizedSearchCV.  
- Apply ensemble learning techniques for better accuracy.  
- Generate insights on how sentiment scores influence pricing.  

Dataset and Files

The dataset includes:

HDB Resale Transaction Data (Raw)
- hdb_resale_2012.csv  
- hdb_resale_2022.csv  
- Data from [data.gov.sg](https://data.gov.sg/)  

MRT Station Data
- mrt_station_coordinates.csv  
- Contains location data of MRT stations  

OneMap API Walking Distance Data
- hdb_mrt_routing_interim_37000.csv  
- Processed dataset with HDB-MRT walking distances  

Reddit Sentiment Data
- reddit_housing_sentiment.csv  
- Extracted sentiment analysis from housing-related discussions  

Processed Data (Post Feature Engineering)
- supervised_data_2012.csv  
- supervised_data_2022.csv  
- Includes additional engineered features (sentiment, MRT proximity)  

Readme.txt
- Detailed explanation of file usage and column descriptions  

Installation & Setup

Ensure the following Python packages are installed:
pip install pandas numpy scikit-learn matplotlib seaborn xgboost tensorflow nltk transformers praw geopy requests polyline


Execution Steps
1. Download all required datasets and scripts
2. Use VS code or Collab to run python scripts
3. Ensure file paths are correct before execution
4. Run each notebook cell sequentially to process data, train models and evaluate performance.
License 
Developed by Machine Learning P4 Group 18
Data sourced from:
•	data.gov.sg (HDB resale transactions)
•	OneMap API (Geospatial data)
•	Reddit API (Sentiment analysis)


