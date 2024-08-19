# Analyzing Bicycle Counts on Seattle's Fremont Bridge

This tutorial will guide you through analyzing the bicycle counts on Seattle's Fremont Bridge using Python. We'll cover how to work with the dataset, and analyze it from various perspectives, including hourly and weekly bicycle counts, average daily counts, and average hourly counts by weekday and weekend.

## Prerequisites

Before we begin, ensure you have the following installed:
- Python 3.x
- Pandas
- Matplotlib

You can install the necessary packages using pip:

```bash
pip install pandas matplotlib
```

## Step 1: Load the Dataset

First, download the dataset from the provided link: [Fremont Bridge Bicycle Counts](https://data.seattle.gov/api/views/65db-xm6k/rows.csv?accessType=DOWNLOAD).

Once downloaded, place the CSV file in your working directory.

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('Fremont_Bridge_Bicycle_Counter.csv')

# Display the first few rows to understand the structure of the data
df.head()
```

## Step 2: Data Preprocessing

### 2.1 Convert Date Column to Datetime

The date and time information is essential for time-based analysis. Convert the 'Date' column to a datetime object.

```python
# Convert the Date column to datetime format
df['Date'] = pd.to_datetime(df['Date'])
```

### 2.2 Handle Missing Data

Check for missing data and handle it accordingly.

```python
# Check for missing data
df.isnull().sum()

# Optionally, drop or fill missing values
df.dropna(inplace=True)
```

## Step 3: Hourly Bicycle Counts

To analyze hourly bicycle counts:

```python
# Group by hour to get the hourly bicycle counts
df['Hour'] = df['Date'].dt.hour
hourly_counts = df.groupby('Hour').sum()

# Plot the hourly bicycle counts
import matplotlib.pyplot as plt

hourly_counts.plot(y='Fremont Bridge Total', kind='bar', figsize=(10, 6))
plt.title('Hourly Bicycle Counts on Fremont Bridge')
plt.xlabel('Hour of the Day')
plt.ylabel('Bicycle Counts')
plt.show()
```

## Step 4: Weekly Bicycle Crossings

To analyze weekly bicycle crossings:

```python
# Group by week to get the weekly bicycle counts
df['Week'] = df['Date'].dt.isocalendar().week
weekly_counts = df.groupby('Week').sum()

# Plot the weekly bicycle counts
weekly_counts.plot(y='Fremont Bridge Total', kind='line', figsize=(10, 6))
plt.title('Weekly Bicycle Crossings on Fremont Bridge')
plt.xlabel('Week of the Year')
plt.ylabel('Bicycle Counts')
plt.show()
```

## Step 5: Average Daily Bicycle Counts

To calculate and visualize average daily bicycle counts:

```python
# Group by date to get daily counts, then calculate the average
daily_counts = df.groupby(df['Date'].dt.date).sum()
average_daily_counts = daily_counts.mean()

# Display the average daily bicycle count
print(f"Average Daily Bicycle Count: {average_daily_counts['Fremont Bridge Total']:.2f}")

# Plot the daily bicycle counts
daily_counts.plot(y='Fremont Bridge Total', kind='line', figsize=(10, 6))
plt.title('Daily Bicycle Counts on Fremont Bridge')
plt.xlabel('Date')
plt.ylabel('Bicycle Counts')
plt.show()
```

## Step 6: Average Hourly Bicycle Counts by Weekday and Weekend

To analyze and compare average hourly counts for weekdays versus weekends:

```python
# Add a column for the day of the week
df['DayOfWeek'] = df['Date'].dt.dayofweek

# Separate data into weekday and weekend
weekday_counts = df[df['DayOfWeek'] < 5].groupby('Hour').mean()
weekend_counts = df[df['DayOfWeek'] >= 5].groupby('Hour').mean()

# Plot average hourly counts for weekdays and weekends
plt.figure(figsize=(10, 6))
plt.plot(weekday_counts.index, weekday_counts['Fremont Bridge Total'], label='Weekdays')
plt.plot(weekend_counts.index, weekend_counts['Fremont Bridge Total'], label='Weekends')
plt.title('Average Hourly Bicycle Counts by Weekday and Weekend')
plt.xlabel('Hour of the Day')
plt.ylabel('Bicycle Counts')
plt.legend()
plt.show()
```

## Conclusion

By following this tutorial, you've explored the bicycle counts on Seattle's Fremont Bridge from various angles. You learned how to process time-series data and create insightful visualizations to understand patterns in bicycle usage.
