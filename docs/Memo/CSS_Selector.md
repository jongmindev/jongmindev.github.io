---
layout : default
title : CSS Selector
nav_order : 1
parent : Memo
---

# CSS Selector
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

[CSS Selector Reference](https://www.w3schools.com/cssref/css_selectors.asp)

## Selectors

|Selector|Example|
|:------:|:------|
|element|p|
|.class||
|#id||
|[attribute="value"]|[img src="url"]|
|element:nth-child(n)|p:nth-child(2) <br/> → 2nd \<p> of its parent|
|* (all)||

## Operators

|Operator|Example|Description|
|:------:|:-----:|:---------:|
|OR|element,element|,(comma)|
|AND|.class1.class2|(no whitespace)|
|descendant|element element|(whitespace)|
|child|element>element|>|
