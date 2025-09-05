# Hotel Booking Data Pipeline 🏨

## 📌 Project Overview
This project builds a **robust data preprocessing pipeline** for the [Hotel Booking Demand Dataset](https://www.sciencedirect.com/science/article/pii/S2352340918315191).  
The objective is to clean, analyze, and transform the raw hotel booking dataset into a **machine-learning-ready format** for predicting booking cancellations.

While the final model is not built here, the **quality of this preprocessing pipeline** directly determines the success of any downstream ML model.

---

## 🎯 Business Problem
The revenue team observed that **last-minute booking cancellations** significantly impact profitability.  
To tackle this, we prepare the dataset by:
- Cleaning missing and inconsistent values
- Handling outliers
- Creating new features
- Encoding categorical variables
- Preventing data leakage

---

## ⚙️ Project Phases

### **Phase 1: Exploratory Data Analysis (EDA)**
- Generated `.info()` and `.describe()` summaries
- Identified missing values
- Visualized missingness (heatmap/bar chart)
- Detected outliers in `adr` and `lead_time` (boxplots, IQR method)

### **Phase 2: Data Cleaning**
- **Missing values:**
  - `company`, `agent` → filled with `0`
  - `country` → imputed with mode
  - `children` → imputed with median
- **Duplicates:** dropped exact duplicates
- **Outliers:** capped `adr` at `1000`, replaced negatives with `0`
- **Invalid rows:** dropped bookings with `adults + children + babies = 0`
- **Data types:** fixed dates (`reservation_status_date`, `arrival_date`)

### **Phase 3: Feature Engineering & Preprocessing**
- New features:
  - `total_guests = adults + children + babies`
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`
  - `is_family = 1 if children or babies > 0`
- Encoded categorical variables:
  - One-Hot Encoding for low-cardinality
  - Frequency encoding for `country`
- Removed **data leakage**:
  - Dropped `reservation_status` and `reservation_status_date`

### **Phase 4: Final Preparation**
- Train/Test Split: `test_size=0.2`, `random_state=42`, stratified by `is_canceled`

---

## 📂 Repository Structure
```

hotel-booking-data-pipeline/
│-- data/
│   └── hotel\_bookings.csv         # raw dataset (not uploaded if large)
│-- notebooks/
│   └── preprocessing\_pipeline.ipynb
│-- scripts/
│   └── preprocessing.py           # full preprocessing script
│-- outputs/
│   ├── hotel\_bookings\_cleaned.csv
│   ├── X\_train.csv
│   ├── X\_test.csv
│   ├── y\_train.csv
│   └── y\_test.csv
│-- README.md

````

---

## 🚀 Usage

### 1. Clone the repo
```bash
git clone https://github.com/gawadx1/hotel-cancellation-data-pipeline.git
cd hotel-booking-data-pipeline
````

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Run preprocessing

```bash
python scripts/preprocessing.py
```

This will generate cleaned datasets in the `outputs/` folder.

---

## 📊 Example Outputs

* **EDA visuals:** Missing value charts, outlier boxplots
* **Cleaned dataset shape:** `(X_train: XXXX, X_test: XXXX)`
* **Target distribution:** Balanced representation of cancellations

---

## 🛠️ Tech Stack

* **Python 3.9+**
* **Pandas, NumPy**
* **Matplotlib, Seaborn**
* **Scikit-learn**

---

## 📈 Next Steps

* Train ML models (Logistic Regression, Random Forest, XGBoost, etc.)
* Hyperparameter tuning
* Model evaluation & deployment

---

## 👤 Author

* **Gawad** – Machine Learning Engineer
  📧 Email: [abdullah.abdelgawwad@gmail.com](mailto:abdullah.abdelgawwad@gmail.com)
  🌐 [LinkedIn](https://www.linkedin.com/in/abdullah-abdalgawwad/) | [GitHub](https://github.com/gawadx1)

---

```
