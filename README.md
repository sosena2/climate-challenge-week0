# Climate Challenge Week 0

## Project Layout

Each branch should keep its own country-specific dataset, notebook, and README content.

```text
climate-challenge-week0/
├── .vscode/
│   └── settings.json
├── .github/
│   └── workflows/
│       └── ci.yml
├── .gitignore
├── requirements.txt
├── README.md
├── data/                     
│   └── kenya_clean.csv
├── notebooks/
│   ├── __init__.py
│   ├── README.md
│   └── kenya_eda.ipynb
├── src/
│   └── __init__.py
├── scripts/
│   ├── __init__.py
│   └── README.md
└── tests/
	└── __init__.py
```

## Setup

1. Clone repository
2. Create virtual environment
3. Activate virtual environment
4. Install dependencies

```bash
pip install -r requirements.txt
```

## Branch Notes

- The `data/` folder stays local and ignored because this branch uses the Kenya CSV.
- The notebook in `notebooks/` should stay aligned with the Kenya dataset and analysis.
- The README content should describe the Kenya CSV and workflow for this branch.
