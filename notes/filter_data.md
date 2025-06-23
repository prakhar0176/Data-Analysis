# Filtering Data in Pandas

Filtering (also known as subsetting or selecting rows) is a fundamental data manipulation technique used to extract specific rows from a DataFrame that meet certain criteria. It's crucial for isolating relevant data, cleaning datasets, and preparing data for machine learning models.

---

## 🧠 Core Concept

- Use boolean conditions on DataFrame columns
- Syntax: `df[condition]`
- Rows where the condition is `True` are retained

---

## 🔹 Basic Filtering

### 1. Filtering by a Single Column's Value

```python
# Filter for products in 'Electronics' category
electronics = df[df['Category'] == 'Electronics']

# Filter for products with Price > 150
expensive = df[df['Price'] > 150]
```

---

## 🔸 Filtering with Multiple Conditions

- `&` : AND
- `|` : OR
- `~` : NOT
- **Use parentheses around each condition**

```python
# 'Clothes' category AND In_Stock
clothes_in_stock = df[(df['Category'] == 'Clothes') & (df['In_Stock'] == True)]

# 'Electronics' OR 'Furniture'
elec_or_furn = df[(df['Category'] == 'Electronics') | (df['Category'] == 'Furniture')]

# NOT In_Stock
out_of_stock = df[~df['In_Stock']]
```

---

## 🔹 Advanced Filtering Techniques

### 3. Using `isin()`

Filter for values present in a list:

```python
# Products A or C
products_a_c = df[df['Product'].isin(['A', 'C'])]
```

### 4. Using `between()`

For numeric ranges (inclusive):

```python
# Price between 100 and 200
mid_range = df[df['Price'].between(100, 200)]
```

### 5. Handling Null Values

```python
# Where 'Price' is missing
df[df['Price'].isnull()]

# Where 'Category' is NOT missing
df[df['Category'].notnull()]
```

### 6. String Filtering with `.str` Methods

```python
# Contains "Apple"
df[df['Text'].str.contains('Apple')]

# Starts with "B"
df[df['Text'].str.startswith('B')]

# Case-insensitive contains "apple"
df[df['Text'].str.contains('apple', case=False)]
```

---

## ✅ Importance in Machine Learning Pipelines

- **Data Cleaning**: Remove noise/outliers
- **Feature Selection**: Select data relevant to the model
- **Segmentation**: Split data by class/category/date
- **Outlier Removal**: Remove high-leverage points
- **Preprocessing**: Filter rows based on time or user activity

Filtering ensures high-quality, relevant data for more accurate and reliable models.

---

> **Tip:** Combine filtering with `.copy()` to avoid SettingWithCopyWarning:

```python
filtered_df = df[df['Price'] > 150].copy()
```
