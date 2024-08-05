
# Exploratory Data Analysis (EDA) Tutorial

Exploratory Data Analysis (EDA) is an essential step in any data science project. It involves summarizing the main characteristics of a dataset, often using visual methods. EDA helps in understanding the data, uncovering patterns, spotting anomalies, and checking assumptions.

## What is Exploratory Data Analysis?

Exploratory Data Analysis (EDA) is a critical process of performing initial investigations on data to discover patterns, spot anomalies, test hypotheses, and check assumptions with the help of summary statistics and graphical representations.

For a comprehensive overview of EDA, you can refer to this [GeeksforGeeks article on Exploratory Data Analysis](https://www.geeksforgeeks.org/what-is-exploratory-data-analysis/).

## Step-by-Step EDA using Python

In this tutorial, we will walk through the process of performing EDA using Python. We will use a dataset containing information about used cars to demonstrate the various steps involved in EDA.

### 1. Importing Libraries

Before we start, we need to import the necessary libraries.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Loading the Dataset

We will load the dataset, which contains information about used cars. You can download the dataset from [this link](https://github.com/sachugowda/Step-by-Step-Exploratory-Data-Analysis-EDA-using-Python/blob/main/used_cars_data.csv).

```python
url = 'https://github.com/sachugowda/Step-by-Step-Exploratory-Data-Analysis-EDA-using-Python/blob/main/used_cars_data.csv'
data = pd.read_csv(url)
```

### 3. Understanding the Data

Let's start by getting a quick overview of the dataset.

```python
# Display the first few rows of the dataset
print(data.head())

# Display basic information about the dataset
print(data.info())

# Summary statistics of numerical columns
print(data.describe())
```

### 4. Handling Missing Data

Missing data is a common issue in datasets. We need to identify and handle it appropriately.

```python
# Check for missing values
print(data.isnull().sum())

# Drop rows with missing values (if applicable)
data_cleaned = data.dropna()

# Alternatively, you can fill missing values with mean/median/mode
data_filled = data.fillna(data.mean())
```

### 5. Univariate Analysis

Univariate analysis involves examining each variable individually. We can look at the distribution of numerical variables and the frequency of categorical variables.

```python
# Distribution of a numerical variable
sns.histplot(data['price'], kde=True)
plt.title('Distribution of Car Prices')
plt.show()

# Frequency of a categorical variable
sns.countplot(x='fuelType', data=data)
plt.title('Count of Cars by Fuel Type')
plt.show()
```

### 6. Bivariate Analysis

Bivariate analysis examines the relationship between two variables. This can involve scatter plots, box plots, and correlation matrices.

```python
# Scatter plot for numerical variables
sns.scatterplot(x='mileage', y='price', data=data)
plt.title('Mileage vs Price')
plt.show()

# Box plot for categorical vs numerical variable
sns.boxplot(x='fuelType', y='price', data=data)
plt.title('Price Distribution by Fuel Type')
plt.show()

# Correlation matrix
corr_matrix = data.corr()
sns.heatmap(corr_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix')
plt.show()
```

### 7. Multivariate Analysis

Multivariate analysis involves examining the relationships between three or more variables. Pair plots and advanced visualizations can be used for this purpose.

```python
# Pair plot for multivariate analysis
sns.pairplot(data, hue='fuelType')
plt.title('Pair Plot of Dataset')
plt.show()
```

### 8. Conclusion

EDA is a crucial step in any data analysis or machine learning project. It helps in understanding the data better and lays the foundation for further analysis or model building.

## Complete EDA Notebook

For a complete walkthrough of EDA using Python, you can refer to this [Jupyter Notebook](https://github.com/sachugowda/Step-by-Step-Exploratory-Data-Analysis-EDA-using-Python/blob/main/DataSciecne_Beginner.ipynb).

---
