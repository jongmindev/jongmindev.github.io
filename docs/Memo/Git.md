---
layout : default
title : Git
nav_order : 2 
parent : Memo
---

# Git, GitHub
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---


## .gitignore
- 의의 : **python venv**, django settings.py, db, log, temp 등은 git에 올리면 안됨.
- 사용법 : 
    - \# 주석  
    - ~~filename.ext #주석~~ (:허용되지 않음)  
    - filename.ext (:모든 디렉토리 내 해당 파일에 대해서 적용됨)  
    - dir/.../filename.ext (:해당 디렉토리 내 해당 파일에 대해서만 적용됨)  
    - [추가문법](https://nochoco-lee.tistory.com/46)
- **프로젝트 도중에 .gitignore 생성 시** : git cache 를 삭제해야 적용됨.  
삭제커맨드 : `git rm -r --cached`
- .gitignore 파일 자동 생성 : [gitignore.io](https://www.toptal.com/developers/gitignore)


## PyCharm - GitHub 연동방법
[Tistory link](https://seong6496.tistory.com/147)
