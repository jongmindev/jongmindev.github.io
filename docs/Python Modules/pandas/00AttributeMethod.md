---
layout : default
title : pandas
nav_order : 3
parent : Python Modules
has_children : true
---

# pandas
{: .no_toc }

DESCRIPTION
{: .fs-6 .fw-300 }

---

## Attributes
DataFrame.index  
DataFrame.columns  


## Methods

|method|DataFrame|Series|Index|note|
|:----:|:-------:|:----:|:---:|----|
|describe|O|O|X||
|head|O|O|X||
|unique|X|O|O||
|value_counts|O|O|O|Return a Series containing counts of unique rows|
|sort_values|O|O|O|by values (along either axis)|
|sort_index|O|O|X|by labels (along an axis)|
|isnull|O|O|O||
|notnull|O|O|O||
|astype|O|O|O||
|to_numpy|O|O|O|convert to NumPy array : values() 대체|
|argmax|X|O|O|Return row integer position -> iloc[]|
|idxmax|O|O|X|Return label -> loc[]|
|isin|O|O|O|완전 일치 -> boolean_mask <br/> df.isin(values) : df 값들이 values 중에 있는지|
|str.contains|X|O|X|문자열 부분 일치(포함) -> boolean_mask <br/> Series.str.contains(pat) : pat 패턴이 Series 값에서 나타는지|
|str.split|X|O|X|-> Series, Index, DataFrame or MultiIndex of splitted str list|
|str.startswith|X|O|X|-> Series or Index of bool (boolean_mask)|
|apply|O|O|X|★apply a function **along on axis**(DataFrame)/values(Series)<br/>[comparison : apply, applymap, map](https://towardsdatascience.com/introduction-to-pandas-apply-applymap-and-map-5d3e044e93ff)|
|applymap|O|X||★apply a function **elementwise**|
|map|X|O|O|★substitute each value with another value(**elementwise**)|
|sum|O|O|X|True=1 / False=0|
|iterrows|O|X|X|Iterate over DataFrame rows as (index, Series) pairs.|
