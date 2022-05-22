---
layout : default
title : 05 Grouping Sorting
nav_order : 5
grand_parent : Python Modules
parent : pandas
---

# Grouping and Sorting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## Grouping (`groupby()`)
1. `groupby()` created a group of (primitive) dataframe which allotted the same column values to the rows. (if `axis='index'`)  
2. return 되는 객체(`pandas.core.groupby`)의 구조 : We generate each group as being a slice of our DataFrame containing only data with values that match. : 기준열(행)의 값에 따라 dataframe 을 분류(분리)해 놓은 것.  
3. method 작동 구조 (roughly) : 원래의 dataframe 을 기준에 따라 여러 dataframe 덩어리로 나누고, 각각의 dataframe 에 대하여 덩어리씩 method() 적용.

`groupby()` 의 return 인 GroupBy 자체보다는 이 객체가 가지고 있는 수많은 method 가 중요하다.  
(ex) `dataframe.groupby('column_name').column_name.count()` == `dataframe.column_name.value_counts()` : just shortcut

```python
DataFrame.groupby(by, axis)         # df.groupby('column_name')
```
>[pandas document - pandas.DataFrame.groupby](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html?highlight=groupby#pandas.DataFrame.groupby)

1. by : *mapping, function, label, or list of labels*  
    - *list of labels* : multiple classification criteria -> multi-index dataframe  
2. axis: *{0 or ‘index’, 1 or ‘columns’}, default 0*  

return : pandas.core.groupby.generic.**DataFrameGroupBy**

### useful Groupby methods
```python
Groupby.agg([callable, callable, ...])              # 한꺼번에 적용
DataFrameGroupBy.coloumn_name.count() == DataFrameGroupBy.size()
DataFrameGroupBy.min()
DataFrameGroupBy.describe()
DataFrameGroupBy.first()
DataFrameGroupBy.last()
DataFrameGroupBy.apply()
```


## Sorting


### sort by **values** of rows/columns
```python
DataFrame.sort_values(by, axis, ascending, inplace)
```
>[pandas document - pandas.DataFrame.sort_values](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_values.html?highlight=sort_value)  

1. by : *str or list of str*
    - *list of str* -> multiple criteria
2. axis : *{0 or ‘index’, 1 or ‘columns’}, default 0*
3. ascending : *bool or list of bool, default True*
    - *list of bool* -> must match the length of the by
4. inplace : *bool, default False*


### sort by **index** of row/column
```python
DataFrame.sort_index(axis, level, ascending, inplace)
```
>[pandas document - pandas.DataFrame.sort_index](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.sort_index.html?highlight=sort_index#pandas.DataFrame.sort_index)

1. axis : *{0 or ‘index’, 1 or ‘columns’}, default 0*
2. level : *int or level name or list of ints or list of level names*
3. ascending : *bool or list-like of bools, default True*
    - *list-like of bool* -> for multiindex, indivisually
4. inplace : *bool, default False*
