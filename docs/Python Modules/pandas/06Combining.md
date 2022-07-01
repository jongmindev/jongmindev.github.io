---
layout : default
title : 06 Combining
nav_order : 6
grand_parent : Python Modules
parent : pandas
---

# Combining
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## Comparison

In order of increasing complexity, these are `concat()`, `join()`, and `merge()`

|`concat()`|`join()`|`merge()`|
|:--------:|:------:|:-----:|
|가로로 합치기 O<br/>세로로 합치기 O|~~가로로 합치기 X~~<br/>세로로 합치기 O|~~가로로 합치기 X~~<br/>세로로 합치기 O|
|left_on X<br/>right_on X|left_on O<br/>right_on X|left_on O<br/>right_on O|
|join : *{‘inner’, ‘outer’}*|how : *{‘left’, ‘right’, ‘outer’, ‘inner’}*|how : *{‘left’, ‘right’, ‘outer’, ‘inner’, ‘cross’}*|


## 3 Methods for Combining

### `concat()`
Concatenate pandas objects along **a particular axis(rows[default] or columns)**.
```python
pandas.concat(objs, axis=0, join='outer')
```
> [pandas document - pandas.concat](https://pandas.pydata.org/docs/reference/api/pandas.concat.html?highlight=concat#pandas.concat)

1. objs : *a sequence or mapping of Series or DataFrame objects*
2. axis : *{0/’index’, 1/’columns’}, default 0*
3. join : *{‘inner’, ‘outer’}, default ‘outer’*

### `join()`
Join **columns** with other DataFrame either **on index** or **on a key column(of given DataFrame)**.  

`df.join(other, on='column_name')` : uses *column_name* of *df* and (only) *index* of *other*.  
Thus if we want to join using the key columns, **we need to set key to be the index** in both df and other. The joined DataFrame will have key as its index.
```python
DataFrame.join(other, on=None, how='left', lsuffix='', rsuffix='')
```
> [pandas document - pandas.DataFrame.join](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html?highlight=join#pandas.DataFrame.join)

1. other : *DataFrame, Series, or list of DataFrame*
2. on : *str, list of str, or array-like, optional*
    - specify column or index to join on (criteria)
    - if `None`, then index-on-index
3. how : *{‘left’, ‘right’, ‘outer’, ‘inner’}, default ‘left’*
    - left : use calling frame’s index (or column if on is specified)
    - right : use other’s index.
    - outer : union , and sort it lexicographically.
    - inner : intersection, preserving the order of the calling’s one(left keys).
    - cross : cartesian product, preserves the order of the left keys.
4. lsuffix, rsuffix : *str, default ‘’*



### `merge()`
```python
DataFrame.merge(right, how='inner', | on=None, | left_on=None, right_on=None, | left_index=False, right_index=False, sort=False, suffixes=('_x', '_y'))

pandas.merge(left, right, how='inner', | on=None, | left_on=None, right_on=None, | left_index=False, right_index=False, sort=False, suffixes=('_x', '_y')
```
>[pandas document - pandas.DataFrame.merge](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.merge.html?highlight=merge#pandas.DataFrame.merge)

>[pandas document - pandas.merge](https://pandas.pydata.org/docs/reference/api/pandas.merge.html?highlight=merge#pandas.merge)

1. left : *DataFrame*
2. right: *DataFrame or named Series*
3. how : *{‘left’, ‘right’, ‘outer’, ‘inner’, ‘cross’}, default ‘inner’*
4. on : label or list
     - Column or index level names to join on in the left DataFrame. Must be common.
5. left_on, right_on : *label or list, or array-like*
6. left_index, right_index : *bool, default False*
     - Use the index from the left DataFrame as the join key(s).
7. sort : *bool, default False*
8. suffixes : *list-like, default is (“_x”, “_y”)*
