---
layout : post
title : Liquid를 알아보자2
category : Liquid
comments : true 
tags : Liquid
related : Liquid
---

# 연산자
---

## 기초 연산자

|==|!=|>|<|>=|<=|or|and|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|**같다**|**다르다**|**크다**|**작다**|**이상**|**이하**|**또는**|**그리고**|

기초 연산자는 평소 다른 언어나 국어처럼 직관적으로 사용하시면 됩니다.

```ruby
{ % if page.title == "연산자" % }
    "이번 포스트는 연산자 입니다"
{ % endif % }
```

## Contains
**contain**은 오직 **string**으로 이루어진 단어나 배열안에서 존재 유무를 판별할 때 사용합니다. 그 외의 자료형에는 사용이 불가합니다.

```ruby
{ % if page.title contains "연산" % }
    "연산이 포함"
{ % endif % }
```

## 연산 순서

**tag** 중에 **or** 이나 **and** 연산자가 중복되어 있을 때는 연산을 오른쪽에서부터 합니다. 괄호를 통해서도 이 순서는 변경되지 않습니다.

```ruby
{ % true and false or false % }
```
> 오른쪽부터 계산하면 false or false -> true. true and true -> true입니다. 따라서 위의 값은 **true**!










