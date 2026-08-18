# Power Consumption Analysis

Exploratory data analysis of electricity consumption in three distribution zones in Tetouan, Morocco.

## Project overview

This project explores electricity demand recorded every 10 minutes during 2017. The analysis compares the three zones and examines:

- daily and monthly consumption patterns;
- hourly demand and peak hours;
- weekday and weekend profiles;
- average consumption by zone;
- the relationship between temperature and total consumption.

## Key findings

- July has the highest average total consumption; December has the lowest.
- Average demand peaks at 20:00 and reaches its minimum at 06:00.
- Zone 1 has the highest average consumption, followed by Zones 2 and 3.
- Temperature has a moderate positive correlation with total consumption (`r = 0.49`).

## Repository structure

```text
.
├── powerconsumption.ipynb  # Analysis, visualizations, and findings
├── requirements.txt        # Python dependencies
├── .gitignore
└── README.md
```

## Dataset

The project uses the [Power Consumption of Tetouan City](https://archive.ics.uci.edu/dataset/849/power+consumption+of+tetouan+city) dataset from the UCI Machine Learning Repository.

Download the CSV file, rename it to `powerconsumption.csv`, and save it as:

```text
data/powerconsumption.csv
```

The raw dataset is excluded from Git because it can be downloaded from the original source.

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook powerconsumption.ipynb
```

On Windows, activate the environment with `.venv\Scripts\activate`.

## Technologies

Python, Jupyter Notebook, pandas, NumPy, Matplotlib, and Seaborn.

## Dataset citation

Salam, A. & El Hibaoui, A. (2018). *Power Consumption of Tetouan City*. UCI Machine Learning Repository. https://doi.org/10.24432/C5B034
