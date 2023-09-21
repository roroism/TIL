# TODAY I LEARNED

## Learned

### CSS 코드 최적화

#### Eliminate render-blocking resources. (렌더 차단 리소스 제거)

- Render blocking 왜 문제인가? 브라우저가 외부 리소스를 다운로드하고 파싱하는 동안 페이지 콘텐츠를 파싱하거나 렌더링하지 않기 때문에 페이지 표시 속도 저하의 원인.
- unused CSS가 Render blocking을 가중하는 요인이다.

##### 해결방법

- lighthouse에서 Eliminate render-blocking resources 항목을 볼 수 있다. 여기 표시되는 목록 파일들이 렌더 차단을 하고 있는 파일들의 목록이다.
- 라이트 하우스가 렌더 블로킹 리소스를 표시하는 조건 : 

1. defer, async 속성이 없는 `<head>` 요소의 `<script>` 태그. -> 해결방법 : script 태그에 async나 defer태그를 사용해야 한다.
2. media 속성과 값이 없는 `<link rel="stylesheet">` 태그. -> 해결방법 : stylesheet 태그에는 media 속성의 태그를 사용해야 한다.

##### Render blocking `<script>`

- 결론적으로 defer태그를 더 추천한다.
- defer속성은 웹 페이지가 모두 그려지고, dom이 들어왔을 때, 그 때 script를 실행한다.

1. 필수 스크립트는 html에 `<script>` 형식으로 작성.
2. 기타 스크립트는 `</body>` 종료 태그 직전에 선언.
3. 마지막에 파싱해도 문제 없으면 defer 속성.
4. 돔이 파싱되는 동시에 가능한 빠른 시점에 실행 필요하면 async 속성.

