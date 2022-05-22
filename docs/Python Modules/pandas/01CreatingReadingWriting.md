---
layout : default
title : 01 Creating, Reading, Writing
nav_order : 1
grand_parent : Python Modules
parent : pandas
---

# Creating, Reading and Writing
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

```python
import pandas as pd
```

## Creating

### pandas DataFrame
```python
pd.DataFrame(data, index, columns, dtype)
```
> [pandas document - pandas.DataFrame](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.html?highlight=dataframe#pandas.DataFrame)

1. data : *ndarray (structured or homogeneous), Iterable, dict, or DataFrame*
    - List-like of List-like : 각 List 는 row 를 나타냄  
    - List-like of Dict : 각 Dict 는 row 를 나타냄  
        - Dict 의 key : columns 의 이름  
          Dict 의 values : columns 의 성분
    - Dict of List-like : 각 List 는 column 을 나타냄
2. index : *Index or array-like*
3. columns : *Index or array-like*
4. dtype : *dtype, default None*


### pandas Series
pandas.Series 는 기본적으로 DataFrame 의 하나의 row data

```python
pd.Series(data, index, name, dtype)
```
> [pandas document - pandas.Series](https://pandas.pydata.org/docs/reference/api/pandas.Series.html?highlight=series#pandas.Series)

1. data : *array-like, Iterable, dict, or scalar value*
2. index : *array-like or Index (1d)*
3. name : *str, optional*
4. dtype : *str, numpy.dtype, or ExtensionDtype, optional*


## Reading
```python
pd.read_csv(filepath_or_buffer, index_col, header, names)
```
>[pandas document - pandas.read_csv](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html?highlight=read_csv#pandas.read_csv)

1. filepath_or_buffer : *str, path object or file-like object*
2. index_col : *int, str, sequence of int / str, or False, optional, default None*
    - which columns to row label?
3. header : *int, list of int, None, default ‘infer’*
    - which rows to column names?
4. names : *array-like, optional*
    - explicitly pass column names

## Writing
```python
pd.DataFrame.to_csv(path_or_buf, encoding)
```
> [pandas document - pandas.DataFrame.to_csv](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_csv.html?highlight=to_csv#pandas.DataFrame.to_csv)

1. path_or_buf : *str, path object, file-like object, or None, default None*
2. encoding : *str, optional*

```python
pd.DataFrame.to_excel(excel_writer, encoding)
```
> [pandas document - pandas.DataFrame.to_excel](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_excel.html#pandas.DataFrame.to_excel)

1. excel_writer : *path-like, file-like, or ExcelWriter object*
2. encoding : *str, optional*
