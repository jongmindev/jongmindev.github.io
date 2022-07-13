---
layout : default
title : Namespace and Scope
nav_order : 2
math: mathjax3
grand_parent : Python Modules
parent : built-in
---

# Namespace and Scope
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

Reference : [파이썬의 Namespace와 Scope](https://hongl.tistory.com/260)


## 1. Namespaces and Variable Scope


### namespaces

- Built-in namespace
- Global namespace
- Enclosing namespace
- Local namespace

### variable scope

- access priority : LEGB


## 2. access to namespaces by built-in functions

### ```globals()```

> Return the *(reference of the)* dictionary implementing the current module namespace.
>
> **Note** : The contents of this dictionary should **be modified; changes may affect**

### ```locals()```

> Update and return a dictionary representing the current local symbol table.  
>
> **Note** : The contents of this dictionary should **not be modified; changes may not affect** the values of local and free variables used by the interpreter.


## 3. modify variables out of scope

keywords : ```global```, ```nonlocal```
