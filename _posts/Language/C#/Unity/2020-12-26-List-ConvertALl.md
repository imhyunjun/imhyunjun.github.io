---
layout : post
title : ConvertAll
category : C#/Unity
comments : true 
tags : C#
related : C#
---

# List.ConvertAll
---


```csharp
List<T>.ConvertAll<TOut>(Converter<T, TOut>)
```

T의형식을 Convertet메소드를 통해 TOut의 형태로 반환합니다. 쉽게 이해하면 List의 원소를 다른 원소로 바꾸어 새 리스트를 만드는 것입니다.

- 예시 1
```csharp
List<int> L1 = new List<int>() { 1, 2, 3, 4 };
List<string> L2 = L1.ConvertAll(x => (x + 1).ToString());
```
int로 이루어진 리스트 L1을 string으로 이루어진 L2로 변환하는 코드입니다. 

출력은 다음과 같습니다.

```csharp
foreach(var l in L1)
{
    Console.WriteLine(l);
}
foreach (var l in L2)
{
    Console.WriteLine(l);
}
```
>L1 : {1, 2, 3, 4}, L2 : {2, 3, 4, 5}

---
- 예시 2

P1, P2클래스를 만듭니다. P1은 **float** 변수, P2는 **int** 변수를 가지고 있습니다.
```csharp
class P1
{
    public float a { get; }
    public float b { get; }

    public P1(float _a, float _b)
    {
        a = _a;
        b = _b;
    }
}

class P2
{
    public int a { get; }
    public int b { get; }

    public P2(int _a, int _b)
    {
        a = _a;
        b = _b;
    }
}
```

이제 P1을 가진 List의 원소를 P2의 형태로 바꾼 새 리스트를 만들것입니다. 

```csharp
List<P1> L3 = new List<P1>();
L3.Add(new P1(1.1f, 3.2f));
L3.Add(new P1(2.2f, 4.5f));
L3.Add(new P1(5.3f, 3.2f));
L3.Add(new P1(1.01f, 3.03f));
List<P2> L4 = L3.ConvertAll(new Converter<P1, P2>(Converting));
```
이 때, P1에서 P2로 바꿔주는 Converter<> 함수를 하나 만들어 넣어줘야합니다.

```csharp
public static P2 Converting(P1 _p1)
{
    P2 p2 = new P2(((int)_p1.a), ((int)_p1.b));
    return p2;
}
```
출력을 해보면 다음과 같이 나옵니다.

```csharp
foreach (var l in L3)
{
    Console.WriteLine($"{l.a}, {l.b}");
}
foreach (var l in L4)
{
    Console.WriteLine($"{l.a}, {l.b}");
}
```
> L3 : {(1.1, 3.2), (2.2, 4.5), (5.3, 3.2), (1.01, 3.03)}
> L4 :{(1, 3), (2, 4), (5, 3), (1, 3)}






