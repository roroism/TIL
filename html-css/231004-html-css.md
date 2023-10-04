# TODAY I LEARNED

## Learned

### 덩어리 콘텐츠 빨리 그리기

#### LCP 개선 사례 (LCP 3.6초 단축한 이야기)

##### Feature detection

- Image type 이나 Viewport width 를 감지해서 성능을 개선하는 방법이다.
- 우리가 일반적으로 사용하는 방법은 아래와 같다.

```html
<!-- UNOPTIMIZED HERO IMAGE (이미지최적화가 되어있지 않음)-->
<img src="large.jpg" alt>
```

- 이미지 회적화를 한다면 아래처럼 할 수 있다.

```html
<!-- OPTIMIZED HERO IMAGE -->
<picture>
	<!-- AVIF && SMALL SCREEN -->
    <source srcset="small.avif" type="image/avif" media="(max-width:640px)">
	<!-- AVIF && LARGE SCREEN -->
    <source srcset="large.avif" type="image/avif">
	<!-- WEBP && SMALL SCREEN -->
    <source srcset="small.webp" type="image/webp" media="(max-width:640px)">
	<!-- WEBP && LARGE SCREEN -->
    <source srcset="large.webp" type="image/webp">
	<!-- FALLBACK -->
    <img src="small.jpg" alt>
</picture>
```

- type 과 media라는 조건 구문을 붙여야 한다.
- 조건 : avif 타입을 지원하면서 동시에 640px 이하이면 small.avif 이미지를 출력한다. -> 이 조건이 충족된다면 `<img src="small.jpg" alt>` 에 small.avif를 표시하게 된다. 실행하게 되면, 나머지 요소들은 다운로드하거나 화면에 표시하지 않게 된다.

##### Image Loading / Decoding

- 앞으로는 loading과 decoding 속성을 명시하는 것을 추천한다.

```html
<!-- 최적화되지 않은 이미지 사용법 (unoptimized image) -->
<img src="example.jpg" alt>
```

```html
<!-- 최적화된 이미지 (optimized image) -->
<img 
    src="example.jpg" 
    loading="lazy"
    decoding="async"
alt>
```

- **loading="lazy"**을 사용하면 뷰포트안에 들어와있지 않으면 이미지를 loading 하지 않는다. 페이지가 로딩되고, 화면 아래쪽에 있는 이미지들은 로딩되지 않은 상태로 존재하다가 사용자가 scroll 하면서 페이지 문서가 뷰포트 안쪽으로 들어올때, 모니터 뷰 포트 높이의 1배에서 2배 크기 아래쪽 부터 이미지가 로딩되기 시작해서 그 때 화면에 표시할 준비를 한다. 이것을 lazy load 기법이라고 한다. javascript를 사용하지 않고도 이미지 지연 로딩을 할 수 있다.
- **decoding="async"** decoding은 암호화했던 이미지를 복호화하는 방법이다. 복호화 방법으로 async 라는 값을 사용하면 화면에 다른 요소를 렌더링 하는 것을 중단하지 않고 다른 요소를 먼저 표시하고 이미지를 뒤늦게(지연해서) 화면에 표시하게 해준다.
- 이 두가지 옵션을 사용하면 가능한 다른 요소들이 빠르게 화면에 표시되기 때문에 이미지 최적화에 매우 큰 도움이 된다.
- loading 과 decoding 이라는 속성은 img속성에만 사용한다. picture나 source 요소에는 loading 과 decoding 속성을 사용하지 않아도 된다.

#### 정리

1. LCP는 뷰포트에 표시하는 가장 큰 콘텐츠 렌더링 성능.
2. 가장 큰 덩어리 콘텐츠를 2.5초 이내로 표시해야 한다.
3. JS/CSS 라이브러리 의존도를 낮추어야 한다.
4. preconnect/preload 속성으로 외부 자원 최적화.
5. photo 요소의 type, media 속성으로 이미지 전송량 최적화.
6. loading/decoding 속성으로 이미지 렌더링 최적화.

