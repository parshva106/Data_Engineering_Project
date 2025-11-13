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
