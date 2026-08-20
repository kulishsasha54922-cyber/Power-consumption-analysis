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

### All three zones follow the same rhythm in January

Looking at January hour by hour, the same daily pattern repeats across all three zones: consumption falls overnight, rises during the day, and peaks in the evening. The overall consumption levels are different, however. Zone 1 records the highest January average at 31.0k, followed by Zone 2 at 19.4k and Zone 3 at 17.7k. The zones also move closely together, with correlations between their hourly series ranging from 0.87 to 0.95. This suggests that they respond to many of the same daily routines and weather conditions.

![Hourly electricity consumption by zone in January 2017](assets/january-zone-profile.png)

The timing is not exactly the same in every zone. Zone 1 and Zone 2 reach their lowest average at 04:00 and peak at 18:00. Zone 3 starts later, with its minimum at 08:00 and its peak at 20:00. When the zones are combined, January demand is lowest at 04:00 and highest at 19:00. The chart also shows an unusual dip around the middle of the month and a smaller drop near 29 January.

### Data quality

Before looking for patterns, I checked the data for gaps and repeated rows. The dataset contains 52,416 readings, recorded every ten minutes throughout 2017. There are no missing values and no duplicate rows, so I could use the full dataset for the hourly, daily, and monthly comparisons.

### Strong summer seasonality

The clearest pattern is the rise in electricity use during the summer. Average total consumption goes from about 66.6k in March to 88.2k in July, which is the highest monthly result. July is roughly 38.3% higher than December (63.8k), the lowest month in the dataset.

What stood out to me was how quickly the change happens: consumption rises by 16.5% between June and July, stays high in August, and then drops by 20.1% in September.

![Average total power consumption by month](assets/monthly-consumption.png)

The daily chart shows the same pattern in more detail. The highest daily average appears on 25 July (98.0k), while the lowest is on 1 December (58.6k). There are also regular dips throughout the year, which look like a repeating weekly pattern rather than random isolated drops.

![Daily average total power consumption](assets/daily-consumption.png)

### Most electricity is used in the evening

Electricity use changes a lot during the day. It falls overnight and reaches its lowest point at 06:00 (50.2k). From there it rises through the morning, stays fairly steady in the afternoon, and climbs sharply after 17:00.

The highest average is at 20:00 (98.0k). That is about 95.3% higher than the morning minimum, so the evening peak is almost twice as high as the lowest point of the day. The period from 19:00 to 21:00 is the most important one to watch when thinking about peak demand.

![Average total power consumption by hour of day](assets/hourly-profile.png)

### Weekday and weekend patterns are more similar than I expected

The overall difference between weekdays and weekends is not very large. Average consumption is 72.0k on weekdays and 69.3k on weekends, a difference of about 3.9%. Overnight, the two lines are almost the same, and both reach their highest point at 20:00.

The main difference appears in the morning. At 08:00, weekday consumption is about 11.3% higher than at the same time on weekends. A likely explanation is that daily activity starts later on Saturdays and Sundays.

![Weekday versus weekend hourly power consumption](assets/weekday-vs-weekend.png)

### The evening peak appears on every day of the week

The heatmap makes the daily pattern easier to compare across the whole week. Every day reaches its highest average at 20:00. The highest single combination is Thursday at 20:00, with an average of 99.6k. The lowest is Sunday at 07:00, with 45.0k, so the highest point is about 121.5% above the lowest one.

![Power consumption by day of week and hour](assets/weekday-hour-heatmap.png)

Weekend mornings are noticeably lighter than weekday mornings, especially between 05:00 and 08:00. The difference becomes much smaller in the evening: average demand from 19:00 to 21:00 is 96.8k on weekdays and 94.4k on weekends. This shows that the evening peak is a consistent feature of the system, not just a weekday effect.

### Zone 1 uses noticeably more electricity

Zone 1 stands out clearly when the three areas are compared. The average results are:

- Zone 1: 32.3k, or 45.4% of average total consumption;
- Zone 2: 21.0k, or 29.5%;
- Zone 3: 17.8k, or 25.0%.

This means that Zone 1 uses about 53.7% more electricity than Zone 2 and 81.4% more than Zone 3. It accounts for almost half of the combined average, so it would be the first area I would examine in a more detailed efficiency analysis.

![Average power consumption by zone](assets/zone-comparison.png)

### Temperature is relevant, does not explain demand alone

Temperature and total consumption have a positive correlation of 0.49. In general, electricity use tends to be higher on warmer days, which matches the summer peak seen earlier.

At the same time, the points on the chart are quite spread out. Similar temperatures can still be linked to very different levels of consumption. So temperature clearly matters, but it does not explain everything by itself. Time of day, weekday or weekend activity, season, and other weather conditions are also likely to play a role.

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
