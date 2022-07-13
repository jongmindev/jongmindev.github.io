---
layout : default
title : Magic Method
nav_order : 1
math: mathjax3 
grand_parent : Python Modules
parent : built-in
---

# Magic Method
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---


## some magic methods

[파이썬 더블 언더스코어: Magic Method](https://corikachu.github.io/articles/python/python-magic-method)

|method|operator(?)|ex|translate (roughly)|
|------|---------|---|------|
| ```object.__getitem__(self, key)``` | ```[]``` | ```mylist[10]``` | ```type(mylist).__getitem__(mylist, 10)``` |
| ```object.__setitem__(self, key, value)``` | ```[]=``` | ```mylist[10] = 1``` | ```type(mylist).__setitem__(mylist, 10, 1)``` |
| ```object.__call__(self[, args...])``` | ```()``` | ```myfunc(arg1, arg2, ...)``` | ```type(myfunc).__call__(myfunc, arg1, ...)``` |


