---
layout : post
title : Liquid를 알아보자1
category : Liquid
comments : true 
tags : Liquid
related : Liquid
---

# Liquid 언어
---


이번에 **Github Page**를 통해 블로그를 만들게 되었습니다. 이 **Github Page**는 **jekyll**을 사용하고 **jekyll**에는 수많은 테마들이 있는데 그 중 하나를 골라서 설정할 수 있습니다. 저는 **Monos**라는 테마를 선택하였고, 지금 현재 제 블로그에 적용했습니다. 하지만, 막상 적용해보니 맘에 들지 않는 부분들이 생겼고 이를 제 입맛에 맞게 커스터마이징 하고 싶어 **Liquid**를 공부해볼까 합니다.

**Liquid**는 아래와 같이 **Ruby**라는 프로그래밍 언어로 만들어져있습니다.

> *Liquid is an open-source template language created by Shopify and written in Ruby.*

하지만 **Ruby**를 몰라도 충분히 배울 수 있습니다.( 저도 아예 모르는 상태라..)

## Object, Tag, Filter
---
**Liquid** 코드는 크게 **Object, Tag, filter**로 나누어질 수 있습니다.
{%raw%}
- Object : 페이지에 보여주는 내용으로 '{{' 와 '}}'를 사용하여 표기합니다. 변수와 같은 개념이라 생각하시면 됩니다.
{% endraw %}
{%raw%}
```ruby
{{ blog.name }}
```  
{% endraw %}
  
- Tag : 각종 논리 연산과 제어 흐름을 를 사용하여 표기합니다.
태그의 종류에는 **Control Flow, Iteration, Variable Assignment**가 있습니다. 

{%raw%}
```ruby
{ % if user % }
 Hello {{ user.name }}!
{ % endif % }
```
{% endraw %}

>사용자의 이름이 있으면 Hello 사용자의 이름을 출력

- Filter : Object를 출력할 때 조건을 이용하여 변경하여 출력합니다. 조건은 '|'를 사용합니다.
조건에는 다양한 함수들이 존재합니다.

{%raw%}
```ruby
{{ "/imhyunjun/github/url" | append: ".io" }}
```
{% endraw %}
> /imhyunjun/github/url.io 출력 

다중 필터를 사용 할 수 있는데 이는 오직 변수 한개에만 사용 가능 합니다.

{%raw%}
```ruby
{{ "adam!" | capitalize | prepend: "Hello " }}
```
{% endraw %}

> adam!의 첫글자를 대문자로 만들고 그 앞에 "Hello"를 붙입니다. -> Hello Adam! 



출처 : [Liquid 홈페이지](https://shopify.github.io/liquid/)