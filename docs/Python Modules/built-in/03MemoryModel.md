---
layout : default
title : Memory Model
nav_order : 3
math: mathjax3
grand_parent : Python Modules
parent : built-in
---

# Memory Model
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 1. Variable Assignment

### ```<<variable>> = <<expression>> ```

- Step 1: *Evaluate* the expression to produce a value. This value is stored in a memory object.
- Step 2: Store the **address** of the memory object in the variable.  
(If the variable already exists, replace the memory address that is contains.)
- Result: The **variable** *points* the memory where the **value** is stored.  
implementation : A (proper) *namespace*(```dict```) has the pair of the ```key``` **variable**(```str```) and the ```value``` **value**(```object```).

### example

input :

```python
f = min
f = max
g, h = min, max
max = g
max(f(2, g(h(1, 5), 3)), 4)
```

step-by-step:  

[0] ```min``` in built-in namespace → \<function min\>  
[0] ```max``` in built-in namespace → \<function max\> 

[1] ```f``` in global namespace → \<function min\>(*evaluation* of ```min```)  
[2] ```f``` in global namespace → \<function max\>(*evaluation* of ```max```)  
[3] ```g``` in global namespace → \<function min\>(*evaluation* of ```min```)  
[3] ```h``` in global namespace → \<function max\>(*evaluation* of ```max```)  
[4] ```max``` in global namespace → \<function min\> (*evaluation* of ```g```)  
[5] ```min(max(2, min(max(1, 5), 3)), 4)```  
[5] ```Return value``` in local(\<function min\>) namespace → ```3```


output :

```console
3
```


## 2. Function Call

### ```myfunc(arg1, agr2, ...)```

- Step 1: *Evaluate* the **arguments** left to right.
- Step 2: Create a **namespace** to hold the function call's **local variables**, including the parameters.
- Step 3: Pass the resulting **argument values** into the fuction by assigning them to the **parameters**.
- Step 4: Execute the **function body**. When a **return** statement is executed, the function terminates and the value of the expression in the return statement is used as the value of the function call.
