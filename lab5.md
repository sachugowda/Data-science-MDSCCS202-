# Visualizing and Analyzing Marathon Race Results

In this tutorial, we'll explore the marathon race results dataset. We'll focus on understanding the distribution of split fractions, analyzing these distributions by gender and age, and examining the relationship between split fraction and finishing time by gender.

## Prerequisites

Before we begin, ensure you have the following installed:
- Python 3.x
- Pandas
- Matplotlib
- Seaborn

You can install the necessary packages using pip:

```bash
pip install pandas matplotlib seaborn
```

## Step 1: Load the Dataset

First, download the dataset from the provided link: [Marathon Data](https://raw.githubusercontent.com/jakevdp/marathon-data/master/marathon-data.csv).

```python
import pandas as pd

# Load the dataset
url = "https://raw.githubusercontent.com/jakevdp/marathon-data/master/marathon-data.csv"
df = pd.read_csv(url)

# Display the first few rows to understand the structure of the data
df.head()
```

## Step 2: Data Preprocessing

### 2.1 Convert Time Columns to Timedelta

The 'split' and 'final' columns represent the split and finishing times. Convert them from strings to timedelta objects.

```python
# Convert time columns to timedelta
df['split'] = pd.to_timedelta(df['split'])
df['final'] = pd.to_timedelta(df['final'])

# Calculate split fraction
df['split_fraction'] = df['split'] / df['final']
```

## Step 3: Distribution of Split Fractions

Let's visualize the distribution of split fractions to understand how athletes distribute their effort between the first and second halves of the race.

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Plot the distribution of split fractions
plt.figure(figsize=(10, 6))
sns.histplot(df['split_fraction'], bins=50, kde=True)
plt.title('Distribution of Split Fractions')
plt.xlabel('Split Fraction')
plt.ylabel('Count')
plt.show()
```

## Step 4: Distribution of Split Fractions by Gender and Age

Now, let's explore how the split fractions differ by gender and age.

### 4.1 Distribution by Gender

```python
# Plot split fraction distribution by gender
plt.figure(figsize=(10, 6))
sns.histplot(df, x='split_fraction', hue='gender', bins=50, kde=True, stat='density', common_norm=False)
plt.title('Distribution of Split Fractions by Gender')
plt.xlabel('Split Fraction')
plt.ylabel('Density')
plt.show()
```

### 4.2 Distribution by Age Group

To visualize the split fraction distribution by age, we can create age groups:

```python
# Create age groups
df['age_group'] = pd.cut(df['age'], bins=[15, 30, 40, 50, 60, 70, 80], labels=['15-30', '31-40', '41-50', '51-60', '61-70', '71-80'])

# Plot split fraction distribution by age group
plt.figure(figsize=(12, 8))
sns.violinplot(x='age_group', y='split_fraction', hue='gender', data=df, split=True, inner='quart')
plt.title('Distribution of Split Fractions by Age Group and Gender')
plt.xlabel('Age Group')
plt.ylabel('Split Fraction')
plt.show()
```

## Step 5: Split Fraction vs Finishing Time by Gender

Finally, let's examine the relationship between split fraction and finishing time, differentiating by gender.

```python
# Convert 'final' to seconds for easier plotting
df['final_seconds'] = df['final'].dt.total_seconds()

# Plot split fraction vs finishing time by gender
plt.figure(figsize=(10, 6))
sns.scatterplot(x='final_seconds', y='split_fraction', hue='gender', alpha=0.5, data=df)
plt.title('Split Fraction vs Finishing Time by Gender')
plt.xlabel('Finishing Time (seconds)')
plt.ylabel('Split Fraction')
plt.show()
```

## Conclusion

By following this tutorial, you've visualized and analyzed the marathon race results, focusing on split fractions, their distribution across different demographics, and the relationship between split fractions and finishing times. This analysis can provide insights into how different groups of athletes pace themselves in a marathon.
