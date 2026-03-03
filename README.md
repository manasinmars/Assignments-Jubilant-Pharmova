
---
# Repository structure 

Assignments-Jubilant-Pharmova/
│
├── Assignment1/
│   ├── code/
│   │   ├── Assignment-1 Code.ipynb
│   │   └── Store Sales Analysis & Prediction.pdf
│   │
│   ├── dataset/
│      └── sales_data.csv
│  
├── Assignment2/
│   ├── code/
│   │   ├── Assignment-2 code.ipynb
│   │   └── Simple_policy_q&a.pdf
│   │
│   ├── dataset/
│       ├── leave_policy.txt
│       ├── it_policy.txt
│       └── travel_policy.txt
│
└── README.md

# 🧠 Assignment 1 – Store Sales Analysis & Prediction

## 🎯 Objective
To analyze one year (366 days) of daily store sales data and build a 
time-series forecasting model to generate reliable short-term predictions.

## 📊 Dataset
- Sales (Target Variable)
- Promotion (0/1 indicator)
- DayOfWeek (1–7)
- Date (converted to datetime index)

## 🔍 Exploratory Data Analysis
- 7-day moving average to smooth trends
- Promotion vs Non-Promotion comparison
- Weekly sales pattern analysis
- Monthly stability analysis

### Key Findings
- Promotions increase sales by ~24%
- Weekdays outperform weekends
- Demand remains stable across months

---

## ⚙️ Feature Engineering

- Lag Features: `lag_1`, `lag_7`, `lag_14`
- Rolling Means: 7-day and 30-day (shifted to prevent leakage)
- Calendar Features: Month, DayOfMonth, IsWeekend
- Interaction Feature: Promo_Weekend

Rows with missing values from rolling operations were removed.

---

## 🤖 Model Development

Model Used: **Gradient Boosting Regressor**

Why?
- Handles non-linear relationships
- Strong performance on tabular data
- Built-in feature importance

### Train-Test Split
- First 306 days → Training
- Last 30 days → Testing
(Chronological split to avoid data leakage)

---

## 📈 Model Performance

- MAE: 12.95
- RMSE: 15.79
- Error ≈ 6.3% of average sales

The model achieved strong short-term forecasting accuracy.

---

## 🔮 Forecasting

A recursive 7-day forecasting approach was implemented:
- Each predicted value is appended to history
- Lag and rolling features update dynamically
- Simulates real-world deployment

---

## 💼 Business Insights

1. Promotions significantly boost revenue (~24%)
2. Weekend sales underperform → opportunity for targeted campaigns
3. Sales show strong short-term momentum
4. Stable monthly demand supports consistent inventory planning
5. Model is suitable for operational decision-making

---

# 🤖 Assignment 2 – Simple Policy Q&A Bot

## 🎯 Objective
To build a retrieval-based Question–Answering system that extracts relevant 
information from policy documents without using paid APIs or LLMs.

---

## 📂 Documents Used

- leave_policy.txt
- it_policy.txt
- travel_policy.txt

Each file contains numbered policy statements.

---

## ⚙️ Approach

### 1️⃣ Statement-Level Chunking
- Each document parsed using regex
- Statements extracted individually
- Stored with:
  - Cleaned version (for vectorization)
  - Original version (for display)
  - Source document name

Total Statements: 15

---

### 2️⃣ TF-IDF Vectorization

- Converts statements into numerical vectors
- TF → term frequency
- IDF → importance weighting
- Stop words removed

Matrix Shape: (15, Vocabulary Size)

---

### 3️⃣ Cosine Similarity

For each user query:
1. Convert query to TF-IDF vector
2. Compute cosine similarity against all statements
3. Select highest similarity score
4. Apply similarity threshold

If below threshold:
> "Information not available in policy documents."

---

## 🧪 Features

- Retrieves exact matching policy statement
- Displays source document
- Shows confidence score
- Includes interactive Q&A mode
- Similarity score visualization using matplotlib

---

## 🔍 Key Insights

- Statement-level retrieval improves precision
- TF-IDF highlights domain-specific terms (e.g., VPN, maternity)
- Cosine similarity enables ranked retrieval
- Transparent and interpretable system

---

## ⚠️ Limitations

- Bag-of-words model (no semantic understanding)
- Cannot detect synonyms effectively
- No generative capability

Future improvement:
- Sentence embeddings (SBERT)
- Local LLM integration

---

# 🛠 Technologies Used

- Python 3
- Pandas
- NumPy
- Matplotlib
- Scikit-learn (Gradient Boosting, TF-IDF, Cosine Similarity)

---

# 🚀 How to Run

1. Clone the repository
2. Navigate to Assignment1 or Assignment2
3. Open the notebook files
4. Run all cells

---

# 📌 Summary

This repository demonstrates:

- End-to-end Time-Series Forecasting
- Feature Engineering for structured data
- Ensemble modeling with Gradient Boosting
- Classical NLP Retrieval System
- TF-IDF + Cosine Similarity implementation
- Threshold-based fallback logic
- Business interpretation of ML outputs

---

**Author:** Manas Malik  
