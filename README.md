# BigMart Sales Predictor 

## Overview
A machine learning web application that predicts sales for BigMart products using a Gradient Boosting model. The app provides an intuitive interface for users to input product and outlet details to get sales predictions.

👉 Live Demo: https://dataengineeringproject.streamlit.app/


## Architecture Overview
<img width="2385" height="3817" alt="deepseek_mermaid_20251110_bf4f86" src="https://github.com/user-attachments/assets/29c36eba-cbe3-44fa-b348-92d2c4fb5c7d" />

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
