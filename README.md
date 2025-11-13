🛒 BigMart Sales Forecasting Pipeline

This repository demonstrates a complete end-to-end Data Engineering and Machine Learning pipeline built around BigMart’s retail sales data.
It automates data ingestion, database creation (MySQL), feature engineering, model training, and deployment through a Streamlit web app.

👉 Live Demo: https://dataengineeringproject-bigmart.streamlit.app

🧱 Project Architecture
flowchart TD
    subgraph Ingestion [📥 Data Ingestion]
        A1[📄 df_item.xml] --> A4[(MySQL: item_info)]
        A2[📄 df_outlet.xml] --> A5[(MySQL: outlet_info)]
        A3[📄 df_sales.xml] --> A6[(MySQL: sales_info)]
    end

    subgraph Processing [⚙️ Data Processing]
        A4 --> B1[🔗 Merge Tables]
        A5 --> B1
        A6 --> B1
        B1 --> B2[🧹 Cleaning & Feature Engineering]
        B2 --> B3[🔀 Train/Test Split]
    end

    subgraph Modeling [🤖 Model Training]
        B3 --> C1[📈 GradientBoostingRegressor + Comparisons]
        C1 --> C2[💾 Save bigmart_best_model.pkl]
    end

    subgraph Deployment [🚀 Streamlit App]
        C2 --> D1[🌐 Streamlit Web Interface]
        D1 --> D2[📊 Predict Item Outlet Sales]
    end

📂 Project Structure
├── app.py                     # Streamlit app for deployment
├── create_db_from_data.py     # Script to create MySQL DB and tables from XML
├── train_model.py             # Model training, evaluation, and pickle save
├── df_item.xml                # Item-level data
├── df_outlet.xml              # Outlet-level data
├── df_sales.xml               # Sales transaction data
├── bigmart_best_model.pkl     # Trained model pipeline (generated after training)
├── requirements.txt           # Dependencies
└── README.md                  # Project documentation

⚙️ Workflow Overview
1️⃣ Data Ingestion

XML files (df_item.xml, df_outlet.xml, df_sales.xml) are read using Pandas.

Tables are created automatically in MySQL with dynamic schema mapping.

Data is inserted efficiently using executemany().

python create_db_from_data.py

2️⃣ Data Processing & Feature Engineering

Performed inside train_model.py:

Merge item, outlet, and sales data on ID.

Clean inconsistent labels (e.g., "low fat" → "Low Fat").

Clip extreme visibility values (>0.3).

Add Outlet_Age = 2025 - Establishment_Year.

3️⃣ Model Training

Trains and compares:

Gradient Boosting Regressor 🏆 (Best model)

Random Forest Regressor

Linear Regression

Metrics used:

R² Score

RMSE

Best-performing model is serialized as bigmart_best_model.pkl.

python train_model.py

4️⃣ Deployment

A clean, interactive Streamlit app (app.py) enables users to:

Enter product and outlet attributes.

Predict expected sales in real-time.

streamlit run app.py

🧠 Tech Stack
Category	Technologies
Languages	Python
Database	MySQL
Data Processing	Pandas, NumPy
Modeling	scikit-learn (GradientBoosting, RandomForest, LinearRegression)
Deployment	Streamlit
Serialization	Pickle
🧩 Key Features

✅ Automated MySQL table creation from XML
✅ Dynamic data type mapping and insertion
✅ End-to-end data preprocessing pipeline
✅ Model comparison and evaluation
✅ Streamlit-based real-time prediction UI

🪄 Example Prediction (from Streamlit UI)
Feature	Example Input
Item Identifier	FDA15
Item Weight	12.5
Item Type	Dairy
Item MRP	150.0
Outlet Type	Supermarket Type1
Outlet Age	15

Predicted Sales → ₹2348.67

📦 Installation Guide

Clone the repo

git clone https://github.com/<your-username>/BigMart-Sales-Forecasting.git
cd BigMart-Sales-Forecasting


Install dependencies

pip install -r requirements.txt


Create database and train model

python create_db_from_data.py
python train_model.py


Run Streamlit app

streamlit run app.py

👨‍💻 Author

Parshva Mehta
🎓 B.Tech – Electronics & Telecommunication
📧 [Your Email Here]
🌐 GitHub Profile
