# 🛒 BigMart Sales Forecasting Pipeline  

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)
![MySQL](https://img.shields.io/badge/Database-MySQL-blue?logo=mysql)
![Scikit-learn](https://img.shields.io/badge/Machine_Learning-ScikitLearn-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Deployed-brightgreen)

---

## 📖 Project Description  

A complete **Data Engineering + Machine Learning** pipeline for **retail sales prediction** using the **BigMart dataset**.  
This project demonstrates a full workflow — from **XML data ingestion**, **MySQL database creation**, **model training**, to **Streamlit app deployment**.

👉 **Live Demo:** https://dataengineeringproject-bigmart.streamlit.app

---

## 🧱 Architecture Overview  

```markdown
## 🧱 Architecture Overview  

```mermaid
flowchart TD
    subgraph Ingestion [Data Ingestion]
        A1[df_item.xml] --> A4[(MySQL: item_info)]
        A2[df_outlet.xml] --> A5[(MySQL: outlet_info)]
        A3[df_sales.xml] --> A6[(MySQL: sales_info)]
    end

    subgraph Processing [Data Processing]
        A4 --> B1[Merge Tables]
        A5 --> B1
        A6 --> B1
        B1 --> B2[Cleaning & Feature Engineering]
        B2 --> B3[Train/Test Split]
    end

    subgraph Modeling [Model Training]
        B3 --> C1[GradientBoostingRegressor]
        C1 --> C2[Save Model]
    end

    subgraph Deployment [Streamlit App]
        C2 --> D1[Web Interface]
        D1 --> D2[Predict Sales]
    end
🚀 Features
📊 Data Engineering Pipeline
Automated XML data ingestion

Dynamic MySQL database creation

Data cleaning and preprocessing

Feature engineering for retail datasets

🤖 Machine Learning
Gradient Boosting Regressor

OneHotEncoding for categorical variables

R² and RMSE evaluation

Model saved using Pickle

🌐 Web App
Streamlit interactive interface

Real-time predictions

Clean UI

🛠️ Technical Stack
Component	Technology
Programming Language	Python 3.10
Database	MySQL
ML Framework	scikit-learn
Web Framework	Streamlit
Libraries	pandas, numpy, pickle, pymysql
Deployment	Streamlit Cloud

📁 Project Structure
bash
Copy code
BigMart-Sales-Forecasting/
│
├── data/
│   ├── df_item.xml
│   ├── df_outlet.xml
│   ├── df_sales.xml
│
├── models/
│   └── bigmart_best_model.pkl
│
├── src/
│   ├── data_ingestion.py
│   ├── database_operations.py
│   ├── model_training.py
│   └── utils.py
│
├── app.py
├── requirements.txt
└── README.md
🎯 Model Features
🔧 Preprocessing Pipeline
OneHotEncoder for categorical features

Numerical features passed through directly

Sparse matrix optimization

📈 Model Specifications
Parameter	Value
Algorithm	GradientBoostingRegressor
Estimators	300
Max Depth	3
Learning Rate	0.1
Loss Function	HalfSquaredError

🏷️ Feature Set
Category	Features
Product Info	Item_Identifier, Item_Weight, Item_Fat_Content, Item_Visibility, Item_Type, Item_MRP
Outlet Info	Outlet_Identifier, Outlet_Size, Outlet_Location_Type, Outlet_Type, Outlet_Age

🚀 Quick Start
1️⃣ Installation
bash
Copy code
git clone https://github.com/parshva106/BigMart-Sales-Forecasting.git
cd BigMart-Sales-Forecasting
pip install -r requirements.txt
2️⃣ Database Setup
bash
Copy code
mysql -u root -p
CREATE DATABASE bigmart_sales;
3️⃣ Run Data Pipeline
bash
Copy code
python src/data_ingestion.py
python src/database_operations.py
python src/model_training.py
4️⃣ Launch Web App
bash
Copy code
streamlit run app.py
💻 Usage Example
python
Copy code
import pickle
import pandas as pd

with open('models/bigmart_best_model.pkl', 'rb') as file:
    model = pickle.load(file)

sample_data = {
    'Item_Identifier': 'FDA15',
    'Item_Weight': 9.30,
    'Item_Fat_Content': 'Low Fat',
    'Item_Visibility': 0.016,
    'Item_Type': 'Dairy',
    'Item_MRP': 249.80,
    'Outlet_Identifier': 'OUT049',
    'Outlet_Size': 'Medium',
    'Outlet_Location_Type': 'Tier 1',
    'Outlet_Type': 'Supermarket Type1',
    'Outlet_Age': 5
}

prediction = model.predict(pd.DataFrame([sample_data]))
print(f"Predicted Sales: ₹{prediction[0]:.2f}")
📊 Results & Performance
High accuracy achieved

Strong generalization across outlets

Works well with mixed data types

Scalable and easy retraining

🔧 Configuration
Environment Variables
bash
Copy code
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=bigmart_sales
MySQL Schema
sql
Copy code
CREATE TABLE item_info (
  item_id VARCHAR(50),
  weight FLOAT,
  fat_content VARCHAR(20)
);

CREATE TABLE outlet_info (
  outlet_id VARCHAR(50),
  size VARCHAR(20),
  location_type VARCHAR(20)
);

CREATE TABLE sales_info (
  item_id VARCHAR(50),
  outlet_id VARCHAR(50),
  sales FLOAT
);
🤝 Contributing
Fork the repo

Create a branch

bash
Copy code
git checkout -b feature/AmazingFeature
Commit

bash
Copy code
git commit -m "Add AmazingFeature"
Push

bash
Copy code
git push origin feature/AmazingFeature
Open a Pull Request

📄 License
MIT License (see LICENSE file)

📞 Contact
Author: Parshva Mehta
GitHub: https://github.com/parshva106
Project Link: https://github.com/parshva106/BigMart-Sales-Forecasting

🎯 Future Enhancements
Real-time data streaming

Feature engineering improvements

Model monitoring dashboard

A/B testing

Multi-store optimization
