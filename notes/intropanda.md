## Introduction to Pandas with Examples

### Comparison to NumPy
While both NumPy and Pandas are fundamental tools in the data science toolkit, they serve different purposes and are optimized for different types of tasks:

- **NumPy**: Primarily used for numerical computations on arrays and matrices. It is highly efficient for performing mathematical operations and is the foundation for many other data science libraries in Python.
  ```python
  import numpy as np

  # Creating a NumPy array
  np_array = np.array([1, 2, 3, 4, 5])
  print(np_array)

  # Performing a mathematical operation
  np_array = np_array * 2
  print(np_array)
  ```

- **Pandas**: Built on top of NumPy, it is designed for handling and analyzing structured data. Pandas introduces two primary data structures, Series and DataFrame, which allow for more complex data manipulation.
  ```python
  import pandas as pd

  # Creating a Pandas Series
  pd_series = pd.Series([1, 2, 3, 4, 5])
  print(pd_series)

  # Creating a Pandas DataFrame
  data = {'A': [1, 2, 3], 'B': [4, 5, 6]}
  pd_dataframe = pd.DataFrame(data)
  print(pd_dataframe)
  ```

### Key Differences
1. **Data Structures**:
   - **NumPy**: Uses n-dimensional arrays (ndarrays).
   - **Pandas**: Uses Series (1-dimensional) and DataFrames (2-dimensional).

2. **Functionality**:
   - **NumPy**: Optimized for numerical operations and is less intuitive for handling tabular data.
   - **Pandas**: Provides rich functionality for data manipulation, such as handling missing data, merging datasets, and working with time series data.

3. **Indexing**:
   - **NumPy**: Uses integer-based indexing.
   - **Pandas**: Allows for more flexible indexing with labels, enabling easier access to data.

### Example: Data Analysis with Pandas
```python
# Importing Pandas
import pandas as pd

# Creating a DataFrame
data = {
    'Name': ['Alice', 'Bob', 'Charlie', 'David'],
    'Age': [24, 27, 22, 32],
    'City': ['New York', 'Los Angeles', 'Chicago', 'Houston']
}
df = pd.DataFrame(data)
print("DataFrame:\n", df)

# Accessing a column
print("Ages:\n", df['Age'])

# Filtering data
print("People older than 25:\n", df[df['Age'] > 25])

# Handling missing data
df.loc[4] = ['Eve', None, 'San Francisco']
print("DataFrame with missing data:\n", df)
df['Age'].fillna(df['Age'].mean(), inplace=True)
print("DataFrame after filling missing data:\n", df)
```

Through these examples and comparisons, you'll gain a better understanding of how Pandas builds upon NumPy's capabilities, offering more sophisticated tools for data manipulation and analysis.
