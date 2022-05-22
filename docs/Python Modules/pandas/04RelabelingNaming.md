---
layout : default
title : 04 Relabeling Naming
nav_order : 4
parent : pandas
math : mathjax3
---

# Relabeling and Naming
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## 'ReLabeling' (renaming)

### `rename()`
Alter axes labels. (usually column labels)

Recommanded use only for 'relabeling' column.  
For 'relabeling' index, use `set_index()` below.

```python
DataFrame.rename(mapper, axis, | index, columns, inplace)     # row/column label 변경
Series.rename(index, inplace)
Index.rename(name, inplace)
```
>[pandas document - pandas.DataFrame.rename](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rename.html?highlight=rename#pandas.DataFrame.rename)

>[pandas document - pandas.Series.rename](https://pandas.pydata.org/docs/reference/api/pandas.Series.rename.html?highlight=rename#pandas.Series.rename)

>[pandas document - pandas.Index.rename](https://pandas.pydata.org/docs/reference/api/pandas.Index.rename.html?highlight=rename#pandas.Index.rename)

1. mapper : *dict-like or function*
2. axis : *{0 or ‘index’, 1 or ‘columns’}, default 0*
3. index : *dict-like or function*
4. columns : *dict-like or function*
5. inplace : *bool, default False*


### `set_index()` $\longleftrightarrow$ `reset_index()`
`set_index()` : Set the index (row labels and name) using one or more existing columns or arrays(of the correct length).
```python
dataframe.set_index(keys, inplace=False)        # 기존 index 를 columns 중 하나로 대체
```
1. keys : *label or array-like or list of labels/arrays*
    - *label* of a column / *list of labels* of columns
    - *List-like* (of the correct length)

(cf) `set index()` 사용 시 기존의 index 는 삭제됨.
```python
dataframe['new_column_name'] = dataframe.index
dataframe.set_index('coloumn_name', inplace=True)

>>> dataframe
# 기존의 index 를 새로운 칼럼에 저장하고,
# 기존의 column 중 하나로 index 를 대체.
```

`reset_index()` : Reset(remove) the index, or a level of it.
```python
dataframe.reset_index(level=None, drop=False, inplace=False)    # opposite of set_index()
```
1. level : *int, str, tuple, or list, default None*
    - Only remove the given levels from the index. Removes all levels by default.
2. drop : *bool, default False*
    - Do not try to insert index into dataframe columns. This resets the index to the default integer index.
3. inplace : *bool, default False*

>[pandas document - pandas.DataFrame.set_index](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.set_index.html?highlight=set_index#pandas.DataFrame.set_index)

>[pandas document - pandas.DataFrame.reset_index](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html#pandas.DataFrame.reset_index)



## 'Naming' (renaming)

### `dataframe.index.name` (attribute)
```python
dataframe.index.name = 'row_axis_name'
```
`pandas.Index.name` → *'name'* of row_axis  
`pandas.Series.name` → *'label'* of row/column


### `rename_axis()`
Set the 'name' of the axis for the index or columns.

```python
DataFrame.rename_axis(mapper, axis, | index, columns, inplace)     # row/column label 변경
Series.rename_axis(mapper, axis, | index, inplace)
```
```console
>>> dataframe.rename_axis("wines", axis='rows').rename_axis("fields", axis='columns')
fields	country 	designation	  points	price
wines													
0	      Italy	   Vulkà Bianco	      87      NaN
...         ...             ...      ...      ...
```

> [pandas document - pandas.DataFrame.rename_axis](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rename_axis.html?highlight=rename_axis#pandas.DataFrame.rename_axis)

1. mapper : *scalar, list-like, optional*
2. axis : *{0 or ‘index’, 1 or ‘columns’}, default 0*
3. index : *scalar, list-like, dict-like or function, optional*
4. columns : *scalar, list-like, dict-like or function, optional*
5. inplace : *bool, default False*
