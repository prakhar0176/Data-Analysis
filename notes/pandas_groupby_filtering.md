## 🔍 Filtering Rows in Pandas

- Use boolean conditions to filter rows.
- Combine conditions with `&`, `|`, and wrap each in `()`.

### Example:

```python
df[df['Age'] < 18]                     # Passengers under 18
df[df['Fare'] > 100]                  # High-paying passengers
df[(df['Sex'] == 'female') & (df['Pclass'] == 1)]  # First-class females
```

## 🔢 Sorting in Pandas

- `sort_values(by='col')` sorts by a column.
- You can sort by multiple columns and set the direction.

### Example:

```python
df.sort_values(by='Fare', ascending=False)
df.sort_values(by=['Age', 'Fare'], ascending=[True, False])
```

## Sort by index:

```python
df.sort_index()  # Useful after setting custom index
```

## 🔁 Pandas GroupBy and Aggregation

### Purpose:

Used to split data into groups and apply summary stats like mean, sum, median, count, etc.

---

### 📌 Syntax:

```python
df.groupby('column')['other_column'].agg_function()

```

### Example

```
df.groupby('Pclass')['Fare'].mean()        # Avg fare by class
df.groupby('Sex')['Age'].mean()            # Avg age by gender
df.groupby('Pclass')['Survived'].sum()     # Total survivors by class

# Multiple aggregations
df.groupby('Pclass').agg({
    'Fare': 'mean',
    'Age': 'median',
    'Survived': 'sum'
})

```

**Tips:**

- .agg() is used for multiple column summarization.
- You can rename columns after aggregation for clarity.

### 🔄 Resetting Index in Pandas

- Use `reset_index()` to flatten hierarchical index after `groupby()`.
- Use `drop=True` to discard the old index completely.

```python
# Keep groupby keys as columns
df.groupby(['Sex', 'Pclass'])['Survived'].sum().reset_index()

# Drop old index and keep clean numeric index
df.reset_index(drop=True, inplace=True)

```
