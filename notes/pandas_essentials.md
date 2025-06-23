# Pandas Essentials – Data Cleaning & Exploration

> 📁 This document contains essential Pandas commands and techniques for Data Cleaning & Exploratory Data Analysis (EDA), using real-world datasets like Titanic.  
> Useful for Data Analyst interviews, case studies, and day-to-day EDA work.

---

## 📊 Exploratory Data Analysis (EDA)

EDA is the process of investigating a dataset to understand its main characteristics before building models or making predictions.

### 🎯 Goals:

- Understand the structure of the data (rows, columns, data types, missing values)
- Uncover patterns and trends in features
- Detect anomalies or outliers that may skew results
- Validate assumptions for modeling
- Form hypotheses and guide preprocessing or feature engineering

### 🔍 Common EDA Techniques:

- `df.head()`, `df.tail()` – View sample records
- `df.info()`, `df.describe()` – Summarize structure and statistics
- `df.isnull().sum()` – Check for missing data
- `df.duplicated()` – Spot duplicate records
- `value_counts()`, `groupby()`, `pivot_table()` – Explore distributions and relationships
- Visual tools: histograms, boxplots, scatter plots, correlation heatmaps

### 🧠 Why It Matters:

Good EDA helps you clean data more effectively and choose better models/features. It’s the **foundation of any robust data project**.

---

## 🔎 Basic Exploration Commands

| Function/Method                         | Purpose                                                         |
| --------------------------------------- | --------------------------------------------------------------- |
| `df.head()`                             | Displays the first `n` rows of the DataFrame (default is 5)     |
| `df.shape`                              | Returns the dimensions of the DataFrame (rows, columns)         |
| `df.info()`                             | Displays column names, types, non-null counts, and memory usage |
| `df.describe()`                         | Generates descriptive statistics for numeric columns            |
| `df.isnull().sum()`                     | Shows the number of missing (NaN) values in each column         |
| `df.duplicated().sum()`                 | Counts the number of duplicated rows                            |
| `df.duplicated(subset=['Name', 'Age'])` | Checks for duplicate rows based on selected columns             |
| `df['Age'].fillna(...)`                 | Fills missing values in the 'Age' column                        |
| `df.drop(...)`                          | Removes rows or columns from the DataFrame                      |
| `df.rename(...)`                        | Renames columns or index labels                                 |

---

## 📌 `df.info()` – Dataset Structure Summary

### Key Outputs:

- **Index Range**: e.g., `RangeIndex: 891 entries, 0 to 890`
- **Columns**: Names, types, and non-null counts
- **Dtype**: Data type of each column
- **Memory Usage**: RAM used by DataFrame

### Why it’s important:

- Detect missing data quickly
- Verify data types before analysis
- Optimize memory usage if needed

## df.info()

Provides a concise summary of the DataFrame including data types, non-null values, and memory usage.

### Key Outputs:

- **Index Range**: Shows the range of the DataFrame index (e.g., RangeIndex: 891 entries, 0 to 890).
- **Column Names**: Lists all columns in the dataset.
- **Non-Null Count**: Shows how many non-missing (non-null) values each column has.
- **Dtype**: Displays the data type of each column (e.g., `int64`, `float64`, `object`).
- **Memory Usage**: Gives an estimate of how much memory the DataFrame occupies.

### Why it’s important:

- Helps detect missing data quickly.
- Useful to verify data types before analysis or preprocessing.
- Reveals large memory usage, which can suggest optimizing with category types.

### Usage:

```python
df.info()
```

## df.describe()

Returns descriptive statistics for numeric columns by default. It's used to quickly understand the central tendency, spread, and shape of a dataset's distribution.

### Breakdown of statistics provided:

- **count**: Number of non-null (non-missing) entries in the column.
- **mean**: The arithmetic average of the values. Useful for identifying the central trend.
- **std (Standard Deviation)**: Measures how spread out the values are around the mean. High std = more variation.
- **min**: The smallest value in the column.
- **25% (Q1)**: First quartile. 25% of the data lies below this value.
- **50% (Median/Q2)**: Middle value of the data. Useful when the mean is affected by outliers.
- **75% (Q3)**: Third quartile. 75% of the data lies below this value.
- **max**: The largest value in the column.

### Usage:

```python
df.describe()
use df.describe(include='object') or include='all' to handle categorical data too.
```

## Handling Missing Data

## df.isnull()

Identifies missing (null/NaN) values in the DataFrame.

### Syntax:

```python
df.isnull()     # - Returns a DataFrame of the same shape with Boolean values (True for null, False otherwise).
df.isnull().sum()  # Common pattern to count nulls column-wise
```

## Pandas `fillna()` – Handling Missing Values

The `fillna()` method in Pandas is used to **replace missing values (NaN)** with specified values or filling methods.

---

### 🔧 Syntax

```python
DataFrame.fillna(value=None, method=None, axis=None, inplace=False, limit=None, downcast=None)

```

### 📋 Parameter Summary Table

| Parameter  | Type                            | Description                                               |
| ---------- | ------------------------------- | --------------------------------------------------------- |
| `value`    | scalar, dict, Series, DataFrame | Value(s) to replace NaNs with                             |
| `method`   | `'ffill'` or `'bfill'`          | Fill using forward/backward propagation                   |
| `axis`     | `0`/`'index'`, `1`/`'columns'`  | Axis to apply fill method along                           |
| `inplace`  | bool (`True`/`False`)           | Modify the original DataFrame or return a copy            |
| `limit`    | int                             | Max number of NaNs to fill (used with `method`)           |
| `downcast` | dict                            | Attempt downcasting to smaller types (e.g., float to int) |

## 🧹 Pandas `dropna()` – Removing Missing Data

The `dropna()` method is used to **remove rows or columns** with missing values (`NaN`) from a DataFrame.

---

### 🔧 Syntax

```python
DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)
```

### 📋 `dropna()` Parameter Summary Table

| Parameter | Type                               | Description                                                |
| --------- | ---------------------------------- | ---------------------------------------------------------- |
| `axis`    | `0` / `'index'`, `1` / `'columns'` | Determines if rows (`0`) or columns (`1`) are removed      |
| `how`     | `'any'` or `'all'`                 | Drop if _any_ or _all_ values are NaN                      |
| `thresh`  | int                                | Keep only rows/columns with at least this many non-NaNs    |
| `subset`  | list-like                          | Labels (e.g., column names) to consider for NaNs           |
| `inplace` | bool                               | If `True`, modifies original; else returns a new DataFrame |

## ❓ Pandas `isna()` – Detecting Missing Values

The `isna()` method is used to **identify missing (NaN) values** in a DataFrame, Series, or array-like object. It returns a Boolean mask where `True` indicates a missing value.

---

### 🔧 Syntax

```python
pd.isna(obj)
# or
DataFrame.isna()
Series.isna()
```

### 📋 `isna()` Parameter Summary Table

| Parameter | Type       | Description                                             |
| --------- | ---------- | ------------------------------------------------------- |
| obj       | array-like | (Only for pd.isna()) Object to check for missing values |

## ✅ Pandas `notna()` – Detecting Non-Missing Values

The `notna()` method is used to **identify non-missing (valid) values** in a DataFrame, Series, or array-like object. It returns a Boolean mask where `True` indicates a non-NaN value.

---

### 🔧 Syntax

```python
pd.notna(obj)
# or
DataFrame.notna()
Series.notna()
```

### 📋 `notna()` Parameter Summary Table

| Parameter | Type       | Description                                                  |
| --------- | ---------- | ------------------------------------------------------------ |
| obj       | array-like | (Only for pd.notna()) Object to check for non-missing values |

### 🧠 Notes

- `notna()` is the logical inverse of `isna()`.
- Commonly used to filter out non-missing values:

  ```python
  df[df['A'].notna()]
  ```

## Handling Duplicates in Data Analysis

When working with datasets, especially large ones, it is common to encounter duplicate entries. These can skew analysis, cause overcounting, or lead to biased outcomes. Pandas provides powerful tools to detect and handle such duplicates.

### `duplicated()` Method

- **Purpose**: Returns a Boolean Series indicating whether each row is a duplicate of a previous row.
- **Usage**:
  ```python
  df.duplicated()
  ```

### Parameters of `duplicated()` in Pandas

| Parameter      | Type                                 | Description                                                                                                                                                             |
| -------------- | ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `subset`       | label or list-like                   | Column label(s) to consider when identifying duplicates. Defaults to all.                                                                                               |
| `keep`         | {`'first'`, `'last'`, `False`}       | Determines which duplicates to mark as `True`: <br> `'first'` (default): Keeps first occurrence <br> `'last'`: Keeps last occurrence <br> `False`: Marks all duplicates |
| `inplace`      | `bool` (deprecated)                  | Whether to perform operation in-place. Deprecated in newer versions.                                                                                                    |
| `ignore_index` | `bool` (available in newer versions) | Whether to reset the index of the result. Useful when chaining operations.                                                                                              |

> 📝 **Note**: As of recent pandas versions, `inplace` is deprecated and might be removed in future releases. Always refer to the latest documentation for updates.

### `drop_duplicates()` Method

- **Purpose**: Removes duplicate rows from a DataFrame.
- **Usage**:
  ```python
  df.drop_duplicates()
  ```

### Parameters of `drop_duplicates()` in Pandas

| Parameter      | Type                           | Description                                                                                                                                                  |
| -------------- | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `subset`       | label or list-like             | Column label(s) to consider when identifying duplicates. Defaults to all.                                                                                    |
| `keep`         | {`'first'`, `'last'`, `False`} | Determines which duplicate to keep: <br> `'first'` (default): Keeps first occurrence <br> `'last'`: Keeps last occurrence <br> `False`: Drops all duplicates |
| `inplace`      | `bool`                         | If `True`, performs operation in-place and returns `None`. Default is `False`.                                                                               |
| `ignore_index` | `bool`                         | If `True`, the resulting DataFrame index will be labeled 0, 1, …, n - 1. Default is `False`.                                                                 |

> 📝 **Note**: Use `ignore_index=True` when you don’t need to retain the original index after dropping duplicates, especially useful in chained operations.

## Renaming Columns and Index in Pandas

The `rename()` method in pandas allows you to **change the names of the index or column labels**. This is useful for making DataFrame labels more descriptive, readable, or consistent.

### Syntax

```python
DataFrame.rename(mapper=None, *, index=None, columns=None, axis=None, copy=True, inplace=False, level=None, errors='ignore')
```

**Example**

```
# Rename column 'A' to 'Alpha'
df_renamed = df.rename(columns={'A': 'Alpha'})

# Rename index 0 to 'Row1'
df_renamed = df.rename(index={0: 'Row1'})

```

### Parameters of `rename()` in Pandas

| Parameter | Type                               | Description                                                                                         |
| --------- | ---------------------------------- | --------------------------------------------------------------------------------------------------- |
| `mapper`  | dict, Series, function             | A general mapping to rename labels for a specific axis (index or columns).                          |
| `index`   | dict, Series, function             | A mapping to rename the index (rows). Use instead of `mapper` for clarity.                          |
| `columns` | dict, Series, function             | A mapping to rename the columns.                                                                    |
| `axis`    | {0 or `'index'`, 1 or `'columns'`} | Axis along which to apply the renaming. Ignored if `index` or `columns` are provided.               |
| `inplace` | bool                               | If `True`, modifies the original DataFrame. Default is `False`.                                     |
| `level`   | int or level name                  | For MultiIndex: specifies the level(s) to apply the renaming.                                       |
| `errors`  | {'ignore', 'raise'}                | Behavior when a label is not found. `'ignore'` will silently ignore, `'raise'` will throw an error. |

## Dropping Data in Pandas with `drop()`

The `drop()` method is used to **remove rows or columns** from a DataFrame. It is a flexible and commonly used tool for cleaning and reshaping data.

### Syntax

```python
DataFrame.drop(labels=None, *, axis=0, index=None, columns=None, level=None, inplace=False, errors='raise')
```

### Parameters of `drop()` in Pandas

| Parameter | Type                               | Description                                                                                              |
| --------- | ---------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `labels`  | single label or list-like          | Index or column labels to drop. Optional if `index` or `columns` is used.                                |
| `axis`    | {0 or `'index'`, 1 or `'columns'`} | Determines whether to drop from rows (`0` or `'index'`) or columns (`1` or `'columns'`). Default is `0`. |
| `index`   | single label or list-like          | Alternative to `labels`. Specifies row labels to drop.                                                   |
| `columns` | single label or list-like          | Alternative to `labels`. Specifies column labels to drop.                                                |
| `level`   | int or level name                  | If the axis is a MultiIndex, this specifies the level from which labels will be removed.                 |
| `inplace` | bool                               | If `True`, modifies the DataFrame in place and returns `None`. Default is `False`.                       |
| `errors`  | {'ignore', 'raise'}                | If `'ignore'`, suppresses errors for nonexistent labels. Default is `'raise'`.                           |
