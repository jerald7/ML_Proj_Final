# Machine Learning for HDB Price Prediction with Sentiment Analysis

## Project Overview
Buying a house in Singapore is a complex and expensive decision. This project leverages machine learning and sentiment analysis to predict HDB resale prices, incorporating location, property attributes, and public sentiment from online discussions.

By analyzing resale transaction data, geospatial features, and sentiment data, this project aims to:
1. Provide a **data-driven valuation** of HDB flats based on historical trends.
2. Incorporate **public sentiment analysis** to measure how location desirability impacts prices.
3. Offer insights into **MRT accessibility and amenities** as key pricing factors.

---

## Project Phases
The development process is divided into three main phases:

### **Phase 1: Data Collection & Preprocessing**
- Collect historical HDB resale transaction data.
- Use OneMap API to retrieve geospatial data (MRT proximity, walking distance).
- Scrape Reddit discussions to extract sentiment on housing and locations.

#### **OneMap API Setup**
To fetch HDB coordinates and calculate walking routes to MRT stations, you must obtain an API key from OneMap.

1. **Sign Up for OneMap API**:
   - Go to: [OneMap API Registration](https://www.onemap.gov.sg/).
   - Sign up for an account and log in.
   - Navigate to "Generate API Token" and request a new key.
   - Copy your access token (a long alphanumeric string).

2. **Add Your API Key to the Code**:
   Once you have your API token, insert it into your script:
   ```python
   # Replace this with your actual OneMap API token
   ONEMAP_API_TOKEN = "your_api_key_here"

   # Initialize OneMap API
   onemap = OneMapAPI(ONEMAP_API_TOKEN)
   ```

#### **Reddit API Setup**
To scrape Reddit discussions for sentiment analysis, you need to obtain Reddit API credentials. Follow these steps:

1. **Create a Reddit Account**:
   - Sign up at [https://www.reddit.com/register](https://www.reddit.com/register).

2. **Create a Reddit App**:
   - Go to the [Reddit App Preferences](https://www.reddit.com/prefs/apps) page.
   - Scroll down and click **Create an App**.
   - Fill out the form:
     - **Name**: Give your app a name (e.g., "Sentiment Analysis Bot").
     - **App Type**: Select **Script**.
     - **Description**: Add a short description (e.g., "A script to analyze sentiment on Reddit posts").
     - **About URL**: Leave blank or provide a placeholder (e.g., `https://example.com`).
     - **Redirect URI**: Enter `http://localhost:8080` (this is required but won't be used for a script).
   - Click **Create App**.

3. **Get Your Credentials**:
   - After creating the app, you’ll see:
     - **Client ID**: A string under "personal use script" (e.g., `abc123def456`).
     - **Client Secret**: A longer string (e.g., `ghi789jkl012`).
     - **User Agent**: A string that identifies your app (e.g., `python:sg-sentiment-analysis:v1.0 (by u/your_username)`).

4. **Add Your Credentials to the Code**:
   - Create a `.env` file in the root directory of your project and add the following lines:
     ```plaintext
     REDDIT_CLIENT_ID=your_client_id
     REDDIT_CLIENT_SECRET=your_client_secret
     REDDIT_USER_AGENT=python:sg-sentiment-analysis:v1.0 (by u/your_username)
     ```
   - Replace `your_client_id`, `your_client_secret`, and `your_username` with the values from your Reddit app.

---

### **Phase 2: Feature Engineering & Model Training**
- Perform feature selection (location, flat type, amenities, sentiment scores).
- Train multiple regression models (Linear Regression, XGBoost, Deep Learning).
- Validate models using RMSE, MAE, and R² scores.

---

### **Phase 3: Model Optimization & Evaluation**
- Fine-tune hyperparameters using RandomizedSearchCV.
- Apply ensemble learning techniques for better accuracy.
- Generate insights on how sentiment scores influence pricing.

---

## Dataset and Files
The dataset includes:

### **HDB Resale Transaction Data (Raw)**
- `ResaleFlatPrices/Resale flat prices based on registration date from Jan-2017 onwards.csv`
- `hdb_resale_2012.csv`
- `hdb_resale_2022.csv`  
Data from [data.gov.sg](https://data.gov.sg/).

### **MRT Station Data**
- `mrt_locations/mrt_lrt_data.csv`  
Contains latitude and longitude of all MRT and LRT stations in Singapore.  
Data from [Kaggle](https://www.kaggle.com/datasets/yxlee245/singapore-train-station-coordinates/).

### **OneMap API Walking Distance Data**
- `hdb_mrt_routing_interim_37000.csv`  
Processed dataset with HDB-MRT walking distances.

### **Multiple Datasets**
- `merged_data_3.csv`  
Final dataset after merging and preprocessing all relevant datasets.

### **`Readme.txt`**
Detailed explanation of file usage and column descriptions.

---

## Installation & Setup
Ensure the following Python packages are installed:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn xgboost tensorflow nltk transformers praw geopy requests polyline python-dotenv tqdm kneed spacy thefuzz
```

---

## Execution Steps
1. Download all required datasets and scripts.
2. Use VS Code or Google Colab to run Python scripts.
3. Ensure file paths are correct before execution.
4. Run each notebook cell sequentially to process data, train models, and evaluate performance.

---

## License
Developed by Machine Learning P4 Group 18.  
Data sourced from:
- [data.gov.sg](https://data.gov.sg/) (HDB resale transactions)
- [OneMap API](https://www.onemap.gov.sg/) (Geospatial data)
- [Reddit API](https://www.reddit.com/dev/api/) (Sentiment analysis)

---

### **Key Improvements**
1. **Clarity**: Added clear headings and subheadings for better readability.
2. **Step-by-Step Instructions**: Provided detailed steps for setting up the OneMap and Reddit APIs.
3. **Code Snippets**: Included code snippets for adding API keys and credentials.
4. **Organization**: Grouped related information together (e.g., API setup, dataset descriptions).
5. **Consistency**: Ensured consistent formatting for file names, code blocks, and links.

---

