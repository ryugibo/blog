---
title: "언리얼 엔진 4 범위 검사 IsWithin"
date: 2021-03-02T23:32:02+09:00
tags: ["Unreal Engine 4", C++]
---

간단한 TIL 정도 내용

언리얼 엔진에서 제공하는 함수중에 특정 값이 범위안에 포함되는지 검사하는 함수가 있어서 기록

```cpp
template< class U > 
static FORCEINLINE bool IsWithin(const U& TestValue, const U& MinValue, const U& MaxValue)
{
    return ((TestValue >= MinValue) && (TestValue < MaxValue));
}
```

정의는 위와 같고 보통 쓰게된다면 아래와 같이 쓰지 않을까..

```cpp
void Function(int32 InNumber)
{
    if (!FMath::IsWithin(InNumber, Min, Max))
    {
        return;
    }

    // Do Something
}
```

비슷하지만 최대값을 포함하는지도 검사하는 `IsWithinInclusive`도 있다.
