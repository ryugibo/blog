---
title: "언리얼 엔진 4 에디터 켜질 때마다 Steam VR 실행되는 문제"
date: 2021-03-01T20:37:10+09:00
ShowToc: true
TocOpen: false
tags: ["Unreal Engine 4"]
---

문제..까지는 아닌데 기본적으로 Steam VR 플러그인이 활성화되도록 되어있어서 VR 관련 설정을 손대지 않아도 자동으로 VR 설정이 되어있는 느낌이다. 결론은 Steam VR 플러그인을 비활성화 해주면 된다.

Oculus VR 은 자동으로 켜지진 않았는데 VR 프로젝트도 아니다 보니 Oculus VR 플러그인도 같이 비활성화해줬다.

에디터를 키기 전에 `*.uproject` 파일에 아래와 같이 `Plugins` 항목에 넣어준다.

```json
{
    // ... 프로젝트 설정들
	"Plugins": [
		{
			"Name": "OculusVR",
			"Enabled": false,
			"SupportedTargetPlatforms": [
				"Win32",
				"Win64",
				"Android"
			]
		},
		{
			"Name": "SteamVR",
			"Enabled": false,
			"SupportedTargetPlatforms": [
				"Win32",
				"Win64",
				"Linux"
			]
		}
	]
}
```

프로젝트가 다수인 경우 Steam VR 플러그인 폴더(`Engine\Plugins\Runtime\Steam\SteamVR`)에 있는 `SteamVR.uplugin` 에서 `"EnabledByDefault": true` 를 `"EnabledByDefault": false`로 하면 기본 비활성 상태로 만든다.

에픽 게임즈 런처로 설치한 경우 변경점을 한눈에 알아보기 어렵고, 엔진 버전 올릴때마다 확인해줘야 하기 떄문에 프로젝트 단위로 설정하는게 좋아보인다.
