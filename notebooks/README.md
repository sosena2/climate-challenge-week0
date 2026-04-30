# 🌍 Climate Data Analysis — Ethiopia (EDA)

## 📌 Project Overview

This branch (`eda-ethiopia`) focuses on **data profiling, cleaning, and exploratory data analysis (EDA)** for Ethiopia’s climate dataset as part of the *Climate Challenge Week 0* project.

The goal is to extract meaningful insights about **temperature, precipitation, humidity, and wind patterns** in Ethiopia in the lead-up to COP32.

---

## 📂 Project Structure

```
climate-challenge-week0/
├── data/                     # Local data storage (not tracked by Git)
│   ├── ethiopia.csv          # Raw dataset
│   └── ethiopia_clean.csv    # Cleaned dataset (generated)
├── notebooks/
│   └── ethiopia_eda.ipynb    # Main EDA notebook
├── src/
├── scripts/
├── tests/
├── requirements.txt
├── README.md
└── .gitignore
```

---

## ⚠️ Data Handling

* The `data/` folder is **excluded from version control** via `.gitignore`.
* Raw data must be placed manually in:

  ```
  data/ethiopia.csv
  ```
* Cleaned data is exported to:

  ```
  data/ethiopia_clean.csv
  ```

---

## ⚙️ Environment Setup

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd climate-challenge-week0
```

### 2. Create and activate virtual environment

#### Using venv:

```bash
python -m venv venv
venv\Scripts\activate      # Windows
# OR
source venv/bin/activate   # Mac/Linux
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Analysis

1. Launch Jupyter Notebook:

```bash
jupyter notebook
```

2. Open:

```
notebooks/ethiopia_eda.ipynb
```

3. Run all cells sequentially.

---

## 🧹 Data Cleaning Steps

* Replaced **-999 sentinel values** with `NaN`
* Removed duplicate rows
* Converted `YEAR` and `DOY` → datetime format
* Extracted **Month** for seasonal analysis
* Handled missing values using:

  * Forward fill for weather variables
  * Dropping rows with excessive missing values (>30%)
* Detected outliers using **Z-score (|Z| > 3)**

---

## 📊 Analysis Performed

### 1. Time Series Analysis

* Monthly average temperature (T2M)
* Monthly total precipitation (PRECTOTCORR)
* Identification of seasonal trends

### 2. Correlation Analysis

* Heatmap of numeric variables
* Key relationships identified between:

  * Temperature & humidity
  * Temperature range & wind speed

### 3. Distribution Analysis

* Histogram of precipitation (log-scaled if skewed)
* Bubble chart:

  * X-axis: Temperature (T2M)
  * Y-axis: Humidity (RH2M)
  * Size: Precipitation

---

## 📈 Key Insights (Summary)

* Seasonal temperature variation shows clear warm and cool periods
* Rainfall patterns indicate distinct rainy seasons
* Strong correlations observed between climate variables
* Some outliers likely correspond to extreme weather events

---

## 🧪 Reproducibility Notes

To reproduce results:

1. Place dataset in `data/`
2. Install dependencies
3. Run the notebook end-to-end

---

## 📚 References & Learning Resources

* Pandas Documentation: https://pandas.pydata.org/
* NumPy Documentation: https://numpy.org/
* Matplotlib Documentation: https://matplotlib.org/
* Seaborn Documentation: https://seaborn.pydata.org/

---

## ✅ Status

✔ Data cleaned and validated
✔ EDA completed with visualizations
✔ Insights documented in notebook

---

