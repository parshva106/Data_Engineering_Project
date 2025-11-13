🛒 BigMart Sales Forecasting Pipeline










🚀 A complete Data Engineering + Machine Learning pipeline for predicting sales across BigMart outlets.
From XML data ingestion → MySQL database → ML model training → Streamlit deployment, this project showcases an end-to-end automated system.

🌐 Live Demo

👉 BigMart Streamlit App

🧩 Project Overview

This project demonstrates how to:

Ingest XML data files directly into a MySQL database

Perform data cleaning and feature engineering

Train and evaluate multiple machine learning models

Deploy a Streamlit web app for real-time sales prediction

🏗️ System Architecture
flowchart TD
    A1[📂 XML Files<br>(df_item, df_outlet, df_sales)] --> B1[(MySQL Database)]
    B1 --> C1[🧹 Data Cleaning<br>& Feature Engineering]
    C1 --> D1[🤖 Model Training<br>(Gradient Boosting, RF, Linear Regression)]
    D1 --> E1[💾 Save Best Model<br>(bigmart_best_model.pkl)]
    E1 --> F1[🌐 Streamlit App<br>(app.py)]
    F1 --> G1[📊 Predict Item Sales]

📂 Repository Structure
BigMart-Sales-Forecasting/
│
├── app.py                     # Streamlit app for live prediction
├── create_db_from_data.py     # Creates MySQL DB & loads XML data
├── train_model.py             # ML model training, evaluation & export
├── df_item.xml                # Item-level data
├── df_outlet.xml              # Outlet-level data
├── df_sales.xml               # Sales transaction data
├── bigmart_best_model.pkl     # Trained ML pipeline (auto-generated)
├── requirements.txt           # Required libraries
└── README.md                  # Project documentation

⚙️ Workflow Summary
🧱 1. Data Ingestion

Parses 3 XML files using Pandas.

Dynamically creates MySQL tables (item_info, outlet_info, sales_info).

Loads all records automatically.

python create_db_from_data.py

🧠 2. Data Processing & Feature Engineering

Merges tables on ID

Fixes inconsistent categories (LF → Low Fat, etc.)

Caps extreme values (Item_Visibility ≤ 0.3)

Creates derived feature: Outlet_Age = 2025 - Establishment_Year

🤖 3. Model Training

Trains and compares 3 regression models:

Model	Description	Result
GradientBoostingRegressor	Ensemble boosting method	🥇 Best performer
RandomForestRegressor	Ensemble bagging method	Good performance
LinearRegression	Baseline linear model	For comparison

✅ Best model saved as bigmart_best_model.pkl.

python train_model.py

🚀 4. Streamlit Deployment

The Streamlit interface allows users to:

Input product & outlet details

Get instant sales predictions in ₹

streamlit run app.py


Sample Output:

📈 Predicted Item Outlet Sales: ₹2457.32

🧠 Tech Stack
Layer	Technologies
Data Storage	MySQL
Data Handling	Pandas, NumPy
Modeling	Scikit-learn (Gradient Boosting, RF, Linear)
Backend	Python
Frontend	Streamlit
Serialization	Pickle
🧩 Key Features

✅ Fully automated database creation from XML
✅ Dynamic SQL table generation
✅ Feature engineering + model evaluation
✅ Interactive web app for predictions
✅ Modular, reproducible pipeline

💡 Example Prediction
Feature	Example
Item Identifier	FDA15
Item Weight	12.5
Item Type	Dairy
Item MRP	150.0
Outlet Type	Supermarket Type1
Outlet Age	15

Predicted Sales → ₹2348.67

⚙️ Installation

1️⃣ Clone this repository

git clone https://github.com/parshva106/BigMart-Sales-Forecasting.git
cd BigMart-Sales-Forecasting


2️⃣ Install dependencies

pip install -r requirements.txt


3️⃣ Set up MySQL

python create_db_from_data.py


4️⃣ Train model

python train_model.py


5️⃣ Run app

streamlit run app.py

🧰 Requirements
streamlit
pandas
numpy
scikit-learn
pymysql
pickle-mixin

🧑‍💻 Author

👋 Parshva Mehta
🎓 B.Tech – Electronics & Telecommunication
📫 parshvamehta@example.com

🌐 GitHub Profile
