# BigMart Sales Predictor

## Overview

A machine learning web application that predicts sales for BigMart products using a Gradient Boosting model. The app provides an intuitive interface for users to input product and outlet details to get sales predictions.

## Architecture Overview

<img width="2385" height="3817" alt="deepseek_mermaid_20251110_bf4f86" src="https://github.com/user-attachments/assets/29c36eba-cbe3-44fa-b348-92d2c4fb5c7d" />

## 🚀 Features

### 📊 Data Engineering Pipeline

* Automated XML data ingestion from multiple sources
* Dynamic **MySQL database creation** and table population
* Data cleaning and feature engineering steps for retail datasets
* Handling of categorical variables and missing values

### 🤖 Machine Learning

* Gradient Boosting Regressor for accurate sales prediction
* Preprocessing with **OneHotEncoder** for categorical variables
* Evaluation metrics: **R² Score** and **RMSE**
* Model persistence using **Pickle** serialization

### 🌐 Web Application

* Built with **Streamlit**
* User-friendly form-based interface
* Real-time sales predictions
* Deployed via **Streamlit Cloud**

---

## 🛠️ Technical Stack

| Component                      | Technology                     |
| ------------------------------ | ------------------------------ |
| **Programming Language**       | Python 3.10                    |
| **Database**                   | MySQL                          |
| **Machine Learning Framework** | scikit-learn                   |
| **Web Framework**              | Streamlit                      |
| **Libraries**                  | pandas, numpy, pickle, pymysql |
| **Deployment**                 | Streamlit Cloud                |

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
```

---

