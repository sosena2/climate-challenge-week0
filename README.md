🌍 Climate Challenge Week 0

This project performs climate data analysis across five African countries in preparation for COP32. It includes data cleaning, exploratory data analysis (EDA), and cross-country climate vulnerability comparison using NASA climate datasets.

📌 Countries Included
Ethiopia
Kenya
Sudan
Uganda
Tanzania
📁 Project Structure
.
├── .github/
│   └── workflows/
│       └── ci.yml
├── .gitignore
├── requirements.txt
├── README.md
├── data/                      # (ignored in git)
│   ├── ethiopia_clean.csv
│   ├── kenya_clean.csv
│   ├── sudan_clean.csv
│   ├── uganda_clean.csv
│   └── tanzania_clean.csv
├── notebooks/
│   ├── ethiopia_eda.ipynb
│   ├── kenya_eda.ipynb
│   ├── sudan_eda.ipynb
│   ├── uganda_eda.ipynb
│   ├── tanzania_eda.ipynb
│   └── compare_countries.ipynb
├── src/
├── scripts/
└── tests/
⚙️ Environment Setup
1. Clone repository
git clone https://github.com/sosena2/climate-challenge-week0.git
cd climate-challenge-week0
2. Create virtual environment
python -m venv venv
3. Activate environment
Windows (PowerShell)
.\venv\Scripts\Activate.ps1
Mac/Linux
source venv/bin/activate
4. Install dependencies
pip install -r requirements.txt
📦 Requirements

Core libraries used:

pandas
numpy
matplotlib
seaborn
scipy
jupyter
ipykernel

Install manually if needed:

pip install pandas numpy matplotlib seaborn scipy
🔁 Git Workflow

This project uses feature branching:

setup-task → environment setup & CI
eda-<country> → country-specific analysis
compare-countries → cross-country comparison
🚀 Task Overview
🧩 Task 1: Git & Environment Setup
Objectives:
Initialize GitHub repository
Set up Python virtual environment
Configure GitHub Actions CI
Create project structure
Required files:
.gitignore (ignore data/, .ipynb_checkpoints/)
requirements.txt
.github/workflows/ci.yml
README.md
CI Pipeline:

Runs on push to main:

python --version
pip install -r requirements.txt
Commit requirements:

At least 3 commits using conventional commits:

init: add .gitignore
chore: setup venv
ci: add GitHub Actions workflow
📊 Task 2: Data Profiling, Cleaning & EDA

Each country is analyzed separately.

Key Steps:
📌 Data Loading & Parsing
Load dataset: pd.read_csv("<country>.csv")
Add Country column
Convert YEAR + DOY → datetime:
pd.to_datetime(df["YEAR"] * 1000 + df["DOY"], format="%Y%j")
Extract Month
📌 Data Cleaning
Replace -999 with NaN
Remove duplicates
Handle missing values:
forward fill OR drop rows >30% missing
Document all decisions
📌 Statistical Analysis
df.describe()
Missing value percentages
Z-score outlier detection:
variables: T2M, T2M_MAX, T2M_MIN, PRECTOTCORR, RH2M, WS2M
📌 Time Series Analysis
Monthly average temperature (T2M)
Monthly precipitation totals
Annotate:
warmest month
coolest month
peak rainfall months
📌 Correlation Analysis
Heatmap of all numeric features
Scatter plots:
T2M vs RH2M
T2M_RANGE vs WS2M
📌 Distribution Analysis
Histograms of precipitation
Bubble plot:
T2M vs RH2M (bubble = rainfall)
📌 Output

Each country exports:

data/<country>_clean.csv
🌍 Task 3: Cross-Country Comparison

Branch: compare-countries
Notebook: compare_countries.ipynb

Countries compared:

Ethiopia, Kenya, Sudan, Uganda, Tanzania

📊 Analysis
🌡 Temperature Comparison
Monthly T2M line chart (all 5 countries)
Summary table:
mean
median
std deviation
🌧 Precipitation Comparison
Boxplots for all countries
Summary statistics table
🔥 Extreme Events

Per country:

Days with T2M_MAX > 35°C
Dry days: PRECTOTCORR < 1mm

Visualized as bar charts.

📊 Statistical Testing
ANOVA or Kruskal-Wallis test on T2M
Report p-values and interpretation
🏆 Climate Vulnerability Ranking

Countries ranked based on:

warming trends
rainfall variability
heat extremes
drought frequency
🧠 COP32 Insights (5 key findings)
Which country is warming fastest?
Which country has most unstable rainfall?
Which country has highest heat/drought risk?
How does Ethiopia compare to neighbors?
Which country should be prioritized for climate finance?
📌 Key Rules
❌ Never commit raw CSV files
❌ Never commit .ipynb_checkpoints
✔ Always use feature branches
✔ Use conventional commit messages
✔ Document all data cleaning decisions
🔄 CI/CD

GitHub Actions runs on every push to main:

checks Python version
installs dependencies
validates environment setup
🎯 Key Performance Indicators (KPIs)
Task 1:
Working CI pipeline
Proper repo setup
3+ meaningful commits
Reproducible environment
Task 2:
Clean handling of missing data (-999)
Proper EDA + documentation
Clean exported datasets per country
Task 3:
All 5 countries included in all comparisons
Statistical analysis completed
Clear vulnerability ranking
COP32 insights clearly written
📬 Author

Climate Data Analysis Project – COP32 Preparation
