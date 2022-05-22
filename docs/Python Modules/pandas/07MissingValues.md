---
layout : default
title : 07 Missing Values
nav_order : 7
grand_parent : Python Modules
parent : pandas
math : mathjax3
---

# Missing Values
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## Missing Data

### `isnull()` == `isna()` (alias)  $\longleftrightarrow$  `notnull()` == `notna()` (alias)

```python
DataFrame.isnull()          # return : DataFrame
Series.isnull()             # return : Series
Index.isnull()              # return : numpy.ndarray[bool]
pandas.isnull(obj)          # return : bool or array-like of bool
```
> [pandas document - pandas.DataFrame.isna](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.isna.html?highlight=isna#pandas.DataFrame.isna)  

return : *boolean_mask*

Q. How many missing values in df.column_name? The following 3 are equivalent.  
```python
df.column_name.isna().sum()             # equivalent
pd.isna(df.coloumn_name).sum()          # equivalent
len(df[df.coloumn_name.isna()])         # equivalent
```

### `fillna()`
```python
DataFrame.fillna(value, method, axis, inplace)
Series.fillna(value, method, axis, inplace)
Index.fillna(value)         # value : scalar only
```
>[pandas document - pandas.DataFrame.fillna](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.fillna.html?highlight=fillna#pandas.DataFrame.fillna)

1. value : *scalar, dict, Series, or DataFrame*
    - *scalar* : value to use to fill holes
    - *dict, Series, or DataFrame* : specify values to use for each index (for a Series) or column (for a DataFrame)
    - ~~*list*~~ : unable
2. method : *{‘backfill’, ‘bfill’, ‘pad’, ‘ffill’, None}, default None*
    - pad / ffill: propagate last valid observation forward to next valid
    - backfill / bfill: use next valid observation to fill gap.
3. axis : *{0 or ‘index’, 1 or ‘columns’}*
4. inplace : *bool, default False*

### `replace()`
```python
DataFrame.replace(to_replace, value, inplace)
Series.replace(to_replace, value, inplace)
```
> [pandas document - pandas.DataFrame.replace](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.replace.html?highlight=replace#pandas.DataFrame.replace)

1. to_replace : *str, regex, list, dict, Series, int, float, or None*
    - how to find the values that will be replaced
2. value : *scalar, dict, list, str, regex, default None*
    - value to replace any values matching to_replace with
3. inplace : *bool, default False*

