---
layout : default
title : Ⅰ System Analysis
nav_order : 1
math: mathjax3 
parent : Markov Process and Expected Value
---

# Ⅰ. 아이템 강화 시스템의 구성 요소
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

- TOC
{:toc}

---

## 아이템강화 시스템의 요소 및 각 모형별 고려 요소

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
  font-weight:normal;overflow:hidden;word-break:normal;}
.tg .tg-x5q1{background-color:#ffffff;border-color:inherit;color:#000000;text-align:center;vertical-align:middle}
.tg .tg-ofrl{background-color:#FF0;border-color:inherit;color:#000000;text-align:center;vertical-align:middle}
.tg .tg-inmt{background-color:#efefef;border-color:inherit;color:#000000;font-weight:bold;text-align:center;vertical-align:middle}
.caption {caption-side: bottom}
</style>
<table class="tg">
<caption class="caption">[표 1] 각각의 아이템 강화 시스템 모형이 고려하는 요소들</caption>
<thead>
  <tr>
    <th class="tg-inmt" rowspan="2">모형</th>
    <th class="tg-inmt">성공</th>
    <th class="tg-inmt" colspan="3">실패</th>
    <th class="tg-inmt" colspan="2">비용</th>
    <th class="tg-inmt" colspan="2">실패 보호</th>
    <th class="tg-inmt" colspan="2">기타</th>
  </tr>
  <tr>
    <th class="tg-inmt">상승</th>
    <th class="tg-inmt">유지</th>
    <th class="tg-inmt">하락</th>
    <th class="tg-inmt">파괴</th>
    <th class="tg-inmt">강화<br>시도*</th>
    <th class="tg-inmt">파괴<br>복구*</th>
    <th class="tg-inmt">하락<br>방지</th>
    <th class="tg-inmt">파괴<br>방지</th>
    <th class="tg-inmt">확률<br>변화*</th>
    <th class="tg-inmt">비용<br>할인*</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-x5q1">Ⅱ.모형ⓐ</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">×</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">×</td>
    <td class="tg-ofrl">×</td>
    <td class="tg-x5q1">n/a</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">n/a</td>
    <td class="tg-ofrl">×</td>
    <td class="tg-ofrl">×</td>
  </tr>
  <tr>
    <td class="tg-x5q1">Ⅲ.모형ⓑ</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">○</td>
    <td class="tg-ofrl">○</td>
    <td class="tg-ofrl">×</td>
    <td class="tg-x5q1">×</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">△</td>
    <td class="tg-ofrl">○</td>
  </tr>
  <tr>
    <td class="tg-x5q1">Ⅳ.모형ⓒ</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-ofrl">○</td>
    <td class="tg-x5q1">×</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">△</td>
    <td class="tg-x5q1">○</td>
  </tr>
  <tr>
    <td class="tg-x5q1">Ⅴ.모형ⓓ</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">×</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
    <td class="tg-x5q1">○</td>
  </tr>
</tbody>
</table>

Ⅱ.모형ⓐ, Ⅲ.모형ⓑ, Ⅳ.모형ⓒ, Ⅴ.모형ⓓ은 각각 아래 해당 목차에서 설명하는 모형을 의미한다.  
모형ⓐ~ⓓ는 순서대로 고려사항이 점점 늘어나며, 모형ⓓ는 메이플스토리 인게임상의 스타포스 시스템과 완전히 동일하다.


### \[표1\] 개별 항목에 대한 부연 설명:  
**비용 - 강화시도**란, 각 강화 단계 별로 강화 (시도) 비용이 차이나는지(non constant) 여부를 의미한다.(단순한 비용 존재 여부가 아님)  
**비용 - 파괴복구**란, 메이플스토리 기준 ‘장비의 흔적’의 ‘장비 전승’ 시스템 존재 여부를 의미한다.  
**기타 - 확률변화**란, 스타캐치, 10성이하 1+1 이벤트, 5·10·15성 100% 이벤트, 찬스타임(2번 연속 실패시 100% 성공) 등 성공 확률 변화 요소를 의미한다. 이 중 찬스타임은 Ⅴ.모형ⓓ만 고려한다.  
**기타 - 비용할인**이란, MVP등급 할인, PC방 할인, 30% 할인 이벤트 등 강화 (시도) 비용 변화 요소를 의미한다.


### 용어의 정의
**강화 비용**이라는 용어는 각 단계에서 강화 시도를 1회 수행하는데 드는 비용(가령, 12성 → 13성 강화버튼을 한 번 누르는 데 필요한 비용)을 의미하는지, 또는 전체 강화 과정(가령, 12성 아이템을 17성까지 강화)에서 총 소모되는 비용을 의미하는지 혼동이 있을 수 있다.  
따라서 본 연구에서는 **강화 비용**은 일반적으로 후자를 의미하는 것으로 하고, 특별히 전자를 언급할 때는 **강화(시도)비용**이라는 용어를 사용하기로 한다.
