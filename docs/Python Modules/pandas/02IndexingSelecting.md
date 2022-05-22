---
layout : default
title : 02 Indexing, Selecting
nav_order : 2 
parent : pandas
---

# Indexing, Selecting
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


```python
import pandas as pd
```

## 4 Ways of Indexing and Selecting

1. as an attribute
    ```python
    dataframe.column_name
    ```

2. indexing operater []
    ```python
    dataframe['column_name']                                # -> Series
    dataframe[['column_name_1', 'column_name_2', ...]]      # -> DataFrame
    dataframe['column_name'][5]
    ```
    ```python
    dataframe[4:7]
    dataframe['row_index':'row_index']              # slice is only for ROWs
    ```

3. iloc attribute : **integer**  
    Allowed inputs are:  
    `5` (integer),  
    `[4, 3, 0]` (list),  
    `1:7` (slice),  
    `dataframe.column_name == 'column_name` (condition : boolean array),  
    `callable function` (callable with one argument)

    ```python
    dataframe.iloc[0]                               # row
    dataframe.iloc[:, 0]                            # row, column
    ```
    > [pandas document - pandas.DataFrame.iloc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html?highlight=iloc#pandas.DataFrame.iloc)

4. loc attribute : **label**
    ```python
    dataframe.loc['row_label']                      # row
    dataframe.loc['row_label', 'column_name']       # row, column
    ```
    > [pandas document - pandas.DataFrame.loc](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html?highlight=loc#pandas.DataFrame.loc)


## MultiIndex and Advanced Indexing

### `reset_index()` Method : 별도 설명
In general the multi-index method you will use most often is the one for converting back to a regular index.
