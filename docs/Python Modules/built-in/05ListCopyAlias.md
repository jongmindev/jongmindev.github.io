---
layout : default
title : List - Copy vs Alias
nav_order : 5
math: mathjax3
grand_parent : Python Modules
parent : built-in
---

# List - Copy vs. Alias
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 0. properties of \<List\>

- **mutable** collection
- **mutable** elements
- **ordered** elements

## 0. memory model of list

Python Lists store *reference* to the objects.

> [Performance Notes](http://web.archive.org/web/20190205055507/http://effbot.org/zone/python-list.htm#performance)  
The list object consists of two internal parts; one object **header**, and one separately allocated **array of object references**. The latter is reallocated as necessary.

## 0. List assignment

When assign a list to a variable, the variable points the header of the list.


## 1. how to copy and make alias

**Copy** : independent (**shallow copy**)

```python
mylist_copy = mylist[:]
```

**Alias** : dependent

```python
mylist_alias = mylist
```


## 2. passed as parameter (as a name only)

Since function parameters are **variables**(just *name*), list parameters cause **aliasing**.

Changing the list inside the function **also changes the original**.


## 3. deep copy

If elements of copied list is **mutable** objects, changing one affects the other list. (**shallow copy**).

When a list is copied, 'new header + new array of existing reference' is created.  
Thus if the elements of the original list is immutable, then no problem (totally independent).  
But if the elements of the original list is mutable, then it's dependent.

Thus if you need a totally independent copied list (**deep copy**), use ```copy.deepcopy```. ([reference](https://stackoverflow.com/questions/56028405/difference-between-array-copy-vs-numpy-copyarray))


## 4. as an iterator (```for``` loop)

### looping over each element's value (unchanged original)

```python
values = [10, 11, 12, 13, 14, 15]
for num in values:              # aliasing
    num = num * 2               # just reassignment
values
```

output :

```python
[10, 11, 12, 13, 14, 15]        # no change
```

### looping over list indices (changed original)

```python
values = [10, 11, 12, 13, 14, 15]
for i in range(len(values)):
    values[i] = values[i] * 2   # direct access
values
```

output :

```python
[20, 22, 24, 26, 28, 30]        # change
```
