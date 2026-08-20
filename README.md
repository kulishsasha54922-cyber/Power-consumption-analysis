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

### Data quality

The dataset contains **52,416 ten-minute observations** covering the full year of 2017. All nine original columns are complete: the analysis found **no missing values and no duplicate rows**. This provides a consistent base for hourly, daily, and monthly aggregation without imputation.

### Strong summer seasonality

Average total consumption increases from approximately **66.6k in March** to **88.2k in July**, the highest monthly level. July is about **38.3% above December** (63.8k), the lowest month. The sharpest movements occur around summer: consumption rises **16.5% from June to July**, remains elevated in August, and then falls **20.1% from August to September**.

![Average total power consumption by month](assets/monthly-consumption.png)

The daily series confirms that the seasonal peak is concentrated in midsummer. The highest daily average occurs on **25 July** (98.0k), while the lowest occurs on **1 December** (58.6k). Regular short downward spikes throughout the year suggest a recurring weekly cycle on top of the broader seasonal pattern.

![Daily average total power consumption](assets/daily-consumption.png)

### Demand is dominated by the evening peak

The daily profile follows a pronounced cycle. Consumption declines overnight to its minimum at **06:00** (50.2k), rises through the morning, levels off around midday, and accelerates after 17:00. It reaches its maximum at **20:00** (98.0k), making the evening peak approximately **95.3% higher than the early-morning minimum**. The 19:00–21:00 period is therefore the clearest demand-management window.

![Average total power consumption by hour of day](assets/hourly-profile.png)

### Weekdays and weekends share the same shape, but differ in the daytime

Weekday consumption averages **72.0k**, compared with **69.3k on weekends**—an overall difference of about **3.9%**. The profiles are nearly identical overnight and during the late-evening decline. The largest gap appears at **08:00**, when weekday demand is approximately **11.3% higher** than weekend demand, which is consistent with a later start to activity on non-working days. Both profiles still peak at 20:00.

![Weekday versus weekend hourly power consumption](assets/weekday-vs-weekend.png)

### Zone 1 carries the largest share of demand

Average consumption differs substantially across the three distribution zones:

- **Zone 1:** 32.3k, or **45.4%** of average total consumption;
- **Zone 2:** 21.0k, or **29.5%**;
- **Zone 3:** 17.8k, or **25.0%**.

Zone 1 consumes about **53.7% more than Zone 2** and **81.4% more than Zone 3**. Capacity planning and efficiency measures would therefore have the greatest absolute impact in Zone 1.

![Average power consumption by zone](assets/zone-comparison.png)

### Temperature is relevant, but does not explain demand alone

Temperature and total consumption have a **moderate positive Pearson correlation of 0.49**. Higher temperatures are generally associated with higher demand, which is consistent with the summer peak. However, the wide vertical spread in the scatter plot shows that observations with similar temperatures can have very different consumption levels. Temperature should therefore be treated as one important driver alongside hour of day, day type, season, and other weather variables—not as a standalone explanation or evidence of causation.

![Relationship between temperature and total power consumption](assets/temperature-relationship.png)

## Repository structure

```text
.
├── assets/                 # Charts used in this README
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
