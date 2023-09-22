# TODAY I LEARNED

## Learned

### CSS 코드 최적화

#### Eliminate render-blocking resources. (렌더 차단 리소스 제거)

##### Render blocking `<script>`

- 결론적으로 defer태그를 더 추천한다.
- defer속성은 웹 페이지가 모두 그려지고, dom이 들어왔을 때, 그 때 script를 실행한다.

```html
// 병렬 다운로드, 즉시 실행
<script async src="script.js"></script>

// 병렬 다운로드, 지연 실행
<script defer src="script.js"></script>
```

1. 필수 스크립트는 html에 `<script>` 형식으로 작성.
2. 기타 스크립트는 `</body>` 종료 태그 직전에 선언.
3. 마지막에 파싱해도 문제 없으면 defer 속성.
4. 돔이 파싱되는 동시에 가능한 빠른 시점에 실행 필요하면 async 속성.

##### Render blocking `<link rel="stylesheet">`

- css의 렌더 블로킹 리소스 문제.
- media 속성이 없으면 css파일을 다운로드하고 해석하는 동안 웹브라우저 화면에는 아무것도 그려내지 않는다.
- media 속성은 하나의 조건문이라고 생각해도 된다.

```html
<!-- Render blocking resource -->
<link href="style.css"    rel="stylesheet">
<link href="style.css"    rel="stylesheet" media="all">
<!-- Render blocking resource -->
<link href="portrait.css" rel="stylesheet" media="orientation:portrait">
<link href="print.css"    rel="stylesheet" media="print">
```

- media="orientation:portrait" // orientation:portrait 일 때만 이 stylesheet를 해석한다는 의미이다.
- media="print" // print 할 때만 해석한다는 의미이다.
- 특정 조건에서만 css를 해석하도록 조건문 처리를 했기 때문에 렌더 차단 리소스로 파악이 되지 않는다.
- 그래서 반응형 웹을 구현을 할 때에도 해상도 구간별로 별도의 css를 작성한 다음에 link 태그에 media 쿼리 구문을 적용하여 모바일에서는 모바일 코드만 데스크탑에서는 데스크탑 코드만 다운로드해서 렌더링 하도록 만들면 가장 좋은 결과를 얻을 수 있다.

##### CSS 파일이 렌더링을 차단하는 과정

- css 로딩이 끝나기 전까지 fcp가 발생하지 않는다.
- fcp는 first content paint의 약자이다. 첫번째 내용물이 화면에 그려지는 시점을 의미한다.
- 즉, css파일이 다운로드되고 해석되는 동안 아무것도 그려내지 않는다. 그래서 사용자들은 이 페이지가 느리다고 생각할 수 있다.

##### 렌더를 차단하는 css파일. 렌더를 차단하는 blocking 이슈를 해결하는 방법

1. 반응형 웹인 경우 해상도 구간별로 css 파일을 분리하고 media 속성으로 분기.

```html
<link href="*.css" rel="stylesheet" media="(max-width:639px)">
<link href="*.css" rel="stylesheet" media="(min-width:640px) and (max-width:960px)">
<link href="*.css" rel="stylesheet" media="(min-width:961px)">
```

- 첫번째 줄 부터 : 모바일에서 적용할 코드, 테블릿에서 적용할 코드, 데스크탑에서 적용할 코드 로 나누었다.
- 조건에 맞지 않는 css링크는 다운로드하지 않고, 해석하지 않기 때문에 더 빨리 렌더링할 수 있다.

2-1. 필수 스타일은 페이지 `<head>`에 `<style>` 태그 안에 css 코드를 작성하는 것. 이렇게하면 이 코드들은 렌더차단 리소스가 되지 않는다.
2-2. 지연하고 싶은 스타일은 `<link rel="preload">` 속성으로 병렬 로딩 후 지연 적용. 예를 들면, javascript도 그렇지만 css도 뷰포트 화면 안에 있는 내용물을 그리는데 당장 필요한 css도 있고, 그렇지 않은 css도 있다. (예를 들어 사용자가 어떠한 행동을 해서 팝업을 띄우거나, 화면 스크롤 아래쪽에 있는 내용들은 당장 필요한 css는 아니다.) 이러한 css 들은 병렬로 loading 하고, 가능한 늦게 화면에 적용이 되도록 지연로딩을 할 수 있다. 이 때 사용하는 기법이 preload(병렬로딩기법) 이다.

- 정리하면. 필수 스타일은 임베딩, 지연 스타일은 병렬 로딩 후 지연 적용. 아래 예시 코드

```html
<style>
/* 필수 스타일 여기 */
</style>
<link rel="preload" as="style" href="x.css" onload="this.onload=null;this.rel='stylesheet'">
```

- onload속성 해석 : javascript로 페이지 onload가 완료(로딩이 완료) 되면 rel 속성에 있는 'preload'라는 값을 'stylesheet'로 바꿔준다.
- 그래서 preload상태일때는 다운로드만 하고, 화면에 적용하지 않다가 'stylesheet' 라는 값이 들어가면 그 때, 화면에 stylesheet를 적용 한다.
- 이 코드를 사용하게되면 css를 병행로딩. 렌더 차단하지 않고 html 문서를 해석하면서 동시에 css도 다운로드 받는다. 그리고 나중에 css 파일 로딩이 끝났을 때, 그 때 웹 페이지에 적용한다.
- 그 결과 아래처럼 Render blocking CSS 이슈를 해결할 수 있다.

#### 정리

1. 웹 브라우저는 외부 JS, CSS 파일을 로딩 하고 파싱 하는 동안 렌더링 차단 상태를 유지한다.
2. 사용하지 않는 JS, CSS 제거.
3. 필수 코드는 페이지에 `<style>...</style>`, `<script>...</script>` 작성하기.
4. 필수 아닌 JS는 `</body>` 종료 직전 위치를 고려. defer, async 속성을 사용.
5. 필수 아닌 CSS는 병렬 로딩(preload)하고 지연 적용(onload)하기.

