# TODAY I LEARNED

## Learned

### 이미지 마크업 최적화

- picture 기능을 잘 활용하면 우리들의 서버비용을 절약할 수 있고, 사용자 경험을 아주 작은 기법만으로도 크게 향상시킬수가 있다.
- 대용량 이미지를 가볍게 만든다.
- jpg/png : 과거의 유산
- webp : jpg/png 대비 30~70% 용량
- avif : 저용량+고품질
- 여러가지 포맷을 준비한 다음에 사용자 환경에 알맞는 이미지 포멧을 내려준다.
- avif 포맷을 권장한다.

#### picture, source, img 마크업 방법

```javascript
if('avif'를 지원하면) {
	'avif' 출력
} else if('webp'를 지원하면) {
	'webp' 출력
} else {
	'jpg' 출력
}
```

- source의 type속성 : 조건절이라고 생각하면 된다.

```html
<!-- 이미지 타입 분기 -->
<picture>
	<source srcset="x.avif" type="image/avif">
	<source srcset="x.webp" type="image/webp">
	<img src="x.jpg" alt>
</picture>
```

- 사용자 환경을 탐지하는 역할을 picture 요소가 제공한다.
- type 뿐만 아니라 media 속성도 가능하다.

```html
<!-- 해상도 분기 -->
<picture>
	<source srcset="small.webp" media="(max-width:960px)">
	<img src="large.webp" alt>
</picture>
```

- 해상력으로 분기

```html
<!-- 해상력 분기 -->
<picture>
	<source srcset="2x.webp 2x, 1x.webp" type="image/webp">
	<img srcset="2x.jpg 2x" src="1x.jpg" alt>
</picture>
```

#### img 요소의 성능

- loading="lazy" 로딩 지연
- decoding="async" 디코딩 지연 : 이미지 디코딩을 병렬로 처리해서 이미지외에 다른 콘텐츠가 웹페이지에 빠르게 표시되게 도와준다.

#### debugging 팁

- picture와 source는 화면에 출력되는 요소가 아니다.
- currentSrc : 현재 화면에 출력하고 있는 소스.
- intrinsic : 현재 화면에 출력하는 소스의 원본 사이즈.

#### 정리

- avif 포맷을 제공하고 webp, jpg를 대체 수단으로 제공한다.
- picture, source, img 요소와 srcset, type, media 속성의 문법을 익히자.
- 빠른 로딩 속도를 통해 UX를 개선하고 이미지 전송 비용을 절약하자.

