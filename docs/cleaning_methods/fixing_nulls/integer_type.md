# INTEGER TYPE COLUMNS
 
- Type - int64

## For Integer type column
We have to follow some steps to fix null values.

### Steps -

**Step 1 :**
- Check how many null values are present.
- Calculate percentage of null values.

**Step 2:**
- If null percentage >= 50 %, drop that column if it is not important.
- Else :
    - Get mean (average)
    - Get median

        - Get their difference (mean - median) or (median - mean)
        - If mean and median is approximately same then use mean.
        - Else :
            - Check for outliers (Use box plots)
            - If outliers present then use median
            - Else use mean
---

Code :
```python
import numpy as np

total_nulls = df.isnull().sum()         # Total null values from each columns
nulls_pct = (total_nulls/len(df))*100   # Missing percentage among each columns

# If nulls_pct >= 50 then drop that column if it is not important
df.drop(columns=[columns], inplace = True)  # Drop columns

# If it is important
mean = df['column'].mean()      # Get mean
median = df['column'].median()  # Get median

differnce = abs(mean - median)  # Get difference
```

### If difference approximately same use mean
```python
df['column'] = df['column'].replace(np.nan, df['column'].mean())
```

### If difference is too much
```python
import seaborn as sns

# use boxplot for detecting outliers
sns.boxplot(
    data=df['column'],
    palette="Set3",
    linewidth=2,
    width=0.6,
    showfliers=True,
    fliersize=5
)
```

### If no outliers
```python
df['column'] = df['column'].replace(np.nan, df['column'].mean())
```

### If outliers
```python
df['column']= df['column'].replace(np.nan, df['column'].median())
```
---

## We can use a simple method to fill null values in numeric type columns.

- We already know that if any column contains outliers then the difference of mean and median will be huge.
- We can check outliers first, if outliers present then we will fill those null values with median else with mean.

Code :
```python

import pandas as pd
import numpy as np

# Create a function which will check outlier
# If outlier detected then it will return True, else False
def is_outlier(col: str, df: pd.DataFrame) -> bool:

    Q1 = df[col].quantile(0.25)
    Q2 = df[col].median()
    Q3 = df[col].quantile(0.75)

    IQR = Q3 - Q1

    lower_limit = Q1 - (IQR * 1.5)
    upper_limit = Q3 + (IQR * 1.5)

    if len(df.loc[df[col] > upper_limit]) > 0 or len(df.loc[df[col] < lower_limit]) > 0:
        return True
    else:
        return False

# Check every column type - [int64, float64]
for column in df.columns:
    if df[column].dtypes == "int64" or df[column].dtypes == "float64:
        missing_pct = np.trunc((df[column].isnull().sum()/len(df))*100)

        if missing_pct <= 50:
            if is_outlier(col=column, df=df):
                df[column] = df[column].replace(np.nan, df[column].median())
            else:
                df[column] = df[column].replace(np.nan, df[column].mean())
```