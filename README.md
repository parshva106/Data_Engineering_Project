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
