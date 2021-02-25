---
title: "hugo PaperMod 테마에 Utterances로 댓글 붙이기"
date: 2021-02-25T22:24:29+09:00
ShowToc: true
TocOpen: false
tags: ["hugo", "PaperMod", "HTML"]
---

# 결론

`layouts/partials/comments.html`을 아래 내용으로 추가.

`utterances` `script`의 `repo` 부분은 저장소에 맞게 수정 필요.

```html
<script>
    document.write('<script src="https://utteranc.es/client.js" repo="ryugibo/blog" issue-term="pathname" label="💬" ');
    if (document.body.className.includes("dark")) {
        document.write('theme="github-dark-orange"');
    } else {
        document.write('theme="github-light"');
    }
    document.write(' crossorigin="anonymous" async><\/script>');
</script>

{{- if (not .Site.Params.disableThemeToggle) }}
<script>
    document.getElementById("theme-toggle").addEventListener("click", () => {
        if (document.body.className.includes("dark")) {
            const utterances = document.querySelector('iframe').contentWindow;
            utterances.postMessage({type: 'set-theme', theme: 'github-light'}, 'https://utteranc.es');
        } else {
            const utterances = document.querySelector('iframe').contentWindow;
            utterances.postMessage({type: 'set-theme', theme: 'github-dark-orange'}, 'https://utteranc.es');
        }
    })
</script>
{{- end }}
```

# 내용

`PaperMod` 테마는 `layouts/partials/comments.html` 를 테마를 사용하는 hugo 프로젝트에서 오버로드해서 사용하기를 권장하고 있다.

그래서 그냥 https://utteranc.es 에서 생성한 script 코드를 붙여넣으면 끝...인줄 알았으나 한 가지 문제가 발생

`PaperMod` 테마는 `light`, `dark` 테마 전환이 가능한데 `utterances`는 `script` 태그에서 테마를 지정해 넣어야 한다는 것.

물론, `defaultTheme` 를 `auto`가 아닌 `light`나 `dark`로 명시적으로 지정하고, `disableThemeToggle`를 `true`로 지정하면 특정 테마로 고정시키면 문제가 없긴한데..

기왕 있는 토글기능.. 써먹는게 좋지 않을까 하는 생각에...

## 테마에 맞게 utterances 테마를 지정

`PaperMod` 에 `layouts/partials/footer.html` 부분에서 테마에 따라 동작이 달라지는 코드가 있어서 해당 부분을 우선 참조해서 

현재 테마에 따라 `utteraces` 스크립트를 생성하도록 작성.

```html
<script>
    document.write('<script src="https://utteranc.es/client.js" repo="ryugibo/blog" issue-term="pathname" label="💬" ');
    if (document.body.className.includes("dark")) {
        document.write('theme="github-dark-orange"');
    } else {
        document.write('theme="github-light"');
    }
    document.write(' crossorigin="anonymous" async><\/script>');
</script>
```

## 테마를 변경했을 때 바로바로 utterances 테마도 같이 변경

위에서도 참조했던 `PaperMod` 에 `layouts/partials/footer.html` 부분은 테마 변경 버튼을 토글할 떄 이벤트에 추가해서 동작하고 있어서 해당 로직을 그대로 사용해서 이 부분도 작성.

처음엔 누를 때마다 `utterances` 스크립트 부분을 덮어씌기라도 해줘야 되나 싶었는데 "utterances theme change"로 구글에 검색하니 관련 기능이 이미 있었다.

https://github.com/utterance/utterances/issues/170

이 내용을 참조해서 버튼을 누를 때마다 갱신해주는 부분을 추가해서 완료.

```html
{{- if (not .Site.Params.disableThemeToggle) }}
<script>
    document.getElementById("theme-toggle").addEventListener("click", () => {
        if (document.body.className.includes("dark")) {
            const utterances = document.querySelector('iframe').contentWindow;
            utterances.postMessage({type: 'set-theme', theme: 'github-light'}, 'https://utteranc.es');
        } else {
            const utterances = document.querySelector('iframe').contentWindow;
            utterances.postMessage({type: 'set-theme', theme: 'github-dark-orange'}, 'https://utteranc.es');
        }
    })
</script>
{{- end }}
```

# 남은 문제

어차피 `comments.html` 을 hugo 프로젝트 수준에서 오버로드 하고 있기 때문에 당장 필요한 부분은 아니라고 생각되지만 `utterances` 의 `repo` 설정은 `config.yml` 에서 조정 가능하도록 하는게 좋을 것 같다.