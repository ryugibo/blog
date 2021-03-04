---
title: "언리얼 엔진 4 BindWidget 사용법 2"
date: 2021-03-03T19:38:01+09:00
ShowToc: true
TocOpen: false
tags: ["Unreal Engine 4", "C++"]
---

[언리얼 엔진 4 BindWidget 사용법]({{< relref "/posts/ue4-bindwidget" >}}) 에 이어서..

2를 붙일 정도로 많은 내용은 아닌데 예전에 정리했던 내용을 다시보니 빼먹은게 있어서 추가

결론부터 말하면 `BindWidget` 사용시엔 `BlueprintReadOnly`도 적어주는게 좋아보인다.

```cpp
#pragma once

#include "CoreMinimal.h"
#include "Blueprint/UserWidget.h"
#include "BoundWidget.generated.h"

UCLASS(Abstract)
class BOUND_API UBoundWidget : public UUserWidget
{
	GENERATED_BODY()

public:

	//~ Begin UserWidget Interfaces
	virtual void NativeConstruct() override;
	//~ End UserWidget Interfaces

public:

	UPROPERTY(BlueprintReadOnly, meta=(BindWidget))
	class UTextBlock* DescText;

	UPROPERTY(meta=(BindWidget, OptionalWidget=true))
	class UTextBlock* DescOptionText;

	UPROPERTY(meta=(BindWidgetOptional))
	class UTextBlock* HelloText;
};
```

C++ 상에서의 `private`이냐 `public`이냐는 것과는 별개로, 위젯 블루프린트 에디터상에서 배치한 위젯을 블루프린트에서 접근하지 못하는 미묘한 상황이 발생하기 때문이다.

C++에서 정의한 `UPROPERTY`에 연결되서 그런것으로 보이는데, 위젯 블루프린트 에디터에서 변수인지를 체크하는 박스는 BindWidget된 경우 동작하지 않는다.

`Optional`로 지정된 위젯은 `BlueprintReadOnly`로 했을 때, 블루프린트에서 접근하는 경우 `Optional`이기 때문에 블루프린트에서 접근할 때 조심할 필요가 있다.

물론 위젯 블루프린트에 로직을 전혀 담지 않는다면 필요없는 내용이다.
