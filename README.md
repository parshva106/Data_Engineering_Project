# 🛒 BigMart Sales Forecasting Pipeline  

A complete **Data Engineering + Machine Learning** pipeline for retail sales prediction.  
This project demonstrates **automated data ingestion**, **MySQL database operations**, **machine learning model training**, and **deployment** via an interactive **Streamlit web application**.

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
🚀 Features
📊 Data Engineering Pipeline
Automated XML data ingestion from multiple sources

MySQL Database Integration with structured schemas

Data Cleaning & Preprocessing pipeline

Feature Engineering for retail sales optimization

🤖 Machine Learning
Gradient Boosting Regressor for accurate sales predictions

Preprocessing pipeline with OneHotEncoding for categorical features

Model persistence using Pickle serialization

Comprehensive feature set including product and outlet characteristics

🌐 Web Application
Interactive Streamlit dashboard

Real-time sales predictions

User-friendly input forms

Visualization of results

🛠️ Technical Stack
Component	Technology
Backend	Python 3.8+
Database	MySQL
ML Framework	Scikit-learn 1.7.2
Web Framework	Streamlit
Data Processing	Pandas, NumPy
Model Serialization	Pickle

📁 Project Structure
bash
Copy code
bigmart-sales-forecasting/
├── data/
│   ├── df_item.xml
│   ├── df_outlet.xml
│   ├── df_sales.xml
├── models/
│   └── bigmart_best_model.pkl
├── src/
│   ├── data_ingestion.py
│   ├── database_operations.py
│   ├── model_training.py
│   └── utils.py
├── app.py
├── requirements.txt
└── README.md
🎯 Model Features
🔧 Preprocessing Pipeline
Categorical Encoding: OneHotEncoder for 7 categorical variables

Numerical Features: Direct pass-through for 4 numerical variables

Sparse Output: Memory-efficient encoding

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
git clone https://github.com/yourusername/bigmart-sales-forecasting.git
cd bigmart-sales-forecasting
pip install -r requirements.txt
2️⃣ Database Setup
bash
Copy code
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

# Prepare input data
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
The model demonstrates:

High accuracy in sales forecasting

Robust performance across diverse product categories

Effective handling of mixed data types (categorical + numerical)

Scalable predictions for retail inventory planning

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

Create your feature branch

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
This project is licensed under the MIT License – see the LICENSE file for details.

📞 Contact
Project Link: https://github.com/yourusername/bigmart-sales-forecasting

🎯 Future Enhancements
Real-time data streaming integration

Advanced feature engineering

Model performance monitoring

A/B testing framework

Multi-store inventory optimization

⭐ Star this repo if you find it helpful!
