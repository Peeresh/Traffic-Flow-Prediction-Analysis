# 🚦 Urban Traffic Flow & Situation Prediction

An end-to-end Machine Learning project developed in a Jupyter Notebook to classify and predict urban traffic congestion situations. By analyzing temporal data alongside distinct vehicular volume streams (cars, bikes, buses, trucks), this project trains an ensemble classifier to accurately categorize traffic density levels.

## 📌 Project Overview
Urban traffic management relies heavily on identifying peak congestion patterns. This repository features a comprehensive engineering workflow that processes sensor/count data to predict the `Traffic Situation` string label (e.g., Low, Normal, High, Heavy).

The complete analysis, data preparation steps, and evaluation metrics are natively executed and documented inside the master workbook: `Traffic_flow_prediction.ipynb`.

---

## 📊 Dataset Features & Architecture

The predictive framework processes the following dataset parameters:

| Feature Column | Data Type | Description |
| :--- | :--- | :--- |
| **Date** | Numeric / Encoded | The calendar day of the observation cycle. |
| **Day of the week** | Categorical (Encoded) | Monday through Sunday, mapping behavioral travel shifts. |
| **Time** | Numeric / Categorical | The time signature or hourly block of data collection. |
| **CarCount** | Numerical (Integer) | Total volume count of cars recorded. |
| **BikeCount** | Numerical (Integer) | Total volume count of motorbikes/bicycles recorded. |
| **BusCount** | Numerical (Integer) | Total volume count of heavy transit buses recorded. |
| **TruckCount** | Numerical (Integer) | Total volume count of logistical transport trucks recorded. |
| **Traffic Situation** | **Target Class** | The density status classification of the road. |

---

## 🛠️ Machine Learning Pipeline Architecture

The notebook structures the data science life cycle into distinct operational cells:

### 1. Exploratory Data Analysis & Heatmaps
* Generates a structural correlation matrix heatmap utilizing `df.corr(numeric_only=True)`.
* This evaluates how spikes in specific categories (like heavy vehicle counts vs. bike counts) mathematically shift or correlate with scheduling metrics.

### 2. Preprocessing & Categorical Encoding
* Translates descriptive text strings like `Day of the week` and `Traffic Situation` into machine-readable numeric formats via Scikit-Learn's `LabelEncoder`.

### 3. Feature Scaling & Partitioning
* Isolates the target array from the feature landscape.
* Segments data arrays into training (80%) and testing (20%) boundaries using `train_test_split`.
* Uses `StandardScaler` (`fit_transform` on training data, `transform` on testing data) to ensure distance calculations are properly weighted.

### 4. Ensemble Modeling
* Initializes and fits a **Random Forest Classifier** (`n_estimators=100`) to master multi-class traffic decisions based on conditional branch voting patterns.

---

## 📈 Evaluation Matrix
Model accuracy is evaluated inside the notebook using robust verification criteria from `sklearn.metrics`:
* **Confusion Matrix:** Tracks specific true positives vs. false assignments across all traffic density classes.
* **Classification Report:** Measures Precision, Recall, and F1-Scores for every individual traffic level to ensure minor classes aren't drowned out by majority data trends.
* **Accuracy Score:** Delivers the total categorical accuracy percentage of the model.

---

## 📁 Repository Structure
```text
TRAFFIC-FLOW-PREDICTION/
│
├── project-files/
│   └── Traffic_flow_prediction.ipynb     # Master notebook (EDA, Scaling, Encoding, Model)
│
└── README.md                             # Comprehensive project documentation