---
layout : default
title : built-in Types
nav_order : 6
math: mathjax3
grand_parent : Python Modules
parent : built-in
---

# built-in Types
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## Mutability of built-in Classes

| Types | collection mutability | elements mutability | ordered | duplicate elements |
|:---:|:---:|:---:|:---:|:---:|
| String | × | ~~×~~ | ○ | ○ |
| List | ○ | ○ | ○ | ○ |
| Tuple | × | ○ | ○ | ○ |
| Set | ○ | × | × | × |
| Dictionary | ○ | × (key)<br/>○ (value) | (○) | × (key)<br/>○ (value) |

(cf) Hashing (```set```, ```key``` of ```dict```) assumes *distinct* & *immutable* elements.

(cf) empty set : ```set()``` ~~```{}```~~  
(cf) empty dictionary : ```{}```
