---
layout : default
title : venv
nav_order : 3
parent : Memo
---

# venv
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## CLI Command : remove and reinstall venv
1. save pip list  

        pip freeze > requirments.txt

2. remove venv  

        rm -rf ./venv
    <span style="color: red">**Caution! : ~~rm -rf /*~~**</span>

3. reinstall venv  

    venv 폴더 생성

        python -m venv /path/to/venv

    가상환경 활성화

        source /path/to/venv/bin/activate

    module 설치

        pip install -r requirements.txt
