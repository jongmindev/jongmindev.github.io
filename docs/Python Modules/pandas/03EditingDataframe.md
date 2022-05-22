---
layout : default
title : 03 Editing Dataframe
nav_order : 3
parent : pandas
---

# Editing DataFrame
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## Append/Change Values
closely related to indexing/selecting

```python
dataframe.loc['row_name'] = data                                # single row
dataframe.loc[['row_name_1', 'row_name_2', ... ]] = data        # multiple rows (change only)
dataframe.loc[['row_name_1st' : 'row_name_last']] = data        # multiple rows (change only)
dataframe.loc[boolean_mask] = data                              # conditional rows (change only)
```
```python
dataframe['column_name'] = data                                 # single column
dataframe[['column_name_1, column_name_2, ... ']] = data        # multiple columns
```
```python
dataframe.loc['row_name', 'column_name'] = data                 # single entry
dataframe.iloc[[1, 3], [1, 4]] = data               # multiple entries (change only) (1, 1) (1, 4) (3, 1) (3, 4)
```


## Delete
```python
dataframe.drop(label, axis, | index, columns, inplace)        # row/column 제거
```
> [pandas document - pandas.DataFrame.drop](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.drop.html?highlight=drop#pandas.DataFrame.drop)

1. labels, index, columns : *single label or list-like*
    - `labels, axis=0` is equivalent to `index=labels`.
    - `labels, axis=1` is equivalent to `columns=labels`.
2. axis : *{0 or ‘index’, 1 or ‘columns’}*


## Data type

### `dtypes`
```python
DataFrame.dtypes            # return : pandas.Series of data_type
Series.dtype
Index.dtype
```
> [pandas document - pandas.DataFrame.dtypes](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.dtypes.html?highlight=dtypes#pandas.DataFrame.dtypes)

### `astype()`
```python
DataFrame.astype(dtype)
Series.astype(dtype)
Index.astype(dtype)
```
> [pandas document - pandas.DataFrame.astype](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html?highlight=astype#pandas.DataFrame.astype)

1. dtype : *data type(str), or dict of column name -> data type*
