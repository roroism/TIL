# TODAY I LEARNED

## Learned

### 덩어리 콘텐츠 빨리 그리기

#### LCP 개선 사례 (LCP 3.6초 단축한 이야기)

##### 라이브러리 의존 줄이기 (jquery, lodash, normalize...)

- jquery가 FCP를 상당히 지연시키고 있다. jquery를 제거할 수 있다면 제거하는 것을 추천한다.
- 사이트 추천 : https://youmightnotneed.com/ jquery나 lodash 대신 사용할 수 있는 바닐라 스크립트를 찾아볼 수 있다. 이 것을 사용해서 javascript 라이브러리를 제거하는데 도움을 받을 수 있다.

```html
<head>
    <!-- <link rel="stylesheet" href="normalize.css"> -->
</head>
```

- normalize나 reset과 같이 잘 사용하지 않거나 필요하지 않은 stylesheet 들을 과감하게 버리자.

##### Preconnect / Preload 기법

- 아래는 일반적으로 css코드를 참조하는 방법.

```html
<head>
    <link rel="stylesheet" href="*.css"> <!-- css를 로딩하고 해석하는 동안 웹 페이지가 차단된다. -->
</head>
```

- 아래처럼 수정하자.

```html
<head>
    <link rel="preconnect" href="https://fonts.gstatic.com">
    <link rel="preload" as="style" href="*.css" onload="this.onload=null;this.rel='stylesheet'">
</head>
```

- preconnect 란 값은 href에 적힌 url을 미리 연결하는 기능이다.

	- 미리 연결하여 준비하고 있다가 필요한 내용을 다운로드 받을 수 있게 도와준다.

- preload를 사용하면 css파일을 다운로드하면서 웹페이지 렌더링을 방해하지 않고, 웹 페이지를 렌더링하는 동시에 css 파일을 다운로드하게 되어 있다.
	- 그리고 onload script를 이용하여 css 다운로드가 끝나면 preload 값을 stylesheet로 바꿔서 stylesheet를 웹페이지에 적용하게 된다. 즉, 지양적용이다.

**<정리>**
`<link rel="preconnect">`
- 도메인을 알지만 자원의 최종 경로를 모르는 경우 서버와의 연결을 미리 설정.
- DNS(Domain Name Server), TCP(Transmission Control Protocol), TLS(Transfer Layer Security) 왕복에 필요한 시간을 단축.
- 서드 파티 자원 연결에 적합. preconnect를 구글 웹폰트를 참조하고 load 하는데 사용하고 있다.

`<link rel="preload">`
- 필요한 자원을 병렬 다운로드.
- 자원을 로딩하는 동안 렌더링을 차단하지 않음.
- as 속성을 함께 명시해 주어야 정상적으로 동작한다. 예) as="style", as="script", as="image".
- css 뿐만 아니라 이미지, 스크립트 등 다양한 파일들을 병행로딩할 수 있다.

