# 🛒 BigMart Sales Forecasting Pipeline  

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)
![MySQL](https://img.shields.io/badge/Database-MySQL-blue?logo=mysql)
![Scikit-learn](https://img.shields.io/badge/Machine_Learning-ScikitLearn-orange?logo=scikit-learn)
![Status](https://img.shields.io/badge/Status-Deployed-brightgreen)

---

## 📖 Project Description  

A complete **Data Engineering + Machine Learning** pipeline for **retail sales prediction** using the **BigMart dataset**.  
This project demonstrates a full pipeline — from **automated XML data ingestion**, **MySQL database creation**, **machine learning model training**, to **Streamlit app deployment**.

👉 **Live Demo:** [https://dataengineeringproject-bigmart.streamlit.app](https://dataengineeringproject-bigmart.streamlit.app)

---

## 🧱 Architecture Overview  

```mermaid
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
        B3 --> C1[📈 GradientBoostingRegressor]
        C1 --> C2[💾 Save bigmart_best_model.pkl]
    end

    subgraph Deployment [🚀 Streamlit App]
        C2 --> D1[🌐 Streamlit Web Interface]
        D1 --> D2[📊 Predict Sales]
    end
## 🚀 Features  

### 📊 Data Engineering Pipeline  
- Automated XML data ingestion from multiple sources  
- Dynamic **MySQL database creation** and table population  
- Data cleaning and feature engineering steps for retail datasets  
- Handling of categorical variables and missing values  

### 🤖 Machine Learning  
- Gradient Boosting Regressor for accurate sales prediction  
- Preprocessing with **OneHotEncoder** for categorical variables  
- Evaluation metrics: **R² Score** and **RMSE**  
- Model persistence using **Pickle** serialization  

### 🌐 Web Application  
- Built with **Streamlit**  
- User-friendly form-based interface  
- Real-time sales predictions  
- Deployed via **Streamlit Cloud**

---

## 🛠️ Technical Stack  

| Component | Technology |
|------------|-------------|
| **Programming Language** | Python 3.10 |
| **Database** | MySQL |
| **Machine Learning Framework** | scikit-learn |
| **Web Framework** | Streamlit |
| **Libraries** | pandas, numpy, pickle, pymysql |
| **Deployment** | Streamlit Cloud |

---

## 📁 Project Structure  

```bash
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
├── app.py                    # Streamlit web application
├── requirements.txt          # Dependencies
└── README.md                 # Project documentation
## 🎯 Model Features  

### 🔧 Preprocessing Pipeline  
- **Categorical Encoding:** OneHotEncoder for 7 categorical features  
- **Numerical Features:** Passed directly without transformation  
- **Sparse Output:** Optimized for memory efficiency  

---

### 📈 Model Specifications  

| Parameter | Value |
|------------|--------|
| Algorithm | GradientBoostingRegressor |
| Estimators | 300 |
| Max Depth | 3 |
| Learning Rate | 0.1 |
| Loss Function | HalfSquaredError |

---

## 🏷️ Feature Set  

| Category | Features |
|-----------|-----------|
| **Product Info** | Item_Identifier, Item_Weight, Item_Fat_Content, Item_Visibility, Item_Type, Item_MRP |
| **Outlet Info** | Outlet_Identifier, Outlet_Size, Outlet_Location_Type, Outlet_Type, Outlet_Age |

---

## 🚀 Quick Start  

### 1️⃣ Installation  

```bash
git clone https://github.com/parshva106/BigMart-Sales-Forecasting.git
cd BigMart-Sales-Forecasting
pip install -r requirements.txt
### 2️⃣ Database Setup  

```bash
# Configure MySQL connection in database_operations.py
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
📊 Making Predictions
python
Copy code
import pickle
import pandas as pd

# Load the trained model
with open('models/bigmart_best_model.pkl', 'rb') as file:
    model = pickle.load(file)

# Prepare sample input
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
Achieved high accuracy in predicting retail sales

Robust generalization across various outlet types and product categories

Handles mixed (categorical + numerical) data effectively

Scalable and easy to retrain with updated datasets

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
  fat_content VARCHAR(20),
  ...
);

CREATE TABLE outlet_info (
  outlet_id VARCHAR(50),
  size VARCHAR(20),
  location_type VARCHAR(20),
  ...
);

CREATE TABLE sales_info (
  item_id VARCHAR(50),
  outlet_id VARCHAR(50),
  sales FLOAT,
  ...
);
🤝 Contributing
Fork the repository

Create a new feature branch

bash
Copy code
git checkout -b feature/AmazingFeature
Commit your changes

bash
Copy code
git commit -m 'Add some AmazingFeature'
Push to the branch

bash
Copy code
git push origin feature/AmazingFeature
Open a Pull Request

📄 License
This project is licensed under the MIT License — see the LICENSE file for details.

📞 Contact
👨‍💻 Author: Parshva Mehta
🎓 B.Tech – Electronics & Telecommunication
📫 Email: parshvamehta@example.com
🌐 GitHub: https://github.com/parshva106
📁 Project Link: https://github.com/parshva106/BigMart-Sales-Forecasting

🎯 Future Enhancements
Real-time data streaming integration

Advanced feature engineering

Model monitoring dashboard

A/B testing framework

Multi-store inventory optimization
