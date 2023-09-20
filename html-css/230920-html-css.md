# TODAY I LEARNED

## Learned

### CSS 코드 최적화

- CSS Optimization

#### 최적화 기법의 2가지 포인트

1. Remove unused CSS (사용하지 않는 CSS 제거)
2. Eliminate render-blocking resources. (렌더 차단 리소스 제거)

- css는 기본적으로 렌더 차단 리소스라고 부른다.
- 웹 브라우저가 css파일을 만나서 다운로드하고, css파일을 해석하는 동안 웹 페이지 랜더링은 차단된다. 그래서 렌더 차단 리소스라고 부른다.
- css를 더 이상 렌더 차단 리소스가 되지 않도록 만들 수 있다.

#### Remove unused CSS (사용하지 않는 CSS 제거)

- unused CSS는 페이지 렌더링을 차단하는 리소스. 이기 때문에 제거해야 한다.
- 브라우저가 스타일을 계산하는데 잠재적으로 더 많은 시간을 소비.
- 구글 라이트하우스는 2KB 이상 미사용 CSS가 포함된 파일을 검출하여 오류로 보고한다.
- 구글 라이트하우스는 개발자도구에 기본적으로 내장되어 있다.

